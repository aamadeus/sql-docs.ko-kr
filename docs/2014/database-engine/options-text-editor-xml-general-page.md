---
title: 옵션 (텍스트 편집기-XML-일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.General
ms.assetid: 46a9f913-d0b9-40ff-b382-9bbdec7461a6
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e5d686db29cd4fe7db3c76be22c67a2aacbec3d9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36092700"
---
# <a name="options-text-editor---xml---general-page"></a>Options (Text Editor - XML - General Page)
  이 대화 상자를 사용하여 XML 문서를 편집하는 데 사용되는 XML 편집기의 일반 편집 동작을 변경할 수 있습니다. 이러한 설정을 표시하려면 **도구** 메뉴에서 **옵션** 을 클릭하고 **XML** 하위 폴더를 확장한 다음 **일반**을 클릭합니다.  
  
## <a name="setting-options-in-multiple-locations"></a>여러 위치에서 옵션 설정  
 XML 편집기에 대한 옵션은 **모든 언어** 대화 상자(일반)에서도 설정할 수 있습니다. **모든 언어** 대화 상자를 사용하여 DMX 또는 MDX 편집기 등의 다른 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 편집기에 대해 다른 옵션을 설정하는 경우에는 이 대화 상자를 사용하여 XML 편집기 옵션을 다시 설정해야 합니다.  
  
## <a name="statement-completion"></a>문 완성  
 **멤버 목록 자동 표시**  
 이 확인란을 선택하면 편집기에 입력할 때 사용 가능한 멤버, 속성, 값 또는 메서드 목록이 표시됩니다. 팝업 목록에서 항목을 선택하면 코드에 해당 항목이 삽입됩니다.  
  
 **고급 멤버 숨기기**  
 이 확인란은 사용할 수 없습니다.  
  
 **매개 변수 정보**  
 이 확인란을 선택하면 편집기의 삽입 지점 왼쪽에 현재 선언이나 프로시저의 전체 구문이 사용 가능한 모든 매개 변수와 함께 표시됩니다. 할당할 수 있는 다음 매개 변수는 굵게 표시됩니다.  
  
## <a name="settings"></a>설정  
 **가상 공간 활성화**  
 이 확인란을 선택하면 각 코드 줄의 끝에 공백이 삽입됩니다. 이 확인란을 선택하면 코드 옆의 일정한 위치에 설명을 배치할 수 있습니다.  
  
 **자동 줄 바꿈**  
 이 확인란을 선택하면 가로로 표시되는 편집기 영역을 벗어나는 줄 부분이 자동으로 다음 줄에 표시됩니다. 이 확인란을 선택하면 **자동 줄 바꿈 시각 문자 표시** 확인란이 활성화됩니다.  
  
 **자동 줄 바꿈 시각 문자 표시**  
 이 확인란을 선택하면 긴 줄이 두 번째 줄로 줄 바꿈될 때 리턴 화살표 표시가 나타납니다. 이러한 표시가 나타나지 않게 하려면 이 확인란의 선택을 취소합니다.  
  
> [!NOTE]  
>  이 미리 알림 화살표는 코드에 추가되거나 인쇄되지 않으며 참조용으로만 사용됩니다.  
  
 **선택 영역이 없는 경우 잘라내기/복사 명령을 빈 줄에 적용**  
 이 확인란은 빈 줄에 삽입 포인터를 두고 어떤 영역도 선택하지 않은 채 **복사** 또는 **잘라내기**를 클릭한 경우의 편집기 동작을 설정합니다.  
  
 이 확인란을 선택하면 빈 줄을 복사하거나 잘라냅니다. 그런 다음 **붙여넣기**를 클릭하면 새로운 빈 줄이 삽입됩니다.  
  
 이 확인란의 선택을 취소하면 아무 것도 복사하거나 잘라내지 않습니다. 그런 다음 **붙여넣기**를 클릭하면 가장 최근에 복사한 내용을 붙여 넣습니다. 이전에 복사한 내용이 없으면 아무 것도 붙여 넣지 않습니다.  
  
 줄이 비어 있지 않으면 이 설정은 **복사** 또는 **잘라내기** 에 영향을 주지 않습니다. 어떤 영역도 선택하지 않으면 줄 전체를 복사하거나 잘라냅니다. 그런 다음 **붙여넣기**를 클릭하면 줄 전체의 텍스트와 줄 끝 문자를 붙여 넣습니다.  
  
## <a name="display"></a>디스플레이  
 **줄 번호**  
 이 확인란을 선택하면 각 코드 줄 옆에 줄 번호가 표시됩니다.  
  
> [!NOTE]  
>  이러한 줄 번호는 코드에 추가되거나 인쇄되지 않으며 참조용으로만 사용됩니다.  
  
 **단일 클릭으로 URL 탐색**  
 이 확인란을 선택하면 편집기에서 URL 위로 커서를 가져갈 때 커서가 가리키는 손 모양으로 변경됩니다. URL을 클릭하면 웹 브라우저에 해당 페이지를 표시할 수 있습니다.  
  
 **탐색 모음**  
 이 확인란은 사용할 수 없습니다.  
  
  