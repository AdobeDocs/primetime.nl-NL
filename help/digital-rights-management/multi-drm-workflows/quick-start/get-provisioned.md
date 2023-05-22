---
description: Als u aan de slag wilt met Primetime DRM Cloud, aangedreven door ExpressPlay, moet u Adobe Cert- en ExpressPlay-accounts instellen met de hulp van uw Adobe-medewerker.
title: Provisioned (accounts, enz.)
exl-id: 2543d997-3495-4545-9395-072c07431aba
source-git-commit: a0917e128862184ce18050792c2ee2ac265050d2
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Provisioned (accounts, enz.) {#get-provisioned-accounts-etc}

Als u aan de slag wilt met Primetime DRM Cloud, aangedreven door ExpressPlay, moet u Adobe Cert- en ExpressPlay-accounts instellen met de hulp van uw Adobe-medewerker.

1. Neem contact op met uw Adobe-vertegenwoordiger en vraag de Adobe Cert- en ExpressPlay-accounts aan die u nodig hebt voor de implementatie van Multi-DRM met TVSDK.

   Geef uw Adobe-vertegenwoordiger het e-mailadres op dat u als contactpunt wilt gebruiken. Adobe maakt vervolgens twee accounts voor u:

   * ***Account certificaatportal*** - ( https://certportal.primetime.adobe.com) : De *Adobe Access/Primetime DRM-team voor certificaatinschrijving* verzendt een e-mail naar de adressen u hen verstrekte. De e-mail bevat de URL van de Adobe cert, samen met een koppeling naar de certificaatinschrijvingsdocumentatie voor het Adobe portal (de meest recente documenten zijn hier te vinden: [Handleiding voor certificaatinschrijving](../../../digital-rights-management/certificate-enrollment-guide/about-certs.md)).

   * ***ExpressPlay-account*** - Adobe stuurt u een e-mail met een koppeling die u gebruikt om u te registreren voor uw ExpressPlay-beheerdersaccount.

1. Meld u aan bij de portal Adobe cert met uw Adobe ID (gebruik hetzelfde e-mailadres dat u aan uw Adobe-vertegenwoordiger hebt opgegeven). Als u nog geen Adobe ID hebt, kunt u er snel een maken door het volgende te doen: *Een Adobe ID ophalen* link van het cert portaal :

   <!--<a id="fig_mst_gtj_wv"></a>-->

   ![](assets/cert_portal_sign-in-page-web.png)

1. Voor het portaal van de Adobe cert, verzoek om *Proefversie* cert.

   Voor de Multi-DRM-proefversie zal één proefcert alle volgende aspecten van de bescherming van inhoud omvatten: verpakking, licenties en vervoer. U moet uw eigen [CSR](../../../digital-rights-management/certificate-enrollment-guide/request-certs/gen-cert-signing-req.md) een verzoek om een uitspraak te doen:
   <!--<a id="fig_op1_xwj_wv"></a>-->

   ![](assets/cert_portal_trial_request-web.png)

   Adobe stuurt u een e-mail waarin wordt aangegeven dat u uw certificaataanvraag accepteert of afwijst. U kunt de status van uw certificaataanvraag(en) bekijken op de *Aanvraaggeschiedenis* tabblad op het cert portaal:
   <!--<a id="fig_gkl_myj_wv"></a>-->

   ![](assets/cert_portal_request_history-web.png)

1. Maak uw ExpressPlay-beheerdersaccount.

   Volg de koppeling naar ExpressPlay die Adobe u ontvangt. Hierdoor wordt het *Een account maken* pagina bij ExpressPlay. Vul de vereiste informatie in en verzend het formulier. U ontvangt een e-mail van `operations@expressplay.com` met een activeringskoppeling die een week goed is. Nadat u hebt geactiveerd, stelt u de ExpressPlay-service in:
   <!--<a id="fig_cjl_ztk_wv"></a>-->

   ![](assets/expressplay_create_service-web.png)

   Wanneer u uw service hebt gemaakt, krijgt u uw eigen beheerpagina te zien. Samen met sommige activiteit die gebieden volgen, zult u uw Productie en Test zien *klantauthenticators* (API-sleutels) en de URL&#39;s van de service Productie en Testen:

   <!--<a id="fig_c5h_xdl_wv"></a>-->

   ![](assets/expressplay_admin_dashboard_2-web.png) ![](assets/expressplay_admin_dashboard-web.png)

1. Als u FairPlay gebruikt, zijn er extra stappen nodig (op de Apple-ontwikkelaarssite) om op te starten met ExpressPlay. Zie [ExpressPlay-service inschakelen voor FairPlay](../../multi-drm-workflows/p-l-and-p/fairplay-workflow.md#enable-expressplay-service-for-fairplay) voor instructies.
