---
title: Een beleid bijwerken met de Java API
description: Een beleid bijwerken met de Java API
copied-description: true
exl-id: 1b03f033-0d29-46cc-ae14-d6fef96fe970
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# Een beleid bijwerken met de Java API {#updating-a-policy-using-the-java-api}

Voer de volgende stappen uit om een beleid bij te werken met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die in [De ontwikkelomgeving instellen](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) in uw project.
1. Een `Policy` -instantie en in het beleid lezen vanuit een bestand of database.

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. Werk de `Policy` objecten door zijn eigenschappen, zoals zijn naam en gebruiksregels te plaatsen.

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

1. De bijgewerkte versie serieel maken `Policy` en sla deze op in een bestand of database.

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

Voor de volledige bron van deze voorbeeldcode raadpleegt u `com.adobe.flashaccess.samples.policy.UpdatePolicy` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s van de naslagimplementatie.
