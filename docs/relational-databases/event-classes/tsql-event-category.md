---
title: TSQL 이벤트 범주 | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SQL Server event classes, TSQL event category
- TSQL event category [SQL Server]
- event classes [SQL Server], TSQL event category
ms.assetid: 215f8747-64b5-4bf3-9845-d476b10cda3a
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3e79d7b85f847ef0410d44b9247bd5bd0b00ba3b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745911"
---
# <a name="tsql-event-category"></a>TSQL 이벤트 범주
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **TSQL** 이벤트 범주에는 일반 TSQL 이벤트가 들어 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
|항목|설명|  
|-----------|-----------------|  
|[Exec Prepared SQL 이벤트 클래스](../../relational-databases/event-classes/exec-prepared-sql-event-class.md)|SqlClient, ODBC, OLE DB 또는 DB-Library가 준비된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행했음을 나타냅니다.|  
|[Prepare SQL 이벤트 클래스](../../relational-databases/event-classes/prepare-sql-event-class.md)|SqlClient, ODBC, OLE DB 또는 DB-Library가 사용할 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 준비했음을 나타냅니다.|  
|[SQL:BatchCompleted 이벤트 클래스](../../relational-databases/event-classes/sql-batchcompleted-event-class.md)|[!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리를 완료했음을 나타냅니다.|  
|[SQL:BatchStarting 이벤트 클래스](../../relational-databases/event-classes/sql-batchstarting-event-class.md)|[!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리를 시작했음을 나타냅니다.|  
|[SQL:StmtCompleted 이벤트 클래스](../../relational-databases/event-classes/sql-stmtcompleted-event-class.md)|[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 완료했음을 나타냅니다.|  
|[SQL:StmtRecompile 이벤트 클래스](../../relational-databases/event-classes/sql-stmtrecompile-event-class.md)|모든 유형의 일괄 처리로 인해 발생한 문 수준의 다시 컴파일을 나타냅니다. 여기에는 저장 프로시저, 트리거, 임시 일괄 처리 및 쿼리가 있습니다.|  
|[SQL:StmtStarting 이벤트 클래스](../../relational-databases/event-classes/sql-stmtstarting-event-class.md)|[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 시작했음을 나타냅니다.|  
|[Unprepare SQL 이벤트 클래스](../../relational-databases/event-classes/unprepare-sql-event-class.md)|SqlClient, ODBC, OLE DB 또는 DB-Library가 준비된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 삭제했음을 나타냅니다.|  
|[XQuery Static Type 이벤트 클래스](../../relational-databases/event-classes/xquery-static-type-event-class.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 XQuery 식을 실행할 때 발생합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Transact-SQL 참조&#40;데이터베이스 엔진&#41;](../../t-sql/transact-sql-reference-database-engine.md)  
  
  
