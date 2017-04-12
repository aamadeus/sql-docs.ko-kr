---
title: "DDL 트리거에 대한 정보 가져오기 | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-ddl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "메타 데이터 [SQL Server], 트리거"
  - "상태 정보 [SQL Server], DDL 트리거"
  - "DDL 트리거, 메타데이터"
ms.assetid: 462becea-292a-4b9e-bb98-533e89733911
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# DDL 트리거에 대한 정보 가져오기
  이 섹션에 나열된 카탈로그 뷰를 사용하여 DDL 트리거에 대한 정보를 가져올 수 있습니다.  
  
 **DDL 트리거를 발생시킬 수 있는 모든 이벤트 또는 이벤트 그룹에 대한 정보를 가져오려면**  
  
-   [sys.trigger_event_types&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trigger-event-types-transact-sql.md)  
  
 **트리거의 종속 관계를 보려면**  
  
-   [sys.sql_expression_dependencies&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  
-   [sys.dm_sql_referenced_entities&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)  
  
-   [sys.dm_sql_referencing_entities&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)  
  
## 데이터베이스 범위 DDL 트리거  
 **데이터베이스 범위 트리거에 대한 정보를 가져오려면**  
  
-   [sys.triggers&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)  
  
 **트리거를 실행하는 데이터베이스 이벤트에 대한 정보를 가져오려면**  
  
-   [sys.trigger_events&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trigger-events-transact-sql.md)  
  
 **데이터베이스 범위 트리거의 정의를 보려면**  
  
-   [sys.sql_modules&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)  
  
 **CLR 데이터베이스 범위 트리거에 대한 정보를 가져오려면**  
  
-   [sys.assembly_modules&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)  
  
## 서버 범위 DDL 트리거  
 **서버 범위 트리거에 대한 정보를 가져오려면**  
  
-   [sys.server_triggers&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)  
  
 **트리거를 실행하는 서버 이벤트에 대한 정보를 가져오려면**  
  
-   [sys.server_trigger_events&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)  
  
 **서버 범위 트리거의 정의를 보려면**  
  
-   [sys.server_sql_modules&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)  
  
 **CLR 서버 범위 트리거에 대한 정보를 가져오려면**  
  
-   [sys.server_assembly_modules&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql.md)  
  
## 참고 항목  
 [DDL 트리거](../../relational-databases/triggers/ddl-triggers.md)  
  
  