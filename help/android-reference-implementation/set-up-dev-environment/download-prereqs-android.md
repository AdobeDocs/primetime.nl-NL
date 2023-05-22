---
title: Voorwaardelijke software downloaden en configureren
description: Het installatieproces is eenvoudig. Als de JDK al op uw systeem is geïnstalleerd, kunt u deze stap overslaan, maar houd er rekening mee dat uw JDK, Eclipse IDE en OS compatibel moeten zijn.
exl-id: c2884a55-4f5e-4da8-807d-633625d7fef9
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Voorwaardelijke software downloaden en configureren {#download-and-configure-prerequisite-software}

1. Download de JDK van [https://www.oracle.com/technetwork/java/javase/downloads/](https://www.oracle.com/technetwork/java/javase/downloads/).

   Het installatieproces is eenvoudig. Als de JDK al op uw systeem is geïnstalleerd, kunt u deze stap overslaan, maar houd er rekening mee dat uw JDK, Eclipse IDE en OS compatibel moeten zijn.
1. Download de Eclipse IDE voor Java-ontwikkelaars van [https://www.eclipse.org/downloads](https://www.eclipse.org/downloads).

   Nadat u het pakket hebt uitgepakt, kunt u Eclipse rechtstreeks uitvoeren. Er is geen installatieprogramma.
1. Download de ADT-bundel van de Android-SDK vanuit [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html).

   Deze bundel bevat Eclipse. Als Eclipse al op uw systeem is geïnstalleerd, kunt u de SDK Tools voor uw platform downloaden van het [!UICONTROL Use An Existing IDE] sectie.

   Pak het uit en installeer op een locatie die u zich herinnert. U zult dit in een recentere stap moeten van verwijzingen voorzien.
1. Configureer de Android-SDK.
   1. Open een terminal (in Mac OS X) of een opdrachtprompt (in Windows).
   1. Navigeer naar de map waarin u de Android-SDK hebt gedownload of uitgepakt.
   1. Ga naar de map Tools die een bestand bevat met de naam [!DNL android].
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

      * toevoegen `-vm C:\[path to your JDK bin]\javaw.exe` aan uw [!DNL eclipse.ini] bestand.
   1. Selecteren  **[!UICONTROL Help]** > **[!UICONTROL Install New Software]** .
   1. Klikken **[!UICONTROL Add...]**.
   1. Enter `Android` voor de naam.
   1. Enter `https://dl-ssl.google.com/android/eclipse/` voor de **[!UICONTROL Work with]** koppeling.
   1. Klikken **[!UICONTROL OK]**.

      U zou een dialoog moeten zien gelijkend op dit:

      ![](assets/available_software.jpg)

   1. Selecteer de resulterende pakketten (die in de Hulpmiddelen van de Ontwikkelaar en Insteekmodules NDK) en klik **[!UICONTROL Next]**.

      Hiermee worden de Android Development Tools (ADT) gedownload.
   1. Start Eclipse opnieuw nadat het downloaden is voltooid.

   De Android-SDK is nu geïnstalleerd. 1. Configureer Eclipse zodat de SDK van Android kan worden gevonden en als bron kan worden gebruikt.
   1. Open Eclipse.
   1. Selecteren  **[!UICONTROL Window]** > **[!UICONTROL Preferences]** in Windows;  **[!UICONTROL ADT]** > **[!UICONTROL Preferences]** op Mac OS X.
   1. Selecteer **[!UICONTROL Android]** tab.
   1. Blader naar de locatie van de Android-SDK.
   1. Klikken **[!UICONTROL Apply]**.

      ![Stap resultaat](assets/ss2.jpg)
