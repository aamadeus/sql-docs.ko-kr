---
title: "SQL Server, Memory Node | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# SQL Server, Memory Node
  Microsoft **의** Memory Node [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체는 NUMA 노드의 서버 메모리 사용량을 모니터링하는 카운터를 제공합니다.  
  
## Memory Node 카운터  
 다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Node** 카운터에 대해 설명합니다.  
  
|SQL Server Memory Manager 카운터|설명|  
|----------------------------------------|-----------------|  
|**Database Node Memory(KB)**|서버가 현재 이 노드에서 데이터베이스 페이지에 사용 중인 메모리의 양을 지정합니다.|  
|**Free Node Memory(KB)**|서버가 이 노드에서 사용하고 있지 않은 메모리의 양을 지정합니다.|  
|**Foreign Node Memory(KB)**|이 노드의 비-NUMA 로컬 메모리의 양을 지정합니다.|  
|**Stolen Memory Node(KB)**|서버가 이 노드에서 데이터베이스 페이지가 아닌 다른 용도로 사용 중인 메모리의 양을 지정합니다.|  
|**Target Node Memory**|이 노드에 적합한 메모리의 양을 지정합니다.|  
|**Total Node Memory**|서버가 이 노드에서 커밋한 총 메모리의 양을 나타냅니다.|  
  
## 참고 항목  
 [리소스 사용 모니터링&#40;시스템 모니터&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server, Buffer Manager 개체](../../relational-databases/performance-monitor/sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)  
  
  