---
title: 저장된 프로시저 호출 | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- ODBC, stored procedures
- stored procedures [ODBC], calling
- SQL Server Native Client ODBC driver, stored procedures
- ODBC CALL escape sequence
- escape sequences [SQL Server]
- CALL statement
ms.assetid: d13737f4-f641-45bf-b56c-523e2ffc080f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d93734ea9ef55361eb065f1f200757632dca1fd7
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51662402"
---
# <a name="calling-a-stored-procedure"></a>저장 프로시저 호출
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 모두 ODBC CALL 이스케이프 시퀀스를 지원 하며 [!INCLUDE[tsql](../../includes/tsql-md.md)] [EXECUTE](../../t-sql/language-elements/execute-transact-sql.md) 문을 실행 하기 위한 저장 프로시저는 ODBC CALL 이스케이프 시퀀스는 기본 방법입니다. ODBC 구문을 사용하면 응용 프로그램에서는 저장 프로시저의 반환 코드를 검색할 수 있고 또한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행하는 컴퓨터 간 RPC(원격 프로시저 호출) 전송을 위해 원래 개발된 프로토콜을 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버가 최적화됩니다. 이 RPC 프로토콜은 서버에서 수행되는 매개 변수 처리와 문 구문 분석의 대부분을 제거하여 성능을 향상시킵니다.  
  
> [!NOTE]  
>  호출할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 저장 프로시저는 ODBC로 명명 된 매개 변수를 사용 하 여 (자세한 내용은 참조 하십시오 [Binding Parameters by Name (Named Parameters)](https://go.microsoft.com/fwlink/?LinkID=209721)), 매개 변수 이름을 사용 하 여 시작 해야 합니다는 '\@' 문자입니다. 이는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에만 적용되는 제한 사항입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 MDAC(Microsoft Data Access Components)보다 이 제한 사항을 더욱 엄격하게 적용합니다.  
  
 프로시저를 호출하는 ODBC CALL 이스케이프 시퀀스는 다음과 같습니다.  
  
 {[**?=**]**call***procedure_name*[([*parameter*][**,**[* parameter*]]...)]}  
  
 여기서 *procedure_name* 프로시저의 이름을 지정 하 고 *매개 변수* 프로시저 매개 변수를 지정 합니다. 명명된 매개 변수는 ODBC CALL 이스케이프 시퀀스를 사용하는 문에서만 지원됩니다.  
  
 프로시저는 0개 이상의 매개 변수를 가질 수 있고 값(구문 시작에 나오는 선택적 매개 변수 표식인 ?=로 표시됨)을 반환할 수도 있습니다. 매개 변수가 입력 또는 입/출력 매개 변수인 경우 리터럴 또는 매개 변수 표식을 사용할 수 있습니다. 매개 변수가 출력 매개 변수인 경우에는 출력을 알 수 없기 때문에 매개 변수 표식을 사용해야 합니다. 매개 변수 표식을 사용 하 여 바인딩되어야 [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) 프로시저 호출 하기 전에 문이 실행 됩니다.  
  
 입력 및 입/출력 매개 변수는 프로시저 호출에서 생략할 수 있습니다. 매개 변수 없이 괄호만 지정하여 프로시저를 호출하면 드라이버는 첫 번째 매개 변수에 기본값을 사용하도록 데이터 원본에 지시합니다. 이는 아래와 같이 함수의 반환값을 데이터 프레임으로 바로 변환하는 데 사용할 수 있음을 나타냅니다.  
  
 {**호출** * * procedure_name **()**}  
  
 프로시저에 매개 변수가 없으면 프로시저가 실패할 수 있습니다. 괄호 없이 프로시저를 호출하면 드라이버는 아무 매개 변수 값도 보내지 않습니다. 이는 아래와 같이 함수의 반환값을 데이터 프레임으로 바로 변환하는 데 사용할 수 있음을 나타냅니다.  
  
 {**call** *procedure_name*}  
  
 프로시저 호출 시 리터럴을 입력 및 입/출력 매개 변수로 지정할 수 있습니다. 예를 들어 InsertOrder 프로시저에는 입력 매개 변수 다섯 개가 있습니다. InsertOrder 다음 호출을 첫 번째 매개 변수를 생략, 두 번째 매개 변수에 리터럴을 제공 및 세 번째, 네 번째 및 다섯 번째 매개 변수 표식을 사용 하 여 매개 변수입니다. 매개 변수는 1부터 차례대로 번호가 지정됩니다.  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}  
```  
  
 매개 변수를 생략하더라도 다른 매개 변수와 구분하는 쉼표는 생략하면 안 됩니다. 입력 또는 입/출력 매개 변수를 생략할 경우 프로시저는 매개 변수의 기본값을 사용합니다. 매개 변수에 바인딩된 길이/표시기 버퍼의 값을 SQL_DEFAULT_PARAM으로 설정하거나, DEFAULT 키워드를 사용하여 입력 또는 입/출력 매개 변수의 기본값을 지정할 수도 있습니다.  
  
 입/출력 매개 변수를 생략하거나, 매개 변수에 리터럴을 제공하면 드라이버는 출력 값을 삭제합니다. 마찬가지로 프로시저의 반환 값에 대한 매개 변수 표식을 생략하면 드라이버는 반환 값을 삭제합니다. 마지막으로, 응용 프로그램에서 값을 반환하지 않는 프로시저에 대해 반환 값 매개 변수를 지정하면 드라이버는 매개 변수에 바인딩된 길이/표시기 버퍼의 값을 SQL_NULL_DATA로 설정합니다.  
  
## <a name="delimiters-in-call-statements"></a>CALL 문의 구분 기호  
 기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 ODBC { CALL } 이스케이프 시퀀스와 관련된 호환성 옵션도 지원합니다. 드라이버는 다음과 같이 전체 저장 프로시저 이름을 구분하는 큰따옴표 쌍 하나만 사용하는 CALL 문을 허용합니다.  
  
```  
{ CALL "master.dbo.sp_who" }  
```  
  
 기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 다음과 같이 ISO 규칙에 따라 각 식별자를 큰따옴표로 묶은 CALL 문도 허용합니다.  
  
```  
{ CALL "master"."dbo"."sp_who" }  
```  
  
 그러나 기본 설정을 사용하여 실행할 경우 적절한 ISO 표준으로 지정되지 않은 문자가 포함된 식별자를 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 두 가지 따옴표 붙은 식별자 형식을 모두 지원하지 않습니다. 예를 들어 드라이버 라는 저장된 프로시저에 액세스할 수 없습니다 **"My.Proc"** 따옴표 붙은 식별자를 사용 하 여 CALL 문을 사용 합니다.  
  
```  
{ CALL "MyDB"."MyOwner"."My.Proc" }  
```  
  
 드라이버는 이 문을 다음과 같이 해석합니다.  
  
```  
{ CALL MyDB.MyOwner.My.Proc }  
```  
  
 서버에 연결된 된 서버 라는 오류가 발생 **MyDB** 존재 하지 않습니다.  
  
 다음과 같이 대괄호로 묶은 식별자를 사용할 경우에는 이 문제가 발생하지 않고 문이 제대로 해석됩니다.  
  
```  
{ CALL [MyDB].[MyOwner].[My.Table] }  
```  
  
## <a name="see-also"></a>관련 항목  
 [저장 프로시저 실행](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
