# Tenant

> [!info|label:Definitie]
>Elke [installatie](/common/content/concept-instance) kan logisch opgedeeld worden in tenants. Elke **tenant** is een afgescheiden geheel waarin content gescheiden is. Maw, redacteurs die in één tenant werken kunnen niet aan content werken uit een andere tenant, tenzij natuurlijk dat ze hier ook de rechten voor hebben. 

In het voorbeeld hieronder heb ik rechten op 2 verschillende tenants als gebruiker. (Ik vermeld momenteel nog even gebruiker, straks gaan we dieper in op de [rollen van het systeem](/redactie/content/toegang-werken-als))

![Multi tenant](../assets/gpubp-multi-tenant.jpg 'Een instantie met 2 tenants')

Belangrijk om te vermelden is dat je per tenant kan kiezen welke [modules](/common/content/concept-modules) je gaat hanteren. Dit is de lijst van geïnstalleerde [WCM modules](/modules/content/wcm-modules.md) voor de instantie die we hosten op het datacenter van Digipolis. In tenant één maken we alle modules beschikbaar, in tenant twee enkel 6 modules. Wil je echter één module anders inzetten (dus het gedrag veranderen door het anders te configureren), dan richt je best verschillende instanties in.

![Modules per tenant](../assets/gpubp-basisbegrippen-modules-per-tenant.png 'De verschillende modules per tenant')

**[Content Types](/common/content/concept-ct)**, **[Content Blokken](/common/content/concept-cb)** en **[Content Componenten](/common/content/concept-cc)** zijn allemaal Tenant specifiek, maw, ze gelden voor de hele tenant.

![Inrichting per tenant](../assets/gpubp-basisbegrippen-content-types.png 'Content types, blokken en componenten zijn per tenant')
