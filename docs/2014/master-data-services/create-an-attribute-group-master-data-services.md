---
title: 특성 그룹 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attribute groups [Master Data Services], creating
- creating attribute groups [Master Data Services]
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0a063af91090ff2e8d5eb1145bb5968573d04523
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36181161"
---
# <a name="create-an-attribute-group-master-data-services"></a>특성 그룹 만들기(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 **탐색기** 표의 개별 탭에 특성을 표시하려는 경우 특성 그룹을 만듭니다.  
  
> [!NOTE]  
>  특성 그룹을 만들면 특성 그룹은 해당 그룹을 만든 사람을 제외한 모든 사용자로부터 자동으로 숨겨집니다. 그룹을 표시 하는 방법에 대 한 자세한 내용은 참조 [사용자에 게는 특성 그룹 표시 &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md)합니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 절차를 수행하려면  
  
-   **시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.  
  
-   모델 관리자여야 합니다. 자세한 내용은 [관리자&#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)를 참조하세요.  
  
-   하나 이상의 특성이 있어야 합니다. 자세한 내용은 [텍스트 특성 만들기&#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)를 참조하세요.  
  
### <a name="to-create-an-attribute-group"></a>특성 그룹을 만들려면  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.  
  
2.  **모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **특성 그룹**을 클릭합니다.  
  
3.  **모델** 목록에서 모델을 선택합니다.  
  
4.  **엔터티** 목록에서 엔터티를 선택합니다.  
  
5.  **리프 그룹**, **통합 그룹**또는 **컬렉션 그룹** 을 클릭하여 각각 리프 멤버, 통합 멤버 또는 컬렉션의 특성 그룹을 만듭니다.  
  
6.  클릭 **특성 그룹 추가**합니다.  
  
7.  에 **리프 그룹 이름** 상자는 그룹에 대 한 이름을 입력 합니다. 이 탭에 표시 되는 이름을 **탐색기**합니다.  
  
    > [!NOTE]  
    >  선택한 경우 **통합 그룹** 또는 **컬렉션 그룹** 5 단계에서이 상자는 **통합 그룹 이름** 또는 **컬렉션 그룹 이름**각각.  
  
8.  **그룹 저장**을 클릭합니다.  
  
9. 그룹에 해당하는 폴더를 확장합니다.  
  
10. **특성**을 클릭합니다.  
  
11. **선택한 항목 편집**을 클릭합니다.  
  
12. 특성을 클릭는 **사용 가능** 상자 한 클릭는 **추가** 화살표입니다. 모두 추가하려면 **모두 추가** 화살표를 클릭합니다.  
  
13. 필요에 따라는 **를** 및 **아래로** 특성의 왼쪽-오른쪽 순서를 변경 하려면 화살표입니다.  
  
14. **저장**을 클릭합니다.  
  
## <a name="next-steps"></a>다음 단계  
  
-   [특성 그룹을 사용자에 게 표시 되도록 설정 &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md)  
  
## <a name="see-also"></a>관련 항목  
 [특성 그룹 &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md)   
 [특성 &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)   
 [특성 그룹 이름 변경&#40;Master Data Services&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md)   
 [특성 그룹 삭제&#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md)   
 [리프 권한 &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [사용 권한 통합 &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  