# Hoofdstuk 6: Werken met events

We bouwen verder op de greetings module en we gaan op basis van onze call een event uitsturen.

## Stap 1: Installeren van event registry helper package en opzet event registry instance

Voor het werken met events is een package voorzien om de werking te stroomlijnen. Documentatie van de functies die deze package export kan je hier vinden: 
[Event Registry Helper (BE) <i class="fa-solid fa-xs fa-arrow-up-right-from-square"></i>](https://gpubp.github.io/event-registry-helper_package_nodejs ':target="_blank"')

Beginnen doen we met deze package te installeren.
```
npm i @wcm/event-registry-helper
```

Om nadien een eventRegistry instantie (singleton) aan te maken.
```ts
// server/src/shared/instances/eventRegistry.ts
import { EventRegistryHelper } from '@wcm/event-registry-helper';

import config from '~config';
import { tenantConfig } from '~shared/helpers/tenant';

export const eventRegistry = new EventRegistryHelper({
	tenantsConfig: tenantConfig,
	kafkaConfig: {
		ca: config.kafka.ca,
		key: config.kafka.key,
		cert: config.kafka.cert,
		origin: config.kafka.origin,
		host: config.kafka.host,
	},
	gatewayBaseUrl: config.gateway.baseUrl,
});
```

Bij het aanmaken van deze instantie geven we de tenantConfig, kafkaConfig en de (base) url van de gateway mee. 

## Stap 2: Registeren van events

Vooraleer we events kunnen uitsturen moet de "blueprint" van deze events gekend zijn in het systeem. Hiervoor maken we gebruik van het gestandaardiseerde cloudevents json schema. 

We maken een `greetings-sent.event.json` file aan dat het event omschrijft.
```json
// server/src/modules/greetings/v1/events/greetings-sent.event.json
{
	"data": {
		"source": "greetings",
		"event": "sent",
		"version": "v1",
		"specVersion": "1.0",
		"description": "Wanneer de greetings endpoint aangesproken is",
		"dataContentType": "application/json",
		"dataSchema":{
			"$schema": "https://json-schema.org/draft-07/schema",
			"$id": "http://example.com/example.json",
			"title": "Root Schema",
			"type": "object",
			"default": {},
			"required": [
				"specVersion",
				"type",
				"source",
				"dataContentType",
				"dataSchema",
				"data"
			],
			"properties": {
				"specVersion": {
					"title": "The specVersion Schema",
					"type": "string",
					"default": "",
					"examples": [
						"1.0"
					]
				},
				"type": {
					"title": "The type Schema",
					"type": "string",
					"default": "",
					"examples": [
						"greetings.sent.v1"
					]
				},
				"source": {
					"title": "The source Schema",
					"type": "string",
					"default": "",
					"examples": [
						"be.digipolis.wcm"
					]
				},
				"dataContentType": {
					"title": "The dataContentType Schema",
					"type": "string",
					"default": "",
					"examples": [
						"application/json"
					]
				},
				"dataSchema": {
					"title": "The dataSchema Schema",
					"type": "string",
					"default": "",
					"examples": [
						"https://wcm-gateway-app1-p.antwerpen.be/docs/..."
					]
				},
				"data": {
					"title": "The data Schema",
					"type": "object",
					"default": {},
					"required": [
						"message"
					],
					"properties": {
						"message": {
							"title": "The message Schema",
							"type": "string",
							"default": "",
							"examples": [
								"Welkom"
							]
						}
					},
					"examples": [{
						"message": "Welkom"
					}]
				}
			},
			"examples": [{
				"specVersion": "1.0",
				"type": "greetings.sent.v1",
				"source": "be.digipolis.wcm",
				"dataContentType": "application/json",
				"dataSchema": "https://wcm-gateway-app1-p.antwerpen.be/docs/...",
				"data": {
					"message": "Welkom"
				}
			}]
		},
	},
	"meta": {
		"category": "public"
	}
}
```

Tip: Het converteren van json naar een jsonschema kan eenvoudig met [jsonschema.net](https://www.jsonschema.net/). 

Vervolgens kunnen we de eventbeschrijving gaan registreren.

```ts
// server/src/modules/greetings/greetings.module.ts

import { greetingsSentEvent } from './events';

...
@Module({
  ...
})
export class GreetingsModule {
	constructor() {
		if (!tenantConfig.getModuleContext()) {
			tenantConfig.on('ready', () => this.registerPermissions());
		} else {
			this.registerEvents();
		}
	}

	private async registerEvents() {
		// tslint:disable-next-line: no-console
		console.log('REGISTERING GREETINGS EVENTS ...');

		const result = await eventRegistry.registerEvents(tenantConfig.getAllApps()[0].apikey, [
			greetingsSentEvent
		]).catch(() => null);

		// tslint:disable-next-line: no-console
		console.log('GREETINGS EVENTS REGISTERED WITH RESULT:', JSON.stringify(result, null, 4));
	}
	...
}
...
```

Na dit voorzien te hebben zijn we klaar om ook effectief events te gaan uitsturen.

## Stap 4: Creëer een interceptor

Om effectief events uit te sturen maken we veelal gebruik van interceptors. Dit om de logica af te schermen en herbruikbaar te maken. We maken een greetings-sent interceptor aan, die een event gaat uitsturen van zodra een GET request naar de `/greetings` endpoint heeft plaatsgevonden. In de interceptor voorzien we logica die na het afhandelen van de request nog een event gaat uitsturen met behulp van de eventRegistry instantie die we eerder aangemaakt hebben. 

```ts
import { CallHandler, ExecutionContext, Injectable, NestInterceptor } from '@nestjs/common';
import { AppContext } from '@wcm/config-helper';
import { Request } from 'express';
import { Observable } from 'rxjs';
import { take, tap } from 'rxjs/operators';

import config from '~config';
import { tenantConfig } from '~shared/helpers/tenant';
import { eventRegistry } from '~shared/instances/eventRegistry';

@Injectable()
export class GreetingsSentInterceptor implements NestInterceptor {
	// tslint:disable-next-line: no-any
	intercept(ctx: ExecutionContext, next: CallHandler): Observable<any> {
		return next.handle().pipe(
			take(1),
			tap(async (data) => {
				const req: Request = ctx.switchToHttp().getRequest();
				const appContext: AppContext = tenantConfig.getAppContext(req.get('apikey'));
				const tenantUuid = appContext.uuid;

				eventRegistry.sendMessage({
						source: 'greetings',
						event: 'sent',
						data: {
							message: 'Welkom uitgestuurd',
						},
					}, config.kafka.topics.content);
			}
		));
	}
}

```

Deze interceptor kunnen we nu op onze endpoint gaan plaatsen. 

```ts
// server/src/modules/greetings/v1/controllers/greetings.controller.ts

import { GreetingsSentInterceptor } from '../interceptors';

...
	@Get()
	@ApiOperation({ summary: 'Get a greeting', description: 'Get a greeting from a tenant' })
	@ApiOkResponse({ type: Greeting })
	@ApiAccess(apiAccessMap.ADMIN)
	@SecurityRights('greetings_read')
	@UseInterceptors(GreetingsSentInterceptor)
	public async getGreeting(): Promise<Greeting> {
		return {
			message: 'Welkom',
		};
	}
```
