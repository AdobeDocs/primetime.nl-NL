---
description: Als u een server wilt upgraden waarop Adobe Access Server voor beveiligde streaming wordt uitgevoerd, vervangt u het bestand flashaccessserver.war dat op uw toepassingsserver is geïmplementeerd door het bestand dat bij de nieuwste Adobe Access is geleverd. Als u de nieuwe hierboven beschreven configuratieopties wenst te gebruiken, werk flashaccess-huurder.xml van uw server bij. U moet jsafe.dll of libjsafe.so ook bijwerken naar de versie die bij de nieuwste Adobe Access wordt geleverd.
seo-description: Als u een server wilt upgraden waarop Adobe Access Server voor beveiligde streaming wordt uitgevoerd, vervangt u het bestand flashaccessserver.war dat op uw toepassingsserver is geïmplementeerd door het bestand dat bij de nieuwste Adobe Access is geleverd. Als u de nieuwe hierboven beschreven configuratieopties wenst te gebruiken, werk flashaccess-huurder.xml van uw server bij. U moet jsafe.dll of libjsafe.so ook bijwerken naar de versie die bij de nieuwste Adobe Access wordt geleverd.
seo-title: De Adobe Access-server voor beveiligde streaming uitvoeren
title: De Adobe Access-server voor beveiligde streaming uitvoeren
uuid: 3819500d-ad2f-49eb-8aa4-e50a55461608
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# De Adobe Access-server voor beveiligde streaming uitvoeren{#running-the-adobe-access-server-for-protected-streaming}

Als u een server wilt upgraden waarop Adobe Access Server voor beveiligde streaming wordt uitgevoerd, vervangt u het bestand flashaccessserver.war dat op uw toepassingsserver is geïmplementeerd door het bestand dat bij de nieuwste Adobe Access is geleverd. Als u de nieuwe hierboven beschreven configuratieopties wenst te gebruiken, werk flashaccess-huurder.xml van uw server bij. U moet jsafe.dll of libjsafe.so ook bijwerken naar de versie die bij de nieuwste Adobe Access wordt geleverd.

Voordat u de Adobe Access-server voor beveiligde streaming uitvoert, raadt Adobe u aan te controleren of de configuratiebestanden geldig zijn met behulp van de hulpprogramma&#39;s die bij de licentieserver zijn meegeleverd. Voor meer details, zie &quot;Validator[van de](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)Configuratie&quot;.

Als u Tomcat en de licentieserver wilt starten, voert u &quot;catalina.bat start&quot; of &quot;catalina.sh start&quot; uit in de directory bin van Tomcat.

Nadat de server is begonnen, verifieer dat het behoorlijk door *https:// vergunning-server-gastheer:haven/flashaccessserver/huurder-naam/flashaccess/license/v1* in een browser venster te openen wordt gevormd. Als de huurdersconfiguratie met succes werd geladen, wordt een bevestigingsbericht getoond.
