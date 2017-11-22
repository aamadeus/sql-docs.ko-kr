---
title: "바인딩 매개 변수 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- statements [ODBC], parameters
- binding parameters [SQL Server Native Client]
- parameter markers [ODBC]
- unbound parameter markers
- SQLBindParameter function
- ODBC applications, parameters
- bound parameter markers [SQL Server Native Client]
ms.assetid: d6c69739-8f89-475f-a60a-b2f6c06576e2
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6f94d2fe217f63e522b8a3d49196e13da0e12451
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="using-statement-parameters---binding-parameters"></a>바인딩 매개 변수-문 매개 변수를 사용 하 여
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  SQL 문을 실행하려면 먼저 SQL 문의 각 매개 변수 표식을 응용 프로그램의 변수에 연결하거나 바인딩해야 합니다. 호출 하 여 이렇게는 [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) 함수입니다. **SQLBindParameter** 드라이버에 프로그램 변수 (주소, C 데이터 형식 및 등)를 설명 합니다. 또한 매개 변수 표식의 서수 값을 나타낸 후 해당 표식이 나타내는 SQL 개체의 특성(SQL 데이터 형식, 전체 자릿수 등)을 설명하여 매개 변수 표식을 식별합니다.  
  
 문을 실행하기 전이라면 언제라도 매개 변수 표식을 바인딩하거나 다시 바인딩할 수 있습니다. 매개 변수 바인딩은 다음 호출 중 하나가 발생하기 전까지 계속 유지됩니다.  
  
-   에 대 한 호출 [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) 와 *옵션* SQL_RESET_PARAMS로 설정한 매개 변수는 문 핸들에 바인딩된 모든 매개 변수를 해제 합니다.  
  
-   에 대 한 호출 **SQLBindParameter** 와 *ParameterNumber* 이전 바인딩을 자동으로 해제 하는 바인딩된 매개 변수 표식의 서 수로 설정 합니다.  
  
 응용 프로그램에서 매개 변수를 프로그램 변수의 배열에 바인딩하여 SQL 문을 일괄 처리할 수도 있습니다. 배열 바인딩에는 다음과 같은 두 가지 유형이 있습니다.  
  
-   열 단위 바인딩은 각 매개 변수가 고유한 변수 배열에 바인딩될 때 발생합니다.  
  
     호출 하 여 지정 된 열 단위 바인딩은 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) 와 *특성* SQL_ATTR_PARAM_BIND_TYPE로 설정 하 고 *ValuePtr* SQL_PARAM_BIND_BY_COLUMN으로 설정 합니다.  
  
-   행 단위 바인딩은 SQL 문의 모든 매개 변수가 매개 변수의 개별 변수를 포함하는 구조체 배열에 하나의 단위로 바인딩될 때 발생합니다.  
  
     호출 하 여 지정 된 행 단위 바인딩은 **SQLSetStmtAttr** 와 *특성* SQL_ATTR_PARAM_BIND_TYPE로 설정 하 고 *ValuePtr* 보관 하는 구조체의 크기로 설정의 프로그램 변수입니다.  
  
 경우는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 서버로 문자나 이진 문자열 매개 변수를 보냅니다, 값에 지정 된 길이 채웁니다 **SQLBindParameter** *ColumnSize* 매개 변수입니다. ODBC 2.x 응용 프로그램에 대해 0을 지정 하는 경우 *ColumnSize*, 드라이버는 데이터 형식의 전체 자릿수에 매개 변수 값을 채웁니다. 전체 자릿수는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서버에 연결할 경우 8000이고 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결할 경우 255입니다. *ColumnSize* 는 variant 열에 대 한 바이트 단위입니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 저장 프로시저 매개 변수의 이름 정의를 지원합니다. ODBC 3.5에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 저장 프로시저를 호출할 때 사용되는 명명된 매개 변수에 대한 지원이 도입되었습니다. 이 지원을 통해 다음을 수행할 수 있습니다.  
  
-   저장 프로시저를 호출하고 저장 프로시저에 대해 정의된 매개 변수의 하위 집합에 대한 값을 제공할 수 있습니다.  
  
-   저장 프로시저를 만들 때 지정한 것과 다른 순서로 응용 프로그램에서 매개 변수를 지정할 수 있습니다.  
  
 명명 된 매개 변수는 사용 하는 경우에 지원 됩니다는 [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXECUTE** 문 또는 저장된 프로시저를 실행 하는 ODBC CALL 이스케이프 시퀀스입니다.  
  
 경우 **SQL_DESC_NAME** 설정 된 저장된 프로시저 매개 변수의 경우 쿼리의 모든 저장된 프로시저 매개 변수가 설정 해야 **SQL_DESC_NAME**합니다.  리터럴이 사용 될 경우 저장된 프로시저 호출에 매개 변수에 **SQL_DESC_NAME** 설정, 리터럴 형식을 사용 해야 *' 이름*=*값*', 여기서 *이름* 은 저장된 프로시저 매개 변수 이름 (예를 들어 @p1). 자세한 내용은 참조 [Binding Parameters by Name (Named Parameters)](http://go.microsoft.com/fwlink/?LinkId=167215)합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [문 매개 변수 사용](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
  