# Prélèvements — app installable

Suivi des dépenses permanentes mensuelles. Une seule page, aucune dépendance,
données stockées sur l'appareil (localStorage).

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

## Sauvegarde

Bouton **Exporter** en bas de l'app : copie toutes les données en JSON.
À coller quelque part une fois par trimestre. Le bouton **Importer** restaure.

⚠️ Effacer les données de navigation de Chrome efface aussi les données de l'app.

## Mise à jour

Remplacer `index.html` dans le dépôt, puis incrémenter `CACHE` dans `sw.js`
(`prelevements-v1` → `prelevements-v2`) pour forcer le rafraîchissement.
