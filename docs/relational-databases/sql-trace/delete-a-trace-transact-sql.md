---
title: "추적 삭제(Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "추적 [SQL Server], 삭제"
  - "추적 제거"
  - "추적 삭제"
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# 추적 삭제(Transact-SQL)
  이 항목에서는 저장 프로시저를 사용하여 추적을 삭제하는 방법에 대해 설명합니다.  
  
 추적 저장 프로시저 사용에 대한 예는 [추적 만들기&#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)를 참조하세요.  
  
### 추적을 삭제하려면  
  
1.  **@status = 0**을 지정하고 **sp_trace_setstatus**를 실행하여 추적을 중지합니다.  
  
2.  **@status = 2**를 지정하고 **sp_trace_setstatus**를 실행하여 추적을 닫고 서버에서 추적 정보를 삭제합니다.  
  
> [!NOTE]  
>  추적은 먼저 중지한 후 닫아야 합니다.  
  
## 참고 항목  
 [sp_trace_setstatus&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [SQL Server Profiler 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  