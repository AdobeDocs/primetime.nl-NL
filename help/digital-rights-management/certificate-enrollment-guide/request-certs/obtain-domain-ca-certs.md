---
title: Domein CA-certificaten verkrijgen
description: Domein CA-certificaten verkrijgen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---


# Domein CA-certificaten verkrijgen{#obtain-domain-ca-certificates}

In tegenstelling tot de Server van de Vergunning, wordt de Packager of het certificaat van het Vervoer van het Vervoer, het certificaat van MAC van het Domein niet uitgegeven door Adobe. U kunt dit certificaat verkrijgen van een certificeringsinstantie of u kunt een zelfondertekend certificaat genereren om dit te gebruiken.

Het certificaat van MAC van het Domein zou een sleutel met 1024 bits moeten gebruiken en de standaardattributen bevatten die in een certificaat van CA worden vereist:

* De basis uitbreiding van Beperkingen met de vlag van CA die aan waar wordt geplaatst
* Sleutelgebruiksextensie waarmee wordt opgegeven dat Certificaat is ondertekend, is toegestaan

Met OpenSSL kunt u bijvoorbeeld als volgt een zelfondertekend CA-certificaat genereren:

1. Maak een bestand met de naam [!DNL ca-extensions.txt] dat het volgende bevat:

   ```
   keyUsage=critical,keyCertSign  
   basicConstraints=critical,CA:TRUE  
   subjectKeyIdentifier=hash 
   ```

1. Sleutel genereren:

   ```
   openssl genrsa -des3 -out domain-ca.key 1024 
   ```

1. CSR genereren:

   ```
   openssl req -new -key domain-ca.key -out domain-ca.csr 
   ```

1. Certificaat genereren:

   ```
   openssl x509 -req -days 365 -in domain-ca.csr -signkey domain-ca.key \ 
     -out domain-ca.cer -extfile ca-extensions.txt 
   ```

1. Wachtwoord genereren:

   ```
   openssl rand -base64 8 
   ```

1. PFX genereren:

   ```
   openssl pkcs12 -export -inkey domain-ca.key \ 
   -in domain-ca.cer -out domain-ca.pfx
   ```

