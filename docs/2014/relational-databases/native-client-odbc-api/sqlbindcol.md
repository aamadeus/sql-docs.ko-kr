---
title: SQLBindCol | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4dafadd6ba64fa08f0329cd73114b4f85a1e376a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141513"
---
# <a name="sqlbindcol"></a>SQLBindCol
  일반적으로 사용 하 여 결과 고려해 야 **SQLBindCol** 데이터 변환 합니다. 바인딩 변환은 클라이언트 프로세스입니다. 예를 들어 문자 열에 바인딩된 부동 소수점 값을 검색하면 행이 인출될 때 드라이버가 부동 소수점 수에서 문자로의 변환을 로컬로 수행합니다. [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT 함수를 사용하면 데이터 변환 비용을 서버가 부담하도록 할 수 있습니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 단일 문 실행에서 결과 행의 집합이 여러 개 반환될 수 있습니다. 이 경우 각 결과 집합은 개별적으로 바인딩해야 합니다. 여러 결과 집합에 대 한 바인딩에 대 한 자세한 내용은 참조 하세요. [SQLMoreResults](sqlmoreresults.md)합니다.  
  
 개발자는 열을 바인딩할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-관련 C 데이터 형식을 사용 하는 *TargetType* 값 `SQL_C_BINARY`합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관련 형식에 바인딩된 열은 이식할 수 없습니다. 정의된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관련 ODBC C 데이터 형식은 DB-Library의 형식 정의와 일치하므로 응용 프로그램을 이식하는 DB-Library 개발자는 이 기능을 이용할 수 있습니다.  
  
 에 비용이 많이 드는 프로세스는 데이터 잘림 보고는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버. 모든 바인딩된 데이터 버퍼의 너비가 반환되는 데이터를 수용할 만큼 넓으면 잘림을 피할 수 있습니다. 문자 데이터의 경우 문자열 종료에 기본 드라이버 동작이 사용될 때는 문자열 종결자를 수용하기 위한 공간도 너비에 포함해야 합니다. 예를 들어 바인딩를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char(5)** 인출 하는 모든 값에서 잘림이 5 자 결과 배열에는 열입니다. 그러나 이 열을 6개 문자의 배열에 바인딩하면 Null 종결자를 저장할 문자 요소가 제공되므로 잘림이 발생하지 않습니다. [SQLGetData](sqlgetdata.md) 긴 문자와 이진 데이터를 잘림 없이 효율적으로 검색할 수 있습니다.  
  
 큰 값 데이터 형식의 경우 사용자가 열의 전체 값을 수용하기에 충분할 만큼 큰 버퍼를 제공하지 않으면 `SQL_SUCCESS_WITH_INFO`가 반환되고 "문자열 데이터의 오른쪽이 잘렸습니다."라는 경고가 발생합니다. `StrLen_or_IndPtr` 인수에는 버퍼에 저장된 문자/바이트의 수가 포함됩니다.  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>향상된 날짜 및 시간 기능에 대한 SQLBindCol 지원  
 날짜/시간 형식의 결과 열 값에 설명 된 대로 변환할지 [SQL에서 C로 변환](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)합니다. Time 및 datetimeoffset 열을 해당 구조를 검색 하는 (`SQL_SS_TIME2_STRUCT` 하 고 **SQL_SS_TIMESTAMPOFFSET_STRUCT**), *TargetType* 로 지정 해야 `SQL_C_DEFAULT` 또는 `SQL_C_BINARY`합니다.  
  
 자세한 내용은 [날짜 및 시간 기능 향상 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)합니다.  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>큰 CLR UDT에 대한 SQLBindCol 지원  
 **SQLBindCol** 는 큰 CLR 사용자 정의 형식 (Udt) 지원 합니다. 자세한 내용은 [Large CLR User-Defined 형식 &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQLBindCol 함수](http://go.microsoft.com/fwlink/?LinkId=59327)   
 [ODBC API 구현 정보](odbc-api-implementation-details.md)  
  
  
