---
title: 매개 변수가 없는 SQL 문을 사용 하 여 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4b0728bd-059b-4b71-895c-999335bc7427
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 041a0119425e6469a394420469b14f47f3b84a81
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674841"
---
# <a name="using-an-sql-statement-with-no-parameters"></a>매개 변수가 없는 SQL 문 사용

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

매개 변수가 없는 SQL 문을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 데이터 작업을 수행하려면 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) 클래스의 [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) 메서드를 사용하여 요청한 데이터가 포함될 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)를 반환합니다. 이렇게 하려면 먼저 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) 클래스의 [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) 메서드를 사용하여 SQLServerStatement 개체를 만들어야 합니다.

다음 예제에서는 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] 샘플 데이터베이스에 대해 열린 연결을 함수로 전달하고 SQL 문을 생성 및 실행한 후 결과 집합에서 결과를 읽습니다.

[!code[JDBC#UsingSQLWithNoParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_0_1.java)]

결과 집합을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [JDBC 드라이버로 결과 집합 관리](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)합니다.

## <a name="see-also"></a>참고 항목

[SQL에 문 사용](../../connect/jdbc/using-statements-with-sql.md)
