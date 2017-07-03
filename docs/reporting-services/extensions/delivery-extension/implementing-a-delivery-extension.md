---
title: Implementing a Delivery Extension | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- delivery [Reporting Services]
- custom delivery extensions [Reporting Services]
- extensions [Reporting Services], delivery
- delivery extensions [Reporting Services]
ms.assetid: 600cd229-efcd-480e-8c95-3c3c39ff4e7a
caps.latest.revision: 32
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 9909a4711eb5b1ffde9b865411bd552e6b409bc6
ms.contentlocale: ko-kr
ms.lasthandoff: 06/22/2017

---
# <a name="implementing-a-delivery-extension"></a>배달 확장 프로그램 구현
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 사용자를 만들고, 한 번 생성 및 게시를 제공할 수 있는 여러 다른 위치로 보고서를 게시할 수 있습니다. 또한 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에는 다수의 배달 확장 프로그램이 포함되어 있으며 개발자가 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 배달 기능을 더욱 확장할 수 있도록 추가 배달 확장 프로그램을 만들 수 있는 배달 API가 포함되어 있습니다.  
  
 배달 확장 프로그램의 샘플 구현을 참조 [SQL Server Reporting Services 제품 샘플](http://go.microsoft.com/fwlink/?LinkId=177889)합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [배달 확장 프로그램 개요](../../../reporting-services/extensions/delivery-extension/delivery-extensions-overview.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]용 사용자 지정 배달 확장 프로그램을 작성하는 방법을 소개합니다.  
  
 [배달 확장 프로그램 구현 준비](../../../reporting-services/extensions/delivery-extension/preparing-to-implement-a-delivery-extension.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 배달 확장 프로그램을 구현할 때 사용할 수 있는 인터페이스와 클래스 및 구현 전에 고려할 사항을 설명합니다.  
  
 [배달 확장 프로그램 라이브러리 만들기](../../../reporting-services/extensions/delivery-extension/creating-a-delivery-extension-library.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 배달 확장 프로그램에 대한 네임스페이스 할당에 대해 설명하고 배달 확장 프로그램을 라이브러리 DLL로 컴파일하는 방법에 대해 설명합니다.  
  
 [배달 확장 프로그램에 대 한 IDeliveryExtension 인터페이스 구현](../../../reporting-services/extensions/delivery-extension/implementing-the-ideliveryextension-interface-for-a-delivery-extension.md)  
 배달 확장 프로그램의 특성 및 고유의 배달 확장 프로그램 클래스를 구현하는 방법을 설명합니다.  
  
 [배달 확장 프로그램에 대 한 알림 클래스를 사용 하 여](../../../reporting-services/extensions/delivery-extension/using-a-notification-class-for-a-delivery-extension.md)  
 특성에 설명 된 **알림** 클래스 및 배달 확장 프로그램 구현에서 사용 하는 방법입니다.  
  
 [배달 확장 프로그램에 대 한 Setting 클래스 사용](../../../reporting-services/extensions/delivery-extension/using-the-setting-class-for-a-delivery-extension.md)  
 특성을 설명는 **설정** 클래스 및 배달 확장 프로그램 구현에서 사용 하는 방법입니다.  
  
 [IDeliveryReportServerInformation 인터페이스를 사용 하 여 배달 확장 프로그램에 대 한](../../../reporting-services/extensions/delivery-extension/using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)  
 특성에 설명 된 **IDeliveryReportServerInformation** 인터페이스 및 배달 확장 프로그램 구현에서 사용 하는 방법입니다.  
  
 [Report 클래스를 사용 하 여 배달 확장 프로그램에 대 한](../../../reporting-services/extensions/delivery-extension/using-the-report-class-for-a-delivery-extension.md)  
 특성에 설명 된 **보고서** 클래스 및 배달 확장 프로그램 구현에서 사용 하는 방법입니다.  
  
 [RenderedOutputFile 클래스를 사용 하 여 배달 확장 프로그램에 대 한](../../../reporting-services/extensions/delivery-extension/using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
 특성에 설명 된 **RenderedOutputFile** 클래스 및 배달 확장 프로그램 구현에서 사용 하는 방법입니다.  
  
 [배달 확장 프로그램에 대 한 ISubscriptionBaseUIUserControl 인터페이스 구현](../../../reporting-services/extensions/delivery-extension/implementing-the-isubscriptionbaseuiusercontrol-interface.md)  
 배달 확장 프로그램 사용자 컨트롤의 특성 및 고유의 구독용 사용자 인터페이스를 구현하는 방법을 설명합니다.  
  
 [배달 확장 프로그램 배포](../../../reporting-services/extensions/delivery-extension/deploying-a-delivery-extension.md)  
 배달 확장 프로그램을 배포하는 방법을 설명합니다.  
  
 [배달 확장 프로그램 코드 디버깅](../../../reporting-services/extensions/delivery-extension/debugging-delivery-extension-code.md)  
 배달 확장 프로그램에서 코드를 디버깅하는 방법을 설명합니다.  
  
 [배달 확장 프로그램 제거](../../../reporting-services/extensions/delivery-extension/removing-a-delivery-extension.md)  
 보고서 서버에서 배달 확장 프로그램을 제거하는 방법을 설명합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [Reporting Services 확장 프로그램](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Reporting Services 확장 프로그램 라이브러리](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  