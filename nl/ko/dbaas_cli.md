---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: instance commands, cluster resource, CLI plugin

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


# {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI 플러그인
{: #dbaas_cli_plugin}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI 플러그인을 사용하여
데이터베이스와 사용자에 대한 정보를 작성, 삭제 및 표시하고 클러스터에 대한 세부사항을 표시하며
인스턴스를 시작 및 중지하고 로그 파일을 나열 및 다운로드할 수 있습니다.
{:shortdesc}


## 선행 조건
{: #prerequisites_dbaas_cli_plugin}

- [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started)를 설치하십시오. {{site.data.keyword.cloud_notm}} CLI에서는 Java SDK 1.7.0이 필요합니다. {{site.data.keyword.cloud_notm}} CLI를 사용하여 명령을 실행하기 위한 접두부는 `ibmcloud`입니다. `ibmcloud` CLI 및 플러그인에 대한 업데이트가 사용 가능하면 터미널에서 알림을 표시합니다. 사용 가능한 모든 명령과 플래그를 사용할 수 있도록 반드시 최신 상태로 CLI를 유지하십시오.

- {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI 플러그인을 설치하십시오. [DBaaS CLI 플러그인 설치](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin)를 참조하십시오. {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
CLI 플러그인의 현재 버전을 보려면 `ibmcloud plugin show dbaas-cli`를 실행하십시오.


## CLI 플러그인 사용 명령
{: #plugin_use}

### `ibmcloud dbaas help`
{: #display_list}

이 명령은 DBaaS 명령의 목록을 표시합니다.

```
ibmcloud help dbaas
```
{: pre}


## 클러스터 명령
{: #cluster_cmds}

### `ibmcloud dbaas cluster-show`
{: #cluster_show}

이 명령은 각 복제본 멤버에 대한 정보를 포함하여 지정된 클러스터의 세부사항을 표시합니다.  

```
ibmcloud dbaas cluster-show <resource_name>
```
{: pre}

**명령 옵션**

<dl>
<dt>*resource_name*</dt>
<dd> 클러스터 리소스의 이름입니다. 리소스 이름을 찾으려면 {{site.data.keyword.cloud_notm}} 명령 `ibmcloud resource service-instances`를 사용하십시오.</dd>
</dl>

## 데이터베이스 명령
{: #db_cmds}

### `ibmcloud dbaas database-create`
{: #db_create}

이 명령은 데이터베이스와 콜렉션(선택사항)을 작성합니다.

```
ibmcloud dbaas database-create <resource_name> <database_name> [<collection>]
```
{: pre}

**명령 옵션**

<dl>
<dt>*resource_name*</dt>
<dd> 클러스터 리소스의 이름입니다.</dd>
<dt>*database_name*</dt>
<dd> 작성할 데이터베이스의 이름입니다.</dd>
<dt>*collection*</dt>
<dd>(선택사항) 작성할 콜렉션의 이름입니다.</dd>
</dl>


### `ibmcloud dbaas database-delete`
{: #db_delete}

이 명령은 데이터베이스를 삭제합니다. 데이터베이스가 인증 정보를 통해 작성되었으며 해당 인증 정보를 아직 사용 중인 경우 해당 데이터베이스를 삭제하지 마십시오.

```
ibmcloud dbaas database-delete <resource_name> <database_name>
```
{: pre}

**명령 옵션**

<dl>
<dt>*resource_name*</dt>
<dd> 클러스터 리소스의 이름입니다.</dd>
<dt>*database_name*</dt>
<dd> 삭제할 데이터베이스의 이름입니다.</dd>
</dl>


### `ibmcloud dbaas databases-list`
{: #db_list}

이 명령은 제공된 클러스터의 모든 데이터베이스를 나열합니다.

```
ibmcloud dbaas databases-list <resource_name>
```
{: pre}

**명령 옵션**

<dl>
<dt>*resource_name*</dt>
<dd> 클러스터 리소스의 이름입니다.</dd>
</dl>


## 데이터베이스 사용자 명령
{: #user_cmds}

### `ibmcloud dbaas user-create`
{: #user_create}

이 명령은 데이터베이스 사용자를 작성합니다.

```
ibmcloud dbaas user-create <resource_name> <username> <password> [<db_name> [<db_name> [...]]]
```
{: pre}

**명령 옵션**

<dl>
<dt>*resource_name*</dt>
<dd> 클러스터 리소스의 이름입니다.</dd>
<dt>*username*</dt>
<dd>작성 중인 데이터베이스 사용자에게 지정할 사용자 이름입니다.</dd>
<dt>*db_name*</dt>
<dd>(선택사항) 사용자가 읽기 및 쓰기 액세스 권한을 보유할 데이터베이스를 지정합니다.</dd>
</dl>


### `ibmcloud dbaas user-delete`
{: #user_delete}

이 명령은 데이터베이스 사용자를 삭제합니다. 데이터베이스 사용자가 인증 정보를 통해 작성되었으며 해당 인증 정보를 아직 사용 중인 경우 해당 데이터베이스 사용자를 삭제하지 마십시오.

```
ibmcloud dbaas user-delete <resource_name> <username>
```
**명령 옵션**

<dl>
<dt>*resource_name*</dt>
<dd> 클러스터 리소스의 이름입니다.</dd>
<dt>*username*</dt>
<dd> 삭제할 데이터베이스 사용자의 사용자 이름입니다.</dd>
</dl>

### `ibmcloud dbaas users-list`
{: #user_list}

이 명령은 모든 데이터베이스 사용자를 나열합니다.

```
ibmcloud dbaas users-list <resource_name>
```
{: pre}

**명령 옵션**

<dl>
<dt>*resource_name*</dt>
<dd> 클러스터 리소스의 이름입니다.</dd>
</dl>


### `ibmcloud dbaas user-show`
{: #user_show}

이 명령은 데이터베이스 사용자에 대한 세부사항을 표시합니다.

```
ibmcloud dbaas user-show <resource_name> <username>
```
{: pre}

**명령 옵션**

<dl>
<dt>*resource_name*</dt>
<dd> 클러스터 리소스의 이름입니다.</dd>
<dt>*username*</dt>
<dd> 표시할 데이터베이스 사용자의 사용자 이름입니다.</dd>
</dl>


## 인스턴스 명령
{: #instance_cmds}

여기에 나열된 인스턴스 명령을 사용하려면 `instance_id`를 알고 있어야 합니다. `instance_id`를 가져오려면 먼저 다음 `ibmcloud` 명령을 사용하여 사용자 계정의 서비스 인스턴스 리소스 그룹 이름을 나열한 후 [`cluster_show`](#cluster_show) 명령을 사용하여 `instance_id`를 가져오십시오.

```
ibmcloud resource service-instances
```
{: pre}


### `ibmcloud dbaas instance-restart`
{: #instance_restart}

이 명령은 실행 중인 인스턴스를 다시 시작합니다.

```
ibmcloud dbaas instance-restart <resource_name> <instance_id>
```
{: pre}

**명령 옵션**

<dl>
<dt>*resource_name*</dt>
<dd> 클러스터 리소스의 이름입니다.</dd>
<dt>*instance_id*</dt>
<dd> 인스턴스의 ID입니다.</dd>
</dl>


### `ibmcloud dbaas instance-start`
{: #instance_start}

이 명령은 중지된 인스턴스를 시작합니다.

```
ibmcloud dbaas instance-start <resource_name> <instance_id>
```
{: pre}

**명령 옵션**

<dl>
<dt>*resource_name*</dt>
<dd> 클러스터 리소스의 이름입니다.</dd>
<dt>*instance_id*</dt>
<dd> 인스턴스의 ID입니다.</dd>
</dl>


### `ibmcloud dbaas instance-stop`
{: #instance_stop}

이 명령은 인스턴스(클러스터의 복제 멤버)를 중지합니다.

```
ibmcloud dbaas instance-stop <resource_name> <instance_id>
```
{: pre}

**명령 옵션**

<dl>
<dt>*resource_name*</dt>
<dd> 클러스터 리소스의 이름입니다.</dd>
<dt>*instance_id*</dt>
<dd> 인스턴스의 ID입니다.</dd>
</dl>


## 로그 명령
{: log_cmds}

### `ibmcloud dbaas log-get`
{: #log_get}

이 명령은 인스턴스에서 로그 파일을 다운로드합니다.

```
ibmcloud dbaas log-get <resource_name> <instance_id> <filename>
```
{: pre}

**명령 옵션**

<dl>
<dt>*resource_name*</dt>
<dd> 클러스터 리소스의 이름입니다.</dd>
<dt>*instance_id*</dt>
<dd> 인스턴스의 ID입니다.</dd>
<dt>*filename*</dt>
<dd> 다운로드할 로그 파일의 이름입니다. 다운로드할 로그 파일의 파일 이름을 판별하려면 [ibmcloud dbaas logs-list](#log_list) 명령을 사용하십시오.</dd>
</dl>

### `ibmcloud dbaas logs-list`
{: #log_list}

이 명령은 인스턴스의 모든 로그 파일을 나열합니다. 나열된 파일 이름을 [ibmcloud dbaas log-get](#log_get) 명령의 입력으로 사용할 수 있습니다.

```
ibmcloud dbaas logs-list <resource_name> <instance_id>
```
{: pre}

**명령 옵션**

<dl>
<dt>*resource_name*</dt>
<dd> 클러스터 리소스의 이름입니다.</dd>
<dt>*instance_id*</dt>
<dd> 인스턴스의 ID입니다.</dd>
</dl>
