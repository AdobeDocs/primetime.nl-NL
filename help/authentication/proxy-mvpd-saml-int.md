---
title: Proxy MVPD SAML-integratie
description: Proxy MVPD SAML-integratie
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 1%

---


# Proxy MVPD SAML-integratie

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Overzicht {#overview-proxy-mvpd-saml-int}

In dit document wordt de SAML-verificatiestroom voor Proxy-integratie beschreven.  Deze stromen zijn afhankelijk van de configuratiegegevens van de Volmacht die in de configuratie van de de authentificatieserver van Adobe Primetime aanwezig zijn. De Volmacht MVPD duwt zijn Volmacht config gegevens aan de de authentificatieserver van Adobe Primetime via de dienst van het Web van de Volmacht van de Volmacht van Adobe Primetime.

## Proxyconfiguratiegegevens {#proxy-config-data}

Elke Volmacht MVPD verstrekt de configuratiegegevens van de Volmacht voor hun Proxied MVPDs aan de Dienst van het Web van de Volmacht van de Volmacht van de Adobe Primetime authentificatieProxy.  De details voor dat worden behandeld in de documentatie van de Dienst van het Web van de Volmacht.   Voor de stroom van SAML AuthN om te werken, moeten de volmacht config gegevens de volgende eigenschappen omvatten:

| Eigenschap | Beschrijving |
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| MVPD-id | Tekenreeks die de Proxied MVPD intern vertegenwoordigt voor Adobe Primetime-verificatie.  Door Adobe als uniek te bevestigen in het kader van Adobe Primetime-verificatie. |
| URL standaardlogo MVPD | URL aan een embleem dat in een Ervaring van de Selecteur MVPD voor de gebruiker kan worden getoond.  Gebruik een transparante achtergrond. |
| Weergavenaam MVPD | Tekenreeks die moet worden gebruikt als de tekst voor de weergavenaam die met het logo kan worden weergegeven, mogelijk als alternatieve tekst. |



## SAML-integratiestromen {#saml-int-flows}

Wanneer een abonnee MVPD de plaats of de toepassing van een Programmer bezoekt, antwoordt de authentificatie van Adobe Primetime aan een API vraag van de plaats of de toepassing met een lijst van MVPDs die voor die Programmer wordt geactiveerd.  De integratie kan direct of geproxideerd zijn; de programmeur maakt er geen onderscheid tussen beide. Hierdoor kunnen programmeurs de lijst met actieve MVPD&#39;s op elke manier presenteren die zij geschikt achten. De abonnee kiest hun MVPD, en de authentificatie van Adobe Primetime richt de abonnee aan specifieke Identiteitsprovider van MVPD opnieuw.

In het geval van een geïntegreerde Volmacht MVPD, wordt de integratie gedaan tussen de authentificatie van Adobe Primetime en de Volmacht MVPD. De authentificatie van Adobe Primetime verzendt het verzoek van de gebruikersauthentificatie naar de Volmacht MVPD, en de Volmacht MVPD behandelt redirection. Opdat de Volmacht MVPD weet waar te om het verzoek van de gebruikersauthentificatie opnieuw te richten, verzendt de authentificatie van Adobe Primetime een herkenningsteken MVPD in het de authentificatieverzoek van SAML.  Dit herkenningsteken is identiteitskaart MVPD die door de Leverancier van de Volmacht als hierboven gespecificeerd wordt gespecificeerd.

### Verificatie {#authn-saml-int}

Adobe Primetime-verificatie kan alleen worden geïntegreerd met een proxy-MVPD als:

* Een Volmacht MVPD verstrekte lijst van Proxied MVPDs, die aan de Dienst van het Web van de Volmacht van Adobe wordt geduwd

* SAML-metagegevens voor de bovenliggende MVPD-proxy

* (Aanbevolen) - Proxy MVPD behandelt extra omleiding aan de login pagina URL van Proxied MVPD

* De Volmacht MVPD moet havens 443 en 80 voor volgende IPs openen:
   * 192.150.4.5
   * 192.150.10.200
   * 192.150.11.4
   * 4.53.93.130
   * 193.105.140.131
   * 193.105.140.132
   * 76.74.170.204
   * 63.140.39.4
   * 66.235.132.38
   * 66.235.139.38
   * 66.235.139.168


#### SAML-verzoek en -antwoord voor verificatie {#authn-saml-req-resp}

In het SAML verzoek AuthN, omvatten de integratie van de Volmacht het volgende extra bezit dat door de Volmacht moet worden behandeld MVPD.  Dit bezit is noodzakelijk om de aanvrager namens Proxied MVPD correct te verwerken, en de juiste login ervaring terug te geven. (Deze eigenschap wordt gemarkeerd in de voorbeeldaanvraag hieronder.)

**Opmaak, eigenschap** - Bevat een item IDPEntry dat de specifieke naam MVPD_ID en MVPD bevat.  Dit vertegenwoordigt MVPD die de gebruiker eigenlijk van de plukker van de Programmer selecteerde, en past MVPD_ID aan die in de Dienst van het Web van de Volmacht wordt gespecificeerd.

Er is een extra bereikeigenschap voor RequestorID die kan worden gebruikt om de aanmelding aan te passen aan het specifieke merk van de programmeur (indien nodig). Het kan ook eenvoudig worden gebruikt voor analyses van de oorsprong van het verzoek.

In de reactie van SAML AuthN, zou de Volmacht MVPD Proxied MVPD als Entiteit IdP in de volgende eigenschappen moeten specificeren:

* SAML-uitgever
* Naamkwalificatie


**Voorbeeld AuthN-verzoek**

```XML
<samlp:AuthnRequest
  AssertionConsumerServiceURL="https://sp.auth-staging.adobe.com/sp/saml/SAMLAssertionConsumer"
  Destination="DESTIONATION_URL"
  ForceAuthn="false"
  ID="_4cb70308-b445-462e-b044-f7d0323dde0c"
  IsPassive="false"
  IssueInstant="2012-04-03T15:41:25.884Z"
  ProtocolBinding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"
  Version="2.0"
  xmlns:ds="http://www.w3.org/2000/09/xmldsig#"
  xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol">
    <saml:Issuer xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion">
      https://saml.sp.auth-staging.adobe.com
    </saml:Issuer>
    <ds:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
        ...........
    </ds:Signature>
    <samlp:NameIDPolicy AllowCreate="true"
                        Format="urn:oasis:names:tc:SAML:2.0:nameid-format:persistent"
                        SPNameQualifier="https://saml.sp.auth-staging.adobe.com"
                        xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol" />
    <samlp:Scoping xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol">
        <samlp:IDPList xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol">
            <samlp:IDPEntry Name="MVPD NAME" ProviderID="MVPD_ID"/>
        </samlp:IDPList>
        <samlp:RequesterID xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol">
          RequestorID-Value
        </samlp:RequesterID>
    </samlp:Scoping>
</samlp:AuthnRequest>
```


**Voorbeeld van authN-respons**

```XML
<samlp:Response Destination="https://sp.auth-staging.adobe.com/sp/saml/SAMLAssertionConsumer"
                ID="_1d39be60-66de-012f-bfd5-0030488a31a4"
                InResponseTo="_4cb70308-b445-462e-b044-f7d0323dde0c"
                IssueInstant="2012-04-12T15:00:06Z"
                Version="2.0"
                xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol" >
    <saml:Issuer xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion">ISSUER_VALUE</saml:Issuer>
    <samlp:Status>
        <samlp:StatusCode Value="urn:oasis:names:tc:SAML:2.0:status:Success"/>
    </samlp:Status>
    <saml:Assertion ID="_1d39c280-66de-012f-bfd6-0030488a31a4"
                    IssueInstant="2012-04-12T15:00:06Z"
                    Version="2.0"
                    xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion" >
        <saml:Issuer>ISSUER_VALUE</saml:Issuer>
        <ds:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
            ...........
        </ds:Signature>
        <saml:Subject>
            <saml:NameID Format="urn:oasis:names:tc:SAML:2.0:nameid-format:persistent"
                         NameQualifier="IDP_NameQualifier"
                         SPNameQualifier="https://saml.sp.auth-staging.adobe.com">
                oRD6ALr5jlzkofNR1OaSCDbC6GaXV1cq8gF7Eotf
            </saml:NameID>
            <saml:SubjectConfirmation Method="urn:oasis:names:tc:SAML:2.0:cm:bearer">
                <saml:SubjectConfirmationData
                  InResponseTo="_4cb70308-b445-462e-b044-f7d0323dde0c"
                  NotOnOrAfter="2012-04-12T15:10:06Z"
                  Recipient="https://sp.auth-staging.adobe.com/sp/saml/SAMLAssertionConsumer" />
            </saml:SubjectConfirmation>
        </saml:Subject>
        <saml:Conditions NotBefore="2012-04-12T15:00:06Z"
                         NotOnOrAfter="2012-04-12T15:10:06Z">
            <saml:AudienceRestriction>
                <saml:Audience>https://saml.sp.auth-staging.adobe.com</saml:Audience>
            </saml:AudienceRestriction>
        </saml:Conditions>
        <saml:AuthnStatement AuthnInstant="2012-04-12T15:00:06Z"
                             SessionIndex="f6d15540cf27966115028d35c94eefb9" >
            <saml:AuthnContext>
                <saml:AuthnContextClassRef>urn:oasis:names:tc:SAML:2.0:ac:classes:PasswordProtectedTransport
                </saml:AuthnContextClassRef>
            </saml:AuthnContext>
        </saml:AuthnStatement>
    </saml:Assertion>
</samlp:Response>
```

### Toestemming {#authz-proxy-mvpd-saml-int}

Voor het machtigingsdeel zou het MVPD de door de programmeur gespecificeerde bron voor goedkeuring moeten goedkeuren.  In de meeste gevallen, is dit een koordherkenningsteken voor het kanaalnetwerk, zoals TBS of TNT.

#### SAML-aanvraag en -antwoord voor autorisatie {#authz-saml-req-resp}

In de reactie AuthZ, moet de ISSUER de ISSUER van de Reactie van SAML aanpassen die het Geavanceerd MVPD herkenningsteken zou moeten zijn.

**Voorbeeld van XACML-aanvraag voor AuthZ**

```XML
<?xml version="1.0" encoding="UTF-8"?>
<soap11:Envelope xmlns:soap11="http://schemas.xmlsoap.org/soap/envelope/">
<soap11:Header/>
<soap11:Body>
    <xacml-samlp:XACMLAuthzDecisionQuery
            xmlns:xacml-samlp="urn:oasis:names:tc:xacml:2.0:profile:saml2.0:v2:schema:protocol"
            ID="_c2346a8f2c9cfb205b6b8bf12c2db4d0" IssueInstant="2012-04-12T15:07:51.280Z" Version="2.0">
        <saml:Issuer xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion">https://saml.sp.auth-staging.adobe.com
        </saml:Issuer>
        <ds:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
            <ds:SignedInfo>
                <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
                <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1"/>
                <ds:Reference URI="#_c2346a8f2c9cfb205b6b8bf12c2db4d0">
                    <ds:Transforms>
                        <ds:Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature"/>
                        <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#">
                            <ec:InclusiveNamespaces xmlns:ec="http://www.w3.org/2001/10/xml-exc-c14n#"
                                                    PrefixList="ds saml xacml-context xacml-samlp"/>
                        </ds:Transform>
                    </ds:Transforms>
                    <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
                    <ds:DigestValue>GmEkSZI+SDS1i4vV2ApGh0mx1X4=</ds:DigestValue>
                </ds:Reference>
            </ds:SignedInfo>
            <ds:SignatureValue>..........</ds:SignatureValue>
        </ds:Signature>
        <xacml-context:Request xmlns:xacml-context="urn:oasis:names:tc:xacml:2.0:context:schema:os">          
            <xacml-context:Subject
              SubjectCategory="urn:oasis:names:tc:xacml:1.0:subject-category:access-subject">
                <xacml-context:Attribute
                  AttributeId="urn:oasis:names:tc:xacml:1.0:subject:subject-id"
                  DataType="http://www.w3.org/2001/XMLSchema#string">
                    <xacml-context:AttributeValue
                      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                      xsi:type="xacml-context:AttributeValueType">
                        oRD6ALr5jlzkofNR1OaSCDbC6GaXV1cq8gF7Eotf
                    </xacml-context:AttributeValue>
                </xacml-context:Attribute>
            </xacml-context:Subject>
            <xacml-context:Resource>
                <xacml-context:Attribute
                  AttributeId="urn:oasis:names:tc:xacml:1.0:resource:resource-id"
                  DataType="http://www.w3.org/2001/XMLSchema#string">
                    <xacml-context:AttributeValue
                      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                      xsi:type="xacml-context:AttributeValueType">TBS
                    </xacml-context:AttributeValue>
                </xacml-context:Attribute>
            </xacml-context:Resource>
            <xacml-context:Action>
                <xacml-context:Attribute AttributeId="urn:oasis:names:tc:xacml:1.0:action:action-id"
                                         DataType="http://www.w3.org/2001/XMLSchema#string">
                    <xacml-context:AttributeValue xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                                                  xsi:type="xacml-context:AttributeValueType">VIEW
                    </xacml-context:AttributeValue>
                </xacml-context:Attribute>
            </xacml-context:Action>
            <xacml-context:Environment>
                <xacml-context:Attribute
                  AttributeId="urn:oasis:names:tc:xacml:1.0:subject:authn-locality:ip-address"
                  DataType="urn:oasis:names:tc:xacml:2.0:data-type:ipAddress">
                    <xacml-context:AttributeValue
                      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                      xsi:type="xacml-context:AttributeValueType">127.0.0.1
                    </xacml-context:AttributeValue>
                </xacml-context:Attribute>
            </xacml-context:Environment>
        </xacml-context:Request>
    </xacml-samlp:XACMLAuthzDecisionQuery>
</soap11:Body>
</soap11:Envelope>
```

**Sample AuthZ XACML Response (autorisatie verleend)**

```XML
<?xml version="1.0" encoding="UTF-8"?>
<soap-env:Envelope xmlns:soap-env="http://schemas.xmlsoap.org/soap/envelope/">
    <soap-env:Body>
        <samlp:Response xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol" ID="_311fa030-66df-012f-bfd7-0030488a31a4"
                        IssueInstant="2012-04-12T15:07:49Z" Version="2.0">
            <saml:Issuer xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion">ISSUER</saml:Issuer>
            <samlp:Status>
                <samlp:StatusCode Value="urn:oasis:names:tc:SAML:2.0:status:Success"/>
            </samlp:Status>
            <ds:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
                <ds:SignedInfo>
                    <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
                    <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1"/>
                    <ds:Reference URI="#_311fa030-66df-012f-bfd7-0030488a31a4">
                        <ds:Transforms>
                            <ds:Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature"/>
                            <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
                        </ds:Transforms>
                        <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
                        <ds:DigestValue>2+fDBPYnOT1w5dufJZoVsgckRkM=</ds:DigestValue>
                    </ds:Reference>
                </ds:SignedInfo>
                <ds:SignatureValue>..........</ds:SignatureValue>
                <ds:KeyInfo>
                    <ds:X509Data>
                        <ds:X509Certificate>.........</ds:X509Certificate>
                    </ds:X509Data>
                </ds:KeyInfo>
            </ds:Signature>
            <xacml-samlp:Assertion xmlns:xacml-samlp="urn:oasis:names:tc:SAML:2.0:assertion"
                                   ID="_311fa5a0-66df-012f-bfd8-0030488a31a4" IssueInstant="2012-04-12T15:07:49Z"
                                   Version="2.0">
                <xacml-samlp:Issuer>ISSUER</xacml-samlp:Issuer>
                <xacml-samlp:Conditions NotBefore="2012-04-12T15:07:49Z" NotOnOrAfter="2012-04-13T15:07:49Z">
                    <xacml-samlp:AudienceRestriction>
                        <xacml-samlp:Audience>https://saml.sp.auth-staging.adobe.com</xacml-samlp:Audience>
                    </xacml-samlp:AudienceRestriction>
                </xacml-samlp:Conditions>
                <xacml-saml:XACMLAuthzDecisionStatement
                        xmlns:xacml-saml="urn:oasis:names:tc:xacml:2.0:profile:saml2.0:v2:schema:assertion"
                        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                    <xacml-context:Response xmlns:xacml-context="urn:oasis:names:tc:xacml:2.0:context:schema:os">
                        <xacml-context:Result ResourceId="TBS">
                            <xacml-context:Decision>Permit</xacml-context:Decision>
                        </xacml-context:Result>
                    </xacml-context:Response>
                </xacml-saml:XACMLAuthzDecisionStatement>
            </xacml-samlp:Assertion>
        </samlp:Response>
    </soap-env:Body>
</soap-env:Envelope>
```

**Sample AuthZ XACML Response (Autorisatie geweigerd)**

```XML
<?xml version="1.0" encoding="UTF-8"?>
<soap-env:Envelope xmlns:soap-env="http://schemas.xmlsoap.org/soap/envelope/">
<soap-env:Body>
    <samlp:Response xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol" ID="_69ed8d80-66df-012f-bfda-0030488a31a4"
                    IssueInstant="2012-04-12T15:09:24Z" Version="2.0">
        <saml:Issuer xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion">ISSUER</saml:Issuer>
        <samlp:Status>
            <samlp:StatusCode Value="urn:oasis:names:tc:SAML:2.0:status:Success"/>
        </samlp:Status>
        <ds:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
            <ds:SignedInfo>
                <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
                <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1"/>
                <ds:Reference URI="#_69ed8d80-66df-012f-bfda-0030488a31a4">
                    <ds:Transforms>
                        <ds:Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature"/>
                        <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
                    </ds:Transforms>
                    <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
                    <ds:DigestValue>2SXNFA4pb/283wq5FVQdp4Ms5SQ=</ds:DigestValue>
                </ds:Reference>
            </ds:SignedInfo>
            <ds:SignatureValue>........</ds:SignatureValue>
            <ds:KeyInfo>
                <ds:X509Data>
                    <ds:X509Certificate>........</ds:X509Certificate>
                </ds:X509Data>
            </ds:KeyInfo>
        </ds:Signature>
        <xacml-samlp:Assertion xmlns:xacml-samlp="urn:oasis:names:tc:SAML:2.0:assertion"
                               ID="_69ed91e0-66df-012f-bfdb-0030488a31a4" IssueInstant="2012-04-12T15:09:24Z"
                               Version="2.0">
            <xacml-samlp:Issuer>ISSUER</xacml-samlp:Issuer>
            <xacml-samlp:Conditions NotBefore="2012-04-12T15:09:24Z" NotOnOrAfter="2012-04-13T15:09:24Z">
                <xacml-samlp:AudienceRestriction>
                    <xacml-samlp:Audience>https://saml.sp.auth-staging.adobe.com</xacml-samlp:Audience>
                </xacml-samlp:AudienceRestriction>
            </xacml-samlp:Conditions>
            <xacml-saml:XACMLAuthzDecisionStatement
                    xmlns:xacml-saml="urn:oasis:names:tc:xacml:2.0:profile:saml2.0:v2:schema:assertion"
                    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                <xacml-context:Response xmlns:xacml-context="urn:oasis:names:tc:xacml:2.0:context:schema:os">
                    <xacml-context:Result ResourceId="NOT_Authorized_Resouce">
                        <xacml-context:Decision>Deny</xacml-context:Decision>
                    </xacml-context:Result>
                </xacml-context:Response>
            </xacml-saml:XACMLAuthzDecisionStatement>
        </xacml-samlp:Assertion>
    </samlp:Response>
</soap-env:Body>
</soap-env:Envelope>
```

<!--
>![RelatedInformation]
>* [ProxyMVPD Web Service](/help/authentication/proxy-mvpd-webserv.md)
>* [Service Provider Scoping](/help/authentication/serv-provider-scoping.md)
-->
