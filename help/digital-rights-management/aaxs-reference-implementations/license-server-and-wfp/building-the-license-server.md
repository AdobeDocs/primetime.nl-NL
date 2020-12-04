---
seo-title: De licentieserver samenstellen
title: De licentieserver samenstellen
uuid: d7ca8a8f-c778-41a2-b823-93fac9ab07c5
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# De licentieserver {#building-the-license-server} samenstellen

De licentieserver voor de referentie-implementatie bevat WAR-bestanden voor de implementatie van de licentieserver. Het omvat ook alle broncode van de vergunningsserver en een Ant bouwt manuscript (Verwijzing Implementation\Server\refimpl\build-refimpl.xml) zodat kunt u gemakkelijk veranderingen in de code aanbrengen.

>[!NOTE]
>
>Deze stap is alleen nodig als u de broncode wilt wijzigen. Voor evaluatiedoeleinden kunt u deze stap overslaan en de WAR-bestanden gebruiken zoals deze worden verzonden.

Voordat u het Ant-script uitvoert, wijzigt u het script om de locaties van de Adobe Access SDK, Tomcat, MySQL en Log4J op te geven. Open build-refimpl.xml in een teksteditor en bewerk de waarden van de eigenschappen `sdkdir, tomcatdir, mysqldir, and log4jdir`. Als u de broncode wilt compileren en de WAR-bestanden voor de referentie-implementatie wilt maken, voert u het script uit met `ant -f build-refimpl.xml all` in de map met het Ant-script. Wanneer het script is voltooid, wordt een map [!DNL refimpl-build/wars] gemaakt die de WAR-bestanden van de server bevat.
