# Guidelines — Design System

## 📜 **Règles d’Usage du Design System**

Ce document définit les **bonnes pratiques** pour utiliser le Design System du **Portfolio Report v2** de manière **cohérente, performante et accessible**.

---

## 🎯 **Principes Fondamentaux**

### **1. Cohérence**
- **Un seul Design System** : Tous les projets doivent utiliser **ce même DS** (pas de déviations).
- **Réutilisation** : Toujours utiliser les **composants existants** avant d’en créer de nouveaux.
- **Tokens** : Utiliser les **tokens CSS** (`--primary-500`, `--space-md`, etc.) au lieu de valeurs hardcodées.

### **2. Performance**
- **Self-contained** : Tout doit être **inline** (pas de CDN, pas de dépendances externes).
- **Léger** : Éviter les animations lourdes sur mobile.
- **Optimisé** : Utiliser `transform` et `opacity` pour les animations (meilleur pour le GPU).

### **3. Accessibilité**
- **Contraste** : Respecter **WCAG AAA** (contraste ≥ 4.5:1 pour le texte).
- **Navigation** : Tout doit être **accessible au clavier** (tab order, focus states).
- **Sémantique** : Utiliser les **balises HTML appropriées** (`<button>`, `<nav>`, etc.).

### **4. Responsive**
- **Mobile-first** : Designer pour mobile **en premier**, puis desktop.
- **Breakpoints** : Utiliser les breakpoints standard :
  - `768px` (Tablette → Mobile)
  - `1024px` (Desktop → Tablette)
- **Flexible** : Utiliser `flex`, `grid`, et `%`/`rem` au lieu de `px` fixes.

---

## 🎨 **Règles de Design**

### **1. Couleurs**

#### **📌 Utilisation des Couleurs**
| **Couleur**          | **Utilisation**                          | **Exemple**                          | **Ne pas utiliser pour** |
|----------------------|------------------------------------------|--------------------------------------|-------------------------|
| `--primary-500`      | Boutons principaux, liens                 | `<button class="btn btn-primary">` | Textes longs           |
| `--primary-600`      | Hover des boutons principaux             | `.btn-primary:hover`                 | Backgrounds            |
| `--secondary-500`    | Boutons secondaires, badges succès        | `<span class="badge badge-success">` | Erreurs              |
| `--success`          | États de succès                          | Badges, alertes                       | Boutons principaux     |
| `--warning`          | Avertissements                           | Alertes, badges                      | Boutons              |
| `--danger`           | Erreurs, états critiques                 | Alertes, badges                      | Boutons principaux     |
| `--gray-600`         | Textes principaux                        | `<p>`, `<span>`                      | Backgrounds            |
| `--gray-500`         | Textes secondaires                       | Labels, placeholders                 | Titres                 |
| `--gray-400`         | Textes tertiaires                        | Placeholders, hints                  | Contenu principal      |
| `--white`           | Backgrounds, textes clairs               | Cartes, modales                      | Textes sur fond clair  |
| `--gray-900`         | Textes noirs                             | Titres, textes importants            | Backgrounds            |

#### **⚠️ Interdictions**
- ❌ **Ne pas utiliser `#000000`** (noir pur) → Utiliser `--gray-900` (`#111827`).
- ❌ **Ne pas utiliser de couleurs hardcodées** → Toujours utiliser les **tokens**. 
  ```css
  /* ❌ Mauvaise pratique */
  .element { color: #6366f1; }
  
  /* ✅ Bonne pratique */
  .element { color: var(--primary-500); }
  ```
- ❌ **Ne pas utiliser de couleurs non accessibles** → Vérifier avec [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/).

#### **🎯 Bonnes Pratiques**
- ✅ **Utiliser des dégradés** pour les boutons et headers :
  ```css
  background: linear-gradient(135deg, var(--primary-500), var(--primary-600));
  ```
- ✅ **Utiliser `--primary-50` à `--primary-100`** pour les backgrounds légers.
- ✅ **Utiliser `--gray-100` à `--gray-200`** pour les borders et diviseurs.

---

### **2. Typographie**

#### **📌 Hiérarchie Typographique**
| **Niveau**       | **Balise** | **Taille** | **Poids** | **Couleur**       | **Utilisation**               |
|------------------|------------|------------|-----------|-------------------|---------------------------------|
| Titre Principal  | `h1`       | `2.25rem`  | `700`     | `--gray-900`      | Titre de page                  |
| Titre Secondaire | `h2`       | `1.875rem` | `700`     | `--gray-900`      | Titre de section               |
| Sous-titre       | `h3`       | `1.5rem`   | `700`     | `--gray-900`      | Sous-section                  |
| Titre de Carte   | `h4`/`h5`  | `1.25rem`  | `700`     | `--gray-900`      | Titre dans une carte           |
| Texte Principal  | `p`        | `1rem`     | `400`     | `--gray-600`      | Contenu principal              |
| Texte Secondaire | `small`    | `0.875rem` | `400`     | `--gray-500`      | Contenu secondaire             |
| Label            | `span`     | `0.75rem`  | `600`     | `--gray-500`      | Labels, métadonnées            |

#### **⚠️ Interdictions**
- ❌ **Ne pas utiliser `font-size` en `px`** → Toujours utiliser `rem`.
- ❌ **Ne pas utiliser `!important`** pour la typographie.
- ❌ **Ne pas dépasser 3 niveaux de titres** par page (h1, h2, h3).

#### **🎯 Bonnes Pratiques**
- ✅ **Limiter la longueur des lignes** à **60-75 caractères** pour une lisibilité optimale.
- ✅ **Utiliser `line-height: 1.5`** pour le corps de texte.
- ✅ **Utiliser `letter-spacing`** pour les textes en majuscules :
  ```css
  text-transform: uppercase;
  letter-spacing: 0.05em;
  ```

---

### **3. Espacements**

#### **📌 Échelle d’Espacements**
| **Token**       | **Valeur** | **Utilisation**                          |
|-----------------|------------|------------------------------------------|
| `--space-xs`    | `0.25rem`  | Espacements très petits (icônes, badges) |
| `--space-sm`    | `0.5rem`   | Espacements petits (padding boutons)    |
| **`--space-md`**| **`1rem`** | **Espacement par défaut**                |
| `--space-lg`    | `1.5rem`   | Espacements moyens (marges sections)    |
| `--space-xl`    | `2rem`     | Espacements grands (marges conteneurs)   |
| `--space-2xl`   | `3rem`     | Espacements très grands (marges pages)   |

#### **⚠️ Interdictions**
- ❌ **Ne pas utiliser de marges/espacements en `px`** → Toujours utiliser `rem` ou les tokens.
- ❌ **Ne pas utiliser `margin: auto`** pour centrer verticalement.
- ❌ **Éviter les marges négatives** (sauf cas très spécifiques).

#### **🎯 Bonnes Pratiques**
- ✅ **Utiliser `--space-md` (1rem) comme espacement par défaut**.
- ✅ **Utiliser des multiples de `--space-md`** pour une cohérence :
  ```css
  /* ✅ Bonne pratique */
  .element { margin-bottom: calc(var(--space-md) * 2); }
  
  /* ❌ Mauvaise pratique */
  .element { margin-bottom: 24px; }
  ```
- ✅ **Utiliser `gap` pour les grilles et flexboxes** :
  ```css
  .grid { gap: var(--space-lg); }
  ```

---

### **4. Ombres**

#### **📌 Hiérarchie des Ombres**
| **Token**       | **Valeur**                                      | **Utilisation**                          |
|-----------------|-------------------------------------------------|------------------------------------------|
| `--shadow-sm`   | `0 1px 2px 0 rgba(0,0,0,0.05)`                   | Éléments subtils (boutons outline)         |
| **`--shadow`**  | `0 1px 3px 0 rgba(0,0,0,0.1), 0 1px 2px -1px rgba(0,0,0,0.1)` | **Ombres par défaut** (cartes) |
| `--shadow-md`   | `0 4px 6px -1px rgba(0,0,0,0.1), 0 2px 4px -2px rgba(0,0,0,0.1)` | Cartes au survol |
| `--shadow-lg`   | `0 10px 15px -3px rgba(0,0,0,0.1), 0 4px 6px -4px rgba(0,0,0,0.1)` | **Cartes au survol** |
| `--shadow-xl`   | `0 20px 25px -5px rgba(0,0,0,0.1), 0 8px 10px -6px rgba(0,0,0,0.1)` | Modales, FAB |
| `--shadow-2xl`  | `0 25px 50px -12px rgba(0,0,0,0.25)`             | Overlays                              |

#### **⚠️ Interdictions**
- ❌ **Ne pas utiliser `box-shadow: none`** sur les cartes (sauf si nécessaire).
- ❌ **Ne pas utiliser d’ombres trop fortes** sur mobile.

#### **🎯 Bonnes Pratiques**
- ✅ **Utiliser `--shadow` pour les cartes par défaut**.
- ✅ **Utiliser `--shadow-lg` ou `--shadow-xl` au survol** pour un effet de profondeur.
- ✅ **Désactiver les ombres sur mobile** si elles nuisent à la performance :
  ```css
  @media (max-width: 768px) {
    .card { box-shadow: none; }
  }
  ```

---

### **5. Bordures & Rayons**

#### **📌 Échelle des Rayons**
| **Token**       | **Valeur** | **Utilisation**                          |
|-----------------|------------|------------------------------------------|
| `--radius-sm`   | `0.25rem`  | Boutons secondaires, badges              |
| **`--radius`**  | **`0.375rem`** | **Rayon par défaut** (boutons, inputs) |
| `--radius-md`   | `0.5rem`   | Cartes, conteneurs                        |
| `--radius-lg`   | `0.75rem`  | **Cartes principales**                   |
| `--radius-xl`   | `1rem`     | Conteneurs larges                        |
| `--radius-full` | `9999px`  | Avatars, badges circulaires              |

#### **⚠️ Interdictions**
- ❌ **Ne pas utiliser `border-radius: 50%`** → Utiliser `--radius-full`.
- ❌ **Ne pas mélanger les rayons** sur un même élément.

#### **🎯 Bonnes Pratiques**
- ✅ **Utiliser `--radius-lg` pour les cartes**.
- ✅ **Utiliser `--radius-full` pour les avatars et badges circulaires**.
- ✅ **Utiliser `--radius` pour les boutons et inputs**.

---

## 🖥️ **Règles de Développement**

### **1. HTML**

#### **📌 Bonnes Pratiques**
- ✅ **Utiliser des balises sémantiques** :
  ```html
  <!-- ✅ Bonne pratique -->
  <header>, <main>, <footer>, <section>, <article>, <nav>, <button>
  
  <!-- ❌ Mauvaise pratique -->
  <div class="header">, <div class="button">
  ```
- ✅ **Utiliser `aria-*` pour l’accessibilité** :
  ```html
  <button aria-label="Fermer" aria-expanded="false">
    <svg>...</svg>
  </button>
  ```
- ✅ **Utiliser `data-*` pour les attributs custom** :
  ```html
  <button data-tooltip="Exporter en PDF">Exporter</button>
  ```
- ✅ **Minifier les SVG** :
  ```html
  <!-- ✅ Bonne pratique -->
  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
    <path d="M12 5v14M5 12h14"/>
  </svg>
  
  <!-- ❌ Mauvaise pratique (SVG non minifié) -->
  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 5v14M5 12h14"/>
  </svg>
  ```

#### **⚠️ Interdictions**
- ❌ **Ne pas utiliser `<div>` pour des boutons** → Toujours utiliser `<button>`.
- ❌ **Ne pas oublier `alt` sur les images** :
  ```html
  <!-- ❌ Mauvaise pratique -->
  <img src="logo.png">
  
  <!-- ✅ Bonne pratique -->
  <img src="logo.png" alt="Logo de l'entreprise">
  ```
- ❌ **Ne pas utiliser `style=` en ligne** → Toujours utiliser des classes CSS.

---

### **2. CSS**

#### **📌 Bonnes Pratiques**
- ✅ **Utiliser les tokens CSS** :
  ```css
  /* ✅ Bonne pratique */
  .element { color: var(--primary-500); }
  
  /* ❌ Mauvaise pratique */
  .element { color: #6366f1; }
  ```
- ✅ **Utiliser `rem` pour les tailles** :
  ```css
  /* ✅ Bonne pratique */
  .element { padding: 1rem; }
  
  /* ❌ Mauvaise pratique */
  .element { padding: 16px; }
  ```
- ✅ **Utiliser `flex` et `grid` pour les layouts** :
  ```css
  /* ✅ Bonne pratique */
  .container { display: grid; gap: 1rem; }
  
  /* ❌ Mauvaise pratique */
  .container { display: block; margin-bottom: 1rem; }
  ```
- ✅ **Utiliser `clamp()` pour les tailles responsives** :
  ```css
  .element { font-size: clamp(1rem, 2vw, 1.5rem); }
  ```
- ✅ **Utiliser `object-fit: cover` pour les images** :
  ```css
  img { object-fit: cover; width: 100%; height: 100%; }
  ```

#### **⚠️ Interdictions**
- ❌ **Ne pas utiliser `!important`** (sauf cas très spécifiques).
- ❌ **Ne pas utiliser `position: absolute` sans raison** (casse le flux).
- ❌ **Ne pas utiliser `z-index` sans nécessité** (risque de conflits).
- ❌ **Ne pas utiliser `* { margin: 0; padding: 0; }`** → Utiliser un reset moderne.

---

### **3. JavaScript**

#### **📌 Bonnes Pratiques**
- ✅ **Utiliser `addEventListener`** :
  ```javascript
  // ✅ Bonne pratique
  button.addEventListener('click', handleClick);
  
  // ❌ Mauvaise pratique
  button.onclick = handleClick;
  ```
- ✅ **Nettoyer les event listeners** :
  ```javascript
  function setup() {
    const button = document.querySelector('.btn');
    const handleClick = () => { /* ... */ };
    button.addEventListener('click', handleClick);
    
    return () => {
      button.removeEventListener('click', handleClick);
    };
  }
  ```
- ✅ **Utiliser `requestAnimationFrame` pour les animations** :
  ```javascript
  function animate() {
    // Mise à jour de l'animation
    requestAnimationFrame(animate);
  }
  requestAnimationFrame(animate);
  ```
- ✅ **Utiliser `dataset` pour les données custom** :
  ```javascript
  const tooltipText = button.dataset.tooltip;
  ```

#### **⚠️ Interdictions**
- ❌ **Ne pas utiliser `setInterval`/`setTimeout` pour les animations** → Utiliser `requestAnimationFrame`.
- ❌ **Ne pas utiliser `innerHTML`** → Utiliser `textContent` ou `createElement`.
- ❌ **Ne pas utiliser `eval()`** (risque de sécurité).
- ❌ **Ne pas bloquer le thread principal** avec des boucles longues.

---

### **4. Performance**

#### **📌 Optimisations**
| **Optimisation**               | **Impact**                          | **Exemple**                          |
|--------------------------------|-------------------------------------|--------------------------------------|
| Utiliser `transform`/`opacity`  | ⭐⭐⭐⭐⭐ (Meilleur pour le GPU)     | `transform: translateY(10px);`        |
| Éviter `width`/`height`        | ⭐⭐⭐⭐ (Mauvais pour le layout)    | ❌ `width: 100px;` → ✅ `transform: scaleX(1.1);` |
| Lazy Loading                   | ⭐⭐⭐⭐ (Images)                     | `<img loading="lazy" src="...">`   |
| `will-change`                  | ⭐⭐⭐ (Préparation GPU)               | `.element { will-change: transform; }` |
| Debounce/Throttle             | ⭐⭐⭐ (Événements scroll/resize)      | `lodash.debounce(handleResize, 100)` |

#### **⚠️ À Éviter**
- ❌ **Animer trop d’éléments en même temps** (surtout sur mobile).
- ❌ **Utiliser des images non optimisées** (toujours compresser en WebP).
- ❌ **Charger des polices non nécessaires** (limiter à 1-2 polices).
- ❌ **Ne pas utiliser `preload` pour les ressources critiques** :
  ```html
  <!-- ✅ Bonne pratique -->
  <link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin>
  ```

---

### **5. Accessibilité**

#### **📌 Checklist WCAG**
| **Critère**                          | **Niveau** | **Exemple**                          |
|--------------------------------------|------------|--------------------------------------|
| Contraste des couleurs ≥ 4.5:1      | AAA        | `--gray-800` sur `--white`           |
| Texte alternatif pour les images     | A          | `<img alt="Description">`          |
| Navigation au clavier                | A          | `tabindex`, `focus` states            |
| Labels pour les inputs               | A          | `<label for="input">`              |
| ARIA pour les composants custom      | A          | `aria-label`, `aria-expanded`        |
| Pas de contenu clignotant            | A          | Éviter `animation: blink`            |
| Ordre de tabulation logique          | A          | `tabindex` si nécessaire              |

#### **⚠️ Interdictions**
- ❌ **Ne pas utiliser `display: none` pour cacher du contenu** → Utiliser `aria-hidden=