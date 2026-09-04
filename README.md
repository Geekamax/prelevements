# Prélèvements — app installable

Suivi des dépenses permanentes mensuelles. Une seule page, aucune dépendance.
Les données vivent en local (localStorage) et sont sauvegardées automatiquement
sur Firestore (projet `prelevements-app`) à chaque modification.

## Mise en ligne (GitHub Pages)

1. Créer un dépôt **public** nommé `prelevements`
2. Y déposer les 6 fichiers de ce dossier (glisser-déposer sur github.com suffit)
3. Settings → Pages → Source : `Deploy from a branch` → Branch `main` / dossier `/ (root)` → Save
4. Attendre ~2 min, l'URL apparaît : `https://<pseudo>.github.io/prelevements/`

Le dépôt doit être public pour que Pages fonctionne sur un compte gratuit.
Le code ne contient aucune donnée personnelle — les montants restent sur le téléphone.

## Installation sur Android

Ouvrir l'URL dans Chrome → menu ⋮ → **Installer l'application**
(ou « Ajouter à l'écran d'accueil »).

Icône sur l'écran d'accueil, ouverture plein écran, fonctionne hors ligne.

## Sauvegarde automatique (cloud)

Chaque modification est poussée vers Firestore (`prelevements-app`), sous un
document identifié par le hash SHA-256 d'un **code de récupération** généré
automatiquement au premier lancement (visible/copiable en bas de l'app,
bouton "Afficher").

Si les données locales de l'appareil sont effacées (nettoyage Chrome, app
mise en veille par Android, réinstallation...), l'app détecte le vide au
démarrage et propose de coller ce code pour tout restaurer depuis le cloud.

Les règles Firestore acceptent lecture/écriture sur `/backups/{code}` pour
quiconque connaît le code exact (hash non énumérable) — pas d'authentification
classique, sécurité par capacité (comme un lien de partage).

Le bouton **Exporter** (JSON en presse-papiers) et **Importer** restent
disponibles en secours manuel (changer d'appareil sans le code, debug, etc).

## Mise à jour

Remplacer `index.html` dans le dépôt, puis incrémenter `CACHE` dans `sw.js`
(`prelevements-v1` → `prelevements-v2`) pour forcer le rafraîchissement.
