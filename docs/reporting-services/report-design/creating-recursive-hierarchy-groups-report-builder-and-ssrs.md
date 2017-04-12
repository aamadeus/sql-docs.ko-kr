---
title: "재귀 계층 구조 그룹 생성(보고서 작성기 및 SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# 재귀 계층 구조 그룹 생성(보고서 작성기 및 SSRS)
페이지가 매겨진 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서에 부모와 자식 간의 관계가 데이터 집합의 필드로 표현되는 재귀 데이터를 표시하려면 자식 필드를 기반으로 데이터 영역 그룹 식을 설정하고 부모 필드를 기반으로 Parent 속성을 설정합니다.  
  
 계층적 데이터를 표시하는 것은 조직도의 직원과 같은 재귀 계층 구조 그룹에 일반적입니다. 데이터 집합에는 직원 및 관리자 목록이 포함되며 관리자 이름은 직원 목록에도 나타납니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## 재귀 계층 만들기  
 테이블릭스 데이터 영역에서 재귀 계층 구조를 작성하려면 자식 데이터를 지정하는 필드로 그룹 식을 설정하고 부모 데이터를 지정하는 필드로 그룹의 Parent 속성을 설정해야 합니다. 예를 들어 직원 ID 및 관리자 ID에 대한 필드를 포함하는 데이터 집합이 있으며 직원이 관리자에게 보고하는 경우 그룹 식을 직원 ID로 설정하고 Parent 속성을 관리자 ID로 설정합니다.  
  
 재귀 계층 구조로 정의된 그룹, 즉 Parent 속성을 사용하는 그룹에는 그룹 식이 하나만 있을 수 있습니다. 입력란 안쪽 여백에 **Level** 함수를 사용하여 계층에서의 수준을 기준으로 직원 이름을 들여쓸 수 있습니다.  
  
 자세한 내용은 [데이터 영역에서 그룹 추가 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) 및 [재귀 계층 구조 그룹 만들기&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/create-a-recursive-hierarchy-group-report-builder-and-ssrs.md)를 참조하세요.  
  
### 재귀를 지원하는 집계 함수  
 매개 변수 *Recursive* 를 허용하는 Reporting Services 집계 함수를 사용하여 재귀 계층 구조의 요약 데이터를 계산할 수 있습니다. 다음 함수 **Sum** , [Avg](../../reporting-services/report-design/sum-function-report-builder-and-ssrs.md), [Count](../../reporting-services/report-design/avg-function-report-builder-and-ssrs.md), [CountDistinct](../../reporting-services/report-design/count-function-report-builder-and-ssrs.md), [CountRows](../../reporting-services/report-design/countdistinct-function-report-builder-and-ssrs.md), [Max](../../reporting-services/report-design/countrows-function-report-builder-and-ssrs.md), [Min](../../reporting-services/report-design/max-function-report-builder-and-ssrs.md), [StDev](../../reporting-services/report-design/min-function-report-builder-and-ssrs.md), [StDevP](../../reporting-services/report-design/stdev-function-report-builder-and-ssrs.md), [Sum](../../reporting-services/report-design/stdevp-function-report-builder-and-ssrs.md), [Var](../../reporting-services/report-design/sum-function-report-builder-and-ssrs.md)및 [VarP](../../reporting-services/report-design/var-function-report-builder-and-ssrs.md)는 매개 변수로 [Recursive](../../reporting-services/report-design/varp-function-report-builder-and-ssrs.md)을 허용합니다. 자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md)를 참조하세요.  
  
## 관련 항목:  
 [테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [테이블릭스 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md)   
 [테이블&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [행렬&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [목록&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)    
 [테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  