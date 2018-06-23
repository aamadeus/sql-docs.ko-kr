---
title: 데이터 영역에 대한 데이터 없음 메시지 설정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b194714-46f7-4f0e-9632-7f89d9600762
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: e741f590755ebd032b7d26af8fe59772110578cf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36181519"
---
# <a name="set-a-no-data-message-for-a-data-region-report-builder-and-ssrs"></a>데이터 영역에 대한 데이터 없음 메시지 설정(보고서 작성기 및 SSRS)
  렌더링된 보고서에서 데이터가 없는 데이터 영역의 자리에 텍스트가 표시되도록 지정하려면 테이블, 행렬 또는 목록 데이터 영역에 대해 NoRowsMessage 속성을 설정하거나 차트 데이터 영역에 대해 NoDataMessage를 설정하거나, 지도의 색 눈금에 대해 NoDataText를 설정합니다. 보고서 처리기는 런타임에 보고서의 각 데이터 집합에 대한 쿼리를 실행하며 해당 데이터 집합 쿼리에서 결과 집합이 생성되지 않을 수 있습니다. 빈 데이터 집합에 바인딩된 데이터 영역의 경우 빈 데이터 영역을 표시하는 대신 텍스트를 지정하여 표시할 수 있습니다. 또한 런타임에, 하위 보고서의 데이터 집합에 데이터가 없는 경우 하위 보고서의 NoRowsMessage 속성을 설정할 수 있습니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-norowsmessage-property-for-a-table-matrix-or-list"></a>테이블, 행렬 또는 목록에 대해 NoRowsMessage 속성을 설정하려면  
  
1.  디자인 뷰에서 디자인 화면의 테이블, 행렬 또는 목록 데이터 영역이나 하위 보고서를 클릭하여 선택합니다. 선택한 항목의 속성이 속성 창에 표시됩니다.  
  
2.  속성 창에서에 메시지로 표시할 텍스트를 입력 `NoRowsMessage` 속성 필드입니다.  
  
     또는 드롭다운 목록에서 **식** 을 클릭하여 **식** 대화 상자를 열고 식을 작성합니다.  
  
### <a name="to-set-the-nodatamessage-property-for-a-chart"></a>차트에 대해 NoDataMessage 속성을 설정하려면  
  
1.  디자인 뷰에서 디자인 화면에 있는 차트를 클릭하여 선택합니다. 선택한 항목의 속성이 속성 창에 표시됩니다.  
  
2.  속성 창에서 노드를 확장 `NoDataMessage`합니다.  
  
3.  **캡션**에 메시지로 표시할 텍스트 입력 `NoDataMessage` 속성 필드입니다.  
  
     또는 드롭다운 목록에서 **식** 을 클릭하여 **식** 대화 상자를 열고 식을 작성합니다.  
  
### <a name="to-set-the-norowsmessage-for-a-subreport"></a>하위 보고서에 대해 NoRowsMessage를 설정하려면  
  
1.  디자인 뷰에서 디자인 화면에 있는 하위 보고서를 클릭하여 선택합니다. 선택한 항목의 속성이 속성 창에 표시됩니다.  
  
2.  속성 창에서에 메시지로 표시할 텍스트를 입력 `NoRowsMessage` 속성 필드입니다.  
  
     또는 드롭다운 목록에서 **식** 을 클릭하여 **식** 대화 상자를 열고 식을 작성합니다.  
  
### <a name="to-set-the-nodatatext-property-for-a-color-scale-for-a-map"></a>지도의 색 눈금에 NoDataText 속성을 설정하려면  
  
1.  디자인 뷰에서 지도에 있는 색 눈금을 클릭하여 선택합니다. 선택한 항목의 속성이 속성 창에 표시됩니다.  
  
2.  속성 창에서에 `NoDataText`, 데이터 값이 없는 색의 레이블로 표시할 텍스트를 입력 합니다.  
  
     또는 드롭다운 목록에서 **식** 을 클릭하여 **식** 대화 상자를 열고 식을 작성합니다.  
  
## <a name="see-also"></a>관련 항목  
 [하위 보고서 &#40;보고서 작성기 및 SSRS&#41;](../report-design/subreports-report-builder-and-ssrs.md)   
 [테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [차트&#40;보고서 작성기 및 SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md)   
 [지도&#40;보고서 작성기 및 SSRS&#41;](../report-design/maps-report-builder-and-ssrs.md)   
 [하위 보고서 &#40;보고서 작성기 및 SSRS&#41;](../report-design/subreports-report-builder-and-ssrs.md)  
  
  