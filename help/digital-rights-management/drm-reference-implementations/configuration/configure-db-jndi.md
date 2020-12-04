---
description: 'null'
seo-description: 'null'
seo-title: De database van de licentieserver configureren
title: De database van de licentieserver configureren
uuid: 6d34e849-1616-46bd-ad18-4f98e6c45af7
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---


# De database van de licentieserver configureren{#configure-the-license-server-database}

Om het steekproefgegevensbestand te vormen door opstelling het gegevensbestandschema en het gegevensbestand met steekproefgegevens te bevolken:

1. Breng omhoog de MySQL bevellijn.

   **In Windows** klikt u   **[!UICONTROL Window's Start Menu]** >  **[!UICONTROL MySQL]** >  **[!UICONTROL MySQL Server 5.1]** >  **[!UICONTROL MySQL Command Line Client]**

   **Op Linux, enz.** - Type  `MySQL`.

1. Voer het volgende SQL-script uit:

   mysql> bron &quot;`"[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\createsampledb.sql" dbscript\createsampledb.sql`&quot;

   Met dit script wordt de gebruikersaccount `dbuser` toegevoegd, wordt een verbinding tot stand gebracht via een webtoepassing en wordt een databaseschema gemaakt.

   >[!NOTE]
   >
   >Zorg ervoor dat er geen puntkomma ( `;`) aan het eind van het manuscript is.

1. Bewerk het `PopulateSampleDB.sql`-script dat voorbeeldgegevens in de tabellen vult en gegevens voor uw test opneemt.

   Dit script bevindt zich in de map `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\ dbscript\`.
1. Voer het [!DNL PopulateSampleDB] manuscript uit om de gegevens te bevolken aangezien u in stap 2 deed.

   >[!NOTE]
   >
   >De eerste keer dat u het [!DNL CreateSampleDB.sql] manuscript in werking stelt komt de volgende fout voor:

   U kunt deze fout veilig negeren. Dit gebeurt alleen wanneer u dit script voor de eerste keer uitvoert.

U moet de Pooling van de Verbinding van het Gegevensbestand (DBCP) vormen, die de Jakarta-Commons Groep van de Verbinding van het Gegevensbestand gebruikt. Een JNDI Datasource TestDB wordt gevormd om uit deze verbinding van de toepassingsserver voordeel te halen die pooling. Als u de databaseverbinding wilt wijzigen zodat deze naar een MySQL-server verwijst die zich niet op localhost bevindt, wijzigt u een van de volgende bestanden:

* Het [!DNL META-INF\context.xml]-bestand, dat de locatie, gebruikersnaam en wachtwoord opgeeft van de database van de licentieserver in het [!DNL flashaccess.war]-bestand.

* Het `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl\WebContent/META-INF\context.xml`-bestand.

en maak het WAR-bestand opnieuw met de bijgewerkte bestanden.

Als u een van deze parameters wilt wijzigen, bewerkt u het [!DNL context.xml]-bestand in de map [!DNL WebContent] en maakt u het WAR-bestand opnieuw met het Ant-script. Om het gegevensbestand te stemmen, verander de JNDI gegevensbronmontages in dit dossier.

Als u het project van de Implementatie van de Verwijzing in Verduistering zuivert, voeg `$CATALINA_HOME\lib\tomcat-dbcp.jar` aan uw looppas/zuivert configuratie toe.

>[!NOTE]
>
>Als u het [!DNL flashaccess.war] dossier op een standalone server van Tomcat 6.0 in werking stelt, wordt deze stap niet vereist.

