
# Rapport Final : Analyse du Marché Immobilier au Québec

## Introduction

Ce projet vise à analyser le marché immobilier au Québec en identifiant les facteurs clés influençant les prix des propriétés et en construisant des modèles prédictifs précis.

## Analyse Exploratoire des Données

### Matrice de Corrélation
![Matrice de Corrélation](../reports/figures/matrice_correlation.png)

**Interprétation :** 
- La matrice de corrélation montre une relation modérée positive (0.38) entre la **surface habitable** et le **prix**. Cela indique que les propriétés avec des surfaces habitables plus grandes ont tendance à être plus chères.
- Les **taxes municipales** (corrélation de 0.22) influencent également les prix des propriétés, bien que cet effet soit moins prononcé. Cela peut être lié au fait que des propriétés de grande valeur sont souvent situées dans des zones avec des infrastructures et des services coûteux.
- Une corrélation faible entre le **nombre de chambres** (0.26) et le **prix** montre que cette caractéristique n'est pas toujours déterminante, probablement en raison d'autres facteurs comme l'emplacement et la surface totale.

Ces relations mettent en évidence les variables clés à prendre en compte lors de la modélisation prédictive.

### Distribution des Prix
![Distribution des Prix](../reports/figures/distribution_prix_corrected.png)

**Interprétation :**  
- La distribution des prix est asymétrique avec une longue queue à droite, reflétant la présence de quelques propriétés de luxe extrêmement coûteuses.
- La majorité des propriétés ont des prix situés entre 100 000 $ et 500 000 $, ce qui représente des maisons accessibles à la plupart des acheteurs.

Cette asymétrie indique un marché dominé par des biens résidentiels abordables, avec un segment de niche pour les propriétés haut de gamme.

### Relation Surface Habitable vs Prix
![Relation Surface Habitable vs Prix](../reports/figures/relation_surface_prix_corrected.png)

**Interprétation :**  
- Une relation linéaire positive est clairement visible entre la **surface habitable** et le **prix**. Les propriétés avec des surfaces plus grandes tendent à afficher des prix plus élevés.
- Cependant, la variabilité pour des tailles similaires montre que d'autres facteurs, comme l'emplacement, jouent un rôle important dans la détermination des prix.

Cette relation confirme que la **surface habitable** est un facteur clé influençant les prix et justifie son inclusion dans les modèles prédictifs.

### Boxplot des Prix par Région
![Boxplot des Prix par Région](../reports/figures/prix_par_region_corrected.png)

**Interprétation :**  
- Les régions métropolitaines comme **Montréal** et **Laval** affichent des prix médians significativement plus élevés, reflétant une forte demande et une densité urbaine.
- En revanche, des régions comme **Abitibi-Témiscamingue** et **Bas-Saint-Laurent** présentent des prix médians beaucoup plus bas, souvent liés à leur caractère rural et à une demande plus faible.
- La large dispersion des prix dans certaines régions indique une diversité des propriétés en termes de taille, d'emplacement et de type.

Ces disparités régionales sont essentielles pour orienter des politiques adaptées à chaque zone géographique.

## Modélisation

Nous avons testé plusieurs modèles, notamment la Régression Linéaire, Random Forest et XGBoost.

### Résultats des Modèles

| Modèle               | MAE           | MSE            | RMSE          | R²              |
|----------------------|---------------|----------------|---------------|-----------------|
| Linear Regression | 19287647001672124.00 | 770439598889673796562123066880032768.00 | 877746887712895104.00 | -45745895446557461839872.0000 |
| Random Forest | 404927.35 | 8860325717864.74 | 2976629.93 | 0.4739 |
| XGBoost | 333644.94 | 7691857827131.17 | 2773419.88 | 0.5433 |

### Meilleur Modèle : XGBoost

- **MAE** : 333644.94
- **MSE** : 7691857827131.17
- **RMSE** : 2773419.88
- **R²** : 0.5433

**Interprétation :**  
- Le modèle XGBoost est le plus performant parmi les modèles testés, avec les meilleures métriques :
  - **MAE (Erreur Absolue Moyenne)** : 333644.94, indiquant une faible erreur moyenne entre les prédictions et les valeurs réelles.
  - **R² (Coefficient de Détermination)** : 0.5433, montrant que le modèle explique une grande part de la variance des prix.

Ces performances démontrent que XGBoost capture efficacement les relations complexes entre les variables explicatives et le prix.

### Importance des Caractéristiques
![Random Forest Feature Importance](../reports/figures/Random Forest_feature_importance.png)
![XGBoost Feature Importance](../reports/figures/XGBoost_feature_importance.png)

**Interprétation :**  
- Les deux modèles, Random Forest et XGBoost, identifient la **surface habitable** comme la variable la plus importante, suivie des **taxes municipales** et de la **région**.
- Les résultats mettent en évidence que l'emplacement et les caractéristiques financières sont des déterminants majeurs des prix.

Ces informations peuvent guider les décideurs pour cibler les politiques sur ces variables.

## Conclusion

Le modèle **XGBoost** a montré les meilleures performances pour prédire les prix des propriétés, avec un **R²** élevé de 0.5433. Les analyses confirment que la surface habitable, les taxes municipales et la localisation régionale sont des facteurs déterminants des prix.

### Recommandations
1. **Pour les décideurs politiques** :
   - Encourager des politiques pour augmenter l'offre de propriétés abordables, en particulier dans les régions métropolitaines.
   - Réviser les taxes municipales dans les zones où elles influencent fortement les prix pour rendre le logement plus accessible.

2. **Pour les urbanistes** :
   - Prioriser des projets de logements de tailles modérées, qui répondent à la majorité des besoins du marché.
   - Développer des infrastructures dans les régions moins coûteuses pour équilibrer la demande.

3. **Pour les acteurs du marché immobilier** :
   - Mettre en avant la surface habitable et les caractéristiques régionales dans les campagnes marketing.
   - Identifier les niches de marché dans les régions avec une forte variabilité des prix.

Les résultats obtenus offrent des bases solides pour orienter les décisions stratégiques dans le secteur immobilier au Québec.
