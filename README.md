```markdown
# Projet HouseMarket: Analyse Statistique des Prix Immobiliers

## Introduction
Ce projet explore les facteurs influençant le prix de vente des maisons à l'aide de tests statistiques, en s'appuyant sur une base de données immobilière fictive. L'objectif principal est d'identifier les caractéristiques des biens (surface, condition, présence de front de mer, rénovation, etc.) qui sont significativement liées aux variations de prix.

## Objectifs du Projet
- **Préparation des données**: Nettoyage et transformation des données brutes.
- **Exploration des variables clés**: Analyse des distributions des variables et création de sous-ensembles pertinents.
- **Tests statistiques**: Application de méthodes d'inférence (t-tests, Mann-Whitney, Kruskal-Wallis, ANOVA) pour comparer les prix moyens entre différents groupes.
- **Interprétation métier**: Traduction des résultats statistiques en informations concrètes pour le marché immobilier simulé.

## Méthodologie
Le projet suit les étapes suivantes :
1. **Chargement et aperçu des données**: Utilisation de `pandas` pour charger le jeu de données `data.csv` et obtenir un aperçu initial (`df.head()`, `df.info()`).
2. **Nettoyage et Feature Engineering**: Conversion du champ 'date' en format `datetime`.
3. **Tests d'hypothèses spécifiques**:
    - **Maisons avec vs sans vue (`view`)**: Comparaison des prix moyens en utilisant le test de Mann-Whitney, compte tenu de la distribution asymétrique des prix.
    - **Surface des maisons en bord de mer (`waterfront`)**: Analyse de la surface habitable moyenne des maisons avec et sans accès au front de mer, également avec le test de Mann-Whitney.
    - **Prix moyen par nombre de chambres (`bedrooms`)**: Comparaison des prix médians pour différents nombres de chambres à l'aide du test de Kruskal-Wallis, en raison de la présence d'outliers et de distributions asymétriques.
    - **Surface habitable par condition (`condition`)**: Examen de la surface habitable en fonction de la condition du bien, en utilisant un test d'ANOVA de Welch (ou `f_oneway` avec `equal_var=False`) suivi d'un test post-hoc de Games-Howell pour identifier les différences inter-groupes.
4. **Analyse de Corrélation**: Étude des corrélations entre le prix et les autres variables quantitatives (`sqft_living`, `sqft_above`, etc.) à l'aide de matrices de corrélation et de nuages de points. Utilisation du test de Spearman et Pearson pour valider la corrélation entre la surface habitable et le prix.

## Résultats Clés
- **Vue (`view`)**: Les maisons avec vue ont un prix moyen significativement plus élevé que celles sans vue (rejet de H0 via Mann-Whitney).
- **Bord de mer (`waterfront`)**: Les maisons en bord de mer ont une surface médiane significativement plus importante que celles qui n'y sont pas (rejet de H0 via Mann-Whitney).
- **Nombre de chambres (`bedrooms`)**: Le prix médian varie significativement selon le nombre de chambres, avec des studios et des maisons de 8 chambres se valorisant particulièrement bien (rejet de H0 via Kruskal-Wallis).
- **Condition du bien (`condition`)**: Il existe des différences significatives dans la surface habitable médiane entre les groupes de différentes conditions de logement (rejet de H0 via ANOVA de Welch et confirmation par Games-Howell).
- **Corrélation Prix/Surface**: La surface habitable (`sqft_living`) et le prix (`price`) s'influencent mutuellement, avec une corrélation positive observée, bien que le pattern visuel puisse être masqué par d'autres facteurs et outliers.

## Conclusion Générale
Les tests statistiques ont démontré que des caractéristiques comme la vue, la proximité du front de mer, le nombre de chambres et la condition du bien sont associées à des variations significatives de prix. Ces analyses fournissent une base rigoureuse pour comprendre les dynamiques de prix sur ce marché immobilier fictif.

## Prochaines Étapes Possibles
- Réaliser des tests statistiques supplémentaires sur d'autres variables ou combinaisons de variables.
- Ajuster les analyses pour prendre en compte plusieurs facteurs simultanément (par exemple, analyse multivariée).
- Développer un modèle de régression pour prédire les prix des maisons en intégrant les facteurs identifiés.
- Affiner l'analyse des outliers et leur impact sur les résultats.

## Technologies Utilisées
- Python
- Pandas
- Matplotlib
- Seaborn
- SciPy (pour les tests statistiques)
- Pingouin (pour les tests post-hoc)

```
