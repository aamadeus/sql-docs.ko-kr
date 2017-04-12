---
title: "Always On 정책을 사용하여 가용성 그룹의 상태 보기(SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "가용성 그룹 [SQL Server], 정책"
ms.assetid: 6f1bcbc3-1220-4071-8e53-4b957f5d3089
caps.latest.revision: 17
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 16
---
# Always On 정책을 사용하여 가용성 그룹의 상태 보기(SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]의 Always On 정책 또는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 PowerShell을 사용하여 Always On 가용성 그룹의 작동 상태를 확인하는 방법에 대해 설명합니다. Always On 정책 기반 관리에 대한 자세한 내용은 [Always On 가용성 그룹의 운영 문제에 대한 Always On 정책&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always on policies for operational issues - always on availability.md)을 참조하세요.  
  
> [!IMPORTANT]  
>  Always On 정책의 경우 범주 이름이 ID로 사용됩니다. Always On 범주의 이름을 변경하면 상태 평가 기능이 작동하지 않으므로 따라서 Always On 범주의 이름을 수정해서는 안 됩니다.  
  
-   **시작하기 전 주의 사항:** [보안](#Security)  
  
-   **Always On 정책을 사용하여 가용성 그룹의 상태를 보려면:**  
  
     [Always On 대시보드](#SSMSProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> 사용 권한  
 연결, 서버 상태 보기 및 모든 정의 보기 권한이 필요합니다.  
  
##  <a name="SSMSProcedure"></a> Always On 대시보드 사용  
 **Always On 대시보드를 열려면**  
  
1.  개체 탐색기에서 가용성 복제본 중 하나를 호스팅하는 서버 인스턴스에 연결합니다. 가용성 그룹의 모든 가용성 복제본에 대한 정보를 보려면 주 복제본을 호스팅하는 서버 인스턴스를 사용합니다.  
  
2.  서버 이름을 클릭하여 서버 트리를 확장합니다.  
  
3.  **Always On 고가용성** 노드를 확장합니다.  
  
     **가용성 그룹**을 마우스 오른쪽 단추로 클릭하거나 이 노드를 확장하고 특정 가용성 그룹을 마우스 오른쪽 단추로 클릭합니다.  
  
4.  **대시보드 표시** 명령을 선택합니다.  
  
 Always On 대시보드를 사용하는 방법은 [Always On 대시보드 사용&#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)을 참조하세요.  
  
##  <a name="PowerShellProcedure"></a> PowerShell 사용  
 **Always On 정책을 사용하여 가용성 그룹의 상태 보기**  
  
1.  가용성 복제본 중 하나를 호스트하는 서버 인스턴스로 기본값을 설정(**cd**)합니다. 가용성 그룹의 모든 가용성 복제본에 대한 정보를 보려면 주 복제본을 호스팅하는 서버 인스턴스를 사용합니다.  
  
2.  다음 cmdlet을 사용합니다.  
  
     **Test-SqlAvailabilityGroup**  
     SQL Server PBM(정책 기반 관리) 정책을 평가하여 가용성 그룹의 상태를 평가합니다. 이 cmdlet을 실행하려면 연결, 서버 상태 보기 및 모든 정의 보기 권한이 있어야 합니다.  
  
     예를 들어 다음 명령은 서버 인스턴스 `Computer\Instance`에서 상태가 "오류"인 모든 가용성 그룹을 보여 줍니다.  
  
    ```  
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups `   
    | Test-SqlAvailabilityGroup | Where-Object { $_.HealthState -eq "Error" }  
    ```  
  
     **Test-SqlAvailabilityReplica**  
     SQL Server PBM(정책 기반 관리) 정책을 평가하여 가용성 복제본의 상태를 평가합니다. 이 cmdlet을 실행하려면 연결, 서버 상태 보기 및 모든 정의 보기 권한이 있어야 합니다.  
  
     예를 들어 다음 명령은 `MyReplica` 가용성 그룹에서 `MyAg`라는 가용성 복제본의 상태를 평가하고 간단한 요약을 출력합니다.  
  
    ```  
    Test-SqlAvailabilityReplica `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
     **Test-SqlDatabaseReplicaState**  
     SQL Server PBM(정책 기반 관리) 정책을 평가하여 모든 조인된 가용성 복제본에 대한 가용성 데이터베이스 상태를 평가합니다.  
  
     예를 들어 다음 명령은 `MyAg` 가용성 그룹에서 모든 가용성 데이터베이스의 상태를 평가하고 각 데이터베이스에 대해 간단한 요약을 출력합니다.  
  
    ```  
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\DatabaseReplicaStates `   
     | Test-SqlDatabaseReplicaState  
    ```  
  
     이러한 cmdlet은 다음 옵션을 사용합니다.  
  
    |옵션|설명|  
    |------------|-----------------|  
    |**AllowUserPolicies**|Always On 정책 범주에 있는 사용자 정책을 실행합니다.|  
    |**InputObject**|사용 중인 cmdlet에 따라 가용성 그룹, 가용성 복제본 또는 가용성 데이터베이스 상태를 나타내는 개체 모음입니다. cmdlet은 지정된 개체의 상태를 계산합니다.|  
    |**NoRefresh**|이 매개 변수를 설정한 경우 cmdlet은 **-Path** 또는 **-InputObject** 매개 변수에 지정된 개체를 수동으로 새로 고치지 않습니다.|  
    |**경로**|사용 중인 cmdlet에 따라 가용성 그룹의 경로, 하나 이상의 가용성 복제본 또는 가용성 데이터베이스의 데이터베이스 복제본 클러스터 상태입니다. 선택적 매개 변수입니다. 지정하지 않으면 이 매개 변수의 값은 기본적으로 현재 작업 위치입니다.|  
    |**ShowPolicyDetails**|이 cmdlet에서 수행하는 각 정책 평가의 결과를 표시합니다. cmdlet은 정책 평가당 하나의 개체를 출력하며, 이 개체에는 평가 결과(정책 통과 여부, 정책 이름과 범주 등)를 설명하는 필드가 있습니다.|  
  
     예를 들어 다음 **Test-SqlAvailabilityGroup** 명령은 **-ShowPolicyDetails** 매개 변수를 지정하고 `MyAg`라는 가용성 그룹에서 실행된 각 PBM(정책 기반 관리) 정책에 대해 이 cmdlet에서 수행한 정책 평가 결과를 각각 표시합니다.  
  
    ```  
    Test-SqlAvailabilityGroup `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\AgName `  
    -ShowPolicyDetails  
  
    ```  
  
    > [!NOTE]  
    >  cmdlet의 구문을 보려면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 환경에서 **Get-Help** cmdlet을 사용합니다. 자세한 내용은 [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md)을 참조하세요.  
  
 **SQL Server PowerShell 공급자를 설정하고 사용하려면**  
  
-   [SQL Server PowerShell 공급자](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
-   [SQL Server PowerShell 도움말 보기](../../../relational-databases/scripting/get-help-sql-server-powershell.md)  
  
##  <a name="RelatedContent"></a> 관련 내용  
 **SQL Server Always On 팀 블로그—PowerShell을 사용하여 Always On 상태 모니터링:**  
  
-   [1부: 기본 Cmdlet 개요](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/13/monitoring-Always%20On-health-with-powershell-part-1.aspx)  
  
-   [2부: 고급 Cmdlet 사용](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/13/monitoring-Always%20On-health-with-powershell-part-2.aspx)  
  
-   [3부: 간단한 모니터링 응용 프로그램](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/15/monitoring-Always%20On-health-with-powershell-part-3.aspx)  
  
-   [4부: SQL Server 에이전트와의 통합](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/15/the-always-on-health-model-part-4.aspx)  
  
## 참고 항목  
 [Always On 가용성 그룹 개요&#40;SQL Server&#41;](../Topic/Overview%20of%20Always On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [가용성 그룹 관리&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/administration-of-an-availability-group-sql-server.md)   
 [가용성 그룹 모니터링&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/monitoring-of-availability-groups-sql-server.md)   
 [Always On 가용성 그룹의 운영 문제에 대한 Always On 정책&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always on policies for operational issues - always on availability.md)  
  
  