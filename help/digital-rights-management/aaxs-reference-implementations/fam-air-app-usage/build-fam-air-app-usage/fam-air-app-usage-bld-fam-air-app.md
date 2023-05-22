---
title: De Flash Access Manager AIR-toepassing samenstellen
description: De Flash Access Manager AIR-toepassing samenstellen
copied-description: true
exl-id: f15fe9d2-d5e8-43ef-a1d5-1211752d54da
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# De Flash Access Manager AIR-toepassing samenstellen {#building-the-flash-access-manager-air-application}

Als u het Flash Access Manager AIR-bestand wilt maken op basis van de broncode, moet de SDK van Flex en AIR op uw computer zijn geïnstalleerd. Voordat u de toepassing in een pakket kunt plaatsen en uitvoeren, moet u de MXML code eerst met de [!DNL amxmlc] compiler. De [!DNL amxmlc] compiler vindt u in het dialoogvenster [!DNL bin] directory van de Flex 4 of hoger SDK. Desgewenst kunt u de omgevingsvariabele van het pad zodanig instellen dat deze de binmap van de Flex SDK bevat, zodat de hulpprogramma&#39;s gemakkelijker op de opdrachtregel kunnen worden uitgevoerd.

Ga als volgt te werk om het Flash Access Manager AIR-bestand te maken:

1. Open bevelshell of een terminal en navigeer aan de projectomslag van de toepassing van AIR van de Manager van de Flash Access ( [!DNL UI Tools\Flash Access Manager] in de map Referentie-implementatie).
1. Voer de volgende opdracht in:

   ```
   amxmlc src\FlashAccessmanager.mxml
   ```

   Wordt uitgevoerd [!DNL amxmlc] produceert [!DNL FlashAccessManager.swf], die de gecompileerde code van de toepassing bevat.

De SDK van Adobe AIR bevat het hulpprogramma AIR Developer Tool (ADT) voor het verpakken van AIR-toepassingen en het genereren van certificaten. AIR-toepassingen moeten digitaal worden ondertekend; gebruikers krijgen een waarschuwing wanneer ze toepassingen installeren die niet correct zijn ondertekend of die helemaal niet zijn ondertekend. Als u een certificaat wilt genereren via de opdrachtregel, opent u een consolevenster in dezelfde map als de AIR-toepassing en typt u het volgende:

```
adt -certificate -cn SelfSigned 1024-RSA testCert.pfx  
<i class="+ topic ph hi-d="" i "="">
  some_password 
</i class="+ topic>
```

Vervangend *some_password* met een door u gekozen wachtwoord. Na een paar seconden moet ADT het certificaatgeneratieproces voltooien en moet u een nieuwe [!DNL testCert.pfx] in uw toepassingsmap.

Gebruik vervolgens ADT om de toepassing in een pakket te plaatsen [!DNL .air] bestand, met de opdracht:

```
adt -package -storetype pkcs12 -keystore testCert.pfx FlashAccessManager.air src\FlashAccessManager-app.xml . -C src assets
```

Deze opdracht geeft ADT de opdracht om uw toepassing in een pakket te plaatsen met behulp van het sleutelbestand in [!DNL testCert.pfx]. In de bovenstaande regel configureert u ADT om de volledige toepassing te verpakken in een bestand met de naam [!DNL FlashAccessManager.air]en om de bestanden op te nemen [!DNL FlashAccessManager-app.xml] en [!DNL FlashAccessManager.swf] en de afbeeldingen uit de map assets.

Tijdens dit proces wordt u gevraagd om het wachtwoord dat u instelt voor het nieuwe certificaatbestand. Voer het in, wacht even en een [!DNL FlashAccessManager.air] bestand moet in dezelfde map staan als de projectbestanden.
