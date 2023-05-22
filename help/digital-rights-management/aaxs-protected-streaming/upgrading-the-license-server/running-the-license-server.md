---
description: Als u een server wilt upgraden waarop Adobe Access Server voor beveiligde streaming wordt uitgevoerd, vervangt u het bestand flashaccessserver.war dat op uw toepassingsserver is geïmplementeerd door het bestand dat met de nieuwste Adobe Access is meegeleverd. Als u de nieuwe hierboven beschreven configuratieopties wenst te gebruiken, werk flashaccess-huurder.xml van uw server bij. U moet jsafe.dll of libjsafe.so ook bijwerken naar de versie die bij de nieuwste Adobe Access wordt geleverd.
title: De Adobe Access Server uitvoeren voor beveiligde streaming
exl-id: 02ba87c9-d4ec-4d39-926e-5d98b1858349
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# De Adobe Access Server uitvoeren voor beveiligde streaming{#running-the-adobe-access-server-for-protected-streaming}

Als u een server wilt upgraden waarop Adobe Access Server voor beveiligde streaming wordt uitgevoerd, vervangt u het bestand flashaccessserver.war dat op uw toepassingsserver is geïmplementeerd door het bestand dat met de nieuwste Adobe Access is meegeleverd. Als u de nieuwe hierboven beschreven configuratieopties wenst te gebruiken, werk flashaccess-huurder.xml van uw server bij. U moet jsafe.dll of libjsafe.so ook bijwerken naar de versie die bij de nieuwste Adobe Access wordt geleverd.

Voordat u de Adobe Access Server for Protected Streaming uitvoert, raadt Adobe u aan te controleren of de configuratiebestanden geldig zijn met behulp van de hulpprogramma&#39;s die bij de licentieserver zijn meegeleverd. Zie voor meer informatie &quot;[Configuratie-validatie](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Als u Tomcat en de licentieserver wilt starten, voert u &quot;catalina.bat start&quot; of &quot;catalina.sh start&quot; uit in de directory bin van Tomcat.

Nadat de server is begonnen, verifieer dat het behoorlijk door te openen wordt gevormd *https:// licentie-server-host:poort/flashaccessserver/huurder-name/flashaccess/license/v1* in een browservenster. Als de huurdersconfiguratie met succes werd geladen, wordt een bevestigingsbericht getoond.
