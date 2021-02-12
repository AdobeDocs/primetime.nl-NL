---
description: Terwijl het standaard creatieve het herverpakken van de dienst (CRS) scenario één Netwerk van de Levering van de Inhoud (CDN) moet gebruiken, kunt u activa CRS op meer dan één CDN opstellen.
seo-description: Terwijl het standaard creatieve het herverpakken van de dienst (CRS) scenario één Netwerk van de Levering van de Inhoud (CDN) moet gebruiken, kunt u activa CRS op meer dan één CDN opstellen.
seo-title: Meerdere CDN-ondersteuning voor CRS en levering
title: Meerdere CDN-ondersteuning voor CRS en levering
uuid: c5557a38-aa49-4161-bb58-3e8dff9a4d64
translation-type: tm+mt
source-git-commit: e1e33d3ac0aad44859cd49566331524da72ac7e4
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# Meerdere CDN-ondersteuning voor CRS en levering {#multiple-cdn-support-for-crs-ad-delivery}

Terwijl het standaard creatieve het herverpakken van de dienst (CRS) scenario één Netwerk van de Levering van de Inhoud (CDN) moet gebruiken, kunt u activa CRS op meer dan één CDN opstellen.

## Vereisten

U kunt meerdere CDN&#39;s gebruiken om de volgende redenen:

* Een vereiste om de schaal te vergroten voor grote weergavegebeurtenissen
* Een vereiste om de CDN-bron van het CRS-element te koppelen aan de CDN-bron van de hoofdinhoud.
* Een vereiste om een verschillende CDN van het gebrek CDN van CRS (Akamai) te gebruiken.

Wanneer de manifestserver omhoog voor getranscodeerde verzoeken maakt, gebruikt het een laarzentrekker URL die een aantal vraagparameters bevat. Als u opstelling een multi-CDN milieu hebt, zal bootstrap URL ook de `ptcdn` parameter moeten bevatten. De manifestserver gebruikt deze parameter om de server te identificeren CDN waarvan om de getranscodeerde versie van de advertentie te krijgen.

Zie [Ondersteuning van meerdere CDN](../../~old-creative-repackaging-service/multi-cdn-supportt.md) in de CRS-documentatie voor meer informatie.
