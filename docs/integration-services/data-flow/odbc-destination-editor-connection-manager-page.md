---
title: "ODBC 대상 편집기(연결 관리자 페이지) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.odbcdest.connection.f1"
ms.assetid: f6d9c6c2-e4c4-468b-9e0d-af7b9609614d
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# ODBC 대상 편집기(연결 관리자 페이지)
  **ODBC 대상 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 대상에 대한 ODBC 연결 관리자를 선택할 수 있습니다. 이 페이지를 사용하면 데이터베이스에서 테이블이나 뷰를 선택할 수도 있습니다.  
  
 ODBC 대상에 대한 자세한 내용은 [ODBC Destination](../../integration-services/data-flow/odbc-destination.md)을 참조하십시오.  
  
 **ODBC 대상 편집기의 연결 관리자 페이지를 열려면**  
  
## 작업 목록  
  
-   [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 ODBC 대상이 있는 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 패키지를 엽니다.  
  
-   **데이터 흐름** 탭에서 ODBC 대상을 두 번 클릭합니다.  
  
-   **ODBC 대상 편집기**에서 **연결 관리자**를 클릭합니다.  
  
## 옵션  
  
### ODBC 대상 편집기  
 목록에서 기존 ODBC 연결 관리자를 선택하거나 새로 만들기를 클릭하여 새 연결을 만듭니다. 어느 ODBC 지원 데이터베이스에나 연결할 수 있습니다.  
  
### 새로 만들기  
 **새로 만들기**를 클릭합니다. 새 연결 관리자를 만들 수 있는 **ODBC 연결 관리자 편집기 구성** 대화 상자가 열립니다.  
  
### 데이터 액세스 모드  
 대상으로 데이터를 로드하는 방법을 선택합니다. 옵션은 다음 표에 표시되어 있습니다.  
  
|옵션|Description|  
|------------|-----------------|  
|테이블 이름 - 일괄 처리|일괄 처리 모드에서 작업하도록 ODBC 대상을 구성하려면 이 옵션을 선택합니다. 이 옵션을 선택하면 다음 옵션을 사용할 수 있습니다.|  
||**테이블 또는 뷰 이름**: 목록에서 사용 가능한 테이블이나 뷰를 선택합니다.<br /><br /> 이 목록에는 처음 1000개의 테이블만 포함되어 있습니다. 데이터베이스에 포함되어 있는 테이블이 1000개를 넘는 경우 테이블 이름의 시작 부분을 입력하거나 와일드카드(\*)를 통해 이름의 일부를 입력하여 사용할 테이블을 표시합니다.<br /><br /> **일괄 처리 크기**: 대량 로드에 대한 일괄 처리 크기를 입력합니다. 일괄 처리로 로드되는 행의 개수입니다.|  
|테이블 이름 - 행 단위|각 행을 한 번에 하나씩 대상 테이블에 삽입하도록 ODBC 대상을 구성하려면 이 옵션을 선택합니다. 이 옵션을 선택하면 다음 옵션을 사용할 수 있습니다.|  
||**테이블 또는 뷰 이름**: 목록의 데이터베이스에서 사용 가능한 테이블이나 뷰를 선택합니다.<br /><br /> 이 목록에는 처음 1000개의 테이블만 포함되어 있습니다. 데이터베이스에 포함되어 있는 테이블이 1000개를 넘는 경우 테이블 이름의 시작 부분을 입력하거나 와일드카드(*)를 통해 이름의 일부를 입력하여 사용할 테이블을 표시합니다.|  
  
### 미리 보기  
 **미리 보기** 를 클릭하면 선택한 테이블의 데이터 행을 최대 200개까지 볼 수 있습니다.  
  
## 관련 항목:  
 [ODBC 대상 사용자 지정 속성](../../integration-services/data-flow/odbc-destination-custom-properties.md)   
 [ODBC 대상 편집기&#40;매핑 페이지&#41;](../../integration-services/data-flow/odbc-destination-editor-mappings-page.md)   
 [ODBC 대상 편집기&#40;오류 출력 페이지&#41;](../../integration-services/data-flow/odbc-destination-editor-error-output-page.md)  
  
  