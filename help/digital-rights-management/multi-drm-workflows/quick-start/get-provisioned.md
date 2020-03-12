---
description: Als u aan de slag wilt met Primetime DRM Cloud, aangedreven door ExpressPlay, moet u Adobe Cert- en ExpressPlay-accounts instellen met de hulp van uw Adobe-vertegenwoordiger.
seo-description: Als u aan de slag wilt met Primetime DRM Cloud, aangedreven door ExpressPlay, moet u Adobe Cert- en ExpressPlay-accounts instellen met de hulp van uw Adobe-vertegenwoordiger.
seo-title: Provisioned (accounts, enz.)
title: Provisioned (accounts, enz.)
uuid: 51b95676-2121-4d8b-8756-9fd097185a13
translation-type: tm+mt
source-git-commit: 9792aff8586c46aabb5bfb70864cfe98c28e602d

---


# Provisioned (accounts, enz.) {#get-provisioned-accounts-etc}

Als u aan de slag wilt met Primetime DRM Cloud, aangedreven door ExpressPlay, moet u Adobe Cert- en ExpressPlay-accounts instellen met de hulp van uw Adobe-vertegenwoordiger.

1. Neem contact op met uw Adobe-vertegenwoordiger en vraag de Adobe Cert- en ExpressPlay-accounts aan die u nodig hebt voor de implementatie van Multi-DRM met TVSDK.

       Geef uw Adobe-vertegenwoordiger het e-mailadres op dat u als contactpunt wilt gebruiken. Adobe maakt vervolgens twee accounts voor u:
   
   * ***Certificaatportalaccount*** - (<span></span>https://certportal.primetime.adobe.com) : Het *Adobe Access-/Primetime DRM-certificaatinschrijvingsteam* verzendt een e-mail naar de adressen die u hen hebt verschaft. Het e-mailbericht bevat de URL voor het Adobe cert-portaal, samen met een koppeling naar de documentatie voor certificaatinschrijving van Adobe (de meest recente documenten zijn hier te vinden: Inschrijvingsgids voor [certificaten](../../../digital-rights-management/certificate-enrollment-guide/about-certs.md)).

   * ***ExpressPlay-account*** - Adobe stuurt u een e-mail met een koppeling die u gebruikt om u te registreren voor uw ExpressPlay-beheerdersaccount.

1. Meld u met uw Adobe-id aan bij het Adobe cert-portaal (gebruik hetzelfde e-mailadres dat u aan uw Adobe-vertegenwoordiger hebt verstrekt). Als u nog geen Adobe-id hebt, kunt u er snel een maken door de koppeling *Een Adobe-id* ophalen op te volgen van de portal Start:

   <!--<a id="fig_mst_gtj_wv"></a>-->

   ![](assets/cert_portal_sign-in-page-web.png)

1. Vraag op de Adobe cert-portal een *proefversie* aan.

   Voor de Multi-DRM-proefversie zal één proefcert alle volgende aspecten van de bescherming van inhoud omvatten: verpakking, licenties en vervoer. U zult uw eigen [CSR](../../../digital-rights-management/certificate-enrollment-guide/request-certs/gen-cert-signing-req.md) moeten leveren om een verzoek om een cert te doen:
   <!--<a id="fig_op1_xwj_wv"></a>-->

   ![](assets/cert_portal_trial_request-web.png)

   Adobe stuurt u een e-mail waarin wordt aangegeven dat u uw certificaataanvraag accepteert of afwijst. U kunt de status van uw certificaataanvraag(en) bekijken op het tabblad *Aanvraaggeschiedenis* op de certificaatportal:
   <!--<a id="fig_gkl_myj_wv"></a>-->

   ![](assets/cert_portal_request_history-web.png)

1. Maak uw ExpressPlay-beheerdersaccount.

   Volg de koppeling naar ExpressPlay die Adobe u heeft verschaft. Hiermee wordt de pagina *Create an Account* at ExpressPlay geopend. Vul de vereiste informatie in en verzend het formulier. U ontvangt een e-mail van `operations@expressplay.com` met een activeringskoppeling die een week goed is. Nadat u hebt geactiveerd, stelt u de ExpressPlay-service in:
   <!--<a id="fig_cjl_ztk_wv"></a>-->

   ![](assets/expressplay_create_service-web.png)

   Wanneer u uw service hebt gemaakt, krijgt u uw eigen beheerpagina te zien. Samen met sommige activiteit die gebieden volgen, zult u uw Productie en de *klantenauthenticators* van de Test (API sleutels), en uw Productie en dienst URLs van de Test zien:

   <!--<a id="fig_c5h_xdl_wv"></a>-->

   ![](assets/expressplay_admin_dashboard_2-web.png) ![](assets/expressplay_admin_dashboard-web.png)

1. Als u FairPlay gebruikt, zijn er extra stappen nodig (op de Apple Developer-site) om op te starten met ExpressPlay. Zie ExpressPlay-service [inschakelen voor FairPlay](../../multi-drm-workflows/p-l-and-p/fairplay-workflow.md#enable-expressplay-service-for-fairplay) voor instructies.
