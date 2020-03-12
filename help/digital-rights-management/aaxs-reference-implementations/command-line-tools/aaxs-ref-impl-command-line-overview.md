---
seo-title: 'Opdrachtregelprogramma''s voor het verpakken van inhoud en het maken van intrekkingslijsten '
title: 'Opdrachtregelprogramma''s voor het verpakken van inhoud en het maken van intrekkingslijsten '
uuid: 2c740521-2004-4320-88e1-118b84e80e31
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d

---


# Opdrachtregelprogramma&#39;s voor het verpakken van inhoud en het maken van intrekkingslijsten {#command-line-tools-for-packaging-content-revocation-lists}

De voorbeeldimplementatie omvat de volgende opdrachtregelprogramma&#39;s:

* Beleidsbeheer: Een hulpmiddel voor het maken en beheren van beleid
* Beheer van lijst met beleidsupdates: Een hulpmiddel om beleidsupdate lijsten te creëren en te bekijken
* Manager intrekkingslijst: Een gereedschap voor het maken en weergeven van intrekkingslijsten
* Media Packager: Een gereedschap voor het maken van gecodeerde FLV- en F4V-bestanden
* AIR Publisher-id
* UtilityLicense Generator
* Licentie insluiten

## Vereisten {#requirements}

De vereisten voor het gebruik van de opdrachtregelprogramma&#39;s die beschikbaar zijn in de referentie-implementaties zijn als volgt:

* Voor alle opdrachtregelprogramma&#39;s is Java 1.5 of hoger vereist.
* De referenties van Packager en License Server (certificaat en wachtwoord) die door Adobe zijn uitgegeven. U hebt referenties nodig om videobestanden te coderen en te ondertekenen, om de lijsten Beleidsupdate en Intrekking te ondertekenen en licenties vooraf te genereren.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Vanwege een Java-bug mogen argumenten die op de opdrachtregel worden gebruikt (zoals bestandsnamen, beleidsnamen of beschrijvingen) alleen tekens uit de standaardtekenset van het besturingssysteem gebruiken.

## Configuratiebestand {#configuration-file}

Verscheidene van de bevel-lijn hulpmiddelen vereisen een configuratiedossier dat informatie voor de hulpmiddelen bevat om voor het toepassen van beleid en het coderen van dossiers te gebruiken.

Het standaardconfiguratiebestand is [!DNL flashaccesstools.properties]. Het bevindt zich in de werkmap; Dat wil zeggen, de map waaruit u de gereedschappen uitvoert (zie De opdrachtregelprogramma&#39;s installeren). Elk gereedschap bevat ook een optie ( `-c`) waarmee u naar het configuratiebestand kunt verwijzen dat u wilt gebruiken als u de standaardinstelling niet wilt gebruiken.

Het configuratiebestand gebruikt de bestandsindeling van het Java-eigenschapbestand. Houd rekening met de volgende beperkingen als waarden voor een van de eigenschappen speciale tekens bevatten:

* Escape-backslashes met een extra backslash. Als u bijvoorbeeld het [!DNL C:\credentials.pfx] bestand wilt opgeven, geeft u het op als [!DNL C:\\credentials.pfx] of `C:/credentials.pfx`. Geef een bestand op een netwerkserver op `\\\\server\\folder\\filename.pfx`.
* Het configuratiebestand mag alleen Latijn-1 tekens bevatten. Als u niet-Latin-1-tekens moet gebruiken, gebruikt u de juiste Unicode-escapereeks (waarbij u optioneel het [!DNL native2ascii] gereedschap gebruikt dat bij Java wordt geleverd).

Stel waarden in voor eigenschappen in het configuratiebestand voordat u de gereedschappen uitvoert. Voor sommige opdrachtregelprogramma&#39;s kunt u de waarden voor bepaalde opties instellen via de opdrachtregel of het configuratiebestand. In die gevallen, nemen de waarden die door de bevellijn worden geplaatst belangrijkheid over om het even welke waarden in het configuratiedossier.

## De opdrachtregelprogramma&#39;s installeren {#installing-the-command-line-tools}

U kunt de gewenste bestanden kopiëren vanuit de [!DNL \Reference Implementation\Command Line Tools] map op de dvd, die het standaardconfiguratiebestand bevat, en vanuit een [!DNL flashaccesstools.properties] [!DNL libs] map met de JAR-bestanden voor de gereedschappen.

De [!DNL samples] map bevat verschillende voorbeelden van Java-bronbestanden die het gebruik van de Adobe Access SDK API&#39;s aantonen. Gebruik het Ant-script om de samples te maken en uit te voeren. [!DNL build-samples.xml]