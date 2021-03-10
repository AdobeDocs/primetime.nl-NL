---
description: U kunt opstelling uw speler om playback en apparatenstatistieken van QoSProvider zo vaak te lezen zoals nodig.
title: QoS-afspeelgegevens en apparaatstatistieken weergeven
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---


# QoS-afspeel- en apparaatstatistieken {#display-qos-playback-and-device-statistics} weergeven

U kunt opstelling uw speler om playback en apparatenstatistieken van QoSProvider zo vaak te lezen zoals nodig.

De klasse `QoSProvider` verstrekt diverse statistieken, met inbegrip van het kadertarief, de tarief van het profielbeetje, de totale tijd die in het als buffer optreden wordt doorgebracht, het aantal het als buffer optreden voor pogingen, de tijd het nam om de eerste byte van het eerste videofragment te krijgen, de tijd het nam om het eerste kader, de momenteel als buffer optredende lengte, en de buffertijd terug te geven.

De verwijzingsimplementatie verstrekt een `QoSManager` klasse waar u de vertoning van de bekleding kunt toelaten QoS. U kunt de zichtbaarheid van QoS ook inschakelen in de gebruikersinterface van Instellingen:

![](assets/qos-configuration.jpg)

`QoSManager` volgt statistieken QoS door apparateninformatie te krijgen, aan de media speler vast te maken, en met de recentste informatie te bijwerken QoS.

**De rapportage van QoS-statistieken in- of uitschakelen**

1. Creeer QosManager of laat QoS rapportering toe gebruikend ManagerFactory.

   * Een QosManager maken:
      * Deze toepassing moet de functie voor de advertentieworkflow gebruiken

   QoSManager qosManager = new QosManagerOn();

   * Om een ManagerFactory te gebruiken om de vertoning van statistieken QoS toe te laten:

   qosManager = ManagerFactory.getQosManager()
   <b>true</b>, config, mediaPlayer);

   >[!NOTE]
   >
   >Als u de Booleaanse waarde wijzigt in `false`, wordt QoS-rapportage uitgeschakeld.

2. Gebeurtenislisteners toevoegen:

   `qosManager.addEventListener(qosManagerEventListener);`

3. Maak de QoS-provider en koppel deze aan de speleractiviteitcontext:

   `qosManager.createQOSProvider(getActivity());`

   >[!NOTE]
   >
   >Wanneer de speleractiviteit zal worden vernietigd, zorg ervoor om [qosManager.destroyQOSProvider](https://help.adobe.com/en_US/primetime/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html#destroyQOSProvider()) te roepen om de leverancier QOS schoon te maken door het van de media speler los te maken.

**Gerelateerde API-documentatie**

* [Klasse QosManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html)
* [Klasse QosManagerOn](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManagerOn.html)
* [QosManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosManagerEventListener.html)
* [QosItem](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosItem.html)
