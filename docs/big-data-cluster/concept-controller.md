---
title: SQL Server 빅 데이터 클러스터 컨트롤러 란? | Microsoft Docs
description: 이 문서에서는 SQL Server 2019 빅 데이터 클러스터의 컨트롤러를 설명 합니다.
author: mihaelablendea
ms.author: mihaelab
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: abf8c174379ad444cd29b5115240ad7c404b2c4b
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221519"
---
# <a name="what-is-the-sql-server-big-data-clusters-controller"></a>SQL Server 빅 데이터 클러스터 컨트롤러 란?

컨트롤러를 배포 하 고 빅 데이터 클러스터를 관리 하기 위한 핵심 논리를 호스트 합니다. Kubernetes 클러스터 및 HDFS 및 Spark와 같은 기타 구성 요소에 포함 된 SQL Server 인스턴스를 사용 하 여 모든 상호 작용 담당 합니다. 

컨트롤러 서비스에는 다음 핵심 기능을 제공합니다.

- 클러스터 수명 주기 관리: 클러스터 부트스트랩 및 구성을 업데이트 하는 delete
- 마스터 SQL Server 인스턴스 관리
- 계산, 데이터 및 저장소 풀 관리
- 클러스터의 상태를 관찰 하려면 모니터링 도구를 노출 합니다.
- 검색 하 고 예기치 않은 문제를 복구 하는 문제 해결 도구를 노출 합니다.
- 클러스터 보안 관리: 보안 클러스터 끝점을 확인, 사용자 및 역할 관리, 클러스터 간 통신에 대 한 자격 증명 구성
- 업그레이드의 워크플로 관리 하므로 안전 하 게 구현 됩니다 (CTP 2.1에서 사용할 수 없음)
- (CTP 2.1에서 사용할 수 없음) 클러스터의 상태 저장 서비스에 대 한 고가용성 및 DR 관리

## <a name="deploying-the-controller-service"></a>컨트롤러 서비스를 배포합니다.

컨트롤러를 배포 하 고 고객이 있는 빅 데이터 클러스터를 구축 하려는 동일한 Kubernetes 네임 스페이스에서 호스트 합니다. 이 서비스 관리자가 설치 하는 Kubernetes 클러스터 부트스트랩 mssqlctl 명령줄 유틸리티를 사용 하는 동안:

```bash
mssqlctl create cluster <name of your cluster>
```

Buildout 워크플로 Kubernetes 기반으로 레이아웃에 설명 된 모든 구성 요소를 포함 하는 모든 기능을 갖춘 SQL Server 빅 데이터 클러스터를 [개요](big-data-cluster-overview.md) 문서. 먼저 부트스트랩 워크플로에서 컨트롤러 서비스를 만들고 컨트롤러 서비스를 설치 및 구성의 마스터, 계산, 데이터 및 저장소 풀의 서비스 파트의 나머지 부분을 조정 합니다이 배포 되 면 합니다.

## <a name="managing-the-cluster-through-the-controller-service"></a>컨트롤러 서비스를 통해 클러스터 관리
순수 하 게 사용 하 여 컨트롤러 서비스를 통해 클러스터를 관리할 수 있습니다 `mssqlctl` Api 또는 클러스터 내에서 호스트 되는 클러스터 관리 포털. 동일한 네임 스페이스에 pod와 같은 추가 Kubernetes 개체를 배포 하는 경우 관리 하거나 하지 컨트롤러 서비스에 의해 모니터링 됩니다.

컨트롤러 및 빅 데이터 클러스터에 대해 생성 된 Kubernetes 개체 (상태 저장 집합, pod, 암호 등)에 전용된 Kubernetes 네임 스페이스에 상주 합니다. 컨트롤러 서비스를 해당 네임 스페이스 내의 모든 리소스를 관리 하는 Kubernetes 클러스터 관리자가 권한이 부여 됩니다.  이 시나리오에 대 한 RBAC 정책을 사용 하 여 초기 클러스터 배포의 일부로 자동으로 구성 된 `mssqlctl`합니다. 

### <a name="mssqlctl"></a>mssqlctl

`mssqlctl` 명령줄 유틸리티 클러스터 관리자가 부트스트랩 및 컨트롤러 서비스에 의해 노출 된 REST Api를 통해 빅 데이터 클러스터를 관리할 수 있도록 Python으로 작성 됩니다.

### <a name="cluster-administration-portal"></a>클러스터 관리 포털

Controller 서비스가 실행 되 면 클러스터 관리자 배포 진행률을 모니터링, 감지 및 클러스터 내에서 서비스를 사용 하 여 문제를 해결 하려면 클러스터 관리 포털을 사용할 수 있습니다. 

## <a name="monitoring-and-troubleshooting-the-controller-service"></a>모니터링 및 컨트롤러 서비스 문제 해결

개봉박두...

## <a name="controller-service-security"></a>컨트롤러 서비스 보안
컨트롤러 서비스에 대 한 모든 통신은 HTTPS를 통한 REST API를 통해 수행 됩니다. 자체 서명 된 인증서를 자동으로 생성 됩니다를 부트스트랩 시. 

인증 컨트롤러 서비스 끝점에는 사용자 이름 및 암호를 기반으로 합니다. 이러한 자격 증명은 입력을 사용 하 여 환경 변수는 클러스터 부트스트랩 시 프로 비전 `CONTROLLER_USERNAME` 고 `CONTROLLER_PASSWORD`입니다.
```

> [!NOTE]
> You must provide a password that is in compliance with [SQL Server password complexity requirements](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017).

## Next steps

To learn more about the SQL Server big data clusters, see the following overview:

- [What are SQL Server 2019 big data clusters?](big-data-cluster-overview.md)
