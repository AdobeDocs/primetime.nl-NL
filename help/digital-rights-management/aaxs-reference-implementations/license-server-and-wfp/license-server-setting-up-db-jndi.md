---
title: De database instellen en de JNDI-gegevensbron configureren
description: De database instellen en de JNDI-gegevensbron configureren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# De database instellen en de JNDI-gegevensbron configureren {#setting-up-the-database-and-configuring-the-jndi-datasource}

Voor de licentieserver voor de voorbeeldimplementatie is een database nodig die de volgende functies ondersteunt:

* Gebruikersverificatie
* Gebruikersmodel demo bedrijfsregels
* Metagegevensomzetting
* Domeinondersteuning

Voor anonieme licentieaanschaf is geen database vereist.

>[!NOTE]
>
>De instructies in deze sectie gelden voor het Microsoft Windows-platform. Voor andere besturingssystemen raadpleegt u de documentatie bij uw besturingssysteem of raadpleegt u de MySQL-documentatie.

Als u de licentieserver wilt uitvoeren, moet u MySQL 5.1.34 installeren en configureren:

1. Voer het MySQL-installatieprogramma uit (in de map Derde Party\MySQL\Installer\5.1 op de dvd).
1. Aan het eind van de installatieprocedure, controleer **[!UICONTROL Configure MySQL Server Now]** om de configuratietovenaar te beginnen. Gebruik de standaardinstellingen of selecteer specifieke instellingen voor uw testdoeleinden, behalve dat u op het vijfde scherm **[!UICONTROL Online Transaction Processing (OLTP)]** of **[!UICONTROL Manual Setting]** moet selecteren en het maximale aantal toegestane verbindingen moet invoeren.

1. Noteer het hoofdwachtwoord.
1. Als u MySQL opnieuw moet installeren, voert u de volgende stappen uit om problemen bij het starten van de server achteraf te voorkomen:

   * Verwijder de map *systeemstation:* [!DNL \Documents and Settings\All Users\Application Data\MySQL].

   * Verwijder de oude installatiemap voor MySQL: bijvoorbeeld *systeemstation:* [!DNL \Program Files\MySQL\MySQL Server 5.1].

Vervolgens moet u MySQL JDBC Driver 5.1.7 installeren. Hiervoor kopieert u [!DNL mysql-connector-java-5.1.7-bin.jar] (in de map [!DNL Third Party\MySQL\Installer\5.1] op de dvd) naar de directory Tomcat Server lib: [!DNL ...\Tomcat6.0\lib].

>[!NOTE]
>
>MySQL JDBC Driver 5.1.7 werkt met Tomcat 6.0. Oudere versies van Tomcat worden niet ondersteund.

Stel de voorbeelddatabase in door het databaseschema in te stellen en de database te vullen met voorbeeldgegevens. Voer hiertoe de volgende stappen uit:

1. Ga naar **[!UICONTROL Window's Start Menu]** > **[!UICONTROL MySQL]** > **[!UICONTROL MySQL Server 5.1]** > **[!UICONTROL MySQL Command Line Client]**.
1. Nadat u het wachtwoord hebt ingevoerd, voert u het volgende SQL-script uit om de gebruikersaccount `dbuser` toe te voegen voor het tot stand brengen van een verbinding via een webtoepassing en maakt u een databaseschema (zorg ervoor dat er geen &quot;;&quot; is aan het einde. Druk gewoon op Enter.)

   ```
       mysql> source “Reference Implementation\Server\dbscript\createsampledb.sql”
   ```

1. Bewerk het script waarmee voorbeeldgegevens in de tabellen worden ingevuld en voeg gegevens voor testdoeleinden toe: [!DNL Reference Implementation\Server\dbscript\PopulateSampleDB.sql].
1. Voer dit manuscript uit om de gegevens te bevolken aangezien u in Stap 2 deed.

>[!NOTE]
>
>De eerste keer dat u het [!DNL CreateSampleDB.sql]-script uitvoert, wordt de volgende fout weergegeven:

*FOUT 1396 (HY000): Operation DROP USER failed for &#39;dbuser&#39;@&#39;localhost&#39; Query OK, 0 rows affected (0,00 sec).*

U kunt deze fout veilig negeren. Dit gebeurt alleen de eerste keer dat u dit script uitvoert.

Op dit punt zult u het Pooling van de Verbinding van het Gegevensbestand (DBCP) moeten vormen. DBCP gebruikt de Jakarta-Commons Groep van de Verbinding van het Gegevensbestand. Een JNDI Datasource TestDB wordt gevormd om uit deze verbinding van de toepassingsserver voordeel te halen die pooling. Als u de databaseverbinding wilt wijzigen zodat deze naar een MySQL-server verwijst die zich niet op de localhost bevindt, wijzigt u het [!DNL META-INF\context.xml]-bestand (dat de locatie, gebruikersnaam en het wachtwoord van de database van de licentieserver opgeeft) in [!DNL flashaccess.war] of wijzigt u [!DNL \Reference Implementation\Server\refimpl\WebContent\META-INF\context.xml] en maakt u het WAR-bestand opnieuw met de bijgewerkte bestanden. Als u een van deze parameters wilt wijzigen, bewerkt u [!DNL context.xml] in de map WebContent en maakt u het WAR-bestand opnieuw met het Ant-script. Om het gegevensbestand te stemmen, verander de JNDI gegevensbronmontages in dit dossier.

Als u het project van de Implementatie van de Verwijzing binnen Verduistering zuivert, moet u `$CATALINA_HOME\lib\tomcat-dbcp.jar` aan uw looppas/zuivert configuratie toevoegen. Deze stap is niet vereist als u het [!DNL flashaccess.war]-bestand op een zelfstandige Tomcat 6.0-server uitvoert.
