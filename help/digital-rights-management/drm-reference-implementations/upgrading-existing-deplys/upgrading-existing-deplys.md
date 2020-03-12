---
description: Als u een server wilt upgraden die versie 3.0 Reference Implementation License Server of Watched Folder Packager ondersteunt, moet u de .war-bestanden die op een toepassingsserver zijn geïmplementeerd vervangen door de bestanden die bij de Adobe Primetime DRM Reference Implementation Server zijn geleverd.
seo-description: Als u een server wilt upgraden die versie 3.0 Reference Implementation License Server of Watched Folder Packager ondersteunt, moet u de .war-bestanden die op een toepassingsserver zijn geïmplementeerd vervangen door de bestanden die bij de Adobe Primetime DRM Reference Implementation Server zijn geleverd.
seo-title: Bestaande implementaties upgraden
title: Bestaande implementaties upgraden
uuid: 1a40aae9-f639-41fa-b42d-cf8cdfcde694
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Overzicht {#upgrade-existing-deployments-overview}

Als u een server wilt upgraden die versie 3.0 Reference Implementation License Server of Watched Folder Packager ondersteunt, moet u de .war-bestanden die op een toepassingsserver zijn geïmplementeerd vervangen door de bestanden die bij de Adobe Primetime DRM Reference Implementation Server zijn geleverd.

Om domeinregistratie met de Server van de Vergunning van de Implementatie van de Verwijzing te gebruiken, worden verscheidene nieuwe gegevensbestandlijsten vereist. U moet het volledige gegevensbestand van de verwijzingsimplementatie opnieuw creëren en lopen `CreateSampleDB.sql`.

Databaserecords behouden en nieuwe tabellen toevoegen:

1. Open `CreateSampleDB.sql` en voer opdrachten uit waarmee de volgende tabellen worden gemaakt:

   * `DomainServerInfo`
   * `DomainKeys`
   * `DomainMembership`
   * `UserDomainMembership`
   * `UserDomainRefCount`

1. Voeg de volgende eigenschappen toe [!DNL flashaccess-refimpl.properties] om de domeinsteun te gebruiken:

   * `HandlerConfiguration.DomainCAs.n` of `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

   * `Domain RegistrationHandler.ServerCredential` en `DomainRegistrationHandler.ServerCredential.password` of `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

   * `DomainRegistrationHandler.DomainServerUrl`

1. Voeg de volgende eigenschappen toe [!DNL flashaccess-refimpl.properties] om levering via externe sleutels aan iOS-clients te ondersteunen:

   * `HandlerConfiguration.KeyServerCertificate` of `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`