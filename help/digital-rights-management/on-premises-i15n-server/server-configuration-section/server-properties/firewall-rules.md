---
title: Firewall-regels
description: Firewall-regels
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---

# Firewall-regels{#firewall-rules}

Om toegang tot de server van de Individualisering te beveiligen, slechts moeten bepaalde toepassingswegen worden blootgesteld. De Individualisatieserver moet verzoeken van cliënten aan deze wegen goedkeuren:

* [!DNL /flashaccess/i15n/*]
* [!DNL /flashaccess/status]
* [!DNL /crossdomain.xml]

Servicepaden, zoals [!DNL /flashaccess/admin/*] (d.w.z. status- en beheerpagina&#39;s) mogen alleen toegankelijk zijn vanuit de firewall. Geen delen van de Zeer belangrijke Server van de Generatie zouden van buiten de firewall moeten worden betreden.
