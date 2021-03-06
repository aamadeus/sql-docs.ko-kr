---
title: 보고서 뷰어 컨트롤을 사용하여 Reporting Services 통합 | Microsoft Docs
ms.date: 09/18/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
helpviewer_keywords:
- Report Viewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b4b7eb42e3254e92b1b9778ac3866178f68e72f2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47786641"
---
# <a name="integrating-reporting-services-using-report-viewer-controls"></a>보고서 뷰어 컨트롤을 사용하여 Reporting Services 통합
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 2015는 보고서 보기 기능을 응용 프로그램에 통합하기 위한 보고서 뷰어 컨트롤을 두 가지 제공합니다. Windows Forms 기반 응용 프로그램용 버전과 Web Forms 응용 프로그램용 버전이 있습니다. 각 컨트롤은 유사한 기능을 제공하지만 개별 환경에 맞게 디자인되었습니다. 두 컨트롤 모두 보고서 서버에 배포되거나(원격 처리 모드) [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]이(가) 설치되지 않은 컴퓨터에 복사된(로컬 처리 모드) 보고서를 처리할 수 있습니다.  
  
 보고서 뷰어 컨트롤에는 화면 해상도가 다른 여러 장치에 동적으로 채택할 수 있는 기본 제공 지원이 포함되지 않습니다.  
  
## <a name="remote-processing-mode"></a>원격 처리 모드  
 원격 처리 모드는 보고서 서버에 배포된 보고서를 보는 데 권장되는 방법입니다. 원격 처리 모드는 다음과 같은 이점을 제공합니다.  
  
-   보고서가 보고서 서버에서 처리되므로 원격 처리는 보고서 실행을 위한 최적화된 솔루션을 제공합니다.  
  
-   모든 처리가 보고서 서버에서 수행되므로 보고서 요청을 스케일 아웃 배포의 여러 보고서 서버 또는 수직 확장 시나리오의 여러 프로세서가 있는 서버에서 처리할 수 있습니다.  
  
 또한 원격 모드에서 보고서를 실행하면 모든 렌더링 및 데이터 확장 프로그램을 포함하여 보고서 서버의 전체 기능을 활용할 수 있습니다.  
  
> [!NOTE]  
>  원격 처리 모드에서 실행될 때 보고서 뷰어 컨트롤에서 사용 가능한 확장 프로그램 목록은 보고서 서버에 설치된 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 버전에 따라 다릅니다.  
  
## <a name="local-processing-mode"></a>로컬 처리 모드  
 로컬 처리 모드는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]가 설치되지 않은 경우 보고서를 보고 렌더링하기 위한 대체 방법입니다. 원격 처리와 달리 보고서 서버에서 제공하는 기능 중 일부만 컨트롤에서 사용할 수 있습니다. 로컬 처리 모드에서 데이터 처리는 컨트롤에서 수행되지 않고 호스팅 응용 프로그램에서 구현됩니다. 그러나 보고서 처리는 컨트롤 자체에서 처리합니다. 로컬 처리 모드에서는 PDF, Excel, Word 및 이미지 렌더링 확장 프로그램만 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [응용 프로그램에 Reporting Services 통합](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [WebForms 보고서 뷰어 컨트롤 사용](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)   
 [WinForms 보고서 뷰어 컨트롤 사용](../../reporting-services/application-integration/using-the-winforms-reportviewer-control.md)  

  
  
