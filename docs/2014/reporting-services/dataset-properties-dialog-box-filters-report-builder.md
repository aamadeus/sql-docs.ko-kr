---
title: 데이터 집합 속성 대화 상자, 필터 (보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10025"
ms.assetid: 933a6f44-4eb7-4e73-9c40-ac0fd17b23d3
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ff8ae37c2caf34432acde8fab2235a3b83b372a6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172153"
---
# <a name="dataset-properties-dialog-box-filters-report-builder"></a>데이터 집합 속성 대화 상자, 필터(보고서 작성기)
  **데이터 집합 속성** 대화 상자에서 **필터** 를 선택하여 데이터 집합에 대한 필터를 만들 수 있습니다.  
  
 보고서 서버에 있는 공유 데이터 집합 정의의 일부인 필터는 공유 데이터 집합을 사용하는 모든 보고서에 영향을 미칩니다. 공유 데이터 집합에 대한 추가 필터는 보고서에 추가된 후 지정될 수 있습니다. 이러한 필터는 해당 필터가 정의된 보고서에만 영향을 미칩니다.  
  
 포함된 데이터 집합에 대한 필터는 해당 필터가 정의된 보고서에만 영향을 미칩니다.  
  
 자세한 내용은 [데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)을 참조하세요.  
  
## <a name="options"></a>변수  
 **추가**  
 새 필터 절을 목록에 추가합니다.  
  
 **Delete**  
 선택한 필터 절을 목록에서 삭제합니다.  
  
 **위쪽 화살표**  
 선택한 필터를 목록에서 위로 이동합니다.  
  
 **아래쪽 화살표**  
 선택한 필터를 목록에서 아래로 이동합니다.  
  
 **식**  
 필터를 적용할 식을 입력하거나 선택합니다. 식을 편집하려면 식(**fx**) 단추를 클릭합니다.  
  
 **Data type**  
 **값**에 대한 데이터 형식을 선택합니다. 가능하면 **식**에 대한 데이터 형식과 일치하는 데이터 형식을 선택합니다.  
  
 **식** 및 **값** 의 값은 동일한 데이터 형식으로 계산되어야 합니다. 예를 들어 **식** 을 데이터 형식이 System.Int32인 필드로 설정하고 **값** 을 7로 설정한 경우 드롭다운 목록에서 **정수**를 선택합니다.  
  
 필요한 데이터 형식 옵션이 드롭다운 목록에 없으면 값을 올바른 데이터 형식으로 변환하는 식을 작성합니다. 자세한 내용은 [필터 수식 예&#40;보고서 작성기 및 SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md)를 참조하세요.  
  
 **연산자**  
 식과 값을 비교하는 데 사용할 연산자를 선택합니다.  
  
 **Value**  
 **식** 상자에 지정된 식을 계산할 때 사용할 값이나 식을 입력합니다. 식을 편집하려면 식(**fx**) 단추를 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [보고서 포함된 데이터 집합 및 공유 데이터 집합&#40;보고서 작성기 및 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](report-design/report-parameters-report-builder-and-report-designer.md)   
 [데이터 집합에 필터 추가 &#40;보고서 작성기 및 SSRS&#41;](report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)   
 [보고서에 사용 되는 식 &#40;보고서 작성기 및 SSRS&#41;](report-design/expression-uses-in-reports-report-builder-and-ssrs.md)  
  
  
