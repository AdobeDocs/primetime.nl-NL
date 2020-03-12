---
seo-title: Overzicht
title: Overzicht
uuid: 7363d241-6947-4a9c-80e5-e50be71066b9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Overzicht {#overview}

Met Adobe® Access™ kunnen inhoudsproviders beleid toepassen op mediabestanden. Met behulp van de API&#39;s voor beleidsbeheer kunnen beheerders beleidsregels maken, weergeven en bijwerken.

Een *beleid* bepaalt hoe de gebruikers inhoud kunnen bekijken; het is een verzameling informatie die beveiligingsinstellingen, verificatievereisten en gebruiksrechten bevat. Wanneer beleid wordt toegepast, staan de encryptie en de ondertekening inhoudsleveranciers toe om controle van hun inhoud te handhaven ongeacht hoe breed het wordt verdeeld. Beveiligde bestanden kunnen worden geleverd met Adobe® Flash® Media Server of een HTTP-server. Ze kunnen worden gedownload en afgespeeld in aangepaste spelers die zijn gemaakt met Adobe® AIR®, Adobe® Flash® Player en Adobe® Primetime SDK voor iOS. Het beleid is een malplaatje voor de vergunningsserver om te gebruiken wanneer het een vergunning produceert. De client kan ook naar het beleid verwijzen voordat een licentie wordt aangevraagd om te bepalen of de gebruiker moet worden gevraagd om te verifiëren voordat een licentieverzoek aan de server wordt verzonden.

Een beleid specificeert één of meerdere rechten die aan de cliënt worden verleend. Doorgaans bevat een beleid minimaal de optie &quot;Rechts afspelen&quot;. Het is ook mogelijk om meerdere rechten voor afspelen op te geven, elk met verschillende beperkingen. Wanneer de client een licentie met meerdere Play Rights aantreft, wordt de eerste gebruikt waarvoor de client aan alle beperkingen voldoet. Deze functie kan bijvoorbeeld worden gebruikt om verschillende uitvoerbeveiligingsinstellingen op verschillende platforms af te dwingen. Zie `CreatePolicyWithOutputProtection.java` in de map &quot;samples&quot; in de opdrachtregelprogramma&#39;s van de Naslagimplementatie voor voorbeeldcode ter illustratie van dit voorbeeld.

U kunt de volgende taken uitvoeren met de API&#39;s voor beleidsbeheer:

* Beleid maken en bijwerken
* Beleidsdetails weergeven
* Beleidsupdate-lijsten beheren

Zie *Adobe Access API Reference* voor meer informatie over de Java API die in dit hoofdstuk wordt besproken.

Voor informatie over de de verwijzingsimplementatie van de Manager van het Beleid, zie het *Gebruiken van de Implementaties* van de Verwijzing van de Toegang van Adobe.
