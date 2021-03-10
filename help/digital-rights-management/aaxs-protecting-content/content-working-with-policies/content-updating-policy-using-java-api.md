---
title: Een beleid bijwerken met de Java API
description: Een beleid bijwerken met de Java API
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# Een beleid bijwerken met de Java API {#updating-a-policy-using-the-java-api}

Voer de volgende stappen uit om een beleid bij te werken met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden vermeld in [De ontwikkelomgeving instellen](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) in uw project.
1. Maak een `Policy`-instantie en lees het beleid in vanuit een bestand of database.

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. Werk het `Policy` voorwerp door zijn eigenschappen, zoals zijn naam en gebruiksregels te plaatsen bij.

   ```java
     // Change the policy name.  
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

1. Serialiseren van het bijgewerkte `Policy`-object en opslaan dit in een bestand of database.

   ```java
      // Serialize the policy.  
      byte[] policyBytes = policy.getBytes();  
      System.out.println("New policy revision number: "  
       +  policy.getRevision());      
      // Write the policy to a file.   
      // Alternatively, the policy may be stored in a database.  
      FileOutputStream out = new FileOutputStream("demopolicy-updated.pol");  
      out.write(policyBytes);  
      out.close(); 
   ```

Voor de volledige bron van deze steekproefcode, zie `com.adobe.flashaccess.samples.policy.UpdatePolicy` in de folder van de &quot;steekproeven&quot;van de Hulpmiddelen van de Lijn van het Bevel van de Implementatie van de Verwijzing.
