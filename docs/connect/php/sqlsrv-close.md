---
title: sqlsrv_close | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_close
apitype: NA
helpviewer_keywords:
- sqlsrv_close
- API Reference, sqlsrv_close
ms.assetid: 6ac6209c-a134-4f8f-b88b-8eefaa1cbc7f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b56cb6975f7fd7a4367912dcd5101271b611336
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806721"
---
# <a name="sqlsrvclose"></a>sqlsrv_close
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

지정된 연결을 닫고 연결된 리소스를 해제합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
sqlsrv_close( resource $conn )  
```  
  
#### <a name="parameters"></a>매개 변수  
*$conn*: 닫히는 연결입니다.  
  
## <a name="return-value"></a>반환 값  
잘못된 매개 변수를 사용하여 함수를 호출하지 않는 한 부울 값 **true** 입니다. 잘못된 매개 변수를 사용하여 함수를 호출하는 경우에는 **false** 가 반환됩니다.  
  
> [!NOTE]  
> **Null** 은 이 함수에 대해 유효한 매개 변수입니다. 그러면 스크립트에서 함수가 여러 번 호출될 수 있습니다. 예를 들어 오류 조건에서 연결을 닫고 스크립트 끝에서 다시 닫는 경우 **sqlsrv_close**(오류 조건)에 대한 첫 번째 호출은 연결 리소스를 **null**로 설정하기 때문에 **sqlsrv_close**에 대한 두 번째 호출에서 **true**를 반환합니다.  
  
## <a name="example"></a>예제  
다음 예제에서는 연결을 닫습니다. 이 예제에서는 SQL Server가 로컬 컴퓨터에 설치된 것으로 가정합니다. 명령줄에서 예제가 실행될 때 모든 출력은 콘솔에 기록됩니다.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$conn = sqlsrv_connect( $serverName);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
//-----------------------------------------------  
// Perform operations with connection here.  
//-----------------------------------------------  
  
/* Close the connection. */  
sqlsrv_close( $conn);  
echo "Connection closed.\n";  
?>  
```  
  
## <a name="see-also"></a>참고 항목  
[SQLSRV 드라이버 API 참조](../../connect/php/sqlsrv-driver-api-reference.md)

[설명서의 코드 예제 정보](../../connect/php/about-code-examples-in-the-documentation.md)  
  
