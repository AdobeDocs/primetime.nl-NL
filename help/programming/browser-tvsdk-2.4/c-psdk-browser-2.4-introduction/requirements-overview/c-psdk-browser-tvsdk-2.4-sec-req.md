---
description: Er zijn enkele beveiligingsoverwegingen die u moet onthouden voor Browser-TVSDK.
title: Beveiligingsoverwegingen
exl-id: bc98890a-082a-4e2d-b927-ecb3bd878de9
source-git-commit: 78be1575cc7bd6630a7bf85faa061327e5c414d7
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Beveiligingsoverwegingen{#security-considerations}

Er zijn enkele beveiligingsoverwegingen die u moet onthouden voor Browser-TVSDK.

* **Adobe Flash Player**

   * Flash Player staat geen toegang tot gegevens toe die buiten het domein verblijven waarvan de SWF voortkwam.

      Om toegang toe te staan, gastheer een dossier van het dwars-domeinbeleid met aangewezen toestemmingen bij de wortel van de server die de gegevens ontvangt. In de Wijze van de Fallback van Flash in Browser TVSDK (versie 23 van Flash Player en hoger), hebt u het toestemmingstoken voor uw domein nodig. Neem contact op met uw Adobe-vertegenwoordiger om het token te genereren.

* **JavaScript**

   * JavaScript voert hetzelfde oorspronkelijke beleid en voorkomt toegang tot bronnen over domeingrenzen.

      Om toegang tot deze middelen toe te staan, moet de toegang-controle-staat-Oorsprong (CORS) kopbal op de middelen worden geplaatst die op oorsprong buiten de speler worden ontvangen. Indien de inhoud wordt gespecificeerd door gebruik te maken van bytebereiken, moet in het verzoek om opties vóór de vlucht van CORS worden aangegeven dat deze aanvragen zijn toegestaan door de oorsprong.

* **Browsers en gemengde inhoud**

   * Browsers vereisen dat met AES-128 gecodeerde inhoud wordt gehost via beveiligde oorsprong (bijvoorbeeld HTTPS).

      Omdat de meeste browsers geen gemengde inhoud toestaan, adviseren wij dat de speler, de inhoud, en de bijbehorende activa zoals Sleutel/WebVTT dossiers ook over veilige Oorsprong worden ontvangen.

      >[!IMPORTANT]
      >
      >Als de speler wordt gehost via HTTPS, wordt vanaf versie 2.4.5 de HTTP-aanroepen door Browser TVSDK geconverteerd naar HTTPS wanneer MSE-technologie wordt gebruikt.
