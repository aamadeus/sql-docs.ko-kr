---
title: 커서 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- results [SQL Server], cursors
- Transact-SQL cursors, about cursors
- cursors [SQL Server]
- data access [SQL Server], cursors
- result sets [SQL Server], cursors
- requesting cursors
- cursors [SQL Server], about cursors
ms.assetid: e668b40c-bd4d-4415-850d-20fc4872ee72
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 10e6590da7d5efdb704a3f4005c278e2add41a5d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48134073"
---
# <a name="cursors"></a>커서
  관계형 데이터베이스에서의 연산은 전체 행 집합에 적용됩니다. 예를 들어 SELECT 문에 의해 반환된 행 집합은 문의 WHERE 절 조건을 만족하는 모든 행으로 구성됩니다. SELECT 문에 의해 반환된 전체 행 집합을 결과 집합이라고 합니다. 응용 프로그램, 특히 대화형 온라인 응용 프로그램에서는 전체 결과 집합을 한 단위로 사용하므로 항상 효과적으로 작업할 수는 없습니다. 이러한 응용 프로그램에는 한 번에 한 행이나 적은 행 블록을 사용하여 작업하는 메커니즘이 필요합니다. 커서는 이러한 메커니즘을 제공하는 결과 집합에 대한 확장입니다.  
  
 커서는 다음과 같이 결과 처리를 확장합니다.  
  
-   결과 집합의 특정 행에 위치를 정할 수 있습니다.  
  
-   결과 집합의 현재 위치에서 한 행 또는 행 블록을 검색합니다.  
  
-   결과 집합의 현재 위치에 있는 행 데이터를 수정할 수 있습니다.  
  
-   결과 집합에 나타난 데이터베이스 데이터에 대해 다른 사용자가 변경한 내용을 여러 가지 수준으로 볼 수 있습니다.  
  
-   스크립트, 저장 프로시저 및 트리거의 [!INCLUDE[tsql](../includes/tsql-md.md)] 문에서 결과 집합의 데이터에 액세스할 수 있도록 합니다.  
  
## <a name="concepts"></a>개념  
 커서 구현  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서는 세 가지 커서 구현을 지원합니다.  
  
 Transact-SQL 커서  
 DECLARE CURSOR 구문을 기반으로 하며 주로 [!INCLUDE[tsql](../includes/tsql-md.md)] 스크립트, 저장 프로시저 및 트리거에 사용됩니다. [!INCLUDE[tsql](../includes/tsql-md.md)] 커서는 서버에 구현되며 클라이언트가 서버로 보내는 [!INCLUDE[tsql](../includes/tsql-md.md)] 문으로 관리됩니다. 또한 일괄 처리, 저장 프로시저 또는 트리거에 포함될 수 있습니다.  
  
 API(응용 프로그래밍 인터페이스) 서버 커서  
 OLE DB와 ODBC의 API 커서 함수를 지원합니다. API 서버 커서는 서버에 구현됩니다. 클라이언트 응용 프로그램에서 API 커서 함수를 호출할 때마다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client OLE DB 공급자나 ODBC 드라이버가 API 서버 커서에 대한 동작 요청을 서버에 전송합니다.  
  
 클라이언트 커서  
 ADO API를 구현하는 DLL과 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client ODBC 드라이버에서 내부적으로 구현됩니다. 클라이언트 커서는 모든 결과 집합 행을 클라이언트에 캐시하여 구현됩니다. 클라이언트 응용 프로그램에서 API 커서 함수를 호출할 때마다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client ODBC 드라이버나 ADO DLL이 클라이언트에 캐시된 결과 집합 행에 대해 커서 작업을 수행합니다.  
  
 커서 유형  
 정방향 전용  
 정방향 전용 커서는 스크롤을 지원하지 않으며 커서의 처음부터 끝까지 순차적인 행 인출만 지원합니다. 행은 인출될 때까지 데이터베이스에서 검색되지 않습니다. 현재 사용자가 만들거나 다른 사용자가 커밋하여 결과 집합의 행에 영향을 주는 모든 INSERT, UPDATE 및 DELETE 문의 결과는 행이 커서에서 인출될 때 표시됩니다.  
  
 이 커서는 뒤로 스크롤할 수 없기 때문에 행이 인출된 후 데이터베이스 행의 변경 내용은 대부분 커서를 통해 표시되지 않습니다. 클러스터형 인덱스가 적용되는 열을 업데이트하는 경우와 같이 결과 집합 내의 행 위치를 결정하는 데 사용되는 값이 수정되면 커서를 통해 수정된 값이 표시됩니다.  
  
 데이터베이스 API 커서 모델에서는 정방향 전용 커서가 고유한 커서 유형으로 간주되지만 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서는 그렇지 않습니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서는 정방향 전용과 스크롤이 모두 정적, 키 집합 및 동적 커서에 적용할 수 있는 옵션으로 간주됩니다. [!INCLUDE[tsql](../includes/tsql-md.md)] 커서는 정방향 전용 정적, 키 집합 및 동적 커서를 지원합니다. 데이터베이스 API 커서 모델은 정적, 키 집합 및 동적 커서가 항상 스크롤 가능하다고 가정합니다. 데이터베이스 API 커서 특성 또는 속성을 정방향 전용으로 설정하면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가 이를 정방향 전용 동적 커서로 구현합니다.  
  
 정적  
 정적 커서의 전체 결과 집합은 커서가 열릴 때 **tempdb** 에 작성됩니다. 정적 커서는 항상 커서가 열렸을 당시의 결과 집합을 표시합니다. 정적 커서는 변경 내용을 거의 검색하지 못하는 반면 스크롤 시 리소스를 거의 소비하지 않습니다.  
  
 커서는 결과 집합의 멤버 자격이나 결과 집합을 구성하는 행의 열 값 변경에 영향을 주는 데이터베이스 변경 내용을 반영하지 않습니다. 정적 커서는 커서가 열린 후 데이터베이스에 삽입된 새 행이 커서 SELECT 문의 검색 조건과 일치하는 경우에도 이러한 행을 표시하지 않습니다. 또한 결과 집합을 구성하는 행을 다른 사용자가 업데이트할 경우 새 데이터 값이 정적 커서에 표시되지 않습니다. 정적 커서는 커서가 열린 후 데이터베이스에서 삭제된 행을 표시합니다. 커서를 닫았다가 다시 열지 않는 한 UPDATE, INSERT 또는 DELETE 작업은 정적 커서에 반영되지 않으며 이는 커서를 연 동일한 연결을 사용하여 수정한 경우에도 마찬가지입니다.  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 정적 커서는 항상 읽기 전용입니다.  
  
 정적 커서의 결과 집합은 **tempdb**의 작업 테이블에 저장되므로 결과 집합의 행 크기가 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 테이블의 최대 행 크기를 초과할 수 없습니다.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] 에서는 정적 커서와 무관한 용어를 사용합니다. 일부 데이터베이스 API에서는 정적 커서를 스냅숏 커서로 식별합니다.  
  
 Keyset  
 키 집합 커서의 멤버 자격과 행 순서는 커서가 열릴 때 고정됩니다. 키 집합 커서는 키 집합이라는 고유 식별자 집합으로 제어되며 키는 결과 집합에서 행을 고유하게 식별하는 열 집합으로 작성됩니다. 키 집합은 커서가 열려 있을 때 SELECT 문의 조건에 맞는 모든 행의 키 값 집합입니다. 키 집합 커서의 키 집합은 커서가 열려 있을 때 **tempdb** 에 작성됩니다.  
  
 Dynamic  
 동적 커서는 정적 커서의 반대 개념입니다. 커서를 통해 스크롤할 때 동적 커서는 행의 모든 변경 내용을 결과 집합에 반영합니다. 따라서 인출할 때마다 결과 집합에서 행의 데이터 값, 순서 및 멤버 자격이 변경될 수 있습니다. 모든 사용자가 실행한 모든 UPDATE, INSERT 및 DELETE 문은 커서를 통해 볼 수 있습니다. **SQLSetPos** 와 같은 API 함수 또는 [!INCLUDE[tsql](../includes/tsql-md.md)] WHERE CURRENT OF 절을 사용하여 커서를 통해 업데이트한 경우 즉시 그 결과를 볼 수 있습니다. 커서 트랜잭션 격리 수준을 커밋되지 않은 읽기로 설정한 경우를 제외하고는 커서 외부에서 수행된 업데이트는 커밋될 때까지 볼 수 없습니다. 동적 커서 계획은 공간 인덱스를 사용하지 않습니다.  
  
## <a name="requesting-a-cursor"></a>커서 요청  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서는 두 가지 방법으로 커서를 요청할 수 있습니다.  
  
-   [!INCLUDE[tsql](../includes/tsql-md.md)]  
  
     [!INCLUDE[tsql](../includes/tsql-md.md)] 언어는 ISO 커서 구문을 본뜬 커서 사용 구문을 지원합니다.  
  
-   데이터베이스 API(응용 프로그래밍 인터페이스) 커서 함수  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서는 다음과 같은 데이터베이스 API의 커서 기능을 지원합니다.  
  
    -   ADO([!INCLUDE[msCoName](../includes/msconame-md.md)] ActiveX Data Object)  
  
    -   OLE DB  
  
    -   ODBC(Open Database Connectivity)  
  
 응용 프로그램에서 이러한 두 가지 커서 요청 방법을 혼합하여 사용할 수 없습니다. API를 사용하여 커서 동작을 지정한 응용 프로그램은 또한 [!INCLUDE[tsql](../includes/tsql-md.md)] DECLARE CURSOR 문을 실행하여 [!INCLUDE[tsql](../includes/tsql-md.md)] 커서를 요청할 수 없습니다. 모든 API 커서 특성을 기본값으로 설정한 경우에만 DECLARE CURSOR를 실행해야 합니다.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] 및 API 커서 모두 요청되지 않은 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 는 기본적으로 기본 결과 집합이라고 하는 전체 결과 집합을 응용 프로그램에 반환합니다.  
  
## <a name="cursor-process"></a>커서 프로세스  
 [!INCLUDE[tsql](../includes/tsql-md.md)] 커서와 API 커서는 구문이 서로 다르지만 모든 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 커서에 대해 다음과 같은 일반 프로세스를 사용합니다.  
  
1.  커서와 [!INCLUDE[tsql](../includes/tsql-md.md)] 문의 결과 집합을 연결하고 커서 행의 업데이트 가능 여부 등 커서의 특성을 정의합니다.  
  
2.  [!INCLUDE[tsql](../includes/tsql-md.md)] 문을 실행하여 커서를 채웁니다.  
  
3.  보려는 커서의 행을 검색합니다. 커서에서 한 행이나 한 행 블록을 검색하는 작업을 인출이라고 합니다. 일련의 인출 작업을 수행하여 행을 앞으로 또는 뒤로 검색하는 것을 스크롤이라고 합니다.  
  
4.  또는 커서의 현재 위치에 있는 행에 대해 수정 작업(업데이트 또는 삭제)을 수행합니다.  
  
5.  커서를 닫습니다.  
  
## <a name="related-content"></a>관련 내용  
 [Cursor Behaviors](native-client-odbc-cursors/cursor-behaviors.md) [How Cursors Are Implemented](native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
## <a name="see-also"></a>관련 항목  
 [DECLARE CURSOR&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-cursor-transact-sql)   
 [커서&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/cursors-transact-sql)   
 [커서 함수&#40;Transact-SQL&#41;](/sql/t-sql/functions/cursor-functions-transact-sql)   
 [커서 저장 프로시저&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/cursor-stored-procedures-transact-sql)  
  
  
