---
title: 마이닝 모델에서 열 제외 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 937a28d77b8398855773cb1c11799de6112a04fa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="exclude-a-column-from-a-mining-model"></a>마이닝 모델에서 열 제외
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  새 마이닝 모델을 만들 때 모델의 기반이 되는 마이닝 구조의 일부 열만 사용할 수도 있습니다. 예를 들어 드릴스루를 위해 추가한 고객 이름 열을 모델링에는 사용하지 않으려는 경우가 있습니다. 또는 여러 다른 불연속화가 있는 열의 여러 복사본을 만든 후 각 모델에 해당 복사본 중 하나만 사용하고 나머지는 무시할 수 있습니다. 여러 다른 모델에 입력 열을 선택적으로 추가하여 추가된 변수가 출력 열에 영향을 주는 방식을 확인할 수도 있습니다.  
  
 각 열 조합에 대해 새 마이닝 구조를 만들 필요가 없습니다. 대신, 특정 모델에서 사용되지 않도록 열에 플래그를 지정할 수 있습니다.  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a>마이닝 모델에서 열을 제외하려면  
  
1.  **의 데이터 마이닝 디자이너에서** 마이닝 모델 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]탭을 선택하고 해당 마이닝 모델에서 제외할 열에 해당하는 셀을 선택합니다.  
  
2.  드롭다운 목록 상자에서 **무시** 를 선택합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [마이닝 모델 태스크 및 방법](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  