---
title: Overzicht van Primetime DRM Key Server implementeren
description: Overzicht van Primetime DRM Key Server implementeren
copied-description: true
exl-id: d70e8315-ed35-4159-842b-5066a2b1c4f0
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---

# De primaire DRM-sleutelserver implementeren {#deploy-the-primetime-drm-key-server}

Voordat u de Primetime DRM-sleutelserver implementeert, moet u controleren of u de vereiste versies van Java en Tomcat hebt geïnstalleerd. Zie, [Vereisten voor DRM-sleutelserver](../../digital-rights-management/using-the-drm-key-server/requirements.md).

Het downloaden van Primetime DRM Key Server omvat [!DNL faxsks.war]. Als u dit WAR-bestand wilt implementeren, kopieert u het bestand naar Tomcat&#39;s [!DNL webapps] directory. Als u eerder het WAR-bestand hebt geïmplementeerd, moet u mogelijk de onverpakte WAR-map handmatig verwijderen. [!DNL faxsks] in Tomcat [!DNL webapps] directory). Als u wilt voorkomen dat Tomcat WAR-bestanden uitpakt, bewerkt u de opdracht [!DNL server.xml] bestand in Tomcat [!DNL conf] en stelt de `unpackWARs` kenmerk naar `false`.

De Primetime DRM-sleutelserver gebruikt optioneel een platformspecifieke bibliotheek (`jsafe.dll` in Windows of `libjsafe.so` in Linux) voor betere prestaties. Kopieer de juiste bibliotheek voor uw platform van `thirdparty/cryptoj/platform` naar een locatie die door de `PATH` omgevingsvariabele (of `LD_LIBRARY_PATH` in Linux).

>[!NOTE]
>
>De 64-bits versie van de [!DNL jsafe] Deze bibliotheek moet alleen worden gebruikt als zowel het besturingssysteem als JDK 64-bits ondersteunen. Als dit niet het geval is, gebruikt u de 32-bits versie.

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

Kopiëren [!DNL server.cer], en [!DNL server.key] naar de Tomcat-directory. Geef de volgende connector op in [!DNL conf/server.xml]:

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

* `KeyServer.ConfigRoot` - Deze map bevat alle configuratiebestanden voor de Primetime DRM-sleutelserver. Voor meer informatie over de inhoud van deze bestanden raadpleegt u [Sleutelserverconfiguratiebestanden](#key-server-configuration-files). Indien niet ingesteld, is de standaardwaarde [!DNL CATALINA_BASE/keyserver].

* `KeyServer.LogRoot` - Dit is een logmap die de toepassingslogbestanden van iOS Key Server bevat. Indien niet ingesteld, is de standaardwaarde gelijk aan `KeyServer.ConfigRoot`

* `XboxKeyServer.LogRoot` - Dit is een logboekfolder die de Xbox Key Server toepassingslogboeken bevat. Indien niet ingesteld, is de standaardwaarde gelijk aan `KeyServer.ConfigRoot`.

Als u [!DNL catalina.bat] of [!DNL catalina.sh] om Tomcat te starten, kunnen deze systeemeigenschappen eenvoudig worden ingesteld met de `JAVA_OPTS` omgevingsvariabele. Alle Java-opties die hier zijn ingesteld, worden gebruikt wanneer Tomcat wordt gestart. Stel bijvoorbeeld:

```
JAVA_OPTS=-DKeyServer.ConfigRoot=”absolute-path-to-config-folder” 
  -DKeyServer.LogRoot=”absolute-path-to-log-folder”
```

## Primetime DRM-referenties {#primetime-drm-credentials}

Om zeer belangrijke verzoeken van Primetime DRM iOS en Xbox 360 cliënten te verwerken, moet de Belangrijkste Server van Primetime DRM met een reeks geloofsbrieven worden gevormd die door Adobe worden uitgegeven. Deze gegevens kunnen worden opgeslagen in PKCS#12 ( [!DNL .pfx]) of op een HSM.

De [!DNL .pfx] bestanden kunnen overal worden gevonden, maar voor de eenvoudige configuratie raadt Adobe u aan de [!DNL .pfx] bestanden in de configuratiemap van de huurder. Zie voor meer informatie [Sleutelserverconfiguratiebestanden](#key-server-configuration-files).

### HSM-configuratie {#section_13A19E3E32934C5FA00AEF621F369877}

Als u ervoor kiest een HSM te gebruiken om uw serverreferenties op te slaan, moet u de persoonlijke sleutels en certificaten op de HSM laden en een *pkcs11.cfg* configuratiebestand. Dit bestand moet zich bevinden in het dialoogvenster *KeyServer.ConfigRoot* directory. Zie de `<Primetime DRM Key Server>/configs` voor een voorbeeld-PKCS 11-configuratiebestand. Voor informatie over het formaat van [!DNL pkcs11.cfg], zie de PKCS11 van de Zon leveranciersdocumentatie.

Om te verifiëren dat uw HSM en PKCS11 configuratiedossiers van de Zon behoorlijk worden gevormd, kunt u het volgende bevel van de folder gebruiken waar [!DNL pkcs11.cfg] bestand bevindt zich ( [!DNL keytool] wordt geïnstalleerd met de Java JRE en JDK):

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Als u uw geloofsbrieven in de lijst ziet, wordt HSM gevormd behoorlijk en de Zeer belangrijke Server zal tot de geloofsbrieven kunnen toegang hebben.

## Sleutelserverconfiguratiebestanden {#key-server-configuration-files}

Voor de Primetime DRM-sleutelserver zijn twee typen configuratiebestanden vereist:

* een algemeen configuratiebestand, [!DNL flashaccess-keyserver-global.xml]
* Een dossier van de huurdersconfiguratie voor elke huurder, [!DNL flashaccess-keyserver-tenant.xml]

Als er wijzigingen worden aangebracht in de configuratiebestanden, moet de server opnieuw worden gestart om de wijzigingen van kracht te laten worden.

Om te voorkomen dat wachtwoorden in duidelijke tekst in de configuratiedossiers beschikbaar worden gemaakt, moeten alle wachtwoorden die in de globale en huurdersconfiguratiedossiers worden gespecificeerd worden gecodeerd. Voor meer informatie over het coderen van wachtwoorden, zie [*Wachtwoordkrambler* in *De Primetime DRM-server gebruiken voor beveiligde streaming*](../protected-streaming/understanding-deployment/drm-for-protected-streaming-utilities/password-scrambler.md).

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

De [!DNL flashaccess-keyserver-global.xml] Het configuratiedossier bevat montages die op alle huurders van de Zeer belangrijke Server van toepassing zijn. Dit bestand moet zich bevinden in `KeyServer.ConfigRoot`. Zie de [!DNL configs] map voor een voorbeeld van een globaal configuratiebestand. Het algemene configuratiebestand bevat het volgende:

* Logboekregistratie - Geeft het registratieniveau op en hoe vaak logbestanden worden gewist.
* HSM-wachtwoord - Alleen vereist als een HSM wordt gebruikt om serverreferenties op te slaan.

Zie de opmerkingen in het algemene configuratiebestand van het voorbeeld in `<Primetime DRM Key Server>/configs` voor meer informatie .

## Aanraakconfiguratiebestanden {#tenant-configuration-files}

De [!DNL flashaccess-ioskeyserver-tenant.xml] en [!DNL flashaccess-xboxkeyserver-tenant.xml] configuratiebestanden bevatten instellingen die van toepassing zijn op een specifieke gebruiker van de Primetime DRM-sleutelserver. Elke huurder heeft zijn eigen geval van deze configuratiedossiers die in worden gevestigd [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]. Zie de [!DNL configs/faxsks/tenants/sampletenant] directory voor een voorbeeld van een configuratiebestand van de huurder.

U kunt alle dossierwegen in het dossier van de huurdersconfiguratie als of absolute wegen of wegen met betrekking tot de de configuratiemap van de huurder specificeren ( [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]).

Alle configuratiebestanden van de huurder bevatten:

* Sleutelserverreferenties - Geeft een of meer sleutelserverreferenties (certificaat en persoonlijke sleutel) aan die door Adobe zijn uitgegeven. Kan worden opgegeven als een pad naar een [!DNL .pfx] bestand en een wachtwoord, of een alias voor een referentie die is opgeslagen op een HSM. Verscheidene dergelijke geloofsbrieven kunnen hier, of als dossierwegen, of belangrijkste aliassen, of allebei worden gespecificeerd.

De **iOS** Het configuratiebestand van de huurder bevat:

* Het zeer belangrijke Venster van de Levering - (Facultatief) specificeert zeer belangrijke het geldigheids venster van de het tijdstempel van de leveringsaanvraag (in seconden). De standaardwaarde is 500 seconden.

De **Xbox 360** Het configuratiebestand van de huurder bevat:

* XSTS Credential - Geeft de referentie aan van de ontwikkelaar van de toepassing die wordt gebruikt om XSTS-tokens te decoderen
* XSTS-ondertekeningscertificaat - Geeft het certificaat op dat wordt gebruikt om de handtekening op XSTS-tokens te verifiëren.
* Packager Lijst van gewenste personen - Packager-certificaten die door de Key Server worden vertrouwd. Als de lijst geen pakketcertificaten bevat, worden alle pakketcertificaten vertrouwd.

## Logbestanden {#log-files}

De logbestanden die worden gegenereerd door de toepassing Primetime DRM Key Server ( [!DNL flashaccess-ioskeyserver_*.log] en [!DNL flashaccess-xboxkeyserver_*.log]) bevindt zich in de map die is opgegeven door `KeyServer.LogRoot`.

De logbestanden worden onderscheiden door het type client. Er zijn twee logboeken per cliënttype:

* An *toegangslogboek* - Bewaking van verzoeken en antwoorden.
* A *contextlogboek* - Bevat gedetailleerde foutberichten en stacksporen.

## De sleutelserver starten {#starting-the-key-server}

Start Tomcat om de Key Server te starten.
