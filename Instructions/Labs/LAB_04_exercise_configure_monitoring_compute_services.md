---
lab:
  title: "Exercice\_: configurer la surveillance pour les services de calcul"
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tâches d'apprentissage

- Créer un point de terminaison de collecte de données
- Créer une règle de collecte de données
- Ajouter une collection de journaux IIS à une règle de collecte de données existante
- Configurer le moniteur de connexion de réseau pour une machine virtuelle IaaS Linux

## Instructions de l’exercice

### Créer un point de terminaison de collecte de données

1. Dans la barre de recherche du Portail Azure, saisissez Moniteur, puis sélectionnez Moniteur dans la liste de résultats.
1. Sur la page Moniteur, sous Paramètres, sélectionnez Points de terminaison de collecte de données.
1. Sur la page Points de terminaison de collecte de données, sélectionnez Créer.
1. Sur la page Créer un point de terminaison de collecte de données, définissez les paramètres suivants, puis sélectionnez Vérifier + Créer.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Nom du point de terminaison  | IaaSVMCollectionEndpoint   |
    | Abonnement  | Votre abonnement  |
    | Groupe de ressources    | rg-alpha  |
    | Région    | USA Est  |

5. Passez en revue les paramètres, puis sélectionnez Créer.

### Créer une règle de collecte de données

1. Dans la barre de recherche du Portail Azure, saisissez **Moniteur**, puis sélectionnez **Moniteur** dans la liste de résultats.
1. Sur la page **Moniteur**, sous **Paramètres**, sélectionnez **Règles de collecte de données**.
1. Sur la page **Règles de collecte de données**, sélectionnez **Créer**.
1. Sur la page **Créer une règle de collecte de données**, configurez les paramètres suivants et sélectionnez **Suivant**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Nom de la règle  | WinVMDCR   |
    | Abonnement  | Votre abonnement   |
    | Groupe de ressources    | rg-alpha  |
    | Région    | USA Est  |
    | Type de plateforme | Windows  |
    | Point de terminaison de collecte de données  | IaaSVMCollectionEndpoint   |

5. Sur la page **Ressources**, sélectionnez **Ajouter des ressources**.
1. Sur la page **Sélectionner une étendue**, cochez la case **WS-VM1** et sélectionnez **Appliquer**.
1. Sur la page **Créer une règle de collecte de données**, sélectionnez **Suivant**.
1. Sur la page **Collecter et livrer**, sélectionnez **Ajouter une source de données**.
1. Sur la page **Ajouter une source de données**, sélectionnez **Journaux des événements Windows**. Dans la catégorie Application, activez les catégories **Critique** et **Erreur**. Dans la catégorie **Sécurité**, choisissez la catégorie **Échec d’audit**. Dans la catégorie **Système**, activez les catégories **Critique** et **Erreur**. 
1. Sélectionnez **Suivant**.
1. Dans la page **Destination**, configurez les paramètres suivants :

    | Propriété | Valeur    |
    |:---------|:---------|
    | Type de destination  | Journaux Azure Monitor   |
    | Abonnement  | Votre abonnement   |
    | Compte ou espace de noms  | LogAnalytics1  |

12. Sélectionnez **Ajouter une source de données**.
1. Sélectionnez **Vérifier + Créer**, puis **Créer**.


### Ajouter une collection de journaux IIS à une règle de collecte de données existante

1. Dans la barre de recherche du Portail Azure, saisissez **Moniteur**, puis sélectionnez **Moniteur** dans la liste de résultats.
1. Sur la page **Moniteur**, sous **Paramètres**, sélectionnez **Règles de collecte de données**.
1. Choisissez la règle **WinVMDRC** dans rg-alpha.
1. Sous **Configuration**, choisissez **Sources de données**.
1. Sur la page **Sources de données**, sélectionnez **Ajouter**.
1. Sur la page **Ajouter une source de données**, sélectionnez **Journaux IIS**.
1. Sélectionnez **Suivant**.
1. Dans la page **Destination**, configurez les paramètres suivants :

    | Propriété | Valeur    |
    |:---------|:---------|
    | Type de destination  | Journaux Azure Monitor   |
    | Abonnement  | Votre abonnement   |
    | Compte ou espace de noms  | LogAnalytics1  |

9. Sélectionnez **Ajouter une source de données**.

### Configurer le moniteur de connexion de réseau pour une machine virtuelle IaaS Linux

1. Dans la barre de recherche du Portail Azure, saisissez **Network Watcher**, puis sélectionnez **Network Watcher** dans la liste de résultats.
1. Sous **Supervision**, sélectionnez **Moniteur de connexion**.
1. Sur la page **Moniteur de connexion**, sélectionnez **Créer**.
1. Sur la page **Informations de base** de l’Assistant de création de moniteur de connexion, saisissez les informations suivantes, puis sélectionnez **Suivant**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Nom du moniteur de connexion  | LinuxVMPubIP   |
    | Abonnement  | Votre abonnement   |
    | Région    | USA Est  |
    | Espace de travail | LogAnalytics1  |

5. Sur la page **Ajouter des détails du groupe de test**, saisissez le nom **LinuxIPTest** et sélectionnez **Ajouter des sources**.
1. Sur la page **Ajouter des sources**, sélectionnez **Points de terminaison** Azure et configurez le type sur **Machines virtuelles**. Sélectionnez **Sous-réseau**, puis cochez la case **Linux-VM**. Sélectionnez **Ajouter des points de terminaison**.
1. Sélectionnez **Ajouter une configuration de test**. 
1. Sur la page **Ajouter une configuration de test**, saisissez le nom **DefaultHTTP** et sélectionnez **Ajouter une configuration de test**.
1. Sélectionnez **Ajouter des destinations**. Sélectionnez **Points de terminaison Azure** et configurez le type sur **Machines virtuelles**. Sélectionnez **Sous-réseau**, puis cochez la case **WS-VM1**. Sélectionnez **Ajouter des points de terminaison**.
1. Sélectionnez **Ajouter un groupe de test**.
1. Sélectionnez **Vérifier + Créer**, puis **Créer**.
