---
title: Bestaande implementaties upgraden
description: Bestaande implementaties upgraden
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Bestaande implementaties upgraden {#upgrading-existing-deployments}

Als u een server wilt upgraden waarop de versie 3.0 Reference Implementation License Server of Watched Folder Packager wordt uitgevoerd, vervangt u de [!DNL .war] bestanden die worden geïmplementeerd op uw toepassingsserver met de bestanden die worden geleverd bij de Adobe Access Reference Implementation Server.

Als u domeinregistratie met de Server van de Vergunning van de Implementatie van de Verwijzing van plan bent te gebruiken, worden verscheidene nieuwe gegevensbestandlijsten vereist. Als u de volledige database voor verwijzingsimplementatie opnieuw wilt maken, voert u `CreateSampleDB.sql`. Als u de bestaande databaserecords wilt behouden en de nieuwe tabellen wilt toevoegen, opent u `CreateSampleDB.sql`en voer alleen de opdrachten uit om de volgende tabellen te maken:

* `DomainServerInfo`
* `DomainKeys`
* `DomainMembership`
* `UserDomainMembership`
* `UserDomainRefCount`

De volgende eigenschappen moeten aan flashaccess-refimpl.properties worden toegevoegd om de domeinsteun te gebruiken:

* `HandlerConfiguration.DomainCAs.n` of `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

* `Domain RegistrationHandler.ServerCredential` en `DomainRegistrationHandler.ServerCredential.password`, of `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

* `DomainRegistrationHandler.DomainServerUrl`

De volgende eigenschappen moeten worden toegevoegd aan [!DNL flashaccess-refimpl.properties] voor ondersteuning van levering via een externe sleutel aan iOS-clients:

* `HandlerConfiguration.KeyServerCertificate` of `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`
