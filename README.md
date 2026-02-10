README

# Analyse statistique des prix immobiliers — Ames Housing (NAmes vs CollgCr)

## Contexte
Ce projet (UA3 — Statistiques avec Python) analyse des données immobilières du dataset **AmesHousing** afin de comparer les **prix de vente** entre deux quartiers de la ville d’Ames (Iowa) et de vérifier si leurs distributions proviennent de la même population. :contentReference[oaicite:1]{index=1}

## Objectif
1) Identifier les deux quartiers les plus représentés dans le dataset (**NAmes** et **CollgCr**). :contentReference[oaicite:2]{index=2}  
2) Comparer les distributions de **SalePrice** (prix de vente) entre ces deux quartiers à l’aide de visualisations et de tests statistiques (Kolmogorov–Smirnov). :contentReference[oaicite:3]{index=3}  
3) Vérifier la normalité des distributions (Shapiro–Wilk + QQ-plots). :contentReference[oaicite:4]{index=4}  
4) Comparer une variable explicative possible : la superficie du premier étage (**1st Flr SF**). :contentReference[oaicite:5]{index=5}  

## Données
- **Dataset :** `AmesHousing.csv`  
- **Taille :** 2 930 lignes × 82 colonnes  
- **Variables utilisées :**
  - `Neighborhood` (quartier)
  - `SalePrice` (prix de vente)
  - `1st Flr SF` (superficie du premier étage en pieds carrés)

> Remarque : si vous préférez garder le repo léger, vous pouvez remplacer le fichier CSV par un lien vers la source ou une méthode de téléchargement (le principe général est de versionner le code plutôt que de gros volumes de données). :contentReference[oaicite:6]{index=6}  

## Méthodologie
Le projet combine exploration descriptive, visualisations et tests statistiques :
- **Python** : `pandas`, `matplotlib`, `scipy`  
- Exploration descriptive : `value_counts`, `describe`  
- Visualisations : histogrammes superposés + **CDF** (fonction de distribution cumulative)  
- Tests : **Kolmogorov–Smirnov** (comparaison de distributions) et **Shapiro–Wilk** (normalité) + **QQ-plots** :contentReference[oaicite:7]{index=7}  

## Résultats clés (insights)
### 1) Comparaison des prix (SalePrice)
- Les histogrammes superposés montrent un décalage net : **CollgCr présente plus de valeurs élevées**.
- La CDF de **CollgCr** est globalement **décalée vers la droite**, ce qui indique des prix plus élevés de manière structurelle. :contentReference[oaicite:8]{index=8}  

**Statistiques descriptives (calculées dans le notebook/script) :**
- Prix moyen NAmes : ~145 097 $
- Prix moyen CollgCr : ~201 803 $
- Médiane NAmes : 140 000 $ | Médiane CollgCr : 200 000 $

### 2) Test Kolmogorov–Smirnov (SalePrice)
- **KS = 0.5837**, **p-value = 3 × 10⁻⁵³**  
 Décision : on **rejette H₀** (les distributions ne proviennent pas de la même population). :contentReference[oaicite:9]{index=9}  

### 3) Normalité des distributions
- Shapiro–Wilk : **p-value << 0.05** pour les deux quartiers  
- QQ-plots + histogrammes : **asymétrie à droite** (queues longues)  
 Conclusion : les distributions de prix **ne suivent pas une loi normale**. :contentReference[oaicite:10]{index=10}  

### 4) Superficie du premier étage (1st Flr SF)
- Comparaison visuelle + test KS sur `1st Flr SF`  
- **KS = 0.153**, **p-value = 0.0007**  
 Décision : on **rejette H₀** (les superficies diffèrent significativement). :contentReference[oaicite:11]{index=11} 
