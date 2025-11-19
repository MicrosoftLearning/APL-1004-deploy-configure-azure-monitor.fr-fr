---
lab:
  title: "Exercice\_: déployer Log Analytics"
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tâches d'apprentissage

- Créez un espace de travail Log Analytics
- Configurer la conservation des données Log Analytics et des stratégies d’archives
- Activer l’accès à un espace de travail Log Analytics

## Instructions de l’exercice

### Créez un espace de travail Log Analytics

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

### Installez et configurez l’agent Log Analytics sur Linux-VM2

1. Dans la barre de recherche du portail Azure, tapez **machines virtuelles**, puis sélectionnez **Machines virtuelles** dans les résultats de la recherche.
1. Sur la page **Machines virtuelles**, sélectionnez **Linux-VM2**.
1. Sur la page **Linux-VM2**, choisissez **Extensions + Applications** sous **Paramètres**.
1. Choisissez **Ajouter** et sélectionnez l’**agent Log Analytics pour Linux** (également appelé OmsAgentForLinux). Sélectionnez **Suivant**.
1. Pour l’ID d’espace de travail et la clé d’espace de travail, accédez à **LogAnalytics1 > Paramètres > Assistants** dans un onglet ou une autre fenêtre du navigateur.
1. Copiez l’**ID d’espace de travail** et la **clé primaire** depuis l’espace de travail LogAnalytics1.
1. Revenez à la page d’installation de l’extension Linux-VM2 et collez l’ID d’espace de travail et la clé d’espace de travail. Choisissez **Passer en revue et créer**, puis **Créer**.
1. Une fois l’installation terminée, sur la page **Extensions + applications Linux-VM2**, sélectionnez **AzureNetworkWatcherExtension**.
1. Sur la page des détails de l’extension, assurez-vous que **Activer la mise à niveau automatique** est défini sur **Oui**. Sinon, activez l’option et choisissez **Enregistrer**.
1. Revenez à la page **Extensions + Applications** et sélectionnez l’extension **OmsAgentForLinux**.
1. Sur la page des détails de l’extension, assurez-vous que **Activer la mise à niveau automatique** est défini sur **Oui**. Sinon, activez l’option et choisissez **Enregistrer**.

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
