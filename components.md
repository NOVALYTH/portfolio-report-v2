# Composants — Design System

## 🧩 **Liste des Composants**

| **Composant**       | **Description**                          | **Variantes**               | **Fichier**          |
|---------------------|------------------------------------------|-----------------------------|---------------------|
| **Button**          | Bouton interactif avec ripple effect     | primary, secondary, outline, ghost, danger, sm, lg, icon | ✅ Implémenté |
| **Badge**           | Étiquette pour statuts                   | success, warning, danger, neutral | ✅ Implémenté |
| **Card**            | Conteneur pour projets                   | active, warning, danger, paused | ✅ Implémenté |
| **Alert**           | Message d’alerte                         | info, warning, success, danger | ✅ Implémenté |
| **ProgressBar**     | Barre de progression                    | - | ✅ Implémenté |
| **Tooltip**         | Info-bulle au survol                     | - | ✅ Implémenté |
| **Avatar**          | Image/icône circulaire                    | sm, md, lg | ✅ Implémenté |
| **ProjectCard**     | Carte de projet (spécifique)             | - | ✅ Implémenté |
| **Header**          | En-tête de page                          | - | ✅ Implémenté |
| **Footer**          | Pied de page                             | - | ✅ Implémenté |
| **FAB**             | Floating Action Button                   | - | ✅ Implémenté |

---

## 🔘 **Button**

### **Props**
| Prop          | Type       | Default     | Description                     |
|---------------|------------|-------------|---------------------------------|
| `variant`     | string     | `primary`   | `primary`, `secondary`, `outline`, `ghost`, `danger` |
| `size`        | string     | `md`        | `sm`, `md`, `lg`, `icon` |
| `disabled`    | boolean    | `false`     | Désactive le bouton |
| `tooltip`     | string     | `null`      | Texte de l’info-bulle (via `data-tooltip`) |

### **Code HTML**
```html
<!-- Bouton primaire (par défaut) -->
<button class="btn btn-primary">
  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
    <path d="M12 5v14M5 12h14"/>
  </svg>
  Bouton
</button>

<!-- Bouton secondaire -->
<button class="btn btn-secondary">Valider</button>

<!-- Bouton outline -->
<button class="btn btn-outline">Annuler</button>

<!-- Bouton ghost (transparent) -->
<button class="btn btn-ghost">Supprimer</button>

<!-- Bouton danger -->
<button class="btn btn-danger">Supprimer</button>

<!-- Bouton avec icône seule -->
<button class="btn btn-primary btn-icon" aria-label="Ajouter">
  <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
    <path d="M12 5v14M5 12h14"/>
  </svg>
</button>

<!-- Bouton avec tooltip -->
<button class="btn btn-outline tooltip" data-tooltip="Exporter en PDF">
  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
    <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/>
  </svg>
  Exporter
</button>
```

### **Code CSS** (Déjà inclus dans le CANVAS.md)
```css
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  font-size: 0.875rem;
  font-weight: 600;
  border-radius: 0.375rem;
  border: none;
  cursor: pointer;
  transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
  position: relative;
  overflow: hidden;
}

.btn:hover {
  transform: translateY(-1px);
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
}

.btn:active {
  transform: translateY(0);
}

.btn-primary {
  background: linear-gradient(135deg, #6366f1, #4f46e5);
  color: white;
}

.btn-secondary {
  background: linear-gradient(135deg, #10b981, #059669);
  color: white;
}

.btn-outline {
  background: transparent;
  border: 1px solid #d1d5db;
  color: #4b5563;
}

.btn-outline:hover {
  background: #f3f4f6;
  border-color: #9ca3af;
}

.btn-ghost {
  background: transparent;
  color: #6b7280;
}

.btn-ghost:hover {
  background: #f3f4f6;
  color: #1f2937;
}

.btn-danger {
  background: #ef4444;
  color: white;
}

.btn-danger:hover {
  background: #dc2626;
}

.btn-sm { padding: 0.25rem 0.75rem; font-size: 0.75rem; }
.btn-lg { padding: 0.75rem 1.5rem; font-size: 1rem; }
.btn-icon { padding: 0.5rem; width: 2.25rem; height: 2.25rem; }

/* Ripple Effect */
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

---

## 🏷️ **Badge**

### **Props**
| Prop          | Type       | Default     | Description                     |
|---------------|------------|-------------|---------------------------------|
| `variant`     | string     | `primary`   | `primary`, `secondary`, `success`, `warning`, `danger`, `neutral` |

### **Code HTML**
```html
<!-- Badge de statut "Actif" -->
<span class="badge badge-success">Actif</span>

<!-- Badge de statut "En pause" -->
<span class="badge badge-neutral">En Pause</span>

<!-- Badge de statut "Warning" -->
<span class="badge badge-warning">Attention</span>

<!-- Badge de statut "Danger" -->
<span class="badge badge-danger">Critique</span>
```

### **Code CSS**
```css
.badge {
  display: inline-flex;
  align-items: center;
  padding: 0.25rem 0.5rem;
  font-size: 0.75rem;
  font-weight: 600;
  border-radius: 9999px;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.badge-primary {
  background: #eef2ff;
  color: #4338ca;
}

.badge-secondary {
  background: #d1fae5;
  color: #047857;
}

.badge-success {
  background: #d1fae5;
  color: #047857;
}

.badge-warning {
  background: #fef3c7;
  color: #92400e;
}

.badge-danger {
  background: #fee2e2;
  color: #991b1b;
}

.badge-neutral {
  background: #e5e7eb;
  color: #374151;
}
```

---

## 🃏 **Card**

### **Props**
| Prop          | Type       | Default     | Description                     |
|---------------|------------|-------------|---------------------------------|
| `status`      | string     | `active`    | `active`, `warning`, `danger`, `paused` |

### **Code HTML**
```html
<div class="card">
  <div class="card-header active">
    <div>
      <div class="project-name">Nom du Projet</div>
      <div class="project-objective">Objectif du projet</div>
    </div>
    <span class="badge badge-success">Actif</span>
  </div>
  <div class="card-body">
    <!-- Contenu -->
    <div class="metric-row">
      <span class="metric-label">Métrique</span>
      <span class="metric-value">Valeur</span>
    </div>
  </div>
  <div class="card-footer">
    <!-- Pied de carte -->
  </div>
</div>
```

### **Code CSS**
```css
.card {
  background: white;
  border-radius: 0.75rem;
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px -1px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -4px rgba(0, 0, 0, 0.1);
}

.card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: linear-gradient(90deg, #6366f1, #10b981);
  transform: scaleX(0);
  transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.card:hover::before {
  transform: scaleX(1);
}

.card-header {
  padding: 1rem 1.5rem;
  border-bottom: 1px solid #e5e7eb;
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  background: #f9fafb;
}

.card-header.active { border-bottom-color: #10b981; }
.card-header.warning { border-bottom-color: #f59e0b; }
.card-header.danger { border-bottom-color: #ef4444; }
.card-header.paused { border-bottom-color: #9ca3af; }

.card-body {
  padding: 1.5rem;
}

.card-footer {
  padding: 0.75rem 1.5rem;
  background: #f9fafb;
  border-top: 1px solid #e5e7eb;
}
```

---

## ⚠️ **Alert**

### **Props**
| Prop          | Type       | Default     | Description                     |
|---------------|------------|-------------|---------------------------------|
| `variant`     | string     | `info`      | `info`, `warning`, `success`, `danger` |

### **Code HTML**
```html
<!-- Alerte info -->
<div class="alert alert-info">
  <h3>ℹ️ Titre de l'alerte</h3>
  <p>Description de l'alerte avec <strong>du texte en gras</strong>.</p>
  <ul>
    <li>Élément 1</li>
    <li>Élément 2</li>
  </ul>
</div>

<!-- Alerte warning -->
<div class="alert alert-warning">
  <h3>⚠️ Attention</h3>
  <p>Message d'avertissement.</p>
</div>
```

### **Code CSS**
```css
.alert {
  padding: 1rem 1.5rem;
  border-radius: 0.5rem;
  margin-bottom: 1.5rem;
  position: relative;
  overflow: hidden;
}

.alert::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 4px;
  height: 100%;
}

.alert-info {
  background: #eff6ff;
  border-left: 4px solid #3b82f6;
  color: #1e40af;
}

.alert-warning {
  background: #fef3c7;
  border-left-color: #f59e0b;
  color: #92400e;
}

.alert-success {
  background: #d1fae5;
  border-left-color: #10b981;
  color: #065f46;
}

.alert-danger {
  background: #fee2e2;
  border-left-color: #ef4444;
  color: #991b1b;
}

.alert h3 {
  margin-bottom: 0.5rem;
  font-size: 1rem;
}

.alert ul {
  margin-left: 1.25rem;
  padding-top: 0.5rem;
}

.alert li {
  margin-bottom: 0.25rem;
}
```

---

## 📊 **ProgressBar**

### **Code HTML**
```html
<div class="progress-container">
  <div class="progress-bar" style="width: 75%;"></div>
</div>
```

### **Code CSS**
```css
.progress-container {
  height: 6px;
  background: #e5e7eb;
  border-radius: 9999px;
  overflow: hidden;
  margin-top: 0.5rem;
}

.progress-bar {
  height: 100%;
  background: linear-gradient(90deg, #6366f1, #10b981);
  border-radius: 9999px;
  transition: width 0.6s ease-out;
}
```

---

## 💬 **Tooltip**

### **Props**
| Prop          | Type       | Default     | Description                     |
|---------------|------------|-------------|---------------------------------|
| `text`        | string     | -           | Texte de l’info-bulle (via `data-tooltip`) |
| `position`    | string     | `top`       | `top`, `bottom`, `left`, `right` |

### **Code HTML**
```html
<!-- Tooltip sur un bouton -->
<button class="btn btn-outline tooltip" data-tooltip="Exporter en PDF">
  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
    <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/>
  </svg>
  Exporter
</button>

<!-- Tooltip sur un span -->
<span class="tooltip" data-tooltip="Ceci est un tooltip">
  Survolez-moi
</span>
```

### **Code CSS**
```css
.tooltip {
  position: relative;
}

.tooltip::after {
  content: attr(data-tooltip);
  position: absolute;
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%);
  padding: 0.25rem 0.5rem;
  background: #111827;
  color: white;
  font-size: 0.75rem;
  border-radius: 0.375rem;
  white-space: nowrap;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.2s ease-out;
  margin-bottom: 0.5rem;
  z-index: 600;
}

.tooltip:hover::after {
  opacity: 1;
}
```

---

## 👤 **Avatar**

### **Props**
| Prop          | Type       | Default     | Description                     |
|---------------|------------|-------------|---------------------------------|
| `size`        | string     | `md`        | `sm`, `md`, `lg` |
| `src`         | string     | -           | URL de l’image (optionnel) |
| `initials`    | string     | -           | Initiales si pas d’image |

### **Code HTML**
```html
<!-- Avatar avec initiales -->
<div class="avatar">JD</div>

<!-- Avatar small -->
<div class="avatar avatar-sm">JD</div>

<!-- Avatar large -->
<div class="avatar avatar-lg">JD</div>
```

### **Code CSS**
```css
.avatar {
  width: 2.5rem;
  height: 2.5rem;
  border-radius: 9999px;
  background: #eef2ff;
  color: #4338ca;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 600;
  font-size: 0.875rem;
}

.avatar-sm { width: 2rem; height: 2rem; font-size: 0.75rem; }
.avatar-lg { width: 3.5rem; height: 3.5rem; font-size: 1.25rem; }
```

---

## 📄 **ProjectCard** (Spécifique au Portfolio)

### **Structure Complète**
```html
<div class="project-card">
  <div class="card-header active">
    <div>
      <div class="project-name">Nom du Projet</div>
      <div class="project-objective">Description de l'objectif</div>
    </div>
    <span class="badge badge-success">Actif</span>
  </div>
  <div class="card-body">
    <!-- Métriques -->
    <div class="metric-row">
      <span class="metric-label">Funnel Opportunité</span>
      <span class="metric-value">Arrêté — verdict trafic 0/695</span>
    </div>
    
    <!-- Blocages -->
    <div class="section-label">Blocages</div>
    <div class="blockers">
      <div class="blocker-item ok">✓ Aucun blocage technique</div>
      <div class="blocker-item">Problème à résoudre</div>
    </div>
    
    <!-- Actions -->
    <div class="section-label">Prochaines Actions</div>
    <div class="next-actions">
      <div class="action-item">Action 1</div>
      <div class="action-item">Action 2</div>
    </div>
    
    <!-- Freshness -->
    <div class="freshness-indicator fresh">✓ Mise à jour: 2026-09-19</div>
    
    <!-- Boutons -->
    <div class="grid grid-cols-2 mt-md">
      <button class="btn btn-outline btn-sm">Relancer</button>
      <button class="btn btn-primary btn-sm">Détails</button>
    </div>
  </div>
</div>
```

### **Code CSS Additionnel**
```css
.project-name {
  font-size: 1.125rem;
  font-weight: 700;
  color: #111827;
  margin-bottom: 0.25rem;
}

.project-objective {
  font-size: 0.875rem;
  color: #6b7280;
  line-height: 1.5;
}

.metric-row {
  margin-bottom: 1rem;
}

.metric-label {
  font-size: 0.75rem;
  font-weight: 600;
  color: #6b7280;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 0.25rem;
  display: block;
}

.metric-value {
  font-size: 0.875rem;
  color: #1f2937;
  line-height: 1.5;
}

.metric-value.zero {
  color: #ef4444;
  font-weight: 600;
}

.metric-value.success {
  color: #10b981;
  font-weight: 600;
}

.section-label {
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  color: #6b7280;
  letter-spacing: 0.05em;
  margin: 1.5rem 0 1rem;
  padding-top: 1rem;
  border-top: 1px solid #e5e7eb;
  position: relative;
}

.section-label::after {
  content: '';
  position: absolute;
  top: -1px;
  left: 0;
  width: 40px;
  height: 2px;
  background: linear-gradient(90deg, #6366f1, #10b981);
}

.blockers, .next-actions {
  font-size: 0.875rem;
  color: #374151;
  line-height: 1.7;
}

.blocker-item {
  margin-bottom: 0.75rem;
  padding-left: 1rem;
  border-left: 2px solid #ef4444;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.blocker-item:hover {
  background: #fee2e2;
  padding-left: 1.25rem;
}

.blocker-item.ok {
  border-left-color: #10b981;
  color: #047857;
}

.blocker-item.ok:hover {
  background: #d1fae5;
}

.action-item {
  margin-bottom: 0.5rem;
  padding-left: 1rem;
  border-left: 2px solid #3b82f6;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
}

.action-item:hover {
  background: #dbeafe;
  padding-left: 1.25rem;
}

.freshness-indicator {
  font-size: 0.75rem;
  margin-top: 1.5rem;
  padding-top: 1rem;
  border-top: 1px solid #e5e7eb;
  color: #6b7280;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.freshness-indicator.fresh {
  color: #047857;
}

.freshness-indicator.fresh::before {
  content: '✓';
  color: #10b981;
  font-weight: bold;
}

.freshness-indicator.stale {
  color: #ef4444;
}

.freshness-indicator.stale::before {
  content: '⚠';
  color: #ef4444;
  font-weight: bold;
}

/* Grid pour les boutons */
.grid {
  display: grid;
  gap: 0.75rem;
}

.grid-cols-1 { grid-template-columns: repeat(1, 1fr); }
.grid-cols-2 { grid-template-columns: repeat(2, 1fr); }
.grid-cols-3 { grid-template-columns: repeat(3, 1fr); }
.grid-cols-4 { grid-template-columns: repeat(4, 1fr); }

@media (max-width: 768px) {
  .grid-cols-2, .grid-cols-3, .grid-cols-4 {
    grid-template-columns: repeat(1, 1fr);
  }
}
```

---

## 📌 **Header**

### **Code HTML**
```html
<header class="header">
  <h1>Portfolio Report v2</h1>
  <div class="header-meta">
    <div class="meta-item">
      <span class="meta-label">Généré:</span>
      <span>2026-09-19</span>
    </div>
    <div class="meta-item">
      <span class="meta-label">Hub refresh:</span>
      <span id="hub-refresh">2026-09-19 12:43</span>
    </div>
    <div class="meta-item">
      <span class="meta-label">Projets Actifs:</span>
      <span>6 + 1 infrastructure</span>
    </div>
  </div>
  <div class="grid grid-cols-3 mt-lg">
    <button class="btn btn-primary">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M23 4v6h-6M1 20v-6h6"/>
      </svg>
      Rafraîchir
    </button>
    <button class="btn btn-outline">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/>
      </svg>
      Exporter
    </button>
    <button class="btn btn-secondary">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M12 5v14M5 12h14"/>
      </svg>
      Nouveau
    </button>
  </div>
</header>
```

### **Code CSS**
```css
.header {
  background: white;
  padding: 2rem;
  border-radius: 0.75rem;
  margin-bottom: 2rem;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -4px rgba(0, 0, 0, 0.1);
  position: relative;
  overflow: hidden;
}

.header::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, #6366f1, #10b981);
}

.header h1 {
  font-size: 2.25rem;
  margin-bottom: 0.5rem;
}

.header-meta {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem;
  margin-top: 1rem;
  font-size: 0.875rem;
  color: #6b7280;
}

.meta-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.meta-label {
  font-weight: 600;
  color: #4b5563;
}

@media (max-width: 768px) {
  .header {
    padding: 1.5rem;
  }
  
  .header h1 {
    font-size: 1.75rem;
  }
  
  .header-meta {
    flex-direction: column;
    gap: 0.75rem;
  }
  
  .grid-cols-3 {
    grid-template-columns: repeat(1, 1fr);
  }
}
```

---

## 👣 **Footer**

### **Code HTML**
```html
<footer class="footer">
  Généré par _metahub reporter (haiku) · Source: PROJECTS_OVERVIEW.md (2026-09-19 12:43) · 6 actifs + 1 infrastructure + 1 pause
</footer>
```

### **Code CSS**
```css
.footer {
  text-align: center;
  font-size: 0.75rem;
  color: #9ca3af;
  margin-top: 3rem;
  padding: 1.5rem;
}
```

---

## 🎯 **FAB (Floating Action Button)**

### **Code HTML**
```html
<button class="fab tooltip" data-tooltip="Nouveau Projet Rapide">
  <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
    <path d="M12 5v14M5 12h14"/>
  </svg>
</button>
```

### **Code CSS**
```css
.fab {
  position: fixed;
  bottom: 2rem;
  right: 2rem;
  width: 3.5rem;
  height: 3.5rem;
  border-radius: 9999px;
  background: linear-gradient(135deg, #6366f1, #4f46e5);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -4px rgba(0, 0, 0, 0.1);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  z-index: 1000;
}

.fab:hover {
  transform: scale(1.1);
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -6px rgba(0, 0, 0, 0.1);
}

@media (max-width: 768px) {
  .fab {
    bottom: 1.5rem;
    right: 1.5rem;
    width: 3rem;
    height: 3rem;
  }
}
```

---

## 📌 **Utilisation des Composants**

### **Exemple Complet : Carte de Projet**
```html
<div class="project-card">
  <div class="card-header active">
    <div>
      <div class="project-name">LiveGood-Profit-System</div>
      <div class="project-objective">OverPower Leads Magnet System via LeadsLeap Phase 1</div>
    </div>
    <span class="badge badge-success">Actif</span>
  </div>
  <div class="card-body">
    <div class="metric-row">
      <span class="metric-label">Revenu</span>
      <span class="metric-value zero">$0</span>
    </div>
    <div class="section-label">Blocages</div>
    <div class="blockers">
      <div class="blocker-item ok">✓ Aucun blocage technique</div>
    </div>
    <div class="section-label">Actions</div>
    <div class="next-actions">
      <div class="action-item">Explorer canal LeadsLeap différent</div>
    </div>
    <div class="freshness-indicator fresh">✓ Mise à jour: 2026-09-19</div>
    <div class="grid grid-cols-2 mt-md">
      <button class="btn btn-outline btn-sm tooltip" data-tooltip="Relancer">
        <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M5 12h14M12 5l7 7-7 7"/>
        </svg>
        Relancer
      </button>
      <button class="btn btn-primary btn-sm tooltip" data-tooltip="Détails">
        <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <circle cx="12" cy="12" r="10"/>
          <path d="M12 6v6l4 2"/>
        </svg>
        Détails
      </button>
    </div>
  </div>
</div>
```

---

## 🔧 **Intégration avec GSAP**

Pour ajouter des **animations avancées** (scroll-triggered, parallax, etc.), utilise le code GSAP inclus dans le `CANVAS.md`.

**Exemple d’animation GSAP** :
```javascript
// Animation de fadeIn + slideUp au scroll
gsap.from(".project-card", {
  scrollTrigger: {
    trigger: ".projects-grid",
    start: "top 80%",
    toggleActions: "play none none reverse"
  },
  y: 50,
  opacity: 0,
  duration: 1,
  stagger: 0.1
});
```

---

## 📚 **Documentation Complète**
- [Tokens (Couleurs, Typographie, etc.)](tokens.md)
- [Animations (GSAP, CSS, JS)](animations.md)
- [Guidelines (Règles d’usage)](guidelines.md)
