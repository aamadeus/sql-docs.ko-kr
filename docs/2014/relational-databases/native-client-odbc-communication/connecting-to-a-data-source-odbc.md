---
title: 데이터 원본 (ODBC)에 연결 | Microsoft Docs
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
- checking connection states
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- SQLBrowseConnect function
- ODBC applications, connections
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLConnect function
- SQLDriveConnect function
- verifying connection states
- SQL Server Native Client ODBC driver, data sources
- SQL Server Native Client ODBC driver, connections
ms.assetid: ae30dd1d-06ae-452b-9618-8fd8cd7ba074
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1b4972792bf40c5569a3529c583209bfd4f53407
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082279"
---
# <a name="connecting-to-a-data-source-odbc"></a>데이터 원본에 연결(ODBC)
  응용 프로그램은 환경 및 연결 핸들을 할당하고 연결 특성을 설정한 후 데이터 원본이나 드라이버에 연결합니다. 연결에 사용할 수 있는 함수는 다음과 같이 세 가지가 있습니다.  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLBrowseConnect**  
  
 를 사용할 수 있는 다양 한 연결 문자열 옵션을 포함 하 여 데이터 원본에 연결 하는 방법에 대 한 자세한 내용은 참조 [Connection String Keywords with SQL Server Native Client를 사용 하 여](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)합니다.  
  
## <a name="sqlconnect"></a>SQLConnect  
 **SQLConnect** 가장 단순한 연결 함수입니다. 이 함수는 데이터 원본 이름, 사용자 ID 및 암호의 세 가지 매개 변수를 허용합니다. 사용 하 여 **SQLConnect** 세 매개 변수는 데이터베이스에 연결 하는 데 필요한 모든 정보를 포함 하는 경우. 이 위해 사용 하 여 데이터 원본 목록을 작성 **SQLDataSources**; 사용자에 게 데이터 원본, 사용자 ID 및 암호입니다; 메시지를 표시 한 다음 호출 **SQLConnect**합니다.  
  
 **SQLConnect** 데이터 원본 이름, 사용자 ID 및 암호는 데이터 원본에 연결 하기에 충분 하 고 ODBC 드라이버가 연결을 만드는 데 필요한 다른 모든 정보가 ODBC 데이터 원본에 포함 되어 있음을 가정 합니다. 와 달리 [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) 및 [SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md), **SQLConnect** 연결 문자열을 사용 하지 않습니다.  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
 **SQLDriverConnect** 데이터 원본 이름, 사용자 ID 및 암호 보다 자세한 정보가 필요한 경우 사용 됩니다. 하나의 매개 변수를 **SQLDriverConnect** 드라이버 관련 정보를 포함 하는 연결 문자열입니다. 사용할 수 있습니다 **SQLDriverConnect** 대신 **SQLConnect** 이유는 다음과 같습니다.  
  
-   연결 시 드라이버 관련 정보를 지정하려는 경우  
  
-   드라이버가 연결 정보를 묻는 메시지를 사용자에게 표시하도록 하려는 경우  
  
-   ODBC 데이터 원본을 사용하지 않고 연결하려는 경우  
  
 **SQLDriverConnect** 연결 문자열에는 일련의 ODBC 드라이버에서 지 원하는 모든 연결 정보를 지정 하는 키워드-값 쌍입니다. 각 드라이버는 드라이버에서 지원하는 모든 연결 정보에 대해 해당 드라이버의 키워드와 함께 표준 ODBC 키워드(DSN, FILEDSN, DRIVER, UID, PWD 및 SAVEFILE)를 지원합니다. **SQLDriverConnect** 사용 하 여 데이터 원본 없이 연결할 수 있습니다. 예를 들어 하는 응용 프로그램 인스턴스에 "DSN 없는" 연결할 수 있도록 디자인 된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 호출할 수 **SQLDriverConnect** 로그인 ID, 암호, 네트워크 라이브러리, 서버 이름을 정의 하는 연결 문자열 에 연결 하 고 기본 데이터베이스를 사용 합니다.  
  
 사용 하는 경우 **SQLDriverConnect**, 필요한 연결 정보에 대 한 사용자에 게 확인 하는 두 가지 옵션이 있습니다.  
  
-   응용 프로그램 대화 상자  
  
     연결 정보를 묻는 메시지를 표시 한 다음 호출 하는 응용 프로그램 대화 상자를 만들 수 있습니다 **SQLDriverConnect** NULL 창 핸들을 사용 하 고 *DriverCompletion* SQL_DRIVER_NOPROMPT로 설정 합니다. 매개 변수를 이렇게 설정하면 ODBC 드라이버가 자체 대화 상자를 열지 않습니다. 이 방법은 응용 프로그램의 사용자 인터페이스를 제어해야 하는 경우 사용합니다.  
  
-   드라이버 대화 상자  
  
     올바른 창 핸들을 전달 하는 응용 프로그램을 코딩할 수 **SQLDriverConnect** 설정 하 고는 *DriverCompletion* 매개 변수를 SQL_DRIVER_COMPLETE, SQL_DRIVER_PROMPT 또는 SQL_DRIVER_COMPLETE_ 필수. 그러면 사용자에게 연결 정보를 묻는 대화 상자를 드라이버에서 생성합니다. 이 방법을 사용할 경우 응용 프로그램 코드가 단순해집니다.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
 **SQLBrowseConnect**처럼 **SQLDriverConnect**, 연결 문자열을 사용 합니다. 그러나 사용 하 여 **SQLBrowseConnect**, 응용 프로그램 실행 시 데이터 원본과 반복적으로 전체 연결 문자열을 생성할 수 있습니다. 이를 통해 응용 프로그램에서는 다음 두 가지 작업이 가능해집니다.  
  
-   해당 정보를 묻는 고유의 대화 상자를 만듭니다. 따라서 해당 사용자 인터페이스에 대한 제어를 유지할 수 있습니다.  
  
-   특정 드라이버에서 사용할 수 있는 데이터 원본을 몇 개의 단계에 따라 시스템에서 찾습니다.  
  
     예를 들어 사용자는 먼저 네트워크에서 서버를 찾아서 선택한 다음 이 서버에서 드라이버가 액세스할 수 있는 데이터베이스를 찾습니다.  
  
 때 **SQLBrowseConnect** 성공적으로 연결을 완료에 대 한 후속 호출에서 사용할 수 있는 연결 문자열을 반환 **SQLDriverConnect**합니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 항상 SQL_SUCCESS_WITH_INFO를 성공적인 반환 **SQLConnect**, **SQLDriverConnect**, 또는 **SQLBrowseConnect**합니다. ODBC 응용 프로그램 호출 하는 경우 **SQLGetDiagRec** SQL_SUCCESS_WITH_INFO를 받은 후 다음과 같은 메시지를 받을 수 있습니다.  
  
 5701  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 데이터 원본에 정의된 기본 데이터베이스 또는 데이터 원본에 기본 데이터베이스가 없는 경우 연결에 사용된 로그인 ID에 대해 정의된 기본 데이터베이스에 사용자의 컨텍스트를 가져옴을 나타냅니다.  
  
 5703  
 서버에서 사용 중인 언어를 나타냅니다.  
  
 다음 예에서는 시스템 관리자가 연결을 성공적으로 수행한 경우 반환되는 메시지를 보여 줍니다.  
  
```  
szSqlState = "01000", *pfNativeError = 5701,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed database context to 'pubs'."  
szSqlState = "01000", *pfNativeError = 5703,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed language setting to 'us_english'."  
```  
  
 메시지 5701 및 5703은 정보 메시지일 뿐이므로 무시해도 됩니다. 그러나 5701이나 5703 이외의 메시지가 반환될 수 있으므로 SQL_SUCCESS_WITH_INFO 반환 코드를 주의해서 검토해야 합니다. 예를 들어의 인스턴스를 실행 하는 서버에 연결 하는 드라이버 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오래 된 카탈로그 저장 프로시저를 통해 반환 오류 중 하나가 **SQLGetDiagRec** sql_success_with_info를 받은 후:  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 오류 처리에 대 한 응용 프로그램의 함수가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 호출 해야 **SQLGetDiagRec** sql_no_data가 반환 될 때까지 합니다. 사용 되지 않는 모든 메시지에는 적용 한 다음 해야는 *pfNative* 코드가 5701 또는 5703 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server와 통신 &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  