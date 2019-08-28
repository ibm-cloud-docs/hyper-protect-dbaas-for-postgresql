---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: service instance, ibmcloud resource

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# Creazione di un'istanza del servizio
{: #dbaas_cli_create_service}

Per creare un'istanza del servizio, utilizza il comando `ibmcloud resource service-instance-create`, come mostrato nel seguente esempio. In Windows, ti consigliamo di utilizzare un terminale bash come Cygwin o Git Bash per immettere il comando.

```javascript
ibmcloud resource service-instance-create MyDBaaSIns03 hyperp-dbaas-postgresql postgresql-small us-south -p '{"name":"DBaaSTestCLICluster03", "admin_name":"admin","password":"passWORD4User19", "confirm_password":"passWORD4User19", "license_agree":["agreed"]}'
```
{: codeblock}

Dove i parametri hanno le seguenti definizioni:

| Parametro        |  Definizione                                                    |
| ---------------- |  -------------------------------------------------------------- |
| *MyDBaaSIns03*   |  Il nome dell'istanza del servizio (sostituisci con un nome di tua scelta). |
| *hyperp-dbaas-postgresql* | Il nome del catalogo di {{site.data.keyword.ihsdbaas_postgresql_full}}. |
| *postgresql-small*  | Il nome del piano. I piani disponibili sono: **postgresql-small**, **postgresql-medium** e **postgresql-large**.  (**Nota:** i nomi dei piani sono sensibili al maiuscolo/minuscolo.) |
| *us-south*            | L'ubicazione in cui sarà posizionato il nuovo database. (**Nota:** al momento solo **us-south** supporta {{site.data.keyword.ihsdbaas_postgresql_full}}.) |
| *-p*               | Una stringa JSON valida che deve contenere i parametri nella seguente tabella. |

<table>
  <tr>
    <th>Parametro -p</th>
    <th>Definizione</th>
  </tr>
  <tr>
    <td>*name*</td>
    <td>Il nome del tuo cluster di database.</td>
  </tr>
  <tr>
    <td>*admin_name*</td>
    <td>Il nome utente dell'amministratore del database che deve essere creato.</td>
  </tr>
  <tr>
    <td>*password*</td>
    <td>
      <p>La password utente dell'amministratore del database che deve essere creato. Devi creare una password sicura con i seguenti attributi:
        <ul>
          <li>una lunghezza di minimo **15 caratteri**</li>
          <li>almeno **un carattere maiuscolo**</li>
          <li>almeno **un carattere minuscolo**</li>
          <li>almeno **un numero**</li>
          <li>non deve contenere il nome utente</li>
        </ul>
      </p>
    </td>
  </tr>
  <tr>
    <td>*confirm_password*</td>
    <td>La stessa password.</td>
  </tr>
  <tr>
    <td>*license_agree*</td>
    <td>Un valore di **agreed** indica che accetti l'accordo di licenza, obbligatorio per utilizzare {{site.data.keyword.ihsdbaas_postgresql_full}}.</td>
  </tr>
</table>

Dopo aver immesso il comando, lo stato della nuova istanza del servizio potrebbe temporaneamente essere inattivo (**inactive**), come mostrato in questo esempio.

```
Creating service instance MYDBaaSIns03 in resource group default of account BSS Metering Test Account as bluemix_ui_metering_test@mailinator.com...
OK
Service instance MYDBaaSIns03 was created.

Name:             MYDBaaSIns03
ID:               crn:v1:bluemix:public:hyperp-dbaas-postgresql:us-south:a/0e79133675a31dbfd10504847a9e174f:279be69f-20f2-4ade-baf9-5c470c400753::
GUID:             279be69f-20f2-4ade-baf9-5c470c400753   
Location:         us-south   
State:            inactive   
Type:             service_instance   
Sub Type:            
Created at:       2019-06-03T06:17:13Z   
Updated at:       2019-06-03T06:17:13Z   
Last Operation:                      
                  Status       create in progress      
                  Updated At   2019-06-03 06:17:13.917566444 +0000 UTC
```
{: codeblock}

Questo si verifica perché servono alcuni minuti per preparare il cluster. Per ottenere un aggiornamento dello stato del cluster, utilizza il comando `ibmcloud resource service-instances`, come mostrato in questo esempio:

```
ibmcloud resource service-instances
Retrieving all instances of all services in resource group default and all locations under account BSS Metering Test Account as bluemix_ui_metering_test@mailinator.com...
OK
Name           Location   State      Type
MyDBaaSIns03   us-south   active     service_instance
```
{: codeblock}

Per rafforzare ulteriormente la sicurezza, ti consigliamo di aggiornare la **password amministratore database** immediatamente dopo il provisioning dell'istanza del servizio. Devi seguire le stesse regole precedentemente menzionate per impostare la nuova password.
{: note}
