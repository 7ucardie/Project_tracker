# Project Tracker

Eenvoudige kanban-projecttracker (Te doen / Bezig / Klaar) voor GitHub Pages, zonder build-stap.

## Hoe de beveiliging werkt

GitHub Pages is statische hosting: er is geen server die een wachtwoord kan controleren. Daarom:

- Alle projecten en taken worden **in je browser versleuteld** (AES-256-GCM, sleutel via PBKDF2-SHA256, 600.000 iteraties) met je wachtwoord en opgeslagen in `localStorage`.
- De repo en de gepubliceerde pagina bevatten alleen code, **geen data**. Zonder wachtwoord is de data onleesbaar.
- Automatisch vergrendelen na 10 minuten inactiviteit; vertraging na foute pogingen.
- Back-ups exporteer/importeer je als versleuteld JSON-bestand (zo neem je data mee naar een ander apparaat).
- Het wachtwoord is **niet te herstellen**. Bewaar het in een wachtwoordmanager.

## 2FA

Echte 2FA kan niet afgedwongen worden op puur statische hosting (een TOTP-geheim in de pagina zou voor iedereen zichtbaar zijn). Wil je 2FA, zet dan een toegangslaag voor de site:

- **Cloudflare Access** (gratis tot 50 gebruikers) voor een eigen domein/Cloudflare Pages, met login via GitHub/Google en hun 2FA, of
- GitHub Pages met toegangscontrole (alleen GitHub Enterprise Cloud).

## Publiceren

1. Merge deze branch naar `main`.
2. GitHub → Settings → Pages → *Deploy from a branch* → `main` / `/ (root)`.
3. Open `https://<gebruiker>.github.io/Project_tracker/`.

Lokaal proberen: `python3 -m http.server` en open `http://localhost:8000`.
