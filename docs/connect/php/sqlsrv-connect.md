---
title: sqlsrv_connect | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_connect
apitype: NA
helpviewer_keywords:
- connecting to the server
- API Reference, sqlsrv_connect
- connection pooling support
- sqlsrv_connect
ms.assetid: 37836b49-258e-45ce-9549-b8bd85d6952d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a8df39220a9d3ee2286e4ed86610790e20a3b78c
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51601193"
---
# <a name="sqlsrvconnect"></a>sqlsrv_connect
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

연결 리소스를 만들고 연결을 엽니다. 기본적으로 Windows 인증을 사용하여 연결을 시도합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
sqlsrv_connect( string $serverName [, array $connectionInfo])  
```  
  
#### <a name="parameters"></a>매개 변수  
*$serverName*: 연결이 설정되는 서버의 이름을 지정하는 문자열입니다. 인스턴스 이름(예: "myServer\instanceName") 또는 포트 번호(예: "myServer 1521")가 이 문자열의 일부로 포함될 수 있습니다. 이 매개 변수에 사용할 수 있는 옵션에 대한 자세한 내용은 [SQL Native Client에서 연결 문자열 키워드 사용](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)의 ODBC 드라이버 연결 문자열 키워드 섹션에서 서버 키워드를 참조하세요.  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]의 버전 3.0부터는 `"(localdb)\instancename"`을 사용하여 LocalDB 인스턴스를 지정할 수도 있습니다. 자세한 내용은 [LocalDB에 대 한 지원을](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)합니다.  
  
또한 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]의 버전 3.0부터 AlwaysOn 가용성 그룹에 연결하기 위해 가상 네트워크 이름을 지정할 수 있습니다. 에 대 한 자세한 내용은 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 에 대 한 지원 [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]를 참조 하십시오 [High Availability, Disaster Recovery에 대 한 지원](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)합니다.  
  
*$connectionInfo* [선택 사항]: 연결 특성을 포함하는 결합형 **배열**(예: **배열**("Database"=> "AdventureWorks"))입니다. 배열에 대해 지원되는 키 목록은 [Connection Options](../../connect/php/connection-options.md) 을 참조하세요.  
  
## <a name="return-value"></a>반환 값  
PHP 연결 리소스입니다. 연결을 만들 수 없고 열 수 없으면 **false** 가 반환됩니다.  
  
## <a name="remarks"></a>Remarks  
*UID* 및 *PWD* 키에 대한 값이 선택적 *$connectionInfo* 매개 변수에 지정되지 않은 경우 Windows 인증을 사용하여 연결을 시도합니다. 서버에 연결하는 방법에 대한 자세한 내용은 [How to: Connect Using Windows Authentication](../../connect/php/how-to-connect-using-windows-authentication.md) 및 [How to: Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md)을 참조하세요.  
  
## <a name="example"></a>예제  
다음 예제에서는 Windows 인증을 사용하여 연결을 만들고 엽니다. 이 예제에서는 SQL Server 및 [AdventureWorks](https://www.codeplex.com/SqlServerSamples) 데이터베이스가 로컬 컴퓨터에 설치된 것으로 가정합니다. 모든 출력은 명령줄에서 예제가 실행될 때 콘솔에 기록됩니다.  
  
```  
<?php  
/*  
Connect to the local server using Windows Authentication and specify  
the AdventureWorks database as the database in use. To connect using  
SQL Server Authentication, set values for the "UID" and "PWD"  
 attributes in the $connectionInfo parameter. For example:  
$connectionInfo = array("UID" => $uid, "PWD" => $pwd, "Database"=>"AdventureWorks");  
*/  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if( $conn )  
{  
     echo "Connection established.\n";  
}  
else  
{  
     echo "Connection could not be established.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
//-----------------------------------------------  
// Perform operations with connection.  
//-----------------------------------------------  
  
/* Close the connection. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>참고 항목  
[SQLSRV 드라이버 API 참조](../../connect/php/sqlsrv-driver-api-reference.md)

[Connecting to the Server](../../connect/php/connecting-to-the-server.md)

[설명서의 코드 예제 정보](../../connect/php/about-code-examples-in-the-documentation.md)  
  
