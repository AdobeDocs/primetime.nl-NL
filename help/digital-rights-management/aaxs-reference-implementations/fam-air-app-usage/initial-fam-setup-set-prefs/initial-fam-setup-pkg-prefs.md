---
seo-title: Voorkeuren voor Packager
title: Voorkeuren voor Packager
uuid: 3e9c971d-3a5f-4f3e-97e7-baab63b1f67f
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# Voorkeuren voor Packager {#packager-preferences}

Dit tabblad bevat de vereiste instellingen voor het verpakken van inhoud. In de volgende tabel worden deze voorkeuren beschreven:

| Voorkeur | Beschrijving |
|--- |--- |
| Vervoerscertificaat licentieserver | Het servertransportcertificaat, uitgegeven door Adobe. Dit certificaat wordt gebruikt om communicatie tussen de client en de licentieserver te beveiligen. Het dossier moet in de Folder van het Middel worden gevestigd. |
| HSM inschakelen | Specificeert of de certificaten en de geloofsbrieven op HSM worden opgeslagen. In dat geval worden de voorkeuren voor certificaten en referenties uitgeschakeld en moeten de eigenschappen op het tabblad HSM worden opgegeven. |
| Opties voor sleutelversleuteling | Hiermee wordt opgegeven hoe de coderingssleutel voor inhoud tijdens het verpakken wordt gecodeerd |
| Certificaat van licentieserver | Het licentieservercertificaat, uitgegeven door Adobe. Het dossier moet in de Folder van het Middel worden gevestigd. De CEK wordt gecodeerd met de openbare sleutel van de licentieserver. Alleen houders van de persoonlijke sleutel van de licentieserver kunnen de CEK decoderen. |
| Packager Credential | De gegevens van de packager, uitgegeven door Adobe. Dit bestand wordt gebruikt om de metagegevens tijdens het verpakken te ondertekenen. |
| Bestandsnaam | Het `PKCS#12` (.pfx)-bestand met certificaat en persoonlijke sleutel. Het dossier moet in de Folder van het Middel worden gevestigd. |
| Wachtwoord voor bestand | Wachtwoord voor PFX-bestand |
| Algemene eigenschappen van gecontroleerde mappen | Geeft instellingen op die van toepassing zijn op alle gecontroleerde mappen die op deze server zijn geconfigureerd. |
| Interval controleren in milliseconden | Hiermee geeft u aan hoe vaak Gecontroleerde mappen moeten controleren of er nieuwe inhoud in het pakket moet worden opgenomen. De server doorloopt alle geconfigureerde Gecontroleerde mappen en slaapt gedurende deze periode. |
| Achtervoegsel uitvoerbestandsnaam | Hiermee geeft u een bestandsextensie op die u wilt toevoegen aan uitvoerbestanden. Als .out bijvoorbeeld is opgegeven en het invoerbestand video.flv is, is het uitvoerbestand video.out.flv. |
| Back-upinvoerbestanden | Geeft aan of een kopie van de oorspronkelijke inhoud moet worden opgeslagen. Als deze optie niet is geselecteerd, wordt het oorspronkelijke bestand verwijderd nadat het verpakken is voltooid. |
| Submapnaam voor back-up invoeren | Als de optie Back-up maken van invoerbestanden is geselecteerd, geeft u een map op waarin de invoerbestanden worden opgeslagen. Met deze optie geeft u een mapnaam op die relatief is ten opzichte van de invoermap voor gecontroleerde mappen. Als de map niet bestaat, wordt deze tijdens het verpakken gemaakt. |
| Bestaande uitvoerbestanden overschrijven | Hiermee wordt aangegeven of het uitvoerbestand kan worden overschreven als er al een bestand met dezelfde naam bestaat. Als deze optie niet is geselecteerd en het uitvoerbestand al bestaat, wordt de verwerking van het invoerbestand overgeslagen. |
