# Myndmy — dossier de l'application

## Contenu
- `index.html` : l'app complète (accueil, Activité, Suivi, Ressources, FAQ, générateur BaZi)
- `manifest.webmanifest` + `icons/` : installation sur l'écran d'accueil
- `sw.js` : service worker (utilisable hors ligne après la 1re visite)
- `netlify.toml` : réglages Netlify
- `capacitor.config.json` + `package.json` : pour empaqueter l'app pour les stores
- `STORES.md` : checklist App Store / Google Play

## Mettre en ligne (Netlify)
Glisse **tout le dossier** (pas seulement index.html) dans Netlify Drop.
L'app doit être en HTTPS pour que l'installation et le hors-ligne fonctionnent.

## Tester sur téléphone
1. Ouvre l'URL Netlify dans Safari (iPhone) ou Chrome (Android).
2. iPhone : Partager → « Sur l'écran d'accueil ». Android : bouton « Installer » (Ressources) ou menu ⋮.
3. Coupe le réseau : l'app doit s'ouvrir quand même.

## Raccourcis
`index.html?p=suivi`, `?p=activite`, `?p=ressources` ouvrent directement la page.
