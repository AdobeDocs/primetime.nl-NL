---
seo-title: Firewall-regels
title: Firewall-regels
uuid: f1629ceb-22de-4bb5-b73f-9b874d97ea8b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---


# firewallregels{#firewall-rules}

Om toegang tot de server van de Individualisering te beveiligen, slechts moeten bepaalde toepassingswegen worden blootgesteld. De Individualisatieserver moet verzoeken van cliënten aan deze wegen goedkeuren:

* [!DNL /flashaccess/i15n/*]
* [!DNL /flashaccess/status]
* [!DNL /crossdomain.xml]

Servicepaden, zoals [!DNL /flashaccess/admin/*] (d.w.z. status- en beheerpagina&#39;s), moeten alleen toegankelijk zijn vanuit de firewall. Geen delen van de Zeer belangrijke Server van de Generatie zouden van buiten de firewall moeten worden betreden.
