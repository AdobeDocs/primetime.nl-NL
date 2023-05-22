---
title: Firewall-regels
description: Firewall-regels
copied-description: true
exl-id: 1a40822a-893d-43ec-9c3e-8e0b4ebe6d01
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
