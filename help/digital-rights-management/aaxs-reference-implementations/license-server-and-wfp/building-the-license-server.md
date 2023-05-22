---
title: De licentieserver samenstellen
description: De licentieserver samenstellen
copied-description: true
exl-id: 0535f1e4-9f63-47a0-b55c-45c32ba0d15e
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# De licentieserver samenstellen {#building-the-license-server}

De licentieserver voor de referentie-implementatie bevat WAR-bestanden voor de implementatie van de licentieserver. Het omvat ook alle broncode van de vergunningsserver en een Ant bouwt manuscript (Verwijzing Implementation\Server\refimpl\build-refimpl.xml) zodat kunt u gemakkelijk veranderingen in de code aanbrengen.

>[!NOTE]
>
>Deze stap is alleen nodig als u de broncode wilt wijzigen. Voor evaluatiedoeleinden kunt u deze stap overslaan en de WAR-bestanden gebruiken zoals deze worden verzonden.

Voordat u het Ant-script uitvoert, wijzigt u het script om de locaties van de Adobe Access SDK, Tomcat, MySQL en Log4J op te geven. Open build-refimpl.xml in een teksteditor en bewerk de waarden van de eigenschappen `sdkdir, tomcatdir, mysqldir, and log4jdir`. Als u de broncode wilt compileren en de WAR-bestanden voor de voorbeeldimplementatie wilt maken, voert u het script uit met `ant -f build-refimpl.xml all` in de map met het Ant-script. Wanneer het script is voltooid, wordt een [!DNL refimpl-build/wars] map met de WAR-bestanden van de server wordt gemaakt.
