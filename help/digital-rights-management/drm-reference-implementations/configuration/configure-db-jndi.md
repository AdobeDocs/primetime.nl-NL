---
title: De database van de licentieserver configureren
description: De database van de licentieserver configureren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# De database van de licentieserver configureren{#configure-the-license-server-database}

Om het steekproefgegevensbestand te vormen door opstelling het gegevensbestandschema en het gegevensbestand met steekproefgegevens te bevolken:

1. Breng omhoog de MySQL bevellijn.

   **In Windows -** Klikken  **[!UICONTROL Window's Start Menu]** > **[!UICONTROL MySQL]** > **[!UICONTROL MySQL Server 5.1]** > **[!UICONTROL MySQL Command Line Client]**

   **Op Linux, enz.** - Type `MySQL`.

1. Voer het volgende SQL-script uit:

   mysql> bron &quot; `"[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\createsampledb.sql" dbscript\createsampledb.sql`&quot;

   Met dit script wordt de gebruikersaccount toegevoegd `dbuser`, maakt een verbinding via een webtoepassing en maakt een databaseschema.

   >[!NOTE]
   >
   >Zorg ervoor dat er geen puntkomma ( `;`) aan het einde van het script.

1. Bewerk de `PopulateSampleDB.sql` script dat voorbeeldgegevens in de tabellen vult om gegevens voor uw tests op te nemen.

   Dit script bevindt zich in het dialoogvenster `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\ dbscript\` map.
1. Voer de [!DNL PopulateSampleDB] gebruiken om de gegevens te vullen zoals u in stap 2 hebt gedaan.

   >[!NOTE]
   >
   >De eerste keer dat u de [!DNL CreateSampleDB.sql] script uitvoeren, treedt de volgende fout op:

   U kunt deze fout veilig negeren. Dit gebeurt alleen wanneer u dit script voor de eerste keer uitvoert.

U moet de Pooling van de Verbinding van het Gegevensbestand (DBCP) vormen, die de Jakarta-Commons Groep van de Verbinding van het Gegevensbestand gebruikt. Een JNDI Datasource TestDB wordt gevormd om uit deze verbinding van de toepassingsserver voordeel te halen die pooling. Als u de databaseverbinding wilt wijzigen zodat deze naar een MySQL-server verwijst die zich niet op localhost bevindt, wijzigt u een van de volgende bestanden:

* De [!DNL META-INF\context.xml] bestand, dat de locatie, gebruikersnaam en het wachtwoord opgeeft van de database van de licentieserver die zich in de [!DNL flashaccess.war] bestand.

* De `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl\WebContent/META-INF\context.xml` bestand.

en maak het WAR-bestand opnieuw met de bijgewerkte bestanden.

Als u een van deze parameters wilt wijzigen, bewerkt u de opdracht [!DNL context.xml] in het [!DNL WebContent] en gebruik het Ant-script om het WAR-bestand opnieuw te maken. Om het gegevensbestand te stemmen, verander de JNDI gegevensbronmontages in dit dossier.

Als u fouten opspoort in het project Referentie-implementatie in Eclipse, voegt u `$CATALINA_HOME\lib\tomcat-dbcp.jar` aan uw looppas/zuivert configuratie.

>[!NOTE]
>
>Als u de [!DNL flashaccess.war] op een zelfstandige Tomcat 6.0-server. Deze stap is niet vereist.
