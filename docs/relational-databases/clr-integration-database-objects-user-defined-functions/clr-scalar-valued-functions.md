---
title: "CLR 스칼라 반환 함수 | Microsoft Docs"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- SVF
- scalar-valued functions
ms.assetid: 20dcf802-c27d-4722-9cd3-206b1e77bee0
caps.latest.revision: "81"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 096b540d63e439677568ab68037d23c1307b40bc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="clr-scalar-valued-functions"></a>CLR 스칼라 반환 함수
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]SVF ()는 스칼라 반환 함수에 문자열, 정수 또는 비트 값 등 단일 값을 반환합니다. 모든.NET Framework 프로그래밍 언어를 사용 하 여 관리 코드로 스칼라 반환 사용자 정의 함수를 만들 수 있습니다. 이러한 함수는 [!INCLUDE[tsql](../../includes/tsql-md.md)]이나 다른 관리 코드에서 액세스할 수 있습니다. 관리 코드 중에서 선택 하 고 CLR 통합의 장점에 대 한 내용은 및 [!INCLUDE[tsql](../../includes/tsql-md.md)], 참조 [CLR 통합 개요](../../relational-databases/clr-integration/clr-integration-overview.md)합니다.  
  
## <a name="requirements-for-clr-scalar-valued-functions"></a>CLR 스칼라 반환 함수에 대한 요구 사항  
 .NET Framework SVF는 .NET Framework 어셈블리 클래스의 메서드로 구현됩니다. 입력된 매개 변수 및는 SVF에서 반환 되는 형식에서 지원 되는 스칼라 데이터 형식 중 하나일 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 제외 하 고 **varchar**, **char**, **rowversion**, **텍스트**, **ntext**, **이미지**, **타임 스탬프**, **테이블**, 또는 **커서** . SVF는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식과 구현 메서드의 반환 데이터 형식이 일치하는지 확인해야 합니다. 형식 변환에 대 한 자세한 내용은 참조 [CLR 매개 변수 데이터 매핑](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)합니다.  
  
 .NET Framework 언어로 .NET Framework SVF를 구현하는 경우 **SqlFunction** 사용자 지정 특성을 지정하여 함수에 대한 추가 정보를 포함할 수 있습니다. **SqlFunction** 특성은 함수가 데이터를 액세스 또는 수정하는지, 결정적인지 여부 및 함수에 부동 소수점 연산이 포함되는지 여부를 나타냅니다.  
  
 스칼라 반환 사용자 정의 함수는 결정적이거나 비결정적일 수 있습니다. 결정적 함수는 특정 입력 매개 변수 집합으로 호출될 때 항상 같은 결과를 반환합니다. 비결정적 함수는 특정 입력 매개 변수 집합으로 호출될 때 다른 결과를 반환할 수 있습니다.  
  
> [!NOTE]  
>  함수가 동일한 입력 값과 동일한 데이터베이스 상태가 지정된 상태에서 항상 동일한 값을 출력하지 않을 경우에는 함수를 결정적인 함수로 표시하지 마십시오. 실제로는 결정적인 함수가 아닌 함수를 결정적인 함수로 표시하면 인덱싱된 뷰 및 계산 열이 손상될 수 있습니다. **IsDeterministic** 속성을 true로 설정하여 함수를 결정적인 함수로 표시합니다.  
  
### <a name="table-valued-parameters"></a>테이블 반환 매개 변수  
 프로시저 또는 함수로 전달되는 사용자 정의 테이블 형식인 TVP(테이블 반환 매개 변수)를 사용하면 여러 개의 데이터 행을 서버로 편리하게 전달할 수 있습니다. TVP는 매개 변수 배열과 유사한 기능을 제공하지만 더 유연하며 [!INCLUDE[tsql](../../includes/tsql-md.md)]과 더 밀접하게 통합됩니다. 또한 성능도 향상될 수 있습니다. TVP는 또한 서버와의 왕복 횟수를 줄이는 데 도움이 될 수 있습니다. 스칼라 매개 변수 목록과 같이 서버로 여러 개의 요청을 보내는 대신 서버에 데이터를 TVP로 보낼 수 있습니다. 사용자 정의 테이블 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스에서 실행 중인 관리되는 저장 프로시저 또는 함수에 테이블 반환 매개 변수로 전달되거나 이러한 저장 프로시저 또는 함수에서 테이블 반환 매개 변수로 반환될 수 없습니다. Tvp에 대 한 자세한 내용은 참조 [테이블 반환 매개 변수 &#40; 데이터베이스 엔진 &#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)합니다.  
  
## <a name="example-of-a-clr-scalar-valued-function"></a>CLR 스칼라 반환 함수 예  
 다음은 데이터를 액세스하고 정수 값을 반환하는 단순한 SVF입니다.  
  
```csharp  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public class T  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static int ReturnOrderCount()  
    {  
        using (SqlConnection conn   
            = new SqlConnection("context connection=true"))  
        {  
            conn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
            return (int)cmd.ExecuteScalar();  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public Class T  
    <SqlFunction(DataAccess:=DataAccessKind.Read)> _  
    Public Shared Function ReturnOrderCount() As Integer  
        Using conn As New SqlConnection("context connection=true")  
            conn.Open()  
            Dim cmd As New SqlCommand("SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
            Return CType(cmd.ExecuteScalar(), Integer)  
        End Using  
    End Function  
End Class  
```  
  
 코드의 첫 번째 줄에서는 **Microsoft.SqlServer.Server** 를 참조하여 특성에 액세스하고 **System.Data.SqlClient** 를 참조하여 ADO.NET 네임스페이스에 액세스합니다. (이 네임 스페이스 포함 **SqlClient**,.NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)  
  
 그런 다음 이 함수는 **SqlFunction** 네임스페이스에 있는 **Microsoft.SqlServer.Server** 사용자 지정 특성을 받습니다. 사용자 지정 특성은 UDF(사용자 정의 함수)에서 in-process 공급자를 사용하여 서버의 데이터를 읽는지 여부를 나타냅니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 UDF로 데이터를 업데이트, 삽입 또는 삭제할 수는 없습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 in-process 공급자를 사용하지 않는 UDF의 실행을 최적화할 수 있습니다. 이렇게 하려면 **DataAccessKind** 를 **DataAccessKind.None**으로 설정합니다. 다음 줄에서 대상 메서드는 public static(Visual Basic .NET의 경우 공유) 메서드입니다.  
  
 **SqlContext** 에 있는 클래스는 **Microsoft.SqlServer.Server** 네임 스페이스에 액세스할 수는 **SqlCommand** 와 연결 된 개체는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이미 설정 하는 인스턴스. 여기서는 사용되지 않지만 **System.Transactions** API(응용 프로그래밍 인터페이스)를 통해 현재 트랜잭션 컨텍스트를 사용할 수도 있습니다.  
  
 함수 본문에 있는 대부분의 줄은 **System.Data.SqlClient** 네임스페이스에 있는 형식을 사용하는 클라이언트 응용 프로그램을 작성해 본 개발자에게 익숙한 코드여야 합니다.  
  
 [C#]  
  
```  
using(SqlConnection conn = new SqlConnection("context connection=true"))   
{  
   conn.Open();  
   SqlCommand cmd = new SqlCommand(  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
   return (int) cmd.ExecuteScalar();  
}    
```  
  
 [Visual Basic]  
  
```  
Using conn As New SqlConnection("context connection=true")  
   conn.Open()  
   Dim cmd As New SqlCommand( _  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
   Return CType(cmd.ExecuteScalar(), Integer)  
End Using  
```  
  
 **SqlCommand** 개체를 초기화하여 적절한 명령 텍스트가 지정됩니다. 앞의 예에서는 **SalesOrderHeader**테이블의 행 수를 계산합니다. 그런 다음 **ExecuteScalar** 개체의 **cmd** 메서드가 호출됩니다. 이렇게 하면 쿼리를 기반으로 **int** 형식의 값이 반환됩니다. 마지막으로 주문 횟수가 호출자에게 반환됩니다.  
  
 이 코드를 FirstUdf.cs라는 파일에 저장하면 다음과 같이 어셈블리로 컴파일할 수 있습니다.  
  
 [C#]  
  
```  
csc.exe /t:library /out:FirstUdf.dll FirstUdf.cs   
```  
  
 [Visual Basic]  
  
```  
vbc.exe /t:library /out:FirstUdf.dll FirstUdf.vb  
```  
  
> [!NOTE]  
>  `/t:library`는 실행 파일 대신 라이브러리를 생성해야 함을 나타냅니다. 실행 파일은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 등록할 수 없습니다.  
  
> [!NOTE]  
>  로 컴파일된 visual c + + 데이터베이스 개체 **/clr: pure** 에 실행에 지원 되지 않는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다. 예를 들어 이러한 데이터베이스 개체에는 스칼라 반환 함수가 포함되어 있습니다.  
  
 어셈블리 및 UDF를 등록하는 예제 호출과 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리는 다음과 같습니다.  
  
```  
CREATE ASSEMBLY FirstUdf FROM 'FirstUdf.dll';  
GO  
  
CREATE FUNCTION CountSalesOrderHeader() RETURNS INT   
AS EXTERNAL NAME FirstUdf.T.ReturnOrderCount;   
GO  
  
SELECT dbo.CountSalesOrderHeader();  
GO  
  
```  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]에 표시된 함수 이름이 대상 public static 메서드의 이름과 일치할 필요는 없습니다.  
  
## <a name="see-also"></a>관련 항목:  
 [CLR 매개 변수 데이터 매핑](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)   
 [CLR 통합 사용자 지정 특성의 개요](http://msdn.microsoft.com/library/ecf5c097-0972-48e2-a9c0-b695b7dd2820)   
 [사용자 정의 함수](../../relational-databases/user-defined-functions/user-defined-functions.md)   
 [CLR 데이터베이스 개체에서 데이터 액세스](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  