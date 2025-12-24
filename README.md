# IVOIRE SHOP - Data Warehouse & Business Intelligence

Projet d'entrepôt de données (Data Warehouse) pour l'analyse des ventes d'une chaîne de magasins, avec pipeline ETL complet et tableaux de bord Power BI.

## Description

Ce projet implémente une solution complète de Business Intelligence comprenant :
- Un entrepôt de données dimensionnel (schéma en étoile)
- Des processus ETL automatisés pour l'extraction, transformation et chargement des données
- Des rapports et visualisations interactives Power BI
- Une documentation technique détaillée

## Architecture

### Base de données : EntrepotVente

**Tables de dimensions :**
- `DIM_CLIENT` - Informations clients
- `DIM_PRODUIT` - Catalogue produits
- `DIM_EMPLOYE` - Données employés
- `DIM_MAGASIN` - Informations magasins
- `DIM_DATE` - Dimension temporelle

**Table de faits :**
- `FAIT_VENTES` - Transactions de ventes avec métriques (quantité, montant, remise)

**Zone de staging :**
- Tables intermédiaires pour le processus ETL
- Schéma `staging` dédié

### Processus ETL

Le script SQL comprend des procédures stockées pour :
- Extraction des données sources
- Transformation et nettoyage
- Chargement dans les dimensions et tables de faits
- Génération automatique de la dimension date
- Orchestration complète via `ETL_Master_Process`

## Structure du projet

```
IVOIRE-SHOP/
├── etl/
│   └── SCRIPT.sql              # Script complet de création et ETL (873 lignes)
├── powerbi/
│   ├── REPORTING IVOIRE SHOP.pbix  # Fichier Power BI
│   └── REPORTING.pdf           # Export PDF des rapports
├── documentation/
│   └── RAPPORT.pdf             # Documentation technique complète
└── captures/
    ├── CUBE.png                # Schéma du cube OLAP
    └── 1MDX.JPG à 7MDX.JPG     # Requêtes MDX et visualisations
```

## Technologies utilisées

- **SGBD :** Microsoft SQL Server 2022 (Compatibility Level 160)
- **ETL :** Procédures stockées T-SQL
- **Reporting :** Microsoft Power BI Desktop
- **OLAP :** SQL Server Analysis Services (SSAS)

## Installation

### Prérequis
- SQL Server 2022 ou version compatible
- Power BI Desktop
- Droits d'administration sur SQL Server

### Déploiement

1. Exécuter le script de création :
```sql
sqlcmd -S <serveur> -i etl/SCRIPT.sql
```

2. Lancer le processus ETL complet :
```sql
EXEC [dbo].[ETL_Master_Process]
```

3. Ouvrir le fichier Power BI :
```
powerbi/REPORTING IVOIRE SHOP.pbix
```

## Utilisation

Le processus ETL peut être exécuté manuellement ou planifié via SQL Server Agent. Les rapports Power BI se connectent directement à l'entrepôt de données pour des analyses en temps réel.

## Documentation

Consulter le fichier `documentation/RAPPORT.pdf` pour :
- Spécifications détaillées du modèle dimensionnel
- Diagrammes d'architecture
- Guide d'utilisation des rapports
- Requêtes MDX pour analyses avancées

## Auteur

**Mohkone01**

## Licence

Ce projet est développé dans un cadre académique/professionnel.
