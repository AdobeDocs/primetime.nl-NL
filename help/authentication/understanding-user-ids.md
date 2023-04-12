---
title: Gebruikersnaam
description: Gebruikersnaam
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---


# Gebruikersnaam {#understanding-user-ids}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

Elke gebruiker die een machtigingsstroom start, is gekoppeld aan één unieke gebruikersnaam. Tijdens een machtigingsstroom kan één gebruiker-id echter op verschillende manieren worden weergegeven, afhankelijk van de API waarvan u de id ontvangt.

De `sessionGUID` in de Short Media Token is de beveiligde vorm van de gebruikersnaam, die beschikbaar is via de `sendTrackingData()` vraag. In alle huidige integratie, is dit een blijvende GUID voor de gebruiker over tijd en apparaten. De bron van GUID begint met identiteitskaart van de Gebruiker van de authentificatiereactie die uit MVPD komt. Nochtans, konden sommige MVPDs hun mening in de toekomst veranderen, en beginnen een voorbijgaande GUID te verzenden. Als een programmeur ervoor wil zorgen dat de MVPD-brongebruikersnaam in de AuthN-respons blijvend is, moeten zij daarvoor zorgen in hun overeenkomsten met MVPD&#39;s.

Hier volgen de verschillende manieren waarop de gebruikersnaam wordt weergegeven in de API&#39;s voor Adobe Primetime-verificatie:

| Eigenschap | Doel | Onderbroken | Digitaal ondertekend | Beschrijving |
| --- | --- | --- | --- | --- |
| sendTrackingData() GUID-eigenschap | Tracering/analyse | Ja | Nee | - De MVPD-gebruikersnaam, gehasht door Adobe. De gebruiker-id kan niet worden teruggezet naar de bron van de MVPD. </br> </br> - Deze vorm van identiteitskaart wordt niet digitaal ondertekend, zodat is het niet veilig voor fraudepreventie. Het is echter goed genoeg voor analyses.  </br> </br> - Deze vorm van de Gebruiker - identiteitskaart wordt verstrekt cliënt-kant op alle gebeurtenissen die de authentificatie van Adobe Primetime in de stroom AuthN/AuthZ produceert. |
| Het bezit sessionGUID van het token van korte media | Fraude bijhouden bij gelijktijdig gebruik | Ja | Ja | - Dit is hetzelfde als de gebruikersnaam via sendTrackingData(), maar deze is digitaal ondertekend om de integriteit ervan te beschermen en is goed genoeg om te worden gebruikt voor het bijhouden van fraude. </br> </br> - Het is bedoeld om op de server te worden verwerkt nadat u onze validatiebibliotheek hebt gebruikt en kan worden geanalyseerd op fraudepatronen voordat de videostream aan de client wordt vrijgegeven.  Het uitvoeren van om het even welk van deze taken is aan de Programmer. |
| getMetadata(), eigenschap userID | Account link, fraude-onderzoek met MVPD | Nee | Nee | - This property allows Adobe om de daadwerkelijke bronMVPD Gebruiker - identiteitskaart aan Programmer bloot te stellen. </br> </br> - In Adobe configuratie kan het niet als gecodeerde (afhankelijk van de voorkeur MVPD) worden geplaatst. Als het gecodeerd is, wordt het versleuteld met de openbare sleutel van het certificaat van de programmeur dat aan Adobe is verstrekt, zodat het niet in duidelijke taal aan de client wordt getoond. </br> </br> - Dit geeft de programmeur de daadwerkelijke identiteitskaart van de Gebruiker van MVPD, zodat is het iets dat voor rekening het verbinden of fraudeonderzoek direct met MVPD kan worden gebruikt. |


**Conclusie**

* In het algemeen biedt de MVPD een blijvende unieke id <u>en geeft deze door aan Adobe bij geslaagde verificatie</u>. Het is over het algemeen verenigbaar over alle netwerken. De uitzondering is Comcast MVPD, die een verschillende Gebruiker - identiteitskaart voor elk kanaal verstrekt.

* De MVPD-gebruikersnaam bevat geen PII en is GEEN rekeningnummer. Het hoeft niet in gecodeerde vorm te worden aangeboden, aangezien we met alle MVPD&#39;s hebben gevalideerd die geen PII worden verzonden.

Hoe je de gebruikersnaam gebruikt, hangt af van het gebruik:

* Als u het voor tracking/analytics nodig hebt, kunt u het het best van `sendTrackingData()`.
* Als u het op de server-kant voor stroomversie, fraude, of operationele gegevens nodig hebt, kunt u het van de Symbolische validator krijgen van Media Token.
* Als u het voor rekening het verbinden en diepere fraude nodig hebt, controleer met uw contact van de Adobe voor beschikbaarheid.

