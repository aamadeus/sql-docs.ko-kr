---
title: 생성, 변경 및 사용자 정의 함수를 제거 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- user-defined functions [SMO]
ms.assetid: 0ebebd3b-0775-41c2-989d-aa4cf81af12a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ced5a796739ea508440fea9ddbb645443fdda786
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054503"
---
# <a name="creating-altering-and-removing-user-defined-functions"></a>사용자 정의 함수 생성, 변경 및 제거
  합니다 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> 에서 사용자 정의 함수를 프로그래밍 방식으로 관리할 수 있는 기능을 제공 하는 개체 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]합니다. 사용자 정의 함수는 입력 및 출력 매개 변수를 지원하며 테이블 열에 대한 직접 참조도 지원합니다.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 저장된 프로시저 내에서 사용할 수 있으려면 먼저 데이터베이스 내에서 등록할 어셈블리, 사용자 정의 함수, 트리거 및 사용자 정의 데이터 형식에 필요 합니다. SMO는 <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> 개체에서 이 기능을 지원합니다.  
  
 합니다 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> 사용 하 여.NET 어셈블리를 참조 하는 개체를 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A>, 및 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A> 속성입니다.  
  
 경우는 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> .NET 어셈블리를 참조 하는 개체를 만들어 어셈블리를 등록 해야 합니다는 <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> 개체에 추가 하는 <xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection> 에 속한 개체를 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체.  
  
## <a name="example"></a>예제  
 제공된 코드 예제를 사용하려면 응용 프로그램을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다. 자세한 내용은 [Visual Studio.NET에서 Visual Basic SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 또는 [Visual C 만들기&#35; Visual Studio.NET에서 SMO 프로젝트](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)합니다.  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-basic"></a>Visual Basic에서 스칼라 사용자 정의 함수 만들기  
 이 코드 예제에서는 만들고에 입력 하는 스칼라 사용자 정의 함수를 제거 하는 방법을 보여 줍니다 <xref:System.DateTime> 개체 매개 변수와 정수 반환 형식에서 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]합니다. 사용자 정의 함수가 생성 된 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 데이터베이스. 이 예에서는 날짜 인수를 사용하여 ISO 주 번호를 계산하는 ISOweek라는 사용자 정의 함수를 만듭니다. 이 함수가 계산을 제대로 수행하기 위해서는 함수를 호출하기 전에 데이터베이스 DATEFIRST 옵션을 1로 설정해야 합니다.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBUserDefFuncs1](SMO How to#SMO_VBUserDefFuncs1)]  -->  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-c"></a>Visual C#에서 스칼라 사용자 정의 함수 만들기  
 이 코드 예제에서는 만들고에 입력 하는 스칼라 사용자 정의 함수를 제거 하는 방법을 보여 줍니다 <xref:System.DateTime> 개체 매개 변수와 정수 반환 형식에서 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]합니다. 사용자 정의 함수가 생성 된 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 데이터베이스. 이 예에서는 사용자 정의 함수를 만듭니다. `ISOweek` 을 참조하세요. 이 함수는 날짜 인수를 사용하여 ISO 주 번호를 계산합니다. 이 함수가 계산을 제대로 수행하기 위해서는 함수를 호출하기 전에 데이터베이스 `DATEFIRST` 옵션을 `1` 로 설정해야 합니다.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
           Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
           Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a UserDefinedFunction object variable by supplying the parent database and the name arguments in the constructor.   
            UserDefinedFunction udf = new UserDefinedFunction(db, "IsOWeek");  
  
            //Set the TextMode property to false and then set the other properties.   
            udf.TextMode = false;  
            udf.DataType = DataType.Int;  
            udf.ExecutionContext = ExecutionContext.Caller;  
            udf.FunctionType = UserDefinedFunctionType.Scalar;  
            udf.ImplementationType = ImplementationType.TransactSql;  
  
            //Add a parameter.   
  
     UserDefinedFunctionParameter par = new UserDefinedFunctionParameter(udf, "@DATE", DataType.DateTime);  
            udf.Parameters.Add(par);  
  
            //Set the TextBody property to define the user-defined function.   
            udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;";  
  
            //Create the user-defined function on the instance of SQL Server.   
            udf.Create();  
  
            //Remove the user-defined function.   
            udf.Drop();  
        }  
```  
  
## <a name="creating-a-scalar-user-defined-function-in-powershell"></a>PowerShell에서 스칼라 사용자 정의 함수 만들기  
 이 코드 예제에서는 만들고에 입력 하는 스칼라 사용자 정의 함수를 제거 하는 방법을 보여 줍니다 <xref:System.DateTime> 개체 매개 변수와 정수 반환 형식에서 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]합니다. 사용자 정의 함수가 생성 된 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 데이터베이스. 이 예에서는 사용자 정의 함수를 만듭니다. `ISOweek` 을 참조하세요. 이 함수는 날짜 인수를 사용하여 ISO 주 번호를 계산합니다. 이 함수가 계산을 제대로 수행하기 위해서는 함수를 호출하기 전에 데이터베이스 `DATEFIRST` 옵션을 `1` 로 설정해야 합니다.  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a user defined function object variable by supplying the parent database and name arguments in the constructor.   
$udf  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunction `  
-argumentlist $db, "IsOWeek"  
  
# Set the TextMode property to false and then set the other properties.   
$udf.TextMode = $false  
$udf.DataType = [Microsoft.SqlServer.Management.SMO.DataType]::Int   
$udf.ExecutionContext = [Microsoft.SqlServer.Management.SMO.ExecutionContext]::Caller  
$udf.FunctionType = [Microsoft.SqlServer.Management.SMO.UserDefinedFunctionType]::Scalar  
$udf.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Define a Parameter object variable by supplying the parent function, name and type arguments in the constructor.  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$par  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunctionParameter `  
-argumentlist $udf, "@DATE",$type  
  
# Add the parameter to the function  
$udf.Parameters.Add($par)  
  
#Set the TextBody property to define the user-defined function.   
$udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;"  
  
# Create the user-defined function on the instance of SQL Server.   
$udf.Create()  
  
# Remove the user-defined function.   
$udf.Drop()  
```  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>  
  
  
