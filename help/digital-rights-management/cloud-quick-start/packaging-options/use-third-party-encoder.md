---
seo-title: Codeermodule van derden gebruiken
title: Codeermodule van derden gebruiken
uuid: 8649303c-b8e6-4c02-a8ad-5734af850bfe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Codeermodule van derden gebruiken{#use-a-third-party-encoder}

Sommige klanten hebben al een contentvoorbereidingspijplijn geïnstalleerd met een hardware- of softwarevideocodeermodule (of Adobe Media Server). Als dit het geval is, kan elk product dat momenteel met Primetime DRM beveiligde inhoud kan maken, inhoud verpakken voor Primetime Cloud DRM met dezelfde configuratie-instellingen als de Primetime Cloud DRM Protection Kit. De vereiste informatie kan uit één van beide bestaande configuratiedossiers worden verkregen inbegrepen in de uitrusting: [!DNL config_hls.xml] of [!DNL config_hds.xml].

De relevante configuratiepunten zijn:

* URL licentieserver
* URL sleutelserver
* Certificaat van licentieserver
* Transportcertificaat

