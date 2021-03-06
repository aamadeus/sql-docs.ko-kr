---
title: 렌더링 확장 프로그램 제거 | Microsoft Docs
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bd360d5a4929ab41c7b77e60b59b394f127f6f13
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47723881"
---
# <a name="removing-a-rendering-extension"></a>렌더링 확장 프로그램 제거
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 렌더링 확장 프로그램을 제거하려면 **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<Instance Name>\Reporting Services\ReportServer** 폴더에 있는 rsreportserver.config 파일에서 렌더링 확장 프로그램에 대한 **Extension** 요소를 제거하면 됩니다. 보고서 서버 및 보고서 디자이너에 대한 항목을 만든 경우에는 [RSReportDesigner 구성 파일](../../../reporting-services/report-server/rsreportdesigner-configuration-file.md)에서도 **Extension** 요소를 제거합니다. 구성 정보를 제거한 후에는 구성 요소에서 렌더링 확장 프로그램을 사용할 수 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Reporting Services 구성 파일](../../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [렌더링 확장 프로그램 구현](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [렌더링 확장 프로그램 개요](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [IRenderingExtension 인터페이스 구현](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [확장에 대한 보안 고려 사항](../../../reporting-services/extensions/security-considerations-for-extensions.md)   
 [렌더링 확장 프로그램 배포](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
  
