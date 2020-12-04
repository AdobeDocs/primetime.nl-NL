---
description: Als u aan de slag wilt met Primetime DRM Cloud, aangedreven door ExpressPlay, moet u Adobe Cert- en ExpressPlay-accounts instellen met de hulp van uw Adobe-medewerker.
seo-description: Als u aan de slag wilt met Primetime DRM Cloud, aangedreven door ExpressPlay, moet u Adobe Cert- en ExpressPlay-accounts instellen met de hulp van uw Adobe-medewerker.
seo-title: Provisioned (accounts, enz.)
title: Provisioned (accounts, enz.)
uuid: 51b95676-2121-4d8b-8756-9fd097185a13
translation-type: tm+mt
source-git-commit: 9792aff8586c46aabb5bfb70864cfe98c28e602d
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Provisioned (Accounts, etc.) {#get-provisioned-accounts-etc}

Als u aan de slag wilt met Primetime DRM Cloud, aangedreven door ExpressPlay, moet u Adobe Cert- en ExpressPlay-accounts instellen met de hulp van uw Adobe-medewerker.

1. Neem contact op met uw Adobe-vertegenwoordiger en vraag de Adobe Cert- en ExpressPlay-accounts aan die u nodig hebt voor de implementatie van Multi-DRM met TVSDK.

       Geef uw Adobe-vertegenwoordiger het e-mailadres op dat u als contactpunt wilt gebruiken. Adobe maakt dan twee accounts voor u:
   
   * ***Certificaatportalaccount*** - ( <span></span>https://certportal.primetime.adobe.com) : De  *Adobe Access / Primetime DRM-* team voor certificaatinschrijving verzendt een e-mail naar de adressen die u hun hebt opgegeven. De e-mail bevat de URL van de Adobe cert, samen met een koppeling naar de certificaatinschrijvingsdocumentatie voor het Adobe portal (de meest recente documenten zijn hier te vinden: [Handleiding voor certificaatinschrijving](../../../digital-rights-management/certificate-enrollment-guide/about-certs.md)).

   * ***ExpressPlay-account***  - Adobe verzendt u een e-mail met een koppeling die u gebruikt om u te registreren voor uw ExpressPlay-beheerdersaccount.

1. Meld u aan bij de portal Adobe cert met uw Adobe ID (gebruik hetzelfde e-mailadres dat u aan uw Adobe-vertegenwoordiger hebt opgegeven). Als u nog geen Adobe ID hebt, kunt u snel tot stand brengen door *een verbinding van Adobe ID* van het cert portaal te volgen:

   <!--<a id="fig_mst_gtj_wv"></a>-->

   ![](assets/cert_portal_sign-in-page-web.png)

1. Vraag op de portal Adobe cert een *Trial* cert aan.

   Voor de Multi-DRM-proefversie zal één proefcert alle volgende aspecten van de bescherming van inhoud omvatten: verpakking, licenties en vervoer. U zult uw eigen [CSR](../../../digital-rights-management/certificate-enrollment-guide/request-certs/gen-cert-signing-req.md) moeten leveren om een verzoek om een cert te doen:
   <!--<a id="fig_op1_xwj_wv"></a>-->

   ![](assets/cert_portal_trial_request-web.png)

   Adobe stuurt u een e-mail waarin wordt aangegeven dat u uw certificaataanvraag accepteert of afwijst. U kunt de status van uw certificaatverzoek(en) op het *Request history* lusje op het cert portaal zien:
   <!--<a id="fig_gkl_myj_wv"></a>-->

   ![](assets/cert_portal_request_history-web.png)

1. Maak uw ExpressPlay-beheerdersaccount.

   Volg de koppeling naar ExpressPlay die Adobe u ontvangt. Hierdoor wordt de pagina *Create an Account* bij ExpressPlay geopend. Vul de vereiste informatie in en verzend het formulier. U ontvangt een e-mail van `operations@expressplay.com` met een activeringskoppeling die een week goed is. Nadat u hebt geactiveerd, stelt u de ExpressPlay-service in:
   <!--<a id="fig_cjl_ztk_wv"></a>-->

   ![](assets/expressplay_create_service-web.png)

   Wanneer u uw service hebt gemaakt, krijgt u uw eigen beheerpagina te zien. Samen met sommige activiteit die gebieden volgen, zult u uw Productie en Test *klantenauthentificators* (API sleutels), en uw Productie en de dienst URLs van de Test zien:

   <!--<a id="fig_c5h_xdl_wv"></a>-->

   ![](assets/expressplay_admin_dashboard_2-web.png) ![](assets/expressplay_admin_dashboard-web.png)

1. Als u FairPlay gebruikt, zijn er extra stappen nodig (op de Apple Developer-site) om op te starten met ExpressPlay. Zie [ExpressPlay-service inschakelen voor FairPlay](../../multi-drm-workflows/p-l-and-p/fairplay-workflow.md#enable-expressplay-service-for-fairplay) voor instructies.
