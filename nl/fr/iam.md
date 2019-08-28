---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: IAM, identity, access management, role

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Rôles et actions Identity and Access Management
{: #iam}

L'accès aux instances de service {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} pour les utilisateurs de votre compte est contrôlé par {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). Chaque utilisateur qui accède au service {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} de votre compte doit se voir attribuer une règle d'accès avec un rôle IAM défini. La règle détermine les actions qu'un utilisateur peut effectuer dans le contexte du service ou de l'instance sélectionnée. Les actions autorisées sont personnalisées et définies par le service {{site.data.keyword.cloud_notm}} en tant qu'opérations pouvant être réalisées sur le service. Les actions sont ensuite mappées à des rôles utilisateur IAM.
{: shortdesc}

Les règles activent l'accès à accorder à différents niveaux. Certaines des options sont les suivantes :

* Accès à l'ensemble des instances du service sur votre compte
* Accès à une instance de service individuelle de votre compte
* Accès à une ressource spécifique dans une instance

Une fois que vous avez défini l'étendue de la règle d'accès, vous attribuez un rôle qui détermine le niveau d'accès de l'utilisateur. Consultez les tableaux suivants décrivant les actions autorisées par chaque rôle dans le service {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}.

Le tableau suivant détaille les actions mappées sur les rôles de gestion de plateforme. Les rôles de gestion de plateforme permettent aux utilisateurs d'effectuer des tâches sur les ressources de service au niveau de la plateforme, par exemple, attribuer un accès utilisateur au service, créer ou supprimer des instances et lier des instances aux applications.

|Rôle Gestion de plateforme|Description d'actions|Exemples d'actions                                                 |
|------------------------|----------------------|----------------------------------------------------------------|
|Afficheur                  |Afficher des instances de service, sans pouvoir les modifier|<ul><li>Répertorier les clusters</li><li>Afficher les détails d'un cluster</li></ul>|
|Editeur                  |Effectuer toutes les actions de plateforme à l'exception de la gestion du compte et de l'affectation de règles d'accès|<ul><li>Lier un service à un cluster</li></ul>|
|Opérateur                |Effectuer les actions de plateforme requises pour configurer et exploiter des instances de service, par exemple, l'affichage de tableau de bord d'un service.|<ul><li>Lier un service à un cluster</li></ul>|
|Administrateur           |Effectuer toutes les actions de plateforme en fonction de la ressource pour laquelle ce rôle est affecté, y compris l'affectation de règles d'accès à d'autres utilisateurs.|<ul><li>Retirer un cluster</li><li>Créer un cluster</li><li>Mise à jour des règles d'accès utilisateur</li><li>Toutes les actions qu'un afficheur, un éditeur et un opérateur peuvent effectuer</li></ul>|
{: caption="Tableau 1. Actions et rôles utilisateur IAM"}

Pour plus d'informations sur l'attribution de rôles d'utilisateur dans l'interface utilisateur, voir [Gestion de l'accès aux ressources](/docs/iam?topic=iam-iammanidaccser#iammanidaccser).
