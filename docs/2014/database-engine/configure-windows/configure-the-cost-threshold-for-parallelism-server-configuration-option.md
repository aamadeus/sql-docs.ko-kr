---
title: cost threshold for parallelism 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- cost threshold for parallelism option
ms.assetid: dad21bee-fe28-41f6-9d2f-e6ababfaf9db
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fd36b02c43dadb7bd6cd5206b36d3db3bcd04eb3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190383"
---
# <a name="configure-the-cost-threshold-for-parallelism-server-configuration-option"></a>cost threshold for parallelism 서버 구성 옵션 구성
  이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 병렬 처리에 대한 비용 임계값 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다. **cost threshold for parallelism** 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 쿼리에 대한 병렬 계획을 만들고 실행하는 임계값을 지정합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 동일한 쿼리의 직렬 계획을 실행하는 데 드는 예상 비용이 **병렬 처리에 대한 비용 임계값**에 설정된 값보다 높은 경우에만 해당 쿼리에 대한 병렬 계획을 만들고 실행합니다. 이 비용은 특정 하드웨어 구성에서 직렬 계획을 실행하는 데 필요한 예상 경과 시간(초)을 참조합니다. **병렬 처리에 대한 비용 임계값** 옵션은 0에서 32767 사이의 모든 값으로 설정할 수 있으며 기본값은 5입니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [제한 사항](#Restrictions)  
  
     [권장 사항](#Recommendations)  
  
     [보안](#Security)  
  
-   **병렬 처리에 대한 비용 임계값 옵션을 구성하려면:**  
  
     다른 도구는 [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **속 작업:**  [병렬 처리에 대한 비용 임계값 옵션을 구성한 후](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Restrictions"></a> 제한 사항  
  
-   이 비용은 특정 하드웨어 구성에서 직렬 계획을 실행하는 데 필요한 예상 경과 시간(초)을 참조합니다. **cost threshold for parallelism** 은 대칭적 다중 프로세서에서만 설정해야 합니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 다음 조건에서 **병렬 처리에 대한 비용 임계값** 값을 무시합니다.  
  
    -   컴퓨터에 논리적 프로세서가 하나만 있습니다.  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 선호도 마스크 **구성 옵션 때문에** 에 단일 논리적 프로세서만 사용할 수 있습니다.  
  
    -   **병렬 처리에 대한 비용 임계값** 옵션이 1로 설정되어 있습니다.  
  
 논리적 프로세서는 운영 체제가 태스크를 전달하거나 스레드 컨텍스트를 실행할 수 있도록 허용하는 프로세서 하드웨어의 기본 단위입니다. 각 논리적 프로세서는 한 번에 하나만 스레드 컨텍스트를 실행할 수 있습니다. 프로세서 코어는 명령을 암호 해독하고 실행할 수 있는 기능을 제공하는 회로입니다. 프로세서 코어에는 하나 이상의 논리적 프로세서가 포함될 수 있습니다. 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리를 사용하면 시스템의 CPU 정보를 가져올 수 있습니다.  
  
```  
SELECT (cpu_count / hyperthread_ratio) AS PhysicalCPUs,   
cpu_count AS logicalCPUs   
FROM sys.dm_os_sys_info  
```  
  
###  <a name="Recommendations"></a> 권장 사항  
  
-   이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.  
  
-   경우에 따라 쿼리 비용 계획이 현재 **병렬 처리에 대한 비용 임계값** 값보다 작아도 병렬 계획을 선택할 수 있습니다. 이는 먼저 제공되는 비용 평가에 따라 병렬 계획 또는 직렬 계획을 사용할 것인지를 결정해야 전체 최적화가 완료되기 때문입니다.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> Permissions  
 매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다. 구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다. **sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-configure-the-cost-threshold-for-parallelism-option"></a>병렬 처리에 대한 비용 임계값 옵션을 구성하려면  
  
1.  개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.  
  
2.  **고급** 노드를 클릭합니다.  
  
3.  **병렬 처리**에서 **병렬 처리에 대한 비용 임계값** 옵션을 원하는 값으로 변경합니다. 0에서 32767까지의 값을 입력 또는 선택합니다.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
  
#### <a name="to-configure-the-cost-threshold-for-parallelism-option"></a>병렬 처리에 대한 비용 임계값 옵션을 구성하려면  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다. 다음 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `cost threshold for parallelism` 옵션의 값을 `10`(으)로 설정하는 방법을 보여 줍니다.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cost threshold for parallelism', 10 ;  
GO  
RECONFIGURE  
GO  
```  
  
 자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.  
  
##  <a name="FollowUp"></a> 후속 작업: 병렬 처리에 대한 비용 임계값 옵션을 구성한 후  
 이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [병렬 인덱스 작업 구성](../../relational-databases/indexes/configure-parallel-index-operations.md)   
 [쿼리 힌트&#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query)   
 [ALTER WORKLOAD GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql)   
 [affinity mask 서버 구성 옵션](affinity-mask-server-configuration-option.md)   
 [RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
