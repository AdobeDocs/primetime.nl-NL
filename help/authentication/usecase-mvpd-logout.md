---
title: MVPD Logout
description: MVPD Logout
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---


# MVPD Logout

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

De gebruiksgevallen van het Logout kunnen of door een Logout van SAML verzoek worden uitgevoerd dat naar IdP wordt verzonden of door een eindpunt van de douanelogout dat wordt geroepen.  De onderstaande verzoek- en responsvoorbeelden bevatten voorbeelden van de SAML-uitlogimplementatie.

## Voorbeeld-afmeldingsaanvraag {#sample-logout-request}

```XML
<?xml version="1.0" encoding="UTF-8"?>
<samlp:LogoutRequest
        Destination="https://idpcom/slo" ID="_b18de1a2-5bc2-4866-88e3-97a9cbb663ca"
        IssueInstant="2010-08-18T07:18:22.479Z"
        Reason="urn:oasis:names:tc:SAML:2.0:logout:user"
        Version="2.0"
        xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion"
        xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol">
    <saml:Issuer>https://saml.sp.auth.adobe.com</saml:Issuer>
    <saml:NameID
        Format="urn:oasis:names:tc:SAML:2.0:nameid format:transient">
            DkCwM54kzVs5coXH0R0IFhPSA9a
    </saml:NameID>
    <samlp:SessionIndex>L4EQmlLCIS-5hHr71z1VfOCEYWk</samlp:SessionIndex>
</samlp:LogoutRequest>
```

## Voorbeeld van afmeldingsreactie {#sample-logout-response}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<samlp:LogoutResponse
        Destination="https://sp.auth-staging.adobe.com/sp/saml/LogoutServiceHTTPRedirectResponse"
        ID="XpsdJNdPp7PEnNxfeBubP.w4e3r"
        InResponseTo="_b18de1a2-5bc2-4866-88e3-97a9cbb663ca"
        IssueInstant="2010-08-18T07:18:24.969Z" Version="2.0"
        xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol">
    <saml:Issuer  
        xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion">https://idp.com/slo
    </saml:Issuer>
    <samlp:Status>
        <samlp:StatusCode Value="urn:oasis:names:tc:SAML:2.0:status:Success"/>
    </samlp:Status>
</samlp:LogoutResponse>
```

<!--
>[!RELATEDINFORMATION]
>* [Content Metadata Exchange](/help/authentication/mvpd-content-metadata-exchange.md)
>* [Preflight Authorization](/help/authentication/mvpd-preflight-authz.md)
>* [MVPD Integration Features](/help/authentication/mvpd-integr-features.md)
-->