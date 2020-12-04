---
seo-title: Vorm en stel de bevel-lijn hulpmiddelen in werking
title: Vorm en stel de bevel-lijn hulpmiddelen in werking
uuid: b65f8621-54fa-4927-b2f4-d2fd60350fc1
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%

---


# Vorm en stel de bevel-lijn hulpmiddelen {#configure-and-run-the-command-line-tools} in werking

De bevel-lijn hulpmiddelen hebben bijbehorende eigenschappen waarvoor u waarden in [!DNL flashaccesstools.properties] *vóór* moet plaatsen u de hulpmiddelen in werking stelt. Met sommige opdrachtregelprogramma&#39;s kunt u ook eigenschapswaarden opgeven via de opdrachtregel. Waarden die u opgeeft vanaf de opdrachtregel hebben voorrang op waarden die u opgeeft vanaf [!DNL flashaccesstools.properties].

U moet instellingen in de volgende secties van [!DNL flashaccesstools.properties] wijzigen om de overeenkomstige opdrachtregelprogramma&#39;s die u wilt gebruiken, in te schakelen:

* **Eigenschappen**  van Media Packager - (voor  [!DNL AdobePackager.jar])

* **De Manager van de Lijst van de Update van het beleid en de Eigenschappen**  van de Manager van de Lijst van de Intrekking (voor  [!DNL AdobePolicyUpdateListManager.jar] en  [!DNL AdobeRevocationListManager.jar])

* **Eigenschappen**  voor beleidsbeheer - (voor  [!DNL AdobePolicyManager.jar])

* **Eigenschappen**  van licentiegenerator - (voor  [!DNL AdobeLicenseGenerator.jar])