---

copyright:
  years: 2019
lastupdated: "2019-12-20"

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

# Installing the DBaaS CLI plug-in
{: #install-dbaas-cli-plugin}

You can use the {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI plug-in to create and manage the {{site.data.keyword.ihsdbaas_postgresql_full}} services.
{: shortdesc}

## Downloading and installing the {{site.data.keyword.cloud_notm}} CLI
{: #install-ibm-cli}

The IBM Cloud CLI tool is what you use to communicate with IBM Cloud from your terminal or command line. To download and install the {{site.data.keyword.cloud}} CLI, see [Getting started with {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started). After the installation is completed, the `ibmcloud` command is available on your system console.

To access a complete set of DBaaS commands when you use the {{site.data.keyword.cloud}} CLI, you must also install the following components:

- Python runtime (**only 3.x is supported**)
- Python Pip3 package management system
- Python Requests library
- DBaaS CLI plug-in

## Installing the DBaaS CLI components (by operating system)
{: #dbaas_cli_instr}

- [On Linux](#dbaas_cli_linux)
- [On MacOS](#dbaas_cli_macos)
- [On Windows](#dbaas_cli_windows)

### On Linux:
{: #dbaas_cli_linux}

1. Most Linux distributions have Python and Pip preinstalled. If yours does not, use these commands to install them (using the Ubuntu distribution as an example):

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

### On MacOS:
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

4. In some macOS systems, such as 10.15, you may set the PYTHONPATH environment variable to locate the requests module. For example:

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

### On Windows:
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

For more information about DBaaS CLI plug-in commands, see [DBaaS CLI reference](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin).
