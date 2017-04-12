---
title: "가용성 그룹의 생성 및 구성(SQL Server) | Microsoft Docs"
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
  - "가용성 그룹 [SQL Server], 배포"
  - "가용성 그룹 [SQL Server], 구성"
  - "가용성 그룹 [SQL Server], 만들기"
ms.assetid: 7f89fab8-6ee2-4273-9de0-e594bfb9407f
caps.latest.revision: 30
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 29
---
# 가용성 그룹의 생성 및 구성(SQL Server)
  이 섹션의 항목에서는 단일 WSFC 장애 조치(Failover) 클러스터 내의 여러 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 노드에 있는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 인스턴스에 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 구현을 배포하는 방법에 대해 설명합니다.  
  
 첫 번째 가용성 그룹을 만들기 전에 다음 항목의 정보를 숙지하는 것이 좋습니다.  
  
 [Always On 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md)  
 이 항목에서는 컴퓨터의 사전 요구 사항, 제한 사항 및 권장 사항과 WSFC 노드, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스, 가용성 그룹, 복제본 및 데이터베이스에 대해 설명합니다. 이 항목에는 보안 고려 사항에 대한 정보도 포함되어 있습니다.  
  
 [Always On 가용성 그룹 시작&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/getting-started-with-always-on-availability-groups-sql-server.md)  
 서버 인스턴스 구성, 가용성 그룹 만들기, 클라이언트 연결을 위한 가용성 그룹 구성, 가용성 그룹 관리 및 가용성 그룹 모니터링 단계에 대한 정보를 포함합니다.  
  
 **항목 내용**  
  
-   [관련 태스크](#RelatedTasks)  
  
-   [관련 내용](#RelatedContent)  
  
##  <a name="RelatedTasks"></a> 관련 태스크  
 **다음에 대한 서버 인스턴스를 구성하려면 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**  
  
-   [Always On 가용성 그룹 활성화 및 비활성화&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [Always On 가용성 그룹에 대한 데이터베이스 미러링 끝점 만들기&#40;SQL Server PowerShell&#41;](../../../database-engine/availability-groups/windows/database mirroring - always on availability groups- powershell.md)  
  
-   [Windows 인증에 대한 데이터베이스 미러링 끝점 만들기&#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [데이터베이스 미러링 끝점의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/database mirroring - use certificates for outbound connections.md)  
  
 **Always On 가용성 그룹 구성을 시작하려면**  
  
-   [Always On 가용성 그룹 시작&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/getting-started-with-always-on-availability-groups-sql-server.md)  
  
 **새 가용성 그룹을 만들고 구성하려면**  
  
-   [가용성 그룹 마법사 사용&#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [가용성 그룹 만들기&#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)  
  
-   [가용성 그룹 만들기&#40;SQL Server PowerShell&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-sql-server-powershell.md)  
  
-   [새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [가용성 복제본 추가 또는 수정 시 끝점 URL 지정&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/specify endpoint url - adding or modifying availability replica.md)  
  
-   [가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [유연한 장애 조치(failover) 정책을 구성하여 자동 장애 조치(failover)의 상태 제어&#40;Always On 가용성 그룹&#41;](../../../database-engine/availability-groups/windows/configure flexible automatic failover policy.md)  
  
-   [가용성 복제본에 백업 구성&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
-   [가용성 복제본에 대한 읽기 전용 액세스 구성&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [가용성 그룹에 대한 읽기 전용 라우팅 구성&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Always On 보조 데이터베이스에서 데이터 이동 시작&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [가용성 그룹에 대한 보조 데이터베이스 수동 준비&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [가용성 그룹의 데이터베이스에 대한 로그인 및 작업 관리&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/logins and jobs for availability group databases.md)  
  
 **문제를 해결하려면**  
  
-   [Always On 가용성 그룹 구성 문제 해결&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [실패한 파일 추가 작업 문제 해결&#40;Always On 가용성 그룹&#41;](../../../database-engine/availability-groups/windows/troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> 관련 내용  
  
-   **블로그:**  
  
     [Always ON - HADRON 학습 시리즈: HADRON 지원 데이터베이스에 대한 작업자 풀 사용](http://blogs.msdn.com/b/psssql/archive/2012/05/17/Always%20On-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [SQL Server Always On 팀 블로그: 공식 SQL Server Always On 팀 블로그](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
     [CSS SQL Server 엔지니어 블로그](http://blogs.msdn.com/b/psssql/)  
  
-   **비디오:**  
  
     [Microsoft SQL Server 코드 이름 "Denali" Always On 시리즈, 1부: 차세대 고가용성 솔루션 소개](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server 코드 이름 "Denali" Always On 시리즈, 2부: Always On을 사용하여 중요 업무용 고가용성 솔루션을 구축](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **백서:**  
  
     [고가용성 및 재해 복구를 위한 Microsoft SQL Server Always On 솔루션 가이드](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [SQL Server 2012에 대한 Microsoft 백서](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server 고객 자문 팀 백서](http://sqlcat.com/)  
  
## 참고 항목  
 [Always On 가용성 그룹 개요&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [가용성 그룹 관리&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/administration-of-an-availability-group-sql-server.md)   
 [Always On 가용성 그룹의 운영 문제에 대한 Always On 정책&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always on policies for operational issues - always on availability.md)   
 [가용성 그룹 모니터링&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/monitoring-of-availability-groups-sql-server.md)   
 [Always On 가용성 그룹: 상호 운용성&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md)  
  
  