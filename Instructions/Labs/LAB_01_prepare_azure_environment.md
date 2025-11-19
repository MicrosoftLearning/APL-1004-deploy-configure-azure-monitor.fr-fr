---
lab:
  title: Préparer votre environnement Azure
  module: Guided Project - Deploy and configure Azure Monitor
---

## Préparer votre BYOS (apportez votre propre abonnement)

Pour effectuer ces exercices de labo, vous devez disposer d’autorisations d’administrateur général dans un abonnement Azure.

1. Dans la barre de recherche du portail Azure, saisissez **Groupes de ressources**, puis sélectionnez **Groupes de ressources** dans les résultats de la recherche.
1. Dans la page **Groupes de ressources**, sélectionnez **Créer**.
1. Dans la page **Créer un groupe de ressources**, sélectionnez votre abonnement et entrez le nom rg-alpha. Définissez la région sur USA Est, sélectionnez **Examiner et créer**, puis **Créer**.

> [!NOTE]
> Cet ensemble d’exercices est basé sur un déploiement dans la région USA Est, mais vous pouvez choisir une autre région si vous le souhaitez. Rappelez-vous que chaque fois que « USA Est » est mentionné dans ces instructions, vous devrez remplacer la région par celle que vous avez choisie.

## Créer un groupe de sécurité App Log Examiners

Dans cet exercice, vous allez créer un groupe de sécurité Entra ID.

1. Dans la barre de recherche du portail Azure, entrez Azure Active Directory (ou Entra ID) dans la liste des résultats.
1. Dans la page **Répertoire par défaut**, sélectionnez **Groupes**.
1. Dans la page **Groupes**, sélectionnez **Nouveau groupe**.
1. Dans la page **Nouveau groupe**, indiquez les valeurs du tableau suivant, puis sélectionnez **Créer**.


    | Propriété | Valeur    |
    |:---------|:---------|
    | Type de groupe  | Sécurité   |
    | Nom du groupe  | App Log Examiners   |
    | Description du groupe  | App Log Examiners   |


## Déployer et configurer WS-VM1

Dans cet exercice, vous allez déployer et configurer une machine virtuelle Windows Server.

1. Dans la barre de recherche du portail Azure, tapez **machines virtuelles**, puis sélectionnez **Machines virtuelles** dans les résultats de la recherche.
1. Dans la page **Machines virtuelles**, sélectionnez **Créer**, puis **Machine virtuelle Azure**.
1. Dans la page **Informations de base** de l’Assistant Créer une machine virtuelle, sélectionnez les paramètres suivants, puis **Examiner et créer**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Abonnement  | Votre abonnement   |
    | Groupe de ressources    | rg-alpha  |
    | Nom de la machine virtuelle  | WS-VM1   |
    | Région    | USA Est  |
    | Options de disponibilité  | Aucune redondance d’infrastructure requise  |
    | Type de sécurité | standard   |
    | Image | Centre de données Windows Server 2022 - Édition Azure - x64 Gen2  |
    | Architecture de machine virtuelle   | x64  |
    | Taille  | Standard_D4s_v3 - 4 processeurs virtuels, 16 Gio de mémoire  |
    | Compte administrateur | prime  |
    | Mot de passe  | [Sélectionner un mot de passe sécurisé unique] P@ssw0rdP@ssw0rd   |
    | Ports entrants | RDP (3389)   |

4. Passez en revue les paramètres, puis sélectionnez **Créer**.
1. Attendez la fin du déploiement. Une fois le déploiement terminé, sélectionnez **Accéder à la ressource**.
1. Dans la page des **propriétés de WS-VM1**, sélectionnez **Mise en réseau**.
1. Dans la page **Mise en réseau**, sélectionnez la règle RDP. 
1. Dans le champ de règle RDP, remplacez la source par « Mon adresse IP », puis cliquez sur **Enregistrer**.

    Cela limite les connexions RDP entrantes à l’adresse IP que vous utilisez actuellement.

9. Dans la page **Mise en réseau**, sélectionnez **Ajouter une règle de trafic entrant pour un port**.
1. Dans la page **Ajouter une règle de sécurité de trafic entrant**, configurez les paramètres suivants et cliquez sur **Ajouter**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Source  | Quelconque  |
    | Source port ranges    | *   |
    | Destination  | Quelconque   |
    | Service   | HTTP  |
    | Action    | Autoriser  |
    | Priority  | 310   |
    | Nom  | AllowAnyHTTPInbound  |

11. Dans la page **WS-VM1**, cliquez sur **Se connecter**.
1. Sous RDP natif, cliquez sur **Sélectionner**.
1. Dans la page **RDP natif**, sélectionnez **Télécharger le fichier RDP**, puis ouvrez le fichier. Cette action permet d’afficher la boîte de dialogue Connexion Bureau à distance.
1. Dans la boîte de dialogue **Sécurité Windows**, sélectionnez **Plus de choix**, puis Utiliser un autre compte.
1. Entrez le nom d’utilisateur « .\prime » et le mot de passe sécurisé que vous avez choisi à l’étape 3, puis cliquez sur **OK**.
1. Une fois connecté à la machine virtuelle Windows Server, cliquez avec le bouton droit sur le conseil de **Démarrage** et sélectionnez **Windows PowerShell (admin)**.
1. À l’invite de commandes avec élévation de privilèges, tapez la commande suivante, puis appuyez sur **Entrée**.
    Install-WindowsFeature Web-Server  -IncludeAllSubFeature -IncludeManagementTools 
1. Une fois l’installation terminée, exécutez la commande suivante pour passer au répertoire racine du serveur web.
    cd c:\inetpub\wwwroot\
1. Exécutez la commande suivante :
    Wget https://raw.githubusercontent.com/Azure-Samples/html-docs-hello-world/master/index.html -OutFile index.html


## Déployer et configurer LX-VM2

Dans cet exercice, vous allez déployer et configurer une machine virtuelle Linux.

1. Dans la barre de recherche du portail Azure, tapez **machines virtuelles**, puis sélectionnez **Machines virtuelles** dans les résultats de la recherche.
1. Dans la page **Machines virtuelles**, sélectionnez **Créer**, puis **Machine virtuelle Azure**.
1. Dans la page **Informations de base** de l’Assistant Créer une machine virtuelle, sélectionnez les paramètres suivants, puis **Examiner et créer**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Abonnement  | Votre abonnement   |
    | Groupe de ressources    | rg-alpha  |
    | Nom de la machine virtuelle  | Linux-VM2   |
    | Région    | USA Est  |
    | Options de disponibilité  | Aucune redondance d’infrastructure requise  |
    | Type de sécurité | standard   |
    | Image | Ubuntu Server 20.04 LTs - x64 Gen2  |
    | Architecture de machine virtuelle   | x64  |
    | Taille  | Standard D2s v3 - 2 processeurs virtuels, 8 Gio de mémoire  |
    | Type d’authentification   | Mot de passe  |
    | Nom d’utilisateur  | Prime   |
    | Mot de passe  | [Sélectionner un mot de passe sécurisé unique] P@ssw0rdP@ssw0rd   |
    | Ports d’entrée publics  | Aucun(e)   |

4. Vérifiez les informations, puis sélectionnez **Créer**.
1. Une fois la machine virtuelle déployée, ouvrez la page des **propriétés de la machine virtuelle** et sélectionnez **Extensions + applications** sous **Paramètres**.
1. Cliquez sur **Ajouter** et sélectionnez l’**Agent Network Watcher pour Linux**. Cliquez sur **Suivant** et sélectionnez **Examiner et créer**. Cliquez sur **Créer**.

> [!NOTE]
> L’installation et la configuration de l’extension OmsAgentForLinux seront effectuées dans l’exercice 2 après la création de l’espace de travail Log Analytics.


## Déployer une application web avec une base de données SQL

1. Vérifiez que vous êtes connecté au portail Azure.
1. Ouvrez un nouvel onglet dans votre navigateur, puis accédez à https://github.com/Azure/azure-quickstart-templates/tree/master/quickstarts/microsoft.web/web-app-sql-database
1. Dans la page GitHub, sélectionnez **Déployer sur Azure**.
1. Un nouvel onglet s’ouvre. Si nécessaire, reconnectez-vous à Azure avec le compte disposant de privilèges d’administrateur général.
1. Sur la page **Informations de base**, sélectionnez **Modifier le modèle**.
1. Dans l’éditeur de modèle, supprimez le contenu des lignes 158 à 174 comprises et supprimez « “,” », à la ligne 157. Choisissez **Enregistrer**.
1. Sous l’onglet **Informations de base**, fournissez les informations suivantes, puis sélectionnez **Suivant**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Abonnement  | Votre abonnement   |
    | Groupe de ressources    | rg-alpha  |
    | Région    | USA Est  |
    | Nom de la référence SKU  | F1  |
    | Capacité de la référence SKU  | 1   |
    | Sql Administrator Login   | prime  |
    | Sql Administrator Login Password  | [Sélectionner un mot de passe sécurisé unique] P@ssw0rdP@ssw0rd   |

8. Vérifiez les informations, puis sélectionnez **Créer**.
1. Lorsque le déploiement est terminé, sélectionnez **Accéder au groupe de ressources**.

## Déployer une application web Linux

1. Vérifiez que vous êtes connecté au portail Azure.
1. Ouvrez un nouvel onglet dans votre navigateur, puis accédez à https://learn.microsoft.com/en-us/samples/azure/azure-quickstart-templates/webapp-basic-linux/
1. Dans la page GitHub, sélectionnez **Déployer sur Azure**.
1. Sous l’onglet **Informations de base**, fournissez les informations suivantes, puis sélectionnez **Suivant**.

    | Propriété | Valeur    |
    |:---------|:---------|
    | Abonnement  | Votre abonnement   |
    | Groupe de ressources    | rg-alpha  |
    | Région    | USA Est  |
    | Nom de l’application web  | AzureLinuxAppWXYZ (attribuez un nombre aléatoire aux quatre derniers caractères du nom)  |
    | Sku   | S1   |
    | Version de LinuxFX  | php|7.4  |

5. Vérifiez les informations, puis sélectionnez **Créer**.
