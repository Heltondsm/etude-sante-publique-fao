# 🌍 Sous-nutrition mondiale — Analyse des données FAO

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=flat-square&logo=python&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-3776AB?style=flat-square&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-22c55e?style=flat-square)

528 millions de personnes sous-alimentées en 2017. Le monde produit pourtant assez pour 94% de la population. 4 datasets FAO, 11 analyses, une conclusion nette : **le problème n'est pas la quantité produite — c'est la distribution.**

---

## 📖 Contexte

Mission d'analyse pour la FAO (Organisation des Nations Unies pour l'Alimentation et l'Agriculture). L'objectif : comprendre les mécanismes de la sous-nutrition mondiale à partir des données de production, disponibilité alimentaire et aide internationale.

**La question :** Est-ce qu'on manque de nourriture, ou est-ce un problème de répartition ?

---

## 🎯 Objectif de l'analyse

Analyser les données FAO 2017 pour :
- Identifier les pays les plus touchés par la sous-nutrition
- Calculer si la production mondiale est suffisante
- Comprendre où passe réellement la nourriture produite
- Évaluer l'efficacité de l'aide alimentaire internationale
- Formuler des recommandations actionnables

---

## 🔍 Résultats clés

### 1️⃣ L'ampleur du problème

**7,01% de la population mondiale en sous-nutrition = 528 millions de personnes**

Top 3 des pays les plus touchés :
- 🇭🇹 **Haïti** : 47,4%
- 🇰🇵 **Corée du Nord** : 45,6%
- 🇲🇬 **Madagascar** : 40,3%

### 2️⃣ La production mondiale est-elle suffisante ?

**OUI.** Le monde produit assez pour nourrir **7,1 milliards de personnes** (94,3% de la population).

Même en ne comptant que les végétaux, on pourrait nourrir **5,87 milliards** (78%).

```python
# Calcul de la capacité théorique mondiale
seuil_fao = 2940  # kcal par personne par jour
production_totale_kcal = dispo_alimentaire['Valeur'].sum()
personnes_nourries = production_totale_kcal / (seuil_fao * 365)

print(f"Capacité : {personnes_nourries/1e9:.2f} milliards de personnes")
# Résultat : 7.1 milliards (94,3% de la population)
```

### 3️⃣ Alors où passe la nourriture ?

**Seulement 49,3% de la production va à l'alimentation humaine.**

Le reste se répartit ainsi :
- 🥩 **36,1% des céréales** → Alimentation animale
- 🏭 **22,4%** → Traitement industriel
- 🗑️ **4,6%** → Pertes et gaspillage
- 🌱 **1,6%** → Semences

```python
# Analyse de l'utilisation des céréales
cereales = dispo_alimentaire[dispo_alimentaire['Produit'].str.contains('Céréales')]
utilisation = cereales.groupby('Élément')['Valeur'].sum()

# Résultat clé :
# Nourriture humaine : 42,9%
# Nourriture animale : 36,1%
# → Les animaux mangent presque autant de céréales que les humains
```

### 4️⃣ Le paradoxe de l'exportation

**Cas de la Thaïlande :**
- Produit 30,2 milliards de kg de manioc
- En exporte **83%**
- Résultat : **8,67% de sa population en sous-nutrition**

**Produire beaucoup ≠ nourrir sa population.**

### 5️⃣ L'aide alimentaire va-t-elle aux bons pays ?

**NON.** Les 3 pays qui reçoivent le plus d'aide (Syrie, Éthiopie, Yémen) n'apparaissent **pas** dans le top 10 de la sous-nutrition chronique.

L'aide répond aux crises et conflits, pas à la faim structurelle.

```python
# Top 10 sous-nutrition vs Top 10 aide alimentaire
top_sous_nutrition = ['Haiti', 'North Korea', 'Madagascar', 'Zambia', ...]
top_aide = ['Syria', 'Ethiopia', 'Yemen', 'South Sudan', ...]

# Intersection : 0 pays en commun dans le top 5
```

---

## 💡 Conclusion

> **Le problème de la faim dans le monde n'est PAS un problème de production, mais de répartition.**

**Les preuves :**
1. Production mondiale suffisante pour 94,3% de la population
2. Seulement 49% de la production destinée aux humains
3. 36% des céréales servent à nourrir les animaux
4. Des pays producteurs exportent massivement malgré leur sous-nutrition interne
5. L'aide alimentaire ne cible pas les pays en faim chronique

---

## 📋 Recommandations pour la FAO

### 🚨 Court terme (0-12 mois)

**1. Rediriger l'aide alimentaire**
- Cibler les pays >35% de sous-nutrition chronique (Haïti, Corée du Nord, Madagascar)
- Stabiliser les flux d'aide (actuellement très irréguliers d'une année à l'autre)

### 🎯 Moyen terme (1-3 ans)

**2. Politiques d'export responsable**
- Taxer les exportations alimentaires depuis les pays >10% de sous-nutrition
- Exemple : La Thaïlande devrait réduire ses exports de manioc de 83% à 50%

**3. Optimiser la chaîne alimentaire**
- Réduire l'utilisation des céréales pour l'alimentation animale (de 36% à 25%)
- Effet : Libère assez de nourriture pour nourrir **150 millions de personnes**

### 🌱 Long terme (3-5 ans)

**4. Transition alimentaire mondiale**
- Promouvoir l'alimentation végétale directe (plus efficace énergétiquement)
- Investir dans l'agriculture locale des pays en sous-nutrition

**5. Réduction des pertes**
- Programme de réduction des pertes post-récolte (actuellement 4,6%)
- Formation des agriculteurs aux techniques de conservation

---

## 🛠️ Technologies utilisées

- **Python 3.9+** : langage de programmation
- **Pandas** : manipulation et analyse de données
- **Matplotlib** : visualisations graphiques
- **Seaborn** : graphiques statistiques avancés
- **Jupyter Notebook** : environnement de développement

---

## 📂 Structure du projet

```
.
├── README.md                            # Documentation du projet
├── analyse_sous_nutrition_mondiale.ipynb # Notebook Jupyter complet
└── data/                                 # Datasets FAO 2017
    ├── population.csv                    # Population par pays
    ├── dispo_alimentaire.csv             # Disponibilité alimentaire
    ├── aide_alimentaire.csv              # Aide alimentaire 2013-2017
    └── sous_nutrition.csv                # Taux de sous-nutrition
```

---

## 🚀 Installation et utilisation

### Prérequis

```bash
Python 3.9+
```

### Installation des dépendances

```bash
pip install pandas matplotlib seaborn jupyter
```

### Lancer le notebook

```bash
git clone https://github.com/Heltondsm/etude-sante-publique-fao.git
cd etude-sante-publique-fao
jupyter notebook analyse_sous_nutrition_mondiale.ipynb
```

---

## 📊 Aperçu du code

### Calcul de la sous-nutrition mondiale

```python
# Chargement des données
population = pd.read_csv('data/population.csv')
sous_nutrition = pd.read_csv('data/sous_nutrition.csv')

# Jointure des datasets
df_2017 = pd.merge(
    population[population['Année'] == 2017],
    sous_nutrition[sous_nutrition['Année'] == 2017],
    on='Zone'
)

# Calcul des personnes sous-nourries
df_2017['Personnes_sous_nourries'] = (
    df_2017['Population'] * df_2017['Pourcentage'] / 100
)

# Agrégation mondiale
total_sous_nutrition = df_2017['Personnes_sous_nourries'].sum()
total_population = df_2017['Population'].sum()
taux_mondial = (total_sous_nutrition / total_population) * 100

print(f"Taux mondial de sous-nutrition : {taux_mondial:.2f}%")
# Résultat : 7.01%
```

### Top 10 des pays les plus touchés

```python
# Tri par taux de sous-nutrition décroissant
top_10 = df_2017.nlargest(10, 'Pourcentage')[['Zone', 'Pourcentage']]

# Visualisation
import matplotlib.pyplot as plt

plt.figure(figsize=(12, 6))
plt.barh(top_10['Zone'], top_10['Pourcentage'], color='#e74c3c')
plt.xlabel('Pourcentage de sous-nutrition (%)')
plt.title('Top 10 des pays les plus touchés (2017)')
plt.gca().invert_yaxis()
plt.show()
```

### Analyse de l'utilisation des céréales

```python
# Filtrer les céréales
cereales = dispo_alimentaire[
    dispo_alimentaire['Produit'].str.contains('Céréales', na=False)
]

# Grouper par utilisation
utilisation = cereales.groupby('Élément')['Valeur'].sum()

# Camembert
plt.pie(utilisation, labels=utilisation.index, autopct='%1.1f%%')
plt.title('Utilisation des céréales mondiales')
plt.show()
```

---

## 📈 Compétences démontrées

### Techniques Data
- ✅ Manipulation de données avec Pandas (merge, groupby, filtering)
- ✅ Nettoyage et harmonisation de 4 datasets FAO
- ✅ Calculs statistiques et agrégations multi-niveaux
- ✅ Visualisations impactantes (barplots, pie charts, scatter plots)
- ✅ Storytelling avec les données

### Business acumen
- ✅ Traduction d'une question business en analyse technique
- ✅ Identification de paradoxes (exportations massives malgré sous-nutrition)
- ✅ Recommandations actionnables basées sur les données
- ✅ Communication claire de résultats complexes

---

## 📧 Contact

**Helton Dos Santos Moreira**
Data Analyst | 10 ans d'expérience Business (retail + e-commerce) → Reconversion Data

- 📧 Email : heltonmail8@gmail.com
- 💼 LinkedIn : [in/helton-dsm-data](https://linkedin.com/in/helton-dsm-data)
- 🐙 GitHub : [Heltondsm](https://github.com/Heltondsm)

---

## 🔗 Autres projets

- [Prévision SARIMA des ventes e-commerce](https://github.com/Heltondsm/ecommerce-sales-analysis-sarima) — Séries temporelles, grid search sur 64 modèles, RMSE ±12%
- [Exploration SQL — Portefeuille assurances habitation](https://github.com/Heltondsm/sql-assurances-habitation) — 50K+ contrats, jointures, agrégations, segmentation géographique
- [Performance e-commerce — Le Grand Marché](https://github.com/Heltondsm/analyse-ventes-ecommerce) — Excel, KPIs, trafic ×30, segmentation 2 profils

---

**Projet réalisé en mars 2026**
