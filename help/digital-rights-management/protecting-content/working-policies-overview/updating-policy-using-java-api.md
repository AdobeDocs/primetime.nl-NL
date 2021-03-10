---
title: Een DRM-beleid bijwerken met de Java API
description: Een DRM-beleid bijwerken met de Java API
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# Een DRM-beleid bijwerken met de Java API {#updating-a-drm-policy-with-the-java-api}

Een DRM-beleid bijwerken met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden vermeld in [De ontwikkelomgeving instellen](../../protecting-content/setting-up-the-sdk/setup-dev-env.md).
1. Maak een DRM `Policy`-instantie en lees het DRM-beleid vanuit een bestand of database.

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. Werk het DRM `Policy` voorwerp door zijn eigenschappen, zoals zijn naam en gebruiksregels te plaatsen bij.

   ```java
   // Change the DRM policy name.  
   policy.setName("UpdatedDemoPolicy");  
   
   // Add DRM module restrictions to the play right  
   for (Right r: policy.getRights()) {  
       if (r instanceof PlayRight) {  
           PlayRight pr = (PlayRight) r;  
           // Disallow Linux versions up to and including 1.9.  Allow  
           // all other OSes and Linux versions above 1.9  
           VersionInfo toExclude = new VersionInfo();  
           toExclude.setOS("Linux");  
           toExclude.setReleaseVersion("1.9");  
           Collection<VersionInfo> exclusions = new ArrayList<VersionInfo>();  
           exclusions.add(toExclude);  
           ModuleRequirements drmRestrictions = new ModuleRequirements();  
           drmRestrictions.setExcludedVersions(exclusions);  
           pr.setDRMModuleRequirements(drmRestrictions);  
           break;  
       }  
   }
   ```

1. Serialiseren van het bijgewerkte DRM `Policy`-object en opslaan dit in een bestand of database.

   ```java
   // Serialize the DRM policy.  
   byte[] policyBytes = policy.getBytes();  
   System.out.println("New DRM policy revision number: "  
       +  policy.getRevision());      
   // Write the DRM policy to a file.   
   // Alternatively, the DRM policy may be stored in a database.  
   FileOutputStream out = new FileOutputStream("demopolicy-updated.pol");  
   out.write(policyBytes);  
   out.close();
   ```

Zie `com.adobe.flashaccess.samples.policy.UpdatePolicy` in de folder van de Hulpmiddelen [!DNL samples] van de Lijn van het Bevel van de Implementatie van de Verwijzing voor de bron van deze steekproefcode.
