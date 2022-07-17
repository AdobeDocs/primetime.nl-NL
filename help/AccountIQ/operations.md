---
title: Activiteiten in rekening-IQ
description: De verrichtingen in Rekening IQ impliceren acties om automatiserings en bulkverrichtingen op abonneerekeningen uit te voeren en hun gevolgen te volgen.
source-git-commit: e61cca77bad4f01de871e300dc99d7368c283f2a
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---


# Bewerkingen {#operations-tab-next-steps}

Als u de gebruikspatronen van uw abonnees hebt begrepen en hebt vastgesteld dat het wachtwoord voor het geselecteerde segment wordt gedeeld (met behulp van rapporten en analyses in Account IQ), kunt u gerichte acties ondernemen om het delen van wachtwoorden te beperken.

De functionaliteit van Verrichtingen in IQ van de Rekening helpt u effectief om geloofsbrieven te pakken en te beheren die door gerichte procedures worden genoemd verrichtingen. Het geeft u opties om een objectieve, op maat gesneden acties (op het doel gebaseerd) voor een specifieke groepen abonneerekeningen te ontwerpen, en hun uitvoering voor een toekomstige duur te automatiseren. Via de functionaliteit Bewerkingen kunt u niet alleen bewerkingen maken en uitvoeren, maar ook de effecten ervan meten. Zo, door de gevolgen in kaart te brengen kunt u uw strategie aanpassen om het effect te optimaliseren, of het converteren van leners of het verlichten van credentiedelen.

Naar weergave **Bewerkingen** pagina selecteren **Bewerkingen** optie onder **Handelingen** in linkernavigatie van de toepassing van IQ van de Rekening. De pagina van Verrichtingen maakt een lijst van alle verrichtingen die reeds op het systeem van IQ van de Rekening samen met hun details bestaan.

![](assets/operations-page.png)

*Afbeelding: Lijst en nadere gegevens van bestaande transacties in IQ van account*

Op de pagina van Verrichtingen, kunt u:

* Een lijst weergeven met bewerkingen die al in Account IQ bestaan

* Bewerkingsdetails weergeven, zoals:

   * status (Gepland, Running, Beëindigd, Fout, of Gestopt)

   * voortgang (in percentage van voltooiing)

   * doelpubliek (segment om de bewerking uit te voeren)

   * schema (begin- en einddatum van de exploitatie)

   * aanmaakdatum en einddatum van de operatie

* [Nieuwe bewerking maken](/help/AccountIQ/operation-affecting-user-segment.md)

* [Bewerkingsrapporten weergeven](#operation-reports)

<!--* Search from the list of operations using Search field

* Stop an operation.

* Create a duplicate operation.

* [Configure columns of Operations details page](#configure-columns)-->

## Bewerkingsrapporten weergeven {#operation-reports}

U kunt de effecten van een bewerking analyseren door het bijbehorende rapport te bekijken. Het rapport van een bewerking weergeven:

1. Selecteer de naam van de bewerking op de hoofdpagina Bewerkingen.

   Het rapport wordt weergegeven in de vorm van een gestapelde staafgrafiek.

   ![](assets/operation-impact-report.png)

   *Afbeelding: Operationeel verslag om de effecten van de concrete acties te bekijken*

   De x-as geeft de evaluatieperiode en de y-as een variabele om de impact van de exploitatie te meten.

   In de bovenstaande afbeelding is de variabele op de y-as bijvoorbeeld het aantal accounts. Als u de grafiek bekijkt, kunt u het aantal rekeningen in het operationele segment vergelijken met het aantal rekeningen buiten het operationele segment op een bepaald tijdstip (zoals week 2e van de operationele evaluatieperiode). Daarom kunt u analyseren hoe over de evaluatieperiode aantal rekeningen binnen het verrichtingssegment en buiten het segment varieert.

   Dus als uw bewerking was om waarschuwings-e-mails naar verdachte accounts te sturen, en accounts in operatiesegmenten waren die met een gedeelde waarschijnlijkheid groter dan 90 en meer dan 5 apparaten gebruiken om inhoud te streamen, dan zijn aan het begin van de evaluatieperiode de accounts in segment meer dan 7 miljoen. Dit aantal verandert tijdens de evaluatieperiode, zoals in de grafiek wordt getoond, en geeft het effect van de operatie aan. Op basis van de evaluatie kunt u corrigerende maatregelen nemen voor het vermoeden van accounts, of doorgaan met de bewerking, of uw strategie aanpassen voor betere resultaten om het delen van referenties te beperken.

2. Om het rapport te sluiten en terug naar de belangrijkste pagina van Verrichtingen te gaan, selecteer **Bewerkingen** optie onder **Handelingen** in linkernavigatie.

<!--

![](assets/operations-details.png)

*Figure: Operation details*
## Configure columns {#configure-columns}

You can select the icon to **Configure columns** on the top of the operations table.

![](assets/config-columns.png)

*Figure: Configure columns of Operations details page*-->