---
title: "SQL Server Express LocalDB 헤더 및 버전 정보 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: localdb
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apilocation: sqluserinstance.dll
ms.assetid: 506b5161-b902-4894-b87b-9192d7b1664a
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1b349093cc92fdfced91476f69bf98b60384e783
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-express-localdb-header-and-version-information"></a>SQL Server Express LocalDB 헤더 및 버전 정보
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]SQL Server Express LocalDB 인스턴스 API;에 대 한 별도 헤더 파일이 없습니다. LocalDB 함수 서명 및 오류 코드는 SQL Server Native Client 헤더 파일 (sqlncli.h)에 정의 됩니다. LocalDB 인스턴스 API를 사용하려면 프로젝트에 sqlncli.h 헤더 파일을 포함해야 합니다.  
  
## <a name="localdb-versioning"></a>LocalDB 버전 관리  
 LocalDB 설치에서는 SQL Server 주 버전당 단일 이진 파일 집합을 사용합니다. 이러한 LocalDB 버전은 독립적으로 유지되고 패치됩니다. 따라서 사용자가 사용할 LocalDB 기준선 릴리스(주 SQL Server 버전)를 직접 지정해야 합니다. .NET Framework에서 정의 된 표준 버전 형식에 지정 된 버전은 **System.Version** 클래스:  
  
 *[.build [.revision]]*  
  
 버전 문자열의 처음 두 번호 (*주요* 및 *부*)는 필수입니다. 버전 문자열의 마지막 두 번호 (*빌드* 및 *개정*)는 선택 사항이 며 기본적으로 0으로는 사용자가 하는 경우. 즉, 사용자가 LocalDB 버전 번호로 "12.2"만 지정한 경우 "12.2.0.0"으로 지정한 것으로 처리됩니다.  
  
 LocalDB 설치에 대한 버전은 SQL Server 인스턴스 레지스트리 키 아래의 MSSQLServer\CurrentVersion 레지스트리 키에 정의됩니다. 예를 들면 다음과 같습니다.  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL13E.LOCALDB\ MSSQLServer\CurrentVersion: "CurrentVersion"="12.0.2531.0"  
```  
  
 동일한 워크스테이션에서 여러 LocalDB 버전을 함께 설치할 수 있습니다. 그러나 사용자 코드 항상 사용 하 여 사용 가능한 최신 **SQLUserInstance** DLL 로컬 컴퓨터에 LocalDB 인스턴스에 연결 하려고 합니다.  
  
## <a name="locating-the-sqluserinstance-dll"></a>SQLUserInstance DLL 찾기  
 찾을 **SQLUserInstance** DLL, 클라이언트 공급자 사용 하 여 다음 레지스트리 키:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions]  
```  
  
 이 키 아래에는 컴퓨터에 설치된 각 LocalDB 버전별로 하나씩 키 목록이 있습니다. 이러한 각 키의 이름이 지정 된 형식의 LocalDB 버전 번호로  *\<주 버전 >*. *\<부 버전 >* (키에 대 한 예를 들어 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 13.0 라는). 각 버전 키 아래에는 해당 버전과 함께 설치되는 SQLUserInstance.dll 파일의 전체 경로를 정의하는 `InstanceAPIPath` 이름-값 쌍이 있습니다. 다음 예제에서는 LocalDB 버전 11.0 및 13.0 설치 되어 있는 컴퓨터에 대 한 레지스트리 항목을 보여 줍니다.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"]  
```  
  
 클라이언트 공급자는 설치 된 모든 버전 및 로드 중에서 최신 버전을 찾아야 합니다는 **SQLUserInstance** DLL 파일에서 연결 된 `InstanceAPIPath` 값입니다.  
  
### <a name="wow64-mode-on-64-bit-windows"></a>64비트 Windows의 WOW64 모드  
 64비트 LocalDB 설치에는 WOW64(Windows-32-on-Windows-64) 모드에서 실행 중인 32비트 응용 프로그램에서 LocalDB를 사용할 수 있도록 해주는 추가 레지스트리 키 집합이 있습니다. 특히 64비트 Windows에서 LocalDB MSI는 다음과 같은 레지스트리 키를 만듭니다.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"]  
  
```  
  
 64 비트 프로그램은는 `Installed Versions` 키의 64 비트 버전을 가리키는 값이 표시 됩니다는 **SQLUserInstance** DLL의 경우 32 비트 프로그램 (WOW64 모드의 64 비트 Windows에서 실행)으로 자동으로 리디렉션되지 것입니다 동안는 `Installed Versions` 키 아래에 `Wow6432Node` 하이브 합니다. 이 키의 32 비트 버전을 가리키는 값이 포함 된 **SQLUserInstance** DLL입니다.  
  
## <a name="using-localdbdefineproxyfunctions"></a>LOCALDB_DEFINE_PROXY_FUNCTIONS 사용  
 자동으로 검색 하 고 로드 하는 localdb_define_proxy_functions 상수를 정의 하는 LocalDB 인스턴스 API는 **SqlUserInstance** DLL입니다.  
  
 이 상수에 의해 설정되는 코드 섹션은 각 LocalDB API에 대한 프록시 구현을 제공합니다. 프록시 구현은 공통 함수를 사용 하 여 설치 된 최신 버전의 진입점에 바인딩할 **SqlUserInstance** DLL의 경우 다음 요청을 전달 하 고 있습니다.  
  
 프록시 함수는 sqlncli.h 파일을 포함하기 전에 LOCALDB_DEFINE_PROXY_FUNCTIONS 상수가 사용자 코드에 정의되는 경우에만 사용됩니다. 이 상수는 모든 API 진입점에 대해 외부 함수 이름을 정의하기 때문에 원본 모듈(.cpp file) 하나에만 정의해야 합니다. 이 상수는 각 LocalDB API에 대한 프록시 구현을 제공합니다.  
  
 다음 코드 예제에서는 네이티브 C++ 코드에서 매크로를 사용하는 방법을 보여 줍니다.  
  
```  
// Define the LOCALDB_DEFINE_PROXY_FUNCTIONS constant to enable the LocalDB proxy functions   
// The #define has to take place BEFORE the API header file (sqlncli.h) is included  
#define LOCALDB_DEFINE_PROXY_FUNCTIONS  
#include <sqlncli.h>  
…  
HRESULT hr = S_OK;  
  
// Create LocalDB instance by calling the create API proxy function included by macro  
if (FAILED(hr = LocalDBCreateInstance( L"12.0", L"name", 0)))  
{  
…  
}  
…  
  
```  
  
  