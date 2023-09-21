---
description: Met alternatief geluid (late binding) kunt u schakelen tussen beschikbare audiotracks voor een videotrack. Op deze manier kunnen gebruikers een taaltrack selecteren wanneer de video wordt afgespeeld.
title: Alternatieve audiotracks in de afspeellijst
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Alternatieve audiotracks in de afspeellijst {#section_BC8C1C74A5A24A8CA68C1E7E721EE742}

De afspeellijst voor een video kan een onbeperkt aantal alternatieve audiotracks voor de hoofdvideo-inhoud opgeven. U kunt bijvoorbeeld verschillende talen toevoegen aan uw video-inhoud of de gebruiker toestaan te schakelen tussen verschillende tracks op het apparaat terwijl de inhoud wordt afgespeeld.

Met alternatieve audiotracks, of audio die laat wordt gekoppeld, kunnen gebruikers schakelen tussen meerdere geluidssporen voor HTTP-videostreams (live/lineair en VOD) en hoeft u de video voor elke audiotrack niet te wijzigen, dupliceren of opnieuw te verpakken. U kunt meerdere geluidssporen voor de taal van een video-element opgeven vóór of na het eerste pakket van het element.

>[!TIP]
>
>De alternatieve audio wordt alleen gemengd met de videotrack van de hoofdmedia als de tijdstempels van de alternatieve track overeenkomen met de tijdstempels van de audio in de hoofdtrack.

De volgende vereisten zijn van toepassing als u afwisselende audiosporen gebruikt en reclame omvat:

* Als de hoofdinhoud alternatieve audiotracks heeft, moeten advertenties ten minste één audiostream hebben.
* Elke segmentduur van de audio-enige stream van een advertentie moet gelijk zijn aan de segmentduur van de videostream van een advertentie.

De hoofdaudiotrack wordt opgenomen in de verzameling audiotracks met de `default` label. Metagegevens voor de alternatieve audiostreams zijn opgenomen in de afspeellijst in het dialoogvenster `#EXT-X-MEDIA` tags met `TYPE=AUDIO`.

Een M3U8-manifest dat bijvoorbeeld meerdere alternatieve audiostreams opgeeft, ziet er als volgt uit:

```
#EXTM3U 
#EXT-X-MEDIA:TYPE=AUDIO,GROUP-ID="bipbop_audio",LANGUAGE="eng",NAME="BipBop Audio 1", 
 AUTOSELECT=YES,DEFAULT=YES 
#EXT-X-MEDIA:TYPE=AUDIO,GROUP-ID="bipbop_audio",LANGUAGE="eng",NAME="BipBop Audio 2", 
 AUTOSELECT=NO,DEFAULT=NO,URI="alternate_audio_aac/prog_index.m3u8" 
#EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="English",AUTOSELECT=YES,FORCED=NO, 
 LANGUAGE="eng",URI="subtitles/eng/prog_index.m3u8" 
#EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="English (Forced)",DEFAULT=YES, 
 AUTOSELECT=YES,FORCED=YES,LANGUAGE="eng",URI="subtitles/eng_forced/prog_index.m3u8" 
#EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="Français",AUTOSELECT=YES,FORCED=NO, 
 LANGUAGE="fra",URI="subtitles/fra/prog_index.m3u8" 
#EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=263851,CODECS="mp4a.40.2, avc1.4d400d", 
 RESOLUTION=416x234,AUDIO="bipbop_audio",SUBTITLES="subs"  
gear1/prog_index.m3u8 
#EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=577610,CODECS="mp4a.40.2, avc1.4d401e", 
 RESOLUTION=640x360,AUDIO="bipbop_audio",SUBTITLES="subs" 
gear2/prog_index.m3u8 
... 
```
