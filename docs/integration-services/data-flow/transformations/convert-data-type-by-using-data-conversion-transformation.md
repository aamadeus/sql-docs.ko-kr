---
title: "데이터 변환을 사용하여 데이터를 다른 데이터 형식으로 변환 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "데이터 형식 변환 [Integration Services]"
  - "데이터 변환"
  - "데이터 형식 [Integration Services], 변환"
ms.assetid: 4aabbe4f-7666-4672-865a-9627bd25fbfd
caps.latest.revision: 41
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 41
---
# 데이터 변환을 사용하여 데이터를 다른 데이터 형식으로 변환
  데이터 변환을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 하나의 원본이 이미 들어 있어야 합니다.  
  
### 데이터를 다른 데이터 형식으로 변환하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.  
  
3.  **데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 데이터 변환을 디자인 화면으로 끌어 옵니다.  
  
4.  원본이나 이전 변환에서 연결선을 데이터 변환으로 끌어서 데이터 변환을 데이터 흐름에 연결합니다.  
  
5.  데이터 변환을 두 번 클릭합니다.  
  
6.  **데이터 변환 편집기** 대화 상자의 **사용 가능한 입력 열** 테이블에서 변환하려는 데이터 형식의 열 옆에 있는 확인란을 선택합니다.  
  
    > [!NOTE]  
    >  입력 열에 여러 개의 데이터 변환을 적용할 수 있습니다.  
  
7.  선택적으로 **출력 별칭** 열의 기본값을 수정합니다.  
  
8.  **데이터 형식** 목록에서 열에 사용할 새 데이터 형식을 선택합니다. 기본 데이터 형식은 입력 열의 데이터 형식입니다.  
  
9. 선택한 데이터 형식에 따라 선택적으로 **길이**, **전체 자릿수**, **소수 자릿수**및 **코드 페이지** 열에서 값을 업데이트합니다.  
  
10. 오류 출력을 구성하려면 **오류 출력 구성**을 클릭합니다. 자세한 내용은 [데이터 흐름 구성 요소에서 오류 출력 구성](../../../integration-services/troubleshooting/configure-an-error-output-in-a-data-flow-component.md)을 참조하세요.  
  
11. **확인**을 클릭합니다.  
  
12. 업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.  
  
## 관련 항목:  
 [데이터 변환](../../../integration-services/data-flow/transformations/data-conversion-transformation.md)   
 [Integration Services 변환](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Integration Services 경로](../../../integration-services/data-flow/integration-services-paths.md)   
 [Integration Services 데이터 형식](../../../integration-services/data-flow/integration-services-data-types.md)   
 [데이터 흐름 태스크](../../../integration-services/control-flow/data-flow-task.md)  
  
  