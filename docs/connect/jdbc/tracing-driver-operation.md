---
title: "드라이버 작업 추적 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 723aeae7-6504-4585-ba8b-3525115bea8b
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e364f990cc2428d771f3bc57015df0636e23fbfb
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="tracing-driver-operation"></a>드라이버 작업 추적
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 추적 또는 로깅 기능 응용 프로그램에서 사용 하는 경우 문제 및 JDBC 드라이버 문제를 해결 하기 위해 사용할 수 있도록 지원 합니다. 추적을 사용 하려면 JDBC 드라이버는로 거와 LogRecord 개체를 만들기 위한 클래스 집합을 제공 하는 java.util.logging의 로깅 Api를 사용 합니다.  
  
> [!NOTE]  
>  JDBC 드라이버에 포함된 네이티브 구성 요소(sqljdbc_xa.dll)의 경우 BID(Built-In Diagnostics) 프레임워크를 사용하여 추적 기능을 활성화합니다. BID에 대 한 정보를 참조 하십시오. [SQL Server의 데이터 액세스 추적](http://go.microsoft.com/fwlink/?LinkId=70042)합니다.  
  
 응용 프로그램을 개발할 때 LogRecord 개체에 전달 되어 처리기 개체에 대 한 처리를 만들고로 거 개체에 대 한 호출을 만들 수 있습니다. 로 거 및 처리기 개체가 로깅 수준, 둘 다 사용 하 고 어떤 LogRecords 제어 하기 위해 로깅 필터를 처리 하는 선택적으로 합니다. 로깅 작업이 완료 되 면 처리기 개체 로그 정보를 게시 포맷터 개체를 선택적으로 사용할 수 있습니다.  
  
 기본적으로 java.util.logging 프레임워크는 출력을 파일에 작성합니다. 이 출력 로그 파일은 JDBC 드라이버가 실행 중인 컨텍스트에 대한 쓰기 권한이 있어야 합니다.  
  
> [!NOTE]  
>  프로그램 추적에 여러 로깅 개체를 사용하는 방법에 대한 자세한 내용은 Sun Microsystems 웹 사이트의 Java Logging APIs 설명서(영문)를 참조하십시오.  
  
 다음 섹션에서는 로깅 수준 및 로깅 가능한 범주를 설명하고 응용 프로그램에서 추적 기능을 활성화하는 방법에 대한 정보를 제공합니다.  
  
## <a name="logging-levels"></a>로깅 수준  
 작성되는 모든 로그 메시지에는 연관된 로깅 수준이 있습니다. 에 정의 된 로그 메시지의 중요도 결정 하는 로깅 수준을 **수준** java.util.logging의 클래스. 한 수준에서 로깅을 설정하면 상위 수준의 로깅도 모두 설정됩니다. 이 섹션에서는 공용 로깅 범주 및 내부 로깅 범주의 로깅 수준에 대해 설명합니다. 로깅 범주에 대한 자세한 내용은 이 항목의 로깅 범주 섹션을 참조하십시오.  
  
 다음 표에서는 공용 로깅 범주에 대해 사용할 수 있는 각 로깅 수준에 대해 설명합니다.  
  
|이름|Description|  
|----------|-----------------|  
|SEVERE|심각한 오류를 나타내는 가장 높은 로깅 수준입니다. JDBC 드라이버에서 이 수준은 오류 및 예외를 보고하는 데 사용합니다.|  
|WARNING|잠재적인 문제를 의미합니다.|  
|INFO|정보 메시지를 제공합니다.|  
|CONFIG|구성 메시지를 제공합니다. JDBC 드라이버는 현재 구성 메시지를 제공하지 않습니다.|  
|FINE|공용 메서드에서 발생한 모든 예외를 포함하는 기본 추적 정보를 제공합니다.|  
|FINER|모든 공용 메서드 진입점 및 진출점과 관련 매개 변수 데이터 형식 및 공용 클래스의 모든 공용 속성을 포함하는 자세한 추적 정보를 제공합니다. 또한 매개 변수, 출력 매개 변수 및 CLOB, BLOB, NCLOB, Reader 제외한 메서드 반환 값을 입력 \<스트림 > 값 형식을 반환 합니다.|  
|FINEST|매우 자세한 추적 정보를 제공합니다. 이 수준은 가장 낮은 로깅 수준입니다.|  
|OFF|로깅을 해제합니다.|  
|ALL|모든 메시지의 로깅을 활성화합니다.|  
  
 다음 표에서는 내부 로깅 범주에 대해 사용할 수 있는 각 로깅 수준에 대해 설명합니다.  
  
|이름|Description|  
|----------|-----------------|  
|SEVERE|심각한 오류를 나타내는 가장 높은 로깅 수준입니다. JDBC 드라이버에서 이 수준은 오류 및 예외를 보고하는 데 사용합니다.|  
|WARNING|잠재적인 문제를 의미합니다.|  
|INFO|정보 메시지를 제공합니다.|  
|FINE|기본 개체 생성 및 소멸을 포함한 추적 정보를 제공합니다. 또한 공용 메서드에서 발생한 모든 예외에 대한 정보도 제공합니다.|  
|FINER|모든 공용 메서드 진입점 및 진출점과 관련 매개 변수 데이터 형식 및 공용 클래스의 모든 공용 속성을 포함하는 자세한 추적 정보를 제공합니다. 또한 매개 변수, 출력 매개 변수 및 CLOB, BLOB, NCLOB, Reader 제외한 메서드 반환 값을 입력 \<스트림 > 값 형식을 반환 합니다.<br /><br /> 로깅 범주는 JDBC 드라이버 버전 1.2에에서 포함 했으며 로깅 수준이 FINE: [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md), [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), XA 및 [SQLServerDataSource ](../../connect/jdbc/reference/sqlserverdatasource-class.md). 이 범주들은 버전 2.0 릴리스에서부터 FINER 수준으로 업그레이드되었습니다.|  
|FINEST|매우 자세한 추적 정보를 제공합니다. 이 수준은 가장 낮은 로깅 수준입니다.<br /><br /> JDBC 드라이버 버전 1.2에 포함된 로깅 범주 중 로깅 수준이 FINEST인 범주는 TDS.DATA 및 TDS.TOKEN입니다. 버전 2.0 릴리스에서부터 FINEST 로깅 수준이 유지됩니다.|  
|OFF|로깅을 해제합니다.|  
|ALL|모든 메시지의 로깅을 활성화합니다.|  
  
## <a name="logging-categories"></a>로깅 범주  
 로 거 개체를 만들 때 명명 된 엔터티나 범주가 로그 정보를 가져올에 관심이 어떤 개체를 지시 해야 합니다. JDBC 드라이버는 com.microsoft.sqlserver.jdbc 드라이버 패키지에 정의된 다음 공용 로깅 범주를 지원합니다.  
  
|이름|Description|  
|----------|-----------------|  
|연결|메시지를 로그에 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINER로 설정할 수 있습니다.|  
|인수를 제거합니다.|메시지를 로그에 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINER로 설정할 수 있습니다.|  
|DataSource|메시지를 로그에 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINE으로 설정할 수 있습니다.|  
|ResultSet|메시지를 로그에 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINER로 설정할 수 있습니다.|  
|드라이버|메시지를 로그에 [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINER로 설정할 수 있습니다.|  
  
 Microsoft JDBC 드라이버 버전 2.0 이상에서는 드라이버가 다음 내부 로깅 범주에 대한 로깅 지원을 포함하는 com.microsoft.sqlserver.jdbc.internals 패키지를 제공합니다.  
  
|이름|Description|  
|----------|-----------------|  
|AuthenticationJNI|Windows에 대 한 로그 메시지 통합 인증 문제 (때는 **authenticationScheme** 연결 속성이 암시적 또는 명시적으로로 설정 되어 **NativeAuthentication**).<br /><br /> 응용 프로그램에서는 로깅 수준을 FINEST 및 FINE으로 설정할 수 있습니다.|  
|SQLServerConnection|메시지를 로그에 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINE 및 FINER로 설정할 수 있습니다.|  
|SQLServerDataSource|메시지를 로그에 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md), [SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md), 및 [SQLServerPooledConnection](../../connect/jdbc/reference/sqlserverpooledconnection-class.md) 클래스입니다.<br /><br /> 응용 프로그램에서는 로깅 수준을 FINER로 설정할 수 있습니다.|  
|InputStream|java.io.InputStream, java.io.Reader 및 varchar, nvarchar, varbinary 데이터 형식 등의 최대값 지정자가 있는 데이터 형식과 관련된 메시지를 로깅합니다. <br /><br /> 응용 프로그램에서는 로깅 수준을 FINER로 설정할 수 있습니다.|  
|SQLServerException|메시지를 로그에 [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINE으로 설정할 수 있습니다.|  
|SQLServerResultSet|메시지를 로그에 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINE, FINER 및 FINEST로 설정할 수 있습니다.|  
|SQLServerStatement|메시지를 로그에 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINE, FINER 및 FINEST로 설정할 수 있습니다.|  
|XA|모든 XA 트랜잭션에 대 한 메시지를 로그에 [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINE 및 FINER로 설정할 수 있습니다.|  
|KerbAuthentication|유형 4 Kerberos 인증 문제에 관한 메시지를 로깅합니다 (때는 **authenticationScheme** 연결 속성이로 설정 되어 **JavaKerberos**). 응용 프로그램에서는 로깅 수준을 FINE 또는 FINER로 설정할 수 있습니다.|  
|TDS.DATA|드라이버와 SQL 서버 간 TDS 프로토콜 수준 대화를 포함하는 메시지를 로깅합니다. 주고받는 각 TDS 패킷의 자세한 내용이 ASCII 및 16진수로 로깅됩니다. 로그인 자격 증명(사용자 이름 및 암호)은 로깅되지 않습니다. 다른 모든 데이터는 로깅됩니다.<br /><br /> 이 범주는 매우 자세한 메시지를 작성하기 때문에 로깅 수준을 FINEST로 설정해야만 사용할 수 있습니다.|  
|TDS.Channel|이 범주는 SQL 서버와의 TCP 통신 채널의 동작을 추적합니다. 로깅된 메시지는 소켓을 열고 닫는 동작과 읽고 쓰는 동작을 포함합니다. 또한 SQL 서버와의 SSL(Secure Sockets Layer) 연결 설정과 관련된 메시지를 추적합니다.<br /><br /> 이 범주는 로깅 수준을 FINE, FINER 또는 FINEST로 설정해야만 사용할 수 있습니다.|  
|TDS.Writer|이 범주는 TDS 채널에 대한 쓰기 동작을 추적합니다. 내용이 아닌, 쓰기 길이만 추적됩니다. 또한 이 범주에서는 문의 실행을 취소하기 위해 주의 신호가 서버로 전송되는 경우의 문제를 추적합니다.<br /><br /> 이 범주는 로깅 수준을 FINEST로 설정해야만 사용할 수 있습니다.|  
|TDS.Reader|FINEST 수준에서 이 범주는 TDS 채널의 특정 읽기 동작을 추적합니다. FINEST 수준에서는 추적이 매우 자세할 수 있습니다. WARNING 및 SEVERE 수준에서 이 범주는 드라이버가 연결을 닫기 전 SQL 서버에서 잘못된 TDS 프로토콜을 수신하는 경우 추적을 수행합니다.<br /><br /> 이 범주는 로깅 수준을 FINER 또는 FINEST로 설정해야만 사용할 수 있습니다.|  
|TDS.Command|이 범주는 낮은 수준의 상태 전환 및 기타 정보 등 TDS 명령 실행과 관련 된 추적 [!INCLUDE[tsql](../../includes/tsql_md.md)] 문 실행, ResultSet 커서 인출, 커밋, 및 등입니다.<br /><br /> 이 범주는 로깅 수준을 FINEST로 설정해야만 사용할 수 있습니다.|  
|TDS.TOKEN|이 범주는 TDS 패킷 내의 토큰만 로깅하며 TDS.DATA 범주보다 정보가 덜 자세합니다. 이 범주는 로깅 수준을 FINEST로 설정해야만 사용할 수 있습니다.<br /><br /> FINEST 수준에서 이 범주는 응답에서 처리되는 TDS 토큰을 추적합니다. SEVERE 수준에서 이 범주는 잘못된 TDS 토큰이 발견되는 경우 추적을 수행합니다.|  
|SQLServerDatabaseMetaData|메시지를 로그에 [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINE으로 설정할 수 있습니다.|  
|SQLServerResultSetMetaData|메시지를 로그에 [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINE으로 설정할 수 있습니다.|  
|SQLServerParameterMetaData|메시지를 로그에 [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINE으로 설정할 수 있습니다.|  
|SQLServerBlob|메시지를 로그에 [SQLServerBlob](../../connect/jdbc/reference/sqlserverblob-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINE으로 설정할 수 있습니다.|  
|SQLServerClob|메시지를 로그에 [SQLServerClob](../../connect/jdbc/reference/sqlserverclob-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINE으로 설정할 수 있습니다.|  
|SQLServerSQLXML|내부 SQLServerSQLXML 클래스의 메시지를 로깅합니다. 응용 프로그램에서는 로깅 수준을 FINE으로 설정할 수 있습니다.|  
|SQLServerDriver|메시지를 로그에 [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINE으로 설정할 수 있습니다.|  
|SQLServerNClob|메시지를 로그에 [SQLServerNClob](../../connect/jdbc/reference/sqlservernclob-class.md) 클래스입니다. 응용 프로그램에서는 로깅 수준을 FINE으로 설정할 수 있습니다.|  
  
## <a name="enabling-tracing-programmatically"></a>프로그래밍 방식으로 추적 활성화  
 추적에 기록 될로 거 개체를 만들고 범주를 나타내는 하 여 프로그래밍 방식으로 설정할 수 있습니다. 예를 들어 다음 코드에서는 SQL 문의 로깅을 활성화하는 방법을 보여 줍니다.  
  
```  
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc.Statement");  
logger.setLevel(Level.FINER);  
```  
  
 코드에서 로깅을 해제하려면 다음을 사용합니다.  
  
```  
logger.setLevel(Level.OFF);  
```  
  
 사용 가능한 모든 범주를 로깅하려면 다음을 사용합니다,  
  
```  
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc");  
logger.setLevel(Level.FINE);  
```  
  
 특정 범주를 로깅하지 않으려면 다음을 사용합니다.  
  
```  
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc.Statement");  
logger.setLevel(Level.OFF);  
```  
  
## <a name="enabling-tracing-by-using-the-loggingproperties-file"></a>Logging.Properties 파일을 사용하여 추적 활성화  
 사용 하 여 추적도 설정할 수 있습니다는 `logging.properties` 에서 찾을 수 있는 파일의 `lib` Java Runtime Environment (JRE) 설치의 디렉터리입니다. 이 파일은 추적 기능을 활성화할 때 사용할 로거 및 처리기의 기본 값을 설정하는 데 사용할 수 있습니다.  
  
 다음은에서 만들 수 있는 설정의 예는 `logging.properties` 파일:  
  
```  
# Specify the handler, the handlers will be installed during VM startup.  
handlers= java.util.logging.FileHandler  
  
# Default global logging level.  
.level= OFF  
  
# default file output is in user's home directory.  
java.util.logging.FileHandler.pattern = %h/java%u.log  
java.util.logging.FileHandler.limit = 5000000  
java.util.logging.FileHandler.count = 20  
java.util.logging.FileHandler.formatter = java.util.logging.SimpleFormatter  
java.util.logging.FileHandler.level = FINEST  
  
# Facility specific properties.  
com.microsoft.sqlserver.jdbc.level=FINEST  
  
```  
  
> [!NOTE]  
>  속성을 설정할 수는 `logging.properties` java.util.logging의 일부인 LogManager 개체를 사용 하 여 파일입니다.  
  
## <a name="see-also"></a>관련 항목:  
 [JDBC 드라이버 관련 문제 진단](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  