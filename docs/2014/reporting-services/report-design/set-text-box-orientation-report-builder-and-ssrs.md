---
title: 입력란 방향 설정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 1e5639e83d3d0abcb9999d03ea0ce954c8824556
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48119583"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>입력란 방향 설정(보고서 작성기 및 SSRS)
  입력란의 방향을 수평, 수직(위에서 아래로 텍스트 읽기) 또는 270도 회전(아래에서 위로 텍스트 읽기)으로 설정할 수 있습니다. 방향이 텍스트가 아니라 입력란에 대해 설정되기 때문에 방향은 입력란의 모든 텍스트에 적용됩니다. 텍스트의 일부에 대해 다른 방향을 지정할 수는 없습니다. 회전된 텍스트를 포함하도록 열 너비와 행 높이를 수동으로 조정합니다.  
  
 텍스트 방향을 지정할 때 사용 하는 WritingMode 속성을 사용할 수 없습니다는 **텍스트 상자 속성** 대화 상자. 즉, 속성 창을 열고 해당 속성을 설정해야 합니다. WritingMode 속성에 대 한 사용 가능한 값은 **가로** (텍스트 읽기 왼쪽에서 오른쪽), **세로** (위에서 아래로 읽는 텍스트), **Rotate270** (텍스트 읽기 위에서 아래로)입니다. 텍스트를 포함하도록 열 너비와 행 높이를 수동으로 조정해야 합니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-text-orientation"></a>텍스트 방향을 설정하려면  
  
1.  새 보고서를 만들거나 기존 보고서를 엽니다.  
  
2.  속성 창이 열려 있지 않으면 **보기** 탭을 클릭하고 **속성** 확인란을 선택합니다.  
  
3.  텍스트 방향을 변경할 입력란을 클릭합니다.  
  
4.  속성 창에서 드롭 다운 목록에서 속성 텍스트 상자에 적용할 텍스트 방향을 선택 WritingMode를 찾습니다.  
  
    > [!NOTE]  
    >  속성 창의 속성이 범주로 구성되어 있는 경우 WritingMode는 **지역화** 범주에 있습니다.  
  
5.  목록 상자에서 **Horizontal**, **Vertical**또는 **Rotate270**을 선택합니다.  
  
## <a name="see-also"></a>관련 항목  
 [텍스트 상자 &#40;보고서 작성기 및 SSRS&#41;](text-boxes-report-builder-and-ssrs.md)   
 [자습서: 텍스트 서식 지정&#40;보고서 작성기&#41;](../tutorial-format-text-report-builder.md)  
  
  
