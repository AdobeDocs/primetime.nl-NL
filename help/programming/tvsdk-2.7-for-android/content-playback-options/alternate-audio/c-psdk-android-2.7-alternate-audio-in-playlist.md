---
description: De afspeellijst voor een video kan een onbeperkt aantal alternatieve audiotracks voor de hoofdvideo-inhoud opgeven. U kunt bijvoorbeeld verschillende talen toevoegen aan uw video-inhoud of de gebruiker toestaan te schakelen tussen verschillende tracks op het apparaat terwijl de inhoud wordt afgespeeld.
seo-description: De afspeellijst voor een video kan een onbeperkt aantal alternatieve audiotracks voor de hoofdvideo-inhoud opgeven. U kunt bijvoorbeeld verschillende talen toevoegen aan uw video-inhoud of de gebruiker toestaan te schakelen tussen verschillende tracks op het apparaat terwijl de inhoud wordt afgespeeld.
seo-title: Alternatieve audiotracks in de afspeellijst
title: Alternatieve audiotracks in de afspeellijst
uuid: 47289392-ae4e-44b9-8d54-6ccee8fe1446
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Alternatieve audiotracks in de afspeellijst {#alternate-audio-tracks-in-the-playlist}

De afspeellijst voor een video kan een onbeperkt aantal alternatieve audiotracks voor de hoofdvideo-inhoud opgeven. U kunt bijvoorbeeld verschillende talen toevoegen aan uw video-inhoud of de gebruiker toestaan te schakelen tussen verschillende tracks op het apparaat terwijl de inhoud wordt afgespeeld.

Met alternatieve audiotracks kunnen gebruikers schakelen tussen meerdere geluidssporen voor HTTP-videostreams (live/lineair en VOD) en hoeft u de video voor elke audiotrack niet te wijzigen, dupliceren of opnieuw te verpakken. U kunt meerdere geluidssporen voor de taal van een video-element opgeven vóór of na het eerste pakket van het element.

>[!IMPORTANT]
>
>De alternatieve audio wordt alleen gemengd met de videotrack van de hoofdmedia als de tijdstempels van de alternatieve track overeenkomen met de tijdstempels van de audio in de hoofdtrack.

De hoofdaudiotrack wordt samen met het `default` label opgenomen in de audiotracks. Metagegevens voor de alternatieve audiostreams worden opgenomen in de afspeellijst in de `#EXT-X-MEDIA` tags met `TYPE=AUDIO`.

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

