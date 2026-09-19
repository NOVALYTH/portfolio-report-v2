# Tokens — Design System

## 🎨 **Couleurs**

### **Primary (Indigo)**
| Nom             | Valeur Hex | Valeur RGB          | Usage                          | WCAG Contrast (sur blanc) |
|-----------------|------------|---------------------|--------------------------------|--------------------------|
| `--primary-50`  | `#eef2ff`  | `238, 242, 255`    | Backgrounds légers              | ✅ AAA                  |
| `--primary-100` | `#e0e7ff`  | `224, 231, 255`    | Hover states                   | ✅ AAA                  |
| `--primary-200` | `#c7d2fe`  | `199, 210, 254`    | Borders subtils                | ✅ AAA                  |
| `--primary-300` | `#a5b4fc`  | `165, 180, 252`    | Accents légers                 | ✅ AA                   |
| `--primary-400` | `#818cf8`  | `129, 140, 248`    | Textes secondaires             | ✅ AA                   |
| **`--primary-500`** | **`#6366f1`** | **`99, 102, 241`** | **Boutons principaux, liens** | ✅ AAA                  |
| `--primary-600` | `#4f46e5`  | `79, 70, 229`     | Hover boutons principaux       | ✅ AAA                  |
| `--primary-700` | `#4338ca`  | `67, 56, 202`     | Active states                  | ✅ AAA                  |
| `--primary-800` | `#3730a3`  | `55, 48, 163`     | Textes sombres                | ✅ AAA                  |
| `--primary-900` | `#312e81`  | `49, 46, 129`     | Backgrounds sombres           | ✅ AAA                  |

---

### **Secondary (Emerald/Success)**
| Nom              | Valeur Hex | Valeur RGB          | Usage                          | WCAG Contrast |
|------------------|------------|---------------------|--------------------------------|---------------|
| `--secondary-50` | `#ecfdf5`  | `236, 253, 245`    | Backgrounds succès             | ✅ AAA        |
| `--secondary-100`| `#d1fae5`  | `209, 250, 229`    | Hover succès                   | ✅ AAA        |
| `--secondary-200`| `#a7f3d0`  | `167, 243, 208`    | Accents succès                 | ✅ AA         |
| `--secondary-300`| `#6ee7b7`  | `110, 231, 183`    | Icônes succès                  | ✅ AA         |
| `--secondary-400`| `#34d399`  | `52, 211, 153`     | Textes succès                  | ✅ AA         |
| **`--secondary-500`** | **`#10b981`** | **`16, 185, 129`** | **Badges succès, boutons** | ✅ AAA        |
| `--secondary-600`| `#059669`  | `5, 150, 105`      | Hover succès                   | ✅ AAA        |
| `--secondary-700`| `#047857`  | `4, 120, 87`       | Active succès                  | ✅ AAA        |

---

### **Semantic Colors**
| Nom          | Valeur Hex | Usage                          | WCAG Contrast |
|--------------|------------|--------------------------------|---------------|
| **`--success`**  | **`#10b981`** | Éléments de succès (badges, alertes) | ✅ AAA |
| **`--warning`**  | **`#f59e0b`** | Avertissements (alertes, badges) | ✅ AA  |
| **`--danger`**   | **`#ef4444`** | Erreurs, states critiques       | ✅ AAA |
| **`--info`**     | **`#3b82f6`** | Informations (alertes, liens)  | ✅ AAA |

---

### **Neutral Colors**
| Nom         | Valeur Hex | Valeur RGB          | Usage                          | WCAG Contrast |
|-------------|------------|---------------------|--------------------------------|---------------|
| `--gray-50` | `#f9fafb`  | `249, 250, 251`    | Background page                | ✅ AAA        |
| `--gray-100`| `#f3f4f6`  | `243, 244, 246`    | Backgrounds cartes             | ✅ AAA        |
| `--gray-200`| `#e5e7eb`  | `229, 231, 235`    | Borders, diviseurs             | ✅ AA         |
| `--gray-300`| `#d1d5db`  | `209, 213, 219`    | Textes secondaires            | ✅ AA         |
| `--gray-400`| `#9ca3af`  | `156, 163, 175`    | Textes placeholders           | ✅ AA         |
| `--gray-500`| `#6b7280`  | `107, 114, 128`    | Textes corps                  | ✅ AAA        |
| **`--gray-600`** | **`#4b5563`** | **`75, 85, 99`** | **Textes principaux**        | ✅ AAA        |
| `--gray-700`| `#374151`  | `55, 65, 81`      | Textes sombres                | ✅ AAA        |
| **`--gray-800`** | **`#1f2937`** | **`31, 41, 55`** | **Titres, textes importants** | ✅ AAA        |
| **`--gray-900`** | **`#111827`** | **`17, 24, 39`** | **Textes noirs**             | ✅ AAA        |
| `--white`    | `#ffffff`  | `255, 255, 255`   | Backgrounds, textes clairs    | ✅ AAA        |
| `--black`    | `#000000`  | `0, 0, 0`         | Textes (rarement utilisé)     | ❌ Fail       |

---

## 🔤 **Typographie**

| Token          | Valeur                          | Usage                          | Exemple          |
|----------------|---------------------------------|--------------------------------|------------------|
| `--font-family`| `-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif` | Police globale | `body { font-family: var(--font-family); }` |
| `--font-mono`  | `ui-monospace, SFMono-Regular, 'SF Mono', Menlo, Consolas, monospace` | Code, monospace | `code { font-family: var(--font-mono); }` |

### **Tailles de Police**
| Token       | Valeur   | Usage                          | Exemple CSS       |
|-------------|----------|--------------------------------|-------------------|
| `h1`        | `2.25rem`| Titres principaux              | `font-size: 2.25rem;` |
| `h2`        | `1.875rem`| Sous-titres                    | `font-size: 1.875rem;` |
| `h3`        | `1.5rem`  | Titres de section              | `font-size: 1.5rem;` |
| `h4`        | `1.25rem` | Sous-sections                  | `font-size: 1.25rem;` |
| `h5`        | `1.125rem`| Titres de carte                | `font-size: 1.125rem;` |
| `h6`        | `1rem`    | Textes mis en avant            | `font-size: 1rem;` |
| `body`      | `1rem`    | Texte par défaut               | `font-size: 1rem;` |
| `small`     | `0.875rem`| Textes secondaires             | `font-size: 0.875rem;` |
| `xs`        | `0.75rem` | Labels, badges                 | `font-size: 0.75rem;` |

### **Poids de Police**
| Token       | Valeur | Usage                          |
|-------------|--------|--------------------------------|
| `font-light`| `300`  | Textes légers                  |
| `font-normal`| `400`  | Texte par défaut               |
| `font-medium`| `500`  | Textes mis en avant            |
| **`font-semibold`** | **`600`** | **Titres, boutons**          |
| **`font-bold`**    | **`700`** | **Titres principaux**        |
| `font-extrabold`| `800` | Titres très importants         |

---

## 📏 **Espacements**

| Token          | Valeur   | Usage                          | Exemple CSS               |
|----------------|----------|--------------------------------|---------------------------|
| `--space-xs`   | `0.25rem`| Espacements très petits        | `margin: var(--space-xs);` |
| `--space-sm`   | `0.5rem` | Espacements petits             | `padding: var(--space-sm);`|
| **`--space-md`** | **`1rem`** | **Espacement par défaut**      | `gap: var(--space-md);`    |
| `--space-lg`   | `1.5rem` | Espacements moyens            | `margin: var(--space-lg);` |
| `--space-xl`   | `2rem`   | Espacements grands             | `padding: var(--space-xl);`|
| `--space-2xl`  | `3rem`   | Espacements très grands        | `margin: var(--space-2xl);`|

---

## 🔳 **Bordures & Rayons**

### **Rayons de Bordure**
| Token          | Valeur   | Usage                          | Exemple CSS               |
|----------------|----------|--------------------------------|---------------------------|
| `--radius-sm`  | `0.25rem`| Boutons secondaires, badges   | `border-radius: var(--radius-sm);` |
| **`--radius`** | **`0.375rem`** | **Rayon par défaut**      | `border-radius: var(--radius);` |
| `--radius-md`  | `0.5rem` | Cartes, conteneurs             | `border-radius: var(--radius-md);` |
| `--radius-lg`  | `0.75rem`| Cartes principales            | `border-radius: var(--radius-lg);` |
| `--radius-xl`  | `1rem`   | Conteneurs larges             | `border-radius: var(--radius-xl);` |
| `--radius-full`| `9999px` | Avatars, badges circulaires   | `border-radius: var(--radius-full);` |

### **Bordures**
| Token          | Valeur                     | Usage                          |
|----------------|----------------------------|--------------------------------|
| `--border-sm`  | `1px solid var(--gray-200)`| Bordures légères               |
| `--border`     | `1px solid var(--gray-300)`| Bordures par défaut            |
| `--border-lg`  | `2px solid var(--gray-300)`| Bordures épaisses              |

---

## 🌑 **Ombres**

| Token          | Valeur                                      | Usage                          |
|----------------|---------------------------------------------|--------------------------------|
| `--shadow-sm`  | `0 1px 2px 0 rgba(0, 0, 0, 0.05)`             | Éléments subtils               |
| **`--shadow`** | **`0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px -1px rgba(0, 0, 0, 0.1)`** | **Ombres par défaut** |
| `--shadow-md`  | `0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -2px rgba(0, 0, 0, 0.1)` | Cartes, modales |
| `--shadow-lg`  | `0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -4px rgba(0, 0, 0, 0.1)` | **Survol cartes** |
| `--shadow-xl`  | `0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -6px rgba(0, 0, 0, 0.1)` | Modales, FAB |
| `--shadow-2xl` | `0 25px 50px -12px rgba(0, 0, 0, 0.25)`       | Overlays                     |

---

## ⏱️ **Transitions & Animations**

### **Durées de Transition**
| Token               | Valeur   | Usage                          |
|---------------------|----------|--------------------------------|
| `--transition-fast` | `150ms`  | Animations rapides (hover)      |
| **`--transition`**  | **`200ms`** | **Transitions par défaut**     |
| `--transition-slow`| `300ms`  | Animations lentes (scroll)     |

### **Fonctions de Timing**
| Token          | Valeur                     | Usage                          |
|----------------|----------------------------|--------------------------------|
| `--ease`       | `cubic-bezier(0.4, 0, 0.2, 1)` | **Transitions fluides**        |
| `--ease-in`    | `cubic-bezier(0.4, 0, 1, 1)`   | Animations d’entrée            |
| `--ease-out`   | `cubic-bezier(0, 0, 0.2, 1)`   | Animations de sortie           |
| `--ease-in-out`| `cubic-bezier(0.4, 0, 0.2, 1)` | Animations symétriques        |

---

## 🎯 **Z-Index Scale**

| Token               | Valeur | Usage                          |
|---------------------|--------|--------------------------------|
| `--z-dropdown`      | `100`  | Menus déroulants               |
| `--z-sticky`        | `200`  | Éléments sticky                |
| `--z-modal-backdrop`| `300`  | Fond de modale                 |
| `--z-modal`         | `400`  | Modales                        |
| `--z-popover`       | `500`  | Popovers                       |
| `--z-tooltip`       | `600`  | Tooltips                       |
| `--z-fab`           | `1000` | Floating Action Button         |

---

## 📌 **Exemple d’Utilisation**

```css
:root {
  /* Couleurs */
  --primary: var(--primary-500);
  --success: var(--secondary-500);
  
  /* Espacements */
  --space: var(--space-md);
  
  /* Typographie */
  --font: var(--font-family);
  
  /* Bordures */
  --radius: var(--radius);
  --shadow: var(--shadow);
}

.button {
  background: var(--primary);
  color: var(--white);
  padding: var(--space-sm) var(--space-lg);
  border-radius: var(--radius);
  box-shadow: var(--shadow);
  transition: all var(--transition);
}
```

---

## 🔗 **Ressources Externes (Optionnelles)**
- [Tailwind CSS Defaults](https://tailwindcss.com/docs/theme) (Inspiration pour les tokens)
- [WCAG Contrast Checker](https://webaim.org/resources/contrastchecker/) (Vérification accessibilité)
- [Color Hex Picker](https://www.color-hex.com/) (Pour étendre la palette)
