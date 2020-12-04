---
seo-title: Overzicht van Primetime DRM Key Server implementeren
title: Overzicht van Primetime DRM Key Server implementeren
uuid: 86630675-c15d-4f32-8212-d7343f4f92e0
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---


# De primaire DRM-sleutelserver {#deploy-the-primetime-drm-key-server} implementeren

Voordat u de Primetime DRM-sleutelserver implementeert, moet u controleren of u de vereiste versies van Java en Tomcat hebt geïnstalleerd. Zie [DRM-essentiële serververeisten](../../digital-rights-management/using-the-drm-key-server/requirements.md).

Het downloaden van Primetime DRM Key Server omvat [!DNL faxsks.war]. Als u dit WAR-bestand wilt implementeren, kopieert u het bestand naar de map [!DNL webapps] van Tomcat. Als u het WAR-bestand eerder hebt geïmplementeerd, moet u mogelijk de onverpakte WAR-map [!DNL faxsks] in de map [!DNL webapps] van Tomcat handmatig verwijderen. Om te voorkomen dat Tomcat WAR-bestanden uitpakt, bewerkt u het [!DNL server.xml]-bestand in de map [!DNL conf] van Tomcat en stelt u het `unpackWARs`-kenmerk in op `false`.

De Primetime DRM-sleutelserver gebruikt optioneel een platformspecifieke bibliotheek (`jsafe.dll` in Windows of `libjsafe.so` in Linux) voor betere prestaties. Kopieer de desbetreffende bibliotheek voor uw platform van `thirdparty/cryptoj/platform` naar een locatie die is opgegeven door de omgevingsvariabele `PATH` (of `LD_LIBRARY_PATH` in Linux).

>[!NOTE]
>
>De 64-bits versie van de bibliotheek [!DNL jsafe] moet alleen worden gebruikt als zowel het besturingssysteem als JDK 64-bits ondersteunen, anders de 32-bits versie gebruiken.

## SSL-configuratie {#ssl-configuration}

SSL is vereist voor externe HTTPS-sleutellevering. De SSL-verbindingen kunnen worden afgehandeld door de toepassingsserver (d.w.z. door SSL te configureren in Tomcat) of kunnen worden afgehandeld op een andere server (d.w.z. een taakverdelingsmechanisme, SSL-versneller of Apache). Voor de externe HTTPS-sleutellevering is een SSL-verbinding vereist. De server heeft een SSL-certificaat nodig dat door een vertrouwde CA is uitgegeven.

Er zijn verschillende opties voor het configureren van SSL. Hieronder volgen voorbeelden voor het configureren van SSL met clientverificatie in Apache en Tomcat.

In het volgende voorbeeld wordt de configuratie van Apache SSL getoond:

```
SSLEngineon 
SSLCertificateFile "certs/server_cert.pem" 
SSLCertificateKeyFile "certs/server_key.pem" 
SSLOptions +StdEnvVars +FakeBasicAuth -ExportCertData +StrictRequire 
SSLRequireSSL 
ProxyRequests Off 
ProxyPass /https://keyserver-name:port/ 
ProxyPassReverse /https://keyserver-name:port/
```

In het volgende voorbeeld ziet u de Tomcat SSL-configuratie. Certificaat- en sleutelbestanden genereren:

```
Generate key:  
 openssl genrsa -des3 -out server.key 1024 
Generate CSR: 
 openssl req -new -key server.key -out server.csr 
Generate Certificate: 
 openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.cer
```

Wanneer ertoe aangezet voor de gemeenschappelijke naam, gebruik volledig - gekwalificeerde Naam van het Domein van uw server (FQDN).

Kopieer [!DNL server.cer] en [!DNL server.key] naar de Tomcat-map. Specificeer de volgende Schakelaar in [!DNL conf/server.xml]:

```
<Connector port="8443" protocol="HTTP/1.1" SSLEnabled="true" 
 maxThreads="150" scheme="https" secure="true" 
 sslProtocol="TLS" 
 SSLCertificateFile="${catalina.base}/server.cer" 
 SSLCertificateKeyFile="${catalina.base}/server.key" 
 SSLPassword="password-for-key-file" 
 SSLVerifyClient="require"/>
```

## Eigenschappen van Java-systemen {#java-system-properties}

U kunt de volgende twee eigenschappen van het Java-systeem instellen om de locatie van configuratie- en logbestanden voor de Primetime DRM-sleutelserver te wijzigen:

* `KeyServer.ConfigRoot` - Deze map bevat alle configuratiebestanden voor de Primetime DRM-sleutelserver. Zie [Belangrijke serverconfiguratiebestanden](#key-server-configuration-files) voor meer informatie over de inhoud van deze bestanden. Indien niet ingesteld, is de standaardwaarde [!DNL CATALINA_BASE/keyserver].

* `KeyServer.LogRoot` - Dit is een logmap die de toepassingslogbestanden van iOS Key Server bevat. Indien niet ingesteld, is de standaardwaarde gelijk aan `KeyServer.ConfigRoot`

* `XboxKeyServer.LogRoot` - Dit is een logboekfolder die de Xbox Key Server toepassingslogboeken bevat. Indien niet ingesteld, is de standaardwaarde gelijk aan `KeyServer.ConfigRoot`.

Als u [!DNL catalina.bat] of [!DNL catalina.sh] gebruikt om Tomcat te starten, kunnen deze systeemeigenschappen eenvoudig worden ingesteld met de omgevingsvariabele `JAVA_OPTS`. Alle Java-opties die hier zijn ingesteld, worden gebruikt wanneer Tomcat wordt gestart. Stel bijvoorbeeld:

```
JAVA_OPTS=-DKeyServer.ConfigRoot=”absolute-path-to-config-folder” 
  -DKeyServer.LogRoot=”absolute-path-to-log-folder”
```

## Primetime DRM-referenties {#primetime-drm-credentials}

Om zeer belangrijke verzoeken van Primetime DRM iOS en Xbox 360 cliënten te verwerken, moet de Belangrijkste Server van Primetime DRM met een reeks geloofsbrieven worden gevormd die door Adobe worden uitgegeven. Deze gegevens kunnen worden opgeslagen in PKCS#12-bestanden ( [!DNL .pfx]) of in een HSM-bestand.

De [!DNL .pfx] dossiers kunnen overal worden gevestigd, maar voor gemak van configuratie, adviseert Adobe het plaatsen van de [!DNL .pfx] dossiers in de de configuratiefolder van de huurder. Voor meer informatie, zie [Zeer belangrijke de configuratiedossiers van de Server](#key-server-configuration-files).

### HSM-configuratie {#section_13A19E3E32934C5FA00AEF621F369877}

Als u ervoor kiest om een HSM te gebruiken om uw servergeloofsbrieven op te slaan, moet u de privé sleutels en de certificaten op HSM laden en een *pkcs11.cfg* configuratiedossier creëren. Dit bestand moet zich in de map *KeyServer.ConfigRoot* bevinden. Zie de map `<Primetime DRM Key Server>/configs` voor een voorbeeld-PKCS 11-configuratiebestand. Raadpleeg de documentatie bij de Sun PKCS11-provider voor informatie over de indeling van [!DNL pkcs11.cfg].

Om te verifiëren dat uw HSM en PKCS11 configuratiedossiers van de Zon behoorlijk worden gevormd, kunt u het volgende bevel van de folder gebruiken waar het [!DNL pkcs11.cfg] dossier wordt gevestigd ( [!DNL keytool] wordt geïnstalleerd met Java JRE en JDK):

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Als u uw geloofsbrieven in de lijst ziet, wordt HSM gevormd behoorlijk en de Zeer belangrijke Server zal tot de geloofsbrieven kunnen toegang hebben.

## Belangrijke serverconfiguratiebestanden {#key-server-configuration-files}

Voor de Primetime DRM-sleutelserver zijn twee typen configuratiebestanden vereist:

* Een globaal configuratiebestand, [!DNL flashaccess-keyserver-global.xml]
* Een configuratiebestand van een huurder voor elke huurder, [!DNL flashaccess-keyserver-tenant.xml]

Als er wijzigingen worden aangebracht in de configuratiebestanden, moet de server opnieuw worden gestart om de wijzigingen van kracht te laten worden.

Om te voorkomen dat wachtwoorden in duidelijke tekst in de configuratiedossiers beschikbaar worden gemaakt, moeten alle wachtwoorden die in de globale en huurdersconfiguratiedossiers worden gespecificeerd worden gecodeerd. Voor meer informatie over het coderen van wachtwoorden, zie [*Wachtwoordkrambler* in *De Server van Primetime DRM voor Beschermde Streaming gebruiken*](../protected-streaming/understanding-deployment/drm-for-protected-streaming-utilities/password-scrambler.md).

## Configuratie van mapstructuur {#configuration-directory-structure}

De configuratiemappen hebben de volgende structuur:

```
KeyServer.ConfigRoot/  
--flashaccess-keyserver-global.xml 
--pkcs11.cfg (optional) 
--faxsks/ 
----tenants/ 
------tenantname/
---------flashaccess-keyserver-tenant.xml 
---------credential.pfx (optional) 
```

## Globaal configuratiebestand {#global-configuration-file}

Het configuratiebestand [!DNL flashaccess-keyserver-global.xml] bevat instellingen die van toepassing zijn op alle huurders van de sleutelserver. Dit bestand moet zich in `KeyServer.ConfigRoot` bevinden. Zie de map [!DNL configs] voor een voorbeeld van een globaal configuratiebestand. Het algemene configuratiebestand bevat het volgende:

* Logboekregistratie - Geeft het registratieniveau op en hoe vaak logbestanden worden gewist.
* HSM-wachtwoord - Alleen vereist als een HSM wordt gebruikt om serverreferenties op te slaan.

Zie de commentaren in het voorbeeld globale configuratiedossier in `<Primetime DRM Key Server>/configs` voor meer details wordt gevestigd die.

## Aanraakconfiguratiebestanden {#tenant-configuration-files}

De [!DNL flashaccess-ioskeyserver-tenant.xml] en [!DNL flashaccess-xboxkeyserver-tenant.xml] configuratiedossiers bevatten montages die op een specifieke huurder van de Belangrijkste Server van Primetime DRM van toepassing zijn. Elke huurder heeft zijn eigen instantie van deze configuratiedossiers die in [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname] worden gevestigd. Zie [!DNL configs/faxsks/tenants/sampletenant] folder voor een dossier van de voorbeeldhuurconfiguratie.

U kunt alle dossierwegen in het dossier van de huurdersconfiguratie als of absolute wegen of wegen met betrekking tot de de configuratiefolder van de huurder ( [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]) specificeren.

Alle configuratiebestanden van de huurder bevatten:

* Sleutelserverreferenties - Geeft een of meer sleutelserverreferenties (certificaat en persoonlijke sleutel) aan die door Adobe zijn uitgegeven. Kan worden opgegeven als een pad naar een [!DNL .pfx]-bestand en een wachtwoord, of als een alias voor een referentie die is opgeslagen op een HSM. Verscheidene dergelijke geloofsbrieven kunnen hier, of als dossierwegen, of belangrijkste aliassen, of allebei worden gespecificeerd.

Het **iOS** configuratiebestand voor de huurder bevat:

* Het zeer belangrijke Venster van de Levering - (Facultatief) specificeert zeer belangrijke het geldigheids venster van de het tijdstempel van de leveringsaanvraag (in seconden). De standaardwaarde is 500 seconden.

Het **Xbox 360** configuratiebestand voor huurders bevat:

* XSTS Credential - Geeft de referentie aan van de ontwikkelaar van de toepassing die wordt gebruikt om XSTS-tokens te decoderen
* XSTS-ondertekeningscertificaat - Geeft het certificaat op dat wordt gebruikt om de handtekening op XSTS-tokens te verifiëren.
* Packager Lijst van gewenste personen - Packager-certificaten die door de Key Server worden vertrouwd. Als de lijst geen pakketcertificaten bevat, worden alle pakketcertificaten vertrouwd.

## Logbestanden {#log-files}

De logbestanden die worden gegenereerd door de toepassing Primetime DRM Key Server ( [!DNL flashaccess-ioskeyserver_*.log] en [!DNL flashaccess-xboxkeyserver_*.log]) bevinden zich in de map die wordt opgegeven door `KeyServer.LogRoot`.

De logbestanden worden onderscheiden door het type client. Er zijn twee logboeken per cliënttype:

* An *access log* - Monitors request and responses only.
* A *contextlog* - Bevat gedetailleerde foutberichten en stacksporen.

## De toetsserver starten {#starting-the-key-server}

Start Tomcat om de Key Server te starten.