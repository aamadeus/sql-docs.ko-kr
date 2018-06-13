---
title: Windows에서 읽기 배율에 대한 SQL Server 가용성 그룹 구성 | Microsoft Docs
description: ''
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.reviewer: ''
ms.date: 05/24/2018
ms.topic: conceptual
ms.prod: sql
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.openlocfilehash: de62bd96371e93e9491b9c781da3b41f7086dc75
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768349"
---
# <a name="configure-a-sql-server-availability-group-for-read-scale-on-windows"></a>Windows에서 읽기 배율에 대한 SQL Server 가용성 그룹 구성

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Windows에서 읽기 배율 작업에 대한 SQL Server Always On AG(가용성 그룹)를 구성할 수 있습니다. AG에 대한 두 가지 종류의 아키텍처가 있습니다. 고가용성을 위한 아키텍처는 클러스터 관리자를 사용하여 향상 된 비즈니스 연속성을 제공하고 읽기 가능한 보조 복제본을 포함할 수 있습니다. 이 고가용성 아키텍처를 만들려면 [Windows에서 가용성 그룹의 생성 및 구성](creation-and-configuration-of-availability-groups-sql-server.md)을 참조하세요. 다른 아키텍처는 읽기 배율 작업만을 지원합니다. 이 문서에서는 읽기 배율 작업에 대한 클러스터 관리자 없이 AG를 만드는 방법을 설명합니다. 이 아키텍처는 읽기 배율만을 제공합니다. 고가용성을 제공하지 않습니다.

>[!NOTE]
>`CLUSTER_TYPE = NONE`인 가용성 그룹은 다른 운영 체제 플랫폼에서 호스팅되는 복제본을 포함할 수 있습니다. 고가용성을 지원할 수 없습니다. Linux 운영 체제의 경우 [Linux에서 읽기 배율에 대한 SQL Server 가용성 그룹 구성](../../../linux/sql-server-linux-availability-group-configure-rs.md)을 참조하세요.

[!INCLUDE [Create prerequisites](../../../includes/ss-availability-group-rs-prereq.md)]

## <a name="create-the-ag"></a>AG 만들기

AG를 만듭니다. `CLUSTER_TYPE = NONE`을 설정합니다. 또한 각 복제본을 `FAILOVER_MODE = NONE`으로 설정합니다. 분석 또는 보고 워크로드를 실행하는 클라이언트 응용 프로그램에서 보조 데이터베이스에 직접 연결할 수 있습니다. 읽기 전용 라우팅 목록을 만들 수도 있습니다. 주 복제본에 대한 연결은 읽기 연결 요청을 라운드 로빈 방식으로 라우팅 목록에서 각 보조 복제본으로 전달합니다.

다음 Transact-SQL 스크립트는 `ag1`이라는 AG를 만듭니다. 스크립트는 `SEEDING_MODE = AUTOMATIC`으로 AG 복제본을 구성합니다. 이렇게 설정하면 SQL Server에서 AG에 추가된 후 각 보조 서버에 데이터베이스를 자동으로 만듭니다. 사용자 환경에 대해 다음 스크립트를 업데이트합니다. `<node1>` 및 `<node2>` 값을 복제본을 호스팅하는 SQL Server 인스턴스의 이름으로 바꿉니다. `<5022>` 값을 엔드포인트에 대해 설정한 포트로 바꿉니다. 주 SQL Server 복제본에서 다음 Transact-SQL 스크립트를 실행합니다.

```sql
CREATE AVAILABILITY GROUP [ag1]
    WITH (CLUSTER_TYPE = NONE)
    FOR REPLICA ON
        N'<node1>' WITH (
            ENDPOINT_URL = N'tcp://<node1>:<5022>',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
                    SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
        N'<node2>' WITH (
            ENDPOINT_URL = N'tcp://<node2>:<5022>',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
            SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            );

ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

### <a name="join-secondary-sql-servers-to-the-ag"></a>AG에 보조 SQL 서버 조인

다음 Transact-SQL 스크립트는 `ag1`이라는 AG에 서버를 조인합니다. 사용자 환경에 대해 스크립트를 업데이트합니다. 각 보조 SQL Server 복제본에서 다음 Transact-SQL 스크립트를 실행하여 AG를 조인합니다.

```sql
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);

ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create post](../../../includes/ss-availability-group-rs-postactivity.md)]

이 AG는 고가용성 구성이 아닙니다. 고가용성이 필요한 경우 [Linux에서 SQL Server에 대한 Always On 가용성 그룹 구성](../../../linux/sql-server-linux-availability-group-configure-ha.md) 또는 [Windows에서 가용성 그룹의 생성 및 구성](creation-and-configuration-of-availability-groups-sql-server.md)의 지침을 따릅니다.

## <a name="connect-to-read-only-secondary-replicas"></a>읽기 전용 보조 복제본에 연결

읽기 전용 보조 복제본에 연결하는 방법은 두 가지가 있습니다. 응용 프로그램은 보조 복제본을 호스팅하는 SQL Server 인스턴스에 직접 연결하고 데이터베이스를 쿼리할 수 있습니다. 또한 수신기가 필요한 읽기 전용 라우팅을 사용할 수도 있습니다.

* [읽기 가능한 보조 복제본](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)
* [읽기 전용 라우팅](listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>읽기 비율 가용성 그룹에서 주 복제본 장애 조치(failover)

[!INCLUDE[Force failover](../../../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>다음 단계

* [분산 가용성 그룹 구성](distributed-availability-groups-always-on-availability-groups.md)
* [가용성 그룹에 대한 자세한 정보](overview-of-always-on-availability-groups-sql-server.md)
* [강제 수동 장애 조치(failover) 수행](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)