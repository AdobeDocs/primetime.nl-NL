---
seo-title: Gedeeltelijk versleutelingsniveau
title: Gedeeltelijk versleutelingsniveau
uuid: 462ca2d0-0d37-43a8-b8a0-8a25ecf73ce1
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---


# Gedeeltelijk versleutelingsniveau{#partial-encryption-level}

Hiermee geeft u op of alle frames, of alleen een subset frames, moeten worden gecodeerd. Er zijn drie niveaus van encryptie: laag, gemiddeld en hoog.

>[!NOTE]
>
>Alleen voor videotracks in F4V/H.264-bestanden.

Gedeeltelijke codering is ontworpen om inhoudsproviders granulariteit te geven bij het coderen van de inhoud in onderdelen. De encryptie van inhoud voegt cpu overheadaan het apparaat toe dat de inhoud decrypteert en bekijkt. Gebruik gedeeltelijke codering om de CPU-overhead te verminderen terwijl de inhoud zeer goed wordt beveiligd. Een motiverend geval voor het gebruiken van deze eigenschap is één enkel stuk van inhoud die bedoeld is om over laag, middelgroot, en hoog aangedreven apparaten te spelen.

Vanwege de aard van videocodering is het niet nodig om 100% van de video te coderen om deze onafspeelbaar te maken als deze wordt gestolen. De gedeeltelijke encryptie heeft drie montages, laag, middelgroot, en hoog, en de bijbehorende percentages van encryptie zijn afhankelijk van hoe de video wordt gecodeerd. Vanwege deze afhankelijkheid van codering valt het percentage van de gecodeerde inhoud binnen de volgende bereiken:

* Hoog: Codeert alle samples.
* Normaal: Codeert een doel 50% van de gegevens.
* Laag: Codeert een doel 20 tot 30% van de gegevens.

Deze instellingen zijn ontworpen met de volgende regel: Alle inhoud die bij de lage instelling is gecodeerd, wordt ook gecodeerd bij de gemiddelde instelling. Dit zorgt ervoor dat hetzelfde stuk inhoud dat bij lage codering door de ene partij wordt gedistribueerd en met gemiddelde codering door een andere partij wordt gedistribueerd, de bescherming van de inhoud niet in gevaar brengt.

Voorbeeld van gebruik: Door het coderingsniveau te verlagen, verlaagt u de decoderingsoverhead op de client en verbetert u de afspeelprestaties op computers met een laag bereik.
