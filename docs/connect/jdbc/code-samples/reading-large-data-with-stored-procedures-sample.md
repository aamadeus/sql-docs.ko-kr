---
title: 저장 프로시저로 대규모 데이터 읽기 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 58c76635-a117-4661-8781-d6cb231c5809
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9dff36847a6c03a300209427fae5a20d1ffea206
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644229"
---
# <a name="reading-large-data-with-stored-procedures-sample"></a>저장 프로시저로 큰 데이터 읽기 샘플

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

이 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 샘플 응용 프로그램은 저장 프로시저에서 큰 OUT 매개 변수를 검색하는 방법을 보여 줍니다.

이 샘플의 코드 파일 이름은 ExecuteStoredProcedure.java이며 다음 위치에 있습니다.

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>요구 사항

이 샘플 응용 프로그램을 실행하려면 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] 샘플 데이터베이스에 대한 액세스 권한이 필요합니다. 또한 mssql-jdbc jar 파일을 포함하도록 클래스 경로를 설정해야 합니다. 클래스 경로 설정 하는 방법에 대 한 자세한 내용은 참조 하세요. [JDBC 드라이버를 사용 하 여](../../../connect/jdbc/using-the-jdbc-driver.md)입니다.

> [!NOTE]  
> [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]는 기본 설정된 JRE(Java Runtime Environment)에 따라 사용할 수 있는 mssql-jdbc 클래스 라이브러리 파일을 제공합니다. JAR 파일을 선택 하는 방법에 대 한 자세한 내용은 참조 하세요. [JDBC 드라이버 시스템 요구 사항](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)합니다.

[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] 샘플 데이터베이스에 다음 저장 프로시저를 만듭니다.

```sql
CREATE PROCEDURE GetLargeDataValue
  (@Document_ID int,
   @Document_ID_out int OUTPUT,
   @Document_Title varchar(50) OUTPUT,  
   @Document_Summary nvarchar(max) OUTPUT)  

AS
BEGIN
   SELECT @Document_ID_out = DocumentID,
          @Document_Title = Title,  
          @Document_Summary = DocumentSummary
    FROM  Production.Document  
    WHERE DocumentID = @Document_ID  
END  
```

## <a name="example"></a>예제

다음 예제의 샘플 코드에서는 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] 데이터베이스에 연결합니다. 그런 다음 샘플 데이터를 만들고 매개 변수가 있는 쿼리를 사용하여 Production.Document 테이블을 업데이트합니다. 그런 다음, [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 클래스의 [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) 메서드를 사용하여 선택 버퍼링 모드를 가져오고 GetLargeDataValue 저장 프로시저를 실행합니다. JDBC 드라이버 버전 2.0 릴리스 이상에서는 기본적으로 responseBuffering 연결 속성이 "adaptive"로 설정됩니다.

마지막으로 샘플 코드는 OUT 매개 변수로 반환된 데이터를 표시하고 스트림에서 `mark` 및 `reset` 메서드를 사용하여 데이터의 부분을 다시 읽는 방법도 보여 줍니다.

[!code[JDBC#UsingAdaptiveBuffering2](../../../connect/jdbc/codesnippet/Java/reading-large-data-with-_1_1.java)]

## <a name="see-also"></a>참고 항목

[대규모 데이터 작업](../../../connect/jdbc/code-samples/working-with-large-data.md)
