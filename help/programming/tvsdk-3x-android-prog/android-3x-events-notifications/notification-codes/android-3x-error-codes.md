---
title: PSDK-foutcodes
description: Informatie over verschillende foutcodes, waarschuwingen en native foutcodes.
translation-type: tm+mt
source-git-commit: eddc327087411a6214cfd8dafef66b850a603f97

---


# PSDK-foutcodes {#psdk-error-codes}

Lees verder voor meer informatie over PSDK-foutcodes, waarschuwingen en native foutcodes.

## Fouten

In de volgende tabel vindt u gedetailleerde informatie over meldingen van FOUTtypen. De meeste fouten bevatten relevante metagegevens. bijvoorbeeld de URL van de bron die niet is gedownload. Sommige meldingen bevatten metagegevens om op te geven of het probleem is opgetreden in de hoofdvideo-inhoud, in de alternatieve audio-inhoud of in een advertentie.

<table frame="all" colsep="1" rowsep="1">
  <tr> 
   <th><b>PSDK-foutnaam</b></th>
   <th><b>PSDK-foutcode</b></th>
   <th><b>Beschrijving</b></th>
  </tr>
  <tr>
    <td>SUCCES</td>
    <td>0</td>
    <td>Bewerking uitgevoerd door onderliggende API is geslaagd.</td>
  </tr>
  <tr>
    <td>INVALID_ARGUMENT</td>
    <td>1</td>
    <td>Gegevens of argumentnotatie die aan de onderliggende API zijn opgegeven, zijn ongeldig.</td>
  </tr>
  <tr>
    <td>NULL_POINTER</td>
    <td>2</td>
    <td>Een van de doorgegeven argumenten is NULL of een van de interne leden is niet geïnitialiseerd.</td>
  </tr>
  <tr>
    <td>ILLEGAL_STATE</td>
    <td>3</td>
    <td>De bewerking wordt niet ondersteund in de huidige spelerstatus.</td>
  </tr>
  <tr>
    <td>INTERFACE_NOT_FOUND</td>
    <td>4</td>
    <td>De interfaceCast methode werpt deze fout wanneer de gevraagde interface niet wordt uitgevoerd/door dit wordt geërft.</td>
  </tr>
  <tr>  
    <td>CREATION_FAILED</td>
    <td>5</td>
    <td>Maken van een van de interne bronnen is mislukt.</td>
  </tr>
  <tr>
    <td>UNSUPPORTED_OPERATION</td>
    <td>6</td>
    <td>De gewenste bewerking wordt momenteel niet ondersteund.</td>
  </tr>
  <tr>
    <td>DATA_NOT_AVAILABLE</td>
    <td>7</td>
    <td>De gevraagde gegevens zijn momenteel niet beschikbaar.</td>
  </tr>
  <tr>
    <td>ZOEKEN_FOUT</td>
    <td>8</td>
    <td>Er is een fout opgetreden tijdens het uitvoeren van een zoekbewerking.</td>
  </tr>
  <tr>
    <td>UNSUPPORTED_FEATURE</td>
    <td>9</td>
    <td>Deze functie/functie wordt niet ondersteund.</td>
  </tr>
  <tr>
    <td>RANGE_ERROR</td>
    <td>10</td>
    <td>De opgegeven waarde ligt buiten het bereik.</td>
  </tr>
  <tr>
    <td>CODEC_NOT_SUPPORTED</td>
    <td>11</td>
    <td>De audio-/videocodec van een bepaalde stream wordt niet ondersteund door TVSDK of door het onderliggende apparaat.</td>
  </tr>
  <tr>
    <td>MEDIA_ERROR</td>
    <td>12</td>
    <td>De opgegeven media is niet gevonden.</td>
  </tr>
  <tr>
    <td>NETWORK_ERROR</td>
    <td>13</td>
    <td>Er is een fout opgetreden tijdens het downloaden van een fragment of segment (zowel video als audio).</td>
  </tr>
  <tr>
    <td>GENERIC_ERROR</td>
    <td>14</td>
    <td>Algemene foutgebeurtenis. Niet daadwerkelijk uitgegeven door TVSDK. Dit is slechts een markering voor het einde van het bereik van numerieke codes die overeenkomen met TVSDK-foutgebeurtenissen.</td>
  </tr>
  <tr>
    <td>INVALID_SEEK_TIME</td>
    <td>15</td>
    <td>De opgegeven zoektijd is ongeldig.</td>
  </tr>
  <tr>
    <td>AUDIO_TRACK_ERROR</td>
    <td>16</td>
    <td>Er is een fout opgetreden met betrekking tot een audiotrack (Alternatieve audio)</td>
  </tr>
  <tr>
    <td>ACCESS_FROM_DIFFERENT_THREAD</td>
    <td>17</td>
    <td>PSDK API wordt geroepen van verschillende draad dan de draad waarin PSDK werd geïnitialiseerd.</td>
  </tr>
  <tr>
    <td>ELEMENT_NOT_FOUND</td>
    <td>18</td>
    <td>Het element is niet gevonden.</td>
  </tr>
  <tr>
    <td>NOT_IMPLEMENTED</td>
    <td>19</td>
    <td>Functie niet geïmplementeerd.</td>
  </tr>
  <tr>
    <td>PRE_ROLL_DISABLED</td>
    <td>20</td>
    <td>Voorwaarde is uitgeschakeld via AdvertisingMetadata.</td>
  </tr>
  <tr>
    <td>PLAYBACK_NOT_AUZED</td>
    <td>57</td>
    <td>Het afspelen van HLS is niet ingeschakeld in Flash Player. Zie AuthorizedFeatures.enableMediaPlayerHLSPlayback().</td>
  </tr>
  <tr>
    <td>NETWORK_TIMEOUT</td>
    <td>58</td>
    <td>Netwerk is uitgelijnd tijdens het ophalen van een resource/verbindingsserver.</td>
  </tr>
</table>

## Waarschuwingen

De volgende lijst verstrekt gedetailleerde informatie over WARN typeberichten.
De meeste waarschuwingen bevatten relevante metagegevens. bijvoorbeeld de URL van de bron die niet is gedownload. Sommige meldingen bevatten metagegevens om op te geven of het probleem is opgetreden in de hoofdvideo-inhoud, in de alternatieve audio-inhoud of in een advertentie.

<table frame="all" colsep="1" rowsep="1">
  <tr>
    <th><b>Foutnaam</b></th>
    <th><b>Code</b></th>
    <th><b>Beschrijving</b></th>
  </tr>
  <tr>
    <td>PLAYBACK_OPERATION_FAILED</td>
    <td>200</td>
    <td>Er is een fout opgetreden tijdens het afspelen. Een afspeelbewerking is mislukt</td>
  </tr>
  <tr>  
    <td>NATIVE_WARNING</td>
    <td>201</td>
    <td>De AVE-bibliotheek op laag niveau heeft een fout gegenereerd.</td>
  </tr>
  <tr>
    <td>AD_RESOLVER_FAILED</td>
    <td>202</td>
    <td>Advertenties zijn niet opgelost met de insteekmodule.</td>
  </tr>
  <tr>
    <td>AD_MANIFEST_LOAD_FAILED</td>
    <td>203</td>
    <td>Kan advertentiemanifest niet laden.</td>
  </tr>
  <tr>
    <td>AD_RESOLUTION_IN_PROGRESS</td>
    <td>204</td>
    <td>Bewerking voor het oplossen van advertenties wordt uitgevoerd.</td>
  </tr>
  </table>

## Info

<table frame="all" colsep="1" rowsep="1">
  <tr> 
    <th><b>Foutnaam</b></th>
    <th><b>Code</b></th>
    <th><b>Beschrijving</b></th>
  </tr>
  <tr>
    <td>REVENUE_OPTIMIZATION_REPORTING</td>
    <td>300</td>
    <td>gedetailleerde kennisgevingen van TVSDK voor verdere rapportage en analyse.</td>
  </tr>
 </table>

## Native foutcodes

De interface Video Encoder van AVE keert deze videoplaybackberichten in het NATIVE_ERROR meta-gegevensvoorwerp terug.

<table frame="all" colsep="1" rowsep="1">
  <tr>
    <th><b>Foutnaam</b></th>
    <th><b>Code</b></th>
    <th><b>Beschrijving</b></th>
  </tr>
  <tr>  
    <td>END_OF_PERIOD</td>
    <td>-1</td>
    <td>Einde van periode.</td>
  </tr>
  <tr>
    <td>SUCCES</td>
    <td>0</td>
    <td>Bewerking gelukt.</td>
  </tr>
  <tr>
    <td>ASYNC_OPERATION_IN_PROGRESS</td>
    <td>1</td>
    <td>Asynchrone bewerking. Het verzoek om een bewerking is uitgevoerd. Informatie over succes/fout is later beschikbaar.</td>
  </tr>
  <tr>
    <td>EOF</td>
    <td>2</td>
    <td>Bewerking niet mogelijk vanwege voorwaarde van einde van bestand (EOF).</td>
  </tr>
  <tr>
    <td>DECODER_FAILED</td>
    <td>3</td>
    <td>De decoder is mislukt bij uitvoering.</td>
  </tr>
  <tr>
    <td>DEVICE_OPEN_ERROR</td>
    <td>4</td>
    <td>Kan hardwaredecoder niet openen.</td>
  </tr>
  <tr>
    <td>FILE_NOT_FOUND</td>
    <td>5</td>
    <td>De bron kan niet worden gevonden.</td>
  </tr>
  <tr>
    <td>GENERIC_ERROR</td>
    <td>6</td>
    <td>Algemene fout.</td>
  </tr>
  <tr>
    <td>IRRECOVERABLE_ERROR</td>
    <td>7</td>
    <td>Een foutvoorwaarde waarvan de video-engine niet kan worden hersteld.</td>
  </tr>
  <tr>
    <td>LOST_CONNECTION_RECOVERABLE</td>
    <td>8</td>
    <td>Netwerkfout, probeert te herstellen.</td>
  </tr>
  <tr> 
    <td>NO_FIXED_SIZE</td>
    <td>9</td>
    <td>De grootte van de bron kan niet worden bepaald.</td>
  </tr>
  <tr>
    <td>NOT_IMPLEMENTED</td>
    <td>10</td>
    <td>Functie niet geïmplementeerd.</td>
  </tr>
  <tr>
    <td>OUT_OF_MEMORY</td>
    <td>11</td>
    <td>Onvoldoende geheugen.</td>
  </tr>
  <tr>
    <td>PARSE_ERROR</td>
    <td>12</td>
    <td>Fout bij het parseren van het mediabestand.</td>
  </tr>
  <tr>  
    <td>SIZE_UNKNOWN</td>
    <td>13</td>
    <td>De bron heeft een grootte, maar het is onbekend.</td>
  </tr>
  <tr>  
    <td>UNDER_FLOW</td>
    <td>14</td>
    <td>Onderstroomvoorwaarde.</td>
  </tr>
  <tr> 
    <td>UNSUPPORTED_CONFIG</td>
    <td>15</td>
    <td>Configuration is not supported.</td>
  </tr>
  <tr>  
    <td>UNSUPPORTED_OPERATION</td>
    <td>16</td>
    <td>Bewerking wordt niet ondersteund.</td>
  </tr>
  <tr>
    <td>WAITING_FOR_INIT</td>
    <td>17</td>
    <td>Nog niet geïnitialiseerd.</td>
  </tr>
  <tr>  
    <td>INVALID_PARAMETER</td>
    <td>18</td>
    <td>Ongeldige parameter.</td>
  </tr>
  <tr>
    <td>INVALID_OPERATION</td>
    <td>19</td>
    <td>Bewerking niet toegestaan.</td>
  </tr>
  <tr>
    <td>OP_ONLY_ALLOWED_IN_PAUSED_STATE</td>
    <td>20</td>
    <td>De bewerking is alleen toegestaan tijdens het pauzeren.</td>
  </tr>
  <tr> 
    <td>OP_INVALID_WITH_AUDIO_ONLY_FILE</td>
    <td>21</td>
    <td>Bewerking kan niet worden gebruikt voor bestanden met alleen audio.</td>
  </tr>
  <tr>
    <td>PREVIOUS_STEP_SEEK_IN_PROGRESS</td>
    <td>22</td>
    <td>De vorige zoekbewerking wordt nog uitgevoerd.</td>
  </tr>
  <tr> 
    <td>SOURCE_NOT_SPECIFIED</td>
    <td>23</td>
    <td>Bron niet opgegeven.</td>
  </tr>
  <tr>
    <td>RANGE_ERROR</td>
    <td>24</td>
    <td>De opgegeven waarde ligt buiten het bereik.</td>
  </tr>
  <tr>
    <td>INVALID_SEEK_TIME</td>
    <td>25</td>
    <td>Ongeldige zoektijd.</td>
  </tr>
  <tr>
    <td>FILE_STRUCTURE_INVALID</td>
    <td>26</td>
    <td>Het opgegeven bestand voldoet niet aan de verwachte syntaxis.</td>
  </tr>
  <tr>
    <td>COMPONENT_CREATION_FAILURE</td>
    <td>27</td>
    <td>Een essentieel onderdeel kan niet worden gemaakt.</td>
  </tr>
  <tr>
    <td>DRM_INIT_ERROR</td>
    <td>28</td>
    <td>Kan DRM-context niet maken.</td>
  </tr>
  <tr>
    <td>CONTAINER_NOT_SUPPORTED</td>
    <td>29</td>
    <td>Containertype wordt niet ondersteund.</td>
  </tr>
  <tr>
    <td>SEEK_FAILED</td>
    <td>30</td>
    <td>Seek is mislukt.</td>
  </tr>
  <tr>
    <td>CODEC_NOT_SUPPORTED</td>
    <td>31</td>
    <td>Niet-ondersteunde codec.</td>
  </tr>
  <tr>
    <td>NETWORK_UNAVAILABLE</td>
    <td>32</td>
    <td>Netwerk is niet beschikbaar.</td>
  </tr>
  <tr>  
    <td>NETWORK_ERROR</td>
    <td>33</td>
    <td>Fout die gegevens van het Netwerk krijgt.</td>
  </tr>
  <tr>
    <td>OVERLOOP</td>
    <td>34</td>
    <td>Overloop.</td>
  </tr>
  <tr>  
    <td>VIDEO_PROFILE_NOT_SUPPORTED</td>
    <td>35</td>
    <td>Niet-ondersteund videoprofiel.</td>
  </tr>
  <tr>
    <td>PERIOD_NOT_LOADED</td>
    <td>36</td>
    <td>Er is geprobeerd een bewerking uit te voeren in een wachttijd of een periode die nog niet is geladen.</td>
  </tr>
  <tr> 
    <td>INVALID_REPLACE_DURATION</td>
    <td>37</td>
    <td>De opgegeven vervangingsduur is ongeldig of loopt voorbij het einde van de stream.</td>
  </tr>
  <tr>
    <td>CALLED_FROM_WRONG_THREAD</td>
    <td>38</td>
    <td>API kan niet worden geroepen van de verkeerde draad. Meestal geldt dit voor API-elementen die alleen vanuit de hoofdthread moeten worden aangeroepen.</td>
  </tr>
  <tr>
    <td>FRAGMENT_READ_ERROR</td>
    <td>39</td>
    <td>Fout bij lezen van fragment. Geen failover aanwezig. De engine probeert het volgende fragment te lezen.</td>
  </tr>
  <tr>
    <td>GEABORTEERD</td>
    <td>40</td>
    <td>De bewerking is afgebroken door een expliciete aanroep Afbreken of Vernietig.</td>
  </tr>
  <tr>
    <td>UNSUPPORTED_HLS_VERSION</td>
    <td>41</td>
    <td>Kan deze versie van HLS-media niet afspelen.</td>
  </tr>
  <tr>
    <td>CANNOT_FAIL_OVER</td>
    <td>42</td>
    <td>Kan niet negeren.</td>
  </tr>
  <tr> 
    <td>HTTP_TIME_OUT</td>
    <td>43</td>
    <td>Er is een time-out opgetreden tijdens het downloaden van HTTP.</td>
  </tr>
  <tr>
    <td>NETWORK_DOWN</td>
    <td>44</td>
    <td>De netwerkverbinding van de gebruiker is verbroken. Het afspelen kan op elk moment worden gestopt en wordt hervat wanneer de verbinding beschikbaar is.</td>
  </tr>
  <tr>
    <td>NO_USABLE_BITRATE_PROFILE</td>
    <td>45</td>
    <td>Geen bruikbaar bitsnelheidprofiel gevonden in de stream.</td>
  </tr>
  <tr>
    <td>BAD_MANIFEST_SIGNATURE</td>
    <td>46</td>
    <td>Het manifest heeft een slechte handtekening. De manifestondertekeningstest is mislukt.</td>
  </tr>
  <tr>
    <td>CANNOT_LOAD_PLAYLIST</td>
    <td>47</td>
    <td>Kan een afspeellijst niet laden.</td>
  </tr>
  <tr>
    <td>REPLACEMENT_FAILED</td>
    <td>48</td>
    <td>Vervanging opgegeven in een API voor invoegen is mislukt. Dit betekent dat de invoeging is gelukt, maar dat de vervanging niet heeft plaatsgevonden. Vervanging kan mislukken als het te vervangen manifest uit de tijdlijn is verwijderd.</td>
  </tr>
  <tr>
    <td>SWITCH_TO_ASYMMETRIC_PROFILE</td>
    <td>49</td>
    <td>DRM schakelt over naar een asymmetrisch profiel. Van alle profielen wordt verwacht dat ze in de duur zijn uitgelijnd. Als dat niet het geval is, wordt deze waarschuwing gegenereerd en kan het afspelen schokken.</td>
  </tr>
  <tr>
    <td>LIVE_WINDOW_MOVED_BACKWARD</td>
    <td>50</td>
    <td>Van een actief venster wordt alleen de volgende verplaatsing verwacht. Als dat niet het geval is, wordt deze waarschuwing gegenereerd en wordt het venster niet gelezen. Hierdoor kan het afspelen schokken (of stoppen/lang pauzeren) veroorzaken.</td>
  </tr>
  <tr>
    <td>CURRENT_PERIOD_EXPIRED</td>
    <td>51</td>
    <td>Live venster wordt na de huidige periode verplaatst.</td>
  </tr>
  <tr>
    <td>CONTENT_LENGTH_MISMATCH</td>
    <td>52</td>
    <td>De lengte van de inhoud die door de HTTP-server wordt gerapporteerd, komt niet overeen met de werkelijke mediagrootte.</td>
  </tr>
  <tr>
    <td>PERIOD_HOLD</td>
    <td>53</td>
    <td>De mediaslezer kan geen verdere informatie lezen omdat deze de tijd heeft bereikt die door de setHoldAt API is ingesteld.</td>
  </tr>
  <tr>  
    <td>LIVE_HOLD</td>
    <td>54</td>
    <td>De mediaslezer kan geen segmenten laden omdat het einde van het live venster is bereikt. Het laden van segmenten wordt hervat wanneer de server nieuwe media aan het live venster toevoegt. Deze status wordt meestal bereikt als:<ul><li>De bufferTime is te hoog (gelijk aan of hoger dan de live vensterduur).</li><li>Een combinatie van een of meer API voor invoegen/wissen heeft meer media vervangen dan er zijn toegevoegd.</li><li>De volgende periode is een live periode met een media-vervanging die in behandeling is (vanwege de API-aanroep InsertBy)</li></ul></td>
  </tr>
  <tr>
    <td>BAD_MEDIA_INTERLEAVING</td>
    <td>55</td>
    <td>De audio- en video-interleave in de media is niet correct uitgevoerd. Dit is een verpakkingsfout. De waarschuwing wordt verzonden wanneer het verschil groter is dan twee seconden.</td>
  </tr>
  <tr>
    <td>DRM_NOT_AVAILABLE</td>
    <td>56</td>
    <td></td>
  </tr>
  <tr>  
    <td>PLAYBACK_NOT_AUZED</td>
    <td>57</td>
    <td>Het afspelen van HLS is niet ingeschakeld in Flash Player. Zie AuthorizedFeatures.enableHLSPlayback.</td>
  </tr>
  <tr>
    <td>BAD_MEDIA_SAMPLE_FOUND</td>
    <td>58</td>
    <td>De decoder heeft een ongeldig monster ontvangen dat niet kan worden gedecodeerd. Dit is meestal geen fatale fout, maar geeft aan dat er wellicht glitches in de audio/video voorkomen. Te veel exemplaren van deze fout geven een onjuiste codering of een ongeldig bestand aan.</td>
  </tr>
  <tr>
    <td>RANGE_SPANS_READ_HEAD</td>
    <td>59</td>
    <td>Nadat het afspelen is gestart, mag het bereik Invoegen/Vervangen niet de leeskop bevatten.</td>
  </tr>
  <tr> 
    <td>POSTROLL_WITH_LIVE_NOT_ALLOWED</td>
    <td>60</td>
    <td>Invoegingen achteraf zijn niet toegestaan op live media. Ze zijn echter wel toegestaan nadat de server de media als voltooid heeft gemarkeerd.</td>
  </tr>
  <tr>
    <td>INTERNAL_ERROR</td>
    <td>61</td>
    <td>Een zeer zeldzame kwestie die nooit zou mogen voorkomen.</td>
  </tr>
  <tr>  
    <td>SPS_PPS_FOUND_OUTSIDE_AVCC</td>
    <td>62</td>
    <td>De stream volgt niet de verpakkingsaanbeveling om H264 SPS/PPS altijd in een AVCC te plaatsen. Problemen met zoeken en afspelen kunnen worden gezien.</td>
  </tr>
  <tr>  
    <td>PARTIAL_REPLACEMENT</td>
    <td>63</td>
    <td>De in een API voor invoegen opgegeven vervanging is slechts gedeeltelijk uitgevoerd. Dit gebeurt wanneer replaceDuration zich over de chronologieduur uitstrekt.</td>
  </tr>
  <tr>
    <td>RENDITION_M3U8_ERROR</td>
    <td>64</td>
    <td>Er is een fout opgetreden bij het laden van de afspeellijst van de vertoning. Dit is alleen voor AVE, niet voor Flash Player.</td>
  </tr>
  <tr>
    <td>NULL_OPERATION</td>
    <td>65</td>
    <td>Bewerking doet niets.</td>
  </tr>
  <tr>
    <td>SEGMENT_SKIPPED_ON_FAILURE</td>
    <td>66</td>
    <td>Segment kan niet worden afgespeeld en wordt overgeslagen als de toepassing mislukt.</td>
  </tr>
  <tr>
    <td>INCOMPATIBLE_RENDER_MODE</td>
    <td>67</td>
    <td>Niet-compatibele rendermodus.</td>
  </tr>
  <tr>
    <td>PROTOCOL_NOT_SUPPORTED</td>
    <td>68</td>
    <td>Het webprotocol dat in de URL wordt gebruikt, wordt niet ondersteund.</td>
  </tr>
  <tr>
    <td>PARSE_ERROR_INCOMPATIBLE_VERSION</td>
    <td>69</td>
    <td>Fout bij parseren van mediabestand.</td>
  </tr>
  <tr>  
    <td>MANIFEST_FILE_UNEXPECTEDLY_CHANGED</td>
    <td>70</td>
    <td>Manifest-bestand is op een onverwachte manier gewijzigd.</td>
  </tr>
  <tr>
    <td>CANNOT_SPLIT_TIMELINE</td>
    <td>71</td>
    <td>Kan geen splitsingsbewerking op een tijdlijn uitvoeren.</td>
  </tr>
  <tr>
    <td>CANNOT_ERASE_TIMELINE</td>
    <td>72</td>
    <td>Kan geen wisbewerking op een tijdlijn uitvoeren.</td>
  </tr>
  <tr>
    <td>DID_NOT_GET_NEXT_FRAGMENT</td>
    <td>73</td>
    <td>Het volgende fragment is niet opgehaald.</td>
  </tr>
  <tr>
    <td>NO_TIMELINE</td>
    <td>74</td>
    <td>Geen tijdlijn aanwezig in een interne gegevensstructuur.</td>
  </tr>
  <tr>
    <td>LISTENER_NOT_FOUND</td>
    <td>75</td>
    <td>Geen listener gevonden in een interne gegevensstructuur.</td>
  </tr>
  <tr>
    <td>AUDIO_START_ERROR</td>
    <td>76</td>
    <td>Kan audio niet starten.</td>
  </tr>
  <tr>
    <td>NO_AUDIO_SINK</td>
    <td>77</td>
    <td>Er is geen audioband aanwezig in een interne gegevensstructuur.</td>
  </tr>
  <tr>  
    <td>FILE_OPEN_ERROR</td>
    <td>78</td>
    <td>Kan bestand niet openen.</td>
  </tr>
  <tr>
    <td>FILE_WRITE_ERROR</td>
    <td>79</td>
    <td>Kan niet naar een bestand schrijven.</td>
  </tr>
  <tr>
    <td>FILE_READ_ERROR</td>
    <td>80</td>
    <td>Kan niet lezen uit een bestand.</td>
  </tr>
  <tr>
    <td>ID3PARSE_ERROR</td>
    <td>81</td>
    <td>Er is een fout opgetreden bij het parseren van ID3-gegevens.</td>
  </tr>
  <tr>
    <td>SECURITY_ERROR</td>
    <td>82</td>
    <td>Het laden van de inhoud is mislukt vanwege beveiligingsbeperkingen.</td>
  </tr>
  <tr>
    <td>TIMELINE_TOO_SHORT</td>
    <td>83</td>
    <td>De tijdlijnduur is te kort. Als dit een live stream is, kan er vaak bufferen optreden.</td>
  </tr>
  <tr>
    <td>AUDIO_ONLY_STREAM_START</td>
    <td>84</td>
    <td>De stream is overgeschakeld naar een alleen-audio stream.</td>
  </tr>
  <tr>  
    <td>AUDIO_ONLY_STREAM_END</td>
    <td>85</td>
    <td>De stream is overgeschakeld van alleen-audio naar een stream met video.</td>
  </tr>
  <tr>
    <td>KEY_NOT_FOUND</td>
    <td>87</td>
    <td>Kan sleutel niet vinden.</td>
  </tr>
  <tr>
    <td>INVALID_KEY</td>
    <td>88</td>
    <td>De sleutel is ongeldig.</td>
  </tr>
  <tr>
    <td>KEY_SERVER_NOT_FOUND</td>
    <td>89</td>
    <td>Sleutelserver retourneert geen sleutel.</td>
  </tr>
  <tr>
    <td>MAIN_MANIFEST_UPDATE_TO_BE_HANDLED</td>
    <td>90</td>
    <td>Kan belangrijkste manifestupdate niet behandelen.</td>
  </tr>
  <tr>
    <td>UNREPORTED_TIME_DISCONTINUITY_FOUND</td>
    <td>91</td>
    <td>Ongemelde tijddiscontinuïteit (PTS) gevonden.</td>
  </tr>
  <tr>
    <td>UNMATCHED_AV_DISCONTINUITY_FOUND</td>
    <td>92</td>
    <td>Niet-overeenkomende audio- en videodiscontinuïteit gevonden.</td>
  </tr>
  <tr>
    <td>TRICKPLAY_ENDED_DUE_TO_ERROR</td>
    <td>93</td>
    <td>Er is een fout opgetreden tijdens het afspelen van media in de truc-afspeelmodus. De modus Steen afspelen wordt beëindigd en de stream wordt gepauzeerd. Roep Play() aan om de media in de normale modus af te spelen.</td>
  </tr>
  <tr>
    <td>LIVE_WINDOW_MOVED_AHEAD</td>
    <td>95</td>
    <td>De speler bevindt zich buiten het livevenster en moet voorwaarts proberen in te halen.</td>
  </tr>
</table>
