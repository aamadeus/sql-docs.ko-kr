---
title: 생성, 변경 및 데이터베이스 제거 | Microsoft Docs
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
- databases [SMO]
- databases [SMO], creating
- databases [SMO], modifying
- databases [SMO], deleting
ms.assetid: fcfb3ec2-7556-4f72-971a-501295892cb0
caps.latest.revision: 38
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cc53250e518b58e8f30c01da9c38bf68a0fd37a0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36080390"
---
# <a name="creating-altering-and-removing-databases"></a>데이터베이스 생성, 변경 및 제거
  SMO에서 데이터베이스는 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체로 표시됩니다.  
  
 데이터베이스를 수정하거나 참조하기 위해 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체를 만들 필요는 없습니다. 데이터베이스는 컬렉션을 사용하여 참조할 수 있습니다.  
  
## <a name="example"></a>예제  
 제공된 코드 예제를 사용하려면 응용 프로그램을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다. 자세한 내용은 참조 [Visual Studio.NET에서 Visual Basic SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 또는 [Visual C를 만들&#35; Visual Studio.NET에서 SMO 프로젝트](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)합니다.  
  
## <a name="creating-altering-and-removing-a-database-in-visual-basic"></a>Visual Basic에서 데이터베이스 생성, 변경 및 제거  
 이 코드 예제는 새 데이터베이스를 만듭니다. 파일 및 파일 그룹은 데이터베이스를 위해 자동으로 만들어집니다.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDatabase1](SMO How to#SMO_VBDatabase1)]  -->  
  
## <a name="creating-altering-and-removing-a-database-in-visual-c"></a>Visual C#에서 데이터베이스 생성, 변경 및 제거  
 이 코드 예제는 새 데이터베이스를 만듭니다. 파일 및 파일 그룹은 데이터베이스를 위해 자동으로 만들어집니다.  
  
```  
{  
                //Connect to the local, default instance of SQL Server.   
                Server srv;  
                srv = new Server();  
                //Define a Database object variable by supplying the server and the database name arguments in the constructor.   
                Database db;  
                db = new Database(srv, "Test_SMO_Database");  
                //Create the database on the instance of SQL Server.   
                db.Create();  
                //Reference the database and display the date when it was created.   
                db = srv.Databases["Test_SMO_Database"];  
                Console.WriteLine(db.CreateDate);  
                //Remove the database.   
                db.Drop();  
            }  
```  
  
## <a name="creating-altering-and-removing-a-database-in-powershell"></a>PowerShell에서 데이터베이스 생성, 변경 및 제거  
 이 코드 예제는 새 데이터베이스를 만듭니다. 파일 및 파일 그룹은 데이터베이스를 위해 자동으로 만들어집니다.  
  
```  
#Get a server object which corresponds to the default instance  
cd \sql\localhost\  
$srv = get-item default  
  
#Create a new database  
$db = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Database -argumentlist $srv, "Test_SMO_Database"  
$db.Create()  
  
#Reference the database and display the date when it was created.   
$db = $srv.Databases["Test_SMO_Database"]  
$db.CreateDate  
  
#Drop the database  
$db.Drop()  
```  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.SqlServer.Management.Smo.Database>  
  
  