---
title: "연결 속성 설정 | Microsoft Docs"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1b62700-f046-488d-bd6b-a5cd8fc345b7
caps.latest.revision: 154
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 56dbb81f9d30ccb41a6247c4fefda9d6ecd703a6
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="setting-the-connection-properties"></a>연결 속성 설정
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  연결 문자열 속성을 지정하는 방식에는 여러 가지가 있습니다.  
  
-   이름으로 = DriverManager 클래스를 사용 하 여 연결할 때 연결 URL의 값 속성입니다.  
  
-   이름으로 = 값 속성에는 *속성* DriverManager 클래스에는 Connect 메서드의 매개 변수입니다.  
  
-   드라이버 데이터 원본의 해당 setter 메서드에 값으로 지정 예를 들어  
  
    ```  
  
    datasource.setServerName(value)  
    datasource.setDatabaseName(value)  
  
    ```  
  
## <a name="remarks"></a>주의  
 속성 이름은 대/소문자를 구분하지 않으며 중복된 속성 이름을 다음 순서로 확인합니다.  
  
1.  API 인수(예: 사용자 및 암호)  
  
2.  속성 컬렉션.  
  
3.  연결 문자열의 마지막 인스턴스.  
  
 또한 속성 이름에 알 수 없는 값이 허용될 뿐 아니라 JDBC 드라이버에서는 이 값의 대/소문자에 대한 유효성을 검사하지 않습니다.  
  
 동의어를 허용하고 중복 속성 이름처럼 순서대로 확인합니다.  
  
 다음 표에서는 JDBC 드라이버에 현재 사용할 수 있는 모든 연결 문자열 속성을 나열합니다.  
  
|속성|형식|기본값|Description|  
|--------------|----------|-------------|-----------------|  
|accessToken|문자열|null|액세스 토큰을 사용 하 여 SQL 데이터베이스에 연결 하려면이 속성을 사용 합니다. **accessToken** 연결 URL을 사용 하 여 설정할 수 없습니다.|  
|applicationIntent|문자열|ReadWrite|서버에 연결할 때 응용 프로그램 작업 유형을 선언합니다. 가능한 값은 **ReadOnly** 및 **ReadWrite**합니다. 자세한 내용은 참조 [고가용성, 재해 복구에 대 한 JDBC 드라이버 지원](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)합니다.|  
|applicationName|문자열<br /><br /> [<=128자]|null|응용 프로그램 이름, 또는 "[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]" 이름을 제공 하지 않으면 경우. 다양 한 특정 응용 프로그램을 식별 하는 데 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 프로 파일링 및 로깅 도구입니다.|  
|인증|문자열|NotSpecified|SQL Server 용 Microsoft JDBC Driver 6.0부터, 속성 (옵션)이 연결에 사용할 SQL 인증 방법을 나타냅니다. 가능한 값은 **ActiveDirectoryIntegrated**, **ActiveDirectoryPassword**, **SqlPassword** 및 기본 **NotSpecified**합니다.<br /><br /> 사용 하 여 **ActiveDirectoryIntegrated** Windows 통합된 인증을 사용 하 여 SQL 데이터베이스에 연결 합니다.<br /><br /> 사용 하 여 **ActiveDirectoryPassword** Azure AD 사용자 이름 및 암호를 사용 하 여 SQL 데이터베이스에 연결 합니다.<br /><br /> 사용 하 여 **SqlPassword** 사용 하 여 SQL Server에 연결 하는 데 **userName**/**사용자** 및 **암호** 속성입니다.<br /><br /> 사용 하 여 **NotSpecified** 필요 하지 않습니다. 이러한 인증 방법의 경우.<br /><br /> **중요:** 인증 ActiveDirectoryIntegrated로 설정 되 면 다음 두 개의 라이브러리 할 경우 설치: **SQLJDBC_AUTH 합니다. DLL** (JDBC 드라이버 패키지에서 사용 가능) 및 SQL Server 용 Azure Active Directory 인증 라이브러리 (**ADALSQL 합니다. DLL**)는 여러 언어로 제공 됩니다 (x86 및 amd64)에서 다운로드 센터에서 [Microsoft SQL Server 용 Microsoft Active Directory 인증 라이브러리](https://www.microsoft.com/en-us/download/details.aspx?id=48742)합니다. JDBC 드라이버 버전 지원 **1.0.2028.318 이상은** 는 ADALSQL에 대 한 합니다. DLL입니다.<br /><br /> **참고:** 인증 속성은로 설정 하면 모든 값 이외의 다른 **NotSpecified**, 기본적으로 드라이버 (SECURE Sockets Layer) 암호화를 사용 합니다.<br /><br /> Azure Active Directory 인증을 구성 하는 방법에 대 한 내용은 방문 [SQL 데이터베이스에서 사용 하 여 Azure Active Directory 인증 연결할](https://azure.microsoft.com/en-us/documentation/articles/sql-database-aad-authentication/)합니다.|  
|authenticationScheme|문자열|"NativeAuthentication"|응용 프로그램에서 사용하려는 통합 보안의 종류를 나타냅니다. 가능한 값은 **JavaKerberos** 및 기본 **NativeAuthentication**합니다.<br /><br /> 사용 하는 경우 **authenticationScheme JavaKerberos =**에서 정규화 된 도메인 이름 (FQDN)을 지정 해야 합니다는 **serverName** 또는 **serverSpn** 속성입니다. 그렇지 않으면 오류가 발생합니다(Kerberos 데이터베이스에서 오류가 발견되지 않았음).<br /><br /> 사용 하 여 대 한 자세한 내용은 **authenticationScheme**, 참조 [Kerberos 통합 인증을 사용 하려면 SQL Server에 연결](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)합니다.|  
|columnEncryptionSetting|문자열<br /><br /> [: "Enabled" &#124; " 사용 안 함 "]|사용 안 함|SQL Server 용 Microsoft JDBC Driver 6.0 상시 암호화 (AE) 기능을 시작 하 여 사용 하도록 "사용"으로 설정 합니다. AE를 사용하도록 설정하면 JDBC 드라이버가 SQL Server의 암호화된 데이터베이스 열에 저장되어 있는 중요한 데이터를 투명하게 암호화하고 암호를 해독합니다.<br /><br /> 참조 [상시 암호화와 JDBC 드라이버를 사용 하 여](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md) 내용을 확인 합니다.<br /><br /> **참고:** 상시 암호화는 SQL Server 2016 이상을 사용할 수 있습니다.|  
|databaseName, database|문자열<br /><br /> [<=128자]|null|연결할 데이터베이스 이름입니다. 지정하지 않으면 기본 데이터베이스에 연결합니다.|  
|disableStatementPooling|boolean<br /><br /> ["true" &#124; " false "]|true|현재는 "true" 값만 지원하며 "false"로 설정할 경우 예외가 발생합니다.|  
|encrypt|boolean<br /><br /> ["true" &#124; " false "]|false|되도록 지정 하려면 "true"로 설정 된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] (SECURE Sockets Layer) 암호화를 사용 하 여 서버 인증서가 설치 되어 있으면 클라이언트와 서버 간에 전송 되는 모든 데이터에 대 한 합니다. 기본값은 False입니다.<br /><br /> SQL Server 용 Microsoft JDBC Driver 6.0부터, 인증이 새 연결 설정을 ''는 기본적으로 SSL 암호화를 사용 합니다. 자세한 내용은 'authentication' 속성을 참조 하십시오.|  
|failoverPartner|문자열|null|데이터베이스 미러링 구성에서 사용되는 장애 조치 서버의 이름입니다. 이 속성은 주 서버에 대한 초기 연결 실패 시 사용되며 초기 연결이 이루어진 후에는 무시됩니다. databaseName 속성과 함께 사용해야 합니다.<br /><br /> **참고:** 드라이버 연결 문자열에서 failoverPartner 속성의 일부로 장애 조치 파트너 인스턴스에 대 한 서버 인스턴스의 포트 번호를 지정할 수 없습니다. 그러나 주 서버 인스턴스의 serverName, instanceName 및 portNumber 속성과 장애 조치(Failover) 파트너 인스턴스의 failoverPartner 속성을 동일한 연결 문자열에 지정할 수는 있습니다.<br /><br /> 에 가상 네트워크 이름을 지정 하는 경우는 **서버** 연결 속성을 데이터베이스 미러링을 사용할 수 없습니다. 참조 [고가용성, 재해 복구에 대 한 JDBC 드라이버 지원](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) 자세한 정보에 대 한 합니다.|  
|hostNameInCertificate|문자열|null|유효성을 검사 하는 데 사용할 호스트 이름에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL 인증서입니다.<br /><br /> HostNameInCertificate 속성이 지정 되지 않았거나 설정 null 인 경우는 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ´ ֲ는 **serverName** 속성 값을 검사할 호스트 이름으로 연결 URL에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL 인증서입니다.<br /><br /> **참고:** 와 함께에서이 속성은 사용 된 **암호화**/**인증** 속성 및 **trustServerCertificate**속성입니다. 이 속성은 연결에서 Secure Sockets Layer (SSL) 암호화를 사용 하는 경우에 인증서 유효성 검사를 적용 및 **trustServerCertificate** "false"로 설정 합니다. 에 전달 된 값 **hostNameInCertificate** 에 대체 SAN (주체 이름) SSL 연결에 대 한 서버 인증서에 성공 하려면 CN (일반 이름) 또는 DNS 이름과 정확히 일치 합니다. 자세한 내용은 참조 [SSL 지원 이해](../../connect/jdbc/understanding-ssl-support.md)합니다.|  
|INSTANCENAME|문자열<br /><br /> [<=128자]|null|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 연결할 인스턴스 이름입니다. 지정하지 않으면 기본 인스턴스에 연결합니다. instanceName 및 포트를 모두 지정하는 경우에 대해서는 포트 관련 설명을 참조하십시오.<br /><br /> 에 가상 네트워크 이름을 지정 하는 경우는 **서버** 사용할 수 없는 연결 속성을 **instanceName** 연결 속성입니다. 참조 [고가용성, 재해 복구에 대 한 JDBC 드라이버 지원](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) 자세한 정보에 대 한 합니다.|  
|integratedSecurity|boolean<br /><br /> ["true" &#124; " false "]|false|증명에서 Windows 자격 증명을 사용 하려면 "true"로 설정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Windows 운영 체제. "true"로 설정하는 경우 JDBC 드라이버는 컴퓨터 또는 네트워크 로그온 시 이미 제공된 자격 증명에 대해 로컬 컴퓨터 자격 증명 캐시를 검색합니다.<br /><br /> "True"로 설정 (으로 **authenticationscheme JavaKerberos =**) Kerberos 자격 증명에서 사용할 나타내기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]합니다. Kerberos 인증에 대 한 자세한 내용은 참조 하십시오. [Kerberos 통합 인증을 사용 하려면 SQL Server에 연결](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)합니다. <br /><br /> "false"로 설정하는 경우 사용자 이름과 암호를 입력해야 합니다.| 
|keyStoreAuthentication|문자열|null| SQL Server 용 Microsoft JDBC Driver 6.0부터,이 속성을 항상 암호화 된 연결에 대 한 원활 하 게 설정 하는 키 저장소를 식별 하 고 키 저장소에 인증 하는 데 사용 되는 인증 메커니즘을 결정 합니다. SQL Server 용 Microsoft JDBC Driver 6.0 설정에서는 최대 지원 Java 키 저장소의 원활 하 게 설정 해야이 속성을 사용 하 여 "**keyStoreAuthentication JavaKeyStorePassword =**"입니다. 이 속성을 사용 하려면도 해야 설정 하는 참고는 **keyStoreLocation** 및 **keyStoreSecret** Java 키 저장소에 대 한 속성입니다. <br/><br/>자세한 내용은 참조 [상시 암호화와 JDBC 드라이버를 사용 하 여](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396)합니다. 
|keyStoreLocation|문자열|null|때 **keyStoreAuthentication JavaKeyStorePassword =**, **keyStoreLocation** 속성의 경로를 사용 하 여 상시 암호화와 함께 열 마스터 키를 저장 하는 Java keystore 파일 식별 데이터입니다. 참고 경로는 키 저장소 파일 이름을 포함 해야 합니다.<br/><br/>자세한 내용은 참조 [상시 암호화와 JDBC 드라이버를 사용 하 여](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396)합니다.
|keyStoreSecret|문자열|null|때 **keyStoreAuthentication JavaKeyStorePassword =**, **keyStoreSecret** 속성 키 뿐만 아니라 keystore에 사용할 암호를 식별 합니다. Java 키 저장소 키 저장소를 사용 하 여에 대 한 사항에 유의 하 고 키 암호가 동일 해야 합니다.<br/><br/>자세한 내용은 참조 [상시 암호화와 JDBC 드라이버를 사용 하 여](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396)합니다.
|lastUpdateCount|boolean<br /><br /> ["true" &#124; " false "]|true|"true" 값을 설정할 경우 서버에 전달된 SQL 문에서 마지막 업데이트 횟수만 반환되며, 이 값을 단일 SELECT, INSERT 또는 DELETE 문에서 사용하면 서버 트리거로 인한 추가 업데이트 횟수를 무시할 수 있습니다. 이 속성을 "false"로 설정하면 서버 트리거로 인해 반환된 업데이트 횟수를 포함하여 모든 업데이트 횟수가 반환됩니다.<br /><br /> **참고:** 함께 사용 하는 경우에이 속성 적용는 [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) 메서드. 다른 모든 실행 메서드 반환 모든 결과 및 업데이트 횟수입니다. 이 속성은 서버 트리거에서 반환하는 업데이트 횟수에만 영향을 미치고 트리거 실행 중 발생하는 오류 또는 결과 집합에는 영향을 미치지 않습니다.|  
|lockTimeout|int|-1|데이터베이스에서 잠금 시간 초과가 보고될 때까지의 대기 시간(밀리초)입니다. 기본 동작은 무한정 대기하는 것입니다. 이 값을 지정하면 연결의 모든 문에 대해 기본값으로 사용됩니다. **Statement.setQueryTimeout()** 는 특정 문에 대 한 제한 시간을 설정 하는 데 사용할 수 있습니다. 대기 시간이 없음을 나타내는 0을 값으로 지정할 수도 있습니다.|  
|loginTimeout|int [0..65535]|15|드라이버가 연결 실패 제한 시간까지 대기해야 하는 시간(초)입니다. 0 값을 지정하면 기본적으로 15초로 지정되는 시스템 제한 시간이 사용됩니다. 0이 아닌 값은 드라이버가 연결 실패 제한 시간까지 대기해야 하는 시간(초)입니다.<br /><br /> 에 가상 네트워크 이름을 지정 하는 경우는 **서버** 연결 속성을 3 분 이상으로 장애 조치 연결이 성공 하려면에 대 한 충분 한 시간 제한 시간 값을 지정 해야 합니다. 참조 [고가용성, 재해 복구에 대 한 JDBC 드라이버 지원](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) 자세한 정보에 대 한 합니다.|  
|multiSubnetFailover|Boolean|false|항상 지정 **multiSubnetFailover = true** 의 가용성 그룹 수신기에 연결할 때는 [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] 가용성 그룹 또는 [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] 장애 조치 클러스터 인스턴스의 합니다. **multiSubnetFailover = true** 구성 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 의 더 빠른 감지와 (현재) 활성 서버 연결을 제공 하도록 합니다. 가능한 값은 true 및 false입니다. 참조 [고가용성, 재해 복구에 대 한 JDBC 드라이버 지원](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) 자세한 정보에 대 한 합니다.<br /><br /> 프로그래밍 방식으로 액세스할 수 있습니다는 **multiSubnetFailover** 연결 속성에 [getPropertyInfo](../../connect/jdbc/reference/getpropertyinfo-method-sqlserverdriver.md), [getMultiSubnetFailover](../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md), 및 [ setMultiSubnetFailover](../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)합니다.<br /><br /> **참고:** multiSubnetFailover 가용성 그룹 수신기에 연결할 때 true로 설정 해야 더 이상 SQL Server 용 Microsoft JDBC Driver 6.0부터 시작 합니다. 새 속성을 **transparentNetworkIPResolution**를 검색 하 고 (현재) 활성 서버 연결을 제공 기본적으로 활성화 되어 있습니다.|  
|packetSize|int [-1 &#124; 0 &#124; 512..32767]|8000|SQL Server와의 통신에 사용되는 네트워크 패킷 크기로서 바이트 단위로 지정합니다. 값 -1은 서버의 기본 패킷 크기가 사용됨을 나타내고 값 0은 최대값인 32767이 사용됨을 나타냅니다. 이 속성을 허용 범위 이외의 값으로 설정하면 예외가 발생합니다.<br /><br /> **중요:** 암호화가 설정 된 경우 packetSize 속성을 사용 하지 않는 것이 좋습니다 (암호화 = true). 그렇지 않으면 드라이버에서 연결 오류가 발생할 수 있습니다. 자세한 내용은 참조는 [setPacketSize](../../connect/jdbc/reference/setpacketsize-method-sqlserverdatasource.md) 의 메서드는 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) 클래스입니다.|  
|password|문자열<br /><br /> [<=128자]|null|데이터베이스 암호를 연결 하는 SQL 사용자 및 암호를 사용 합니다.<BR/>사용자 이름 및 암호로 Kerberos 연결의 경우 Kerberos 보안 주체 암호를이 속성이 설정 되어 있습니다.|  
|portNumber, port|int [0..65535]|1433|포트를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 수신 대기 합니다. 연결 문자열에 포트 번호가 지정되어 있으면 sqlbrowser에 요청을 보내지 않습니다. 포트와 instanceName을 모두 지정한 경우 지정된 포트로 연결합니다. 그러나는 **instanceName** 유효성을 검사와 포트와 일치 하지 않는 경우 오류가 발생 합니다.<br /><br /> **중요:** 권장는 포트 번호는 항상 지정, 이것이 sqlbrowser를 사용 하 여 보다 더 안전 합니다.|  
|responseBuffering|문자열<br /><br /> ["완전히" &#124; " adaptive "]|adaptive|이 속성이 "adaptive"로 설정되어 있으면 필요할 때 최소한의 데이터가 버퍼링됩니다. 기본 모드는 "adaptive"입니다.<br /><br /> 이 속성이 "full"로 설정되어 있으면 문이 실행될 때 전체 결과 집합을 서버에서 읽습니다.<br /><br /> **참고:** "JDBC 드라이버 버전 1.2에서에서 업그레이드 한 후 기본 버퍼링 동작은 adaptive"가 됩니다. 연결 속성 또는 사용 하 여 responseBufferring 속성을 "full"을 설정 해야 응용 프로그램 "responseBuffering" 속성을 설정 하지 않은 응용 프로그램에서 버전 1.2 기본 동작을 유지 하려는 경우는 [ setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) 의 메서드는 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) 개체입니다.|  
|selectMethod|문자열<br /><br /> ["direct" &#124; " 커서 "]|direct|이 속성을 "cursor"로 설정하면 TYPE_FORWARD_ONLY 및 CONCUR_READ_ONLY 커서에 대한 연결에서 생성된 각 쿼리에 대해 데이터베이스 커서가 만들어집니다. 이 속성은 대개 응용 프로그램에서 클라이언트 메모리에 완전히 집어넣을 수 없는 매우 큰 결과 집합을 생성하는 경우에만 필요합니다. 이 속성을 "cursor"로 설정하면 클라이언트 메모리에 제한된 수의 결과 집합 행만 유지됩니다. 기본 동작은 클라이언트 메모리에 모든 결과 집합 행이 유지되는 것입니다. 이 동작은 응용 프로그램에서 모든 행을 처리하는 경우에 성능 면에서 가장 효과적입니다.|  
|sendStringParametersAsUnicode|boolean<br /><br /> ["true" &#124; " false "]|true|경우는 **sendStringParametersAsUnicode** 속성이 "true", 문자열 매개 변수가 유니코드 형식으로 서버에에서 전송 됩니다.<br /><br /> 경우는 **sendStringParametersAsUnicode** 속성이 "false"로 설정 되어 있으면 문자열 매개 변수가 유니코드가 아닌 ASCII/MBCS 등의 형식에 대 한 서버에 전송 됩니다.<br /><br /> 기본값은 **sendStringParametersAsUnicode** 속성은 "true"입니다.<br /><br /> **참고:** 는 **sendStringParametersAsUnicode** 속성은 매개 변수 값을 보낼 때만 확인 **CHAR**, **VARCHAR**, 또는 **LONGVARCHAR** JDBC 형식입니다. setNString, setNCharacterStream, setNClob 메서드와 같은 새 JDBC 4.0 국가별 문자 메서드 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) 및 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) 항상 클래스 이 속성의 설정에 관계 없이 서버에 유니코드 매개 변수 값을 보냅니다.<br /><br /> 최적의 성능을 얻으려면는 **CHAR**, **VARCHAR**, 및 **LONGVARCHAR** 응용 프로그램에서 설정 해야 JDBC 데이터 형식에는 ** sendStringParametersAsUnicode** 속성을 "false"로 사용 하 여 setString, setCharacterStream, 및의 setClob 비 국가별 문자 메서드는 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) 및 [ SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) 클래스입니다.<br /><br /> 응용 프로그램 설정 하는 경우는 **sendStringParametersAsUnicode** 속성을 "false"로 사용 하 여 서버측 유니코드 데이터에 액세스 하는 비 국가별 문자 메서드 형식 (같은 **nchar**, **nvarchar** 및 **ntext**), 데이터베이스 데이터 정렬에서 비 국가별 문자 메서드가 전달 하는 문자열 매개 변수의 문자를 지원 하지 않으면 일부 데이터가 손실 될 수 있습니다.<br /><br /> 응용 프로그램의 setNString, setNCharacterStream, setNClob 국가별 문자 메서드를 사용 해야는 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) 및 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) 에 대 한 클래스 **NCHAR**, **NVARCHAR**, 및 **LONGNVARCHAR** JDBC 데이터 형식입니다.|  
|sendTimeAsDatetime|boolean<br /><br /> ["true" &#124; " false "]|true|이 속성에 추가 된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] JDBC 드라이버 3.0.<br /><br /> True 이면 java.sql.Time 값이 보내집니다로 서버에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **datetime** 값입니다.<br /><br /> False 이면 java.sql.Time 값이 보내집니다로 서버에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **시간** 값입니다.<br /><br /> **sendTimeAsDatetime** 하 여 프로그래밍 방식으로 수정할 수도 있습니다 [SQLServerDataSource.setSendTimeAsDatetime](../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)합니다.<br /><br /> 이 속성의 기본값은 이후 버전에서 변경될 수 있습니다.<br /><br /> 방식에 대 한 자세한 내용은 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] java.sql.Time 값 구성 하는 서버에 보내기 전에 참조 [java.sql.Time 값 구성 방법에 서버에 보내집니다](../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)합니다.|  
|serverName, server|문자열|null|실행 중인 컴퓨터 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]합니다.<br /><br /> [!INCLUDE[ssHADR](../../includes/sshadr_md.md)] 가용성 그룹의 Virtual Network 이름을 지정할 수도 있습니다. 참조 [고가용성, 재해 복구에 대 한 JDBC 드라이버 지원](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) 자세한 정보에 대 한 합니다.|  
|serverSpn|문자열|null|SQL Server용 Microsoft JDBC Driver 4.2부터는 이 선택적 속성을 사용하여 Java Kerberos 연결에 대한 SPN(서비스 사용자 이름)을 지정할 수 있습니다.  와 함께에서 사용 되는 **authenticationScheme**합니다.<br /><br /> SPN을 지정 하는 것이의 형태로: "MSSQLSvc/fqdn:port@REALM" 여기서 fqdn은 정규화 된 도메인 이름, 포트는 포트 번호 및 REALM은 대문자로의 SQL Server의 Kerberos 영역입니다.<br /><br /> 참고:는 @REALM (Kerberos 구성에 지정 된) 대로 클라이언트의 기본 영역이 SQL Server의 Kerberos 영역과 동일한 경우 선택 사항입니다.<br /><br /> 사용 하 여 대 한 자세한 내용은 **serverSpn** Java Kerberos와 함께 참조 [Kerberos 통합 인증을 사용 하려면 SQL Server에 연결](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)합니다.|  
|serverNameAsACE|boolean<br /><br /> ["true" &#124; " false "]|false|SQL Server용 Microsoft JDBC Driver 6.0부터 이 속성을 "true"로 설정하면 드라이버가 유니코드 서버 이름을 ASCII 호환 인코딩(Punycode)으로 변환해서 연결해야 합니다. 이 설정이 false이면 드라이버는 사용자가 제공한 서버 이름을 사용하여 연결합니다.<br /><br /> 참조 [JDBC 드라이버의 국제 기능](../../connect/jdbc/international-features-of-the-jdbc-driver.md) 내용을 확인 합니다.|  
|TransparentNetworkIPResolution|boolean<br /><br /> ["true" &#124; " false "]|true|이 속성, transparentNetworkIPResolution SQL Server 용 Microsoft JDBC Driver 6.0부터, 더 빠르게 검색 하 고 (현재) 활성 서버 연결을 제공 합니다. 가능한 값은 true와 false와 true 값을 기본값으로 합니다.<br /><br /> SQL Server 용 Microsoft JDBC Driver 6.0, 이전 버전 응용 프로그램을 포함 하도록 연결 문자열을 설정 하려면 했습니다 "multiSubnetFailover = true" AlwaysOn 가용성 그룹에 연결 되었음을 나타냅니다. MultiSubnetFailover 연결 키워드를 true로 설정 하지 않을 응용 프로그램 AlwaysOn 가용성 그룹에 연결 하는 동안 시간 초과가 발생할 수 있습니다. SQL Server 용 Microsoft JDBC Driver 6.0부터, 응용 프로그램 하지 않아도 multiSubnetFailover 더 이상 true로 설정 합니다. <br /><br />**참고:** 경우 transparentNetworkIPResolution = true 이면 연결 시도 처음 사용 하 여 500 밀리초의 시간 제한으로 합니다. MultiSubnetFailover 속성에 의해 사용 된 것과 동일한 제한 시간 논리를 사용 하는 모든 후속 시도 합니다.|  
|columnEncryptionSetting|boolean<br /><br /> ["true" &#124; " false "]|false|SQL Server용 Microsoft JDBC Driver 6.0부터 "true"로 설정하면 AE(상시 암호화) 기능을 사용할 수 있습니다. AE를 사용하도록 설정하면 JDBC 드라이버가 SQL Server의 암호화된 데이터베이스 열에 저장되어 있는 중요한 데이터를 투명하게 암호화하고 암호를 해독합니다.<br /><br /> 참조 [상시 암호화와 JDBC 드라이버를 사용 하 여](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md) 내용을 확인 합니다.<br /><br /> **참고:** 상시 암호화는 SQL Server 2016 버전 이상에서 사용할 수 있습니다.|  
|trustServerCertificate|boolean<br /><br /> ["true" &#124; " false "]|false|되도록 지정 하려면 "true"로 설정 된 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 유효성을 검사 하지 것입니다는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL 인증서.<br /><br /> "True"는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 통신 계층이 SSL을 사용 하 여 암호화 된 경우 SSL 인증서가 자동으로 트러스트 합니다.<br /><br /> "False"는 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 서버 SSL 인증서의 유효성을 검사 합니다. 서버 인증서의 유효성 검사를 실패할 경우 드라이버에서 오류가 발생하고 연결이 종료됩니다. 기본값은 "false"입니다. 에 전달 된 값 **serverName** 성공 하려면 SSL 연결에 대 한 서버 인증서의 주체 대체 이름에서 CN (일반 이름) 또는 DNS 이름과 정확히 일치 합니다. 자세한 내용은 참조 [SSL 지원 이해](../../connect/jdbc/understanding-ssl-support.md)합니다.<br /><br /> **참고:** 와 함께에서이 속성은 사용 된 **암호화**/**인증** 속성입니다. 이 속성 연결에서 SSL 암호화를 사용 하는 경우에만 서버 SSL 인증서 유효성 검사를 적용 합니다.|  
|trustStore|문자열|null|인증서 trustStore 파일에 대한 경로(파일 이름 포함)입니다. trustStore 파일에는 클라이언트에서 신뢰하는 인증서 목록이 포함되어 있습니다.<br /><br /> 이 속성이 지정되지 않았거나 null로 설정된 경우 드라이버에서는 트러스트 관리자 팩터리의 조회 규칙에 따라 사용할 인증서 저장소를 결정합니다.<br /><br /> **기본 SunX509 TrustManagerFactory에서는 다음 검색 순서에 트러스트 자료를 찾으려고 시도:**<br /><br /> "javax.net.ssl.trustStore" JVM(Java Virtual Machine) 시스템 속성에 지정된 파일<br /><br /> "\<java 홈 >/lib/보안/jssecacerts" 파일입니다.<br /><br /> "\<java 홈 >/lib/보안/cacerts" 파일입니다.<br /><br /> <br /><br /> 자세한 내용은 Sun Microsystems 웹 사이트에서 SUNX509 TrustManager 인터페이스 설명서를 참조하십시오.<br /><br /> **참고:** 연결에서 SSL 암호화를 사용 하는 경우에만 인증서 trustStore 조회를 적용이 속성 및 **trustServerCertificate** 속성이 "false"로 설정 되어 있습니다.|  
|trustStorePassword|문자열|null|trustStore 데이터의 무결성을 검사하는 데 사용되는 암호입니다.<br /><br /> trustStore 속성은 설정되어 있지만 trustStorePassword 속성이 설정되어 있지 않는 경우 trustStore의 무결성을 검사하지 않습니다.<br /><br /> trustStore 속성과 trustStorePassword 속성이 모두 지정되어 있지 않는 경우 드라이버에서 JVM 시스템 속성 "javax.net.ssl.trustStore" 및 "javax.net.ssl.trustStorePassword"를 사용합니다. "javax.net.ssl.trustStorePassword" 시스템 속성이 지정되어 있지 않는 경우 trustStore의 무결성을 검사하지 않습니다.<br /><br /> trustStore 속성은 설정되어 있지 않지만 trustStorePassword 속성이 설정되어 있는 경우 JDBC 드라이버에서는 "javax.net.ssl.trustStore"에 지정된 파일을 트러스트 저장소로 사용하여 지정된 trustStorePassword로 트러스트 저장소의 무결성을 검사합니다. 클라이언트 응용 프로그램이 JVM 시스템 속성에 암호를 저장하지 않는 경우 이 방법이 필요할 수 있습니다.<br /><br /> **참고:** 연결에서 SSL 연결을 사용 하는 경우에만 인증서 trustStore 조회를 적용 trustStorePassword 속성 및 **trustServerCertificate** 속성이 "false"로 설정 되어 있습니다.|  
|userName, user|문자열<br /><br /> [<=128자]|null|데이터베이스 사용자는 SQL 사용자 및 암호와 함께 연결 합니다.<BR/>사용자 이름 및 암호로 Kerberos 연결의 경우이 속성은 Kerberos 계정 이름으로 설정 됩니다.|  
|workstationID|문자열<br /><br /> [<=128자]|\<빈 문자열 >|워크스테이션 ID로, 다양 한에서 특정 워크스테이션을 식별 하는 데 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 프로 파일링 및 로깅 도구입니다. 지정 하지 않으면는 \<빈 문자열 > 사용 됩니다.|  
|xopenStates|boolean<br /><br /> ["true" &#124; " false "]|false|"true"로 설정하면 드라이버에서 예외 발생 시 XOPEN 규격 상태 코드를 반환합니다. 기본값은 SQL 99 상태 코드를 반환하는 것입니다.|  
|gsscredential|org.ietf.jgss.GSSCredential|null|SQL Server 용 Microsoft JDBC 드라이버 6.2부터, 사용자 자격 증명을 사용 하 여 Kerberos 제한 위임에 대해이 속성에 전달할 수 있습니다. <BR/>이 프로필은 사용할 수 해야 **integratedSecurity** 으로 **true** 및 **JavaKerberos** **authenticationscheme**합니다.| 
|jaasConfigurationName|문자열|SQLJDBCDriver|SQL Server 용 Microsoft JDBC 드라이버 6.2부터, SQL Server에 연결할 때마다 Kerberos 연결을 설정 하는 자체 JAAS 로그인 구성 파일을 있을 수 있습니다. 로그인 구성 파일의 이름은이 속성을 통해 전달할 수 있습니다. <BR/> 기본적으로 드라이버 설정 속성 `useDefaultCcache = true` IBM Jvm에 대 한 및 `useTicketCache = true` 다른 Jvm에 대 한 합니다.|
|serverPreparedStatementDiscardThreshold|정수|10|서버에서 미처리 핸들 정리에 대 한 호출을 실행 하기 전에 개수 처리 중인 준비 된 문을 삭제 동작 (sp_unprepare) 연결 별로 처리 중인 있을 수 있으므로 제어 합니다. 설정 되어 있으면 < = 1 취소-준비 작업 준비 문에서 닫기 즉시 실행 됩니다. 로 설정 되어 있으면 > 1 sp_unprepare를 너무 자주 호출의 오버 헤드를 방지 하기 위해 이러한 호출을 함께 일괄 처리할 됩니다.|
|enablePrepareOnFirstPreparedStatementCall|boolean<br /><br /> ["true" &#124; " false "]|false|이 구성이 false로 설정 된 경우 준비 된 문을 첫 번째 실행에서 sp_executesql을 호출 하 고 sp_prepexec를 호출 하 고 준비 된 문 핸들을 실제로 설치 발생 하는 두 번째로 실행 되 면 문을 준비 하지 됩니다.|
|statementPoolingCacheSize|정수|10|풀에서 다시 사용할 수 있는 구성 가능한 캐시할 문| 
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 서버 ANSI_DEFAULTS 및 IMPLICIT_TRANSACTIONS를 제외한 연결 속성에 대 한 기본값을 사용 합니다. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 자동으로 ANSI_DEFAULTS를 ON으로 설정 하 고 IMPLICIT_TRANSACTIONS를 OFF로 설정 합니다.  

> [!Note]
> 중요: ActiveDirectoryPassword, 인증을 설정 하는 경우 다음 라이브러리 클래스 경로에 포함 되도록 해야 합니다: [azure-active directory-라이브러리-에-java](https://github.com/AzureAD/azure-activedirectory-library-for-java)합니다. 찾을 수 있습니다 [Maven 리포지토리](https://mvnrepository.com/artifact/com.microsoft.azure/adal4j)합니다. 라이브러리 및 해당 종속성을 다운로드 하는 가장 간단한 방법은 Maven를 사용 하 여: 
 >1. 먼저, Maven 시스템에 설치 
 >2. 이동 하 여 [GitHub 페이지](https://github.com/Microsoft/mssql-jdbc) 드라이버의
 >3. Pom.xml 파일 다운로드
 >4. 라이브러리 및 해당 종속성을 다운로드 하려면 다음 Maven 명령을 실행: mvn 종속성: 복사-종속성
  
## <a name="see-also"></a>관련 항목:  
 [JDBC 드라이버로 SQL Server에 연결](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
 [FIPS 모드](../../connect/jdbc/fips-mode.md)
  
  
