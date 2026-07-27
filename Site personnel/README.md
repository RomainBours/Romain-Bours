# Guide — modifier le site soi-même

Le site est fait uniquement de fichiers HTML/CSS/JS "à plat", sans outil de build. Ça veut dire que tu peux l'ouvrir avec n'importe quel éditeur de texte et le modifier directement, sans rien installer d'obligatoire.

## Ce qu'il te faut

- **Un éditeur de code** : [VS Code](https://code.visualstudio.com/) (gratuit) est le plus simple. Tu peux aussi ouvrir les fichiers avec Bloc-notes/TextEdit, mais VS Code colore le code et repère les erreurs.
- **Un navigateur** pour prévisualiser : double-clique sur `index.html`, ça s'ouvre directement dans Chrome/Safari/etc. Après une modification, sauvegarde le fichier puis rafraîchis la page (Cmd+R) pour voir le changement.
- (Optionnel) Dans VS Code, l'extension **"Live Server"** rafraîchit automatiquement le navigateur à chaque sauvegarde.

## Structure des fichiers

```
index.html                  → Page d'accueil
education.html              → Parcours académique
experience.html             → Expériences (HEC Consulting, CapitalatWork, basket...)
skills.html                 → Compétences, langues, certifications, intérêts
contact.html                → Coordonnées + formulaire
capitalatwork-project.html  → Page dédiée au stage CapitalatWork (à compléter plus tard)
style.css                   → Toutes les couleurs, polices, espacements
script.js                   → Petites interactions (menu mobile, formulaire de contact)
assets/                     → Photos et PDF (relevés de notes, etc.)
```

## Point important : pas de menu "partagé"

Chaque page contient sa propre copie du menu de navigation (`<header class="site-header">...`) et du pied de page (`<footer class="site-footer">...`). Si un jour tu ajoutes une page ou changes un lien du menu, il faut répéter la modification **dans chaque fichier .html**, sinon le menu ne sera pas cohérent d'une page à l'autre.

## Modifier du texte

Ouvre le fichier `.html` concerné, cherche le texte à changer (il est en clair dans le code), modifie-le, sauvegarde. Exemple dans `experience.html` :

```html
<h3>HEC Consulting</h3>
<p class="role">President — Apr 2026 – Present</p>
<p>
  Ton texte ici...
</p>
```

## Ajouter une nouvelle expérience / formation

Le plus simple : copie un bloc existant `<div class="entry"> ... </div>` en entier, colle-le au bon endroit (le plus récent en haut), et change les dates, le titre et le texte à l'intérieur.

## Changer les couleurs ou les polices

Tout est centralisé en haut de `style.css`, dans le bloc `:root` :

```css
:root {
  --bg: #faf9f6;        /* couleur de fond */
  --ink: #1c1c1c;       /* couleur du texte */
  --accent: #1f3a5f;    /* couleur d'accent (boutons, liens) */
  ...
}
```

Changer une seule de ces valeurs met à jour la couleur partout sur le site.

## Ajouter une photo ou un document

1. Dépose le fichier (image ou PDF) dans le dossier `assets/`.
2. Référence-le dans le HTML, par exemple :
   ```html
   <img src="assets/ma-photo.jpg" alt="Description">
   ```
   ou pour un lien vers un PDF :
   ```html
   <a href="assets/mon-document.pdf" target="_blank">Voir le document</a>
   ```

## Une fois le site en ligne (GitHub Pages / Netlify)

- **GitHub Pages** : tu modifies les fichiers, tu fais un commit + push sur GitHub, le site se met à jour automatiquement en 1-2 minutes.
- **Netlify (glisser-déposer)** : il faut re-glisser le dossier complet à chaque modification pour republier (sauf si tu connectes Netlify à un dépôt GitHub, auquel cas ça devient automatique comme ci-dessus).
