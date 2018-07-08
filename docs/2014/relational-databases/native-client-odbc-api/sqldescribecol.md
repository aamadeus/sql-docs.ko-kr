---
title: SQLDescribeCol | Microsoft Docs
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
topic_type:
- apiref
helpviewer_keywords:
- SQLDescribeCol function
ms.assetid: ffbf34c6-8268-434f-829a-82009a6cda59
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c9c7a2471662efb547d8572ebb78a0a99646c20a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36092881"
---
# <a name="sqldescribecol"></a>SQLDescribeCol
  실행 된 문의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 결과 집합의 열을 설명 하기 위해 서버를 쿼리하려면 필요 하지 않습니다. 이 경우 `SQLDescribeCol` 서버 왕복은 발생 하지 않습니다. 마찬가지로 [SQLColAttribute](sqlnumresultcols.md)호출, `SQLDescribeCol` 에 준비 되었지만 실행된 되지 않은 문에 하면 서버 왕복이 발생 합니다.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 또는 문 일괄 처리에서 여러 결과 행 집합이 반환되는 경우 서수로 참조되는 열이 별도의 테이블에서 시작되거나 결과 집합의 완전히 다른 열을 참조할 수 있습니다. `SQLDescribeCol` 각 집합에 대해 호출 되어야 합니다. 결과 집합이 변경되면 응용 프로그램에서는 행 결과를 인출하기 전에 데이터 값을 다시 바인딩해야 합니다. 집합 반환을 여러 결과 처리 하는 방법에 대 한 자세한 내용은 참조 하십시오. [SQLMoreResults](sqlmoreresults.md)합니다.  
  
 준비된 SQL 문의 일괄 처리에서 여러 개의 결과 집합이 생성될 경우 첫 번째 결과 집합에 대해서만 열 특성이 보고됩니다.  
  
 큰 값 데이터 형식, 반환 되는 값에 *DataTypePtr* 은 SQL_VARCHAR, SQL_VARBINARY 또는 SQL_NVARCHAR입니다. SQL_SS_LENGTH_UNLIMITED 값 *ColumnSizePtr* 크기가 "제한" 하지 않음을 나타냅니다.  
  
 부터는 데이터베이스 엔진의 향상 된 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SQLDescribeCol 예상된 결과 대 한 보다 정확한 설명의 얻을를 허용 합니다. 이전 버전의 SQLDescribeCol 반환 하는 값에서 다를 수 있습니다 이러한 보다 정확한 결과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다. 자세한 내용은 참조 [메타 데이터 검색](../native-client/features/metadata-discovery.md)합니다.  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a>향상된 날짜 및 시간 기능에 대한 SQLDescribeCol 지원  
 날짜/시간 형식에 대해 반환되는 값은 다음과 같습니다.  
  
||*DataTypePtr*|*ColumnSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|---------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|날짜|SQL_TYPE_DATE|10|0|  
|Time|SQL_SS_TIME2|8, 10..16|0..7|  
|Datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 자세한 내용은 참조 [날짜 및 시간 기능 향상 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)합니다.  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>큰 CLR UDT에 대한 SQLDescribeCol 지원  
 `SQLDescribeCol`는 큰 CLR UDT(사용자 정의 형식)를 지원합니다. 자세한 내용은 참조 [Large CLR User-Defined 형식 &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQLDescribeCol 함수](http://go.microsoft.com/fwlink/?LinkID=59338)   
 [ODBC API 구현 정보](odbc-api-implementation-details.md)  
  
  