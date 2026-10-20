# Passer de l'app web aux stores

Ce que le code fait déjà : plein écran mobile, zones de sécurité iPhone (encoche), icônes, manifest, hors-ligne, rappel quotidien, export des données, retours haptiques.
Ce qui reste à faire par toi (je ne peux pas le faire à ta place) : comptes développeur, signatures, soumission.

## 1. Comptes
- Apple Developer Program : 99 €/an (obligatoire pour l'App Store). Il faut un Mac avec Xcode pour compiler.
- Google Play Console : 25 € une seule fois. Android Studio suffit (Windows/Mac/Linux).

## 2. Empaqueter (Capacitor)
```
npm install
npx cap add ios        # Mac uniquement
npx cap add android
npm run ios            # ouvre Xcode
npm run android        # ouvre Android Studio
```
Icône et splash : mets `icons/icon-512.png` dans `assets/icon.png` (1024×1024 conseillé) puis `npx capacitor-assets generate`.

## 3. À faire avant soumission
- [ ] Nom, identifiant `com.myndmy.app` (à valider avec le client)
- [ ] Politique de confidentialité en ligne (URL obligatoire) : données stockées localement, aucune donnée envoyée
- [ ] Mentions santé : « Myndmy est un outil de bien-être, pas un dispositif médical » (déjà dans la FAQ, à répéter dans la fiche store)
- [ ] Captures d'écran : iPhone 6,7" (1290×2796) et 6,5", Android téléphone ; 3 à 8 par taille
- [ ] Description, mots-clés, catégorie (Santé et forme), classification d'âge
- [ ] Apple : formulaire « App Privacy » (collecte de données : aucune pour l'instant)
- [ ] Google : formulaire « Sécurité des données », test fermé de 12 testeurs pendant 14 jours si compte perso créé après nov. 2023

## 4. Points d'attention
- **Apple refuse souvent les simples « sites emballés »** (règle 4.2). Il faut apporter de la valeur native : ajoute les notifications locales (`@capacitor/local-notifications`) pour le rappel app fermée, et les haptiques (`@capacitor/haptics`).
- Notifications **app fermée** : impossibles en PWA seule sur iPhone sans push ; avec Capacitor, les notifications locales règlent le rappel quotidien.
- Suivi « d'un appareil à l'autre » : demande un compte utilisateur et un backend (Supabase / Firebase). Aujourd'hui tout est local au téléphone.
- Les calculs BaZi sont indicatifs : garde la mention dans la fiche store.
- Polices : Poppins est chargée depuis Google Fonts. Pour la version store, héberge-la dans l'app (téléchargée en local) pour le 100 % hors-ligne.

## 5. Ordre conseillé
1. Déployer sur Netlify et tester 1 semaine sur 3-4 téléphones
2. Corriger les retours
3. Ajouter compte + sauvegarde cloud si le client veut le suivi multi-appareils
4. Empaqueter avec Capacitor, tester via TestFlight (iOS) et test interne (Android)
5. Soumettre
