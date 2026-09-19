# Animations — Design System

## 🎬 **Système d’Animations**

Ce Design System utilise **3 approches** pour les animations :

| **Approche**       | **Utilisation**                          | **Avantages**                          | **Inconvénients**               |
|--------------------|------------------------------------------|----------------------------------------|---------------------------------|
| **CSS Native**     | Animations simples (hover, transitions)   | Léger, pas de JS, performant           | Limité aux transitions basiques |
| **Vanilla JS**     | Animations scroll-based (Intersection Observer) | Pas de dépendance, performant | Code plus verbeux             |
| **GSAP**           | Animations complexes (scroll-triggered, timeline) | Puissant, fluide, professionnel | ~50KB (mais inline)             |

---

## 🎨 **Animations CSS (Native)**

### **1. Transitions de Base**
Toutes les transitions utilisent les **tokens** définis dans `tokens.md` :

```css
/* Exemple avec un bouton */
.btn {
  transition: all var(--transition); /* 200ms cubic-bezier(0.4, 0, 0.2, 1) */
}

.btn:hover {
  transform: translateY(-1px);
  box-shadow: var(--shadow-md);
}
```

**Tokens disponibles** :
- `--transition-fast`: 150ms (hover rapide)
- `--transition`: 200ms (par défaut)
- `--transition-slow`: 300ms (animations lentes)

---

### **2. Animations Clé (Keyframes)**

#### **Fade In**
```css
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

/* Utilisation */
.element {
  animation: fadeIn 0.6s ease-out;
}
```

#### **Slide In (de gauche)**
```css
@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateX(-20px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

/* Utilisation */
.element {
  animation: slideIn 0.5s ease-out;
}
```

#### **Slide Up (du bas)**
```css
@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Utilisation */
.element {
  animation: slideUp 0.5s ease-out;
}
```

#### **Pulse**
```css
@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.8;
  }
}

/* Utilisation */
.element {
  animation: pulse 2s infinite;
}
```

#### **Shimmer (Effet de chargement)**
```css
@keyframes shimmer {
  0% {
    background-position: -200% 0;
  }
  100% {
    background-position: 200% 0;
  }
}

/* Utilisation */
.element {
  background: linear-gradient(
    90deg,
    var(--gray-200),
    var(--gray-300),
    var(--gray-200)
  );
  background-size: 200% 100%;
  animation: shimmer 1.5s infinite;
}
```

#### **Spin (Rotation)**
```css
@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

/* Utilisation */
.element {
  animation: spin 1s linear infinite;
}

/* Classe utilitaire */
.animate-spin {
  animation: spin 1s linear infinite;
}
```

---

### **3. Animations Appliquées aux Composants**

#### **Boutons (Ripple Effect)**
```css
.btn::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  background: rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  transition: width 0.6s ease-out, height 0.6s ease-out;
  pointer-events: none;
}

.btn:active::after {
  width: 200%;
  height: 200%;
}
```

**JavaScript pour le ripple** (déjà inclus dans le CANVAS.md) :
```javascript
document.querySelectorAll('.btn, .fab').forEach(button => {
  button.addEventListener('click', function(e) {
    const ripple = document.createElement('span');
    const rect = button.getBoundingClientRect();
    const size = Math.max(rect.width, rect.height);
    const x = e.clientX - rect.left - size / 2;
    const y = e.clientY - rect.top - size / 2;

    ripple.style.cssText = `
      position: absolute;
      width: ${size}px;
      height: ${size}px;
      left: ${x}px;
      top: ${y}px;
      background: rgba(255, 255, 255, 0.3);
      border-radius: 50%;
      transform: scale(0);
      animation: ripple 0.6s ease-out;
      pointer-events: none;
      z-index: 1;
    `;

    button.appendChild(ripple);
    setTimeout(() => ripple.remove(), 600);
  });
});
```

#### **Cartes (Hover Effect)**
```css
.project-card {
  transition: all var(--transition);
}

.project-card:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-xl);
}

.project-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--primary-500), var(--secondary-500));
  transform: scaleX(0);
  transition: transform var(--transition);
}

.project-card:hover::before {
  transform: scaleX(1);
}
```

#### **Scroll Motion (Intersection Observer)**
**JavaScript** (déjà inclus dans le CANVAS.md) :
```javascript
const observerOptions = {
  root: null,
  rootMargin: '0px',
  threshold: 0.1
};

const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
    }
  });
}, observerOptions);

// Appliquer à tous les éléments avec la classe .scroll-motion
document.querySelectorAll('.scroll-motion').forEach(el => {
  observer.observe(el);
});
```

**CSS** :
```css
.scroll-motion {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.6s ease-out, transform 0.6s ease-out;
}

.scroll-motion.visible {
  opacity: 1;
  transform: translateY(0);
}
```

---

## 🚀 **GSAP (GreenSock Animation Platform)**

### **Pourquoi GSAP ?**
- **Performant** : Optimisé pour 60 FPS.
- **Puissant** : Timelines, scroll-triggered animations, morphing SVG.
- **Professionnel** : Utilisé par les meilleurs sites (Apple, Google, etc.).

---

### **1. Intégration dans le Projet**
GSAP est **inclu en inline** dans le `CANVAS.md` (version minifiée de ~50KB).

**Alternative** : Si tu préfères une version plus légère, utilise **vanilla JS + Intersection Observer** (déjà implémenté).

---

### **2. Exemples d’Animations GSAP**

#### **Fade In + Slide Up au Scroll**
```javascript
// Animer les cartes de projet au scroll
gsap.from(".project-card", {
  scrollTrigger: {
    trigger: ".projects-grid",
    start: "top 80%",
    toggleActions: "play none none reverse"
  },
  y: 50,
  opacity: 0,
  duration: 1,
  stagger: 0.1 // Décalage entre chaque carte
});
```

#### **Scale In (Effet de zoom)**
```javascript
gsap.from(".card-header", {
  scrollTrigger: {
    trigger: ".project-card",
    start: "top 90%"
  },
  scale: 0.95,
  opacity: 0,
  duration: 0.8,
  ease: "back.out(1.7)"
});
```

#### **Parallax Effect**
```javascript
// Effet de parallaxe sur le header
gsap.to(".header", {
  scrollTrigger: {
    trigger: ".container",
    start: "top top",
    end: "bottom top",
    scrub: true
  },
  y: -50,
  ease: "none"
});
```

#### **Timeline (Séquence d’animations)**
```javascript
const tl = gsap.timeline({
  scrollTrigger: {
    trigger: ".hero",
    start: "top center"
  }
});

tl.from(".hero h1", { y: 50, opacity: 0, duration: 0.8 })
  .from(".hero p", { y: 30, opacity: 0, duration: 0.6 }, "-=0.4")
  .from(".hero .btn", { y: 20, opacity: 0, duration: 0.5 }, "-=0.2");
```

#### **Horizontal Scroll (Défilement horizontal)**
```javascript
const sections = gsap.utils.toArray(".panel");

let scrollTween = gsap.to(sections, {
  xPercent: -100 * (sections.length - 1),
  ease: "none",
  scrollTrigger: {
    trigger: ".container",
    pin: true,
    scrub: 1,
    snap: 1 / (sections.length - 1),
    end: () => "+=" + (document.querySelector(".container").scrollWidth)
  }
});
```

#### **Morphing SVG**
```javascript
// Animer un SVG (ex: icône qui se transforme)
gsap.to("#svg-path", {
  duration: 1,
  morphSVG: "#new-svg-path",
  repeat: -1,
  yoyo: true
});
```

---

### **3. ScrollTrigger (Animations Déclenchées par le Scroll)**

**ScrollTrigger** est un plugin GSAP qui permet de déclencher des animations en fonction de la position de scroll.

#### **Exemple 1 : Animation au passage**
```javascript
gsap.from(".element", {
  scrollTrigger: {
    trigger: ".element",
    start: "top 80%", // Quand le haut de l'élément atteint 80% de la fenêtre
    end: "top 20%",   // Quand le haut atteint 20%
    toggleActions: "play none none reverse", // Jouer à l'entrée, inverser à la sortie
    markers: true     // Affiche des marqueurs pour le débogage (à désactiver en prod)
  },
  y: 50,
  opacity: 0,
  duration: 1
});
```

#### **Exemple 2 : Pinning (Fixer un élément pendant le scroll)**
```javascript
gsap.to(".sidebar", {
  scrollTrigger: {
    trigger: ".main-content",
    pin: true,       // Fixe le sidebar
    start: "top top",
    end: "bottom top"
  }
});
```

#### **Exemple 3 : Scrub (Animation synchronisée avec le scroll)**
```javascript
gsap.to(".progress-bar", {
  scrollTrigger: {
    trigger: ".container",
    scrub: true,    // Animation fluide synchronisée avec le scroll
    start: "top center",
    end: "bottom center"
  },
  width: "100%",
  ease: "none"
});
```

#### **Exemple 4 : Horizontal Scroll**
```javascript
const horizontalTL = gsap.timeline({
  scrollTrigger: {
    trigger: ".horizontal-container",
    pin: true,
    scrub: 1,
    end: () => "+=" + document.querySelector(".horizontal-container").scrollWidth
  }
});

horizontalTL.to(".horizontal-items", { x: () => - (document.querySelector(".horizontal-items").scrollWidth - window.innerWidth), ease: "none" });
```

---

## 🎯 **Animations Vanilla JS (Alternative à GSAP)**

Si tu préfères éviter GSAP (~50KB), voici des alternatives **légères** en vanilla JS.

### **1. Scroll Animations (Intersection Observer)**
Déjà implémenté dans le `CANVAS.md` :
```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('animate-fade-in');
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('.animate-on-scroll').forEach(el => {
  observer.observe(el);
});
```

**CSS** :
```css
.animate-on-scroll {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.6s ease-out, transform 0.6s ease-out;
}

.animate-on-scroll.animate-fade-in {
  opacity: 1;
  transform: translateY(0);
}
```

---

### **2. Parallax Simple**
```javascript
window.addEventListener('scroll', () => {
  const scrolled = window.pageYOffset;
  const parallax = document.querySelector('.parallax');
  const speed = 0.5;
  
  parallax.style.transform = `translateY(${scrolled * speed}px)`;
});
```

---

### **3. Counter Animation**
```javascript
function animateCounter(element, target, duration = 1000) {
  const start = 0;
  const increment = target / (duration / 16);
  let current = start;
  
  const timer = setInterval(() => {
    current += increment;
    if (current >= target) {
      element.textContent = target;
      clearInterval(timer);
    } else {
      element.textContent = Math.floor(current);
    }
  }, 16);
}

// Utilisation
animateCounter(document.getElementById('counter'), 1000);
```

---

### **4. Typewriter Effect**
```javascript
function typeWriter(element, text, speed = 50) {
  let i = 0;
  element.textContent = '';
  
  const timer = setInterval(() => {
    if (i < text.length) {
      element.textContent += text.charAt(i);
      i++;
    } else {
      clearInterval(timer);
    }
  }, speed);
}

// Utilisation
typeWriter(document.getElementById('typing-text'), 'Bonjour le monde !');
```

---

## 📊 **Performance des Animations**

| **Type d’Animation**       | **Impact Performance** | **Recommandation**                          |
|----------------------------|------------------------|--------------------------------------------|
| CSS `transform`/`opacity`   | ⭐⭐⭐⭐⭐ (Très léger) | **À privilégier** pour les animations simples |
| CSS `keyframes`             | ⭐⭐⭐⭐ (Léger)        | Bon pour les animations complexes           |
| Vanilla JS (IO)            | ⭐⭐⭐⭐ (Léger)        | Alternative à GSAP pour le scroll           |
| GSAP                       | ⭐⭐⭐ (Moyen)         | **À utiliser pour les animations pro**      |
| JavaScript `setInterval`   | ⭐ (Lourd)             | **À éviter** (utilise `requestAnimationFrame`) |

---

## 🛠️ **Bonnes Pratiques**

### **✅ À Faire**
1. **Utilise `transform` et `opacity`** pour les animations (meilleur pour le GPU).
2. **Préfère `requestAnimationFrame`** à `setInterval`/`setTimeout` pour les animations JS.
3. **Désactive les animations sur mobile** si elles ne sont pas essentielles :
   ```css
   @media (max-width: 768px) {
     .element {
       animation: none !important;
     }
   }
   ```
4. **Utilise `will-change`** pour les éléments animés :
   ```css
   .element {
     will-change: transform, opacity;
   }
   ```
5. **Limite le nombre d’animations simultanées** (max 5-10 par page).

### **❌ À Éviter**
1. **Animer `width`, `height`, `top`, `left`** (mauvais pour la performance).
   → Utilise `transform: scale()` ou `transform: translate()` à la place.
2. **Animer des propriétés qui déclenchent des `layout recalculations`** (ex: `margin`, `padding`).
3. **Utiliser `setInterval` pour les animations** (pas synchro avec le refresh rate).
4. **Animer trop d’éléments en même temps** (surtout sur mobile).
5. **Oublier de nettoyer les `event listeners`** (memory leaks).

---

## 📚 **Ressources Externes**
- [GSAP Documentation](https://greensock.com/docs/) (Pour aller plus loin)
- [GSAP Learning](https://greensock.com/learning/) (Tutoriels)
- [CSS Tricks — Animations](https://css-tricks.com/almanac/properties/a/animation/) (CSS Native)
- [MDN — Intersection Observer](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API) (Vanilla JS)
- [Web Animations API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Animations_API) (Alternative à GSAP)

---

## 🎯 **Résumé des Animations Implémentées**

| **Composant**       | **Type d’Animation**               | **Technologie**       | **Fichier**          |
|---------------------|------------------------------------|-----------------------|---------------------|
| Boutons             | Ripple Effect + Hover               | CSS + JS              | CANVAS.md          |
| Cartes              | Hover (translateY + shadow)        | CSS                   | CANVAS.md          |
| Scroll Motion       | Fade In + Slide Up                 | Intersection Observer | CANVAS.md          |
| Header              | Gradient Border                   | CSS                   | CANVAS.md          |
| FAB                 | Scale + Shadow                    | CSS                   | CANVAS.md          |
| Chargement          | Spin                              | CSS                   | CANVAS.md          |

**Prochaine étape** : [Voir les Guidelines](guidelines.md) pour les règles d’usage du Design System.
