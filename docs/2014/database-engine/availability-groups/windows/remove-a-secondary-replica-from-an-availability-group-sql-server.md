---
title: 가용성 그룹에서 보조 복제본 제거(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.availabilitygroup.removesecondaryar.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], configuring
ms.assetid: 35ddc8b6-3e7c-4417-9a0a-d4987a09ddf7
caps.latest.revision: 35
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: 8dd0df4b298c998d5697a43b04a0a892541be87f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36183106"
---
# <a name="remove-a-secondary-replica-from-an-availability-group-sql-server"></a>가용성 그룹에서 보조 복제본 제거(SQL Server)
  이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[tsql](../../../includes/tsql-md.md)], [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]또는 PowerShell을 사용하여 AlwaysOn 가용성 그룹에서 보조 복제본을 제거하는 방법에 대해 설명합니다.  
  
-   **시작하기 전 주의 사항:**  
  
     [제한 사항](#Restrictions)  
  
     [필수 구성 요소](#Prerequisites)  
  
     [보안](#Security)  
  
-   **보조 복제본을 제거하려면:**  
  
     다른 도구는 [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **후속 작업:**  [보조 복제본을 제거한 후](#PostBestPractices)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Restrictions"></a> 제한 사항  
  
-   이 태스크는 주 복제본에서만 지원됩니다.  
  
-   가용성 그룹에서는 보조 복제본만 제거할 수 있습니다.  
  
###  <a name="Prerequisites"></a> 사전 요구 사항  
  
-   가용성 그룹의 주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> Permissions  
 가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
 **보조 복제본을 제거하려면**  
  
1.  개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.  
  
2.  **AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.  
  
3.  가용성 그룹을 선택하고 **가용성 복제본** 노드를 확장합니다.  
  
4.  이 단계는 여러 복제본을 제거할지 아니면 복제본을 하나만 제거할지에 따라 다음과 같이 달라집니다.  
  
    -   여러 복제본을 제거하려면 **개체 탐색기 정보** 창을 사용하여 제거할 모든 복제본을 표시하고 선택합니다. 자세한 내용은 [개체 탐색기 정보를 사용하여 가용성 그룹 모니터링&#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)을 참조하세요.  
  
    -   단일 복제본을 제거하려면 **개체 탐색기** 창 또는 **개체 탐색기 정보** 창에서 복제본을 선택합니다.  
  
5.  선택한 보조 복제본을 마우스 오른쪽 단추로 클릭하고 명령 메뉴에서 **가용성 그룹에서 제거** 를 선택합니다.  
  
6.  **가용성 그룹에서 보조 복제본 제거** 대화 상자에서 나열된 보조 복제본을 모두 제거하려면 **확인**을 클릭합니다. 나열된 모든 복제본을 제거하지 않으려면 **취소**를 클릭합니다.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
 **보조 복제본을 제거하려면**  
  
1.  주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.  
  
2.  다음과 같은 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 문을 사용합니다.  
  
     ALTER AVAILABILITY GROUP *group_name* REMOVE REPLICA ON '*instance_name*' [,...*n*]  
  
     여기서 *group_name* 은 가용성 그룹의 이름이고 *instance_name* 은 보조 복제본이 있는 서버 인스턴스입니다.  
  
     다음 예에서는 *MyAG* 가용성 그룹에서 보조 복제본을 제거합니다. 대상 보조 복제본은 *COMPUTER02* 라는 컴퓨터에서 *HADR_INSTANCE*라는 서버 인스턴스에 있습니다.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG REMOVE REPLICA ON 'COMPUTER02\HADR_INSTANCE';  
    ```  
  
##  <a name="PowerShellProcedure"></a> PowerShell 사용  
 **보조 복제본을 제거하려면**  
  
1.  주 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.  
  
2.  **Remove-SqlAvailabilityReplica** cmdlet을 사용합니다.  
  
     예를 들어 다음 명령은 `MyReplica` 라는 가용성 그룹에서 `MyAg`서버의 가용성 복제본을 제거합니다.  이 명령은 가용성 그룹의 주 복제본을 호스팅하는 서버 인스턴스에서 실행해야 합니다.  
  
    ```  
    Remove-SqlAvailabilityReplica `   
    -Path SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Cmdlet의 구문을 보려면에서 사용 하 여는 `Get-Help` cmdlet에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 환경입니다. 자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.  
  
 **SQL Server PowerShell 공급자를 설정하고 사용하려면**  
  
-   [SQL Server PowerShell 공급자](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="PostBestPractices"></a> 후속 작업: 보조 복제본을 제거한 후  
 현재 사용할 수 없는 복제본을 지정할 경우 복제본이 온라인 상태가 될 때 제거되었음을 확인할 수 있습니다.  
  
 복제본을 제거하면 데이터 수신이 중지됩니다. 보조 복제본이 글로벌 상점에서 제거되었음을 확인한 후 이 복제본은 RECOVERING 상태에서 로컬 서버 인스턴스에 남아 있는 가용성 그룹 설정을 데이터베이스에서 제거합니다.  
  
## <a name="see-also"></a>관련 항목  
 [AlwaysOn 가용성 그룹 개요 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)   
 [가용성 그룹 제거&#40;SQL Server&#41;](remove-an-availability-group-sql-server.md)  
  
  