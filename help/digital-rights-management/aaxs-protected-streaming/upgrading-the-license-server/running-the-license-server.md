---
description: Als u een server wilt upgraden waarop Adobe Access Server voor beveiligde streaming wordt uitgevoerd, vervangt u het bestand flashaccessserver.war dat op uw toepassingsserver is geïmplementeerd door het bestand dat met de nieuwste Adobe Access is meegeleverd. Als u de nieuwe hierboven beschreven configuratieopties wenst te gebruiken, werk flashaccess-huurder.xml van uw server bij. U moet jsafe.dll of libjsafe.so ook bijwerken naar de versie die bij de nieuwste Adobe Access wordt geleverd.
title: De Adobe Access Server uitvoeren voor beveiligde streaming
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# Adobe Access Server uitvoeren voor beveiligde streaming{#running-the-adobe-access-server-for-protected-streaming}

Als u een server wilt upgraden waarop Adobe Access Server voor beveiligde streaming wordt uitgevoerd, vervangt u het bestand flashaccessserver.war dat op uw toepassingsserver is geïmplementeerd door het bestand dat met de nieuwste Adobe Access is meegeleverd. Als u de nieuwe hierboven beschreven configuratieopties wenst te gebruiken, werk flashaccess-huurder.xml van uw server bij. U moet jsafe.dll of libjsafe.so ook bijwerken naar de versie die bij de nieuwste Adobe Access wordt geleverd.

Voordat u de Adobe Access Server for Protected Streaming uitvoert, raadt Adobe u aan te controleren of de configuratiebestanden geldig zijn met behulp van de hulpprogramma&#39;s die bij de licentieserver zijn meegeleverd. Voor meer details, zie &quot;[Validator van de Configuratie](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Als u Tomcat en de licentieserver wilt starten, voert u &quot;catalina.bat start&quot; of &quot;catalina.sh start&quot; uit in de directory bin van Tomcat.

Nadat de server is begonnen, verifieer dat het behoorlijk door *https:// vergunning-server-gastheer:haven/flashaccessserver/huurder-name/flashaccess/license/v1* in een browser venster te openen wordt gevormd. Als de huurdersconfiguratie met succes werd geladen, wordt een bevestigingsbericht getoond.
