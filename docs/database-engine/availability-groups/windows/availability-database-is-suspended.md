---
title: "가용성 데이터베이스가 일시 중지됨 | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.agdashboard.drp1notsuspended.issues.f1"
helpviewer_keywords: 
  - "가용성 그룹 [SQL Server], 정책"
ms.assetid: 6baee70f-848c-4e86-b20d-78875c0f82cb
caps.latest.revision: 15
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 15
---
# 가용성 데이터베이스가 일시 중지됨
    
## 소개  
  
|||  
|-|-|  
|**정책 이름**|가용성 데이터베이스 일시 중지 상태|  
|**문제점**|가용성 데이터베이스가 일시 중지됨|  
|**범주**|**경고**|  
|**패싯**|가용성 데이터베이스|  
  
## 설명  
 이 정책은 보조 데이터베이스("보조 데이터베이스 복제본"이라고도 함)의 데이터 이동 상태를 확인합니다. 데이터 이동이 일시 중지되는 경우 정책은 비정상 상태에 있습니다. 그렇지 않으면 정책은 정상 상태입니다.  
  
> [!NOTE]  
>  이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 릴리스의 경우 가능한 원인 및 해결 방법은 TechNet Wiki의 [가용성 데이터베이스가 일시 중지됨](http://go.microsoft.com/fwlink/p/?LinkId=220860)을 참조하세요.  
  
## 가능한 원인  
 이 가용성 데이터베이스의 데이터 동기화는 다음과 같은 이유로 일시 중지되었을 수 있습니다.  
  
-   오류가 발생하여 시스템에서 데이터 동기화를 일시 중지했을 수 있습니다.  
  
-   데이터베이스 관리자가 유지 보수를 위해 데이터 동기화를 일시 중지했을 수 있습니다.  
  
## 가능한 해결 방법  
 데이터 동기화를 다시 시작합니다. 문제가 계속되면 이벤트 로그에서 가용성 그룹을 확인하여 시스템에서 데이터 이동이 일시 중지된 이유를 진단합니다.  
  
## 참고 항목  
 [Always On 가용성 그룹 개요&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Always On 대시보드 사용&#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  