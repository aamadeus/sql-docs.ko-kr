---
title: 지정 된 데이터 형식 및 내용 유형 (기본 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 72484d27-3ef1-4f16-813c-2f43231fc2da
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b97cec782c7f95de42ee64d7db0ce56ffa916c3e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48176615"
---
# <a name="specifying-the-data-type-and-content-type-basic-data-mining-tutorial"></a>데이터 형식 및 내용 유형 지정(기본 데이터 마이닝 마법사)
  구조를 구축하고 모델을 학습하는 데 사용할 열을 선택했으므로 마법사에서 설정한 기본 데이터와 내용 유형을 변경해야 합니다.  
  
#### <a name="review-and-modify-content-type-and-data-type-for-each-column"></a>각 열에 대한 내용 유형과 데이터 형식 검토 및 수정  
  
1.  에 **지정할 열 내용 및 데이터 형식** 페이지에서 **검색** 기본 데이터 및 각 열에 대 한 콘텐츠 유형을 결정 하는 알고리즘을 실행 합니다.  
  
2.  항목을 검토 합니다 **Content-type** 및 **데이터 형식** 열 하 고 설정을 다음 표에 나열 된 것과 동일한 지 확인 하는 데 필요한 경우 변경 합니다.  
  
     일반적으로 마법사는 숫자를 검색하고 적절한 숫자 데이터 형식을 할당하지만 사용자가 숫자를 텍스트로 처리하려는 경우도 많이 있습니다. 예를 들어 합니다 **GeographyKey** 보는 것이 식별자에는 수학 연산을 수행 하기에 적합 하기 때문에 텍스트로 처리 해야 합니다.  
  
    |Column|내용 유형|데이터 형식|  
    |------------|------------------|---------------|  
    |**주소 줄 1**|**불연속**|**텍스트**|  
    |**주소 줄 2**|**불연속**|**텍스트**|  
    |**Age**|**연속**|**Long**|  
    |**Bike Buyer**|**불연속**|**Long**|  
    |**Commute Distance**|**불연속**|**텍스트**|  
    |**CustomerKey**|**Key**|**Long**|  
    |**DateLastPurchase**|**연속**|**날짜**|  
    |**Email Address**|**불연속**|**텍스트**|  
    |**English Education**|**불연속**|**텍스트**|  
    |**English Occupation**|**불연속**|**텍스트**|  
    |**FirstName**|**불연속**|**텍스트**|  
    |**Gender**|**불연속**|**텍스트**|  
    |**Geography Key**|**불연속**|**텍스트**|  
    |**House Owner Flag**|**불연속**|**텍스트**|  
    |**Last Name**|**불연속**|**텍스트**|  
    |**Marital Status**|**불연속**|**텍스트**|  
    |**Number Cars Owned**|**불연속**|**Long**|  
    |**Number Children At Home**|**불연속**|**Long**|  
    |**Region**|**불연속**|**텍스트**|  
    |**Total Children**|**불연속**|**Long**|  
    |**Yearly Income**|**연속**|**Double**|  
  
3.  **다음**을 클릭합니다.  
  
## <a name="next-task-in-lesson"></a>단원의 다음 태스크  
 [구조에 대 한 테스트 데이터 집합을 지정 &#40;기본 데이터 마이닝 자습서&#41;](../../2014/tutorials/specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>단원의 이전 태스크  
 [타겟된 메일링 마이닝 모델 구조 만들기 &#40;기본 데이터 마이닝 자습서&#41;](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>관련 항목  
 [콘텐츠 형식 &#40;데이터 마이닝&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)   
 [데이터 형식 &#40;데이터 마이닝&#41;](../../2014/analysis-services/data-mining/data-types-data-mining.md)  
  
  
