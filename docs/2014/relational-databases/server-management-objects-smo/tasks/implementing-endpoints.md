---
title: 끝점 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- endpoints [SMO]
ms.assetid: f8674dbb-9bc0-488f-9def-e9e0ce1ddf86
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 17e154743d221cfd4a2070c56634c6364a910afb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48081642"
---
# <a name="implementing-endpoints"></a>엔드포인트 구현
  엔드포인트는 기본적으로 요청을 수신할 수 있는 서비스입니다. SMO를 사용 하 여 다양 한 유형의 끝점을 지원 합니다 <xref:Microsoft.SqlServer.Management.Smo.Endpoint> 개체입니다. <xref:Microsoft.SqlServer.Management.Smo.Endpoint> 개체 인스턴스를 만들고 해당 속성을 설정하여 특정 프로토콜을 사용하는 특정 유형의 페이로드를 처리하는 엔드포인트 서비스를 만들 수 있습니다.  
  
 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.EndpointType%2A> 의 속성을 <xref:Microsoft.SqlServer.Management.Smo.Endpoint> 개체를 사용 하 여 다음 페이로드 유형 중 하나를 지정할 수 있습니다.  
  
-   데이터베이스 미러링  
  
-   SOAP(SOAP 엔드포인트에 대한 지원은 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 및 이전 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 버전에 있음)  
  
-   Service Broker  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)]  
  
 또한 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> 속성을 사용하여 다음 두 가지 지원 프로토콜을 지정할 수 있습니다.  
  
-   HTTP 프로토콜  
  
-   TCP 프로토콜  
  
 페이로드 유형을 지정한, 실제 페이로드 설정할 수 있습니다 사용 하 여는 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Payload%2A> 개체 속성입니다. <xref:Microsoft.SqlServer.Management.Smo.Payload> 개체 속성은 지정된 유형의 페이로드 개체에 대한 참조를 제공하며 이에 대한 속성을 수정할 수 있습니다.  
  
 <xref:Microsoft.SqlServer.Management.Smo.DatabaseMirroringPayload> 개체의 경우 미러링 역할과 암호화 설정 여부를 지정해야 합니다. <xref:Microsoft.SqlServer.Management.Smo.ServiceBrokerPayload> 개체에 메시지 전달, 허용 되는 연결의 최대 수 및 인증 모드에 대 한 정보가 필요 합니다. <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethod.%23ctor%2A> 개체에서는 클라이언트(저장 프로시저 및 사용자 정의 함수)에 사용할 수 있는 SOAP 페이로드 메서드를 지정하는 <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethodCollection.Add%2A> 개체 속성을 비롯하여 다양한 속성을 설정해야 합니다.  
  
 마찬가지로 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Protocol%2A> 속성으로 지정된 유형의 프로토콜 개체를 참조하는 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> 개체 속성을 사용하여 실제 프로토콜을 설정할 수 있습니다. <xref:Microsoft.SqlServer.Management.Smo.HttpProtocol> 개체에는 제한된 IP 주소 목록과 포트, 웹 사이트 및 인증 정보가 필요합니다. <xref:Microsoft.SqlServer.Management.Smo.TcpProtocol> 개체에도 제한 된 IP 주소 목록과 포트 정보가 필요 합니다.  
  
 엔드포인트가 만들어지고 완전히 정의되었으면 데이터베이스 사용자, 그룹, 역할 및 로그온에 대해 액세스를 부여, 취소 및 거부할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음 코드 예제를 사용하려면 응용 프로그램을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다. 자세한 내용은 [Visual Studio.NET에서 Visual Basic SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 및 [Visual C 만들기&#35; Visual Studio.NET에서 SMO 프로젝트](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)합니다.  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-basic"></a>Visual Basic에서 데이터베이스 미러링 엔드포인트 서비스 만들기  
 코드 예제는 SMO에서 데이터베이스 미러링 엔드포인트를 만드는 방법을 보여 줍니다. 이 작업은 데이터베이스 미러를 만들기 전에 수행해야 합니다. 데이터베이스 미러를 만들려면 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> 및 기타 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체의 속성을 사용하십시오.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBEndpoints1](SMO How to#SMO_VBEndpoints1)]  -->  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-c"></a>Visual C#에서 데이터베이스 미러링 엔드포인트 서비스 만들기  
 코드 예제는 SMO에서 데이터베이스 미러링 엔드포인트를 만드는 방법을 보여 줍니다. 이 작업은 데이터베이스 미러를 만들기 전에 수행해야 합니다. 데이터베이스 미러를 만들려면 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> 및 기타 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체의 속성을 사용하십시오.  
  
```  
{  
            //Set up a database mirroring endpoint on the server before   
        //setting up a database mirror.   
        //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Define an Endpoint object variable for database mirroring.   
            Endpoint ep = default(Endpoint);  
            ep = new Endpoint(srv, "Mirroring_Endpoint");  
            ep.ProtocolType = ProtocolType.Tcp;  
            ep.EndpointType = EndpointType.DatabaseMirroring;  
            //Specify the protocol ports.   
            ep.Protocol.Http.SslPort = 5024;  
            ep.Protocol.Tcp.ListenerPort = 6666;  
            //Specify the role of the payload.   
            ep.Payload.DatabaseMirroring.ServerMirroringRole = ServerMirroringRole.All;  
            //Create the endpoint on the instance of SQL Server.   
            ep.Create();  
            //Start the endpoint.   
            ep.Start();  
            Console.WriteLine(ep.EndpointState);  
        }  
```  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-powershell"></a>PowerShell에서 데이터베이스 미러링 엔드포인트 서비스 만들기  
 코드 예제는 SMO에서 데이터베이스 미러링 엔드포인트를 만드는 방법을 보여 줍니다. 이 작업은 데이터베이스 미러를 만들기 전에 수행해야 합니다. 데이터베이스 미러를 만들려면 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> 및 기타 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체의 속성을 사용하십시오.  
  
```  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Get a new endpoint to congure and add  
$ep = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Endpoint -argumentlist $srv,"Mirroring_Endpoint"  
  
#Set some properties  
$ep.ProtocolType = [Microsoft.SqlServer.Management.SMO.ProtocolType]::Tcp  
$ep.EndpointType = [Microsoft.SqlServer.Management.SMO.EndpointType]::DatabaseMirroring  
$ep.Protocol.Http.SslPort = 5024  
$ep.Protocol.Tcp.ListenerPort = 6666 #inline comment  
$ep.Payload.DatabaseMirroring.ServerMirroringRole = [Microsoft.SqlServer.Management.SMO.ServerMirroringRole]::All  
  
# Create the endpoint on the instance  
$ep.Create()  
  
# Start the endpoint  
$ep.Start()  
  
# Report its state  
$ep.EndpointState;  
```  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 미러링 엔드포인트&amp;#40;SQL Server&amp;#41;](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  
