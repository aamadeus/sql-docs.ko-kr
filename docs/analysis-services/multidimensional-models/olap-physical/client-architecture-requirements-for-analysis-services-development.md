---
title: 분석을 위한 클라이언트 아키텍처 요구 사항 서비스 개발 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ef45e149fc70fdf338a60cd823497eb2efb6a215
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34022390"
---
# <a name="client-architecture-requirements-for-analysis-services-development"></a>Analysis Services 배포의 클라이언트 아키텍처 요구 사항
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 씬 클라이언트 아키텍처를 지원 합니다. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 계산 엔진은 완전히 서버 기반으로 하므로 모든 쿼리가 서버에서 확인 됩니다. 결과적으로 각 쿼리에는 클라이언트와 서버 간의 단일 왕복만이 필요하여 쿼리가 복잡해짐에 따라 성능이 확장될 수 있습니다.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]의 네이티브 프로토콜은 XML/A(XML for Analysis)입니다. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]에서는 클라이언트 응용 프로그램에 여러 데이터 액세스 인터페이스를 제공하지만 이러한 구성 요소는 모두 XML/A를 사용하여 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스와 통신합니다.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]는 다른 프로그래밍 언어 지원을 위해 몇 개의 공급자를 제공하고 있습니다. 공급자는 인터넷 정보 서비스(IIS)를 통한 HTTP나 TCP/IP에서 SOAP 패킷으로 XML for Analysis를 보내고 받으며 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]와 통신합니다. HTTP 연결은 IIS에서 인스턴스화되는 COM 개체를 사용합니다. 이러한 개체를 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터의 통로 역할을 하는 데이터 펌프라고 합니다. 데이터 펌프는 HTTP 스트림에 포함된 기본 데이터를 검사하지 않으며 데이터 라이브러리 자체의 코드에 사용할 수 있는 기본 데이터 구조도 아닙니다.  
  
 ![Analysis Services에 대 한 논리 클라이언트 아키텍처](../../../analysis-services/multidimensional-models/olap-physical/media/as-clientarch9.gif "Analysis Services에 대 한 논리 클라이언트 아키텍처")  
  
 Win32 클라이언트 응용 프로그램은 Microsoft Visual Basic 과 같은 COM(구성 요소 개체 모델) 자동화 언어용 Microsoft ADO(ActiveX Data Objects) 개체 모델 또는 OLAP용 OLE DB 인터페이스를 사용하여 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 서버에 연결할 수 있습니다. .NET 언어로 코딩된 응용 프로그램은 ADOMD.NET을 사용하여 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 서버에 연결할 수 있습니다.  
  
 기존 응용 프로그램은 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 공급자 중 하나를 그대로 사용하여 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]와 통신할 수 있습니다.  
  
|프로그래밍 언어|데이터 액세스 인터페이스|  
|--------------------------|---------------------------|  
|C++|OLAP용 OLE DB|  
|Visual Basic 6|ADO MD|  
|.NET 언어|ADO MD.NET|  
|모든 SOAP 지원 언어|XML for Analysis|  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]에는 소규모 조직과 대규모 조직 모두에서 배포할 수 있는 완전히 확장 가능한 중간 계층을 포함하는 웹 아키텍처가 있습니다. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]는 웹 서비스를 위해 중간 계층을 광범위하게 지원합니다. ASP 응용 프로그램은 OLE DB에서 OLAP 용 지원 되며 ADO MD, ASP.NET 응용 프로그램은 ADOMD.NET에서 지원 됩니다. 다음 그림에서 설명하는 중간 계층은 많은 동시 사용자로 확장 가능합니다.  
  
 ![중간 계층 아키텍처에 대 한 논리 다이어그램](../../../analysis-services/multidimensional-models/olap-physical/media/as-midtierarch9.gif "중간 계층 아키텍처에 대 한 논리 다이어그램")  
  
 클라이언트 응용 프로그램 및 중간 계층 응용 프로그램 모두는 공급자를 사용하지 않고 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]와 직접 통신할 수 있습니다. 클라이언트 응용 프로그램과 중간 계층 응용 프로그램은 TCP/IP, HTTP 또는 HTTPS에서 SOAP 패킷으로 XML for Analysis를 보낼 수 있습니다. SOAP를 지원하는 언어를 사용하여 클라이언트를 작성할 수 있습니다. 이러한 경우 TCP/IP를 사용하여 서버에 직접 연결하도록 코딩할 수 있지만 HTTP를 사용하여 인터넷 정보 서비스(IIS)로 통신을 관리하는 것이 가장 쉽습니다. 이것이 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]에 대한 최상의 씬 클라이언트 솔루션입니다.  
  
## <a name="analysis-services-in-tabular-or-sharepoint-mode"></a>테이블 형식 또는 SharePoint 모드의 Analysis Services  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]을 및 테이블 형식 데이터베이스에 대 한 xVelocity 메모리 내 분석 엔진 (VertiPaq) 모드에서 서버를 시작할 수 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] SharePoint 사이트에 게시 된 통합 문서.  
  
 [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)] 및 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]는 SharePoint 또는 테이블 형식 모드 각각을 사용하는 메모리 내 데이터베이스 만들고 쿼리하기 위해 지원되는 유일한 클라이언트 환경입니다. 포함 된 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Excel을 사용 하 여 만든 데이터베이스 및 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 도구는 Excel 통합 문서 내에서 포함 되며 Excel.xlsx 파일의 일부로 저장 됩니다.  
  
 그러나 큐브 데이터를 통합 문서에 가져올 경우 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 통합 문서는 기존 큐브에 저장된 데이터를 사용할 수 있습니다. SharePoint 사이트에 게시된 경우 다른 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 통합 문서에서 데이터를 가져올 수도 있습니다.  
  
> [!NOTE]  
>  큐브를 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 통합 문서의 데이터 원본으로 사용할 경우 큐브에서 가져오는 데이터는 MDX 쿼리로 정의되지만, 결합된 스냅숏으로 데이터를 가져옵니다. 대화형으로 데이터를 사용하거나 큐브에서 데이터를 새로 고칠 수 없습니다.  
  
 SSAS 큐브를 데이터 원본으로 사용 하는 방법에 대 한 자세한 내용은 참조는 [Excel 용 파워 피벗](http://go.microsoft.com/fwlink/?LinkId=164234)합니다.  
  
### <a name="interfaces-for-power-pivot-client"></a>Power Pivot 클라이언트에 대 한 인터페이스  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Analysis Services에 대 한 설정 된 인터페이스 및 언어를 사용 하 여 통합 문서 내에서 xVelocity 메모리 내 분석 엔진 (VertiPaq) 저장소 엔진와 상호 작용: AMO 및 ADOMD.NET 및 MDX 및 XMLA 합니다. 추가 기능 내에서 측정값은 Excel, DAX(Data Analysis Expressions)와 유사한 수식 언어를 사용하여 정의됩니다. DAX 식은 in-process 서버에 보낸 XMLA 메시지 내에 포함됩니다.  
  
### <a name="providers"></a>공급자  
 간의 통신 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 및 Excel에는 MSOLAP OLEDB 공급자 (버전 11.0) 사용 합니다. MSOLAP 공급자 내에는 클라이언트와 서버 간에 메시지를 보내는 데 사용할 수 있는 네 가지 모듈 또는 전송이 있습니다.  
  
 **TCP/IP** 일반적인 클라이언트-서버 연결에 사용 합니다.  
  
 **HTTP** SSAS 데이터 펌프 서비스 또는 SharePoint 호출 하 여 HTTP 연결에 사용 되는 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] WS (웹 서비스) 구성 요소입니다.  
  
 **INPROC** in-process 엔진에 연결할 때 사용 합니다.  
  
 **채널** 통신에 예약 된 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] SharePoint 팜에서 시스템 서비스입니다.  
  
## <a name="see-also"></a>관련 항목:  
 [OLAP 엔진 서버 구성 요소](../../../analysis-services/multidimensional-models/olap-physical/olap-engine-server-components.md)  
  
  
