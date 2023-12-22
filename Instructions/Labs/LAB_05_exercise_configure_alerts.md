---
lab:
  title: "Exercice\_: configurer des alertes"
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tâches d'apprentissage

- Créer un groupe d’actions pour envoyer un e-mail
- Créer une alerte pour l’utilisation de l’UC de machine virtuelle

## Instructions de l’exercice

### Créer un groupe d’actions pour envoyer un e-mail

1. Dans la barre de recherche du Portail Azure, saisissez **Moniteur**, puis sélectionnez **Moniteur** dans la liste de résultats.
1. Dans le menu de navigation, sélectionnez **Alertes**.
1. Sélectionnez des **groupes d’actions**.
1. Sur la page **Groupes d’actions**, sélectionnez **Créer**.
1. Sur la page **Informations de base** de l’Assistant de création de groupe d’actions, définissez les paramètres suivants, puis sélectionnez **Suivant**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Abonnement  | Votre abonnement   |
    | Groupe de ressources  | rg-alpha   |
    | Région    | Global  |
    | Nom du groupe d’actions | NotifyCPU  |
    | Nom d’affichage  | NotifyCPU  |

6. Sur la page **Notifications**, définissez le type de notification sur **E-mail/SMS/Push/Voix**, puis le Nom sur **NotificationEmail**. Cliquez sur l’icône **Modifier** représentant un crayon.
1. Sur la notification E-mail/SMS/Push/Voix, cochez la case **E-mail** saisissez l’adresse **prime@fabrikam.com**. Sélectionnez **OK**. 
1. Sélectionnez **Vérifier + créer**. Cliquez sur **Créer**.


### Créer une alerte pour l’utilisation de l’UC de machine virtuelle

1. Dans la barre de recherche du Portail Azure, saisissez **rg-alpha**, puis sélectionnez **rg-alpha** dans la liste de résultats.
1. Dans la liste des éléments du groupe de ressources, sélectionnez **Linux-VM2**.
1. Sur la page des **propriétés Linux-VM2**, sélectionnez **Alertes**, sous **Supervision**.
1. Sur la page **Alertes**, choisissez **Créer**, puis choisissez **Règle d’alerte**.
1. Sur la page **Condition** de l’Assistant de création de règle d’alerte, définissez le Nom du signal sur **Pourcentage de l’UC**. Utilisez les paramètres par défaut, puis sélectionnez **Suivant**.
1. Sur la page **Actions**, choisissez **Sélectionner un groupe d’actions**.
1. Sur la page **Sélectionner un groupe d’actions**, sélectionnez **NotifyCPU**, puis choisissez **Sélectionner**.
1. Sur la page **Détails**, saisissez le nom de règle d’alerte **HighCPU**. Sélectionnez **Vérifier + Créer**, puis **Créer**.

## Effacer l’abonnement

Pour effacer l’abonnement, supprimez le groupe de ressources **rg-alpha** et supprimez le groupe de sécurité **App Log Examiners**.
