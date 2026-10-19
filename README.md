# Analyse de la performance commerciale de BottleNeck

**Projet 9 — Parcours Business Intelligence Analyst | OpenClassrooms**

## Présentation

Ce projet pédagogique accompagne le pilotage commercial de BottleNeck à partir de données financières, de ventes, de promotions et de catalogue web. Il associe une comparaison des méthodes d'accès aux données, un notebook de préparation et un tableau de bord Power BI.

Les trois livrables sont conservés dans leur version fournie, sans modification.

## Objectifs métier

- Comparer les solutions d'extraction, de préparation et de visualisation des données.
- Contrôler la qualité et la cohérence des tables avant leur exploitation.
- Suivre le chiffre d'affaires, les quantités vendues, la marge brute et le taux de marque.
- Analyser les stocks et les priorités de réapprovisionnement.
- Examiner les ventes promotionnelles et les remises estimées.
- Présenter une synthèse et des recommandations opérationnelles.

## Livrables disponibles

| Fichier | Contenu |
|---|---|
| [Rapport d'analyse](Humbert_Paco_1_rapport_092026.docx) | Comparaison de la connexion directe SQLite, de l'extraction CSV et d'une approche ETL |
| [Tableau de bord Power BI](Humbert_Paco_2_tableau_092026.pbix) | Rapport interactif de performance commerciale, stocks et promotions |
| [Notebook de préparation](Humbert_Paco_P9_Final.ipynb) | Audit des CSV, conversions, contrôles de clés et préparation des sources Power BI |

## Sources et documentation incluses

Les sources de préparation et les exports Power BI sont présents dans ce dépôt :

| Dossier | Contenu et utilisation |
|---|---|
| `CSV/` | `Finance.csv`, `Promo.csv`, `Sales.csv`, `Web.csv` : exports bruts utilisés pour la préparation |
| `CSV/PowerBI/` | `Finance_PowerBI.csv`, `Promo_PowerBI.csv`, `Sales_PowerBI.csv`, `Web_PowerBI.csv` : tables préparées fournies pour Power BI |
| `base_donnees/` | Base SQLite initiale `Bottleneck.db` |
| `documentation/` | Dictionnaire des données, schéma de la base et note de cadrage fournis |
| `variantes_csv_fournies/` | Versions distinctes de `Web.csv` et de `PowerBI/Web_PowerBI.csv`, issues du dossier `CSV_corrige/CSV` de l'archive reçue |

Les fichiers de `CSV/` constituent la version de référence conservée pour cette organisation. Les deux variantes Web sont livrées séparément pour ne pas les substituer silencieusement aux sources. Les six autres fichiers de `CSV_corrige/CSV` étant strictement identiques à ceux de `CSV/`, ils ne sont pas dupliqués.

### Accès aux sources

- [Finance.csv](CSV/Finance.csv)
- [Promo.csv](CSV/Promo.csv)
- [Sales.csv](CSV/Sales.csv)
- [Web.csv](CSV/Web.csv)
- [Finance_PowerBI.csv](CSV/PowerBI/Finance_PowerBI.csv)
- [Promo_PowerBI.csv](CSV/PowerBI/Promo_PowerBI.csv)
- [Sales_PowerBI.csv](CSV/PowerBI/Sales_PowerBI.csv)
- [Web_PowerBI.csv](CSV/PowerBI/Web_PowerBI.csv)
- [Bottleneck.db](base_donnees/Bottleneck.db)

### Documents de référence

- [Dictionnaire des données - Bottleneck.pdf](documentation/Dictionnaire%20des%20donn%C3%A9es%20-%20Bottleneck.pdf)
- [Schéma de la base de données.pdf](documentation/Sch%C3%A9ma%20de%20la%20base%20de%20donn%C3%A9es.pdf)
- [Note+de+cadrage+–+Projet+data+Visualisation+-+Bottleneck.pdf](documentation/Note%2Bde%2Bcadrage%2B%E2%80%93%2BProjet%2Bdata%2BVisualisation%2B-%2BBottleneck.pdf)

## Technologies

SQLite, SQLiteStudio, Python, pandas, Jupyter Notebook, Power BI Desktop, Power Query et DAX.

## Préparation des données

Le notebook documente les étapes suivantes :

1. Chargement des quatre CSV avec le séparateur point-virgule.
2. Conservation des DataFrames d'origine et création de copies de travail.
3. Contrôle des dimensions, des types, des valeurs manquantes et des doublons.
4. Conversion des dates, des identifiants et des variables numériques.
5. Vérification de l'unicité des clés et des correspondances entre tables.
6. Contrôle de la période et des anomalies métier.
7. Préparation des quatre tables pour Power BI et export en UTF-8 avec BOM.

Le périmètre d'analyse décrit dans le notebook et le rapport est du **1er octobre 2022 au 30 septembre 2023**. Les lignes d'octobre 2023 sont isolées des tables destinées à ce périmètre.

## Choix d'accès aux données

Le rapport compare la connexion directe à SQLite, l'export CSV et l'utilisation d'un ETL. Il retient le CSV pour le besoin ponctuel étudié, avec des contrôles pandas avant chargement dans Power BI. Une approche ETL est discutée comme évolution en cas de mises à jour plus fréquentes.

## Pages du tableau de bord

| Page | Contenu |
|---|---|
| Performance commerciale | CA, quantités, marge brute, taux de marque, évolution mensuelle et segments |
| Top et Flop des produits | Classements des produits selon leur CA et leur marge brute |
| Stocks et approvisionnements | Stock disponible, valorisation, couverture et rythme de ventes |
| Analyse des stocks et priorités de réapprovisionnement | Références en rupture, à réapprovisionner ou en surstock |
| Promotions | CA et ventes promotionnels, remises estimées et taux de marque promotionnel |
| Synthèse et recommandations | Indicateurs récapitulatifs et recommandations |

Les pages concernées disposent de filtres par mois, segment et type de produit. Des infobulles complètent les indicateurs.

## Limites et points de vigilance documentés

Le rapport et le notebook signalent notamment :

- des valeurs manquantes de commandes fournisseurs, conservées distinctes des zéros ;
- des absences de lignes de ventes pour certains produits, sans imputation arbitraire ;
- une incohérence entre ventes promotionnelles et ventes mensuelles ;
- une date web invalide, sans correction inventée ;
- des observations hors de la période annoncée.

Ces réserves doivent accompagner l'interprétation des indicateurs. Les données et mesures n'ont pas été recalculées lors de la préparation de ce dépôt.

## Consulter le projet

Le notebook est consultable sur GitHub avec ses sorties enregistrées. Le rapport Word peut être téléchargé pour lecture. Le fichier PBIX nécessite Power BI Desktop sous Windows : GitHub permet son téléchargement mais n'affiche pas le tableau de bord interactif.

Le PBIX de cette archive complète a été inspecté pour confirmer ses pages et ses indicateurs. Il n'a pas été ouvert ni actualisé dans Power BI Desktop lors de cette préparation.

## Réexécuter la préparation

1. Conserver les quatre CSV bruts dans le dossier `CSV/` fourni.
2. Installer les dépendances Python puis lancer Jupyter :

```bash
python -m pip install -r requirements.txt
python -m notebook
```

3. Dans une copie du notebook, adapter la variable `DATA_DIR` au dossier local `CSV/`. Par exemple, si Jupyter est lancé depuis la racine du dépôt : `DATA_DIR = Path.cwd() / "CSV"`. Le livrable original conserve son chemin Windows d'origine.
4. Exécuter les cellules dans l'ordre. La cellule d'export écrit les tables préparées dans le sous-dossier `PowerBI` du dossier source.
5. Pour actualiser le tableau de bord, adapter les chemins des sources dans Power BI Desktop aux fichiers fournis dans `CSV/PowerBI/`. Une réexécution peut réécrire ces exports : travailler sur une copie du dépôt si l'on souhaite préserver les fichiers reçus.

Le fichier de dépendances liste les bibliothèques nécessaires à l'ouverture et à l'exécution du notebook ; les versions historiques ne sont pas figées.

## Compétences illustrées

- Comparaison de solutions techniques selon un besoin métier.
- Préparation et contrôle de données relationnelles avec Python.
- Traçabilité des anomalies et gestion des valeurs manquantes.
- Modélisation et restitution d'indicateurs avec Power BI.
- Analyse commerciale, suivi des stocks et lecture des promotions.

## Auteur

Paco Humbert — Projet pédagogique réalisé dans le cadre de la formation Business Intelligence Analyst d'OpenClassrooms.

Seuls ce README, le fichier de dépendances et le `.gitignore` ont été ajoutés pour la publication. Les trois livrables d'origine sont strictement inchangés.

## Sélection des fichiers de l'archive complète

Le rapport, le tableau de bord et le notebook principaux sont ceux du dossier `Botteleneck_Humbert_Paco` de `Projet-9.zip`. Cette copie du PBIX provient de cette nouvelle archive et remplace la copie de l'archive transmise précédemment.

Les autres versions de travail (`Final`, `Final_corrige`, `.vscode`), les guides personnels de soutenance, le modèle de rapport et le ZIP imbriqué ne sont pas repris dans ce dépôt de présentation. Ils restent dans l'archive source, qui n'a pas été modifiée. Aucune correction du code, des mesures, du document Word ou des données n'a été effectuée pour cette publication.
