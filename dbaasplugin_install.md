---

copyright:
  years: 2019, 2020
lastupdated: "2020-10-13"

keywords: DBaaS CLI, Python runtime

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:pre: .pre}
{:note: .note}
{:external: target="_blank" .external}

# Setting up the CLI
{: #install-dbaas-cli-plugin}

Use the {{site.data.keyword.cloud}} CLI to manage your {{site.data.keyword.cloud_notm}} account and resources from your terminal or command line. Use the DBaaS CLI plug-in to get information about your cluster, databases, users, and nodes, and to list and download log files.
{: shortdesc}

## Installing the {{site.data.keyword.cloud_notm}} CLI
{: #install-ibm-cli}

1. To download and install the {{site.data.keyword.cloud_notm}} CLI, see [Getting started with {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started). After the installation is completed, the `ibmcloud` command is available on your system console.
 
2. Log in to the {{site.data.keyword.cloud_notm}}.

   {{site.data.keyword.cloud_notm}} provides various geographical regions that you can log in to. Use the `ibmcloud regions` command to list all the regions. Currently, {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} is supported in the `us-south`, `eu-de`, and `au-syd` regions.
   {: note}

   1. Enter the `ibmcloud login` command, indicating that you're using Single Sign-On (SSO) and specifying the URL of the endpoint you want to log in to, as shown in this example:

      ```
      ibmcloud login --sso -a https://cloud.ibm.com -r us-south
      ```
      {:codeblock}

      The system displays a URL for a web page that provides you with a one-time passcode.

   2. Type in **Y** to open the URL in your default browser.

      Your browser displays the **{{site.data.keyword.cloud_notm}} One time passcode** page.

   3. Copy the passcode from the web page and paste it into your system console command line.

      The passcode isn't displayed in the command line. When the password is authenticated, you receive an **OK** message that indicates you're logged in.

For more {{site.data.keyword.cloud_notm}} CLI commands, see the [REFERENCE section of the {{site.data.keyword.cloud_notm}} CLI documentation](/docs/cli?topic=cli-ibmcloud_cli). You can find more information about the `ibmcloud login` command parameters there.

When you use {{site.data.keyword.ihsdbaas_postgresql_full}}, you might need to create spaces in more than one region and switch between regions by using the `ibmcloud target` command. For more information, see [Adding orgs and spaces](/docs/account?topic=account-orgsspacesusers#orgsspacesusers) and [ibmcloud target](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_target).
{: note}

## Installing the DBaaS CLI components (by operating system)
{: #dbaas_cli_instr}

- [On Linux](#dbaas_cli_linux)
- [On MacOS](#dbaas_cli_macos)
- [On Windows](#dbaas_cli_windows)

To access a complete set of DBaaS commands when you use the {{site.data.keyword.cloud_notm}} CLI, you must also install the following components:

- Python runtime (**only 3.6.x is supported**)
- Python Pip3 package management system
- Python Requests library
- DBaaS CLI plug-in

### On Linux
{: #dbaas_cli_linux}

1. Most Linux distributions have Python and Pip preinstalled. If yours doesn't, use these commands to install them (using the Ubuntu distribution as an example):

   ```
   sudo apt-get install python3 python3-dev
   sudo apt-get install python3-pip
   ```
   {: codeblock}

2. To install the Python Requests library, use this command:

   ```
   sudo pip3 install requests
   ```
   {: codeblock}

3. To add the Python directory to PATH, use this command:

   ```
   export PATH=/usr/bin/python3:$PATH
   ```
   {: codeblock}

4. To install the DBaaS CLI plug-in, use this command:

   ```
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

5. To confirm that the DBaaS CLI plug-in is installed correctly, use this command:

   ```
   ibmcloud
   ```
   {: codeblock}

   The system displays `dbaas` in the list of available commands.

### On MacOS
{: #dbaas_cli_macos}

1. If you don't have Python, download and install it by following these instructions:

    a. Go to the Python website at this URL: https://www.python.org/downloads/mac-osx/

    b. Download and run the appropriate MacOS installer. The installation should include Pip3.

2. To install the Python Requests library, use this command:

   ```
   sudo pip3 install requests
   ```
   {: codeblock}

3. Make sure that Python is in the PATH environment. If not, use one of the following commands, depending on where your Python is located.

   ```
   export PATH=/usr/bin/python3:$PATH
   ```
   {: codeblock}

   ```
   export PATH = /usr/local/bin/python3:$PATH
   ```
   {: codeblock}

4. In some macOS systems, such as 10.15, you can set the PYTHONPATH environment variable to locate the requests module. For example:

   ```
   export PYTHONPATH=/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/site-packages
   ```
   {: codeblock}

5. To install the DBaaS CLI plug-in, use this command:

   ```
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

6. To confirm that the DBaaS CLI plug-in is installed correctly, use this command:

   ```
   ibmcloud
   ```
   {: codeblock}

   The system displays `dbaas` in the list of available commands.

If the installation fails with the message `Unable to obtain plug-in’s metadata. Error: signal: abort trap`, either the installed Python version isn't correct (only Python 3.6.x is supported), or `python-dev` isn't included in the installed python package. Make sure to download and install the correct Python package with the link in the first step.
{: note}

### On Windows
{: #dbaas_cli_windows}

**Note:** Only the x86_64 version of Windows is supported.

1. If you don't have Python, download and install it by following these instructions:

    a. Go to the Python website at this URL: https://www.python.org/downloads/windows/

    b. Download and run the **Windows x86-64 MSI** installer.

    c. On the **Customize Python** menu of the **Python Setup** wizard, specify: **pip Will be installed on local hard disk drive**

2. After installing Python, use your Windows **Edit System Variable** dialog to
   append the following values to the existing **Path** variable value (using Python 3.6 as an example):

   ```
   C:\Python36;C:\Python36\Scripts
   ```
   {: codeblock}

3. To install the Python Requests library, open the **Command Prompt** window and enter this command:

   ```
   pip3 install requests
   ```
   {: codeblock}

4. To install the DBaaS CLI plug-in, use this command:

   ```
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

5. To confirm that the DBaaS CLI plug-in is installed correctly, use this command:

   ```
   ibmcloud
   ```
   {: codeblock}

   The system displays `dbaas` in the list of available commands.

For more information about DBaaS CLI plug-in commands, see [DBaaS CLI reference](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin).
