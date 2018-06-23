---
title: 보고서 서버 웹 서비스 끝점 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- management endpoints [Reporting Services]
- Web service [Reporting Services], endpoints
- endpoints [Reporting Services]
- execution endpoints [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: f3f5d85f-9359-4508-bc5a-7f78a3cf7421
caps.latest.revision: 25
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b525f90b91d3b1d540513212164b8efc062b6ed3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173275"
---
# <a name="report-server-web-service-endpoints"></a>보고서 서버 웹 서비스 끝점
  보고서 서버 웹 서비스는 보고서 서버 관리 및 보고서의 실행과 탐색을 위한 끝점을 다수 제공합니다.  
  
## <a name="the-management-endpoints"></a>관리 끝점  
 보고서 서버에서 개체 관리를 위해 사용할 수 있는 세 가지 끝점에는 <xref:ReportService2005>, <xref:ReportService2006> 및 <xref:ReportService2010>이 있습니다. <xref:ReportService2005> 끝점은 기본 모드로 구성된 보고서 서버에서 개체를 관리하는 데 사용되며, <xref:ReportService2006> 끝점은 SharePoint 통합 모드로 구성된 보고서 서버에서 개체를 관리하는 데 사용됩니다. <xref:ReportService2010> 끝점은 <xref:ReportService2005> 및 <xref:ReportService2006>의 기능을 병합하며, 기본 모드 또는 SharePoint 통합 모드용으로 구성된 보고서 서버의 개체를 관리할 수 있습니다.  
  
> [!IMPORTANT]  
>  보고서 서버가 SharePoint 통합 모드로 구성된 경우 <xref:ReportService2005> API는 `rsOperationNotSupportedSharePointMode` 오류를 반환합니다. 보고서 서버가 기본 모드로 구성된 경우 <xref:ReportService2006> API는 `rsOperationNotSupportedNativeMode` 오류를 반환합니다. 마찬가지로 <xref:ReportService2010>의 모드별 API를 잘못된 모드에 사용하면 API에서 해당 오류를 반환합니다.  
  
> [!NOTE]  
>  <xref:ReportService2005> 및 <xref:ReportService2006> 끝점은 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]에서 더 이상 사용되지 않습니다. <xref:ReportService2010> 끝점에는 두 끝점의 기능이 모두 포함되어 있으며 추가 관리 기능도 포함되어 있습니다.  
  
 보고서 서버가 기본 모드 또는 SharePoint 통합 모드로 구성된 경우 관리 끝점용 WSDL은 다음 URL 중 하나를 사용하여 액세스할 수 있습니다.  
  
```  
http://<Server Name>/ReportServer/ReportService2010.asmx?wsdl  
```  
  
 자세한 내용은 [SOAP API 액세스](../accessing-the-soap-api.md)를 참조하세요.  
  
## <a name="the-execution-endpoint"></a>실행 끝점  
 <xref:ReportExecution2005> 끝점을 통해 개발자는 기본 모드 및 SharePoint 통합 모드로 보고서 서버에서 보고서 처리 및 렌더링을 쉽게 사용자 지정할 수 있습니다. 이 끝점에는 이전 버전의 보고서 서버 웹 서비스에 있던 클래스 및 메서드가 포함되어 있습니다. 또한 실행 끝점을 통해 제공되는 다수의 새 클래스 및 메서드가 보고서 서버 웹 서비스에 추가되었습니다.  
  
 관리 끝점에 대한 WSDL은 다음 URL을 사용하여 액세스할 수 있습니다.  
  
```  
http://<Server Name>/ReportServer/ReportExecution2005.asmx?wsdl  
```  
  
 보고서 서버가 SharePoint 통합 모드로 구성된 경우 WSDL은 다음 URL을 사용하여 액세스할 수 있습니다.  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportExecution2005.asmx?wsdl  
```  
  
 자세한 내용은 [SOAP API 액세스](../accessing-the-soap-api.md)를 참조하세요.  
  
## <a name="sharepoint-proxy-endpoints"></a>SharePoint 프록시 끝점  
 보고서 서버가 SharePoint 통합 모드로 구성되고 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 추가 기능이 설치된 경우 프록시 끝점 집합이 SharePoint 서버에 설치됩니다. 프록시 끝점은 보고서 서버가 SharePoint 통합 모드로 구성된 경우 보고서 솔루션을 개발하기 위한 기본 API입니다. 프록시 끝점에 대해 개발할 때 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 추가 기능은 SharePoint 서버와 트러스트된 계정 인증 모드 보고서 서버 간의 자격 증명 교환을 관리합니다. 보고서 서버 끝점에 대해 개발할 때는 호출하는 응용 프로그램이 트러스트된 계정 인증 모드에서 자격 증명 교환을 관리해야 합니다. 다음 표는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 추가 기능과 함께 설치되는 끝점을 나열합니다.  
  
|프록시 끝점|Description|  
|--------------------|-----------------|  
|<xref:ReportService2006>|SharePoint 통합 모드로 구성된 보고서 서버를 관리하기 위한 API를 제공합니다. **참고:** 이 끝점에서 사용 되지 않는 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]합니다.|  
|<xref:ReportService2010>|기본 모드 또는 SharePoint 통합 모드로 구성된 보고서 서버를 관리하기 위한 API를 제공합니다.|  
|<xref:ReportExecution2005>|보고서 실행 및 탐색을 위한 API를 제공합니다.|  
|<xref:ReportServiceAuthentication>|폼 인증을 위해 SharePoint 웹 응용 프로그램이 구성된 경우 보고서 서버에 대해 사용자를 인증하기 위한 API를 제공합니다.|  
  
 다음은 SharePoint 사이트에서 프록시 끝점을 참조하기 위한 URL의 예입니다.  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportService2010.asmx  
```  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportExecution2005.asmx  
```  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportServiceAuthentication.asmx  
```  
  
## <a name="see-also"></a>관련 항목  
 [웹 서비스 및 .NET Framework를 사용하여 응용 프로그램 빌드](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  