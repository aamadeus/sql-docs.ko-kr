---
title: "데이터베이스 미러링 모니터 개요 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.dbmmonitor.main.f1"
helpviewer_keywords: 
  - "데이터베이스 미러링 모니터 [SQL Server], 인터페이스"
ms.assetid: 8ebbdcd6-565a-498f-b674-289c84b985eb
caps.latest.revision: 40
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 40
---
# 데이터베이스 미러링 모니터 개요
  올바른 사용 권한이 있는 경우 데이터베이스 미러링 모니터를 사용하여 서버 인스턴스에 있는 미러된 데이터베이스의 모든 하위 집합을 모니터링할 수 있습니다. 모니터링을 사용하면 데이터베이스 미러링 세션에서 데이터가 제대로 흐르고 있는지 확인할 수 있습니다. 또한 데이터베이스 미러링 모니터는 데이터 흐름 감소의 원인을 해결하는 데 도움이 됩니다.  
  
 각 장애 조치(Failover) 파트너에서 개별적으로 모니터링하기 위해 미러된 데이터베이스를 등록할 수 있습니다. 데이터베이스를 등록하면 데이터베이스 미러링 모니터는 데이터베이스에 대한 다음 정보를 캐시합니다.  
  
-   데이터베이스 이름  
  
-   두 파트너 서버 인스턴스의 이름  
  
-   각 파트너의 마지막으로 알려진 역할(주 서버 또는 미러 서버)  
  
## 사용 권한  
 데이터베이스 미러링을 모니터링하려면 서버 인스턴스의 **msdb** 데이터베이스에서 **sysadmin** 고정 서버 역할 또는 **dbm_monitor** 고정 데이터베이스 역할의 멤버여야 합니다. 파트너 서버 인스턴스 중 하나에서만 **sysadmin** 또는 **dbm_monitor**의 멤버인 경우 모니터는 해당 파트너에만 연결될 수 있습니다. 즉, 모니터는 다른 파트너에서 정보를 검색할 수 없습니다.  
  
 서버 인스턴스에서 **dbm_monitor**의 멤버인 경우에만 해당 서버 인스턴스에서 제한된 사용 권한을 갖게 됩니다. 사용자는 최신 상태 행만 볼 수 있습니다. **dbm_monitor** 권한을 사용하여 서버 인스턴스에 연결할 경우 데이터베이스 미러링 모니터는 사용자에게 제한된 사용 권한이 있다는 것을 알립니다.  
  
> [!IMPORTANT]  
>  데이터베이스 미러링 모니터에서 첫 번째 데이터베이스를 등록하면 **dbm_monitor** 고정 데이터베이스 역할이 **msdb** 데이터베이스에서 만들어집니다. 새 **dbm_monitor** 역할은 시스템 관리자가 사용자를 할당할 때까지 멤버가 없습니다.  
  
## 탐색 트리  
 데이터베이스 미러링 모니터가 모니터링하도록 데이터베이스가 등록된 경우 등록된 데이터베이스 목록이 탐색 트리에 표시됩니다. 이 트리는 30초마다 자동으로 새로 고쳐집니다. 등록된 데이터베이스의 상태를 보려면 해당 데이터베이스를 선택합니다. 자세한 내용은 이 항목의 뒷부분에 나오는 "세부 정보 창"을 참조하십시오.  
  
 등록된 각 데이터베이스에 대해 다음 정보가 표시됩니다.  
  
 *<Database_name>* **(** *\<Status>* **,** *<PRINCIPAL_SERVER>* **->** *<MIRROR_SERVER>* **)**  
  
 *<Database_name>*  
 데이터베이스 미러링 모니터에 등록한 미러된 데이터베이스의 이름입니다.  
  
 *\<Status>*  
 가능한 상태 및 연관된 아이콘은 다음과 같습니다.  
  
|아이콘|상태|설명|  
|----------|------------|-----------------|  
|경고 아이콘|**알 수 없음**|모니터가 어느 파트너에도 연결되지 않았습니다. 사용할 수 있는 유일한 정보는 모니터가 캐시한 내용입니다.|  
|경고 아이콘|**동기화 중**|미러 데이터베이스의 내용이 주 데이터베이스의 내용보다 오래된 것입니다. 주 서버 인스턴스에서 로그 레코드를 미러 서버 인스턴스로 보내면 미러 서버 인스턴스에서 변경 사항을 미러 데이터베이스에 적용하여 롤포워드합니다.<br /><br /> 데이터베이스 미러링 세션을 시작할 때는 미러 데이터베이스와 주 데이터베이스가 이 상태입니다.|  
|표준 데이터베이스 실린더|**동기화됨**|미러 서버가 주 서버와 충분히 동기화되면 데이터베이스 상태가 **동기화됨**으로 변경됩니다. 주 서버에서 계속 변경 내용을 미러 서버로 보내고 미러 서버에서 계속 변경 내용을 미러 데이터베이스에 적용하면 데이터베이스는 이 상태로 유지됩니다.<br /><br /> 보호 우선 모드의 경우 데이터 손실 없이 자동 장애 조치 및 수동 장애 조치가 모두 가능합니다.<br /><br /> 성능 우선 모드의 경우 **동기화됨** 상태에서도 일부 데이터 손실이 항상 발생할 수 있습니다.|  
|경고 아이콘|**일시 중지됨**|주 데이터베이스는 사용 가능하지만 미러 서버로 로그를 보내지 않습니다.|  
|오류 아이콘|**연결 끊김**|서버 인스턴스를 해당 파트너에 연결할 수 없습니다.|  
  
 *<PRINCIPAL_SERVER>*  
 현재 주 서버 인스턴스인 파트너의 이름입니다. 이름의 형식은 다음과 같습니다.  
  
 *<SYSTEM_NAME>*[**\\***<instance_name>*]  
  
 여기서 *<SYSTEM_NAME>*은 서버 인스턴스가 있는 시스템의 이름입니다. 기본이 아닌 서버 인스턴스의 경우에도 인스턴스 이름이 *<SYSTEM_NAME>***\\***<instance_name>*으로 표시됩니다.  
  
 *<MIRROR_SERVER>*  
 현재 미러 서버 인스턴스인 파트너의 이름입니다. 형식은 주 서버와 동일합니다.  
  
## 세부 정보 창  
 모니터의 모양은 데이터베이스가 선택되었는지 여부에 따라 달라집니다. 모니터를 열면 세부 정보 창에 **미러된 데이터베이스 등록** 링크가 표시됩니다. 데이터베이스를 등록하려면 이 링크를 클릭합니다. 등록된 데이터베이스는 탐색 트리에서 **데이터베이스 미러링 모니터** 노드 아래에 나열됩니다. 데이터베이스 미러링 모니터는 서버 인스턴스에 대한 저장된 자격 증명이 있을 경우 이러한 모든 서버 인스턴스에 항상 연결을 시도합니다.  
  
 데이터베이스를 선택하면 세부 정보 창의 **상태** 탭 페이지에 해당 상태가 표시됩니다. 이 페이지의 내용은 주 서버 인스턴스 및 미러 서버 인스턴스에서 가져옵니다. 주 서버 인스턴스와 미러 서버 인스턴스에 각각 연결하여 상태가 수집되므로 페이지는 비동기적으로 채워집니다. 상태는 30초마다 자동으로 새로 고쳐집니다.  
  
> [!NOTE]  
>  모니터의 새로 고침 빈도를 변경할 수 없지만 **데이터베이스 미러링 기록** 대화 상자에서 상태 테이블을 새로 고칠 수 있습니다.  
  
 시스템 관리자는 **경고** 탭 페이지를 선택하여 데이터베이스에 대한 현재의 경고 구성을 볼 수 있습니다. 관리자는 이 페이지에서 **경고 임계값 설정** 대화 상자를 실행하여 하나 이상의 경고 임계값을 설정 및 구성할 수 있습니다.  
  
 세부 정보 창에서 탭 위의 배너에는 모니터가 상태 정보를 마지막으로 새로 고친 시간이 **마지막 새로 고침:***\<날짜>**\<시간>*으로 표시됩니다. 일반적으로 데이터베이스 미러링 모니터는 서로 다른 시간에 주 서버 인스턴스 및 미러 서버 인스턴스에서 상태 정보를 검색합니다. 이러한 두 새로 고침 시간 중에서 이전 시간이 표시됩니다.  
  
## 동작 메뉴  
 **동작** 메뉴에는 항상 다음 명령이 포함됩니다.  
  
|Command|설명|  
|-------------|-----------------|  
|**미러된 데이터베이스 등록...**|**미러된 데이터베이스 등록** 대화 상자를 엽니다. 이 대화 상자를 사용하면 데이터베이스 미러링 모니터에 데이터베이스를 추가하여 지정된 서버 인스턴스에서 하나 이상의 미러된 데이터베이스를 등록할 수 있습니다. 데이터베이스가 추가되면 데이터베이스 미러링 모니터는 데이터베이스, 해당 파트너, 파트너에 연결되는 방법 등에 대한 정보를 로컬로 캐시합니다.|  
|**서버 인스턴스 연결 관리...**|이 명령을 선택할 경우 **서버 연결 관리** 대화 상자가 열립니다. 이 대화 상자에서 지정된 파트너에 연결할 때 사용할 모니터에 대한 자격 증명을 지정할 서버 인스턴스를 선택할 수 있습니다.<br /><br /> 파트너에 대한 자격 증명을 편집하려면 **서버 인스턴스** 표에서 항목을 찾은 다음 해당 행에서 **편집** 을 클릭합니다. 서버 인스턴스 이름이 고정되어 있고 자격 증명 컨트롤이 현재 캐시된 값으로 초기화된 상태에서 **서버에 연결** 대화 상자가 나타납니다. 필요에 따라 인증 정보를 변경하고 **연결**을 클릭합니다. 자격 증명에 충분한 권한이 있는 경우 **연결 방법** 열이 새 자격 증명으로 업데이트됩니다.|  
  
 데이터베이스를 선택할 경우 **동작** 메뉴에는 다음 명령도 포함됩니다.  
  
|Command|설명|  
|-------------|-----------------|  
|**이 데이터베이스 등록 취소**|선택한 데이터베이스를 데이터베이스 미러링 모니터에서 제거합니다.|  
|**경고 임계값 설정...**|**경고 임계값 설정** 대화 상자를 엽니다. 이 대화 상자에서 시스템 관리자는 각 파트너의 데이터베이스에 대한 경고를 설정 또는 해제하고 각 경고의 임계값을 변경할 수 있습니다. 데이터베이스가 장애 조치될 경우 경고가 유지되도록 두 파트너 모두에 지정된 경고에 대한 임계값을 설정하는 것이 좋습니다. 각 파트너에 적합한 임계값은 각 파트너 시스템의 성능 기능에 따라 달라집니다.<br /><br /> 상태 테이블을 업데이트할 때 해당 값이 임계값보다 크거나 같을 경우에만 성능의 이벤트 로그에 이벤트가 기록됩니다. 상태 업데이트 사이에 최대값이 일시적으로 임계값에 도달할 경우 해당 값은 누락됩니다.|  
  
 **SQL Server Management Studio를 사용하여 데이터베이스 미러링을 모니터링하려면**  
  
-   [데이터베이스 미러링 모니터 시작&#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## 참고 항목  
 [데이터베이스 미러링 모니터링&#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [데이터베이스 미러링 보안 구성 마법사 시작&#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start the configuring database mirroring security wizard.md)  
  
  