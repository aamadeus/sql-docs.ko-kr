---
title: 데이터베이스 메일을 사용 하 여 | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- e-mail [SMO]
- Database Mail [SMO]
- mail [SMO]
ms.assetid: 7605390f-b485-48cc-8d97-e364a066067b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a0fdeb7bb85fb00656390dcc537ccebd3b9142bc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784911"
---
# <a name="using-database-mail"></a>데이터베이스 메일 사용
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  SMO에서 데이터베이스 메일 하위 시스템은 <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 속성에서 참조되는 <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> 개체로 표시됩니다. SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 개체를 사용하여 데이터베이스 메일 하위 시스템을 구성하고 프로필 및 메일 계정을 관리할 수 있습니다. SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 개체가 속한 합니다 **Server** 개체는 메일 계정의 범위가 서버 수준에서 임을 의미 합니다.  
  
## <a name="examples"></a>예  
 제공된 코드 예제를 사용하려면 응용 프로그램을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다. 자세한 내용은 [Visual C 만들기&#35; Visual Studio.NET에서 SMO 프로젝트](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)합니다.  
  
 사용 하는 프로그램에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 포함 해야 하는 데이터베이스 메일을 **Imports** 메일 네임 스페이스를 정규화 하는 문입니다. 다음과 같이 응용 프로그램의 선언 앞에, 다른 **Imports** 문 끝에 구문을 삽입하십시오.  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Mail`  
  
## <a name="creating-a-database-mail-account-by-using-visual-basic"></a>Visual Basic을 사용하여 데이터베이스 메일 계정 만들기  
 이 코드 예제는 SMO에서 전자 메일 계정을 만드는 방법을 보여 줍니다. 데이터베이스 메일은 <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 개체로 표시되며 <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Server> 속성에서 참조됩니다. SMO에서는 데이터베이스 메일을 프로그래밍 방식으로 구성할 수 있지만 수신된 전자 메일을 보내거나 처리할 수는 없습니다.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server()
'Define the Database Mail service with a SqlMail object variable and reference it using the Server Mail property.
Dim sm As SqlMail
sm = srv.Mail
'Define and create a mail account by supplying the Database Mail service, name, description, display name, and email address arguments in the constructor.
Dim a As MailAccount
a = New MailAccount(sm, "AdventureWorks Administrator", "AdventureWorks Automated Mailer", "Mail account for administrative e-mail.", "dba@Adventure-Works.com")
a.Create()
```
  
## <a name="creating-a-database-mail-account-by-using-visual-c"></a>Visual C#을 사용하여 데이터베이스 메일 계정 만들기  
 이 코드 예제는 SMO에서 전자 메일 계정을 만드는 방법을 보여 줍니다. 데이터베이스 메일은 <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 개체로 표시되며 <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Server> 속성에서 참조됩니다. SMO에서는 데이터베이스 메일을 프로그래밍 방식으로 구성할 수 있지만 수신된 전자 메일을 보내거나 처리할 수는 없습니다.  
  
```csharp  
{  
         //Connect to the local, default instance of SQL Server.  
         Server srv = default(Server);   
           srv = new Server();   
           //Define the Database Mail service with a SqlMail object variable   
           //and reference it using the Server Mail property.   
           SqlMail sm;   
           sm = srv.Mail;   
           //Define and create a mail account by supplying the Database Mail  
           //service, name, description, display name, and email address  
           //arguments in the constructor.   
           MailAccount a = default(MailAccount);   
           a = new MailAccount(sm, "AdventureWorks2012 Administrator", "AdventureWorks2012 Automated Mailer", "Mail account for administrative e-mail.", "dba@Adventure-Works.com");   
           a.Create();    
}  
```  
  
## <a name="creating-a-database-mail-account-by-using-powershell"></a>PowerShell을 사용하여 데이터베이스 메일 계정 만들기  
 이 코드 예제는 SMO에서 전자 메일 계정을 만드는 방법을 보여 줍니다. 데이터베이스 메일은 <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 개체로 표시되며 <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Server> 속성에서 참조됩니다. SMO에서는 데이터베이스 메일을 프로그래밍 방식으로 구성할 수 있지만 수신된 전자 메일을 보내거나 처리할 수는 없습니다.  
  
  
  
```powershell  
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define the Database Mail; reference it using the Server Mail property.  
$sm = $srv.Mail  
  
#Define and create a mail account by supplying the Database Mail service,  
#name, description, display name, and email address arguments in the constructor.  
$a = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Mail.MailAccount -argumentlist $sm, `  
"Adventure Works Administrator", "Adventure Works Automated Mailer",`  
 "Mail account for administrative e-mail.", "dba@Adventure-Works.com"  
$a.Create()  
```  
  
  
