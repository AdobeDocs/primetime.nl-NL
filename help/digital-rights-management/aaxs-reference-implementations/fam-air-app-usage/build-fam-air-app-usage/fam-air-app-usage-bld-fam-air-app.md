---
title: De AIR-toepassing voor Flash Access Manager maken
description: De AIR-toepassing voor Flash Access Manager maken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# De Flash Access Manager AIR-toepassing {#building-the-flash-access-manager-air-application} samenstellen

Als u het AIR-bestand voor Flash Access Manager wilt maken op basis van de broncode, moet de SDK van Flex en AIR op uw computer zijn geïnstalleerd. Voordat u de toepassing kunt verpakken en uitvoeren, moet u de MXML code in een SWF-bestand compileren met de compiler [!DNL amxmlc]. De compiler [!DNL amxmlc] vindt u in de map [!DNL bin] van de SDK van Flex 4 of hoger. Desgewenst kunt u de omgevingsvariabele van het pad zodanig instellen dat deze de binmap van de Flex SDK bevat, zodat de hulpprogramma&#39;s gemakkelijker op de opdrachtregel kunnen worden uitgevoerd.

Gebruik de volgende procedure om het AIR-bestand voor Flash Access Manager te maken:

1. Open een opdrachtshell of een terminal en navigeer naar de projectmap van de Flash Access Manager AIR-toepassing ( [!DNL UI Tools\Flash Access Manager] in de map Reference Implementation).
1. Voer de volgende opdracht in:

   ```
   amxmlc src\FlashAccessmanager.mxml
   ```

   Als u [!DNL amxmlc] uitvoert, wordt [!DNL FlashAccessManager.swf] gemaakt, die de gecompileerde code van de toepassing bevat.

De SDK van Adobe AIR bevat het hulpprogramma ADT (AIR Developer Tool) voor het verpakken van AIR-toepassingen en het genereren van certificaten. AIR-toepassingen moeten digitaal worden ondertekend; gebruikers krijgen een waarschuwing wanneer ze toepassingen installeren die niet correct zijn ondertekend of die helemaal niet zijn ondertekend. Als u een certificaat wilt genereren via de opdrachtregel, opent u een consolevenster in dezelfde map als de AIR-toepassing en typt u het volgende:

```
adt -certificate -cn SelfSigned 1024-RSA testCert.pfx  
<i class="+ topic ph hi-d="" i "="">
  some_password 
</i class="+ topic>
```

Vervang *some_password* met een wachtwoord van uw keus. Na een paar seconden moet ADT het certificaatgeneratieproces voltooien en moet u een nieuw [!DNL testCert.pfx]-bestand in uw toepassingsmap hebben.

Gebruik vervolgens ADT om de toepassing in een [!DNL .air]-bestand te verpakken met de opdracht:

```
adt -package -storetype pkcs12 -keystore testCert.pfx FlashAccessManager.air src\FlashAccessManager-app.xml . -C src assets
```

Deze opdracht geeft ADT de opdracht om uw toepassing te verpakken met behulp van het sleutelbestand in [!DNL testCert.pfx]. In de bovenstaande regel configureert u ADT om de volledige toepassing te verpakken in een bestand met de naam [!DNL FlashAccessManager.air] en om de bestanden [!DNL FlashAccessManager-app.xml] en [!DNL FlashAccessManager.swf] en de afbeeldingen uit de map assets op te nemen.

Tijdens dit proces wordt u gevraagd om het wachtwoord dat u instelt voor het nieuwe certificaatbestand. Ga het in, wacht een ogenblik, en een [!DNL FlashAccessManager.air] dossier zou in de zelfde folder moeten verschijnen zoals uw projectdossiers.
