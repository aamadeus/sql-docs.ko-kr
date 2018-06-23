---
title: 메모리 내 OLTP에 대한 Transact-SQL 지원 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
caps.latest.revision: 52
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: f5c7dd02a31a466e5e6e96a815ed27795f62f978
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36091079"
---
# <a name="transact-sql-support-for-in-memory-oltp"></a>메모리 내 OLTP에 대한 Transact-SQL 지원
  Transact-SQL 쿼리 또는 DML 문(SELECT, INSERT, UPDATE 또는 DELETE), 임시 문과, 저장 프로시저, 테이블 반환 함수, 스칼라 함수, 트리거, 뷰와 같은 SQL 모듈을 사용하여 메모리 최적화 테이블에 액세스할 수 있습니다. 자세한 내용은 참조 [표를 사용 하 여 해석 된 TRANSACT-SQL 메모리](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)합니다.  
  
 메모리 최적화 테이블만 참조하는 저장 프로시저는 기계어 코드에 고유하게 컴파일될 수 있으며, 일반적으로 해석되는 (디스크 기반) 저장 프로시저에서 상당한 성능 향상을 제공합니다. 메모리 최적화 테이블에 최적으로 액세스하려면 고유하게 컴파일된 저장 프로시저를 사용합니다. 자세한 내용은 [고유하게 컴파일된 저장 프로시저](natively-compiled-stored-procedures.md)를 참조하세요.  
  
 데이터베이스 개체(DDL 문)를 만들고 수정할 때 다음 문이 수정되었습니다.  
  
-   [ALTER DATABASE 파일 및 파일 그룹 옵션 &#40;TRANSACT-SQL&#41; ](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) (참조 `MEMORY_OPTIMIZED_DATA`)  
  
-   [CREATE DATABASE &#40;SQL Server TRANSACT-SQL&#41; ](/sql/t-sql/statements/create-database-sql-server-transact-sql) (참조 `MEMORY_OPTIMIZED_DATA`)  
  
-   [CREATE PROCEDURE &#40;TRANSACT-SQL&#41; ](/sql/t-sql/statements/create-procedure-transact-sql) (참조 `NATIVE_COMPILATION`, `SCHEMABINDING`, `EXECUTE AS`, 및 `BEGIN ATOMIC`)  
  
-   [CREATE TABLE &#40;TRANSACT-SQL&#41; ](/sql/t-sql/statements/create-table-transact-sql) (참조 `MEMORY_OPTIMIZED`, `DURABILITY`, `BUCKET_COUNT`, `INDEX`, 및 `HASH`)  
  
-   [CREATE TYPE &#40;TRANSACT-SQL&#41; ](/sql/t-sql/statements/create-type-transact-sql) (참조 `MEMORY_OPTIMIZED`, `BUCKET_COUNT`, `INDEX`, 및 `HASH`)  
  
-   [선언 @local_variable &#40;TRANSACT-SQL&#41; ](/sql/t-sql/language-elements/declare-local-variable-transact-sql) (참조 `NULL`  |  `NOT NULL`)  
  
 메모리 액세스에 최적화된 테이블은 `PRIMARY KEY` 및 `NOT NULL` 제약 조건을 지원합니다. 지원 되지 않는 제약 조건 구현에 대 한 자세한 내용은 참조 하십시오. [마이그레이션 확인 및 Foreign Key Constraints](../../database-engine/migrating-check-and-foreign-key-constraints.md)합니다.  
  
 지원되지 않는 기능에 대한 자세한 내용은 [메모리 내 OLTP에서 지원되지 않는 Transact-SQL 구문](transact-sql-constructs-not-supported-by-in-memory-oltp.md)을 참조하세요.  
  
## <a name="in-this-section"></a>섹션 내용  
  
-   [지원되는 데이터 형식](supported-data-types-for-in-memory-oltp.md)  
  
-   [해석된 Transact-SQL을 사용하여 메모리 액세스에 최적화된 테이블에 액세스](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)  
  
-   [메모리 내 OLTP에 대한 시스템 뷰, 저장 프로시저, DMV 및 대기 유형](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)  
  
## <a name="see-also"></a>관련 항목  
 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](in-memory-oltp-in-memory-optimization.md)   
 [고유하게 컴파일된 저장 프로시저의 마이그레이션 문제](migration-issues-for-natively-compiled-stored-procedures.md)   
 [지원 되는 SQL Server 기능](unsupported-sql-server-features-for-in-memory-oltp.md)   
 [고유하게 컴파일된 저장 프로시저](natively-compiled-stored-procedures.md)  
  
  