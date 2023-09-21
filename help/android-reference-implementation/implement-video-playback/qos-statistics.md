---
description: U kunt opstelling uw speler om playback en apparatenstatistieken van QoSProvider zo vaak te lezen zoals nodig.
title: QoS-afspeelgegevens en apparaatstatistieken weergeven
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# QoS-afspeelgegevens en apparaatstatistieken weergeven {#display-qos-playback-and-device-statistics}

U kunt opstelling uw speler om playback en apparatenstatistieken van QoSProvider zo vaak te lezen zoals nodig.

De `QoSProvider` klasse verstrekt diverse statistieken, met inbegrip van het kadertarief, de tarief van het profielbeetje, de totale tijd die in het als buffer optreden wordt doorgebracht, het aantal het als buffer optreden voor pogingen, de tijd het nam om de eerste byte van het eerste videofragment te krijgen, de tijd het nam om het eerste kader, de momenteel als buffer optredende voor lengte, en de buffertijd terug te geven.

De referentie-implementatie biedt een `QoSManager` klasse waar u de weergave van de QoS-bedekking kunt inschakelen. U kunt de zichtbaarheid van QoS ook inschakelen in de gebruikersinterface van Instellingen:

![](assets/qos-configuration.jpg)

De `QoSManager` volgt statistieken QoS door apparateninformatie, vastmakend aan de media speler, en het bijwerken met de recentste informatie QoS te krijgen.

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
   >De Booleaanse waarde wijzigen in `false` Hiermee schakelt u QoS-rapportage uit.

2. Gebeurtenislisteners toevoegen:

   `qosManager.addEventListener(qosManagerEventListener);`

3. Maak de QoS-provider en koppel deze aan de speleractiviteitcontext:

   `qosManager.createQOSProvider(getActivity());`

   >[!NOTE]
   >
   >Wanneer de speleractiviteit zal worden vernietigd, zorg ervoor [qosManager.destroyQOSProvider](https://help.adobe.com/en_US/primetime/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html#destroyQOSProvider()) om de QOS-provider op te schonen door deze van de mediaspeler los te koppelen.

**Gerelateerde API-documentatie**

* [Klasse QosManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html)
* [Klasse QosManagerOn](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManagerOn.html)
* [QosManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosManagerEventListener.html)
* [QosItem](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosItem.html)
