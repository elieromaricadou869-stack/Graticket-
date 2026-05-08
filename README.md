⁷# 🖤 GRATICKET – Application de Billetterie Mobile

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/Platform-iOS%20%7C%20Android-blue)](https://github.com)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

**Graticket** est une application mobile de billetterie premium destinée au marché ivoirien. Elle permet aux étudiants et professionnels d'acheter des billets pour des événements (galas, séminaires, afterworks) et de payer via **Wave, Orange Money et MTN MoMo**.

> ✨ "L'or de tes soirées t'attend."

---

## 📱 Aperçu de l'Application

| Écran | Description |
|-------|-------------|
| 🏠 **Accueil** | Fil d'actualité, recherche d'événements, catégories rapides |
| 🎟️ **Événements** | Liste filtrée par catégorie, date, ville et prix |
| 🧾 **Mes Billets** | Billets à venir avec QR code animé, billets passés |
| 👤 **Profil** | Informations personnelles, historique, mode étudiant/pro |
| 💳 **Paiement** | Paiement sécurisé via Wave, Orange Money, MTN MoMo |
| 🎫 **Scan QR** | Validation à l'entrée des événements (pour contrôleurs) |

---

## 🎨 Design System

### Palette de couleurs

| Usage | Couleur | Code Hex |
|-------|---------|----------|
| Fond principal | Noir absolu | `#0A0A0A` |
| Fond secondaire | Noir profond | `#1A1A1A` |
| Texte principal | Blanc cassé | `#F5F5F0` |
| Texte secondaire | Gris élégant | `#A0A0A0` |
| **Accent principal** | **Or métallique** | **`#D4AF37`** |
| Wave | Vert Wave | `#00A859` |
| Orange Money | Orange | `#FF6600` |
| MTN MoMo | Jaune | `#FFD100` |

### Typographie

- **Titres** (H1, H2, H3) : `Playfair Display` – Élégant, serif
- **Corps de texte** : `Inter` – Moderne, sans-serif, très lisible
- **Boutons** : `Inter Semi-Bold`

---

## ⚙️ Stack Technique Recommandée

### Frontend (Application Mobile)

| Technologie | Utilisation |
|-------------|-------------|
| **React Native** + **Expo** | Framework cross-platform (iOS & Android) |
| **React Navigation** | Navigation entre les écrans |
| **Redux Toolkit** | Gestion d'état globale |
| **Framer Motion** (via react-native-reanimated) | Animations fluides |
| **Tailwind CSS** (via NativeWind) | Stylisation rapide |

### Backend

| Technologie | Utilisation |
|-------------|-------------|
| **Node.js** + **Express** | API RESTful |
| **PostgreSQL** | Base de données principale |
| **Redis** | Cache et sessions |
| **Firebase Cloud Messaging** | Notifications push |

### Paiements

| Moyen de paiement | API | Documentation |
|-------------------|-----|---------------|
| 💚 **Wave** | Wave API | [wave.com/developers](https://wave.com/fr/developers) |
| 🔶 **Orange Money** | Orange Money API CI | [developer.orange.com](https://developer.orange.com) |
| 💛 **MTN MoMo** | MoMo API | [momoapi.mtn.com](https://momoapi.mtn.com) |

---

## 📂 Structure du Projet (Arborescence)
# Graticket-
Graticket un site et une app mobile a ta convenance et un style moderne,  luxe ,étudiant et professionnel pour les ivoiriens| Type | Police | Taille |
|------|--------|--------|
| Titres | Playfair Display (serif) | 32px (mobile) |
| Corps | Inter (sans-serif) | 16px |
| Petits textes | Inter | 14px |
| Boutons | Inter Semi-Bold | 16px |<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Graticket — L'accès au prestige, redéfini.</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500&family=Bebas+Neue&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  :root {
    --gold: #C9A84C;
    --gold-light: #E8C97A;
    --gold-dark: #8B6914;
    --black: #080808;
    --dark: #0F0F0F;
    --surface: #161616;
    --surface2: #1E1E1E;
    --border: rgba(201,168,76,0.18);
    --text: #F0EDE6;
    --muted: #8A8578;
    --white: #FAFAF8;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--black);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    position: fixed; width: 8px; height: 8px;
    background: var(--gold); border-radius: 50%;
    pointer-events: none; z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s, width 0.3s, height 0.3s, opacity 0.3s;
  }
  .cursor-ring {
    position: fixed; width: 36px; height: 36px;
    border: 1px solid var(--gold); border-radius: 50%;
    pointer-events: none; z-index: 9998;
    transform: translate(-50%, -50%);
    transition: transform 0.25s cubic-bezier(.23,1,.32,1), width 0.4s, height 0.4s;
    opacity: 0.5;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    padding: 0 60px;
    display: flex; align-items: center; justify-content: space-between;
    height: 72px;
    border-bottom: 1px solid rgba(201,168,76,0.08);
    backdrop-filter: blur(20px);
    background: rgba(8,8,8,0.7);
  }
  .nav-logo {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
    letter-spacing: 4px;
    background: linear-gradient(135deg, var(--gold-light), var(--gold), var(--gold-dark));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .nav-links { display: flex; gap: 40px; }
  .nav-links a {
    color: var(--muted); font-size: 13px; letter-spacing: 1.5px;
    text-transform: uppercase; text-decoration: none;
    transition: color 0.3s;
    font-weight: 400;
  }
  .nav-links a:hover { color: var(--gold); }
  .nav-cta {
    background: transparent;
    border: 1px solid var(--gold);
    color: var(--gold);
    padding: 10px 28px;
    font-family: 'DM Sans', sans-serif;
    font-size: 12px;
    letter-spacing: 2px;
    text-transform: uppercase;
    cursor: none;
    transition: all 0.3s;
  }
  .nav-cta:hover {
    background: var(--gold);
    color: var(--black);
  }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    position: relative; overflow: hidden;
    padding: 120px 60px 80px;
    text-align: center;
  }
  .hero-bg {
    position: absolute; inset: 0;
    background: radial-gradient(ellipse 80% 60% at 50% 40%, rgba(201,168,76,0.07) 0%, transparent 70%),
                radial-gradient(ellipse 40% 40% at 20% 80%, rgba(201,168,76,0.04) 0%, transparent 60%),
                radial-gradient(ellipse 40% 40% at 80% 20%, rgba(201,168,76,0.04) 0%, transparent 60%);
  }
  .hero-grid {
    position: absolute; inset: 0;
    background-image: linear-gradient(rgba(201,168,76,0.04) 1px, transparent 1px),
                      linear-gradient(90deg, rgba(201,168,76,0.04) 1px, transparent 1px);
    background-size: 80px 80px;
    mask-image: radial-gradient(ellipse 80% 80% at 50% 50%, black, transparent);
  }

  .hero-badge {
    display: inline-flex; align-items: center; gap: 10px;
    border: 1px solid var(--border);
    padding: 8px 20px; margin-bottom: 48px;
    font-size: 11px; letter-spacing: 3px; text-transform: uppercase;
    color: var(--gold); position: relative;
    animation: fadeUp 1s 0.2s both;
  }
  .hero-badge::before {
    content: ''; width: 6px; height: 6px;
    border-radius: 50%; background: var(--gold);
    animation: pulse 2s infinite;
  }
  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.3} }

  .hero h1 {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(64px, 9vw, 130px);
    font-weight: 300;
    line-height: 0.9;
    letter-spacing: -2px;
    margin-bottom: 16px;
    animation: fadeUp 1s 0.4s both;
  }
  .hero h1 em {
    font-style: italic;
    background: linear-gradient(135deg, var(--gold-light) 0%, var(--gold) 50%, var(--gold-dark) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .hero-sub {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(18px, 2.5vw, 28px);
    font-weight: 300;
    font-style: italic;
    color: var(--muted);
    margin-bottom: 48px;
    animation: fadeUp 1s 0.6s both;
  }

  .hero-actions {
    display: flex; gap: 16px; justify-content: center; flex-wrap: wrap;
    animation: fadeUp 1s 0.8s both;
  }
  .btn-primary {
    background: linear-gradient(135deg, var(--gold-light), var(--gold));
    color: var(--black);
    border: none;
    padding: 16px 48px;
    font-family: 'DM Sans', sans-serif;
    font-size: 13px;
    letter-spacing: 2px;
    text-transform: uppercase;
    cursor: none;
    font-weight: 500;
    transition: all 0.3s;
    clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%);
  }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 20px 60px rgba(201,168,76,0.3); }
  .btn-secondary {
    background: transparent;
    color: var(--text);
    border: 1px solid rgba(240,237,230,0.2);
    padding: 16px 48px;
    font-family: 'DM Sans', sans-serif;
    font-size: 13px;
    letter-spacing: 2px;
    text-transform: uppercase;
    cursor: none;
    transition: all 0.3s;
    clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%);
  }
  .btn-secondary:hover { border-color: var(--gold); color: var(--gold); }

  .hero-stats {
    display: flex; gap: 60px; margin-top: 80px; justify-content: center;
    animation: fadeUp 1s 1s both;
  }
  .stat { text-align: center; }
  .stat-num {
    font-family: 'Cormorant Garamond', serif;
    font-size: 40px; font-weight: 300;
    color: var(--gold-light);
    display: block;
  }
  .stat-label { font-size: 11px; letter-spacing: 2px; color: var(--muted); text-transform: uppercase; }

  /* SCROLLING TICKER */
  .ticker-wrap {
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    padding: 14px 0; overflow: hidden;
    background: var(--surface);
  }
  .ticker { display: flex; gap: 0; animation: ticker 30s linear infinite; white-space: nowrap; }
  .ticker-item {
    padding: 0 40px;
    font-size: 12px; letter-spacing: 3px; text-transform: uppercase;
    color: var(--muted);
    display: flex; align-items: center; gap: 16px;
  }
  .ticker-item span { color: var(--gold); }
  @keyframes ticker { from{transform:translateX(0)} to{transform:translateX(-50%)} }

  /* SECTION DEFAULTS */
  section { padding: 120px 60px; position: relative; }

  .section-label {
    font-size: 10px; letter-spacing: 4px; text-transform: uppercase;
    color: var(--gold); margin-bottom: 20px;
    display: flex; align-items: center; gap: 12px;
  }
  .section-label::before {
    content: ''; width: 24px; height: 1px; background: var(--gold);
  }

  /* FEATURES */
  .features { background: var(--dark); }
  .features-header { max-width: 700px; margin-bottom: 80px; }
  .features-header h2 {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(40px, 5vw, 68px);
    font-weight: 300;
    line-height: 1.05;
  }
  .features-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: var(--border);
  }
  .feature-card {
    background: var(--dark);
    padding: 48px 40px;
    transition: background 0.3s;
    position: relative; overflow: hidden;
  }
  .feature-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
    transform: translateX(-100%);
    transition: transform 0.6s;
  }
  .feature-card:hover::before { transform: translateX(0); }
  .feature-card:hover { background: var(--surface); }
  .feature-icon {
    width: 48px; height: 48px;
    border: 1px solid var(--border);
    display: flex; align-items: center; justify-content: center;
    margin-bottom: 28px;
    font-size: 20px;
  }
  .feature-card h3 {
    font-family: 'Cormorant Garamond', serif;
    font-size: 24px; font-weight: 400;
    margin-bottom: 12px;
  }
  .feature-card p { color: var(--muted); font-size: 14px; line-height: 1.7; }

  /* TICKETS SHOWCASE */
  .tickets-section { background: var(--black); }
  .tickets-header {
    display: flex; justify-content: space-between;
    align-items: flex-end; margin-bottom: 60px;
  }
  .tickets-header h2 {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(36px, 4vw, 60px);
    font-weight: 300;
  }
  .view-all {
    color: var(--gold); font-size: 12px; letter-spacing: 2px;
    text-transform: uppercase; cursor: none; border-bottom: 1px solid var(--gold);
    padding-bottom: 2px;
  }

  .tickets-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px; }

  .ticket-card {
    background: var(--surface);
    border: 1px solid var(--border);
    overflow: hidden;
    transition: transform 0.4s cubic-bezier(.23,1,.32,1), box-shadow 0.4s;
    position: relative;
  }
  .ticket-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 40px 80px rgba(0,0,0,0.6), 0 0 0 1px rgba(201,168,76,0.3);
  }
  .ticket-img {
    height: 200px;
    position: relative; overflow: hidden;
  }
  .ticket-img-bg {
    width: 100%; height: 100%;
    display: flex; align-items: center; justify-content: center;
    font-size: 60px;
    transition: transform 0.5s;
  }
  .ticket-card:hover .ticket-img-bg { transform: scale(1.08); }
  .ticket-category {
    position: absolute; top: 16px; right: 16px;
    background: rgba(8,8,8,0.8);
    border: 1px solid var(--border);
    padding: 4px 12px;
    font-size: 10px; letter-spacing: 2px; text-transform: uppercase;
    color: var(--gold);
  }

  .ticket-body { padding: 28px; }
  .ticket-body h3 {
    font-family: 'Cormorant Garamond', serif;
    font-size: 22px; font-weight: 400;
    margin-bottom: 8px;
  }
  .ticket-meta {
    display: flex; gap: 16px; margin-bottom: 20px;
    font-size: 12px; color: var(--muted); letter-spacing: 0.5px;
  }
  .ticket-divider {
    height: 1px;
    background: repeating-linear-gradient(90deg, var(--border) 0, var(--border) 8px, transparent 8px, transparent 14px);
    margin: 20px 0; position: relative;
  }
  .ticket-divider::before, .ticket-divider::after {
    content: ''; position: absolute; top: 50%; transform: translateY(-50%);
    width: 20px; height: 20px; border-radius: 50%;
    background: var(--black); border: 1px solid var(--border);
  }
  .ticket-divider::before { left: -12px; }
  .ticket-divider::after { right: -12px; }
  .ticket-footer { display: flex; justify-content: space-between; align-items: center; }
  .ticket-price {
    font-family: 'Cormorant Garamond', serif;
    font-size: 28px; color: var(--gold);
  }
  .ticket-price small { font-size: 13px; color: var(--muted); font-family: 'DM Sans', sans-serif; }
  .ticket-btn {
    background: transparent; border: 1px solid var(--gold);
    color: var(--gold); padding: 8px 20px;
    font-size: 11px; letter-spacing: 1.5px; text-transform: uppercase;
    cursor: none; transition: all 0.3s;
    font-family: 'DM Sans', sans-serif;
  }
  .ticket-btn:hover { background: var(--gold); color: var(--black); }

  /* MOBILE APP SECTION */
  .app-section {
    background: var(--surface);
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 80px; align-items: center;
  }
  .app-content h2 {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(36px, 4vw, 60px);
    font-weight: 300; line-height: 1.1;
    margin-bottom: 24px;
  }
  .app-content p { color: var(--muted); font-size: 15px; line-height: 1.8; margin-bottom: 40px; }
  .app-features { display: flex; flex-direction: column; gap: 20px; margin-bottom: 40px; }
  .app-feat {
    display: flex; align-items: flex-start; gap: 16px;
    padding: 20px; border: 1px solid var(--border);
    transition: border-color 0.3s;
  }
  .app-feat:hover { border-color: var(--gold); }
  .app-feat-icon { font-size: 22px; flex-shrink: 0; }
  .app-feat h4 { font-size: 14px; font-weight: 500; margin-bottom: 4px; }
  .app-feat p { font-size: 13px; color: var(--muted); line-height: 1.5; }
  .store-btns { display: flex; gap: 12px; }
  .store-btn {
    border: 1px solid var(--border);
    padding: 14px 24px;
    display: flex; align-items: center; gap: 12px;
    cursor: none; transition: border-color 0.3s;
  }
  .store-btn:hover { border-color: var(--gold); }
  .store-btn-icon { font-size: 24px; }
  .store-btn-text span { display: block; }
  .store-btn-text .s1 { font-size: 9px; letter-spacing: 1px; color: var(--muted); text-transform: uppercase; }
  .store-btn-text .s2 { font-size: 14px; font-weight: 500; }

  /* PHONE MOCKUP */
  .phone-mockup {
    display: flex; justify-content: center; align-items: center;
    position: relative;
  }
  .phone {
    width: 280px; height: 580px;
    background: var(--surface2);
    border-radius: 44px;
    border: 1.5px solid rgba(201,168,76,0.3);
    padding: 12px;
    position: relative;
    box-shadow: 0 60px 120px rgba(0,0,0,0.8),
                inset 0 0 0 1px rgba(255,255,255,0.03),
                0 0 60px rgba(201,168,76,0.06);
    animation: phoneFloat 4s ease-in-out infinite;
  }
  @keyframes phoneFloat {
    0%,100%{transform:translateY(0) rotate(-2deg)}
    50%{transform:translateY(-16px) rotate(-2deg)}
  }
  .phone-notch {
    position: absolute; top: 16px; left: 50%; transform: translateX(-50%);
    width: 90px; height: 28px;
    background: var(--dark);
    border-radius: 0 0 18px 18px;
    z-index: 2;
  }
  .phone-screen {
    background: var(--dark); border-radius: 34px;
    width: 100%; height: 100%;
    overflow: hidden;
    display: flex; flex-direction: column;
  }
  .ps-header {
    background: var(--surface); padding: 48px 18px 16px;
    border-bottom: 1px solid var(--border);
  }
  .ps-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 22px; letter-spacing: 3px;
    background: linear-gradient(135deg, var(--gold-light), var(--gold));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  }
  .ps-search {
    margin-top: 12px; background: var(--dark);
    border: 1px solid var(--border); border-radius: 8px;
    padding: 8px 12px; font-size: 10px; color: var(--muted);
    display: flex; align-items: center; gap: 8px;
  }
  .ps-body { flex: 1; padding: 16px; overflow: hidden; display: flex; flex-direction: column; gap: 10px; }
  .ps-section-label { font-size: 8px; letter-spacing: 2px; text-transform: uppercase; color: var(--gold); margin-top: 6px; }
  .ps-card {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 10px; overflow: hidden; display: flex; gap: 10px;
    padding: 10px;
  }
  .ps-card-img {
    width: 50px; height: 50px; border-radius: 6px;
    display: flex; align-items: center; justify-content: center; font-size: 22px;
    flex-shrink: 0;
  }
  .ps-card-title { font-size: 10px; font-weight: 500; margin-bottom: 3px; }
  .ps-card-meta { font-size: 8px; color: var(--muted); }
  .ps-card-price { font-size: 9px; color: var(--gold); margin-top: 4px; }
  .ps-nav {
    background: var(--surface); padding: 12px 20px;
    border-top: 1px solid var(--border);
    display: flex; justify-content: space-around;
    font-size: 18px;
  }

  /* STUDENTS */
  .students-section { background: var(--black); }
  .students-grid { display: grid; grid-template-columns: 1fr 2fr; gap: 80px; align-items: start; }
  .students-text h2 {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(36px, 4vw, 60px);
    font-weight: 300; line-height: 1.1;
    margin-bottom: 24px;
  }
  .students-text p { color: var(--muted); font-size: 15px; line-height: 1.8; }
  .perks-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 2px; background: var(--border); }
  .perk {
    background: var(--dark); padding: 36px 32px;
    transition: background 0.3s;
  }
  .perk:hover { background: var(--surface); }
  .perk-num {
    font-family: 'Cormorant Garamond', serif;
    font-size: 52px; font-weight: 300;
    color: rgba(201,168,76,0.15);
    line-height: 1; margin-bottom: 12px;
  }
  .perk h4 { font-size: 15px; font-weight: 400; margin-bottom: 8px; }
  .perk p { font-size: 13px; color: var(--muted); line-height: 1.6; }

  /* CTA SECTION */
  .cta-section {
    background: var(--surface);
    text-align: center;
    padding: 140px 60px;
    position: relative; overflow: hidden;
  }
  .cta-section::before {
    content: 'GRATICKET';
    font-family: 'Bebas Neue', sans-serif;
    font-size: 20vw;
    position: absolute; top: 50%; left: 50%; transform: translate(-50%,-50%);
    color: rgba(201,168,76,0.025);
    letter-spacing: 8px;
    white-space: nowrap;
    pointer-events: none;
  }
  .cta-section h2 {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(40px, 6vw, 90px);
    font-weight: 300; line-height: 1;
    margin-bottom: 24px; position: relative;
  }
  .cta-section p {
    color: var(--muted); font-size: 16px; max-width: 560px;
    margin: 0 auto 48px; line-height: 1.7; position: relative;
  }
  .cta-actions { display: flex; gap: 16px; justify-content: center; position: relative; }

  /* FOOTER */
  footer {
    background: var(--dark);
    border-top: 1px solid var(--border);
    padding: 60px;
  }
  .footer-grid {
    display: grid; grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 60px; margin-bottom: 60px;
  }
  .footer-brand .nav-logo { display: block; margin-bottom: 16px; }
  .footer-brand p { color: var(--muted); font-size: 13px; line-height: 1.7; max-width: 280px; }
  .footer-col h5 {
    font-size: 10px; letter-spacing: 3px; text-transform: uppercase;
    color: var(--gold); margin-bottom: 20px;
  }
  .footer-col a {
    display: block; color: var(--muted); font-size: 13px;
    text-decoration: none; margin-bottom: 12px; transition: color 0.3s;
  }
  .footer-col a:hover { color: var(--text); }
  .footer-bottom {
    padding-top: 32px; border-top: 1px solid rgba(201,168,76,0.08);
    display: flex; justify-content: space-between; align-items: center;
  }
  .footer-bottom p { font-size: 12px; color: var(--muted); }
  .footer-social { display: flex; gap: 16px; }
  .social-link {
    width: 36px; height: 36px;
    border: 1px solid var(--border);
    display: flex; align-items: center; justify-content: center;
    color: var(--muted); text-decoration: none; font-size: 14px;
    transition: all 0.3s; cursor: none;
  }
  .social-link:hover { border-color: var(--gold); color: var(--gold); }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* Responsive basic */
  @media(max-width: 1024px) {
    nav { padding: 0 32px; }
    .nav-links { display: none; }
    section { padding: 80px 32px; }
    .features-grid, .tickets-grid { grid-template-columns: 1fr; }
    .app-section { grid-template-columns: 1fr; }
    .students-grid { grid-template-columns: 1fr; }
    .footer-grid { grid-template-columns: 1fr 1fr; }
    .tickets-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo">Graticket</div>
  <div class="nav-links">
    <a href="#">Événements</a>
    <a href="#">Étudiants</a>
    <a href="#">Pro</a>
    <a href="#">À propos</a>
  </div>
  <button class="nav-cta">Rejoindre</button>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-grid"></div>

  <div class="hero-badge">
    <span>Nouveau · Saison 2025</span>
  </div>

  <h1>L'accès au<br><em>prestige,</em><br>redéfini.</h1>
  <p class="hero-sub">Événements exclusifs pour étudiants & professionnels ambitieux.</p>

  <div class="hero-actions">
    <button class="btn-primary">Découvrir les tickets</button>
    <button class="btn-secondary">Voir l'app ↓</button>
  </div>

  <div class="hero-stats">
    <div class="stat">
      <span class="stat-num">84K+</span>
      <span class="stat-label">Membres actifs</span>
    </div>
    <div class="stat">
      <span class="stat-num">1,200</span>
      <span class="stat-label">Événements / mois</span>
    </div>
    <div class="stat">
      <span class="stat-num">−70%</span>
      <span class="stat-label">Sur le prix public</span>
    </div>
  </div>
</section>

<!-- TICKER -->
<div class="ticker-wrap">
  <div class="ticker">
    <span class="ticker-item">Concerts <span>✦</span></span>
    <span class="ticker-item">Conférences <span>✦</span></span>
    <span class="ticker-item">Galas & Soirées <span>✦</span></span>
    <span class="ticker-item">Expositions <span>✦</span></span>
    <span class="ticker-item">Networking Pro <span>✦</span></span>
    <span class="ticker-item">Forums Étudiants <span>✦</span></span>
    <span class="ticker-item">Spectacles <span>✦</span></span>
    <span class="ticker-item">Concerts <span>✦</span></span>
    <span class="ticker-item">Conférences <span>✦</span></span>
    <span class="ticker-item">Galas & Soirées <span>✦</span></span>
    <span class="ticker-item">Expositions <span>✦</span></span>
    <span class="ticker-item">Networking Pro <span>✦</span></span>
    <span class="ticker-item">Forums Étudiants <span>✦</span></span>
    <span class="ticker-item">Spectacles <span>✦</span></span>
  </div>
</div>

<!-- FEATURES -->
<section class="features">
  <div class="features-header">
    <div class="section-label">Pourquoi Graticket</div>
    <h2>Une plateforme<br>taillée pour <em style="font-family:'Cormorant Garamond';font-style:italic;color:var(--gold)">l'excellence.</em></h2>
  </div>
  <div class="features-grid">
    <div class="feature-card">
      <div class="feature-icon">🎫</div>
      <h3>Tickets vérifiés</h3>
      <p>Chaque billet est authentifié par notre système blockchain. Zéro risque de fraude, 100% de sécurité pour votre entrée.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">⚡</div>
      <h3>Accès prioritaire</h3>
      <p>Les membres Graticket accèdent aux pré-ventes 48h avant le grand public. Les meilleures places, toujours.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">🎓</div>
      <h3>Tarifs étudiants</h3>
      <p>Jusqu'à 70% de réduction sur présentation de votre statut étudiant. Vérification instantanée via votre adresse académique.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">💼</div>
      <h3>Espace Pro</h3>
      <p>Conférences, forums et événements B2B réservés aux professionnels vérifiés. Élargissez votre réseau au niveau supérieur.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">🌍</div>
      <h3>Couverture nationale</h3>
      <p>Plus de 50 villes en France, Belgique, Suisse et Maroc. Votre accès culturel, partout où vous vous trouvez.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">✨</div>
      <h3>Expérience premium</h3>
      <p>Interface épurée, wallet intégré, historique complet. La sophistication au service de votre vie culturelle.</p>
    </div>
  </div>
</section>

<!-- TICKETS SHOWCASE -->
<section class="tickets-section">
  <div class="tickets-header">
    <div>
      <div class="section-label">Événements à la une</div>
      <h2>Sélection<br><em style="font-family:'Cormorant Garamond';font-style:italic">du moment</em></h2>
    </div>
    <span class="view-all">Voir tout →</span>
  </div>
  <div class="tickets-grid">
    <div class="ticket-card">
      <div class="ticket-img">
        <div class="ticket-img-bg" style="background:linear-gradient(135deg,#1a0a2e,#2d1b5e)">🎵</div>
        <span class="ticket-category">Concert</span>
      </div>
      <div class="ticket-body">
        <h3>Jazz au Grand Palais</h3>
        <div class="ticket-meta">
          <span>📅 14 Juin 2025</span>
          <span>📍 Paris</span>
        </div>
        <div class="ticket-divider"></div>
        <div class="ticket-footer">
          <div class="ticket-price">12€ <small>étudiant</small></div>
          <button class="ticket-btn">Réserver</button>
        </div>
      </div>
    </div>
    <div class="ticket-card">
      <div class="ticket-img">
        <div class="ticket-img-bg" style="background:linear-gradient(135deg,#0a1a0a,#1a3a1a)">💼</div>
        <span class="ticket-category">Forum Pro</span>
      </div>
      <div class="ticket-body">
        <h3>Tech Leaders Summit</h3>
        <div class="ticket-meta">
          <span>📅 21 Juin 2025</span>
          <span>📍 Lyon</span>
        </div>
        <div class="ticket-divider"></div>
        <div class="ticket-footer">
          <div class="ticket-price">Gratuit <small>pro vérifié</small></div>
          <button class="ticket-btn">Rejoindre</button>
        </div>
      </div>
    </div>
    <div class="ticket-card">
      <div class="ticket-img">
        <div class="ticket-img-bg" style="background:linear-gradient(135deg,#1a0f00,#3a2000)">🎭</div>
        <span class="ticket-category">Spectacle</span>
      </div>
      <div class="ticket-body">
        <h3>Opéra Moderne — ARIA</h3>
        <div class="ticket-meta">
          <span>📅 28 Juin 2025</span>
          <span>📍 Bordeaux</span>
        </div>
        <div class="ticket-divider"></div>
        <div class="ticket-footer">
          <div class="ticket-price">8€ <small>étudiant</small></div>
          <button class="ticket-btn">Réserver</button>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- APP SECTION -->
<section class="app-section">
  <div class="app-content">
    <div class="section-label">Application mobile</div>
    <h2>Votre vie<br>culturelle,<br><em style="font-family:'Cormorant Garamond';font-style:italic;color:var(--gold)">dans votre poche.</em></h2>
    <p>Graticket sur mobile, c'est toute la puissance de la plateforme avec la fluidité d'un outil pensé pour votre rythme de vie — étudiant ou professionnel.</p>
    <div class="app-features">
      <div class="app-feat">
        <div class="app-feat-icon">🔔</div>
        <div>
          <h4>Alertes personnalisées</h4>
          <p>Recevez des notifications pour les événements qui correspondent à vos centres d'intérêt, avant sold-out.</p>
        </div>
      </div>
      <div class="app-feat">
        <div class="app-feat-icon">🎟️</div>
        <div>
          <h4>Wallet de tickets</h4>
          <p>Tous vos billets centralisés, accessibles hors-ligne. QR Code dynamique anti-falsification.</p>
        </div>
      </div>
      <div class="app-feat">
        <div class="app-feat-icon">🤝</div>
        <div>
          <h4>Mode groupe</h4>
          <p>Réservez à plusieurs en un clic, partagez les billets et coordonnez-vous facilement.</p>
        </div>
      </div>
    </div>
    <div class="store-btns">
      <div class="store-btn">
        <div class="store-btn-icon">🍎</div>
        <div class="store-btn-text">
          <span class="s1">Télécharger sur</span>
          <span class="s2">App Store</span>
        </div>
      </div>
      <div class="store-btn">
        <div class="store-btn-icon">▶</div>
        <div class="store-btn-text">
          <span class="s1">Disponible sur</span>
          <span class="s2">Google Play</span>
        </div>
      </div>
    </div>
  </div>

  <!-- PHONE MOCKUP -->
  <div class="phone-mockup">
    <div class="phone">
      <div class="phone-notch"></div>
      <div class="phone-screen">
        <div class="ps-header">
          <div class="ps-title">GRATICKET</div>
          <div class="ps-search">🔍 &nbsp;Rechercher un événement…</div>
        </div>
        <div class="ps-body">
          <div class="ps-section-label">✦ Pour vous ce soir</div>
          <div class="ps-card">
            <div class="ps-card-img" style="background:linear-gradient(135deg,#1a0a2e,#2d1b5e)">🎵</div>
            <div>
              <div class="ps-card-title">Jazz au Grand Palais</div>
              <div class="ps-card-meta">📅 Ce soir · Paris 8e</div>
              <div class="ps-card-price">12€ étudiant</div>
            </div>
          </div>
          <div class="ps-card">
            <div class="ps-card-img" style="background:linear-gradient(135deg,#0a1a0a,#1a3a1a)">💼</div>
            <div>
              <div class="ps-card-title">Tech Leaders Summit</div>
              <div class="ps-card-meta">📅 Demain · Lyon</div>
              <div class="ps-card-price">Gratuit · Pro</div>
            </div>
          </div>
          <div class="ps-section-label">✦ Tendances</div>
          <div class="ps-card">
            <div class="ps-card-img" style="background:linear-gradient(135deg,#1a0f00,#3a2000)">🎭</div>
            <div>
              <div class="ps-card-title">ARIA — Opéra Moderne</div>
              <div class="ps-card-meta">📅 28 Juin · Bordeaux</div>
              <div class="ps-card-price">8€ étudiant</div>
            </div>
          </div>
        </div>
        <div class="ps-nav">
          <span title="Accueil">🏠</span>
          <span title="Chercher">🔍</span>
          <span title="Tickets" style="color:var(--gold)">🎫</span>
          <span title="Profil">👤</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- STUDENTS PERKS -->
<section class="students-section">
  <div class="students-grid">
    <div class="students-text">
      <div class="section-label">Programme Étudiant</div>
      <h2>Conçu pour<br><em style="font-family:'Cormorant Garamond';font-style:italic;color:var(--gold)">votre génération.</em></h2>
      <p>Nous croyons que l'accès à la culture, au réseau et aux opportunités ne devrait pas être réservé à une élite fortunée. Graticket démocratise le prestige.</p>
    </div>
    <div class="perks-grid">
      <div class="perk">
        <div class="perk-num">01</div>
        <h4>Vérification instantanée</h4>
        <p>Votre statut étudiant activé en 60 secondes via votre email académique ou carte étudiante.</p>
      </div>
      <div class="perk">
        <div class="perk-num">02</div>
        <h4>Jusqu'à −70%</h4>
        <p>Tarifs préférentiels sur plus de 5 000 événements partenaires. Culture accessible, sans compromis.</p>
      </div>
      <div class="perk">
        <div class="perk-num">03</div>
        <h4>Réseau pro inclus</h4>
        <p>Accès gratuit aux événements networking pour préparer votre entrée dans la vie professionnelle.</p>
      </div>
      <div class="perk">
        <div class="perk-num">04</div>
        <h4>Cashback sur chaque ticket</h4>
        <p>Cumulez des points à chaque achat, échangeables contre des billets gratuits ou des expériences VIP.</p>
      </div>
    </div>
  </div>
</section>

<!-- CTA -->
<section class="cta-section">
  <h2>Prêt à vivre<br><em style="font-family:'Cormorant Garamond';font-style:italic;color:var(--gold)">l'extraordinaire ?</em></h2>
  <p>Rejoignez 84 000 membres qui vivent déjà la culture autrement. Inscription gratuite, accès immédiat.</p>
  <div class="cta-actions">
    <button class="btn-primary">Créer mon compte</button>
    <button class="btn-secondary">Télécharger l'app</button>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-grid">
    <div class="footer-brand">
      <div class="nav-logo">Graticket</div>
      <p>La plateforme qui rend le prestige accessible à tous les esprits curieux et ambitieux.</p>
    </div>
    <div class="footer-col">
      <h5>Plateforme</h5>
      <a href="#">Événements</a>
      <a href="#">Billets</a>
      <a href="#">Application</a>
      <a href="#">Partenaires</a>
    </div>
    <div class="footer-col">
      <h5>Programmes</h5>
      <a href="#">Étudiants</a>
      <a href="#">Professionnels</a>
      <a href="#">Organisateurs</a>
      <a href="#">Ambassadeurs</a>
    </div>
    <div class="footer-col">
      <h5>Légal</h5>
      <a href="#">CGU</a>
      <a href="#">Confidentialité</a>
      <a href="#">Cookies</a>
      <a href="#">Contact</a>
    </div>
  </div>
  <div class="footer-bottom">
    <p>© 2025 Graticket. Tous droits réservés.</p>
    <div class="footer-social">
      <a class="social-link" href="#">𝕏</a>
      <a class="social-link" href="#">in</a>
      <a class="social-link" href="#">ig</a>
      <a class="social-link" href="#">tt</a>
    </div>
  </div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;

  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px';
    cursor.style.top = my + 'px';
  });

  function animRing() {
    rx += (mx - rx) * 0.12;
    ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px';
    ring.style.top = ry + 'px';
    requestAnimationFrame(animRing);
  }
  animRing();

  document.querySelectorAll('a, button, .ticket-card, .feature-card, .perk, .app-feat, .store-btn').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.transform = 'translate(-50%,-50%) scale(2.5)';
      ring.style.width = '60px'; ring.style.height = '60px';
      ring.style.opacity = '0.8';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.transform = 'translate(-50%,-50%) scale(1)';
      ring.style.width = '36px'; ring.style.height = '36px';
      ring.style.opacity = '0.5';
    });
  });

  // Intersection Observer for fade-in
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.style.opacity = '1';
        e.target.style.transform = 'translateY(0)';
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.feature-card, .ticket-card, .perk, .app-feat').forEach(el => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(20px)';
    el.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
    observer.observe(el);
  });
</script>
</body>
</html>
| Usage | Code Hex | Nom |
|-------|----------|-----|
| Fond principal | `#0A0A0A` | Noir absolu |
| Fond secondaire | `#1A1A1A` | Noir profond |
| Texte principal | `#F5F5F0` | Blanc cassé |
| Texte secondaire | `#A0A0A0` | Gris élégant |
| **Or principal** | `#D4AF37` | Or métallique |
| Orange Money | `#FF6600` | Orange |
| MTN MoMo | `#FFD100` | Jaune |
| Wave | `#00A859` | Vert Wave |
| Succès | `#2ECC71` | Vert |
| Erreur | `#E74C3C` | Rouge || Onglet | Icône | Écrans |
|--------|-------|--------|
| **Accueil** | 🏠 | Fil d'actualité, recherche, catégories |
| **Événements** | 🎟️ | Liste filtrée, carte géolocalisée |
| **Mes Billets** | 🧾 | Billets à venir + passés + QR code |
| **Profil** | 👤 | Infos, historique, paramètres, déconnexion |# 🖤 GRATICKET – Application de Billetterie Mobile

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/Platform-iOS%20%7C%20Android-blue)](https://github.com)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

**Graticket** est une application mobile de billetterie premium destinée au marché ivoirien. Elle permet aux étudiants et professionnels d'acheter des billets pour des événements (galas, séminaires, afterworks) et de payer via **Wave, Orange Money et MTN MoMo**.

> ✨ "L'or de tes soirées t'attend."

---

## 📱 Aperçu de l'Application

| Écran | Description |
|-------|-------------|
| 🏠 **Accueil** | Fil d'actualité, recherche d'événements, catégories rapides |
| 🎟️ **Événements** | Liste filtrée par catégorie, date, ville et prix |
| 🧾 **Mes Billets** | Billets à venir avec QR code animé, billets passés |
| 👤 **Profil** | Informations personnelles, historique, mode étudiant/pro |
| 💳 **Paiement** | Paiement sécurisé via Wave, Orange Money, MTN MoMo |
| 🎫 **Scan QR** | Validation à l'entrée des événements (pour contrôleurs) |

---

## 🎨 Design System

### Palette de couleurs

| Usage | Couleur | Code Hex |
|-------|---------|----------|
| Fond principal | Noir absolu | `#0A0A0A` |
| Fond secondaire | Noir profond | `#1A1A1A` |
| Texte principal | Blanc cassé | `#F5F5F0` |
| Texte secondaire | Gris élégant | `#A0A0A0` |
| **Accent principal** | **Or métallique** | **`#D4AF37`** |
| Wave | Vert Wave | `#00A859` |
| Orange Money | Orange | `#FF6600` |
| MTN MoMo | Jaune | `#FFD100` |

### Typographie

- **Titres** (H1, H2, H3) : `Playfair Display` – Élégant, serif
- **Corps de texte** : `Inter` – Moderne, sans-serif, très lisible
- **Boutons** : `Inter Semi-Bold`

---

## ⚙️ Stack Technique Recommandée

### Frontend (Application Mobile)

| Technologie | Utilisation |
|-------------|-------------|
| **React Native** + **Expo** | Framework cross-platform (iOS & Android) |
| **React Navigation** | Navigation entre les écrans |
| **Redux Toolkit** | Gestion d'état globale |
| **Framer Motion** (via react-native-reanimated) | Animations fluides |
| **Tailwind CSS** (via NativeWind) | Stylisation rapide |

### Backend

| Technologie | Utilisation |
|-------------|-------------|
| **Node.js** + **Express** | API RESTful |
| **PostgreSQL** | Base de données principale |
| **Redis** | Cache et sessions |
| **Firebase Cloud Messaging** | Notifications push |

### Paiements

| Moyen de paiement | API | Documentation |
|-------------------|-----|---------------|
| 💚 **Wave** | Wave API | [wave.com/developers](https://wave.com/fr/developers) |
| 🔶 **Orange Money** | Orange Money API CI | [developer.orange.com](https://developer.orange.com) |
| 💛 **MTN MoMo** | MoMo API | [momoapi.mtn.com](https://momoapi.mtn.com) |

---

## 📂 Structure du Projet (Arborescence)
Écrans principaux
1. Accueil  
   - Logo doré “GRATICKET” sur fond noir.  
   - Barre de recherche d’événements.  
   - Cartes interactives (Gala Étudiant, Séminaire Pro, Afterwork).  
   - Navigation en bas : Accueil | Événements | Mes Billets | Profil.  

2. Billetterie  
   - Détails de l’événement (date, lieu, image premium).  
   - Choix des tickets : Standard, Étudiant (tarif réduit), VIP (accès champagne & espace privé).  
   - Bouton doré “Continuer” avec total affiché.  

3. Mes Billets  
   - Liste des billets achetés.  
   - QR codes dynamiques pour l’entrée.  
   - Historique des événements passés.  
   - Notifications pour les événements à venir.  

4. Tableau de bord organisateur  
   - Statistiques en temps réel (billets vendus, revenus).  
   - Graphiques dorés élégants.  
   - Gestion des événements (ajout, modification, suppression).  
   - Export des données (PDF, Excel).  

5. Profil utilisateur  
   - Informations personnelles.  
   - Historique des achats.  
   - Paramètres (mode étudiant/professionnel).  

