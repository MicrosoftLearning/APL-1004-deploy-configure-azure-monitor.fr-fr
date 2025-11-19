---
lab:
  title: "Exercice\_: surveiller les applications web"
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tâches d'apprentissage

- Activer Application Insights
- Désactiver la journalisation pour le débogueur .NET Core de capture instantanée
- Configurer les journaux HTTP d’application web à écrire dans un espace de travail Log Analytics
- Configurer les données SQL Insights d’application web à écrire dans un espace de travail Log Analytics
- Activer le suivi des changements apportés aux fichiers et à la configuration pour les applications web

## Instructions de l’exercice

### Activer Application Insights

1. Dans la barre de recherche du Portail Azure, saisissez **rg-alpha**, puis sélectionnez **rg-alpha** dans la liste de résultats.
1. Dans la liste des éléments du groupe de ressources, sélectionnez **App Services pour l’application web avec une base de données SQL**.
1. Sous **Surveillance**, choisissez **Application Insights**.
1. Sur la page **Application Insights**, sélectionnez **Activer Application Insights**.
1. Sur la page **Application Insights**, vérifiez que **Créer une ressource** est sélectionnée et que l’espace de travail Log Analytics est défini sur **LogAnalytics1** et choisissez **Appliquer**.
1. Dans la boîte de dialogue **Appliquer les paramètres de supervision**, sélectionnez **Oui**.

### Désactiver la journalisation pour le débogueur .NET Core de capture instantanée

1. Dans la barre de recherche du Portail Azure, saisissez **rg-alpha**, puis sélectionnez **rg-alpha** dans la liste de résultats.
1. Dans la liste des éléments du groupe de ressources, sélectionnez **App Services pour l’application web avec une base de données SQL**.
1. Sous **Surveillance**, choisissez **Application Insights**.
1. Sous **Instrumenter votre application**, sélectionnez **.NET Core**, puis définissez le paramètre Débogueur de capture instantanée sur **Désactivé**. Sélectionnez **Appliquer**.
1. Dans la boîte de dialogue **Appliquer les paramètres de supervision**, sélectionnez **Oui**.

### Configurer les journaux HTTP d’application web à écrire dans un espace de travail Log Analytics

1. Dans la barre de recherche du Portail Azure, saisissez **rg-alpha**, puis sélectionnez **rg-alpha** dans la liste de résultats.
1. Dans la liste des éléments du groupe de ressources, sélectionnez **App Services pour l’application web avec une base de données SQL**.
1. Sous **Supervision**, sélectionnez **Paramètres de diagnostic**.
1. Sur la page **Paramètres de diagnostic**, sélectionnez **Ajouter des paramètres de diagnostic**.
1. Su la page **Paramètres de diagnostic**, choisissez les éléments suivants, puis sélectionnez **Enregistrer**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Nom du paramètre de diagnostic  | httplogs   |
    | Catégories    | Journaux HTTP  |
    | Détails de la destination   | Envoyer à l’espace de travail Log Analytics  |
    | Abonnement  | Votre abonnement  |
    | Espace de travail Log Analytics   | LogAnalytics1   |

### Configurer les données SQL Insights d’application web à écrire dans un espace de travail Log Analytics

1. Dans la barre de recherche du Portail Azure, saisissez **rg-alpha**, puis sélectionnez **rg-alpha** dans la liste de résultats.
1. Dans la liste des éléments du groupe de ressources, sélectionnez l’échantillon de base de données SQL.
1. Sous **Supervision**, sélectionnez **Paramètres de diagnostic**.
1. Sur la page **Paramètres de diagnostic**, sélectionnez **Ajouter un paramètre de diagnostic**.
1. Sur la page **Paramètre de diagnostic**, fournissez les informations suivantes, puis sélectionnez **Enregistrer**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Nom du paramètre de diagnostic  | InsightLogAnalytics   |
    | Catégories    | SQL Insights  |
    | Détails de la destination   | Envoyer à l’espace de travail Log Analytics  |
    | Abonnement  | Votre abonnement  |
    | Espace de travail Log Analytics   | LogAnalytics1   |
