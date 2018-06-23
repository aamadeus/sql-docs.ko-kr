---
title: Excel 장치 정보 설정 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
caps.latest.revision: 40
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 518033807ca52001a09a01136225f3a7594af7d2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36183203"
---
# <a name="excel-device-information-settings"></a>Excel 장치 정보 설정
  다음 표는 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 형식으로 렌더링하기 위한 장치 정보 설정을 나열합니다.  
  
|설정|값|  
|-------------|-----------|  
|**OmitDocumentMap**|지원하는 보고서에 대한 문서 구조를 생략할지 여부를 나타냅니다. 기본값은 `false`입니다.|  
|**OmitFormulas**|렌더링된 보고서에서 수식을 생략할지 여부를 나타냅니다. 기본값은 `false`입니다.|  
|`SimplePageHeade`rs|보고서의 페이지 머리글이 Excel 페이지 머리글로 렌더링되는지 여부를 나타냅니다. 값이 `false` 페이지 머리글이 워크시트의 첫 번째 행으로 렌더링 됨을 나타냅니다. 기본값은 `false`입니다.|  
  
## <a name="see-also"></a>관련 항목  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [장치 정보 설정을 렌더링 확장 프로그램에 전달](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [RSReportServer.Config의 렌더링 확장 프로그램 매개 변수를 사용자 지정](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [기술 참조&#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  