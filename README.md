# Son premier téléphone — déploiement

Application statique (aucun serveur, aucune base de données). Tout tient dans ce dossier :

```
index.html
manifest.json
sw.js
icons/
```

## Publier en 2 minutes (recommandé : Netlify)

1. Allez sur https://app.netlify.com/drop
2. Glissez-déposez ce dossier entier dans la page.
3. Netlify vous donne une URL en `https://....netlify.app` — c'est en ligne, en HTTPS, immédiatement.
4. (Optionnel) Dans les réglages Netlify, ajoutez un nom de domaine à vous.

Alternatives tout aussi simples, au choix :
- **Vercel** : `vercel deploy` depuis ce dossier, ou glisser-déposer sur vercel.com.
- **GitHub Pages** : poussez ce dossier dans un repo GitHub, puis Réglages → Pages → Deploy from branch.
- **Cloudflare Pages** : glisser-déposer sur pages.cloudflare.com.

Un point important : le **HTTPS est obligatoire** pour qu'un service worker s'installe et que l'app soit "installable" (PWA). Les quatre options ci-dessus le fournissent automatiquement — vous n'avez rien à configurer.

## Vérifier que la PWA fonctionne

Une fois en ligne :
1. Ouvrez l'URL sur un téléphone (Chrome Android ou Safari iOS).
2. Android/Chrome : un bandeau ou le menu ⋮ propose "Ajouter à l'écran d'accueil" / "Installer l'application".
3. iOS/Safari : bouton Partager → "Sur l'écran d'accueil".
4. Ouvrez l'app depuis l'icône ajoutée : elle se lance en plein écran, sans barre de navigateur.
5. Testez le mode hors-ligne : ouvrez l'app une première fois en ligne (pour que le service worker mette l'app en cache), puis activez le mode avion et rouvrez l'app — elle doit toujours s'afficher.

## Si vous déployez dans un sous-dossier (ex. `monsite.fr/spt/`)

Tous les chemins du projet sont relatifs (`./`, `icons/...`), donc ça fonctionne tel quel, sans rien modifier.

## Modifier plus tard

- Les icônes viennent d'un script Python (Pillow) qui n'est pas inclus ici — dites-le-moi si vous voulez le regénérer avec un autre visuel.
- Le contenu (questions, actions, fiches par appli) est dans le `<script>` d'`index.html`, dans les constantes `QUESTIONS`, `ACTIONS`, `BRIEFS`. Si le projet grossit encore, ça vaudra le coup de sortir ces trois constantes dans un fichier `contenu.json` séparé pour éditer sans toucher au code.
- `VERIF` (en haut du script, section ACTIONS) est la date "chemins vérifiés en...", affichée sur chaque écran de réglage — à mettre à jour quand vous revérifiez les parcours.
