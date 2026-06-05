# LON-Meldpunt 2026

Digitaal meldpunt voor Scholengroep Londerzeel BaO — Veiligheid · Welzijn · Incidenten

**Live URL:** https://lon-ka.github.io/LON-Meldpunt-2026/

---

## Scholen

| Sleutel | School |
|---------|--------|
| `csl` | Centrumschool — Lijsterstraat |
| `css` | Centrumschool — Stationsstraat |
| `ko` | Kouterschool |
| `te` | School Ter Elst |

## Bestanden

| Bestand | Functie | Wie |
|---------|---------|-----|
| `index.html` | Meldpunt-app — snelle aangifte, mijn meldingen, 3 pijlers | Alle personeelsleden |
| `beheer.html` | Beheerspaneel — overzicht, opvolging, rapportering | Directie, zorgcoördinatoren, admin |
| `setup.html` | Eenmalige setup — SharePoint-lijsten aanmaken | ICT-verantwoordelijke (eenmalig) |
| `gdpr.html` | Privacy & GDPR-informatie voor melders | Iedereen |

## Technologie

- **Frontend:** HTML/CSS/JavaScript (geen framework, geen buildstap)
- **Authenticatie:** Microsoft MSAL v3 (via CDN)
- **Backend:** Microsoft Graph API + SharePoint Online
- **Hosting:** GitHub Pages (gratis)
- **Dataopslag:** SharePoint Online (`londerwijs.sharepoint.com`)

## Azure App Registration

| Parameter | Waarde |
|-----------|--------|
| App-naam | LON-Meldpunt |
| Tenant | londerwijs.be |

> ⚠️ Client ID en Tenant ID worden **niet** in dit publieke bestand opgenomen.
> Raadpleeg het interne configuratiedocument (bewaard buiten deze repository).

## SharePoint

**Site:** `https://londerwijs.sharepoint.com/sites/BaO-Meldpunt`

**SharePoint-lijsten (13):**

Per school (× 4): `LON-Veiligheid-[sleutel]`, `LON-Welzijn-[sleutel]`, `LON-Incidenten-[sleutel]`
Centraal: `LON-Beheerders`

> ⚠️ List IDs worden **niet** in dit publieke bestand opgenomen.
> Ze staan enkel in de lokale kopie van `index.html` en `beheer.html`.

## API-machtigingen

| Machtiging | Gebruik |
|---|---|
| `Sites.ReadWrite.All` | Meldingen lezen en schrijven |
| `User.Read` | Ingelogde gebruiker identificeren |
| `Mail.Send` | E-mailnotificaties |
| `Sites.FullControl.All` | Enkel tijdens setup — daarna verwijderen |

## Installatie

### 1. Setup uitvoeren (eenmalig)
1. Upload alle bestanden naar deze repository
2. Activeer GitHub Pages: Settings → Pages → Branch: main / root
3. Voeg tijdelijk `Sites.FullControl.All` toe in Azure Portal
4. Open `setup.html` en meld aan als ICT-beheerder
5. Klik "SharePoint-lijsten aanmaken"
6. Kopieer de List IDs naar `index.html` en `beheer.html`
7. Verwijder `Sites.FullControl.All` uit Azure Portal

### 2. Beheerders toevoegen
Voeg de bevoegde personen toe aan de `LON-Beheerders` lijst in SharePoint.
Kolommen: `Title` (naam), `Email`, `Rol` (admin / directie / zorg), `School` (sleutel), `Actief` (ja/nee).

> ⚠️ Voeg **geen namen of e-mailadressen** toe aan dit publieke README-bestand.
> Beheerdersbeheer gebeurt uitsluitend via de SharePoint-lijst.

### 3. Bijwerken
Pas `index.html` of `beheer.html` aan en push naar `main`.
GitHub Pages is automatisch live na ±1 minuut.

## GDPR

Zie `gdpr.html` voor het volledige privacybeleid.
Verwerkingsregister en handleidingen zijn beschikbaar als aparte Word-documenten (intern bewaard, niet in deze repository).

> ℹ️ Deze repository is publiek. Voeg **nooit** persoonsgegevens, wachtwoorden,
> API-sleutels, Client IDs, List IDs of e-mailadressen toe aan bestanden in deze repository.

---

*Scholengroep Londerzeel BaO — LON-Meldpunt 2026 · Versie 1.0 · Juni 2026*
