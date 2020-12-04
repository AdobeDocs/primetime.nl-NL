---
seo-title: 'Opdrachtregelprogramma''s voor het verpakken van inhoud en het maken van intrekkingslijsten '
title: 'Opdrachtregelprogramma''s voor het verpakken van inhoud en het maken van intrekkingslijsten '
uuid: 2c740521-2004-4320-88e1-118b84e80e31
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

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
* De geloofsbrieven van de Server van het pakket en van de Vergunning (certificaat en wachtwoord) die door Adobe worden uitgegeven. U hebt referenties nodig om videobestanden te coderen en te ondertekenen, om de lijsten Beleidsupdate en Intrekking te ondertekenen en licenties vooraf te genereren.

>[!NOTE]
>
>Vanwege een Java-bug mogen argumenten die op de opdrachtregel worden gebruikt (zoals bestandsnamen, beleidsnamen of beschrijvingen) alleen tekens uit de standaardtekenset van het besturingssysteem gebruiken.

## Configuratiebestand {#configuration-file}

Verscheidene van de bevel-lijn hulpmiddelen vereisen een configuratiedossier dat informatie voor de hulpmiddelen bevat om voor het toepassen van beleid en het coderen van dossiers te gebruiken.

Het standaardconfiguratiebestand is [!DNL flashaccesstools.properties]. Het bevindt zich in de werkmap; Dat wil zeggen, de map waaruit u de gereedschappen uitvoert (zie De opdrachtregelprogramma&#39;s installeren). Elk hulpmiddel bevat ook een optie ( `-c`) die u aan het configuratiedossier laat richten u wilt gebruiken als u verkiest niet het gebrek te gebruiken.

Het configuratiebestand gebruikt de bestandsindeling van het Java-eigenschapbestand. Houd rekening met de volgende beperkingen als waarden voor een van de eigenschappen speciale tekens bevatten:

* Escape-backslashes met een extra backslash. Als u bijvoorbeeld het [!DNL C:\credentials.pfx]-bestand wilt opgeven, geeft u dit op als [!DNL C:\\credentials.pfx] of `C:/credentials.pfx`. Als u een bestand op een netwerkserver wilt opgeven, geeft u `\\\\server\\folder\\filename.pfx` op.
* Het configuratiebestand mag alleen Latijn-1 tekens bevatten. Als u niet-Latin-1-tekens moet gebruiken, gebruikt u de juiste Unicode-escapereeks (waarbij u desgewenst het [!DNL native2ascii]-gereedschap gebruikt dat bij Java wordt geleverd).

Stel waarden in voor eigenschappen in het configuratiebestand voordat u de gereedschappen uitvoert. Voor sommige opdrachtregelprogramma&#39;s kunt u de waarden voor bepaalde opties instellen via de opdrachtregel of het configuratiebestand. In die gevallen, nemen de waarden die door de bevellijn worden geplaatst belangrijkheid over om het even welke waarden in het configuratiedossier.

## De opdrachtregelprogramma&#39;s installeren {#installing-the-command-line-tools}

U kunt de bestanden die u nodig hebt kopiëren vanuit de map [!DNL \Reference Implementation\Command Line Tools] op de dvd, die het standaardconfiguratiebestand [!DNL flashaccesstools.properties] bevat, en een map [!DNL libs], die de JAR-bestanden voor de gereedschappen bevat.

De map [!DNL samples] bevat diverse voorbeeld-Java-bronbestanden die het gebruik van de Adobe Access SDK API&#39;s aantonen. Gebruik het Ant-script [!DNL build-samples.xml] om de samples te maken en uit te voeren.