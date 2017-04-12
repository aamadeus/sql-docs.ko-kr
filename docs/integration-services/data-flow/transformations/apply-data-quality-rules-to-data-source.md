---
title: "데이터 원본에 데이터 품질 규칙 적용 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# 데이터 원본에 데이터 품질 규칙 적용
  DQS(Data Quality Services)를 통해 데이터 원본에 DQS 정리 변환을 연결하여 패키지 데이터 흐름의 데이터를 수정할 수 있습니다. DQS에 대한 자세한 내용은 [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md)을 참조하십시오. 변환에 대한 자세한 내용은 [DQS Cleansing Transformation](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)을 참조하십시오.  
  
 DQS 정리 변환을 사용하여 데이터를 처리할 경우 Data Quality 서버에 데이터 품질 프로젝트가 만들어집니다. Data Quality 클라이언트를 사용하여 프로젝트를 관리합니다. 자세한 내용은 [데이터 품질 프로젝트 열기, 잠금 해제, 이름 바꾸기 및 삭제](https://msdn.microsoft.com/library/hh510417.aspx)를 참조하세요.  
  
### 데이터 흐름에서 데이터를 수정하려면  
  
1.  패키지를 만듭니다.  
  
2.  DQS 정리 변환을 구성하고 추가합니다. 자세한 내용은 [DQS Cleansing Transformation Editor Dialog Box](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md)을 참조하세요.  
  
3.  DQS 정리 변환을 데이터 원본에 연결합니다.  
  
  