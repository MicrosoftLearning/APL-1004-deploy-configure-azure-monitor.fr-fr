---
lab:
  title: Préparer votre environnement Azure
  module: Guided Project - Deploy and configure Azure Monitor
---

## Préparer votre BYOS (bring-your-own-subscription)

Cet ensemble d’exercices de labo suppose que vous disposez d’autorisations d’administrateur général pour un abonnement Azure.

1. Dans la barre de recherche du Portail Azure, saisissez **Groupes de ressources**, puis sélectionnez **Groupes de ressources** dans la liste de résultats.
1. Sur la page **Groupes de ressources**, sélectionnez **Créer**.
1. Sur la page **Créer un groupe de ressources**, sélectionnez votre abonnement et entrez le nom « rg-alpha ». Définissez la région sur USA Est, choisissez **Vérifier + Créer**, puis sélectionnez **Créer**.

> [!NOTE]
> Cet ensemble d’exercices part du principe que vous choisissez de déployer dans la région USA Est, mais vous pouvez la remplacer par une autre région si vous le souhaitez. N’oubliez pas que chaque fois que vous voyez USA Est mentionné dans ces instructions, vous devrez remplacer cette région par celle que vous avez choisie.

## Créer un groupe de sécurité App Log Examiners

Dans cet exercice, vous devez créer un groupe de sécurité Entra ID.

1. Dans la barre de recherche du Portail Azure, entrez Azure Active Directory (ou Entra ID) et sélectionnez Azure Active Directory (ou Entra ID) dans la liste des résultats.
1. Sur la page **Répertoire par défaut**, sélectionnez **Groupes**.
1. Sur la page **Groupes**, sélectionnez **Nouveau groupe**.
1. Sur la page **Nouveau groupe**, indiquez les valeurs du tableau suivant, puis choisissez **Créer**.


    | Propriété | Valeur    |
    |:---------|:---------|
    | Type de groupe  | Sécurité   |
    | Nom du groupe  | AppLogExaminers   |
    | Description du groupe  | AppLogExaminers   |


## Déployer et configurer WS-VM1

Dans cet exercice, vous allez déployer et configurer une machine virtuelle Windows Server.

1. Dans la barre de recherche du Portail Azure, saisissez **Machines virtuelles**, puis sélectionnez **Machines virtuelles** dans la liste de résultats.
1. Sur la page **Machines virtuelles**, sélectionnez **Créer**, puis **Machine virtuelle Azure**.
1. Sur la page **Informations de base** de l’Assistant de création de machine virtuelle, sélectionnez les paramètres suivants, puis choisissez **Vérifier + Créer**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Abonnement  | Votre abonnement   |
    | Groupe de ressources    | rg-alpha  |
    | Nom de la machine virtuelle  | WS-VM1   |
    | Région    | USA Est  |
    | Options de disponibilité  | Aucune redondance de l’infrastructure requise  |
    | Type de sécurité | standard   |
    | Image | Centre de données Windows Server 2022 : Édition Azure (x64 Gen2)  |
    | Architecture de machine virtuelle   | x64  |
    | Taille  | Standard_D4s_v3 (4 processeurs virtuels), 16 Gio de mémoire  |
    | Compte administrateur | prime  |
    | Mot de passe  | [Sélectionner un mot de passe sécurisé unique] P@ssw0rdP@ssw0rd   |
    | Ports entrants | RDP 3389   |

4. Passez en revue les paramètres, puis sélectionnez **Créer**.
1. Attendez la fin du déploiement. Une fois le déploiement terminé, sélectionnez **Accéder à la ressource**.
1. Sur la page des **propriétés de WS-VM1**, sélectionnez **Mise en réseau**.
1. Sur la page **Mise en réseau**, sélectionnez la règle RDP. 
1. Dans le champ de règle RDP, remplacez la source par Mon adresse IP, puis sélectionnez **Enregistrer**.

    Cela limite les connexions RDP entrantes à l’adresse IP que vous utilisez actuellement.

9. Sur la page **Mise en réseau**, sélectionnez **Ajouter une règle de port d’entrée**.
1. Sur la page **Ajouter une règle de sécurité d’entrée**, configurez les paramètres suivants et sélectionnez **Ajouter**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Source  | Aucune  |
    | Source port ranges    | *   |
    | Destination  | Quelconque   |
    | Action    | Autoriser  |
    | Priorité  | 310   |
    | Nom  | AllowAnyHTTPInbound  |

11. Sur la page **WS-VM1**, sélectionnez **Connecter**.
1. Sous RDP native, choisissez **Sélectionner**.
1. Sur la page **RDP native**, sélectionnez **Télécharger le fichier RDP**, puis ouvrez le fichier. La boîte de dialogue Connexion Bureau à distance s’ouvre.
1. Dans la boîte de dialogue **Sécurité Windows**, sélectionnez **Plus de choix**, puis Utiliser un autre compte.
1. Entrez le nom d’utilisateur .\prime et le mot de passe sécurisé que vous avez choisi à l’étape 3, puis sélectionnez **OK**.
1. Quand vous êtes connecté à la machine virtuelle Windows Server, cliquez avec le bouton droit sur l’indicateur **Démarrer**, puis sélectionnez **Windows PowerShell (Administrateur)**.
1. Dans l’invite de commandes à privilège élevé, tapez la commande suivante, puis appuyez sur **Entrée**.
    Install-WindowsFeature Web-Server  -IncludeAllSubFeature -IncludeManagementTools 
1. Une fois l’installation terminée, exécutez la commande suivante pour passer au répertoire racine du serveur web.
    Cd c :\inetpub\wwwroot\
1. Exécutez la commande suivante :
    Wget https://raw.githubusercontent.com/Azure-Samples/html-docs-hello-world/master/index.html-OutFile index.html


## Déployer et configurer LX-VM2

Dans cet exercice, vous allez déployer et configurer une machine virtuelle Linux.

1. Dans la barre de recherche du Portail Azure, saisissez **Machines virtuelles**, puis sélectionnez **Machines virtuelles** dans la liste de résultats.
1. Sur la page **Machines virtuelles**, sélectionnez **Créer**, puis **Machine virtuelle Azure**.
1. Sur la page **Informations de base** de l’Assistant de création de machine virtuelle, sélectionnez les paramètres suivants, puis choisissez **Vérifier + Créer**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Abonnement  | Votre abonnement   |
    | Groupe de ressources    | rg-alpha  |
    | Nom de la machine virtuelle  | Linux-VM2   |
    | Région    | USA Est  |
    | Options de disponibilité  | Aucune redondance de l’infrastructure requise  |
    | Type de sécurité | standard   |
    | Image | Ubuntu Server 20.04 LTS (x64 Gen2)  |
    | Architecture de machine virtuelle   | x64  |
    | Taille  | Standard_D2s_v3 (2 processeurs virtuels), 8 Gio de mémoire  |
    | Type d’authentification   | Mot de passe  |
    | Nom d’utilisateur  | Prime   |
    | Mot de passe  | [Sélectionner un mot de passe sécurisé unique] P@ssw0rdP@ssw0rd   |
    | Aucun port d’entrée public  | Aucun   |

4. Vérifiez les informations, puis sélectionnez **Créer**.
1. Une fois la machine virtuelle déployée, ouvrez la page des **propriétés de la machine virtuelle** et sélectionnez **Extensions + Applications** sous **Paramètres**.
1. Sélectionnez **Ajouter**, puis choisissez l’**agent Network Watcher pour Linux**. Sélectionnez **Suivant**, puis **Vérifier + Créer**. Cliquez sur **Créer**.
1. Configurez l’extension AzureNetworkWatcherExtension et OmsAgentForLinux afin qu’elles soient automatiquement mises à niveau.


## Déployer une application web avec une base de données SQL

1. Vérifiez que vous êtes connecté au Portail Azure.
1. Ouvrez un nouvel onglet dans votre navigateur, puis accédez à https://github.com/Azure/azure-quickstart-templates/tree/master/quickstarts/microsoft.web/web-app-sql-database
1. Sur la page GitHub, sélectionnez **Déployer sur Azure**.
1. Un nouvel onglet s’ouvre. Si nécessaire, reconnectez-vous à Azure avec le compte disposant des privilèges d’administrateur général.
1. Sur la page **Informations de base**, sélectionnez **Modifier le modèle**.
1. Dans l’éditeur de modèle, supprimez le contenu des lignes 158 à 174 incluses et supprimez les guillemets à la ligne 157. Choisissez **Enregistrer**.
1. Sur la page **Informations de base**, fournissez les informations suivantes, puis sélectionnez **Suivant**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Abonnement  | Votre abonnement   |
    | Groupe de ressources    | rg-alpha  |
    | Région    | USA Est  |
    | Nom de la référence SKU  | F1  |
    | Capacité de la référence SKU  | 1   |
    | Sql Administrator Login   | prime  |
    | Sql Administrator Login Password  | [Sélectionner un mot de passe sécurisé unique] P@ssw0rdP@ssw0rd   |

8. Vérifiez les informations qui s’affichent, puis sélectionnez **Créer**.
1. Lorsque le déploiement est terminé, sélectionnez **Accéder au groupe de ressources**.

## Déployer une application web Linux

1. Vérifiez que vous êtes connecté au Portail Azure.
1. Ouvrez un nouvel onglet dans votre navigateur, puis accédez à https://learn.microsoft.com/en-us/samples/azure/azure-quickstart-templates/webapp-basic-linux/
1. Sur la page GitHub, sélectionnez **Déployer sur Azure**.
1. Sur la page **Informations de base**, fournissez les informations suivantes, puis sélectionnez **Suivant**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Abonnement  | Votre abonnement   |
    | Groupe de ressources    | rg-alpha  |
    | Région    | USA Est  |
    | Nom de l’application web  | AzureLinuxAppWXYZ (attribuez un nombre aléatoire aux quatre derniers caractères du nom)  |
    | Sku   | S1   |
    | Version LinuxFX  | php|7.4  |

5. Vérifiez les informations, puis sélectionnez **Créer**.
