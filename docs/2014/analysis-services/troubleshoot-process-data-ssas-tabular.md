---
title: 데이터 처리 (SSAS 테이블 형식) 문제 해결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 678f523c-e181-4456-9a54-7b7bf044b8d2
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8ddebb4bb6a2e1c3e3d4bc53052ff207d7bb1d40
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36172734"
---
# <a name="troubleshoot-process-data-ssas-tabular"></a>데이터 처리 문제 해결(SSAS 테이블 형식)
  이 항목에서는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]를 사용하여 모델을 제작할 때의 모델 데이터 처리(새로 고침)에 대한 정보를 제공합니다. 이 항목에서는 Analysis Services 서버 인스턴스에 배포된 모델에서 데이터 처리에 대한 정보를 제공하지 않습니다. 배포된 모델에서 데이터를 처리하는 방법에 대한 자세한 내용은 [Analysis Services의 스크립트 관리 태스크](script-administrative-tasks-in-analysis-services.md)를 참조하세요.  
  
 이 항목의 섹션:  
  
-   [데이터 처리 방법](#bkmk_how_df_works)  
  
-   [데이터 처리의 영향](#bkmk_impact_of_df)  
  
-   [데이터 원본 결정](#bkmk_det_source)  
  
-   [데이터를 마지막으로 새로 고친 시간 확인](#bkmk_det_last_ref)  
  
-   [새로 고칠 수 있는 데이터 원본에 대한 제한 사항](#bkmk_restrictions)  
  
-   [데이터 원본 변경에 대한 제한 사항](#bkmk_rest_changes)  
  
##  <a name="bkmk_how_df_works"></a> 데이터 처리 방법  
 데이터를 처리하면 모델 디자이너의 데이터가 새 데이터로 바뀝니다. 새로운 데이터 행 또는 변경된 데이터만 가져올 수는 없습니다. 모델 디자이너에서는 이전에 추가된 행을 추적하지 않습니다.  
  
 데이터 처리는 트랜잭션의 형태로 수행됩니다. 즉, 데이터 업데이트를 시작하면 전체 업데이트가 실패하거나 성공할 수만 있지 부분적으로 올바른 데이터는 있을 수 없습니다.  
  
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 시작하는 수동 데이터 처리는 Analysis Services의 로컬 메모리 내 인스턴스에서 처리됩니다. 따라서 데이터 처리 작업은 컴퓨터의 다른 태스크 성능에 영향을 줄 수 있습니다. 그러나 스크립트를 사용하여 배포된 모델에서 데이터 자동 처리를 예약하면 Analysis Services의 인스턴스에서 가져오기 프로세스 및 타이밍을 관리합니다.  
  
##  <a name="bkmk_impact_of_df"></a> 데이터 처리의 영향  
 데이터 프로세스는 일반적으로 데이터 재계산을 트리거합니다.  데이터 처리는 외부 원본에서 최신 데이터를 가져오는 것을 의미하고 다시 계산은 변경된 데이터를 사용하는 모든 수식의 결과를 업데이트하는 것을 의미합니다. 처리 작업은 일반적으로 다시 계산을 트리거합니다.  
  
 따라서 데이터 원본을 변경하거나 해당 데이터 원본에서 가져온 데이터를 처리하기 전에 항상 잠재적인 영향에 주의해야 하며 다음과 같은 잠재적인 결과를 고려해야 합니다.  
  
-   데이터 원본의 변경으로 인해 모델 데이터의 일부가 손상될 수도 있습니다. 데이터 원본에서 일부 열을 검색할 수 없는 경우(예: 해당 열이 삭제되거나 변경된 경우) 처리가 실패하며 원본 데이터와 모델 데이터 간의 매핑을 업데이트해야 합니다. 자세한 내용은 참조 [기존 데이터 원본 연결 편집 &#40;SSAS 테이블 형식&#41;](edit-an-existing-data-source-connection-ssas-tabular.md)합니다.  
  
-   처리 후 일부 열이 오류를 포함하는 것으로 플래그가 지정될 수도 있습니다. 이러한 문제는 열에 있는 DAX 수식에서 사용하는 데이터가 처리로 인해 사용할 수 없게 되거나 데이터 형식이 변경되거나 잘못된 값이 외부 데이터에 추가되었기 때문에 발생합니다. 이 문제를 해결하려면 수식을 편집하거나 더 이상 사용할 수 없는 데이터에 기반하는 열을 삭제합니다.  
  
-   업데이트된 데이터를 사용하는 수식은 다시 계산해야 합니다. 모델의 크기에 따라 다소 시간이 걸릴 수 있습니다.  
  
-   모델의 데이터 원본이 여러 개일 경우에는 하나의 외부 데이터 원본만 변경한 경우에도 전체 모델을 처리(모두 처리)해야 할 수 있습니다. 예를 들어 계산 열을 사용하는 측정값을 만드는 경우 이러한 계산 열에 다른 계산 열의 값이 사용되면 모델 디자이너는 먼저 종속성을 분석한 다음 관련 개체의 전체 체인을 순서대로 처리합니다. 종속성의 복잡도에 따라 처리에 오랜 시간이 걸릴 수 있습니다.  
  
-   필터를 변경한 경우 전체 모델을 다시 계산해야 합니다.  
  
##  <a name="bkmk_det_source"></a> 데이터 원본 결정  
 모델의 데이터를 가져올 위치를 잘 모르는 경우 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 의 도구를 사용하여 원본 파일 이름 및 경로를 포함하는 세부 정보를 얻을 수 있습니다.  
  
#### <a name="to-find-the-source-of-existing-data"></a>기존 데이터의 원본을 찾으려면  
  
1.  모델 디자이너에서 원본을 확인할 데이터가 포함된 테이블을 선택합니다.  
  
2.  **테이블** 메뉴를 클릭한 다음 **테이블 속성**을 클릭합니다.  
  
3.  **테이블 속성 편집** 대화 상자에서 **연결 이름**에 나열된 값을 기록해 둡니다.  
  
4.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]의 **모델** 메뉴에서 **기존 연결**을 클릭합니다.  
  
5.  **기존 연결** 대화 상자에서 3단계에서 확인한 이름의 데이터 원본을 선택한 다음 **편집**을 클릭합니다.  
  
6.  **연결 편집** 대화 상자에서 데이터베이스 이름, 파일 경로 또는 보고서 경로와 같은 연결 정보를 봅니다.  
  
##  <a name="bkmk_det_last_ref"></a> 데이터를 마지막으로 새로 고친 시간 확인  
 테이블 속성을 사용하여 데이터를 마지막으로 새로 고친 시간을 확인할 수 있습니다.  
  
#### <a name="to-find-the-date-and-time-that-a-table-was-last-processed"></a>테이블을 마지막으로 처리한 날짜와 시간을 찾으려면  
  
1.  모델 디자이너에서 새로 고침 날짜를 확인할 데이터가 포함된 테이블을 선택합니다.  
  
2.  **테이블** 메뉴를 클릭한 다음 **테이블 속성**을 클릭합니다.  
  
3.  **테이블 속성 편집** 대화 상자의 **마지막 새로 고침** 에 테이블을 마지막으로 새로 고친 날짜가 표시됩니다.  
  
##  <a name="bkmk_restrictions"></a> 새로 고칠 수 있는 데이터 원본에 대한 제한 사항  
 Analysis Services 인스턴스의 배포된 모델에서 자동으로 처리할 수 있는 데이터 원본에는 몇 가지 제한 사항이 적용됩니다. 다음 조건을 만족하는 데이터 원본만 선택하십시오.  
  
-   데이터 원본을 데이터 처리가 수행될 때와 명시된 위치에서 사용할 수 있어야 합니다. 원래 데이터 원본이 모델을 제작한 사용자의 로컬 디스크 드라이브에 있을 경우 데이터 처리 작업에서 해당 데이터 원본을 제외하거나 네트워크 연결을 통해 액세스할 수 있는 위치에 해당 데이터 원본을 게시할 방법을 찾아야 합니다. 데이터 원본을 네트워크 위치로 이동한 경우에는 모델 디자이너에서 모델을 열고 데이터 검색 단계를 반복해야 합니다. 데이터 원본 연결 속성에 저장되어 있는 연결 정보를 다시 설정하기 위해 이 작업이 필요합니다.  
  
-   데이터 원본 연결에 포함되어 있는 자격 증명을 사용하여 데이터 원본에 액세스해야 합니다. 외부 데이터 원본에 연결할 때 포함된 자격 증명이 데이터 원본 연결에 만들어집니다.  
  
-   지정한 모든 데이터 원본에 대해 데이터 처리가 성공해야 합니다. 그렇지 않으면 처리한 데이터가 무시되고 마지막으로 저장한 버전의 모델이 남게 됩니다. 확신할 수 없는 데이터 원본은 제외합니다.  
  
-   데이터 처리가 모델의 다른 데이터를 무효화하지 않아야 합니다. 데이터의 하위 집합을 처리할 때 최신 데이터가 다른 기간의 정적 데이터와 함께 집계된 후에도 모델이 유효한지 확인하는 것이 중요합니다. 모델 디자이너는 데이터 종속성을 알고 있어야 하며 데이터 처리가 모델 자체에 적합한지 확인해야 합니다.  
  
     외부 데이터 원본은 테이블 가져오기 마법사를 사용하여 원래 데이터를 모델로 가져올 때 지정한 포함된 연결 문자열, URL 또는 UNC 경로를 통해 액세스됩니다. 데이터 원본 연결에 저장되는 원래 연결 정보가 다음 데이터 새로 고침 작업에 다시 사용됩니다. 데이터 처리를 위해 만들어지고 관리되는 별도의 연결 정보는 없으며, 기존 연결 정보만 사용됩니다.  
  
##  <a name="bkmk_rest_changes"></a> 데이터 원본 변경에 대한 제한 사항  
 데이터 원본을 변경하는 데는 몇 가지 제한이 있습니다.  
  
-   열의 데이터 형식은 호환되는 데이터 형식으로만 변경할 수 있습니다. 예를 들어 열의 데이터가 10진수를 포함하는 경우 데이터 형식을 정수로 변경할 수 없습니다. 그러나 숫자 데이터는 텍스트로 변경할 수 있습니다. 데이터 형식에 대한 자세한 내용은 [지원되는 데이터 형식&#40;SSAS 테이블 형식&#41;](tabular-models/data-types-supported-ssas-tabular.md)을 참조하세요.  
  
-   서로 다른 테이블의 열을 다중 선택하고 열의 속성을 변경하는 것은 불가능합니다. 한 번에 하나의 테이블 또는 뷰만 사용할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [데이터를 수동으로 처리 &#40;SSAS 테이블 형식&#41;](manually-process-data-ssas-tabular.md)   
 [기존 데이터 원본 연결 편집 &#40;SSAS 테이블 형식&#41;](edit-an-existing-data-source-connection-ssas-tabular.md)  
  
  