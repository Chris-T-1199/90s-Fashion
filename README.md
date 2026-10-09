# Supermodèles 90s

Site web sur les grands mannequins de 1990 à 1999 : fiches détaillées, photos, chronologie et vidéos des défilés mythiques.

## API utilisées

| API | Rôle | Clé requise |
|-----|------|-------------|
| Wikipedia Action API | Portrait, résumé et article complet (FR ou EN) | Non |
| Wikimedia Commons API | Photothèque de chaque mannequin (24 photos par page) | Non |
| YouTube Data API v3 | Vidéos par catégorie : fashion weeks, pubs, clips, entrevues, documentaires | Oui (gratuite) |

## Fiche mannequin

Cliquez sur un portrait (ou ouvrez `index.html#naomi`, `#kate`…) :

- **Aperçu** : résumé, moments marquants, marques, vidéo à la une
- **Carrière** : réalisations des années 90 par catégorie (`carrieres.js`) et article Wikipedia intégral, en français ou en anglais
- **Photos** : photothèque Wikimedia Commons avec visionneuse (flèches ← →), crédits et licences
- **Vidéos** : fashion weeks filtrables par maison (Versace, Chanel…), campagnes, clips, entrevues, documentaires, avec « Plus de vidéos »

## Lancer le site

Servez le dossier en local (l'API YouTube refuse souvent les pages ouvertes en `file://`) :

```bash
python -m http.server 8000
```

Ouvrez ensuite http://localhost:8000.

## Activer les vidéos intégrées

1. Créez un projet sur https://console.cloud.google.com
2. Activez **YouTube Data API v3**, puis créez une **clé API**
3. Collez-la dans `config.js` → `YOUTUBE_API_KEY`

Sans clé, chaque vidéo s'affiche sous forme de lien vers une recherche YouTube.
Les résultats sont mis en cache 24 h dans le navigateur, parce qu'une recherche consomme 100 unités sur un quota gratuit de 10 000 par jour.

## Fichiers

- `index.html` : structure de la page
- `style.css` : design éditorial de magazine de mode (respecte le réglage « réduire les animations » du système)
- `data.js` : contenu éditorial (mannequins, défilés, chronologie)
- `carrieres.js` : réalisations détaillées de chaque mannequin
- `app.js` : appels aux API et affichage
- `animations.js` : intro en rideau, couverture animée, podium avec flashs, ruban à mesurer, apparitions au défilement, curseur
- `config.js` : clé YouTube et options
