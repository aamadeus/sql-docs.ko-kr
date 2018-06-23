---
title: 해석된 Transact-SQL을 사용하여 메모리 액세스에 최적화된 테이블에 액세스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92a44d4d-0e53-4fb0-b890-de264c65c95a
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: 030b8563ac272b0594697048169ade487c2321bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36185396"
---
# <a name="accessing-memory-optimized-tables-using-interpreted-transact-sql"></a>해석된 Transact-SQL을 사용하여 메모리 액세스에 최적화된 테이블에 액세스
  단지 몇 가지 예외를 제외하고 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리 또는 DML 작업(SELECT, INSERT, UPDATE 또는 DELETE), 임시 일괄 처리, 테이블 반환 함수, 트리거, 뷰 및 저장 프로시저와 같은 SQL 모듈을 사용하여 메모리 최적화 테이블에 액세스할 수 있습니다.  
  
 해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리 또는 고유하게 컴파일된 저장 프로시저가 아닌 저장 프로시저를 의미합니다. 메모리 최적화 테이블에 대한 해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 액세스를 interop 액세스라고 합니다.  
  
 메모리 액세스에 최적화된 테이블은 고유하게 컴파일된 저장 프로시저를 사용하여 액세스할 수도 있습니다. 고유하게 컴파일된 저장 프로시저는 성능이 중요한 OLTP 작업에 권장됩니다.  
  
 해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 액세스는 다음과 같은 시나리오에 권장됩니다.  
  
-   임시 쿼리 및 관리 태스크  
  
-   고유하게 컴파일된 저장 프로시저(예: 창 함수)에서 사용할 수 없는 구문을 일반적으로 사용하는 보고 쿼리  
  
-   응용 프로그램 코드를 최소한으로 변경하거나 변경하지 않고 응용 프로그램에서 성능이 중요한 부분을 메모리 최적화 테이블로 마이그레이션하려는 경우. 테이블을 마이그레이션하면 성능이 향상될 수 있습니다. 그런 다음 저장 프로시저를 고유하게 컴파일된 저장 프로시저로 마이그레이션하면 성능이 추가로 향상될 수 있습니다.  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 고유하게 컴파일된 저장 프로시저에 사용할 수 없는 경우  
  
 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문은 메모리 최적화 테이블의 데이터에 액세스하는 해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저에서 지원되지 않습니다.  
  
|영역|지원되지 않음|  
|----------|-----------------|  
|테이블에 대한 액세스|TRUNCATE TABLE<br /><br /> MERGE(메모리 최적화 테이블을 대상으로 사용)<br /><br /> 동적 및 키 집합 커서(자동으로 정적 커서로 강등됨)<br /><br /> 컨텍스트 연결을 사용하여 CLR 모듈에서 액세스<br /><br /> 인덱싱된 뷰에서 메모리 최적화 테이블 참조|  
|데이터베이스 간|데이터베이스 간 쿼리<br /><br /> 데이터베이스 간 트랜잭션<br /><br /> 연결된 서버|  
  
## <a name="table-hints"></a>테이블 힌트  
 테이블 힌트에 대한 자세한 내용은 [테이블 힌트&#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)를 참조하세요. [!INCLUDE[hek_2](../../includes/hek-2-md.md)]를 지원하기 위해 SNAPSHOT 격리가 추가되었습니다.  
  
 다음 테이블 힌트는 해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 메모리 최적화 테이블에 액세스하는 경우 지원되지 않습니다.  
  
|||||  
|-|-|-|-|  
|HOLDLOCK|IGNORE_CONSTRAINTS|IGNORE_TRIGGERS|NOWAIT|  
|PAGLOCK|READCOMMITTED|READCOMMITTEDLOCK|READPAST|  
|READUNCOMMITTED|ROWLOCK|SPATIAL_WINDOW_MAX_CELLS = *integer*|TABLOCK|  
|TABLOCKXX|UPDLOCK|XLOCK||  
  
 해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 명시적 또는 암시적 트랜잭션으로부터 메모리 최적화 테이블에 액세스할 때 SNAPSHOT, REPEATABLEREAD, SERIALIZABLE 등의 격리 수준 테이블 힌트 중 하나를 포함해야 합니다. 또는 MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT을 사용해도 됩니다. 자세한 내용은 참조 [트랜잭션 격리 수준에 메모리 최적화 된 테이블에 대 한 지침이](memory-optimized-tables.md) 및 [ALTER DATABASE SET 옵션 &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)합니다.  
  
> [!NOTE]  
>  자동 커밋 모드에서 실행되는 쿼리에서 액세스하는 메모리 최적화 테이블에는 격리 수준 테이블 힌트가 필요하지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [메모리 내 OLTP에 대한 Transact-SQL 지원](transact-sql-support-for-in-memory-oltp.md)   
 [메모리 내 OLTP로 마이그레이션](migrating-to-in-memory-oltp.md)  
  
  