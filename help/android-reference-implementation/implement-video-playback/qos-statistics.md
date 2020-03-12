---
description: U kunt opstelling uw speler om playback en apparatenstatistieken van QoSProvider zo vaak te lezen zoals nodig.
seo-description: U kunt opstelling uw speler om playback en apparatenstatistieken van QoSProvider zo vaak te lezen zoals nodig.
seo-title: QoS-afspeelgegevens en apparaatstatistieken weergeven
title: QoS-afspeelgegevens en apparaatstatistieken weergeven
uuid: 8fc45a2f-03d4-4fa0-979b-eb816419c4f7
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# QoS-afspeelgegevens en apparaatstatistieken weergeven {#display-qos-playback-and-device-statistics}

U kunt opstelling uw speler om playback en apparatenstatistieken van QoSProvider zo vaak te lezen zoals nodig.

De `QoSProvider` klasse biedt diverse statistieken, waaronder de framesnelheid, de bitsnelheid van het profiel, de totale tijd die is besteed aan bufferen, het aantal bufferpogingen, de tijd die nodig was om de eerste byte van het eerste videofragment op te halen, de tijd die nodig was om het eerste frame te renderen, de momenteel gebufferde lengte en de buffertijd.

De verwijzingsimplementatie verstrekt een `QoSManager` klasse waar u de vertoning van de bekleding kunt toelaten QoS. U kunt de zichtbaarheid van QoS ook inschakelen in de gebruikersinterface van Instellingen:

![](assets/qos-configuration.jpg)

De `QoSManager` sporen statistieken QoS door apparateninformatie te krijgen, aan de media speler vast te maken, en met de recentste informatie te bijwerken QoS.

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
   >Als u de Booleaanse waarde wijzigt in `false` schakelt u de QoS-rapportage uit.

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
