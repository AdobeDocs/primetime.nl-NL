---
seo-title: Een DRM-beleid maken met de Java API
title: Een DRM-beleid maken met de Java API
uuid: 1672a6d0-e38c-4330-97b0-02147f99db47
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Een DRM-beleid maken met de Java API {#creating-a-drm-policy-with-the-java-api}

Een DRM-beleid maken met de Java API:

1. Stel uw ontwikkelomgeving in en neem in uw project alle JAR-bestanden op die in de ontwikkelomgeving [instellen staan.](../../protecting-content/setting-up-the-sdk/setup-dev-env.md).
1. Maak een `com.adobe.flashaccess.sdk.policy.Policy` object en geef de eigenschappen ervan op, zoals de rechten, de duur van het in cache plaatsen van licenties en de einddatum van het DRM-beleid.

   ```java
   // Create a new DRM policy object.  
   // False indicates the DRM policy does not use license chaining.  
   Policy policy = new Policy(false);  
   
   policy.setName("DemoPolicy");  
   
   // Specify that the DRM policy requires authentication to obtain a license.  
   policy.setLicenseServerInfo(new LicenseServerInfo(AuthenticationType.UsernamePassword));  
   
   // A DRM policy must have at least one Right, typically the play right  
   PlayRight play = new PlayRight();  
   
   // Users can only view content for 24 hours.  
   play.setPlaybackWindow(24L * 60 * 60);  
   
   // Add the play right to the DRM policy.  
   List<Right> rightsList = new ArrayList<Right>();  
   rightsList.add(play);  
   policy.setRights(rightsList);  
   
   // Licenses can be stored on the client for 7 days after downloading  
   policy.setLicenseCachingDuration(7L * 24 * 60 * 60);  
   try {  
       // Content will expire December 31, 2010  
       SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd");  
       policy.setPolicyEndDate(dateFormat.parse("2010-12-31"));  
   } catch (ParseException e) {  
       // Invalid date specified in dateFormat.parse()  
       e.printStackTrace();  
   } 
   ```

1. Serialiseer het DRM- `Policy` object en sla het op in een bestand of database.

   ```java
   // Serialize the DRM policy  
   byte[] policyBytes = policy.getBytes();  
   System.out.println("Created DRM policy with ID: " + policy.getId());  
   
   // Write the DRM policy to a file.   
   // Alternatively, the DRM policy may be stored in a database.  
   FileOutputStream out = new FileOutputStream("demopolicy.pol");  
   out.write(policyBytes);  
   out.close(); 
   ```

Zie [!DNL com.adobe.flashaccess.samples.policy.CreatePolicy] in de [!DNL samples] map Reference Implementation Command Line Tools voor de volledige bron van deze voorbeeldcode.
