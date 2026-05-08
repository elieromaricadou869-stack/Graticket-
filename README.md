# 🖤 GRATICKET – Application de Billetterie Mobile

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
Graticket un site et une app mobile a ta convenance et un style moderne,  luxe ,étudiant et professionnel pour les ivoiriens
