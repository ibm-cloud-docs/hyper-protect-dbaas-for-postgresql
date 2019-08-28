---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: DBaaS CLI, Python runtime

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# Installation du plug-in CLI DBaaS
{: #install-dbaas-cli-plugin}

Pour accéder à un jeu complet de commandes DBaaS lorsque vous utilisez l'interface CLI {{site.data.keyword.cloud}}, vous devez installer les composants suivants (voir la rubrique [Instructions](#dbaas_cli_instr)) :

- Le moteur d'exécution Python (la valeur 2.7.15 est recommandée ; les versions 3.x **ne sont pas** prises en charge)
- Le système de gestion de packages Python Pip
- La bibliothèque de demandes Python
- Le plug-in CLI DBaaS

## Instructions d'installation des composants CLI DBaaS (par système d'exploitation)
{: #dbaas_cli_instr}

- [Sous Linux](#dbaas_cli_linux)
- [Sous MacOS](#dbaas_cli_macos)
- [Sous Windows](#dbaas_cli_windows)

### Sous Linux :
{: #dbaas_cli_linux}

1. Python et Pip sont préinstallés sur la plupart des distributions Linux. Si tel n'est pas le cas, utilisez les commandes suivantes pour les installer :

   ```javascript
   sudo apt-get install python python2.7 python-dev
   sudo apt-get install python-pip
   ```
   {: codeblock}

2. Pour installer la bibliothèque de demandes Python, utilisez la commande suivante :

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. Pour installer le plug-in CLI DBaaS, utilisez la commande suivante :

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. Pour vérifier que le plug-in CLI DBaaS a été correctement installé, utilisez la commande suivante :

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   Le système affiche `dbaas` dans la liste des commandes disponibles.

### Sous MacOS :
{: #dbaas_cli_macos}

1. Si vous ne disposez pas encore de Python, téléchargez-le et installez-le en exécutant les instructions suivantes :

    a. Accédez au site Web de Python à l'adresse URL https://www.python.org/downloads/release/python-2715/

    b. Sélectionnez le programme d'installation MacOS approprié, téléchargez-le, puis exécutez-le. Pip doit être inclus dans l'installation.

2. Pour installer la bibliothèque de demandes Python, utilisez la commande suivante :

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. Pour installer le plug-in CLI DBaaS, utilisez la commande suivante :

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. Pour vérifier que le plug-in CLI DBaaS a été correctement installé, utilisez la commande suivante :

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   Le système affiche `dbaas` dans la liste des commandes disponibles.

### Sous Windows :
{: #dbaas_cli_windows}

**Remarque :** seule la version x86_64 de Windows est prise en charge.

1. Si vous ne disposez pas encore de Python, téléchargez-le et installez-le en exécutant les instructions suivantes :

    a. Accédez au site Web de Python à l'adresse URL https://www.python.org/downloads/release/python-2715/

    b. Sélectionnez le programme d'installation **Windows x86-64 MSI**, téléchargez-le, puis exécutez-le.

    c. Dans le menu **Customize Python** de l'assistant **Python Setup**, spécifiez **pip Will be installed on local hard disk drive**

2. Après avoir installé Python, utilisez la boîte de dialogue **Modifier la variable système** de votre système d'exploitation Windows pour ajouter les valeurs suivantes à la valeur de variable **Path** existante :

   ```javascript
   C:\Python27;C:\Python27\Scripts
   ```
   {: codeblock}

3. Pour installer la bibliothèque de demandes Python, ouvrez la fenêtre **Invite de commandes** et entrez la commande suivante :

   ```javascript
   pip install requests
   ```
   {: codeblock}

4. Pour installer le plug-in CLI DBaaS, utilisez la commande suivante :

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

5. Pour vérifier que le plug-in CLI DBaaS a été correctement installé, utilisez la commande suivante :

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   Le système affiche `dbaas` dans la liste des commandes disponibles.

Pour plus d'informations sur les commandes du plug-in DBaaS CLI, vous pouvez vous reporter à [DBaaS CLI reference](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin).
