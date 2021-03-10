---
description: Of een cliëntvideospeler of de manifestserver kunnen met CRS in wisselwerking staan om JIT te bereiken herverpakken. Beide gebruiken dezelfde logica en selectielogica.
title: Gedetailleerde workflows voor JIT-herverpakken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# Gedetailleerde workflows voor JIT-herverpakken {#detailed-workflows-for-jit-repackaging}

Of een cliëntvideospeler of de manifestserver kunnen met CRS in wisselwerking staan om JIT te bereiken herverpakken. Beide gebruiken dezelfde logica en selectielogica.

## JIT-herverpakking geïnitieerd door de Manifest-server {#section_1F1C1B7DD146403890C2B43E24FEF0EB}

![](assets/ssai_JIT-workflow_web.png)

De workflow voor JIT-herverpakken aan de kant van de manifestserver ziet er als volgt uit:

1. De manifestserver doet een verzoek aan de advertentieserver.
1. De manifestserver ontvangt een advertentie die niet in formaat HLS is.
1. De manifestserver verzendt een verzoek naar de server CDN voor een eerder getranscodeerde versie van HLS van de creatieve advertentie.

   >[!NOTE]
   >
   >In een multi-CDN opstelling, gebruikt de manifestserver `ptcdn` parameter in bootstrap URL om de server te identificeren CDN.

1. De manifestserver controleert de reactie:

   1. Als het verzoek slaagt, neemt de manifestserver de eerder getranscodeerde versie van HLS van de advertentie creatief in de inhoudsstroom op.
   1. Als het verzoek ontbreekt, produceert de manifestserver een logboekingang en verzoekt om een getranscodeerde versie van CRS.

1. CRS transcodeert de advertentie creatief en uploadt de versie HLS aan de server CDN voor toekomstig gebruik.

Voor alle verdere verzoeken om dat creatieve, duidelijke server terugwint de versie HLS van CDN en neemt het in de inhoudsstroom op.

## JIT-herverpakking geïnitieerd door de client {#section_FBC97D40043F4FDD98247A08BB6195B0}

<!--<a id="fig_hkn_ndt_3z"></a>-->

![](assets/ssai_JIT-workflow_client_web.png)

Een client die is gebaseerd op TVSDK of met vergelijkbare mogelijkheden, kan als volgt met CRS communiceren om JIT-herverpakking te realiseren:

1. De client vraagt om een advertentie van de advertentieserver.
1. De advertentieserver retourneert de advertentie naar de client.
1. De client controleert de indeling van de advertentie op de advertentieserver:

   1. Als de advertentie de HLS-indeling heeft, voegt de client de advertentie in de inhoud in (hecht) en is deze gereed.
   1. Als de advertentie niet in formaat HLS is, verzoekt de cliënt om één van de server CDN.

      >[!NOTE]
      >
      >In een multi-CDN opstelling, gebruikt de manifestserver `ptcdn` parameter in bootstrap URL om de server te identificeren CDN.

1. De client controleert de reactie van de CDN-server.

   1. Als CDN een versie HLS verstrekte, neemt de cliënt (stitches) het in de inhoud op, en wordt gedaan.
   1. Als de CDN-server geen HLS-versie levert, vraagt de client de advertentieserver om er een van CRS aan te vragen. De client voegt de advertentie niet in de inhoud in.

1. De server van de hulp verzoekt dat niet-HLS aan HLS zou moeten worden getranscodeerd.
1. CRS leidt tot een versie van HLS en uploadt het aan de server CDN voor toekomstig gebruik.

## Advertentieprioriteiten en tijdlijn {#section_A74DE37A57BF45D7B6D09E3DE40F8E61}

De manifestserver en de cliënt gebruiken de zelfde selectielogica om de prioriteiten voor het spelen van beschikbare advertenties te bepalen. HLS-Geformatteerde advertenties zijn eerste prioriteit, die door MP4, FLV, en tenslotte WebM wordt gevolgd.

CRS vereist typisch 2-4 minuten om een niet-HLS en creatief, en gewoonlijk minder dan 3 minuten te verwerken.

CRS veroorzaakt verschillende HLS beetjetarieven, zodat kan de advertentie bij een snelheid spelen die aan de beschikbare verbindingssnelheid en bandbreedte wordt aangepast. Als er veelvoudige beschikbare beetjetarieven zijn, kiest CRS het hoogste beschikbare beetjetarief. Als CRS een niet-HLS en creatief ontvangt, produceert het een versie HLS bij de hoogste beschikbare resolutie.