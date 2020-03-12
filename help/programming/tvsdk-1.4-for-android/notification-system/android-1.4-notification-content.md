---
description: MediaPlayerNotification-objecten bieden informatie over wijzigingen in spelerstatus, waarschuwingen en fouten. Fouten die het afspelen van de video stoppen, veroorzaken ook een wijziging in de status van de speler.
seo-description: MediaPlayerNotification-objecten bieden informatie over wijzigingen in spelerstatus, waarschuwingen en fouten. Fouten die het afspelen van de video stoppen, veroorzaken ook een wijziging in de status van de speler.
seo-title: Inhoud voor meldingen
title: Inhoud voor meldingen
uuid: 89fb8f63-b0d5-45cd-bdad-348529fd07d0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Inhoud voor meldingen {#notification-content}

MediaPlayerNotification-objecten bieden informatie over wijzigingen in spelerstatus, waarschuwingen en fouten. Fouten die het afspelen van de video stoppen, veroorzaken ook een wijziging in de status van de speler.

Uw toepassing kan de melding- en statusgegevens ophalen. U kunt ook een registratiesysteem voor diagnostiek en validatie maken met behulp van de meldingsgegevens.

U implementeert gebeurtenislisteners om gebeurtenissen vast te leggen en erop te reageren. Veel gebeurtenissen bieden `MediaPlayerNotification` statusmeldingen.

`MediaPlayerNotification` geeft informatie over de status van de speler.

TVSDK verstrekt een chronologische lijst van `MediaPlayerNotification` berichten. Elke melding bevat de volgende informatie:

* Tijdstempel
* Diagnostische metagegevens die bestaan uit de volgende elementen:

   * `type`: INFORMATIE, WAARSCHUWING of FOUT.
   * `code`: Een numerieke weergave van de kennisgeving.
   * `name`: Een door mensen leesbare beschrijving van de melding, zoals SEEK_ERROR
   * `metadata`: Sleutel-waardeparen die relevante informatie over de kennisgeving bevatten. Een benoemde sleutel `URL` biedt bijvoorbeeld een waarde die een URL is die gerelateerd is aan het bericht.

   * `innerNotification`: Een verwijzing naar een ander `MediaPlayerNotification` object dat rechtstreeks van invloed is op deze melding.

U kunt deze informatie lokaal opslaan voor latere analyse of naar een externe server verzenden voor registratie en grafische weergave.

## Uw meldingssysteem instellen {#set-up-your-notification-system}

U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.

De kern van het meldingssysteem van de Speler Primetime is de `Notification` klasse, die een standalone bericht vertegenwoordigt.

De `NotificationHistory` klasse biedt een mechanisme voor het verzamelen van meldingen. Het slaat een logboek van bericht (NotificationHistoryItem) voorwerpen op die een inzameling van Meldingen vertegenwoordigt.

Om meldingen te ontvangen:

* Luisteren naar meldingen
* Meldingen toevoegen aan de berichtgeschiedenis

1. Luisteren naar statuswijzigingen.
1. Implementeer de `MediaPlayer.PlaybackEventListener.onStateChanged` callback.
1. TVSDK geeft twee parameters door aan de callback:

   * Het nieuwe frame ( `MediaPlayer.PlayerState`)
   * Een `MediaPlayerNotification` object

## Logboekregistratie en foutopsporing in realtime toevoegen {#add-real-time-logging-and-debugging}

U kunt meldingen gebruiken om realtime aanmelding in uw videotoepassing te implementeren.

Het berichtsysteem staat u toe om het registreren en het zuiveren informatie voor diagnostiek en bevestiging te verzamelen zonder het systeem te benadrukken.

>[!IMPORTANT]
>
>Het registreren achtereind maakt geen deel uit van een productieconfiguratie en wordt niet verwacht om hoog-ladingsverkeer te behandelen. Als uw implementatie niet volledig hoeft te zijn, kunt u beter de efficiëntie van gegevensoverdracht in overweging nemen om te voorkomen dat uw systeem wordt overbelast.

Hier is een voorbeeld van hoe u meldingen kunt ophalen.

1. Creeer een op tijdopnemer-gebaseerde uitvoeringsdraad voor uw videotoepassing die periodiek de gegevens vraagt die door het TVSDK berichtsysteem worden verzameld.

1. Als het interval van de timer te groot is en de gebeurtenislijst te klein is, loopt de lijst met berichtgebeurtenissen over. Voer een van de volgende handelingen uit om deze overloop te voorkomen:

   * Verlaag het tijdinterval dat de draad drijft die voor nieuwe gebeurtenissen opiniepeilt.
   * Vergroot de lijst met meldingen.

1. Serialiseren van de meest recente berichtgebeurtenisberichten in JSON-indeling en verzenden de berichten naar een externe server voor nabewerking.

   De externe server kan de verschafte gegevens dan grafisch in real-time weergeven.
1. Om het verlies van berichtgebeurtenissen te ontdekken, zoek hiaten in de opeenvolging van waarden van de gebeurtenisindex.

   Elke meldingsgebeurtenis heeft een indexwaarde die automatisch wordt verhoogd door de `session.NotificationHistory` klasse.

## ID3-tags {#id-tags}

ID3-tags bieden informatie over een audio- of videobestand, zoals de titel van het bestand of de naam van de artiest. TVSDK detecteert ID3-tags op het segmentniveau van de transportstream (TS) in HLS-streams en verzendt een gebeurtenis. De toepassing kan gegevens uit de tag extraheren.

>[!IMPORTANT]
>
>TVSDK herkent ID3-metagegevens (versie 2.3.0 of 2.4.0) in audio- (AAC) en videostreams (H.264) in een van de mogelijke coderingen (ASCII, UTF8, UTF16-BE of UTF16-LE). ID3-tags worden genegeerd die zich niet in een van de herkende versies of indelingen bevinden. Niet-opgegeven codering wordt behandeld als UTF8.

Wanneer TVSDK ID3-metagegevens detecteert, wordt een melding met de volgende gegevens weergegeven:

* InfoCode = 303007
* TYPE = ID3
* NAME = niet aanwezig
* ID = 0

1. Implementeer een gebeurtenislistener voor `MediaPlayer.PlaybackEventListener#onTimedMetadata(TimeMetadata timeMetadata)` en registreer deze bij het `MediaPlayer` object.

   TVSDK roept deze listener aan wanneer deze ID3-metagegevens detecteert.

   >[!NOTE]
   >
   >Aangepaste cues en cues gebruiken dezelfde `onTimedMetadata` gebeurtenis om de detectie van een nieuwe tag aan te geven. Dit mag geen verwarring veroorzaken omdat aangepaste ad-cues worden gedetecteerd op manifestniveau en ID3-tags zijn ingesloten in de stream. Voor meer informatie, zie douane-markeringen-vormen.

1. Haal de metagegevens op.

   ```java
   @Override 
   public void onTimedMetadata(TimedMetadata timedMetadata) { 
       TimedMetadata.Type type = timedMetadata.getType(); 
       if (type.equals(TimedMetadata.Type.ID3)){ 
           long time = timeMetadata.getTime(); 
           Metadata metadata = timedMetadata.getMetadata(); 
           Set<String> keys = metadata.keySet(); 
           for (String key : keys){ 
               String value = metadata.getValue(key); 
           } 
       } 
   }
   ```
