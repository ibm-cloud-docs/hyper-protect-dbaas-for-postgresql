---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: database cluster, service instance, pricing plans, License Agreement

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# Istanze del servizio
{: #dbaas_webui_service}

## Creazione di un'istanza del servizio
{: #dbaas_webui_create_service}

<ol>
<li>Fai clic sulla voce di catalogo {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} per aprire la schermata di creazione del servizio.</li>
<li>Immetti i valori richiesti.
  <dl>
    <dt>Nome del servizio:</dt>
    <dd>Un nome per il servizio database.</dd>

    <dt>Scegli una regione/ubicazione in cui distribuire:</dt>
    <dd>Seleziona il data center dove sarà ubicato il database.</dd>

    <dt>Seleziona un gruppo di risorse:</dt>
    <dd>Se non è possibile selezionare alcun gruppo di risorse, puoi crearne uno sul dashboard {{site.data.keyword.cloud_notm}}.</dd>

    <dt>Tag:</dt>
    <dd>Le tag sono facoltative. Vedi [Aggiunta di tag alle risorse](/docs/resources?topic=resources-tag#tag) per ulteriori informazioni sull'aggiunta di tag.</dd>

    <dt>Nome cluster/serie di repliche:</dt>
    <dd>Un nome per l'istanza del servizio.</dd>

    <dt>Nome amministratore database:</dt>
    <dd>Un ID utente per l'amministratore del database (DBA).
    <p>**Nota:** l'amministratore del database non deve avere l'autorità SUPERUSER. Le autorità dell'amministratore del database sono limitate a INHERIT, CREATEROLE, CREATEDB, LOGIN e REPLICATION.</p></dd>

    <dt>Password amministratore database:</dt>
    <dd>
    <p>Una password per l'ID utente DBA. Devi creare una password sicura con i seguenti attributi:
      <ul>
        <li>una lunghezza di minimo **15 caratteri**</li>
        <li>almeno **un carattere maiuscolo**</li>
        <li>almeno **un carattere minuscolo**</li>
        <li>almeno **un numero**</li>
        <li>non deve contenere il nome utente</li>
      </ul>
    </p>
    </dd>

    <dt>Conferma password:</dt>
    <dd>Conferma la password per l'ID utente DBA.</dd>

    <dt>Accordo di licenza:</dt>
    <dd>Dopo aver letto l'accordo di licenza, spunta la casella per confermare che lo accetti.</dd>

    <dt>Piani dei prezzi:</dt>
    <dd>I piani dei prezzi offrono diverse categorie di prezzi per i database del tipo PostgreSQL. Scegli quello che meglio si adatta ai tuoi bisogni.</dd>
  </dl>
</li>
<li>Fai clic su **Create**.
<p>Dopo che è stata visualizzata una finestra di dialogo che ti informa che ci vuole del tempo per distribuire il servizio, viene visualizzato il dashboard dell'elenco risorse di {{site.data.keyword.cloud_notm}}. Puoi visualizzare nell'elenco l'istanza del servizio che hai creato nella sezione **Services**. Quando lo stato del servizio è **Provisioned**, l'istanza è pronta per essere utilizzata.</p>
</li>

<li>Seleziona il servizio per visualizzarne il dashboard {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}</li>
</ol>

Per rafforzare ulteriormente la sicurezza, ti consigliamo di aggiornare la **password amministratore database** immediatamente dopo il provisioning dell'istanza del servizio. Devi seguire le stesse regole precedentemente menzionate per impostare la nuova password.
{: note}

## Elenco di tutte le istanze del servizio
{: #dbaas_webui_list_service}

Apri il dashboard {{site.data.keyword.cloud_notm}} per visualizzare un elenco di istanze del servizio create:

<ol>
	<li>Fai clic sul pulsante delle tre barre nella parte in alto a sinistra della console.</li>
	<li>Seleziona Dashboard.</li>
	<li>Seleziona Services.</li>
</ol>

## Visualizzazione delle informazioni dettagliate di un'istanza del servizio
{: #dbaas_webui_show_detail_service}

1. Fai clic sul nome dell'istanza di destinazione per visualizzare il dashboard del servizio.
2. Seleziona **Manage** nella barra di navigazione di sinistra per visualizzare le informazioni generali sulla pagina della scheda **Overview**.
3. Seleziona la scheda **Instances** per visualizzare le informazioni dettagliate.


## Eliminazione di un'istanza del servizio
{: #dbaas_webui_delete_service}

1. Visualizza l'elenco di risorse {{site.data.keyword.cloud_notm}} facendo clic su **Navigation Menu > Resource List**.
2. Apri il twister **Service** per visualizzare le tue istanze del servizio.
3. Seleziona l'istanza del servizio che vuoi eliminare.
4. Fai clic sui tre punti sulla destra.
5. Fai clic su **Delete**.
