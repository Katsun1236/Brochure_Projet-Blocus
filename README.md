# Brochure Interactive 3D - Projet Blocus

Une brochure web interactive en 3D présentant le Projet Blocus, une plateforme d'IA pour aider les étudiants durant leur période de blocus.

## Aperçu

Cette brochure utilise des transformations CSS 3D pour créer un effet de dépliage réaliste, simulant une vraie brochure papier en trois volets.

### Fonctionnalités

- **Animation 3D fluide** : Effet de dépliage avec animations spring (rebond)
- **Texture papier** : Grain subtil pour un rendu réaliste
- **Effets de lumière** : Reflets brillants et ombres dynamiques
- **Responsive** : S'adapte aux différentes tailles d'écran
- **Interactif** : Cliquez pour ouvrir/fermer la brochure

## Structure du Projet

```
Brochure_Projet-Blocus/
├── index.html           # Fichier principal de la brochure
├── netlify.toml         # Configuration Netlify
├── README.md            # Ce fichier
└── assets/
    └── images/          # Images de la mascotte Locus
        ├── locus-neon-favicon.png
        ├── locus-loupe.png
        ├── locus-presentation-teaching.png
        └── locus-wings-open-hero.png
```

## Déploiement sur Netlify

### Option 1 : Via le Site Web Netlify

1. Connectez-vous sur [Netlify](https://www.netlify.com/)
2. Cliquez sur "Add new site" > "Import an existing project"
3. Connectez votre dépôt GitHub
4. Netlify détectera automatiquement la configuration via `netlify.toml`
5. Cliquez sur "Deploy site"

### Option 2 : Via Netlify CLI

```bash
# Installer Netlify CLI
npm install -g netlify-cli

# Se connecter à Netlify
netlify login

# Déployer le site
netlify deploy --prod
```

### Option 3 : Drag & Drop

1. Allez sur [app.netlify.com/drop](https://app.netlify.com/drop)
2. Glissez-déposez le dossier du projet
3. Votre site sera déployé instantanément

## Technologies Utilisées

- **HTML5** : Structure sémantique
- **CSS3** : Transformations 3D, animations, gradients
- **JavaScript Vanilla** : Interactions (toggle open/close)
- **TailwindCSS** : Utilitaires de style (via CDN)
- **Google Fonts** : Police "Plus Jakarta Sans"

## Architecture CSS 3D

### Hiérarchie des Conteneurs

1. **`.scene`** : Définit la perspective (point de vue utilisateur)
2. **`.brochure`** : Conteneur parent avec `transform-style: preserve-3d`
3. **`.panel`** : Chaque volet (gauche, centre, droit)
4. **`.cover`** : Face avant (recto) fixée sur le volet droit

### Points de Pivot

- **Volet gauche** : `transform-origin: right` (pivote sur son bord droit)
- **Volet droit/couverture** : `transform-origin: left` (pivote sur son bord gauche)

### Rotations

- **État fermé** : `rotateY(175deg)` et `rotateY(-175deg)`
- **État ouvert** : `rotateY(0deg)` avec effet spring via `cubic-bezier(0.34, 1.56, 0.64, 1)`

## Améliorations Implémentées

### Textures
- Grain de papier via `repeating-linear-gradient`
- Filtre SVG de noise pour plus de réalisme

### Animations
- **Spring effect** : Rebond lors de l'ouverture
- **Float animation** : Mascotte flottante sur la couverture
- **Fade-in staggered** : Apparition séquentielle des cartes

### Effets Visuels
- Reflets brillants (`::before` et `::after`)
- Ombres portées dynamiques
- Hover effects sur le bouton CTA

## Personnalisation

### Modifier les Couleurs

Éditez les variables CSS dans `index.html` :

```css
:root {
    --indigo-600: #4f46e5;  /* Couleur principale */
    --orange-500: #f97316;  /* Couleur CTA */
    --slate-900: #0f172a;   /* Texte foncé */
    --paper-white: #ffffff; /* Fond papier */
}
```

### Ajouter des Images

Placez vos images dans `assets/images/` et mettez à jour les chemins dans le HTML.

### Modifier le Contenu

Éditez directement les sections dans `index.html` :
- **`.cover`** : Page de couverture
- **`.panel-left`** : Constat/Problème
- **`.panel-center`** : Solutions
- **`.panel-right`** : Bénéfices/CTA

## Compatibilité

- Chrome/Edge : ✅ Support complet
- Firefox : ✅ Support complet
- Safari : ✅ Support complet
- Mobile : ✅ Responsive (tactile supporté)

## Auteur

**Bastien Festor** - HEAJ 2026

## Licence

Ce projet est destiné à un usage éducatif dans le cadre du Projet Blocus.

## Liens Utiles

- [Site Projet Blocus](https://projet-blocus.vercel.app)
- [Documentation CSS 3D Transforms](https://developer.mozilla.org/en-US/docs/Web/CSS/transform)
- [Netlify Documentation](https://docs.netlify.com/)
