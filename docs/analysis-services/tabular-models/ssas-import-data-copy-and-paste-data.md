---
title: "데이터 (SSAS 테이블 형식) 복사 및 붙여넣기 | Microsoft Docs"
ms.custom: 
ms.date: 05/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.pastepreviewdb.f1
ms.assetid: 2f8d8b3d-810b-4c31-98f2-341015e13da8
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5bbc30ea67df15827da8b289fe1481beee0b6016
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="import-data---copy-and-paste-data"></a>데이터 가져오기-데이터 복사 및 붙여넣기
  외부 응용 프로그램에서 테이블 형식의 데이터를 복사하여 모델 디자이너의 신규 또는 기존 테이블에 붙여넣을 수 있습니다. Excel 또는 Word에서 복사한 데이터와 같은 클립보드에서 붙여넣는 데이터는 HTML 형식이어야 합니다. 모델 디자이너는 데이터 형식을 자동으로 감지하여 붙여넣은 데이터에 적용합니다. 사용자가 직접 열의 데이터 형식이나 서식을 수정할 수도 있습니다.  
  
 데이터 원본에 연결된 테이블과 달리 붙여넣은 테이블에는 연결 이름 또는 원본 데이터 속성이 없습니다. 붙여넣은 데이터는 Model.bim 파일에 보관됩니다. 프로젝트 또는 Model.bim 파일이 저장되면 붙여넣은 데이터도 저장됩니다.  
  
 모델이 배포될 때 모델의 처리 여부에 관계없이 붙여넣은 데이터도 함께 배포됩니다.  
  
 이 항목의 섹션:  
  
-   [필수 구성 요소](#bkmk_prerequisites)  
  
-   [데이터 붙여넣기](#bkmk_paste_data)  
  
-   [붙여넣기 미리 보기 대화 상자](#bkmk_paste_preview)  
  
##  <a name="bkmk_prerequisites"></a> 필수 구성 요소  
 데이터를 붙여넣을 때 몇 가지 제한 사항이 있습니다.  
  
-   붙여넣은 테이블은 10,000개 이상의 행을 가질 수 없습니다.  
  
-   붙여넣은 테이블은 분할할 수 없습니다.  
  
-   붙여넣은 테이블은 DirectQuery 모드에서 지원되지 않습니다.  
  
-   **추가하여 붙여넣기** 및 **바꿔서 붙여넣기** 옵션은 처음에 클립보드에서 데이터를 붙여넣는 방법으로 만든 테이블로 작업할 때만 사용할 수 있습니다. 가져온 데이터의 테이블에 **추가하여 붙여넣기** 또는 **바꿔서 붙여넣기** 를 사용하여 데이터 원본의 형식이 다른 데이터를 추가할 수 없습니다.  
  
-   **추가하여 붙여넣기** 또는 **바꿔서 붙여넣기**를 사용할 때는 새 데이터의 열 수가 원래 데이터의 열 수와 정확하게 같아야 합니다. 또한 붙여넣거나 추가하는 데이터 열이 대상 테이블의 데이터 열과 같거나 호환되는 데이터 형식인 것이 좋습니다. 경우에 따라서는 다른 데이터 형식을 사용할 수도 있지만 **형식 불일치** 오류가 발생할 수 있습니다.  
  
##  <a name="bkmk_paste_data"></a> 데이터 붙여넣기  
  
#### <a name="to-paste-data-into-the-designer"></a>디자이너에 데이터를 붙여넣으려면  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 **편집** 메뉴를 클릭한 후 다음 중 하나를 클릭합니다.  
  
    -   클립보드의 내용을 새 테이블에 붙여넣으려면 **붙여넣기** 를 클릭합니다.  
  
    -   클립보드의 내용을 선택한 테이블에 추가 행으로 붙여넣으려면 **추가하여 붙여넣기** 를 클릭합니다. 새 행이 테이블의 끝에 추가됩니다.  
  
    -   선택한 테이블을 클립보드의 내용으로 바꾸려면 **바꿔서 붙여넣기** 를 클릭합니다. 모든 기존 열 머리글 이름이 테이블에서 유지되고 관계가 보존됩니다.  
  
##  <a name="bkmk_paste_preview"></a> 붙여넣기 미리 보기 대화 상자  
 **붙여넣기 미리 보기** 대화 상자에서는 디자이너 창에 복사할 데이터를 미리 보고 데이터가 올바르게 복사되는지 확인할 수 있습니다. 이 대화 상자를 열려면 HTML 형식의 테이블 기반 데이터를 클립보드에 복사하고 디자이너에서 **편집** 메뉴를 클릭한 다음 **붙여넣기**, **추가하여 붙여넣기**또는 **바꿔서 붙여넣기**를 클릭합니다. **추가하여 붙여넣기** 및 **바꿔서 붙여넣기** 옵션은 클립보드에서 복사하여 붙여넣는 방법으로 만든 테이블의 데이터를 추가하거나 바꿀 때만 사용할 수 있습니다. **추가하여 붙여넣기** 또는 **바꿔서 붙여넣기** 를 사용하여 가져온 데이터의 테이블에 데이터를 추가할 수는 없습니다.  
  
 이 대화 상자의 옵션은 데이터를 완전히 새 테이블에 붙여넣는지, 데이터를 기존 테이블에 붙여넣고 기존 데이터를 새 데이터로 바꾸는지, 데이터를 기존 테이블에 추가하는지에 따라 달라집니다.  
  
### <a name="paste-to-new-table"></a>새 테이블에 붙여넣기  
 **테이블 이름**  
 디자이너에서 만들 테이블의 이름을 지정합니다.  
  
 **붙여넣을 데이터**  
 대상 테이블에 추가할 클립보드 내용의 예제를 보여 줍니다.  
  
### <a name="paste-append"></a>추가하여 붙여넣기  
 **테이블의 기존 데이터**  
 열, 데이터 형식 등을 확인할 수 있도록 테이블의 기존 데이터 예제를 보여 줍니다.  
  
 **붙여넣을 데이터**  
 클립보드 내용의 예제를 보여 줍니다. 기존 데이터에 이 데이터가 추가됩니다.  
  
### <a name="paste-replace"></a>바꿔서 붙여넣기  
 **테이블의 기존 데이터**  
 열, 데이터 형식 등을 확인할 수 있도록 테이블의 기존 데이터 예제를 보여 줍니다.  
  
 **붙여넣을 데이터**  
 클립보드 내용의 예제를 보여 줍니다. 대상 테이블의 기존 데이터가 삭제되고 새 행이 테이블에 삽입됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [데이터 가져오기&#40;SSAS 테이블 형식&#41;](http://msdn.microsoft.com/library/6617b2a2-9f69-433e-89e0-4c5dc92982cf)   
 [지원되는 데이터 원본&#40;SSAS 테이블 형식&#41;](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)   
 [열 데이터 형식 설정&#40;SSAS 테이블 형식&#41;](../../analysis-services/tabular-models/set-the-data-type-of-a-column-ssas-tabular.md)  
  
  