# Design System — Portfolio Report v2

**Dernière mise à jour** : 2026-09-19
**Version** : 1.0.0
**Auteur** : Stacked Stock (via Mistral)

---

## 📚 **Documentation**

| **Fichier**          | **Description**                          | **Lien** |
|----------------------|------------------------------------------|----------|
| **KNOWLEDGE.md**     | Entrypoint du Design System              | [Lire](knowledge://design-system/KNOWLEDGE.md) |
| **tokens.md**        | Tokens CSS (couleurs, typographie, etc.)  | [Lire](knowledge://design-system/tokens.md) |
| **components.md**    | Composants réutilisables (Button, Card, etc.) | [Lire](knowledge://design-system/components.md) |
| **animations.md**    | Animations (GSAP, CSS, vanilla JS)        | [Lire](knowledge://design-system/animations.md) |
| **guidelines.md**    | Règles d’usage et bonnes pratiques        | [Lire](knowledge://design-system/guidelines.md) |

---

## 🎯 **Quick Start**

### **1. Utiliser un Composant**
Copie-colle directement le code depuis [`components.md`](knowledge://design-system/components.md) :

```html
<!-- Bouton primaire -->
<button class="btn btn-primary">
  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
    <path d="M12 5v14M5 12h14"/>
  </svg>
  Bouton
</button>
```

### **2. Personnaliser un Token**
Modifie les tokens dans [`tokens.md`](knowledge://design-system/tokens.md) et met à jour le CSS :

```css
:root {
  --primary-500: #6366f1; /* Couleur principale */
  --space-md: 1rem;      /* Espacement par défaut */
}
```

### **3. Ajouter une Animation**
Utilise les exemples dans [`animations.md`](knowledge://design-system/animations.md) :

```javascript
// Animation au scroll (Intersection Observer)
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
    }
  });
});
```

---

## 📂 **Structure du Projet**

```
/knowledge/design-system/
├── README.md          # Ce fichier
├── KNOWLEDGE.md       # Entrypoint
├── tokens.md          # Tokens CSS
├── components.md       # Composants
├── animations.md       # Animations
└── guidelines.md       # Règles d’usage

/canvases/portfolio-report-v2/
└── CANVAS.md          # Implémentation HTML/CSS/JS
```

---

## 🚀 **Déploiement**

### **1. Versioning (GitHub)**
1. **Crée un repo GitHub** : `portfolio-report-v2`
2. **Push le contenu** du Canvas :
   ```bash
   git add .
   git commit -m "feat: initial design system"
   git push origin main
   ```
3. **Active GitHub Pages** pour un hébergement gratuit.

### **2. Hébergement Alternatif**
| **Service**       | **Lien**                          | **Avantages**               |
|-------------------|-----------------------------------|-----------------------------|
| GitHub Pages      | [github.com](https://github.com)  | Gratuit, intégré à GitHub     |
| Netlify           | [netlify.com](https://netlify.com) | Déploiement continu, gratuit |
| Vercel            | [vercel.com](https://vercel.com)   | Optimisé pour Next.js        |

---

## 🔧 **Outils Recommandés**

| **Outil**               | **Utilité**                          | **Lien** |
|------------------------|--------------------------------------|----------|
| **Figma**              | Design + Prototypage                 | [figma.com](https://figma.com) |
| **VS Code**            | Éditeur de code                       | [code.visualstudio.com](https://code.visualstudio.com) |
| **Chrome DevTools**    | Débogage et inspection               | Intégré à Chrome |
| **WebAIM Contrast**    | Vérification accessibilité            | [webaim.org](https://webaim.org/resources/contrastchecker) |

---

## 🤝 **Contribuer**

1. **Fork le repo** sur GitHub.
2. **Crée une branche** : `git checkout -b feature/nouveau-composant`
3. **Commit tes modifications** : `git commit -m "feat: ajoute nouveau composant"`
4. **Push et crée une PR** : `git push origin feature/nouveau-composant`

---

## 📜 **Licence**

**MIT License** – Libre d’utiliser, modifier et distribuer.

---

## 💬 **Contact**

Pour toute question ou suggestion :
- **GitHub** : [@ton_username](https://github.com/ton_username)
- **Email** : ton@email.com

---

**✨ Bon développement !** 🚀
