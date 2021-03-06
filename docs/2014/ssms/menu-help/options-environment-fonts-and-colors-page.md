---
title: '옵션 (환경: 글꼴 및 색 페이지) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: ea3aa222-538d-485f-99dc-01eb02cdcfea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f2a73bd30ab72cc293f8cbd0dcebc2b123d6538e
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51031811"
---
# <a name="options-environment-fonts-and-colors-page"></a>옵션(환경: 글꼴 및 색 페이지)
  **옵션** 대화 상자를 통해 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 여러 사용자 인터페이스 요소에 사용되는 사용자 지정 글꼴 및 색 구성표를 설정할 수 있습니다. **도구** 메뉴에서 **옵션** 을 클릭하고 **환경** 폴더를 확장한 다음 **글꼴 및 색**을 선택합니다.  
  
 색 구성표 변경 내용은 설정을 변경하는 세션 동안에는 적용되지 않습니다. 다른 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 인스턴스를 열고 변경 내용이 적용될 만한 상황을 만들어 색 변경 내용을 평가할 수 있습니다.  
  
## <a name="uielement-list"></a>UIElement 목록  
 **설정 표시**  
 글꼴과 색 구성표를 변경할 수 있는 모든 사용자 인터페이스 요소를 나열합니다. 이 목록에서 항목을 선택한 후에는 **표시 항목**에서 선택한 항목의 색 설정을 사용자 지정할 수 있습니다.  
  
|용어|정의|  
|----------|----------------|  
|텍스트 편집기|텍스트 편집기에 대한 글꼴 스타일, 크기 및 색 표시 설정 변경 내용은 기본 텍스트 편집기에 표시되는 텍스트의 모양에 영향을 줍니다. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 외부의 텍스트 편집기에서 연 문서에는 이 설정이 적용되지 않습니다.|  
|프린터|프린터에 대한 글꼴 스타일, 크기 및 색 표시 설정 변경 내용은 인쇄된 문서의 텍스트 모양에 영향을 줍니다.<br /><br /> 팁: 필요에 따라 텍스트 편집기에서 표시 되는 보다 인쇄에 대 한 다른 기본 글꼴을 선택할 수 있습니다. 이러한 설정은 싱글바이트 문자와 더블바이트 문자가 모두 포함되어 있는 코드를 인쇄하는 경우에 유용합니다.|  
|[모든 텍스트 도구 창 **]**|이 항목에 대한 글꼴 스타일, 크기 및 색 표시 설정 변경 내용은 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에 출력 창이 표시되는 도구 창의 텍스트 모양에 영향을 줍니다. 예를 들어 출력 창, 텍스트 결과 창 등이 있습니다.<br /><br /> 참고: [모든 텍스트 도구 창] 항목에 대한 변경 내용은 설정을 변경하는 세션 동안에는 적용되지 않습니다. 다른 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]인스턴스를 열어 이러한 변경 내용을 평가할 수 있습니다.|  
|찾기 결과 창|이 항목에 대한 글꼴 스타일, 크기 및 색 표시 설정 변경 내용은 찾기 결과 창의 텍스트 모양에 영향을 줍니다.|  
|출력 창|이 항목에 대한 글꼴 스타일, 크기 및 색 표시 설정 변경 내용은 출력 창의 텍스트 모양에 영향을 줍니다.|  
|표 형태 결과|이 항목에 대한 글꼴 스타일, 크기 및 색 표시 설정 변경 내용은 쿼리 창의 **표 형태 결과** 영역에 표시되는 텍스트 모양에 영향을 줍니다.|  
|실행 계획|이 항목에 대한 글꼴 스타일, 크기 및 색 표시 설정 변경 내용은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 쿼리의 실행 계획에 표시되는 텍스트 모양에 영향을 줍니다.|  
|텍스트 결과|이 항목에 대한 글꼴 스타일, 크기 및 색 표시 설정 변경 내용은 쿼리 창의 **텍스트 결과** 영역에 표시되는 텍스트 모양에 영향을 줍니다.|  
|비즈니스 인텔리전스 디자이너|이 항목에 대한 글꼴 스타일, 크기 및 색 표시 설정 변경 내용은 비즈니스 인텔리전스 디자이너 창에 표시되는 텍스트 모양에 영향을 줍니다.|  
  
 **기본값 사용**  
 **기본값 사용** 단추를 클릭하면 값이 **설정 표시** 목록에서 선택한 목록 항목의 기본 글꼴 및 색 값으로 다시 설정됩니다.  
  
 **글꼴(굵은 글꼴은 고정 너비 글꼴을 나타냄)**  
 시스템에 설치되어 있는 모든 글꼴을 나열합니다. 이 드롭다운 목록을 처음으로 열면 **설정 표시** 목록에서 선택한 요소의 현재 글꼴이 선택됩니다. 편집기에서 맞추기가 쉬운 고정 글꼴은 굵은 글꼴로 표시됩니다.  
  
 **크기**  
 선택한 글꼴에 사용할 수 있는 글꼴 크기를 나열합니다. 글꼴 크기를 변경하면 **설정 표시** 에서 선택한 항목에 대한 모든 **표시 항목** 에 영향을 줍니다.  
  
 **표시 항목**  
 전경색과 배경색을 수정할 수 있는 모든 항목을 나열합니다.  
  
> [!NOTE]  
>  기본 표시 항목에는 텍스트입니다. 텍스트에 지정된 이 속성은 다른 표시 항목에 지정된 속성에 의해 덮어써집니다. 예를 들어 **텍스트** 색을 파랑으로 지정하고 식별자 색을 녹색으로 지정하면 모든 식별자가 녹색으로 표시됩니다. 이 예에서는 식별자 속성이 텍스트 속성을 덮어쓴 것입니다.  
  
 일부 표시 항목에는 다음과 같은 옵션이 포함되어 있습니다.  
  
-   표시기 여백: 코드 편집기 왼쪽에 중단점 아이콘과 책갈피 아이콘이 표시되는 여백입니다.  
  
-   축소 가능 텍스트: 코드 편집기에서 보기로 또는 보기에서 전환할 수 있는 텍스트 또는 코드 블록입니다(XML만 해당).  
  
 **항목 전경**  
 **표시 항목**에서 선택한 항목의 전경색으로 사용할 수 있는 색을 나열합니다. 일부 항목은 서로 관련이 있기 때문에 표시 구성표의 일관성을 유지해야 합니다. 예를 들어 텍스트의 전경색을 변경하면 문자열과 같은 요소의 전경색도 변경됩니다.  
  
 **Custom**  
 **표시 항목** 목록에서 선택한 항목의 사용자 지정 색을 설정하는 **색** 대화 상자를 표시합니다.  
  
> [!NOTE]  
>  컴퓨터 디스플레이의 색 설정에 따라 사용자 지정 색을 정의하는 기능이 제한될 수 있습니다. 예를 들어 컴퓨터가 256색을 표시하도록 설정되어 있는 경우 **색** 대화 상자에서 사용자 지정 색을 선택하면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서는 **기본 색** 중 가장 가까운 색을 기본값으로 선택하고 **색** 대화 상자에는 검정색을 표시합니다.  
  
 **항목 배경**  
 **표시 항목**에서 선택한 항목의 배경색을 선택할 수 있는 색상표를 제공합니다. 일부 항목은 서로 관련이 있기 때문에 표시 구성표의 일관성을 유지해야 합니다. 예를 들어 텍스트의 배경색을 변경하면 문자열과 같은 요소의 배경색도 변경됩니다.  
  
 **사용자 지정**  
 **표시 항목** 목록에서 선택한 항목의 사용자 지정 색을 설정하는 **색** 대화 상자를 표시합니다.  
  
 **굵게**  
 선택한 표시 항목의 텍스트를 굵은 글꼴로 표시하려면 이 확인란을 선택합니다. 굵은 글꼴의 텍스트는 편집기에서 찾기가 쉽습니다.  
  
 **예제**  
 **설정 표시** 및 **표시 항목**에서 선택한 값에 대한 글꼴 스타일, 크기 및 색 구성표 샘플을 표시합니다. 이 입력란을 사용하여 여러 서식 옵션을 적용한 결과를 미리 볼 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [쿼리 편집기에서 코드 색상 지정](../../relational-databases/scripting/color-coding-in-query-editors.md)   
 [옵션 &#40;텍스트 편집기: 편집기 탭 및 상태 표시줄 페이지&#41;](../../database-engine/options-text-editor-editor-tab-and-status-bar-page.md)  
  
  
