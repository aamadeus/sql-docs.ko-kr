---
title: 데이터베이스 스냅숏(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- static database views
- snapshots [SQL Server database snapshots]
- source databases [SQL Server]
- snapshots [SQL Server database snapshots], about database snapshots
- database snapshots [SQL Server]
- read-only database views
- database snapshots [SQL Server], about database snapshots
ms.assetid: 00179314-f23e-47cb-a35c-da6f180f86d3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 475a631c3155d116ef0530992503d3f7fd7cbfc2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213923"
---
# <a name="database-snapshots-sql-server"></a>데이터베이스 스냅숏(SQL Server)
  데이터베이스 스냅숏은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스(*원본 데이터베이스*)의 읽기 전용 정적 뷰입니다. 데이터베이스 스냅숏은 스냅숏을 만든 시점의 원본 데이터베이스와 트랜잭션이 일치합니다. 데이터베이스 스냅숏은 항상 원본 데이터베이스와 동일한 서버 인스턴스에 있습니다. 원본 데이터베이스가 업데이트되면 데이터베이스 스냅숏도 업데이트됩니다. 따라서 데이터베이스 스냅숏을 오래 보관할수록 사용 가능한 공간이 소모될 가능성이 높습니다.  
  
 지정된 원본 데이터베이스에 스냅숏이 여러 개 있을 수 있습니다. 각 데이터베이스 스냅숏은 데이터베이스 소유자가 명시적으로 삭제하기 전까지 유지됩니다.  
  
> [!NOTE]  
>  데이터베이스 스냅숏은 스냅숏 백업, 트랜잭션의 스냅숏 격리 또는 스냅숏 복제와 관련이 없습니다.  
  
 **항목 내용:**  
  
-   [기능 개요](#FeatureOverview)  
  
-   [데이터베이스 스냅숏의 이점](#Benefits)  
  
-   [용어 및 정의](#TermsAndDefinitions)  
  
-   [데이터베이스 스냅숏 사전 요구 사항 및 제한 사항](#LimitationsRequirements)  
  
-   [관련 작업](#RelatedTasks)  
  
##  <a name="FeatureOverview"></a> 기능 개요  
 데이터베이스 스냅숏은 데이터 페이지 수준에서 작동합니다. 원본 데이터베이스의 페이지를 처음 수정하기 전에 원본 페이지는 원본 데이터베이스에서 스냅숏으로 복사됩니다. 스냅숏은 원본 페이지를 저장하여 스냅숏이 만들어질 때 상태 그대로 데이터 레코드를 유지합니다. 처음 수정하는 모든 페이지에 같은 프로세스가 반복됩니다. 사용자에게 데이터베이스 스냅숏은 변경되지 않는 것으로 보입니다. 데이터베이스 스냅숏의 읽기 작업은 원본 데이터 페이지의 위치에 관계없이 항상 원본 데이터 페이지에 액세스하기 때문입니다.  
  
 복사된 원본 페이지를 저장하기 위해 스냅숏은 하나 이상의 *스파스 파일*을 사용합니다. 처음에 스파스 파일은 기본적으로 사용자 데이터가 없는 빈 파일이며 사용자 데이터에 대한 디스크 공간이 할당되어 있지 않습니다. 원본 데이터베이스에서 페이지를 업데이트할수록 파일 크기가 증가합니다. 다음 그림은 스냅숏 크기에 대한 두 가지 상반된 업데이트 패턴의 효과를 보여 줍니다. 업데이트 패턴 A는 스냅숏 수명 동안 원본 페이지의 30%가 업데이트되는 환경을 반영합니다. 업데이트 패턴 B는 스냅숏 수명 동안 원본 페이지의 80%가 업데이트되는 환경을 반영합니다.  
  
 ![대체 업데이트 패턴 및 스냅숏 크기](../../database-engine/media/dbview-04.gif "대체 업데이트 패턴 및 스냅숏 크기")  
  
##  <a name="Benefits"></a> 데이터베이스 스냅숏의 이점  
  
-   스냅숏은 보고 용도로 사용할 수 있습니다.  
  
     클라이언트는 데이터베이스 스냅숏을 쿼리할 수 있으며 이 기능은 스냅숏 생성 시의 데이터를 기준으로 보고서를 작성하는 데 유용합니다.  
  
-   보고서 생성을 위해 기록 데이터 유지 관리  
  
     스냅숏은 사용자 액세스를 특정 지정 시간의 데이터로 확장할 수 있습니다. 예를 들어 회계 분기와 같은 지정된 기간이 끝나는 시점에 데이터베이스 스냅숏을 만들어 향후 보고 시 사용할 수 있습니다. 그런 다음 스냅숏을 통해 기말 보고서를 실행할 수 있습니다. 또한 디스크 공간이 충분하다면 기말 스냅숏을 무제한 보관하여 조직 성과 조사 등의 목적을 위해 해당 기간의 결과를 대상으로 쿼리할 수 있습니다.  
  
-   가용성 목적으로 유지 관리 중인 미러 데이터베이스를 활용하여 보고 작업 오프로드  
  
     데이터베이스 스냅숏을 데이터베이스 미러링에 사용하면 보고를 위해 미러 서버의 데이터에 액세스할 수 있습니다. 또한 미러 데이터베이스에서 쿼리를 실행하면 주 데이터베이스의 리소스를 확보할 수 있습니다. 자세한 내용은 [데이터베이스 미러링 및 데이터베이스 스냅숏&#40;SQL Server&#41;](database-snapshots-sql-server.md)을 사용합니다.  
  
-   관리 오류로부터 데이터 보호  
  
-   원본 데이터베이스에서 사용자 오류가 발생할 경우 지정된 데이터베이스 스냅숏을 생성했을 때의 상태로 원본 데이터베이스를 되돌릴 수 있습니다. 데이터 손실은 스냅숏 생성 이후의 데이터베이스 업데이트로 제한됩니다.  
  
     예를 들어 대량 업데이트 또는 스키마 변경과 같은 주요 업데이트를 수행하기 전에 데이터베이스에 데이터베이스 스냅숏을 만들어 데이터를 보호합니다. 오류가 발생하면 스냅숏을 사용하여 데이터베이스를 해당 스냅숏으로 되돌려 복구할 수 있습니다. 이러한 용도에는 백업에서 복원하는 것보다 되돌리는 것이 훨씬 빠를 가능성이 높지만 되돌린 시점 이후로는 롤포워드할 수 없습니다.  
  
    > [!IMPORTANT]  
    >  오프라인 또는 손상된 데이터베이스에서는 되돌릴 수 없습니다. 따라서 데이터베이스를 보호하려면 정기적으로 백업하고 복원 계획을 테스트해야 합니다.  
  
    > [!NOTE]  
    >  데이터베이스 스냅숏은 원본 데이터베이스에 따라 달라집니다. 따라서 데이터베이스 스냅숏을 사용하여 데이터베이스를 되돌리는 기능은 백업 및 복원 전략을 대체하지 않습니다. 예약된 백업 일정도 반드시 수행해야 합니다. 데이터베이스 스냅숏을 만든 시점까지 원본 데이터베이스를 복원해야 하는 경우 이 작업을 수행할 수 있는 백업 정책을 구현합니다.  
  
-   사용자 오류로부터 데이터 보호  
  
     정기적으로 데이터베이스 스냅숏을 만들면 테이블 삭제와 같은 주요 사용자 오류의 영향을 줄일 수 있습니다. 철저한 보호를 위해 충분한 기간에 걸쳐 일련의 데이터베이스 스냅숏을 만들어 대부분의 사용자 오류를 찾아내고 이에 대처할 수 있습니다. 예를 들어 디스크 리소스에 따라 24시간 간격으로 6개에서 12개 사이의 연속된 스냅숏을 유지 관리할 수 있습니다. 그러면 새 스냅숏이 생성될 때마다 가장 오래된 스냅숏을 삭제할 수 있습니다.  
  
    -   사용자 오류로부터 복구하려면 오류 발생 직전의 스냅숏으로 데이터베이스를 되돌리면 됩니다. 이러한 용도에는 백업에서 복원하는 것보다 되돌리는 것이 훨씬 빠를 가능성이 높지만 되돌린 시점 이후로는 롤포워드할 수 없습니다.  
  
    -   또는 스냅숏의 정보를 사용하여 삭제된 테이블이나 그 밖의 손실된 데이터를 직접 다시 만들 수 있습니다. 예를 들어 스냅숏의 데이터를 데이터베이스로 대량 복사하고 이 데이터를 데이터베이스에 직접 다시 병합할 수 있습니다.  
  
    > [!NOTE]  
    >  데이터베이스 스냅숏의 사용 목적에 따라 데이터베이스에 필요한 동시 스냅숏의 수, 새 스냅숏 생성 간격 및 보관 기간이 결정됩니다.  
  
-   테스트 데이터베이스 관리  
  
     테스트 환경에서 테스트 프로토콜을 반복 실행하는 경우 각 테스트 시작 시 데이터베이스에 동일한 데이터가 있는 것이 유용할 수 있습니다. 첫 번째 테스트를 실행하기 전에 응용 프로그램 개발자나 테스터는 테스트 데이터베이스에서 데이터베이스 스냅숏을 만들 수 있습니다. 각 테스트를 실행한 후 데이터베이스 스냅숏을 되돌리면 신속하게 데이터베이스를 이전 상태로 되돌릴 수 있습니다.  
  
##  <a name="TermsAndDefinitions"></a> 용어 및 정의  
 database snapshot  
 데이터베이스(원본 데이터베이스)의 트랜잭션이 일치하는 읽기 전용 정적 뷰입니다.  
  
 원본 데이터베이스  
 데이터베이스 스냅숏의 경우 스냅숏이 만들어진 데이터베이스입니다. 데이터베이스 스냅숏은 원본 데이터베이스에 따라 달라집니다. 데이터베이스 스냅숏은 데이터베이스와 동일한 서버 인스턴스에 있어야 합니다. 또한 어떤 이유에서든 데이터베이스를 사용할 수 없게 되면 해당 데이터베이스 스냅숏도 모두 사용할 수 없습니다.  
  
 스파스 파일(sparse file)  
 NTFS 파일 시스템에서 제공하는 파일로, 다른 경우보다 훨씬 더 적은 디스크 공간만 사용합니다. 스파스 파일은 데이터베이스 스냅숏에 복사된 페이지를 저장하는 데 사용됩니다. 스파스 파일은 처음 만들어질 때 디스크 공간을 거의 차지하지 않습니다. 데이터베이스 스냅숏에 데이터를 쓸수록 NTFS는 해당하는 스파스 파일에 점진적으로 디스크 공간을 할당합니다.  
  
##  <a name="LimitationsRequirements"></a> 데이터베이스 스냅숏 사전 요구 사항 및 제한 사항  
 **섹션 내용**  
  
-   [필수 구성 요소](#Prerequisites)  
  
-   [원본 데이터베이스에 대한 제한 사항](#LimitsOnSourceDb)  
  
-   [데이터베이스 스냅숏에 대한 제한 사항](#LimitsOnDbSS)  
  
-   [디스크 공간 요구 사항](#DiskSpace)  
  
-   [오프라인 파일 그룹의 데이터베이스 스냅숏](#OfflineFGs)  
  
###  <a name="Prerequisites"></a> 사전 요구 사항  
 복구 모델을 사용할 수 있는 원본 데이터베이스는 다음 사전 요구 사항을 충족해야 합니다.  
  
-   서버 인스턴스는 데이터베이스 스냅숏을 지원하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 버전을 실행해야 합니다. 자세한 내용은 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.  
  
-   데이터베이스 미러링 세션의 미러 데이터베이스가 아닌 경우 원본 데이터베이스는 온라인 상태여야 합니다.  
  
-   가용성 그룹의 주 데이터베이스 또는 보조 데이터베이스에서 데이터베이스 스냅숏을 만들 수 있습니다. 복제본 역할은 RESOLVING 상태가 아닌 PRIMARY 또는 SECONDARY 상태여야 합니다.  
  
     데이터베이스 동기화 상태가 SYNCHRONIZING 또는 SYNCHRONIZED인 상태에서 데이터베이스 스냅숏을 만드는 것이 좋습니다. 데이터베이스 동기화 상태가 NOT SYNCHRONIZING인 경우에도 데이터베이스 스냅숏을 만들 수는 있습니다.  
  
     자세한 내용은 [AlwaysOn 가용성 그룹이 있는 데이터베이스 스냅숏&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/database-snapshots-with-always-on-availability-groups-sql-server.md)을 참조하세요.  
  
-   미러 데이터베이스에서 데이터베이스 스냅숏을 만들려면 데이터베이스가 SYNCHRONIZED 미러링 상태여야 합니다.  
  
-   원본 데이터베이스는 확장 가능한 공유 데이터베이스로 구성할 수 없습니다.  
  
> [!NOTE]  
>  모든 복구 모델에서 데이터베이스 스냅숏을 지원합니다.  
  
###  <a name="LimitsOnSourceDb"></a> 원본 데이터베이스에 대한 제한 사항  
 데이터베이스 스냅숏이 있는 경우 스냅숏의 원본 데이터베이스에 다음 제한 사항이 적용됩니다.  
  
-   데이터베이스를 삭제, 분리 또는 복원할 수 없습니다.  
  
    > [!NOTE]  
    >  원본 데이터베이스의 백업은 정상적으로 수행되며 데이터베이스 스냅숏의 영향을 받지 않습니다.  
  
-   페이지가 업데이트될 때마다 스냅숏에 대한 쓰기 시 복사 작업으로 인해 원본 데이터베이스의 I/O가 증가하여 성능이 저하됩니다.  
  
-   원본 데이터베이스 또는 모든 스냅숏에서 파일을 삭제할 수 없습니다.  
  
###  <a name="LimitsOnDbSS"></a> 데이터베이스 스냅숏에 대한 제한 사항  
 데이터베이스 스냅숏에 다음 제한 사항이 적용됩니다.  
  
-   데이터베이스 스냅숏은 원본 데이터베이스와 같은 서버 인스턴스에서 생성 및 유지되어야 합니다.  
  
-   데이터베이스 스냅숏은 항상 전체 데이터베이스에 대해 작동합니다.  
  
-   데이터베이스 스냅숏은 원본 데이터베이스에 따라 달라지며 중복 저장소가 아닙니다. 데이터베이스 스냅숏은 디스크 오류나 다른 유형의 손상을 방지하지 못합니다. 따라서 데이터베이스 스냅숏을 사용하여 데이터베이스를 되돌리는 기능은 백업 및 복원 전략을 대체하지 않습니다. 예약된 백업 일정도 반드시 수행해야 합니다. 데이터베이스 스냅숏을 만든 시점까지 원본 데이터베이스를 복원해야 하는 경우 이 작업을 수행할 수 있는 백업 정책을 구현합니다.  
  
-   원본 데이터베이스에서 업데이트되는 페이지를 스냅숏으로 밀어넣을 때 스냅숏이 디스크 공간을 모두 소모했거나 다른 오류가 발생한 경우 스냅숏이 주의 대상이 되어 삭제해야 합니다.  
  
-   스냅숏은 읽기 전용입니다. 읽기 전용이므로 업그레이드할 수 없습니다. 따라서 업그레이드 후 데이터베이스 스냅숏은 표시되지 않습니다.  
  
-   **model**, **master**및 **tempdb** 데이터베이스의 스냅숏은 금지됩니다.  
  
-   데이터베이스 스냅숏 파일의 사양을 변경할 수 없습니다.  
  
-   데이터베이스 스냅숏에서 파일을 삭제할 수 없습니다.  
  
-   데이터베이스 스냅숏은 백업 또는 복원할 수 없습니다.  
  
-   데이터베이스 스냅숏은 연결 또는 분리할 수 없습니다.  
  
-   FAT32 파일 시스템 또는 RAW 파티션에 데이터베이스 스냅숏을 만들 수 없습니다. 데이터베이스 스냅숏에 사용되는 스파스 파일은 NTFS 파일 시스템에서 제공합니다.  
  
-   데이터베이스 스냅숏에서는 전체 텍스트 인덱싱이 지원되지 않습니다. 전체 텍스트 카탈로그가 원본 데이터베이스로부터 전파되지 않습니다.  
  
-   데이터베이스 스냅숏은 스냅숏을 만든 시점의 원본 데이터베이스의 보안 제약 조건을 상속합니다. 스냅숏은 읽기 전용이므로 상속된 사용 권한을 변경할 수 없으며 원본의 사용 권한을 변경해도 기존의 스냅숏은 영향을 받지 않습니다.  
  
-   스냅숏은 항상 스냅숏을 만든 시점의 파일 그룹 상태를 반영합니다. 즉, 온라인 파일 그룹은 온라인 상태를 유지하고 오프라인 파일 그룹은 오프라인 상태를 유지합니다. 자세한 내용은 이 항목 뒷부분의 "오프라인 파일 그룹의 데이터베이스 스냅숏"을 참조하세요.  
  
-   원본 데이터베이스가 RECOVERY_PENDING이 되면 해당 데이터베이스 스냅숏에 액세스하지 못할 수도 있습니다. 그러나 원본 데이터베이스의 문제가 해결되면 스냅숏을 다시 사용할 수 있습니다.  
  
-   압축된 파일 그룹과 읽기 전용 파일 그룹은 되돌리기가 지원되지 않습니다. 두 유형의 파일 그룹 중 하나가 포함된 데이터베이스를 되돌리려고 하면 작업이 실패합니다.  
  
-   로그 전달 구성에서는 보조 데이터베이스가 아닌 주 데이터베이스에서만 데이터베이스 스냅숏을 만들 수 있습니다. 주 서버 인스턴스와 보조 서버 인스턴스의 역할을 전환하는 경우 주 데이터베이스를 보조 데이터베이스로 설정하려면 먼저 모든 데이터베이스 스냅숏을 삭제해야 합니다.  
  
-   데이터베이스 스냅숏은 확장 가능한 공유 데이터베이스로 구성할 수 없습니다.  
  
-   FILESTREAM 파일 그룹은 데이터베이스 스냅숏에서 지원되지 않습니다. FILESTREAM 파일 그룹이 원본 데이터베이스에 있으면 해당 데이터베이스 스냅숏에서 이 파일 그룹이 오프라인 상태로 표시되고 데이터베이스를 되돌리는 데 데이터베이스 스냅숏을 사용할 수 없습니다.  
  
    > [!NOTE]  
    >  데이터베이스 스냅숏에 대해 실행되는 SELECT 문에는 FILESTREAM 열을 지정하지 말아야 합니다. 그렇지 않으면 다음 오류 메시지가 반환됩니다. `Could not continue scan with NOLOCK due to data movement.`  
  
-   읽기 전용 스냅숏에 대한 통계가 없거나 유효하지 않을 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 tempdb에서 임시 통계를 만들어 유지 관리합니다. 자세한 내용은 [Statistics](../statistics/statistics.md)을(를) 참조하세요.  
  
###  <a name="DiskSpace"></a> 디스크 공간 요구 사항  
 데이터베이스 스냅숏은 디스크 공간을 사용합니다. 데이터베이스 스냅숏이 디스크 공간을 모두 소모하면 스냅숏이 주의 대상으로 표시되어 삭제해야 합니다. 그러나 원본 데이터베이스는 영향을 받지 않으며 정상적으로 동작이 계속됩니다. 그러나 데이터베이스의 전체 복사본과 비교할 때 스냅숏은 공간을 매우 효율적으로 사용합니다. 스냅숏은 사용 기간 동안 변경되는 페이지를 저장할 수 있는 공간만 필요로 합니다. 일반적으로 스냅숏은 제한된 시간 동안 보관되므로 크기는 중요한 문제가 아닙니다.  
  
 그러나 스냅숏을 오래 보관할수록 사용 가능한 공간을 모두 소모할 가능성이 높습니다. 스파스 파일이 커질 수 있는 최대 크기는 스냅숏을 만든 시점의 해당 원본 데이터베이스 파일의 크기입니다.  
  
 데이터베이스 스냅숏이 디스크 공간을 모두 소모한 경우 스냅숏을 삭제해야 합니다.  
  
> [!NOTE]  
>  파일 공간을 제외하고 데이터베이스 스냅숏은 대략 데이터베이스와 같은 양의 리소스를 사용합니다.  
  
###  <a name="OfflineFGs"></a> 오프라인 파일 그룹의 데이터베이스 스냅숏  
 원본 데이터베이스의 오프라인 파일 그룹은 다음 작업을 수행하려 할 때 데이터베이스 스냅숏에 영향을 줍니다.  
  
-   스냅숏 만들기  
  
     원본 데이터베이스에 하나 이상의 오프라인 파일 그룹이 있는 경우 오프라인 파일 그룹의 스냅숏 만들기가 성공합니다. 오프라인 파일 그룹의 경우 스파스 파일이 생성되지 않습니다.  
  
-   파일 그룹을 오프라인 상태로 만들기  
  
     원본 데이터베이스에서 파일 그룹을 오프라인 상태로 만들 수 있습니다. 그러나 스냅숏을 만들 때 온라인 상태였던 파일 그룹은 데이터베이스 스냅숏에서 온라인 상태를 유지합니다. 스냅숏을 만든 후 쿼리한 데이터가 변경된 경우 스냅숏에서 해당 원본 데이터 페이지에 액세스할 수 있습니다. 그러나 스냅숏을 사용하여 파일 그룹의 수정되지 않은 데이터에 액세스하는 쿼리는 입출력 오류로 인해 실패할 수 있습니다.  
  
-   파일 그룹을 온라인 상태로 만들기  
  
     데이터베이스 스냅숏이 있는 데이터베이스의 파일 그룹은 온라인 상태로 만들 수 없습니다. 스냅숏 생성 시 파일 그룹이 오프라인 상태이거나 데이터베이스 스냅숏이 있는 동안 오프라인 상태로 만들면 이 파일 그룹은 계속 오프라인 상태로 유지됩니다. 이는 파일을 다시 온라인 상태로 만들려면 파일을 복원해야 하는데, 데이터베이스에 데이터베이스 스냅숏이 있을 경우 복원할 수 없기 때문입니다.  
  
-   원본 데이터베이스를 스냅숏으로 되돌리기  
  
     원본 데이터베이스를 데이터베이스 스냅숏으로 되돌리려면 스냅숏을 만들 때 오프라인 상태였던 파일 그룹을 제외하고 모든 파일 그룹이 온라인 상태여야 합니다.  
  
##  <a name="RelatedTasks"></a> 관련 태스크  
  
-   [데이터베이스 스냅숏 만들기&#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md)  
  
-   [데이터베이스 스냅숏 보기&#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md)  
  
-   [데이터베이스 스냅숏 스파스 파일의 크기 보기&#40;Transact-SQL&#41;](view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md)  
  
-   [데이터베이스를 데이터베이스 스냅숏으로 되돌리기](revert-a-database-to-a-database-snapshot.md)  
  
-   [데이터베이스 스냅숏 삭제&#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 미러링 및 데이터베이스 스냅숏&#40;SQL Server&#41;](database-snapshots-sql-server.md)  
  
  
