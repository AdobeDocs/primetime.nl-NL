---
seo-title: De server instellen en implementeren voor beveiligde streaming
title: De server instellen en implementeren voor beveiligde streaming
uuid: 300a1b63-0bf0-48a8-977d-212563025c19
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# De server instellen en implementeren voor beveiligde streaming {#set-up-and-deploy-the-server-for-protected-streaming}

1. Stel de configuratiemap in op de Primetime DRM DVD:

   `\Adobe Access Server for Protected Streaming\configs\`
1. Kopieer de voorbeeldmap `configs` naar uw `<Tomcat_installation_dir>` en geef de gekopieerde map een andere naam naar `licenseserver`.

   Het pad naar de map configs moet nu `<Tomcat_install_dir>\licenseserver\` zijn.
1. Voer `Scrambler.bat` uit om de gecodeerde wachtwoorden voor de PFX-bestanden van de transport- en licentieserver in de directory Primetime DRM `<DVD>` `\Adobe Access Server for Protected Streaming\` te verkrijgen:

   * `Scrambler.bat <Adobe-provided transport credential password>`
   * `Scrambler.bat <Adobe-provided license server credential password>`

1. Kopieer de PFX-bestanden naar de map `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\<tenant-name>\`.
1. Bewerk de overeenkomende huurdersconfiguratie in `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\sampletenant\flashaccess-tenant.xml`, met de volgende instellingen:

   ```
   Configuration|Tenant|Credentials|TransportCredential|File|path=<filename-transport-credential-PFX> 
   Configuration|Tenant|Credentials|TransportCredential|File|password=<scrambled-transportcredential-password> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|path=<fielname-license-servercredential-PFX> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|password=<scrambled-license-servercredential-password>
   ```

1. Voer het hulpprogramma `Validator.bat` uit om te controleren of de configuratie geldig is:

   ```
   Validator.bat -g -r <absolute-path-to TomcatInstallDir\licenseserver>
   ```

1. Kopieer het bestand `flashaccessserver.war` van de cd naar de map `<TomcatInstallDir>\webapps\`.
1. Als Tomcat wordt uitgevoerd, stop de lopende instantie van Tomcat door `<CTRL-C>` in het bevelvenster te drukken (als het van het bevelvenster werd gelanceerd). U kunt de server van de toepassing van de Diensten van Vensters ook tegenhouden als Tomcat als Dienst van Vensters werd geïnstalleerd.
1. Voer de volgende opdracht in om Tomcat te starten:

   ```
   <TomcatInstallDir>\bin\catalina run
   ```

1. Voer de volgende URL in een browser in om de instelling te controleren:

   ```
    https://<LicenseServer>:8080/flashaccessserver/flashaccess/license/v2
   ```
