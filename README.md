# ONPPC – Gouvernance Logistique Dashboard

**Dashboard interactif** documentant la réflexion stratégique sur le renforcement de la gouvernance logistique de l'ONPPC (Office National des Produits Pharmaceutiques et Chimiques) au Niger, dans le cadre du projet PSM Chemonics financé par le Fonds Mondial.

---

## Documents de référence

| Document | Description | Lien |
|---|---|---|
| Note de réflexion | Document principal de réflexion stratégique sur la gouvernance logistique | [Ouvrir dans Google Drive](https://docs.google.com/document/d/17hc899Oqsiz1uWMcfBxN5Xx38ajYg_36/edit?usp=sharing) |
| Note de plaidoyer | Note de plaidoyer UGL–UGS–ONPPC | [Ouvrir dans Google Drive](https://docs.google.com/document/d/1bbBSzyTz1W31jGaBxCxtmJ3ze73xAf7s/edit?usp=sharing) |

---

## Contexte et conception

### Contexte programmatique

Le projet PSM (Procurement and Supply Management) de Chemonics International intervient au Niger depuis plus de 8 ans dans le renforcement de la chaîne d'approvisionnement pharmaceutique. Ce dashboard synthétise la réflexion stratégique autour d'un mécanisme de gouvernance logistique durable centré sur l'ONPPC.

### Proposition centrale : l'Unité de Gestion Logistique (UGL)

La proposition est la création d'une **UGL (Unité de Gestion Logistique)** au sein de l'UGS Fonds Mondial (Unité de Gestion des Subventions), physiquement hébergée à l'ONPPC. Ce mécanisme matriciel implique un double rattachement :

- **Rattachement administratif et financier** → UGS Fonds Mondial
- **Rattachement technique et opérationnel** → ONPPC

L'objectif est de convaincre le Ministère de créer cette UGL pour assurer une gestion logistique structurée et pérenne, indépendante des financements FM à terme.

### Structure narrative du document

Le dashboard suit la progression argumentative suivante :

1. **Constat** – Situation logistique actuelle et lacunes constatées
2. **Enjeu stratégique** – Importance de la gouvernance logistique pour l'ONPPC
3. **L'UGL** – Arguments en faveur de la création de l'unité
4. **Schéma de gouvernance** – Visualisation matricielle du double rattachement
5. **Phases d'intervention** – Plan d'action 2026–2030 en 3 phases
6. **Partenariat** – Rôle de Chemonics et collaboration institutionnelle

---

## Fichiers

| Fichier | Description |
|---|---|
| `ONPPC_Gouvernance_Logistique.html` | Dashboard principal (single-file, auto-contenu) |
| `Schema_Gouvernance_UGL.html` | Schéma matriciel standalone, optimisé impression A4 |
| `README.md` | Ce fichier de documentation |

---

## Spécifications UI/UX

### Palette de couleurs (marque CHEMONICS)

| Variable CSS | Valeur hex | Usage |
|---|---|---|
| `--teal` | `#005D83` | Couleur primaire, titres, icônes |
| `--teal-dark` | `#00202D` | Fond hero, nav, en-têtes de section |
| `--teal-mid` | `#00A095` | Teal intermédiaire |
| `--cyan` | `#00B7F1` | Accent cyan vif |
| `--lime` | `#9DBB2E` | Accent lime, badges, bordures actives |
| `--lime-dark` | `#7A9322` | Lime foncé (hover) |
| `--orange` | `#FF7F32` | Accent secondaire |
| `--bg-light` | `#E1F4FD` | Fond cartes clair |
| `--text-dark` | `#333E48` | Texte corps principal |
| `--text-mid` | `#54585A` | Texte secondaire |
| `--border` | `#CEDBE6` | Bordures |

### Typographie

- **Titres / headings** : `'Aptos Display', 'Aptos', 'Segoe UI', 'Source Sans 3', system-ui, sans-serif`
- **Corps** : `'Aptos', 'Segoe UI', 'Source Sans 3', system-ui, sans-serif`
- **Taille de base** : 15px, line-height 1.6

> Aptos est la police d'entreprise de Microsoft Office 2023+. Le stack assure le fallback sur Segoe UI puis les polices système.

### Layout

- **Navigation** : fixe en haut, hauteur 54px, fond `--teal-dark`, accent lime 3px en haut
- **Hero** : dégradé `teal-dark → #00415C → teal`, hauteur auto, padding 60px 52px
- **Sections** : alternance fond blanc / `#F5F8FA`, padding 48px 52px
- **Barre de section** : fond `--teal-dark`, label texte 10px uppercase, letter-spacing 2px

### Responsive

| Breakpoint | Comportement |
|---|---|
| `> 960px` | Layout complet, grilles multi-colonnes |
| `≤ 960px` | Grilles passent en 1 colonne, hero adapté |
| `≤ 600px` | Mobile : padding réduit, hero stats empilées, nav overflow-x:auto |

### Icônes

Tous les icônes sont des **SVG inline** (aucun emoji, aucune dépendance externe) :
- ViewBox 44×44
- Stroke-based, fond transparent
- Couleur principale : `#005D83` (teal)
- Accent : `#9DBB2E` (lime)
- stroke-width : 2.0–2.8px selon l'importance visuelle

### Logo ONPPC (hero)

Le logo ONPPC est intégré en **base64** comme `background-image` CSS sur un cercle blanc de 104px :
```css
background-size: 82%;
background-position: center center;
background-repeat: no-repeat;
```

### Logos pied de page

- **Chemonics** : SVG inline blanc (`cls-2: #ffffff`)
- **ONPPC** : SVG avec `filter: brightness(0) invert(1)` pour rendu blanc sur fond sombre

---

## Spécifications de code

### Architecture technique

Le dashboard est un **fichier HTML unique auto-contenu** (single-file HTML) :
- Tout le CSS est dans `<head>` (balise `<style>`)
- Tout le JavaScript est en bas de `<body>` (balise `<script>`)
- Aucune dépendance externe (pas de CDN, pas de framework)
- Le logo ONPPC PNG est encodé en base64 dans le CSS

### Structure HTML

```
<html lang="fr">
├── <head>
│   ├── Meta (charset, viewport)
│   ├── <title>
│   └── <style> — CSS complet (~500 lignes)
│       ├── :root — variables CSS CHEMONICS
│       ├── Reset
│       ├── Nav
│       ├── Hero
│       ├── Section base
│       ├── Cards (constat, enjeu, ugpl)
│       ├── UGL arguments grid
│       ├── Matrix schema (préfixe ms-)
│       ├── Phases timeline
│       ├── Partenariat
│       ├── Footer
│       └── @media queries
└── <body>
    ├── <nav> — navigation fixe avec liens de section
    ├── <main>
    │   ├── Section hero
    │   ├── #constat — Constat logistique
    │   ├── #enjeu — Enjeu stratégique
    │   ├── #ugpl — L'UGL (arguments + responsabilités)
    │   ├── #schema-ugl — Schéma de gouvernance matriciel
    │   ├── #phases — Phases d'intervention 2026–2030
    │   └── #partenariat — Partenariat Chemonics–ONPPC
    └── <footer>
        └── Logos Chemonics + ONPPC + lien document
```

### CSS Architecture

#### Variables globales (`:root`)
Toutes les couleurs, typographies, ombres et rayons sont définis comme custom properties CSS dans `:root`. Usage systématique de `var()` dans tout le document.

#### Isolation du schéma matriciel (préfixe `ms-`)
Les styles du schéma de gouvernance utilisent le préfixe `ms-` (matrix schema) pour éviter les conflits avec le reste du dashboard :
```css
.ms-top-row   /* ligne du haut (UGS + ONPPC) */
.ms-box       /* conteneur de carte */
.ms-box-head  /* en-tête coloré de carte */
.ms-ugs       /* carte UGS Fonds Mondial */
.ms-onppc     /* carte ONPPC */
.ms-ugl       /* carte centrale UGL */
.ms-ugl-wrap  /* conteneur centré de l'UGL */
.ms-connector /* SVG des flèches de connexion */
```

> **Décision architecturale** : Les styles du schéma avaient initialement été placés dans un `<style>` embedded dans le `<body>` (à l'intérieur d'une div `.reveal`). L'animation `.reveal { opacity: 0 }` masquait le `<style>` avant que le navigateur ne le parse, cassant le layout. Solution : déplacement de tous les styles dans `<head>` avec le préfixe `ms-`.

#### Animations scroll

```css
/* État initial (caché) */
.reveal {
  opacity: 0;
  transform: translateY(18px);
  transition: opacity .55s ease, transform .55s ease;
}
/* Visible après intersection */
.reveal.visible {
  opacity: 1;
  transform: none;
}
/* Délais en cascade */
.d1 { transition-delay: .10s; }
.d2 { transition-delay: .20s; }
.d3 { transition-delay: .30s; }
```

### JavaScript

#### Navigation scroll-spy (IntersectionObserver)
```javascript
// Observer chaque section et mettre à jour le lien actif dans la nav
const sections = document.querySelectorAll('section[id]');
const navLinks = document.querySelectorAll('.nav-links a');
const observer = new IntersectionObserver(cb, { threshold: 0.3 });
```

#### Animations reveal (IntersectionObserver)
```javascript
const revealObserver = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) e.target.classList.add('visible');
  });
}, { threshold: 0.12 });
document.querySelectorAll('.reveal').forEach(el => revealObserver.observe(el));
```

### Schéma de gouvernance SVG

Le schéma matriciel est une **disposition à deux niveaux** :
- **Niveau supérieur** : deux boîtes côte à côte — UGS Fonds Mondial (gauche) et ONPPC (droite)
- **Niveau inférieur** : boîte centrale UGL (62% de largeur)
- **Connecteurs** : SVG `viewBox="0 0 800 110"` avec deux lignes diagonales et pointes de flèches

Calcul des pointes de flèches (géométrie vectorielle) :
```svg
<!-- Ligne gauche (UGS → UGL) : de (200,4) vers (370,96) -->
<line x1="200" y1="4" x2="370" y2="96" stroke="#00202D" stroke-width="2.4"/>
<polyline points="354.8,94.6 370,96 360.5,84.1" .../>

<!-- Ligne droite (ONPPC → UGL) : de (600,4) vers (430,96) stroke-dasharray pour différencier -->
<line x1="600" y1="4" x2="430" y2="96" stroke="#0079A6" stroke-width="2.4" stroke-dasharray="8,5"/>
<polyline points="439.5,84.1 430,96 445.2,94.6" .../>
```

---

## Contenu des sections

### Hero
- **Titre** : "Réflexion sur le renforcement de la **Gouvernance Logistique** de l'ONPPC"
- **Eyebrow** : "Note de réflexion · Juin 2026"
- **3 badges** : 10 Composantes BPE / 3 Phases d'intervention proposées / 8+ Ans de présence Chemonics au Niger

### Navigation (ancres)
| Lien | Section |
|---|---|
| Constat | `#constat` |
| Enjeu | `#enjeu` |
| UGL | `#ugpl` |
| Schéma UGL | `#schema-ugl` |
| Phases | `#phases` |
| Partenariat | `#partenariat` |

### L'UGL – 6 arguments (grille `.ugl-args-grid`)
1. Structurer la gestion quotidienne de l'entrepôt FM
2. Garantir la conformité BPE (10 composantes)
3. Renforcer les capacités institutionnelles de l'ONPPC
4. Optimiser la coordination avec les partenaires
5. Préparer la transition vers l'autonomie (UGPL future)
6. Maximiser le retour sur investissement FM

### L'UGL – 5 domaines de responsabilité (`.ugpl-grid`)
1. Gouvernance des actifs logistiques
2. Conformité & assurance qualité
3. Gestion des stocks FM
4. Système d'information logistique
5. Développement des capacités

### Phases (Timeline 2026–2030)
| Phase | Période | Objectif |
|---|---|---|
| Phase 1 | 2026–2027 | Création et démarrage de l'UGL |
| Phase 2 | 2027–2028 | Consolidation et transfert de compétences |
| Phase 3 | 2028–2030 | Pérennisation et autonomisation (UGPL) |

---

## Décisions de design clés

### Langage diplomatique
Le dashboard évite systématiquement les termes négatifs ("insuffisant", "absent", "défaillance", "lacune") au profit d'un langage constructif orienté opportunités. Exception : le terme technique "non-conformités" est conservé dans le contexte BPE.

### Gouvernance matricielle vs hiérarchie linéaire
Le schéma a évolué d'une représentation linéaire (UGS → UGL → ONPPC) vers une représentation **matricielle à deux niveaux** pour mieux illustrer le double rattachement : l'UGL n'est pas un intermédiaire mais une unité ayant deux lignes d'autorité distinctes.

### Single-file HTML
Le choix d'un fichier HTML unique facilite la distribution (email, partage direct) sans dépendances serveur, tout en maintenant une qualité de rendu professionnelle.

---

## Déploiement

Le dashboard est déployé sur Netlify : **[onppc-gouvernance-logistique.netlify.app](https://onppc-gouvernance-logistique.netlify.app)**

---

## Historique des révisions

| Date | Modification |
|---|---|
| Juin 2026 | Création initiale du dashboard |
| Juin 2026 | Remplacement UGPL → UGL, refonte argumentaire |
| Juin 2026 | Ajout schéma matriciel de gouvernance |
| Juin 2026 | Compatibilité mobile, correction icônes SVG |
| Juillet 2026 | Mise à jour lien Google Drive, langage diplomatique |

---

*Produit par Chemonics International – Projet PSM Niger – Juillet 2026*
