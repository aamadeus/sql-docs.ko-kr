---
title: "SQL Server, SQL Errors 개체 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Errors 개체"
  - "SQLServer:SQL Errors"
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# SQL Server, SQL Errors 개체
  Microsoft **의** SQLServer:SQL Errors [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체는 **SQL Errors**를 모니터링하는 카운터를 제공합니다.  
  
 이 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** 카운터를 설명합니다.  
  
|SQL Server SQL Errors 카운터|설명|  
|------------------------------------|-----------------|  
|**Errors/sec**|초당 오류 개수입니다.|  
  
 개체의 각 카운터는 다음 인스턴스를 포함합니다.  
  
|항목|정의|  
|----------|----------------|  
|**_Total**|모든 오류에 대한 정보입니다.|  
|**DB Offline Errors**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 현재 데이터베이스를 오프라인 상태로 만드는 심각한 오류를 추적합니다.|  
|**Info Errors**|사용자에게 정보를 제공하지만 오류는 발생시키지 않는 오류 메시지 관련 정보입니다.|  
|**Kill Connection Errors**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 현재 연결을 해제하게 만드는 심각한 오류를 추적합니다.|  
|**User Errors**|사용자 오류에 대한 정보입니다.|  
  
## 참고 항목  
 [리소스 사용 모니터링&#40;시스템 모니터&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  