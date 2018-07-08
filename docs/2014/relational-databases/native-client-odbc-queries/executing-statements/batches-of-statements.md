---
title: 문의 일괄 처리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- statements [ODBC], batches
- batches [ODBC]
- ODBC applications, statements
- multiple statements, batches
- SQLMoreResults function
- SQLExecDirect function
ms.assetid: 057d7c1c-1428-4780-9447-a002ea741188
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2ebe40de44765e974a63fc0eb6282ae0b979b607
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180815"
---
# <a name="batches-of-statements"></a>문의 일괄 처리
  일괄 처리를 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 에 전달 된 단일 문자열에 세미콜론 (;)으로 구분 된 두 개 이상의 문을 포함 하 여 문을 **SQLExecDirect** 또는 [SQLPrepare 함수](http://go.microsoft.com/fwlink/?LinkId=59360)합니다. 예를 들어:  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 일괄 처리를 사용하면 대개 네트워크 트래픽이 줄어들므로 문을 개별적으로 전송하는 것보다 효율적일 수 있습니다. 사용 하 여 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) 를 다음 결과 집합 현재 결과 집합 후에 위치를 지정 합니다.  
  
 ODBC 커서 특성을 행 집합 크기가 1인 정방향 전용의 읽기 전용 커서(기본값)로 설정하면 항상 일괄 처리를 사용할 수 있습니다.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 대해 서버 커서를 사용할 때 일괄 처리를 실행하면 서버 커서가 암시적으로 기본 결과 집합으로 변환됩니다. **SQLExecDirect** 또는 **SQLExecute** SQL_SUCCESS_WITH_INFO, 및에 대 한 호출 반환 **SQLGetDiagRec** 반환:  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a>관련 항목  
 [문을 실행 &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  