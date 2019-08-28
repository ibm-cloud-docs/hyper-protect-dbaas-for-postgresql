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


# DBaaS CLI 플러그인 설치
{: #install-dbaas-cli-plugin}

{{site.data.keyword.cloud}} CLI 사용 시에 전체 DBaaS 명령 세트에 액세스하려면 다음 컴포넌트를 설치해야 합니다([지시사항](#dbaas_cli_instr) 참조).

- Python 런타임(2.7.15 권장, 3.x는 지원되지 **않음**)
- Python Pip 패키지 관리 시스템
- Python Requests 라이브러리
- DBaaS CLI 플러그인

## DBaaS CLI 컴포넌트 설치를 위한 지시사항(운영 체제별)
{: #dbaas_cli_instr}

- [Linux의 경우](#dbaas_cli_linux)
- [MacOS의 경우](#dbaas_cli_macos)
- [Windows의 경우](#dbaas_cli_windows)

### Linux의 경우:
{: #dbaas_cli_linux}

1. 대부분의 Linux 배포판에는 Python 및 Pip가 사전 설치되어 있습니다. 아직 설치되지 않은 경우에는 다음 명령을 사용하여 이를 설치하십시오.

   ```javascript
   sudo apt-get install python python2.7 python-dev
   sudo apt-get install python-pip
   ```
   {: codeblock}

2. Python Requests 라이브러리를 설치하려면 다음 명령을 사용하십시오.

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. DBaaS CLI 플러그인을 설치하려면 다음 명령을 사용하십시오.

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. DBaaS CLI 플러그인이 제대로 설치되었는지 확인하려면 다음 명령을 사용하십시오.

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   시스템에서 사용 가능한 명령의 목록에 `dbaas`를 표시합니다.

### MacOS의 경우:
{: #dbaas_cli_macos}

1. 아직 Python이 설치되지 않은 경우에는 다음 지시사항에 따라 이를 다운로드하여 설치하십시오.

    a. Python 웹 사이트(URL: https://www.python.org/downloads/release/python-2715/) 로 이동하십시오.

    b. 적합한 MacOS 설치 프로그램을 선택하고 이를 다운로드하여 실행하십시오. 설치에 Pip가 포함되어야 합니다.

2. Python Requests 라이브러리를 설치하려면 다음 명령을 사용하십시오.

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. DBaaS CLI 플러그인을 설치하려면 다음 명령을 사용하십시오.

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. DBaaS CLI 플러그인이 제대로 설치되었는지 확인하려면 다음 명령을 사용하십시오.

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   시스템에서 사용 가능한 명령의 목록에 `dbaas`를 표시합니다.

### Windows의 경우:
{: #dbaas_cli_windows}

**참고:** Windows의 x86_64 버전만 지원됩니다.

1. 아직 Python이 설치되지 않은 경우에는 다음 지시사항에 따라 이를 다운로드하여 설치하십시오.

    a. Python 웹 사이트(URL: https://www.python.org/downloads/release/python-2715/) 로 이동하십시오.

    b. **Windows x86-64 MSI** 설치 프로그램을 선택하고 이를 다운로드하여 실행하십시오.

    c. **Python 설정** 마법사의 **Python 사용자 정의** 메뉴에서 **pip가 로컬 하드 디스크 드라이브에 설치될 예정임**을 지정하십시오.

2. Python 설치 이후에는 Windows **시스템 변수 편집** 대화 상자를 사용하여 다음 값을 기존 **경로** 변수값에 추가하십시오.

   ```javascript
   C:\Python27;C:\Python27\Scripts
   ```
   {: codeblock}

3. Python Requests 라이브러리를 설치하려면 **명령 프롬프트** 창을 열고 다음 명령을 입력하십시오.

   ```javascript
   pip install requests
   ```
   {: codeblock}

4. DBaaS CLI 플러그인을 설치하려면 다음 명령을 사용하십시오.

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

5. DBaaS CLI 플러그인이 제대로 설치되었는지 확인하려면 다음 명령을 사용하십시오.

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   시스템에서 사용 가능한 명령의 목록에 `dbaas`를 표시합니다.

DBaaS CLI 플러그인 명령에 대한 자세한 정보는 [DBaaS CLI 참조](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin)를 참조하십시오.
