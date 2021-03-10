---
title: Firewall-regels
description: Firewall-regels
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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
