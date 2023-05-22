---
title: De server instellen en implementeren voor beveiligde streaming
description: De server instellen en implementeren voor beveiligde streaming
copied-description: true
exl-id: de1488e6-ccee-49e6-999e-6c6762dd55be
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# De server instellen en implementeren voor beveiligde streaming {#set-up-and-deploy-the-server-for-protected-streaming}

1. Stel de configuratiemap in op de Primetime DRM DVD:

   `\Adobe Access Server for Protected Streaming\configs\`
1. Het voorbeeld kopiëren `configs` map naar uw `<Tomcat_installation_dir>` en wijzig de naam van de gekopieerde map in `licenseserver`.

   Het pad naar de map configs moet nu `<Tomcat_install_dir>\licenseserver\`.
1. Uitvoeren `Scrambler.bat` om de gecodeerde wachtwoorden voor de vervoer en vergunning server PFX- dossiers in Primetime DRM te verkrijgen `<DVD>` `\Adobe Access Server for Protected Streaming\` map:

   * `Scrambler.bat <Adobe-provided transport credential password>`
   * `Scrambler.bat <Adobe-provided license server credential password>`

1. De PFX-bestanden kopiëren naar de `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\<tenant-name>\` directory.
1. Geef de overeenkomstige huurdersconfiguratie in uit `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\sampletenant\flashaccess-tenant.xml`, met de volgende instellingen:

   ```
   Configuration|Tenant|Credentials|TransportCredential|File|path=<filename-transport-credential-PFX> 
   Configuration|Tenant|Credentials|TransportCredential|File|password=<scrambled-transportcredential-password> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|path=<fielname-license-servercredential-PFX> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|password=<scrambled-license-servercredential-password>
   ```

1. Voer de `Validator.bat` Het nut om configuratie te verifiëren is geldig:

   ```
   Validator.bat -g -r <absolute-path-to TomcatInstallDir\licenseserver>
   ```

1. Kopieer de `flashaccessserver.war` bestand van de cd naar de `<TomcatInstallDir>\webapps\` directory.
1. Als Tomcat wordt uitgevoerd, onderbreekt u de actieve Tomcat-instantie door op `<CTRL-C>` in het opdrachtvenster (als deze functie is gestart vanuit het opdrachtvenster). U kunt de server van de toepassing van de Diensten van Vensters ook tegenhouden als Tomcat als Dienst van Vensters werd geïnstalleerd.
1. Voer de volgende opdracht in om Tomcat te starten:

   ```
   <TomcatInstallDir>\bin\catalina run
   ```

1. Voer de volgende URL in een browser in om de instelling te controleren:

   ```
    https://<LicenseServer>:8080/flashaccessserver/flashaccess/license/v2
   ```
