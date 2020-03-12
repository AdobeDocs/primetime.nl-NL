---
seo-title: Bestaande implementaties upgraden
title: Bestaande implementaties upgraden
uuid: 57e62a88-e541-435c-8274-7f1602548601
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Bestaande implementaties upgraden {#upgrading-existing-deployments}

Als u een server wilt upgraden waarop versie 3.0 Reference Implementation License Server of Watched Folder Packager wordt uitgevoerd, vervangt u de [!DNL .war] bestanden die op uw toepassingsserver zijn geïmplementeerd door de bestanden die bij de Adobe Access Reference Implementation Server zijn geleverd.

Als u domeinregistratie met de Server van de Vergunning van de Implementatie van de Verwijzing van plan bent te gebruiken, worden verscheidene nieuwe gegevensbestandlijsten vereist. Als u de volledige database voor de verwijzingsimplementatie opnieuw wilt maken, voert u deze uit `CreateSampleDB.sql`. Als u de bestaande databaserecords wilt behouden en de nieuwe tabellen wilt toevoegen, opent `CreateSampleDB.sql`en voert u alleen de opdrachten uit om de volgende tabellen te maken:

* `DomainServerInfo`
* `DomainKeys`
* `DomainMembership`
* `UserDomainMembership`
* `UserDomainRefCount`

De volgende eigenschappen moeten aan flashaccess-refimpl.properties worden toegevoegd om de domeinsteun te gebruiken:

* `HandlerConfiguration.DomainCAs.n` of `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

* `Domain RegistrationHandler.ServerCredential` en `DomainRegistrationHandler.ServerCredential.password`, of `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

* `DomainRegistrationHandler.DomainServerUrl`

De volgende eigenschappen moeten worden toegevoegd [!DNL flashaccess-refimpl.properties] om levering via een externe toets aan iOS-clients te ondersteunen:

* `HandlerConfiguration.KeyServerCertificate` of `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`

