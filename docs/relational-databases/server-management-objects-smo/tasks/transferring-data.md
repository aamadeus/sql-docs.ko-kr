---
title: 데이터 전송 | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- data transfers [SMO]
- transferring data
ms.assetid: eea255c3-8251-40f0-973b-fe4ef6cb5261
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 31e75a6c540525237b4760e03ddecf63b435d8c0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47621881"
---
# <a name="transferring-data"></a>데이터 전송
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  <xref:Microsoft.SqlServer.Management.Smo.Transfer> 클래스는 개체와 데이터를 전송하기 위한 도구를 제공하는 유틸리티 클래스입니다.  
  
 데이터베이스 스키마의 개체는 대상 서버에서 생성된 스크립트를 실행하여 전송됩니다. <xref:Microsoft.SqlServer.Management.Smo.Table> 데이터는 동적으로 생성된 DTS 패키지를 사용하여 전송됩니다.  
  
 합니다 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 개체에서 사용 하는 [SQLBulkCopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy.aspx) API 데이터를 전송 합니다. 또한 데이터 전송을 수행하는 메서드와 속성은 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 개체가 아니라 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체에 있습니다. 인스턴스 클래스에서 유틸리티 클래스로 기능을 이동하면 특정 태스크의 코드가 필요할 때만 로드되므로 개체 모델이 보다 단순해집니다.  
  
 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 개체는 <xref:Microsoft.SqlServer.Management.Smo.Database.CompatibilityLevel%2A>이 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 인스턴스 버전보다 낮은 대상 데이터베이스로의 데이터 전송을 지원하지 않습니다.  
  
## <a name="example"></a>예제  
제공된 코드 예제를 사용하려면 응용 프로그램을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다. 자세한 내용은 [Visual C 만들기&#35; Visual Studio.NET에서 SMO 프로젝트](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)합니다.  
 
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-basic"></a>Visual Basic에서 데이터베이스 간 스키마 및 데이터 전송  
 이 코드 예제에서는 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 개체를 사용하여 데이터베이스 간에 스키마와 데이터를 전송하는 방법을 보여 줍니다.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Create a new database that is to be destination database.
Dim dbCopy As Database
dbCopy = New Database(srv, "AdventureWorks2012Copy")
dbCopy.Create()
'Define a Transfer object and set the required options and properties.
Dim xfr As Transfer
xfr = New Transfer(db)
xfr.CopyAllTables = True
xfr.Options.WithDependencies = True
xfr.Options.ContinueScriptingOnError = True
xfr.DestinationDatabase = "AdventureWorks2012Copy"
xfr.DestinationServer = srv.Name
xfr.DestinationLoginSecure = True
xfr.CopySchema = True
'Script the transfer. Alternatively perform immediate data transfer with TransferData method.
xfr.ScriptTransfer()
```
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-c"></a>Visual C#에서 데이터베이스 간 스키마 및 데이터 전송  
 이 코드 예제에서는 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 개체를 사용하여 데이터베이스 간에 스키마와 데이터를 전송하는 방법을 보여 줍니다.  
  
```csharp  
{  
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Create a new database that is to be destination database.   
            Database dbCopy;  
            dbCopy = new Database(srv, "AdventureWorks2012Copy");  
            dbCopy.Create();  
            //Define a Transfer object and set the required options and properties.   
            Transfer xfr;  
            xfr = new Transfer(db);  
            xfr.CopyAllTables = true;  
            xfr.Options.WithDependencies = true;  
            xfr.Options.ContinueScriptingOnError = true;  
            xfr.DestinationDatabase = "AdventureWorks2012Copy";  
            xfr.DestinationServer = srv.Name;  
            xfr.DestinationLoginSecure = true;  
            xfr.CopySchema = true;  
            //Script the transfer. Alternatively perform immediate data transfer   
            // with TransferData method.   
            xfr.ScriptTransfer();  
        }   
```  
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-powershell"></a>PowerShell에서 데이터베이스 간 스키마 및 데이터 전송  
 이 코드 예제에서는 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 개체를 사용하여 데이터베이스 간에 스키마와 데이터를 전송하는 방법을 보여 줍니다.  
  
```powershell  
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Reference the AdventureWorks2012 database.  
$db = $srv.Databases["AdventureWorks2012"]  
  
#Create a database to hold the copy of AdventureWorks  
$dbCopy = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Database -argumentlist $srv, "AdventureWorksCopy"  
$dbCopy.Create()  
  
#Define a Transfer object and set the required options and properties.  
$xfr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Transfer -argumentlist $db  
  
#Set this objects properties  
$xfr.CopyAllTables = $true  
$xfr.Options.WithDependencies = $true  
$xfr.Options.ContinueScriptingOnError = $true  
$xfr.DestinationDatabase = "AdventureWorksCopy"  
$xfr.DestinationServer = $srv.Name  
$xfr.DestinationLoginSecure = $true  
$xfr.CopySchema = $true  
"Scripting Data Transfer"  
#Script the transfer. Alternatively perform immediate data transfer with TransferData method.  
$xfr.ScriptTransfer()  
```  
  
  
