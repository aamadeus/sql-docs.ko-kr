---
title: "구독 뷰를 만들어 데이터 내보내기(Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "구독 뷰 [Master Data Services], 만들기"
  - "구독 뷰 만들기 [Master Data Services]"
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# 구독 뷰를 만들어 데이터 내보내기(Master Data Services)
  구독 뷰를 만들어 구독 시스템으로 Master Data Services 데이터를 내보낼 수 있습니다. 그러면 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에 데이터의 뷰가 생성됩니다.  
  
## 필수 구성 요소  
 이 절차를 수행하려면  
  
-   **통합 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다. 자세한 내용은 참조 [기능 영역 권한 & #40; Master Data Services & #41;](../master-data-services/functional-area-permissions-master-data-services.md)합니다.  
  
-   모델 관리자여야 합니다. 자세한 내용은 참조 [관리자 및 #40; Master Data Services & #41;](../master-data-services/administrators-master-data-services.md)합니다.  
  
### 구독 뷰를 만들고 편집하려면  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **통합 관리**를 클릭합니다.  
  
2.  메뉴 모음에서 **뷰 만들기**를 클릭합니다.  
  
3.  **구독 뷰** 페이지에서 보기를 만들려면 **추가** 를 클릭하고 보기를 편집하려면 **편집** 을 클릭합니다. 그러면 오른쪽에 패널이 표시됩니다.  
  
4.  **구독 뷰 만들기** 창의 **이름** 상자에 뷰의 이름을 입력합니다.  
  
     **구독 뷰 편집** 창의 **이름** 상자에 업데이트된 뷰의 이름을 입력합니다.  
  
5.  **모델** 목록에서 모델을 선택합니다.  
  
6.  선택 **일시적으로 삭제 된 멤버 포함**, 보기에서 일시적으로 삭제 된 멤버를 포함 합니다.  
  
7.  **버전 옵션** 에서 **버전** 또는 **버전 플래그**를 선택하고 해당하는 목록에서 옵션을 선택합니다.  
  
    > [!TIP]  
    >  버전 플래그를 기반으로 구독 뷰를 만듭니다. 버전을 잠그는 경우에는 구독 뷰를 업데이트하지 않고 플래그를 열린 버전에 다시 할당할 수 있습니다.  
  
8.  **데이터 원본** 옵션에서 **엔터티** 또는 **파생 계층** 을 선택하고 해당하는 목록에서 옵션을 선택합니다.  
  
9. **형식** 목록에서 구독 뷰 형식을 선택합니다.  
  
10. **형식** 목록에서 **명시적 수준** 또는 **파생 수준** 을 선택한 경우에는 뷰에 포함할 계층의 수준 수를 입력합니다.  
  
11. **저장**을 클릭합니다.  
  
## 뷰 정보  
 생성되는 각 뷰에 대해 열이 10개 포함된 행이 표에 추가됩니다. 다음 표에서는 이러한 열에 대해 설명합니다.  
  
|열|설명|  
|------------|-----------------|  
|상태|보기 상태입니다.<br /><br /> 클릭할 때 **저장**,  ![Icon for updating status](../master-data-services/media/mds-statusicon-updating.png "Icon for updating status") 디스플레이, 뷰를 업데이트 하는 나타내는 이미지입니다.<br /><br /> 만들거나 보기를 편집할 때 오류가 있는 경우는 ![Icon for error status](../master-data-services/media/mds-statusicon-error.png "Icon for error status") 이미지를 표시 합니다.<br /><br /> 그렇지 않으면 상태는 확인 및 ![Icon for OK status](../master-data-services/media/mds-statusicon-ok.png "Icon for OK status") 이미지를 표시 합니다.|  
|이름|구독 뷰 이름입니다.|  
|모델|모델 이름입니다.|  
|버전 옵션|버전 이름입니다.|  
|버전|버전 플래그 이름입니다.|  
|엔터티|파생 계층 이름입니다.|  
|데이터 원본|엔터티 이름입니다.|  
|형식|뷰의 데이터 형식을 지정합니다.|  
|Level|명시적 수준 또는 파생 수준 뷰 형식에만 사용되는 뷰의 수준 수를 지정합니다.|  
|삭제된 멤버 포함|일시 삭제된 멤버가 뷰에 포함되는지 여부를 나타냅니다.|  
  
 뷰를 클릭하면 다음 정보가 표시됩니다.  
  
-   **만든 사람**: 뷰를 만든 사용자의 이름입니다.  
  
-   **날짜**: 뷰를 만든 날짜와 시간입니다.  
  
-   **업데이트한 사람**: 뷰를 마지막으로 업데이트한 사용자의 이름입니다.  
  
-   **날짜**: 뷰를 마지막으로 업데이트한 날짜와 시간입니다.  
  
## 참고 항목  
 [개요: 데이터 및 #40; 내보내기 Master Data Services & #41;](../master-data-services/overview-exporting-data-master-data-services.md)   
 [구독 뷰 & #40; 삭제 Master Data Services & #41;](../master-data-services/delete-a-subscription-view-master-data-services.md)   
 [버전 플래그 및 #40; 만들기 Master Data Services & #41;](../master-data-services/create-a-version-flag-master-data-services.md)  
  
  