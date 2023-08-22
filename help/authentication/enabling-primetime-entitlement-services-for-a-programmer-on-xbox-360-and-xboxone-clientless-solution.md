---
title: Primetime machtigingsservices inschakelen voor een programmeur op Xbox 360 en XboxOne-client
description: Primetime machtigingsservices inschakelen voor een programmeur op Xbox 360 en XboxOne-client
exl-id: ff7254de-9ea4-4c27-a186-d1c2eea12222
source-git-commit: 84a16ce775a0aab96ad954997c008b5265e69283
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Primetime machtigingsservices inschakelen voor een programmeur op Xbox 360 en XboxOne-client {#enabling-primetime-entitlement-services-for-a-programer-on-xbox-360-and-xboxone-clientless}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.




1. De programmeur creeert een kaartje van Zendesk voor het toelaten van Xbox 360/One voor de cliënt van de authentificatie Primetime door de volgende informatie te verstrekken:

   1. Platform: bv. Xbox 360, Xbox One

   1. Id aanvrager: bv. netgeo, CNN enz.

1. De Adobe zal X509 Certificaten tot stand brengen en zal de privé sleutel en het wachtwoord aan zijn eind vormen.

1. De Adobe zal het Openbare certificaat (van X509 cert) aan Programmeur in het kaartje of via e-mail verstrekken.

1. De programmeur moet dat openbare certificaat dan installeren op de GDNP-portal voor de toepassing die bij Microsoft is geregistreerd.

1. De programmeur zal dan JWT (Java Web Token) of STS Token voor XboxOne of 360 van de dienst van de Xbox Live van Microsoft verzoeken, die zou worden gecodeerd gebruikend het openbare certificaat X509 dat in stap 3 wordt verstrekt.

1. Dit zijn de tokens die unieke deviceId voor Xbox-apparaten bevatten. Neem het token (JWT of STS) op in de machtigingheader met behulp van de parameter &#39;x&#39;, zoals hieronder:

   1. Voor Xbox 360 moet het XSTS-token Base64-gecodeerd zijn voordat het naar Primetime pay-TV-verificatie wordt verzonden.
   1. Voor Xbox One is de JWT al correct gecodeerd, zodat er geen extra codering moet plaatsvinden.

1. Alle API-aanroepen van het Xbox-apparaat moeten de machtigingsheader met het bovenstaande token in de parameter x bevatten.



>[!NOTE]
>
>Met name de Xbox heeft een aantal unieke vereisten met betrekking tot digitale ondertekening. De apparaat-id van de XBox-console is opgenomen in het XSTS-token.  Voor Xbox 360 is dit een gecodeerde SAML-bewering; voor Xbox One is dit een gecodeerde JWT. De XBox-console-app verzendt het volledige XSTS-token naar Primetime-verificatie voor betaaltelevisie. De betaling-TV van de primaire tijd authentificatie decrypteert het teken gebruikend zijn openbare sleutel, ontleedt het teken, en haalt deviceId uit het uit.

>[!NOTE]
>
>Wegens de grote lengte van het teken van XSTS, heeft de console XBox een technische beperking: het kan niet het teken als parameter van HTTP naar Primetime betaal-TV authentificatie APIs verzenden. Om dit te behandelen, staat de betaling-TV authentificatie Primetime toe verzendend het teken van XSTS als deel van de kopbal van HTTP &quot;Vergunning&quot;wanneer het roepen van APIs. De token XSTS moet worden gecodeerd met de openbare sleutel van het X.509-certificaat dat aan de programmeur is uitgegeven vanaf Primetime betaaltelevisie-verificatie. Bij betaaltelevisie in primetime wordt de bijbehorende persoonlijke sleutel opgeslagen en gebruikt om het XSTS-token te decoderen en de deviceId uit het token te extraheren.
