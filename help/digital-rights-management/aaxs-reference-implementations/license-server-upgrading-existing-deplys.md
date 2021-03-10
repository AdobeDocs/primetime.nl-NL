---
title: Bestaande implementaties upgraden
description: Bestaande implementaties upgraden
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Bestaande implementaties upgraden {#upgrading-existing-deployments}

Als u een server wilt upgraden waarop versie 3.0 Reference Implementation License Server of Watched Folder Packager wordt uitgevoerd, vervangt u de [!DNL .war]-bestanden die op uw toepassingsserver zijn geïmplementeerd door de bestanden die bij de Adobe Access Reference Implementation Server zijn geleverd.

Als u domeinregistratie met de Server van de Vergunning van de Implementatie van de Verwijzing van plan bent te gebruiken, worden verscheidene nieuwe gegevensbestandlijsten vereist. Als u de volledige database voor de implementatie van verwijzingen opnieuw wilt maken, voert u `CreateSampleDB.sql` uit. Als u de bestaande databaserecords wilt behouden en de nieuwe tabellen wilt toevoegen, opent u `CreateSampleDB.sql`en voert u alleen de opdrachten uit om de volgende tabellen te maken:

* `DomainServerInfo`
* `DomainKeys`
* `DomainMembership`
* `UserDomainMembership`
* `UserDomainRefCount`

De volgende eigenschappen moeten aan flashaccess-refimpl.properties worden toegevoegd om de domeinsteun te gebruiken:

* `HandlerConfiguration.DomainCAs.n` of  `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

* `Domain RegistrationHandler.ServerCredential` en  `DomainRegistrationHandler.ServerCredential.password`, of  `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

* `DomainRegistrationHandler.DomainServerUrl`

De volgende eigenschappen moeten aan [!DNL flashaccess-refimpl.properties] worden toegevoegd om levering op een externe toets aan iOS-clients te ondersteunen:

* `HandlerConfiguration.KeyServerCertificate` of  `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`

