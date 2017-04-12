---
title: "데이터 흐름에서 구성 요소 추가 또는 삭제 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "구성 요소 추가"
  - "구성 요소 [Integration Services], 데이터 흐름"
ms.assetid: d99124f9-0994-4f40-a48e-fdca6a4383e7
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# 데이터 흐름에서 구성 요소 추가 또는 삭제
  데이터 흐름 구성 요소는 데이터 흐름에 있는 원본, 대상 및 변환입니다. 데이터 흐름에 구성 요소를 추가하려면 패키지의 제어 흐름에 데이터 흐름 태스크 포함되어 있어야 합니다.  
  
 다음 절차에서는 패키지의 데이터 흐름에서 구성 요소를 추가하거나 삭제하는 방법에 대해 설명합니다.  
  
### 데이터 흐름에 구성 요소를 추가하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.  
  
3.  **제어 흐름** 탭을 클릭한 후 구성 요소를 추가하려는 데이터 흐름이 들어 있는 데이터 흐름 태스크를 두 번 클릭합니다.  
  
4.  도구 상자에서 **데이터 흐름 원본**, **데이터 흐름 변환**또는 **데이터 흐름 대상**을 확장한 후 데이터 흐름 항목을 **데이터 흐름** 탭의 디자인 화면으로 끌어 옵니다.  
  
5.  업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.  
  
### 데이터 흐름에서 구성 요소를 삭제하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.  
  
3.  **제어 흐름** 탭을 클릭한 후 구성 요소를 삭제하려는 데이터 흐름이 들어 있는 데이터 흐름 태스크를 두 번 클릭합니다.  
  
4.  데이터 흐름 구성 요소를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.  
  
5.  삭제 작업을 확인합니다.  
  
6.  업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.  
  
## 관련 항목:  
 [데이터 흐름의 구성 요소 연결](../../integration-services/data-flow/connect-components-in-a-data-flow.md)   
 [데이터 흐름 구성 요소에서 오류 출력 구성](../../integration-services/troubleshooting/configure-an-error-output-in-a-data-flow-component.md)   
 [데이터 흐름](../../integration-services/data-flow/data-flow.md)  
  
  