---

copyright:
  years: 2019, 2021
lastupdated: "2021-04-13"

keywords: DBaaS CLI, Python runtime

subcollection: hyper-protect-dbaas-for-postgresql

---

{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note .note}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Setting up the CLI
{: #install-dbaas-cli-plugin}

Use the {{site.data.keyword.cloud}} CLI to manage your {{site.data.keyword.cloud_notm}} account and resources from your terminal or command line. Use the DBaaS CLI plug-in to get information about your cluster, databases, users, and nodes, and to list and download log files.
{: shortdesc}

## Installing the {{site.data.keyword.cloud_notm}} CLI
{: #install-ibm-cli}

1. To download and install the {{site.data.keyword.cloud_notm}} CLI, see [Getting started with {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started). After the installation is completed, the `ibmcloud` command is available on your system console.
 
2. Log in to the {{site.data.keyword.cloud_notm}}.

   {{site.data.keyword.cloud_notm}} provides various geographical regions that you can log in to. Use the `ibmcloud regions` command to list all the regions. Currently, {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} is supported in the `us-south` (Dallas), `us-east` (Washington DC), `eu-de` (Frankfurt), and `au-syd` (Sydney) regions.
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

- Python 3 runtime
- Python Pip3 package management system
- Python Requests library
- DBaaS CLI plug-in

### On Linux
{: #dbaas_cli_linux}

1. Most Linux distributions have Python and Pip preinstalled. If yours doesn't, use the following commands to install them (using the Ubuntu distribution as an example).

   ```
   sudo apt-get install python3
   sudo apt-get install python3-pip
   ```
   {: codeblock}

2. To install the Python Requests library, use the following command.

   ```
   sudo pip3 install requests
   ```
   {: codeblock}

3. To add the Python directory to PATH, use the following command.

   ```
   export PATH=/usr/bin/python3:$PATH
   ```
   {: codeblock}

4. To install the DBaaS CLI plug-in, use the following command.

   ```
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

5. To confirm that the DBaaS CLI plug-in is installed correctly, use the following command.

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

2. To install the Python Requests library, use the following command.

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
   export PATH=/usr/local/bin/python3:$PATH
   ```
   {: codeblock}

4. In some macOS systems, such as 10.15, you can set the PYTHONPATH environment variable to locate the requests module. For example:

   ```
   export PYTHONPATH=/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/site-packages
   ```
   {: codeblock}

5. To install the DBaaS CLI plug-in, use the following command.

   ```
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

6. To confirm that the DBaaS CLI plug-in is installed correctly, use the following command.

   ```
   ibmcloud
   ```
   {: codeblock}

   The system displays `dbaas` in the list of available commands.

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

3. To install the Python Requests library, open the **Command Prompt** window and enter the following command.

   ```
   pip3 install requests
   ```
   {: codeblock}

4. To install the DBaaS CLI plug-in, use the following command.

   ```
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

5. To confirm that the DBaaS CLI plug-in is installed correctly, use the following command.

   ```
   ibmcloud
   ```
   {: codeblock}

   The system displays `dbaas` in the list of available commands.

For more information about DBaaS CLI plug-in commands, see [DBaaS CLI reference](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin).
