---
title: Aangepast DRM-beleid maken (optioneel)
description: Aangepast DRM-beleid maken (optioneel)
copied-description: true
exl-id: a74f60b1-96a0-4fc4-bbf2-5db78f343562
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Aangepast DRM-beleid maken (optioneel){#create-custom-drm-policies-optional}

De Primetime Cloud DRM Protection Kit wordt geleverd met een paar vooraf geconfigureerde beleidsregels die tijdens het verpakken kunnen worden gebruikt. Als extra beleidsconfiguraties worden gewenst, bijvoorbeeld, een specifiek SWF-toestaat aanbiedingsrecht, kan de inbegrepen Manager van het Beleid van Primetime DRM worden gebruikt om douanebeleid te produceren.

>[!NOTE]
>
>Alle beleidsregels moeten ANONYMOUS-verificatie gebruiken (niet Wachtwoord gebruikersnaam of Aangepast), ongeacht of de workflow Aangepaste verificatie/machtiging wordt gebruikt.

In de beleidsmanager is de [!DNL flashaccesstools.properties] configuratiebestand, dat is gewijzigd om alleen de configureerbare beleidsopties beschikbaar te maken die door de Primetime Cloud DRM-service worden ondersteund. Als u beleidsopties instelt die niet worden ondersteund door de Primetime Cloud DRM-service, worden fouten met licentieverwervingen gegenereerd. Voor informatie over het gebruiken van de Manager van het Beleid Primetime DRM, verwijs naar: [Implementaties van primaire DRM-naslaggids: Beleidsbeheer](https://help.adobe.com/en_US/primetime/drm/5.3/reference_implementations/index.html#concept-DRM_Policy_Manager).

Als u een nieuw beleid wilt maken, werkt u de [!DNL flashaccesstools.properties] en gebruikt u de opdracht:

```
java -jar libs/AdobePolicyManager.jar new myPolicy.pol
```

## Beleid dynamisch maken voor Aangepaste auth/Entitlement{#create-policies-dynamically-for-custom-auth-entitlement}

Als u de Aangepaste verificatie/machtiging van Primetime Cloud DRM gebruikt en u wilt dynamisch een nieuw DRM-beleid maken voor elke licentieaanvraag (in plaats van beleid uit een vooraf gegenereerde pool op te halen), raadt Adobe u aan de Primetime DRM Java SDK rechtstreeks te gebruiken. Het rechtstreeks gebruiken van de SDK van Java is sneller dan [!DNL AdobePolicyManager.jar] -gereedschap, dat het beleidsbestand automatisch naar schijf uitvoert, met I/O-overhead voor de schijf.

Voorbeeldcode met de Java SDK vindt u in het dialoogvenster [!DNL /Primetime DRM PolicyManager/sampleCode/] map, naam [!DNL CreatePolicy.java] en [!DNL CreatePolicyWithOutputProtection.java]. JavaDocs en documentatie voor de Java SDK vindt u op [Een overzicht van de Adobe Primetime DRM SDK](../../../digital-rights-management/drm-sdk-overview/overview.md)

Kopieer de .java-bestanden naar de map ../libs/ en voer deze uit om de voorbeelden te maken en uit te voeren:

```
javac -cp adobe-flashaccess-sdk.jar:. CreatePolicy.java
java -cp adobe-flashaccess-sdk.jar:. CreatePolicy
```
