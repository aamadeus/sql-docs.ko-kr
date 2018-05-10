---
title: SSDT에서 DirectQuery 모드를 사용 하도록 설정 | Microsoft Docs
ms.custom: ''
ms.date: 02/22/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: aefaf3c32f070036cba01696b249842b7563307b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="enable-directquery-mode-in-ssdt"></a>SSDT에서 DirectQuery 모드를 사용하도록 설정
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
이 항목에서는 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 테이블 형식 모델 프로젝트에 대해 DirectQuery 모드를 사용하도록 설정하는 방법을 설명합니다.  
  
SSDT에서 디자인 중인 테이블 형식 모델에 대해 DirectQuery 모드를 사용하도록 설정할 경우
-   DirectQuery 모드와 호환되지 않는 기능을 사용할 수 없습니다.  
-   기존 모델의 유효성이 검사됩니다. 기능이 DirectQuery 모드와 호환되지 않으면 경고가 표시됩니다.  
-   DirectQuery 모드를 사용하도록 설정하기 전에 데이터를 가져왔으면 작업 모델의 캐시가 비워집니다.  
  
### <a name="enable-directquery"></a>DirectQuery 사용  
  
SSDT의 **Model.bim** 파일에 대한 **속성** 창에서 **DirectQuery 모드**속성을 **켜짐**으로 변경합니다.  

![SSDT에서 DirectQuery 모드를 사용하도록 설정](../../analysis-services/tabular-models/media/enable-directquery-mode-in-ssdt.png)
  
모델에 데이터 원본과 기존 데이터에 대한 연결이 이미 있을 경우 관계형 데이터베이스에 연결하는 데 사용되는 데이터베이스 자격 증명을 입력하라는 메시지가 표시됩니다. 모델 내에 이미 있는 데이터는 메모리 내 캐시에서 제거됩니다.  
  
DirectQuery 모드를 사용하도록 설정하기 전에 모델이 부분적으로 또는 완전히 완료된 경우 호환되지 않는 기능에 대한 오류가 표시될 수 있습니다. 이 경우 Visual Studio에서 **오류 목록** 을 열고 모델을 DirectQuery 모드로 전환할 수 없도록 하는 문제를 해결합니다.  


### <a name="whats-next"></a>다음 단계 
이제 모델에 대한 메타데이터를 가져오기 위해 테이블 가져오기 마법사를 사용하여 데이터를 가져올 수 있습니다. 데이터 행은 가져올 수 없지만 모델의 기준으로 사용할 테이블, 열 및 관계는 가져올 수 있습니다. 

모델을 작성할 때 모델 동작을 확인할 수 있도록 각 테이블에 대한 샘플 파티션을 만들고 샘플 데이터를 추가할 수 있습니다. 추가하는 샘플 데이터는 **Excel에서 분석** 또는 작업 영역 데이터베이스에 연결할 수 있는 기타 클라이언트 도구에서 사용됩니다. 자세한 내용은 [디자인 모드에서 DirectQuery 모델에 샘플 데이터 추가](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md) 를 참조하세요.  
  
> [!TIP]  
    >  빈 모델의 DirectQuery 모드에서도 항상 각 테이블에 대해 작은 기본 제공 행 집합이 표시됩니다. 50행 데이터 집합을 보려면 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **테이블** > **테이블 속성** 을 클릭합니다.  
  
  
## <a name="see-also"></a>참고 항목  
[SSMS에서 DirectQuery 모드를 사용하도록 설정](../../analysis-services/tabular-models/enable-directquery-mode-in-ssms.md)

[디자인 모드에서 DirectQuery 모델에 샘플 데이터 추가](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md)
  