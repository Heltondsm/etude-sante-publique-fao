# 🌍 Sous-nutrition mondiale : analyse des données FAO

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=flat-square&logo=python&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-3776AB?style=flat-square&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-22c55e?style=flat-square)

528 millions de personnes sous-alimentées en 2017, alors que la production mondiale suffit à nourrir **94,3 % de la population**. 4 jeux de données de la FAO croisés pour arriver à une conclusion nette : **la faim est un problème de répartition, pas de quantité.**

---

## 📖 Le problème

La FAO veut comprendre les mécanismes de la sous-nutrition dans le monde, pour mieux orienter son action. La question centrale : **manque-t-on de nourriture, ou est-elle mal répartie ?**

---

## 🛠️ Ma solution

Un notebook Python qui croise 4 jeux de données de 2017 : population, disponibilité alimentaire, aide alimentaire et sous-nutrition. Pour chaque question, un calcul, un graphique et une conclusion.

---

## 🔍 Résultats clés

### 1️⃣ L'ampleur du problème

**7,01 % de la population mondiale en sous-nutrition, soit 528 millions de personnes.**

Les 3 pays les plus touchés en proportion : **Haïti, la Corée du Nord et Madagascar**, tous au-dessus de 40 %.

### 2️⃣ La production suffit à nourrir presque tout le monde

```python
# Calcul du nombre d'humains pouvant être nourris
total_dispo_kcal = df_pop_dispo_2017["dispo_kcal"].sum()
nb_possible_humains_nourris = (total_dispo_kcal / kcal_par_personne)
# Résultat : 7 115 300 894 personnes, soit 94,3 % de la population
```

Avec un besoin de 2 940 kcal par personne et par jour, la nourriture disponible en 2017 couvre **7,1 milliards de personnes**. Les seuls produits végétaux en couvriraient **5,87 milliards**, soit 78 %.

### 3️⃣ Une grande partie des céréales ne nourrit pas les humains

```python
aliments_animaux = df_cereales["Aliments pour animaux"].sum()
disponibilite = df_cereales["Disponibilité intérieure"].sum()
proportion_animaux = aliments_animaux / disponibilite * 100
# Résultat : 36 % des céréales disponibles vont à l'alimentation animale
```

**36 % des céréales** servent à nourrir les animaux, presque autant que la part destinée aux humains (43 %).

### 4️⃣ Produire beaucoup ne suffit pas à nourrir sa population

La **Thaïlande** produit 30,2 milliards de kg de manioc et en exporte **83 %**, alors que **8,67 %** de sa population est sous-alimentée.

### 5️⃣ L'aide alimentaire ne va pas aux pays de la faim chronique

Les pays qui reçoivent le plus d'aide (la Syrie, l'Éthiopie, le Yémen) n'ont **aucun point commun** avec le top 10 des pays les plus touchés par la sous-nutrition. L'aide répond aux crises et aux conflits, pas à la faim structurelle.

---

## 💡 Recommandations pour la FAO

1. **Orienter une partie de l'aide vers les pays en faim chronique**, comme Haïti, la Corée du Nord et Madagascar, en plus des zones de crise
2. **Encourager les pays exportateurs touchés par la sous-nutrition** à garder une part de leur production pour leur population
3. **Réduire la part des céréales destinées aux animaux** au profit de l'alimentation humaine
4. **Investir dans l'agriculture locale** et la réduction des pertes après récolte

---

## 🛠️ Technologies utilisées

- **Python** · **Pandas** : manipulation et analyse des données
- **Matplotlib** · **Seaborn** : graphiques
- **Jupyter Notebook**

---

## 📂 Structure du projet

```
.
├── README.md
├── analyse_sous_nutrition_mondiale.ipynb   # le notebook complet
└── data/                                    # données FAO 2017
    ├── population.csv
    ├── dispo_alimentaire.csv
    ├── aide_alimentaire.csv
    └── sous_nutrition.csv
```

---

## 🚀 Lancer le notebook

```bash
git clone https://github.com/Heltondsm/etude-sante-publique-fao.git
cd etude-sante-publique-fao
pip install pandas matplotlib seaborn jupyter
jupyter notebook analyse_sous_nutrition_mondiale.ipynb
```

---

## 📧 Contact

**Helton Dos Santos Moreira**
Data Analyst / Data Engineer | 10 ans d'expérience business (retail et e-commerce)

- 📧 Email : heltonmail8@gmail.com
- 💼 LinkedIn : [in/helton-dsm-data](https://linkedin.com/in/helton-dsm-data)
- 🐙 GitHub : [Heltondsm](https://github.com/Heltondsm)

---

## 🔗 Autres projets

- [Tableau de bord Power BI : portefeuille de projets](https://github.com/Heltondsm/powerbi-portefeuille-projets-rls), 104 projets dans 52 pays, sécurité au niveau des lignes sur 3 rôles, 25 mesures DAX
- [Audit données catalogue : e-commerce vins](https://github.com/Heltondsm/python-audit-donnees-catalogue), 3 sources réconciliées, 9 anomalies, 276 859 € de stock valorisé
- [Tendances du streaming musical](https://github.com/Heltondsm/analyse-streaming-musical), 114 000 morceaux, tests statistiques et calendrier de sortie

---

**Projet réalisé en mars 2026**
