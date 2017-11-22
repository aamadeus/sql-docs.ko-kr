---
title: "커서 옵션 (ODBC) 설정 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: cursors [ODBC], options
ms.assetid: 0e72b48a-fc5a-4656-8cf5-39f57d8c1565
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0ad0441f511edd74d1644185d807b75cfd6b7bf3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="set-cursor-options-odbc"></a>커서 옵션 설정(ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  커서 옵션을 설정 하려면 호출 [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) 설정 하려면 또는 [SQLGetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) 커서 동작을 제어 하는 문 옵션을 얻으려고 합니다.  
  
|*Attribute*|지정 내용|  
|-----------------|---------------|  
|SQL_ATTR_CURSOR_TYPE|커서 유형(정방향 전용, 정적, 동적 또는 키 집합)|  
|SQL_ATTR_CONCURRENCY|동시성 제어 옵션(읽기 전용, 잠금, 타임스탬프를 사용한 낙관적 또는 값을 사용한 낙관적)|  
|SQL_ATTR_ROW_ARRAY_SIZE|각 인출에서 검색된 행의 수|  
|SQL_ATTR_CURSOR_SENSITIVITY|다른 연결에서 만든 커서 행에 대한 업데이트를 표시하거나 표시하지 않는 커서|  
|SQL_ATTR_CURSOR_SCROLLABLE|앞뒤로 스크롤할 수 있는 커서|  
  
 이러한 특성의 기본값(정방향 전용, 읽기 전용, 행 집합 크기 1)을 설정하면 서버 커서가 사용되지 않습니다. 서버 커서를 사용하려면 이러한 특성 중 하나 이상을 기본값이 아닌 값으로 설정해야 하며 실행 중인 문이 단일 SELECT 문이거나 단일 SELECT 문을 포함하는 저장 프로시저여야 합니다. SELECT 문을 서버 커서에서 지원 하지 않는 서버 커서를 사용 하는 경우 사용할 수 없습니다: COMPUTE, COMPUTE BY, FOR BROWSE 및 INTO 합니다.  
  
 SQL_ATTR_CURSOR_TYPE 및 SQL_ATTR_CONCURRENCY를 설정하거나 SQL_ATTR_CURSOR_SENSITIVITY 및 SQL_ATTR_CURSOR_SCROLLABLE을 설정하여 사용되는 커서 유형을 제어할 수 있습니다. 커서 동작을 지정할 때 이 두 방법을 함께 사용하면 안 됩니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 문 핸들을 할당하고, 행 버전 관리 낙관적 동시성을 사용하여 동적 커서 유형을 설정한 다음 SELECT를 실행합니다.  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_DYNAMIC, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CONCURRENCY, SQLPOINTER)SQL_CONCUR_ROWVER, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, SELECT au_lname FROM authors", SQL_NTS);  
```  
  
## <a name="example"></a>예제  
 다음 예에서는 문 핸들을 할당하고, 스크롤 가능한 sensitive 커서를 설정한 다음 SELECT를 실행합니다.  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
  
// Set the cursor options and execute the statement.  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SCROLLABLE, SQLPOINTER)SQL_SCROLLABLE, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SENSITIVITY, SQLPOINTER)SQL_INSENSITIVE, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, select au_lname from authors", SQL_NTS);  
```  
  
## <a name="see-also"></a>관련 항목:  
 [실행 중인 쿼리 방법 도움말 항목 &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  