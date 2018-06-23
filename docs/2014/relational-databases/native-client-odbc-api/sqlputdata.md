---
title: SQLPutData | Microsoft Docs
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
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
caps.latest.revision: 49
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: abce5378b6df9bcce36bf6e1a2c9ed884f977824
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36172635"
---
# <a name="sqlputdata"></a>SQLPutData
  SQLPutData를 사용 하 여 65, 535 바이트가 넘는 데이터를 보낼 때 다음과 같은 제한 사항이 적용 (에 대 한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전 4.21 a) 또는 400KB sql_longvarchar (SQL Server 버전 6.0 이상)에 대 한 데이터 (`text`), SQL_WLONGVARCHAR (`ntext`) 또는 SQL_LONGVARBINARY (`image`) 열:  
  
-   참조 된 매개 변수 수는 *insert_value* 문입니다.  
  
-   참조 된 매개 변수 수는 *식* UPDATE 문의 SET 절에서.  
  
 시퀀스를 실행 하는 서버는 블록의에서 데이터를 제공 하는 SQLPutData 호출 취소 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 또는 이전 버전을 사용 하는 열의 값과의 부분 업데이트를 발생 시킵니다. `text`, `ntext`, 또는 `image` SQLCancel가 호출 될 때 참조 된 열은 중간 자리 표시자 값으로 설정 합니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 및 이전 버전에 대한 연결을 지원하지 않습니다.  
  
## <a name="diagnostics"></a>진단  
 하나의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLPutData에 대 한 특정 SQLSTATE Native Client:  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|22026|문자열 데이터, 길이가 일치하지 않음|보낼 바이트에 데이터의 길이가 지정 된 경우 응용 프로그램에서 예를 들어 SQL_LEN_DATA_AT_EXEC로 (*n*) 여기서 *n* 총을 통해 응용 프로그램에서 제공 하는 바이트 수가 0 보다 크면 SQLPutData 지정 된 길이 일치 해야 합니다.|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>SQLPutData 및 테이블 반환 매개 변수  
 SQLPutData 가변 행 바인딩을 테이블 반환 매개 변수와 함께 사용 하는 경우 응용 프로그램에서 사용 됩니다. *StrLen_Or_Ind* 매개 변수 행이 더 이상를 사용할 수 있는지 또는 다음 행 또는 테이블 반환 매개 변수 데이터의 행에 대 한 데이터를 수집 하도록 드라이버에 대 한 준비가 되었음을 나타냅니다.  
  
-   0보다 큰 값은 다음 행 값의 집합을 사용할 수 있음을 나타냅니다.  
  
-   값이 0이면 보낼 행이 더 이상 없음을 나타냅니다.  
  
-   0보다 작은 값은 오류를 나타내며 SQLState HY090 및 "잘못된 문자열 또는 버퍼 길이입니다."라는 메시지가 포함된 진단 레코드가 기록됩니다.  
  
 *DataPtr* 매개 변수는 무시 되지만 NULL이 아닌 값으로 설정 되어 있어야 합니다. 자세한 내용은 섹션을 참조의 변수 TVP 행 바인딩에 대 [바인딩 및 Data Transfer of Table-Valued 매개 변수 및 열 값](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)합니다.  
  
 경우 *StrLen_Or_Ind* 이 0과 SQL_PARAMSET_SIZE 사이의 숫자 또는 SQL_DEFAULT_PARAM 이외의 값 (즉,는 *ColumnSize* SQLBindParameter의 매개 변수), 오류가 발생 합니다. 이 오류가 발생 하면 SQLPutData에서 SQL_ERROR: SQLSTATE = HY090, "잘못 된 문자열 또는 버퍼 길이"입니다.  
  
 테이블 반환 매개 변수에 대 한 자세한 내용은 참조 [테이블 반환 매개 변수 &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)합니다.  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>향상된 날짜 및 시간 기능에 대한 SQLPutData 지원  
 날짜/시간 형식의 매개 변수 값에 설명 된 대로 변환 됩니다 [C에서 SQL로 변환을](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)합니다.  
  
 자세한 내용은 참조 [날짜 및 시간 기능 향상 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)합니다.  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>큰 CLR UDT에 대한 SQLPutData 지원  
 `SQLPutData`는 큰 CLR UDT(사용자 정의 형식)를 지원합니다. 자세한 내용은 참조 [Large CLR User-Defined 형식 &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQLPutData 함수](http://go.microsoft.com/fwlink/?LinkId=59365)   
 [ODBC API 구현 정보](odbc-api-implementation-details.md)  
  
  