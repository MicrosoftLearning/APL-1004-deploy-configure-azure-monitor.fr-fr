---
lab:
  title: "Exercice\_: déployer Log Analytics"
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tâches d'apprentissage

- Créer un espace de travail Log Analytics
- Configurer la conservation des données Log Analytics et des stratégies d’archives
- Activer l’accès à un espace de travail Log Analytics

## Instructions de l’exercice

### Créer un espace de travail Log Analytics

1. Dans la barre de recherche du Portail Azure, saisissez **Log Analytics**, puis sélectionnez **Log Analytics** dans la liste de résultats.
1. Sur la page **Espaces de travail Log Analytics**, sélectionnez **Créer**.
1. Sur la page **Informations de base** de l’Assistant de création d’espace de travail Log Analytics, saisissez les informations suivantes, puis sélectionnez **Vérifier + Créer**.
   
    | Propriété | Valeur    |
    |:---------|:---------|
    | Abonnement  | Votre abonnement   |
    | Groupe de ressources    | rg-alpha  |
    | Nom  | LogAnalytics1  |
    | Région    | USA Est  |

4. Vérifiez les informations, puis sélectionnez **Créer**.

### Configurer la conservation des données Log Analytics et des stratégies d’archives

1. Dans la barre de recherche du Portail Azure, saisissez **Log Analytics**, puis sélectionnez **Log Analytics** dans la liste de résultats.
1. Sur la page **Espaces de travail Log Analytics**, sélectionnez **LogAnalytics1**.
1. Sur la page **Espace de travail Log Analytics** de LogAnalytics1, sélectionnez **Utilisation et estimation des coûts**.
1. Sélectionnez **Rétention des données** et glissez le curseur sur 60 jours. Choisissez **OK**.
1. Sur la page **Espace de travail Log Analytics** de LogAnalytics1, sélectionnez **Utilisation et estimation des coûts**.
1. Définissez un **plafond quotidien**. Choisissez **Activé**. Définissez la limite quotidienne sur 10 Go et choisissez **OK**.

### Activer l’accès à un espace de travail Log Analytics

1. Dans la barre de recherche du Portail Azure, saisissez **Log Analytics**, puis sélectionnez **Log Analytics** dans la liste de résultats.
1. Sur la page **Espaces de travail Log Analytics**, sélectionnez **LogAnalytics1**.
1. Sélectionnez **Contrôle d’accès (IAM)** .
1. Sélectionnez **Ajouter**, puis **Ajouter une attribution de rôle**.
1. Dans la liste des rôles, sélectionnez **Lecteur Log Analytics**, puis **Suivant**.
1. Sur la page **Membres**, choisissez **Sélectionner des membres**, puis sélectionnez le groupe de sécurité App Log Examiners. Choisissez **Sélectionner**.
1. Dans l’espace **Membres**, sélectionnez **Vérifier + Attribuer**.
