---
description: Kopieer bestanden van de dvd om de Adobe® Access™ voor gebruik in te stellen. Deze bestanden bevatten JAR-bestanden met code, certificaten en klassen van derden. Vraag bovendien een certificaat aan bij Adobe Systems Incorporated. U krijgt meerdere referenties toegewezen die worden gebruikt om de integriteit van inhoud, licenties en communicatie tussen de client en de server in het pakket te beschermen.
title: De ontwikkelomgeving instellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# SDK {#setting-up-the-sdk} instellen

Kopieer bestanden van de dvd om de Adobe® Access™ voor gebruik in te stellen. Deze bestanden bevatten JAR-bestanden met code, certificaten en klassen van derden. Vraag bovendien een certificaat aan bij Adobe Systems Incorporated. U krijgt meerdere referenties toegewezen die worden gebruikt om de integriteit van inhoud, licenties en communicatie tussen de client en de server in het pakket te beschermen.

De Adobe Access SDK is beschikbaar in twee typen:
* Adobe Access Core SDK
* Adobe Access Professional SDK

De volgende lijst toont een basisvergelijking van Adobe Access SDKs:

| Functie | Adobe Access Core SDK | Adobe Access Professional SDK |
|---|---|---|
| Functies van Flash Access 2.0 | Beschikbaar | Beschikbaar |
| Toetsrotatie | - | Beschikbaar |
| Domeinondersteuning | Beschikbaar | Beschikbaar |
| Enhanced License Chaining | Beschikbaar | Beschikbaar |
| Synchronisatieberichten | Beschikbaar | Beschikbaar |
| Licentie vooraf genereren | Beschikbaar | Beschikbaar |
| Ingesloten licenties | Beschikbaar | Beschikbaar |

## De ontwikkelomgeving instellen {#setting-up-the-development-environment}

Kopieer vanaf de dvd de volgende SDK-bestanden voor gebruik in uw ontwikkelomgeving en uw Java-klassepad:

* adobe-flashaccess-certs.jar (bevat Adobe-basiscertificaten)
* adobe-flashaccess-sdk.jar (bevat Adobe Access Core SDK-klassen)
* adobe-flashaccess-sdk-pro.jar (bevat Adobe Access Professional SDK-klassen, alleen vereist voor Professional-functies)

U hebt de volgende JAR-bestanden van derden nodig die ook op de dvd staan in de map &quot;third-party&quot; van de SDK:

* bcmail-jdk15-141.jar
* bcprov-jdk15-141.jar
* commons-discovery-0.4.jar
* commons-logging-1.1.1.jar
* cryptoj.jar
* jaxb-api.jar
* jaxb-impl.jar
* jaxb-libs.jar
* relaxngDatatype.jar
* rm-pdrl.jar
* xsdlib.jar

Voor betere prestaties, kunt u naar keuze inheemse steun voor cryptografische verrichtingen toelaten door de platform-specifieke bibliotheken op te stellen die in de &quot;derde/cryptoj&quot;omslag van SDK worden gevestigd. Als u native ondersteuning wilt inschakelen, voegt u de bibliotheek voor uw platform (jsafe.dll voor Windows of libjsafe.so voor Linux) toe aan het pad. De 32-bits en 64-bits versies van deze bibliotheken zijn beschikbaar. (De 64-bits versie mag alleen worden gebruikt als u een 64-bits besturingssysteem hebt en u de 64-bits versie van Java uitvoert).

Bovendien is een optioneel deel van de SDK adobe-flashaccess-lcrm.jar. Dit bestand is alleen nodig voor functionaliteit die gerelateerd is aan Adobe Flash Media Rights Management Server (FMRMS) 1.x-compatibiliteit. Als u eerder FMRMS 1.x hebt geïmplementeerd en uw met FMRMS beveiligde inhoud niet opnieuw wilt verpakken, moet u ondersteuning toevoegen aan uw licentieserver zodat deze oude inhoud en clients kan verwerken.
