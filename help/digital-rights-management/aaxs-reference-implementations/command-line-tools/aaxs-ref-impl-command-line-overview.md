---
title: Opdrachtregelprogramma's voor het verpakken van inhoud en het maken van intrekkingslijsten
description: Opdrachtregelprogramma's voor het verpakken van inhoud en het maken van intrekkingslijsten
copied-description: true
exl-id: 34305dab-a2f0-41c2-9a59-3261e8dea7e2
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
* AIR Publisher ID
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

Het standaardconfiguratiebestand is [!DNL flashaccesstools.properties]. Het bevindt zich in de werkmap; Dat wil zeggen, de map waaruit u de gereedschappen uitvoert (zie De opdrachtregelprogramma&#39;s installeren). Elk gereedschap bevat ook een optie ( `-c`) waarmee u naar het configuratiebestand kunt verwijzen dat u wilt gebruiken als u de standaardinstelling niet wilt gebruiken.

Het configuratiebestand gebruikt de bestandsindeling van het Java-eigenschapbestand. Houd rekening met de volgende beperkingen als waarden voor een van de eigenschappen speciale tekens bevatten:

* Escape-backslashes met een extra backslash. Als u bijvoorbeeld de opdracht [!DNL C:\credentials.pfx] bestand, opgeven als [!DNL C:\\credentials.pfx] of `C:/credentials.pfx`. Als u een bestand op een netwerkserver wilt opgeven, geeft u `\\\\server\\folder\\filename.pfx`.
* Het configuratiebestand mag alleen Latijn-1 tekens bevatten. Als u niet-Latin-1-tekens moet gebruiken, gebruikt u de juiste Unicode-escapereeks (waarbij optioneel de opdracht [!DNL native2ascii] die bij Java wordt geleverd).

Stel waarden in voor eigenschappen in het configuratiebestand voordat u de gereedschappen uitvoert. Voor sommige opdrachtregelprogramma&#39;s kunt u de waarden voor bepaalde opties instellen via de opdrachtregel of het configuratiebestand. In die gevallen, nemen de waarden die door de bevellijn worden geplaatst belangrijkheid over om het even welke waarden in het configuratiedossier.

## De opdrachtregelprogramma&#39;s installeren  {#installing-the-command-line-tools}

U kunt de bestanden die u nodig hebt kopiëren uit het dialoogvenster [!DNL \Reference Implementation\Command Line Tools] directory op de dvd, die de standaardinstelling bevat [!DNL flashaccesstools.properties] configuratiebestand en een [!DNL libs] , die de JAR-bestanden voor de gereedschappen bevat.

De [!DNL samples] Deze map bevat verschillende voorbeelden van Java-bronbestanden die het gebruik van de Adobe Access SDK API&#39;s aantonen. Om de steekproeven te bouwen en in werking te stellen, gebruik [!DNL build-samples.xml] Ant-script.
