---
title: "웹 구성 페이지(Master Data Services 구성 마법사) | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.mds.configmanager.webconfigpg.f1"
ms.assetid: 7b900778-0169-4e42-9faf-98dc1c01313e
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# 웹 구성 페이지(Master Data Services 구성 마법사)
  **웹 구성** 페이지를 사용하여 웹 사이트 및 웹 응용 프로그램을 구성합니다. 또한 Data Quality Services도 사용할 수 있습니다.  
  
## 웹 응용 프로그램 구성  
  
|컨트롤 이름|Description|  
|------------------|-----------------|  
|**웹 사이트**|새 웹 사이트를 만들거나, 기본 웹 사이트를 선택하거나, 다른 사용 가능한 사이트(목록에 있는 경우)를 선택합니다. 이 목록에는 로컬 컴퓨터의 인터넷 정보 서비스(IIS)에 정의된 웹 사이트가 표시됩니다. 새 웹 사이트를 만들면 새 웹 응용 프로그램이 자동으로 만들어집니다. 기본 또는 다른 기존 사이트를 선택하면 응용 프로그램을 수동으로 만들어야 합니다.|  
|**웹 응용 프로그램**|구성할 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 응용 프로그램을 선택합니다. 이 상자에는 선택한 웹 사이트의 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 응용 프로그램만 표시됩니다.<br /><br /> 아무 항목도 표시되지 않으면 **만들기**를 클릭하여 웹 사이트를 만듭니다.|  
|**만들기**|**웹 응용 프로그램 만들기** 대화 상자를 열어 선택한 사이트에서 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 응용 프로그램을 만듭니다. 이 단추는 선택한 사이트에 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 응용 프로그램으로 구성된 루트 웹 응용 프로그램이 없는 경우에만 활성화됩니다.|  
  
## 응용 프로그램을 데이터베이스에 연결  
  
|컨트롤 이름|Description|  
|------------------|-----------------|  
|**Select**|**서버에 연결** 대화 상자를 열어 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결하고 선택한 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 웹 응용 프로그램과 연결할 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 데이터베이스를 선택합니다.|  
|**SQL Server 인스턴스**|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스를 호스팅하는 선택한 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 인스턴스의 이름을 표시합니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결하고 데이터베이스를 선택할 때까지 비어 있습니다.|  
|**데이터베이스**|선택한 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 웹 응용 프로그램과 연결된 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 데이터베이스의 이름을 표시합니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결하고 데이터베이스를 선택할 때까지 비어 있습니다.|  
  
## DQS 통합 사용  
  
|컨트롤 이름|Description|  
|------------------|-----------------|  
|**Data Quality Services와의 통합 사용**|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]에서 데이터 품질 기능을 사용하도록 설정하려면 이 옵션을 선택합니다. 자세한 내용은 [Enable Data Quality Services Integration with Master Data Services](../master-data-services/install-windows/enable-data-quality-services-integration-with-master-data-services.md)을 참조하세요.|  
  
## 관련 항목:  
 [Master Data Services 시작&#40;SQL Server 2016&#41;](../Topic/Get%20Started%20with%20Master%20Data%20Services%20\(SQL%20Server%202016\).md)   
 [웹 응용 프로그램 요구 사항&#40;Master Data Services&#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md)   
 [마스터 데이터 관리자 웹 응용 프로그램 만들기&#40;Master Data Services&#41;](../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  