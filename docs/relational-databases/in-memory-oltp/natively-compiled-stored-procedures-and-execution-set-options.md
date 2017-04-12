---
title: "고유하게 컴파일된 저장 프로시저 및 Execution Set 옵션 | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# 고유하게 컴파일된 저장 프로시저 및 Execution Set 옵션
  ATOMIC 블록에서 Session 옵션은 고정됩니다. 저장 프로시저 실행은 세션의 SET 옵션의 영향을 받지 않습니다. 하지만 SET NOEXEC, SET SHOWPLAN_XML과 같은 일부 SET 옵션은 저장 프로시저(고유하게 컴파일된 저장 프로시저 포함)가 실행되지 않도록 합니다.  
  
 STATISTICS 옵션을 사용하도록 설정한 상태에서 고유하게 컴파일된 저장 프로시저를 실행하면 프로시저에 대한 통계가 문별로 수집되지 않고 전체적으로 수집됩니다. 자세한 내용은 [SET STATISTICS IO&#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-io-transact-sql.md), [STATISTICS PROFILE&#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-profile-transact-sql.md), [STATISTICS TIME&#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-time-transact-sql.md) 및 [STATISTICS XML&#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-xml-transact-sql.md)을 참조하세요. 고유하게 컴파일된 저장 프로시저의 문별 수준에 대한 실행 통계를 구하려면 저장 프로시저의 각 개별 쿼리 실행이 완료될 때 시작되는 sp_statement_completed 이벤트에 확장 이벤트 세션을 사용합니다. 확장 이벤트 세션을 만드는 방법은 [CREATE EVENT SESSION&#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md)을 참조하세요.  
  
 **SHOWPLAN_XML**은 고유하게 컴파일된 저장 프로시저에서 지원됩니다. **SHOWPLAN_ALL** 및 **SHOWPLAN_TEXT**는 고유하게 컴파일된 저장 프로시저에서 지원되지 않습니다.  
  
 **SET FMTONLY** 는 고유하게 컴파일된 저장 프로시저에서 지원되지 않습니다. 대신 [sp_describe_first_result_set&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)를 사용하세요.  
  
## 참고 항목  
 [고유하게 컴파일된 저장 프로시저](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  