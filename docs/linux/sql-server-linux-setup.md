---
title: "SQL Server 2017 linux 설치 | Microsoft Docs"
description: "설치, 업데이트 및 Linux에서 SQL Server를 제거 합니다. 이 항목에서는 온라인, 오프 라인 및 무인 시나리오에 설명 합니다."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 08/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: c5bd1be5cbe08e9454b1640d9dd58584aa54955f
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Linux에서 SQL Server에 대 한 설치 지침

이 항목에서는 설치, 업데이트 및 SQL Server 2017 Linux에서 제거 하는 방법에 설명 합니다. SQL Server 2017 RC2 Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES), 및 Ubuntu에서 지원 됩니다. Linux 또는 Docker에 대 한 Windows/Mac. Docker 엔진에서 실행할 수 있는 Docker 이미지 형식으로 제공 됩니다.

> [!TIP]
> 빠르게 시작 하려면 하나에 대 한 빠른 시작 자습서로 이동할 [RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), [Ubuntu](quickstart-install-connect-ubuntu.md), 또는 [Docker](quickstart-install-connect-docker.md)합니다.

## <a id="supportedplatforms"></a>지원 되는 플랫폼

SQL Server 2017 Linux 다음 플랫폼에서 사용할 수 있습니다.

| 플랫폼 | 지원 되는 버전 | 가져오기
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 | [RHEL 7.3 가져오기](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | v12 SP2 | [SLES v12 SP2 받기](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [Ubuntu 16.04 가져오기](http://www.ubuntu.com/download/server)
| **Docker 엔진** | 1.8+ | [Docker 가져오기](http://www.docker.com/products/overview)

## <a id="system"></a>시스템 요구 사항

SQL Server 2017 Linux에 대 한 다음과 같은 시스템 요구 사항에 있습니다.

|||
|-----|-----|
| **메모리** | 3.25 GB |
| **파일 시스템** | **XFS** 또는 **EXT4** (예: 다른 파일 시스템, **BTRFS**, 지원 되지 않습니다) |
| **디스크 공간** | 6GB |
| **프로세서 속도** | 2 GHz |
| **프로세서 코어** | 2 코어 |
| **프로세서 유형** | x64 호환만 |

> [!NOTE]
> SQL Server 엔진 되었습니다.이 이번에 최대 1TB의 메모리를 테스트 합니다.

## <a id="platforms"></a> SQL Server 설치

명령줄에서 Linux에서 SQL Server를 설치할 수 있습니다. 자세한 내용은 다음 빠른 시작 자습서 중 하나를 참조 하십시오.

- [Red Hat Enterprise Linux에 설치](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server에 설치](quickstart-install-connect-suse.md)
- [Ubuntu 설치](quickstart-install-connect-ubuntu.md)
- [Docker에서 실행](quickstart-install-connect-ubuntu.md)

## <a id="upgrade"></a>SQL Server 업그레이드

업그레이드 하는 **mssql 서버** linux 플랫폼에 따라 다음 명령 중 하나를 사용 합니다.

| 플랫폼 | 패키지 업데이트 명령 |
|-----|-----|
| RHEL | `sudo yum update mssql-server` |
| SLES | `sudo zypper update mssql-server` |
| Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server` |

이 명령은 최신 패키지를 다운로드 하 고 아래에 있는 이진 파일을 대체 `/opt/mssql/`합니다. 사용자가 생성 한 데이터베이스 및 시스템 데이터베이스는이 작업에 영향을 받지 않습니다.

## <a id="uninstall"></a>SQL Server 제거

제거 하는 **mssql 서버** linux 플랫폼에 따라 다음 명령 중 하나를 사용 합니다.

| 플랫폼 | 패키지 제거 명령 |
|-----|-----|
| RHEL | `sudo yum remove mssql-server` |
| SLES | `sudo zypper remove mssql-server` |
| Ubuntu | `sudo apt-get remove mssql-server` |

패키지를 제거 하는 경우에 생성 된 데이터베이스 파일이 삭제 되지 않습니다. 데이터베이스 파일을 삭제 하려면 다음 명령을 사용 합니다.

```bash
sudo rm -rf /var/opt/mssql/
```

## <a id="unattended"></a>무인된 설치

다음과 같은 방식으로 무인된 설치를 수행할 수 있습니다.

- 초기 단계에서 수행 된 [빠른 시작 자습서](#platforms) 리포지토리를 등록 및 SQL Server를 설치 합니다.
- 실행 하는 경우 `mssql-conf setup`설정, [환경 변수](sql-server-linux-configure-environment-variables.md) 사용 하는 `-n` (메시지 표시) 옵션입니다.

다음 예제에서는 구성 사용 하 여 SQL server Developer edition에서 **MSSQL_PID** 환경 변수입니다. EULA 받기도 (**ACCEPT_EULA**) SA 사용자 암호를 설정 하 고 (**MSSQL_SA_PASSWORD**). `-n` 매개 변수는 구성 값 환경 변수에서 찾아볼 수 있는 unprompted 설치 수행 합니다.

```bash
sudo MSSQL_PID=Developer ACCEPT_EULA=Y MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' /opt/mssql/bin/mssql-conf -n setup
```

또한 다른 동작을 수행 하는 스크립트를 만들 수 있습니다. 예를 들어 다른 SQL Server 패키지를 설치할 수 있습니다.

더 자세한 예제 스크립트를 다음 예제를 참조 하세요.

- [Red Hat 무인된 설치 스크립트](sample-unattended-install-redhat.md)
- [SUSE 무인된 설치 스크립트](sample-unattended-install-suse.md)
- [Ubuntu 무인된 설치 스크립트](sample-unattended-install-ubuntu.md)

## <a id="offline"></a>오프 라인 설치

Linux 컴퓨터에 없는 경우 액세스에 사용 되는 온라인 저장소에는 [빠른 시작](#platforms), 패키지 파일을 직접 다운로드할 수 있습니다. 이러한 패키지는 Microsoft 저장소에 있는 [https://packages.microsoft.com](https://packages.microsoft.com)합니다.

> [!TIP]
> 빠른 시작의 단계와 성공적으로 설치를 다운로드 하거나 아래 패키지를 수동으로 설치할 필요가 없습니다. 이 섹션은 오프 라인 시나리오에 대해서만 합니다.

1. **사용 중인 플랫폼에 대 한 데이터베이스 엔진 패키지 다운로드**합니다. 패키지 세부 정보 구역에서 패키지 다운로드 링크를 찾습니다는 [릴리스 정보](sql-server-linux-release-notes.md)합니다.

1. **Linux 컴퓨터에 다운로드 한 패키지를 이동**합니다. Linux 컴퓨터에 패키지를 이동 하는 한 가지 방법은와 다른 컴퓨터를 사용 하 여 패키지를 다운로드 하도록 하는 경우는 **scp** 명령입니다.

1. **데이터베이스 엔진 패키지 설치**합니다. 해당 플랫폼에 따라 다음 명령 중 하나를 사용 합니다. 이 예제 패키지 파일 이름을 다운로드 한 정확한 이름으로 바꿉니다.

   | 플랫폼 | 패키지 제거 명령 |
   |-----|-----|
   | RHEL | `sudo yum localinstall mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `sudo zypper install mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `sudo dpkg -i mssql-server_versionnumber_amd64.deb` |

    > [!NOTE]
    > 와 (RHEL 및 SLES) RPM 패키지를 설치할 수도 있습니다는 `rpm -ivh` 명령을 하지만 앞의 표에서 명령을 자동으로 종속성 승인한 경우 설치할에서 사용할 수 있는 저장소입니다.

1. **누락 된 종속성 해결**: 누락 된 종속성이 시점에서 할 수 있습니다. 그렇지 않은 경우이 단계를 건너뛸 수 있습니다. Ubuntu, 해당 종속성을 포함 하는 승인 된 저장소에 액세스할 수 있는 경우 가장 쉬운 방법은 사용 하 여 `apt-get -f install` 명령입니다. 또한이 명령은 SQL Server 설치를 완료합니다. 종속성을 수동으로 조사 하는 다음 명령을 사용 합니다.

   | 플랫폼 | 종속성 목록 표시 명령 |
   |-----|-----|
   | RHEL | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `dpkg -I mssql-server_versionnumber_amd64.deb` |

   누락 된 종속성을 해결 한 후 mssql 서버 패키지를 다시 설치 하려고 합니다.

1. **SQL Server 설치를 완료**합니다. 사용 하 여 **mssql conf** SQL Server 설치를 완료 하려면:

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

## <a name="next-steps"></a>다음 단계

설치 후 다른 선택적 SQL Server 패키지를 설치할 수 있습니다.

- [SQL Server 명령줄 도구](sql-server-linux-setup-tools.md)
- [SQL Server 에이전트](sql-server-linux-setup-sql-agent.md)
- [SQL Server 전체 텍스트 검색](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services (Ubuntu)](sql-server-linux-setup-ssis.md)

데이터베이스 만들기 및 관리를 시작 하 여 SQL Server 인스턴스에 연결 합니다. 시작 하려면 빠른 시작 자습서를 참조 합니다.

- [Red Hat Enterprise Linux에 설치](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server에 설치](quickstart-install-connect-suse.md)
- [Ubuntu 설치](quickstart-install-connect-ubuntu.md)
- [Docker에서 실행](quickstart-install-connect-ubuntu.md)
