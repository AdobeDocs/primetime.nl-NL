---
seo-title: De Flash Access Manager AIR-toepassing samenstellen
title: De Flash Access Manager AIR-toepassing samenstellen
uuid: 00927eb3-b8eb-4dd4-b528-91b70760c8cd
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# De Flash Access Manager AIR-toepassing samenstellen {#building-the-flash-access-manager-air-application}

Als u het AIR-bestand van Flash Access Manager wilt maken op basis van de broncode, moet de SDK van Flex en AIR op uw computer zijn geïnstalleerd. Voordat u de toepassing in een pakket kunt plaatsen en uitvoeren, moet u de MXML-code met de [!DNL amxmlc] compiler in een SWF-bestand compileren. De [!DNL amxmlc] compiler vindt u in de [!DNL bin] map van de SDK van Flex 4 of hoger. U kunt desgewenst de omgevingsvariabele van het pad zo instellen dat deze de binmap SDK van Flex bevat, zodat de hulpprogramma&#39;s gemakkelijker op de opdrachtregel kunnen worden uitgevoerd.

Gebruik de volgende procedure om het Flash Access Manager AIR-bestand te maken:

1. Open een opdrachtshell of een terminal en navigeer naar de projectmap van de Flash Access Manager AIR-toepassing ( [!DNL UI Tools\Flash Access Manager] in de map Reference Implementation).
1. Voer de volgende opdracht in:

   ```
   amxmlc src\FlashAccessmanager.mxml
   ```

   Running [!DNL amxmlc] produceert [!DNL FlashAccessManager.swf], die de gecompileerde code van de toepassing bevat.

De SDK van Adobe AIR bevat het hulpprogramma AIR Developer Tool (ADT) voor het verpakken van AIR-toepassingen en het genereren van certificaten. AIR-toepassingen moeten digitaal worden ondertekend; gebruikers krijgen een waarschuwing wanneer ze toepassingen installeren die niet correct zijn ondertekend of die helemaal niet zijn ondertekend. Als u een certificaat wilt genereren via de opdrachtregel, opent u een consolevenster in dezelfde map als de AIR-toepassing en typt u het volgende:

```
adt -certificate -cn SelfSigned 1024-RSA testCert.pfx  
<i class="+ topic ph hi-d="" i "="">
  some_password 
</i class="+ topic>
```

Vervang *some_password* door een wachtwoord van uw keuze. Na een paar seconden moet ADT het certificaatgeneratieproces voltooien en moet u een nieuw [!DNL testCert.pfx] bestand in uw toepassingsmap hebben.

Gebruik vervolgens ADT om de toepassing in een [!DNL .air] bestand te verpakken met de opdracht:

```
adt -package -storetype pkcs12 -keystore testCert.pfx FlashAccessManager.air src\FlashAccessManager-app.xml . -C src assets
```

Deze opdracht geeft ADT de opdracht om uw toepassing te verpakken met behulp van het sleutelbestand in [!DNL testCert.pfx]. In de bovenstaande regel configureert u ADT om de volledige toepassing te verpakken in een bestand met de naam [!DNL FlashAccessManager.air], en om de bestanden [!DNL FlashAccessManager-app.xml] en [!DNL FlashAccessManager.swf] de afbeeldingen uit de map assets op te nemen.

Tijdens dit proces wordt u gevraagd om het wachtwoord dat u instelt voor het nieuwe certificaatbestand. Ga het in, wacht een ogenblik, en een [!DNL FlashAccessManager.air] dossier zou in de zelfde folder moeten verschijnen zoals uw projectdossiers.
