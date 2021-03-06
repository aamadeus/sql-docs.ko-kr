---
title: SQL Server PowerShell 공급자에 인스턴스 지정 | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 9373de68-fd43-45f2-b9a6-149c96610aeb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 07bcf5a82df9f60f539ea763cf70b0a0a60633c0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825471"
---
# <a name="specify-instances-in-the-sql-server-powershell-provider"></a>SQL Server PowerShell 공급자에 인스턴스 지정
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

SQL Server PowerShell 공급자에 대해 지정되는 경로는 [!INCLUDE[ssDE](../includes/ssde-md.md)] 의 인스턴스와 해당 인스턴스가 실행 중인 컴퓨터를 식별해야 합니다. 컴퓨터와 인스턴스를 지정하는 구문은 SQL Server 식별자 규칙과 Windows PowerShell 경로 규칙을 모두 준수해야 합니다.  
  
> [!NOTE]
> SQL Server PowerShell 모듈은 **SqlServer**와 **SQLPS**의 두 가지가 있습니다. **SQLPS** 모듈은 (이전 버전과의 호환성을 위해) SQL Server 설치에 포함되어 있지만 더 이상 업데이트되지는 않습니다. 최신 PowerShell 모듈은 **SqlServer** 모듈입니다. **SqlServer** 모듈은 **SQLPS**에 업데이트된 버전의 cmdlet이 포함되어 있으며, 최신 SQL 기능을 지원하는 새로운 cmdlet도 포함되어 있습니다.  
> 이전 버전의 **SqlServer** 모듈은 SSMS(SQL Server Management Studio)에 *포함되었습니다*(SSMS 16.x 버전만 해당). SSMS 17.0 이상이 포함된 PowerShell을 사용하려면 PowerShell 갤러리에서 **SqlServer** 모듈을 설치해야 합니다.
> **SqlServer** 모듈을 설치하려면 [SQL Server PowerShell 설치](download-sql-server-ps-module.md)를 참조하세요.
  
  
## <a name="before-you-begin"></a>시작하기 전 주의 사항  
 SQL Server 공급자 경로에서 SQLSERVER:\SQL 다음에 오는 첫 번째 노드는 [!INCLUDE[ssDE](../includes/ssde-md.md)]인스턴스를 실행하는 컴퓨터 이름입니다. 예를 들면 다음과 같습니다.  
  
```  
SQLSERVER:\SQL\MyComputer  
```  
  
 [!INCLUDE[ssDE](../includes/ssde-md.md)]인스턴스와 동일한 컴퓨터에 Windows PowerShell을 실행하는 경우 컴퓨터 이름 대신 localhost 또는 (local)을 사용할 수 있습니다. localhost 또는 (로컬)을 사용하는 스크립트는 다른 컴퓨터 이름을 반영하도록 변경하지 않고도 모든 컴퓨터에서 실행할 수 있습니다.  
  
 [!INCLUDE[ssDE](../includes/ssde-md.md)] 실행 프로그램의 여러 인스턴스를 동일한 컴퓨터에서 실행할 수 있습니다. SQL Server 공급자 경로에서 컴퓨터 이름 다음에 오는 노드는 인스턴스를 식별합니다. 예를 들면 다음과 같습니다.  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance  
```  
  
 각 컴퓨터는 기본 [!INCLUDE[ssDE](../includes/ssde-md.md)]인스턴스를 한 개 가질 수 있습니다. 기본 인스턴스는 설치할 때 이름을 지정하지 마세요. 연결 문자열에 컴퓨터 이름만 지정하면 해당 컴퓨터의 기본 인스턴스로 연결됩니다. 컴퓨터의 다른 모든 인스턴스는 명명된 인스턴스여야 합니다. 인스턴스 이름은 설치 시 지정하고, 연결 문자열에는 컴퓨터 이름과 인스턴스 이름을 모두 지정해야 합니다.  
  
###  <a name="LimitationsRestrictions"></a> 제한 사항  
 PowerShell 스크립트에서 마침표(.)를 사용하여 로컬 컴퓨터를 지정할 수 없습니다. 마침표는 PowerShell에서 명령으로 해석되기 때문에 지원되지 않습니다.  
  
 (local)의 괄호 문자는 일반적으로 Windows PowerShell에서 명령으로 처리됩니다. 따라서 경로에 사용할 수 있도록 괄호 문자를 인코딩 또는 이스케이프하거나, 경로를 큰따옴표로 묶어야 합니다. 자세한 내용은 SQL Server 식별자 인코딩 및 디코딩을 참조하세요.  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자는 항상 인스턴스 이름을 지정하도록 요청합니다. 기본 인스턴스의 인스턴스 이름은 DEFAULT로 지정해야 합니다.  
  
##  <a name="Examples"></a> 예: 컴퓨터 및 인스턴스 이름  
 이 예에서는 localhost 및 DEFAULT를 사용하여 로컬 컴퓨터의 기본 인스턴스를 지정합니다.  
  
```  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT   
```  
  
 (local)의 괄호 문자는 일반적으로 Windows PowerShell에서 명령으로 처리됩니다. 다음 중 하나를 수행해야 합니다.  
  
-   경로 문자열을 따옴표로 묶습니다.  
  
    ```  
    Set-Location "SQLSERVER:\SQL\(local)\DEFAULT"  
    ```  
  
-   역따옴표 문자(`)를 사용하여 괄호를 이스케이프 처리합니다.  
  
    ```  
    Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
    ```  
  
-   16진수 표현을 사용하여 괄호를 인코딩합니다.  
  
    ```  
    Set-Location SQLSERVER:\SQL\%28local%29\DEFAULT  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [PowerShell의 SQL Server 식별자](sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell Provider](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
