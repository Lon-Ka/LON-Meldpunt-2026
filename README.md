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
| Client ID | `08dcc1b5-6041-4e67-ba6f-14650d4e6e62` |
| Tenant ID | `655d15e1-e5fc-4868-8462-8463dc0ff014` |
| Tenant | londerwijs.be |

**Redirect URIs (SPA):**
```
https://lon-ka.github.io/LON-Meldpunt-2026/
https://lon-ka.github.io/LON-Meldpunt-2026/index.html
https://lon-ka.github.io/LON-Meldpunt-2026/beheer.html
https://lon-ka.github.io/LON-Meldpunt-2026/setup.html
```

**API-machtigingen:**
- `Sites.ReadWrite.All` (Gedelegeerd) — normaal gebruik
- `Sites.FullControl.All` (Gedelegeerd) — enkel tijdens setup, daarna verwijderen
- `Mail.Send` (Gedelegeerd) — e-mailnotificaties

## SharePoint

**Site:** `https://londerwijs.sharepoint.com/sites/BaO-Meldpunt`  
**Site ID:** `londerwijs.sharepoint.com,2463b644-ba24-4563-a37f-a67f26941a09,4d5ecb10-38f0-422f-b892-af256a5da6fc`

**SharePoint-lijsten (13):**

Per school (× 4): `LON-Veiligheid-[sleutel]`, `LON-Welzijn-[sleutel]`, `LON-Incidenten-[sleutel]`  
Centraal: `LON-Beheerders`

## Installatie

### 1. Setup uitvoeren (eenmalig)
1. Upload alle bestanden naar deze repository
2. Activeer GitHub Pages: Settings → Pages → Branch: main / root
3. Open `setup.html` in de browser
4. Meld aan als ICT-beheerder met `Sites.FullControl.All`-machtiging
5. Klik "SharePoint-lijsten aanmaken"
6. Kopieer de List IDs naar `index.html` en `beheer.html`

### 2. List IDs invullen
Zoek in `index.html` en `beheer.html` de `CONFIG`-sectie en vervang elke `PLACEHOLDER` door de corresponderende List ID uit setup.html.

### 3. Sites.FullControl.All verwijderen
Na de setup verwijder je de `Sites.FullControl.All` machtiging in Azure Portal → API permissions. De app werkt verder met `Sites.ReadWrite.All`.

### 4. Beheerders toevoegen
Voeg de eerste beheerders toe aan de `LON-Beheerders` lijst in SharePoint:

| Naam | E-mail | Rol | School |
|------|--------|-----|--------|
| Wim Cools | ict@centrumschool.londerzeel.be | admin | alle |
| Katelijne Jespers | directie@centrumschool.londerzeel.be | directie | csl |
| Farah De Clercq | directie@kouterschool.londerzeel.be | directie | ko |
| Pieter Sarens | directie@terelst.londerzeel.be | directie | te |
| Iris De Vocht | irisdevocht@terelst.londerzeel.be | zorg | te |
| Els Segers | elssegers@terelst.londerzeel.be | zorg | te |
| Lymke Celerier | lymkecelerier@centrumschool.londerzeel.be | zorg | csl |
| Silke Royaert | silkeroyaert@centrumschool.londerzeel.be | zorg | csl |
| Laura Boeykens | lauraboeyns@centrumschool.londerzeel.be | zorg | csl |
| Leen Van Beneden | zorg@kouterschool.londerzeel.be | zorg | ko |
| Rita Rubbrecht | secretariaatlonka@centrumschool.londerzeel.be | admin | alle |

## Bijwerken

Pas `index.html` of `beheer.html` aan en push naar `main`. GitHub Pages is automatisch live na ±1 minuut (controleer de groene vink bij **Actions**).

## GDPR

Zie `gdpr.html` voor het volledige privacybeleid.  
Verwerkingsregister en handleidingen zijn beschikbaar als aparte Word-documenten.

---

*Scholengroep Londerzeel BaO — LON-Meldpunt 2026 · Versie 1.0 · Juni 2026*
