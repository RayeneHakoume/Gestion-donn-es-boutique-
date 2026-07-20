# Gestion-donn-es-boutique-
Une gestion des données d'une boutique 
Voici une proposition de fichier **README.md** complet, structuré et professionnel pour ce troisième projet stratégique (**BottleNeck**), axé sur le nettoyage de données, le rapprochement de systèmes (ERP/Web) et l'analyse de la performance des ventes de vins.

---

# 📝 README.md

# Projet BottleNeck — Rapprochement ERP/Web & Analyse de la Performance des Ventes de Vins

## 📌 Présentation du Projet

**BottleNeck** est un marchand de vin prestigieux qui fait face à des défis de croissance opérationnelle. Actuellement, la gestion des stocks et l'analyse des ventes reposent sur des outils artisanaux et des systèmes silotés.

Sous la direction de Nicolas, responsable des ventes, ce projet a pour but de **fusionner les données de l'ERP logistique et de la plateforme e-commerce (WordPress/WooCommerce)**. Cette unification permettra de dresser un panorama fiable de la santé financière de l'entreprise, d'identifier les anomalies de tarification et de présenter des indicateurs clés de performance (KPI) au Comité de Direction (CODIR).

---

## 🎯 Objectifs de la Mission

### Phase 1 : Data Cleaning & Rapprochement des Systèmes

* **Jointure des bases :** Unifier l'extraction ERP et l'extraction Web en utilisant une table de liaison (le *SKU* du site web ne correspondant pas aux *références produits* de l'ERP).
* **Audit Qualité & Data Cleaning :** Détecter au moins **8 types d'erreurs** (erreurs de saisie, de types de données, de calculs, de doublons, lignes vides, etc.).
* **Gouvernance & RGPD :** Formaliser le processus de nettoyage, justifier la conformité RGPD (absence de données clients sensibles, données purement transactionnelles et produits) et proposer des solutions d'automatisation pour assainir les futurs flux de données.

### Phase 2 : Analyses Statistiques & Business Intelligence pour le CODIR

* **Analyse du Chiffre d'Affaires (CA) :** Calculer le CA par produit ainsi que le CA global généré sur le mois d'octobre.
* **Analyse des Ventes :** Identifier les tops références et appliquer la **loi de Pareto (20/80)** pour isoler les produits moteurs du catalogue.
* **Gestion des Stocks & Logistique :** Analyser l'état des stocks, la rotation des stocks, les taux de marge et le nombre de mois de stock restants.
* **Détection des valeurs aberrantes (Outliers) :** Utiliser des méthodes statistiques comme le **Z-Score** ou l'**Écart Interquartile (IQR)** avec une représentation par *Boxplot* pour repérer d'éventuelles anomalies de prix.
* **Analyse de Corrélation :** Étudier les relations mathématiques entre les variables quantitatives (Prix, Quantités vendues, Stock, Taux de marge).

---

## 📁 Structure des Données

Le projet utilise trois fichiers d'extractions de données arrêtés au **31 octobre** (les ventes couvrant la période du 1er au 31 octobre) :

* `erp.csv` : Références produits, prix de vente HT, prix d'achat, statut et état du stock physique.
* `web.csv` : SKU (Stock Keeping Unit), volumes vendus, noms et descriptions des bouteilles en ligne.
* `liaison.csv` : Table de correspondance entre la `référence ERP` et le `SKU Web`, mise à jour par le stagiaire.

---

## 🛠️ Stack Technique

* **Langage :** **Python** (choisi pour la flexibilité de son écosystème Data).
* **Manipulation de Données :** `Pandas`, `NumPy`.
* **Statistiques & Dataviz :** `Matplotlib`, `Seaborn` (pour les Boxplots et les matrices de corrélation).
* **Environnement :** Jupyter Notebook.

---

## 🔬 Méthodologie Statistique Appliquée

Pour la détection des prix potentiellement erronés ou atypiques (grands crus), la méthode de l'**Écart Interquartile (IQR)** a été privilégiée :

$$IQR = Q_3 - Q_1$$

Tout produit dont le prix se situe au-delà de la barrière supérieure suivante est isolé comme *outlier* :

$$\text{Seuil Supérieur} = Q_3 + (1.5 \times IQR)$$

> **Note Business :** Un prix identifié comme "valeur aberrante statistique" n'est pas nécessairement une erreur de saisie. Dans le domaine du vin, cela correspond souvent à des bouteilles de prestige (Grands Crus). Le rapport fait explicitement la distinction entre une anomalie de prix et une valeur atypique légitime.

---

## 🚀 Plan d'Action du Notebook

1. **Exploration Initiale :** Analyse de la forme des fichiers, décompte des valeurs manquantes (`NaN`) et des doublons.
2. **Rapprochement :** Jointure progressive (`merge`) des trois fichiers et isolation des lignes sans correspondance (erreurs de jointure).
3. **Nettoyage & Correction :** Traitement des 8 types d'erreurs identifiées et conversion des types.
4. **Calcul des Métriques & Analyse :** Génération des tableaux de CA, application de Pareto, et calcul des indicateurs de rotation des stocks.
5. **Analyse Graphique :** Génération du Boxplot des prix et de la Heatmap de corrélation.

---

## 👥 Équipe Projet

* **Nicolas** : Responsable Ventes (Porteur du projet, validation des KPI commerciaux).
* **Le Comité de Direction (CODIR)** : Destinataire final de la présentation stratégique.
* **Le Stagiaire** : Chargé de la mise à jour initiale de la table de liaison.
* **Vous** : Data Analyst en charge du nettoyage, de la fusion des systèmes et de l'analyse statistique exploratoire.
