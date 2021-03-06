---
title: Azure SQL database에 연결 | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 49645b1f-39b1-4757-bda1-c51ebc375c34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c4caaa9ca14fd2f8eb396ef2c2869ba30bd48420
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602213"
---
# <a name="connecting-to-an-azure-sql-database"></a>Azure SQL 데이터베이스에 연결

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

이 문서에서는 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]를 사용하여 [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]에 연결하는 경우의 문제에 대해 논의합니다. [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] 연결 정보에 대한 자세한 내용은 다음을 참조하세요.  
  
- [SQL Azure 데이터베이스](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)  
  
- [방법: JDBC를 사용하여 SQL Azure에 연결](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java)  

- [Azure Active Directory 인증을 사용하여 연결](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md)  
  
## <a name="details"></a>세부 정보

에 연결할 때는 [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]를 호출 하려면 master 데이터베이스에 연결 해야 **SQLServerDatabaseMetaData.getCatalogs**합니다.  
[!INCLUDE[ssAzure](../../includes/ssazure_md.md)]는 사용자 데이터베이스에서 전체 카탈로그 집합을 반환하는 기능을 지원하지 않습니다. **SQLServerDatabaseMetaData.getCatalogs** sys.databases 뷰를 사용 하 여 카탈로그를 가져옵니다. 권한 설명을 참조 하세요 [sys.databases (SQL Azure 데이터베이스)](https://go.microsoft.com/fwlink/?LinkId=217396) 알아야 **SQLServerDatabaseMetaData.getCatalogs** 동작을 [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]입니다.  
  
## <a name="connections-dropped"></a>연결이 삭제됨

[!INCLUDE[ssAzure](../../includes/ssazure_md.md)]에 연결할 때 비활성 기간 후 방화벽과 같은 네트워크 구성 요소에서 유휴 연결을 종료할 수 있습니다. 유휴 연결에는  

- 네트워크 장치에서 연결을 삭제할 수 있는 TCP 계층에서 유휴 연결(Idle at the TCP layer) 및  

- TCP **keepalive** 메시지가 발생할 수 있으나(TCP 쪽에서 유휴 상태가 아닌 연결하기) 30분간 활성 쿼리가 없는 SQL Azure 게이트웨이에서 유휴 연결(Idle by the SQL Azure Gateway)의 두 가지 종류가 있습니다. 이 시나리오에서 게이트웨이가 TDS 연결이 30분간 유휴 상태이고 연결을 종료됨을 결정합니다.  
  
네트워크 구성 요소에서 유휴 연결을 삭제하지 않도록 하려면 드라이버가 로드된 운영 체제에서 다음 레지스트리 설정(또는 Windows가 아닌 경우 이에 해당하는 설정)을 설정해야 합니다.  
  
|레지스트리 설정|권장 값|  
|----------------------|-----------------------|  
|HKEY_LOCAL_MACHINE \ 시스템 \ CurrentControlSet \ 서비스 \ Tcpip \ 매개 변수 \ KeepAliveTime|30000|  
|HKEY_LOCAL_MACHINE \ 시스템 \ CurrentControlSet \ 서비스 \ Tcpip \ 매개 변수 \ KeepAliveInterval|1000|  
|HKEY_LOCAL_MACHINE \ 시스템 \ CurrentControlSet \ 서비스 \ Tcpip \ 매개 변수 \ TcpMaxDataRetransmissions|10|  
  
레지스트리 설정을 적용하려면 컴퓨터를 다시 시작합니다.  

Windows 실행 시 이 작업을 수행하기 위해 Azure는 시작 태스크를 생성하여 레지스트리 키를 추가합니다.  예를 들어 다음과 같은 시작 태스크를 서비스 정의 파일에 추가합니다.  

```xml
<Startup>  
    <Task commandLine="AddKeepAlive.cmd" executionContext="elevated" taskType="simple">  
    </Task>  
</Startup>  
```

그런 다음 프로젝트에 AddKeepAlive.cmd 파일을 추가합니다. "출력 디렉터리로 복사" 설정을 항상 복사로 설정합니다. 다음은 예제 AddKeepAlive.cmd 파일입니다.  

```bat
if exist keepalive.txt goto done  
time /t > keepalive.txt  
REM Workaround for JDBC keep alive on SQL Azure  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveTime /t REG_DWORD /d 30000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveInterval /t REG_DWORD /d 1000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v TcpMaxDataRetransmissions /t REG_DWORD /d 10 >> keepalive.txt  
shutdown /r /t 1  
:done  
```

## <a name="appending-the-server-name-to-the-userid-in-the-connection-string"></a>연결 문자열에서 서버 이름을 사용자 ID에 추가  

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]의 4.0 버전 이전에는 [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]에 연결할 때 연결 문자열에서 서버 이름을 사용자 ID에 추가해야 했습니다. user@servername)을 입력합니다. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 4.0 버전부터 연결 문자열에서 @servername을 사용자 ID에 추가할 필요가 없게 되었습니다.  
  
## <a name="using-encryption-requires-setting-hostnameincertificate"></a>암호화 사용에 hostNameInCertificate 설정 필요

에 연결할 때는 [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]를 지정 해야 **hostNameInCertificate** 지정 하는 경우 **암호화 = true**합니다. (연결 문자열에 서버 이름이 *shortName*. *domainName*로 설정 합니다 **hostNameInCertificate** 속성을 \*. *domainName*.)  
  
예를 들어 다음과 같이 사용할 수 있습니다.  

```java
jdbc:sqlserver://abcd.int.mscds.com;databaseName= myDatabase;user=myName;password=myPassword;encrypt=true;hostNameInCertificate= *.int.mscds.com;  
```

## <a name="see-also"></a>참고 항목

[JDBC 드라이버로 SQL Server에 연결](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
