---
title: 행 집합 바인딩 (ODBC) 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowset binding [ODBC]
ms.assetid: a7be05f0-6b11-4b53-9fbc-501e591eef09
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da0cfb6552153676b838d7df4d526e12def3f517
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48180993"
---
# <a name="use-rowset-binding-odbc"></a>행 집합 바인딩 사용(ODBC)
    
### <a name="to-use-column-wise-binding"></a>열 단위 바인딩을 사용하려면  
  
1.  바인딩된 각 열에 대해 다음을 수행합니다.  
  
    -   데이터 값을 저장할 R개 이상의 열 버퍼 배열을 할당합니다. 여기서 R은 행 집합의 행 수입니다.  
  
    -   필요에 따라 데이터 길이를 저장할 R개 이상의 열 버퍼 배열을 할당합니다.  
  
    -   호출 [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) 에 열의 데이터 값 및 데이터 길이 배열을 행 집합의 열에 바인딩합니다.  
  
2.  [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 을 호출하여 다음 특성을 설정합니다.  
  
    -   SQL_ATTR_ROW_ARRAY_SIZE를 행 집합의 행 수(R)로 설정합니다.  
  
    -   SQL_ATTR_ROW_BIND_TYPE을 SQL_BIND_BY_COLUMN으로 설정합니다.  
  
    -   SQL_ATTR_ROWS FETCHED_PTR 특성을 인출된 행 수를 보유하는 SQLUINTEGER 변수를 가리키도록 설정합니다.  
  
    -   SQL_ATTR_ROW_STATUS_PTR을 행 상태 표시를 보유하는 SQLUSSMALLINT 변수의 배열[R]을 가리키도록 설정합니다.  
  
3.  해당 문을 실행합니다.  
  
4.  호출할 때마다 [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) 하거나 [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) R 개의 행을 검색 하 고 바인딩된 열에 데이터를 전송 합니다.  
  
### <a name="to-use-row-wise-binding"></a>행 단위 바인딩을 사용하려면  
  
1.  구조의 배열[R]을 할당합니다. 여기서 R은 행 집합의 행 수입니다. 구조에는 각 열에 대해 요소가 하나씩 포함되고 각 요소에는 두 부분이 포함됩니다.  
  
    -   첫 번째 부분은 열 데이터를 보유하는 적절한 데이터 형식의 변수입니다.  
  
    -   두 번째 부분은 열 상태 표시를 보유하는 SQLINTEGER 변수입니다.  
  
2.  [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 을 호출하여 다음 특성을 설정합니다.  
  
    -   SQL_ATTR_ROW_ARRAY_SIZE를 행 집합의 행 수(R)로 설정합니다.  
  
    -   SQL_ATTR_ROW_BIND_TYPE을 1단계에서 할당한 구조의 크기로 설정합니다.  
  
    -   SQL_ATTR_ROWS_FETCHED_PTR 특성을 인출된 행 수를 보유하는 SQLUINTEGER 변수를 가리키도록 설정합니다.  
  
    -   SQL_ATTR_PARAMS_STATUS_PTR을 행 상태 표시를 보유하는 SQLUSSMALLINT 변수의 배열[R]을 가리키도록 설정합니다.  
  
3.  결과 집합의 각 열에 대 한 호출 [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) 데이터 값 및 열 데이터 길이 포인터가 1 단계에서에서 할당 한 구조 배열의 첫 번째 요소에 있는 해당 변수를 가리키도록 합니다.  
  
4.  해당 문을 실행합니다.  
  
5.  호출할 때마다 [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) 하거나 [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) R 개의 행을 검색 하 고 바인딩된 열에 데이터를 전송 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [커서 방법 도움말 항목을 사용 하 여 &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md)   
 [커서 구현 방법](../../native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)   
 [커서를 사용 하 여 &#40;ODBC&#41;](use-cursors-odbc.md)  
  
  
