---
title: Overzicht
description: Overzicht
copied-description: true
exl-id: 15733120-b1bb-46a7-90d2-4eb11c539d62
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Overzicht  {#overview}

Met Adobe® Access™ kunnen inhoudsproviders beleid toepassen op mediabestanden. Met behulp van de API&#39;s voor beleidsbeheer kunnen beheerders beleidsregels maken, weergeven en bijwerken.

A *beleid* bepaalt hoe de gebruikers inhoud kunnen bekijken; het is een verzameling informatie die beveiligingsinstellingen, verificatievereisten en gebruiksrechten bevat. Wanneer beleid wordt toegepast, staan de encryptie en de ondertekening inhoudsleveranciers toe om controle van hun inhoud te handhaven ongeacht hoe breed het wordt verdeeld. Beveiligde bestanden kunnen worden geleverd met Adobe® Flash® Media Server of een HTTP-server. Ze kunnen worden gedownload en afgespeeld in aangepaste spelers die zijn gemaakt met Adobe® AIR®, Adobe® Flash® Player en Adobe® Primetime SDK voor iOS. Het beleid is een malplaatje voor de vergunningsserver om te gebruiken wanneer het een vergunning produceert. De client kan ook naar het beleid verwijzen voordat een licentie wordt aangevraagd om te bepalen of de gebruiker moet worden gevraagd om te verifiëren voordat een licentieverzoek aan de server wordt verzonden.

Een beleid specificeert één of meerdere rechten die aan de cliënt worden verleend. Doorgaans bevat een beleid minimaal de optie &quot;Rechts afspelen&quot;. Het is ook mogelijk om meerdere rechten voor afspelen op te geven, elk met verschillende beperkingen. Wanneer de client een licentie met meerdere Play Rights aantreft, wordt de eerste gebruikt waarvoor de client aan alle beperkingen voldoet. Deze functie kan bijvoorbeeld worden gebruikt om verschillende uitvoerbeveiligingsinstellingen op verschillende platforms af te dwingen. Zie voor voorbeeldcode ter illustratie van dit voorbeeld `CreatePolicyWithOutputProtection.java` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s van de naslagimplementatie.

U kunt de volgende taken uitvoeren met de API&#39;s voor beleidsbeheer:

* Beleid maken en bijwerken
* Beleidsdetails weergeven
* Beleidsupdate-lijsten beheren

Zie voor meer informatie over de Java API die in dit hoofdstuk wordt besproken *Referentie voor Adobe Access API*.

Voor informatie over de de verwijzingsimplementatie van de Manager van het Beleid, zie *Implementaties van de Adobe Access-naslaggids gebruiken*.
