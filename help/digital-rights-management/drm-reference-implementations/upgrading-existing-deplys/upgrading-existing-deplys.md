---
description: Als u een server wilt upgraden die versie 3.0 Reference Implementation License Server of Watched Folder Packager ondersteunt, moet u de .war-bestanden die zijn geïmplementeerd op een toepassingsserver vervangen door de bestanden die zijn opgenomen met de Adobe Primetime DRM Reference Implementation Server.
title: Bestaande implementaties upgraden
exl-id: 83edaf0a-e527-470d-8b8d-23e5ba86b039
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Overzicht {#upgrade-existing-deployments-overview}

Als u een server wilt upgraden die versie 3.0 Reference Implementation License Server of Watched Folder Packager ondersteunt, moet u de .war-bestanden die zijn geïmplementeerd op een toepassingsserver vervangen door de bestanden die zijn opgenomen met de Adobe Primetime DRM Reference Implementation Server.

Om domeinregistratie met de Server van de Vergunning van de Implementatie van de Verwijzing te gebruiken, worden verscheidene nieuwe gegevensbestandlijsten vereist. U moet het volledige gegevensbestand van de verwijzingsimplementatie opnieuw creëren en in werking stellen `CreateSampleDB.sql`.

Databaserecords behouden en nieuwe tabellen toevoegen:

1. Openen `CreateSampleDB.sql` en voer opdrachten uit die de volgende tabellen maken:

   * `DomainServerInfo`
   * `DomainKeys`
   * `DomainMembership`
   * `UserDomainMembership`
   * `UserDomainRefCount`

1. Voeg de volgende eigenschappen toe aan [!DNL flashaccess-refimpl.properties] om de domeinsteun te gebruiken:

   * `HandlerConfiguration.DomainCAs.n` of `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

   * `Domain RegistrationHandler.ServerCredential` en `DomainRegistrationHandler.ServerCredential.password` of `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

   * `DomainRegistrationHandler.DomainServerUrl`

1. Voeg de volgende eigenschappen toe aan [!DNL flashaccess-refimpl.properties] voor ondersteuning van levering via een externe sleutel aan iOS-clients:

   * `HandlerConfiguration.KeyServerCertificate` of `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`
