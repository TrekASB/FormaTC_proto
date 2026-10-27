# Forma → Trimble Connect

Selvstendig Trimble Connect 3D Viewer extension for å finne filer i Autodesk Forma / APS Data Management og overføre dem til valgt mappe i det aktive Trimble Connect-prosjektet.

Dette repositoryet er skilt ut fra [BIM_proto](https://github.com/TrekASB/BIM_proto). Andre BIM Tools-programmer er ikke med. Original-repositoryet er uendret.

## Registrering i Trimble Connect

**Manifest:** https://trekasb.github.io/FormaTC_proto/manifest.json

**App:** https://trekasb.github.io/FormaTC_proto/apps/forma-connect-bridge.html

Aktiver GitHub Pages fra `main` / root under Settings → Pages og registrer manifest-URL-en som Project Extension.

## Innhold

- `manifest.json` – selvstendig Trimble-extension
- `apps/forma-connect-bridge.html` – brukergrensesnitt og Forma/APS-synkronisering
- `apps/trimble-tcps-bridge.js` – Trimble Connect TCPS SDK for opplasting/mappevisning
- `apps/forma-auth-callback.html` og `apps/forma-auth-return.html` – tilhørende autentiseringssider (bevart fra originalen; primærflyten bruker lokal helper)
- `assets/norconsult-logo.svg` – logo
- `local-helper/` – valgfri lokal Node.js OAuth callback-helper, **nødvendig for den nåværende innloggingsflyten**

## Autodesk APS

Den nåværende applikasjonen bruker OAuth 2.0 Authorization Code + PKCE og følgende registrerte callback:

`http://localhost:3000/api/forge/callback/oauth`

Denne adressen er bevart ved utskillingen. Client ID fylles inn i extensionen; ingen Client Secret skal legges i repositoryet. Installer og start `local-helper/` lokalt på brukerens PC før innlogging; se [local-helper/README.md](local-helper/README.md).

## Avhengigheter og merknader

- Trimble Connect Workspace SDK lastes av appen fra eksisterende CDN-kilde.
- TCPS-broen bruker `trimble-connect-sdk@4.0.11` fra jsDelivr.
- Helperen kjører lokalt med Node.js og Express.
- Filoverføring, tokenadgang og prosjekt-rettigheter må prøves i et faktisk Trimble Connect/Autodesk-miljø.
- GitHub Pages må aktiveres. Ingen automatisk deploy eller ende-til-ende-test er utført av denne repository-migreringen.
- Eksisterende PKCE-/callback-logikk er videreført uendret for kompatibilitet.
