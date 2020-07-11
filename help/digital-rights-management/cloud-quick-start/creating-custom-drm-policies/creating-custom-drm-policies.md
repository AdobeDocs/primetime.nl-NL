---
seo-title: Aangepast DRM-beleid maken (optioneel)
title: Aangepast DRM-beleid maken (optioneel)
uuid: 701b51d9-6dde-4c21-bc5b-09e612582968
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# Aangepast DRM-beleid maken (optioneel){#create-custom-drm-policies-optional}

De Primetime Cloud DRM Protection Kit wordt geleverd met een paar vooraf geconfigureerde beleidsregels die tijdens het verpakken kunnen worden gebruikt. Als extra beleidsconfiguraties worden gewenst, bijvoorbeeld, een specifiek SWF-allow aanbiedingsrecht, kan de inbegrepen Manager van het Beleid van Primetime DRM worden gebruikt om douanebeleid te produceren.

>[!NOTE]
>
>Alle beleidsregels moeten ANONYMOUS-verificatie gebruiken (niet Wachtwoord gebruikersnaam of Aangepast), ongeacht of de workflow Aangepaste controle/machtiging wordt gebruikt.

Bij de Manager van het Beleid wordt inbegrepen is het [!DNL flashaccesstools.properties] configuratiedossier, dat is gewijzigd om slechts de configureerbare beleidsopties bloot te stellen die de Dienst van de Wolk DRM steunt. Als u beleidsopties instelt die niet worden ondersteund door de Primetime Cloud DRM-service, worden fouten met licentieverwervingen gegenereerd. Voor informatie over het gebruiken van de Manager van het Beleid Primetime DRM, verwijs naar: [Implementaties van primaire DRM-naslaggids: Beleidsbeheer](https://help.adobe.com/en_US/primetime/drm/5.3/reference_implementations/index.html#concept-DRM_Policy_Manager).

Als u een nieuw beleid wilt maken, werkt u het [!DNL flashaccesstools.properties] bestand naar wens bij en gebruikt u de opdracht:

```
java -jar libs/AdobePolicyManager.jar new myPolicy.pol
```

## Beleid dynamisch maken voor Aangepaste auth/Entitlement{#create-policies-dynamically-for-custom-auth-entitlement}

Als u Primetime Cloud DRM Custom Authentication/Entitlement gebruikt en u wilt dynamisch een nieuw DRM-beleid maken voor elke licentieaanvraag (in plaats van beleidsregels uit een vooraf gegenereerde pool op te halen), raadt Adobe u aan de Primetime DRM Java SDK rechtstreeks te gebruiken. Het rechtstreeks gebruiken van de SDK van Java is sneller dan het [!DNL AdobePolicyManager.jar] hulpmiddel, dat automatisch het beleidsdossier aan schijf uitzet, die schijf I/O overheadkosten.

Voorbeeldcode met de Java SDK vindt u in de [!DNL /Primetime DRM PolicyManager/sampleCode/] map met de naam [!DNL CreatePolicy.java] en [!DNL CreatePolicyWithOutputProtection.java]. JavaDocs en documentatie voor de Java SDK vindt u in [Een overzicht van de Adobe Primetime DRM SDK](../../../digital-rights-management/drm-sdk-overview/overview.md)

Kopieer de .java-bestanden naar de map ../libs/ en voer deze uit om de voorbeelden te maken en uit te voeren:

```
javac -cp adobe-flashaccess-sdk.jar:. CreatePolicy.java
java -cp adobe-flashaccess-sdk.jar:. CreatePolicy
```
