---
description: Met informatie over verpakking en bescherming van inhoud kunt u uw inhoud beschermen.
seo-description: Met informatie over verpakking en bescherming van inhoud kunt u uw inhoud beschermen.
seo-title: Inhoud verpakken en beschermen
title: Inhoud verpakken en beschermen
uuid: 9bf89f86-082e-40f9-8deb-c9774a9d8e02
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---


# Inhoud verpakken en beveiligen {#packaging-protecting-content}

Met informatie over verpakking en bescherming van inhoud kunt u uw inhoud beschermen.

## De server {#securing-the-server} beveiligen

U moet de computer fysiek beveiligen waarop beleidsbeheer en inhoudspakketten plaatsvinden.

Voor meer informatie, zie [Fysieke veiligheid en toegang](../../secure-deployment-guidelines/physical-sec-and-access.md).

Als uw implementatie van het verpakken van inhoud netwerkconnectiviteit vereist, moet u uw werkend systeem hard maken en een aangewezen firewalloplossing uitvoeren. Voor meer informatie, zie [Netwerktopologie](../../secure-deployment-guidelines/overview/network-topology.md).

## Inhoud {#securely-packaging-content} op veilige wijze verpakken

Voor het configuratiebestand voor het opdrachtregelprogramma Adobe Primetime DRM Media Packager is een PKCS12-referentie vereist die tijdens het verpakken wordt gebruikt.

In de bevel-tijdehulpmiddelen van de Implementatie van de Verwijzing, wordt het wachtwoord voor het PKCS12 geloofsbrieven dossier opgeslagen in het `flashaccess.properties` dossier in duidelijke teksten. Daarom moet u extra voorzichtig zijn wanneer u de computer beveiligt waarop dit bestand wordt gehost en zorgt u ervoor dat de computer zich in een veilige omgeving bevindt. Voor meer informatie, zie [Fysieke veiligheid en toegang](../../secure-deployment-guidelines/physical-sec-and-access.md).

De verpakker gebruikt ook de certificaten van het Vervoer van de Server van de Vergunning en van de Server van de Vergunning, en de integriteit en de vertrouwelijkheid van deze informatie moeten worden beschermd. Alleen bevoegde entiteiten mogen de verpakker gebruiken. Als uw persoonlijke sleutels worden gecompromitteerd, informeer Adobe Systems Incorporated onmiddellijk zodat het certificaat kan worden ingetrokken.

>[!NOTE]
>
>Met de API kunt u dezelfde sleutel gebruiken voor meerdere inhoud. Om het hoogste niveau van veiligheid te verzekeren, zou u deze eigenschap slechts voor multi-beetjetarief FMS inhoud moeten gebruiken. Gebruik niet dezelfde sleutel voor meerdere bestanden die verschillende inhoud vertegenwoordigen.

De Primetime DRM Packaging-API geeft onder bepaalde omstandigheden waarschuwingen weer. Controleer deze waarschuwingen om te bepalen of uw bestanden zijn versleuteld. De waarschuwingsberichten kunnen een van de volgende zijn:

* Het beleid is verlopen en een niet-herkende tag of track kan niet worden gecodeerd.
* Filmfragmenten kunnen niet worden gecodeerd en verwijzingen in die fragmenten kunnen ongeldig zijn.
* Metagegevens kunnen niet worden gecodeerd.

Als inhoud wordt verpakt door een beleid met onjuiste kenmerken te gebruiken, moet het beleid worden bijgewerkt. Het bijgewerkte beleid moet aan de Server van de Vergunning door een lijst van de beleidsupdate of een ander leveringsmechanisme ter beschikking worden gesteld. Sommige beleidskenmerken kunnen niet worden gewijzigd nadat het beleid is gemaakt. Als deze kenmerken onjuist zijn, trekt u de inhoud terug van de distributieplaatsen, trekt u het beleid in zodat geen toekomstige licenties kunnen worden verleend, en versleutelt u de inhoud opnieuw.

Wanneer het verpakken volledig is, wordt de verpakkingssleutel huisvuil-verzameld, en niet uitdrukkelijk vernietigd. Hierdoor blijft de verpakkingssleutel enige tijd in het geheugen aanwezig. U moet ervoor zorgen dat u geen ongeoorloofde toegang tot de computer hebt en dat u geen bestanden, zoals kerndumpen, weergeeft die deze informatie kunnen weergeven.

## Beleid {#securely-storing-policies} veilig opslaan

Met de Adobe Primetime DRM SDK kunt u toepassingen ontwikkelen die kunnen worden gebruikt in het verpakken van inhoud en het maken van beleid.

Wanneer u deze toepassingen maakt, kunt u toestaan dat sommige gebruikers beleid maken en wijzigen en andere gebruikers beperken tot het toepassen van bestaand beleid op de inhoud. U moet de noodzakelijke toegangscontroles uitvoeren en gebruikersrekeningen met verschillende voorrechten voor beleidsverwezenlijking en beleidstoepassing creëren.

Het beleid wordt pas ondertekend of tegen wijzigingen beschermd als het in een pakket wordt gebruikt. Als u zich zorgen maakt dat gebruikers van verpakkingsgereedschappen beleid kunnen wijzigen, ondertekent u het beleid om ervoor te zorgen dat het beleid niet kan worden gewijzigd.

Zie de API&#39;s voor primetime DRM op [API-referenties voor primetime](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References) voor meer informatie over het maken van toepassingen met de SDK.

## Asymmetrische sleutelversleuteling {#asymmetric-key-encryption}

Bij asymmetrische sleutelversleuteling, ook wel versleuteling met een openbare sleutel genoemd, worden sleutelparen gebruikt. De ene sleutel is voor versleuteling, de andere is voor ontsleuteling.

De decryptiesleutel, of *`private key`*, wordt geheim gehouden; de coderingssleutel, of de *`public key`*, wordt beschikbaar gesteld aan iedereen die gemachtigd is om inhoud te coderen. Iedereen met toegang tot de openbare sleutel kan inhoud coderen. Nochtans, slechts kan iemand met toegang tot de privé sleutel de inhoud decrypteren. De persoonlijke sleutel kan niet opnieuw worden opgebouwd op basis van de openbare sleutel.

Wanneer u inhoud verpakt, wordt de openbare sleutel van de Server van de Vergunning gebruikt om de sleutel van de inhoudsencryptie (CEK) in de meta-gegevens te coderen DRM. U moet ervoor zorgen dat alleen de licentieserver toegang heeft tot de persoonlijke sleutel van de licentieserver. Als iemand anders over de sleutel beschikt, kan hij of zij de inhoud decoderen en bekijken.

>[!CAUTION]
>
>Zorg ervoor dat u het certificaat van de Server van de Vergunning verkrijgt dat de openbare sleutel van een vertrouwde bron omvat. Op deze manier kunt u ervoor zorgen dat het de sleutel van de Server van de Vergunning en niet een schurken openbare sleutel is. Als aanvallers hun openbare sleutel voor de sleutel van de Server van de Vergunning moesten vervangen, konden zij uw inhoud decrypteren.

Zie [De Adobe Primetime DRM SDK gebruiken voor het beveiligen van inhoud](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_protecting_content.pdf) voor meer informatie over het verpakken van inhoud.