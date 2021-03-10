---
title: Voorwaardelijke software downloaden en configureren
description: Het installatieproces is eenvoudig. Als de JDK al op uw systeem is geïnstalleerd, kunt u deze stap overslaan, maar houd er rekening mee dat uw JDK, Eclipse IDE en OS compatibel moeten zijn.
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---


# In eerste instantie vereiste software downloaden en configureren {#download-and-configure-prerequisite-software}

1. Download JDK van [https://www.oracle.com/technetwork/java/javase/downloads/](https://www.oracle.com/technetwork/java/javase/downloads/).

   Het installatieproces is eenvoudig. Als de JDK al op uw systeem is geïnstalleerd, kunt u deze stap overslaan, maar houd er rekening mee dat uw JDK, Eclipse IDE en OS compatibel moeten zijn.
1. Download Eclipse IDE for Java Developers van [https://www.eclipse.org/downloads](https://www.eclipse.org/downloads).

   Nadat u het pakket hebt uitgepakt, kunt u Eclipse rechtstreeks uitvoeren. Er is geen installatieprogramma.
1. Download de ADT-bundel van de Android-SDK via [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html).

   Deze bundel bevat Eclipse. Als Eclipse al op uw systeem is geïnstalleerd, kunt u de SDK Tools voor uw platform downloaden in de sectie [!UICONTROL Use An Existing IDE].

   Pak het uit en installeer op een locatie die u zich herinnert. U zult dit in een recentere stap moeten van verwijzingen voorzien.
1. Configureer de Android-SDK.
   1. Open een terminal (in Mac OS X) of een opdrachtprompt (in Windows).
   1. Navigeer naar de map waarin u de Android-SDK hebt gedownload of uitgepakt.
   1. Ga naar de hulpmiddelenomslag, die een dossier genoemd [!DNL android] bevat.
   1. Voer de volgende opdrachten uit:

      * Voor Mac OS X/Unix:

         ```
         chmod +x android 
         android update sdk --no-ui
         ```

      * Voor Windows:

         ```
         android update sdk --no-ui
         ```

         Dit proces duurt even.

1. Verduistering configureren.
   1. Begin Eclipse.

      Als Eclipse in Windows niet wordt gestart en het gemelde probleem is dat Eclipse een vereist Java-bestand niet kan vinden, probeert u het volgende:

      * Voeg `-vm C:\[path to your JDK bin]\javaw.exe` aan uw [!DNL eclipse.ini] dossier toe.
   1. Selecteer **[!UICONTROL Help]** > **[!UICONTROL Install New Software]**.
   1. Klik op **[!UICONTROL Add...]**.
   1. Voer `Android` in voor de naam.
   1. Typ `https://dl-ssl.google.com/android/eclipse/` voor de koppeling **[!UICONTROL Work with]**.
   1. Klik op **[!UICONTROL OK]**.

      U zou een dialoog moeten zien gelijkend op dit:

      ![](assets/available_software.jpg)

   1. Selecteer de resulterende pakketten (die in de Hulpmiddelen van de Ontwikkelaar en Insteekmodules NDK) en klik **[!UICONTROL Next]**.

      Hiermee worden de Android Development Tools (ADT) gedownload.
   1. Start Eclipse opnieuw nadat het downloaden is voltooid.

   De Android-SDK is nu geïnstalleerd. 1. Configureer Eclipse zodat de SDK van Android kan worden gevonden en als bron kan worden gebruikt.
   1. Open Eclipse.
   1. Selecteer **[!UICONTROL Window]** > **[!UICONTROL Preferences]** in Windows.  **[!UICONTROL ADT]** > **[!UICONTROL Preferences]** in Mac OS X.
   1. Selecteer het tabblad **[!UICONTROL Android]**.
   1. Blader naar de locatie van de Android-SDK.
   1. Klik op **[!UICONTROL Apply]**.

      ![Stap resultaat](assets/ss2.jpg)


