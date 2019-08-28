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


# Instalación del plugin de la CLI de DBaaS
{: #install-dbaas-cli-plugin}

Para acceder a un conjunto completo de mandatos de DBaaS cuando se utiliza la CLI de {{site.data.keyword.cloud}},
debe instalar los siguientes componentes
(consulte las [Instrucciones](#dbaas_cli_instr)):

- Tiempo de ejecución de Python (se recomienda 2.7.15; 3.x **no** está soportado)
- Sistema de gestión de paquetes Python Pip
- Biblioteca de solicitudes de Python
- Plugin de CLI de DBaaS

## Instrucciones para instalar los componentes de la CLI de DBaaS (por sistema operativo)
{: #dbaas_cli_instr}

- [En Linux](#dbaas_cli_linux)
- [En MacOS](#dbaas_cli_macos)
- [En Windows](#dbaas_cli_windows)

### En Linux:
{: #dbaas_cli_linux}

1. La mayoría de las distribuciones de Linux tienen preinstalado Python y Pip. Si no es su caso, utilice estos mandatos para instalarlos:

   ```javascript
   sudo apt-get install python python2.7 python-dev
   sudo apt-get install python-pip
   ```
   {: codeblock}

2. Para instalar la biblioteca de solicitudes de Python, utilice este mandato:

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. Para instalar el plugin de la CLI de DBaaS, utilice este mandato:

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. Para confirmar que el plugin de la CLI de DBaaS se ha instalado correctamente, utilice este mandato:

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   El sistema muestra `dbaas` en la lista de mandatos disponibles.

### En MacOS:
{: #dbaas_cli_macos}

1. Si todavía no tiene Python, descárguelo e instálelo siguiendo estas instrucciones:

    a. Vaya al sitio web de Python en este URL: https://www.python.org/downloads/release/python-2715/

    b. Seleccione el instalador de MacOS adecuado, descárguelo y ejecútelo. La instalación debe incluir Pip.

2. Para instalar la biblioteca de solicitudes de Python, utilice este mandato:

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. Para instalar el plugin de la CLI de DBaaS, utilice este mandato:

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. Para confirmar que el plugin de la CLI de DBaaS se ha instalado correctamente, utilice este mandato:

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   El sistema muestra `dbaas` en la lista de mandatos disponibles.

### En Windows:
{: #dbaas_cli_windows}

**Nota:** solo se admite la versión x86_64 de Windows.

1. Si todavía no tiene Python, descárguelo e instálelo siguiendo estas instrucciones:

    a. Vaya al sitio web de Python en este URL: https://www.python.org/downloads/release/python-2715/

    b. Seleccione el instalador de **Windows x86-64 MSI**, descárguelo y ejecútelo.

    c. En el menú **Personalizar Python** del asistente de **Configuración de Python**, especifique: **pip se instalará en la unidad de disco duro local**

2. Después de instalar Python, utilice el diálogo **Editar variable del sistema** de Windows para añadir los valores siguientes al valor de la variable **Vía de acceso** existente:

   ```javascript
   C:\Python27;C:\Python27\Scripts
   ```
   {: codeblock}

3. Para instalar la biblioteca de solicitudes de Python, abra la ventana **Indicador de mandatos** y especifique este mandato:

   ```javascript
   pip install requests
   ```
   {: codeblock}

4. Para instalar el plugin de la CLI de DBaaS, utilice este mandato:

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

5. Para confirmar que el plugin de la CLI de DBaaS se ha instalado correctamente, utilice este mandato:

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   El sistema muestra `dbaas` en la lista de mandatos disponibles.

Para ver más información sobre los mandatos del plugin de la CLI de DBaaS, revise la [Consulta de la CLI de DBaaS](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin).
