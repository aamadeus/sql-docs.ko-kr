---
title: 트리 다이어그램 연습 (데이터 마이닝 추가 기능)을 의사 결정 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- shapes, data mining
- diagram, decision tree
- Visio shapes, decision tree
- decision tree [data mining]
ms.assetid: 9566f6a2-c750-4125-ba5e-42c7251a78c7
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 951a0e0722aaa5a631140da9ddec9255246aaffd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36184151"
---
# <a name="decision-tree-diagram-walkthrough--data-mining-add-ins"></a>의사 결정 트리 다이어그램 연습 (데이터 마이닝 추가 기능)
  의사 결정 트리 모델을 만든 경우 의사 결정 트리 셰이프 또는 종속성 네트워크 셰이프를 사용하여 Visio에서 사용자 지정된 다이어그램을 만들 수 있습니다. 이 항목으로 수행할 수 있는 사용자 지정을 설명는 **의사 결정 트리** 셰이프 및 이러한 컨트롤:  
  
-   의사 결정 트리 다이어그램의 렌더링 컨트롤  
  
     이러한 옵션은의 일부는 **의사 결정 트리 마법사** Visio 작업 영역에 셰이프를 끌어서 놓을 때 시작 되 합니다.  
  
-   **데이터 마이닝 레이아웃** 도구 모음  
  
     이러한 옵션은 셰이프와 상호 작용하는 데 도움이 되도록 Visio 작업 영역에 추가되었습니다.  
  
## <a name="build-a-decision-tree-diagram"></a>의사 결정 트리 다이어그램 작성  
 의사 결정 트리 셰이프를 Visio 페이지 시작에 **의사 결정 트리 Visio 셰이프 마법사** 고 다이어그램 옵션을 설정 합니다.  
  
#### <a name="use-the-decision-tree-wizard"></a>의사 결정 트리 마법사 사용  
  
1.  표시 되지 않으면 **Microsoft 데이터 마이닝 셰이프** 에 **셰이프** 목록에서 클릭 **추가 셰이프**선택, **스텐실 열기**, 엽니다는 기본 설치 위치에서 템플릿입니다.  
  
     \<드라이브 >: \Program files (x85) \Microsoft SQL Server 2012 DM 추가 기능  
  
2.  끌어서는 **의사 결정 트리** 셰이프를 페이지로 합니다.  
  
3.  시작 페이지에서는 **의사 결정 트리 Visio 셰이프 마법사**, 클릭 **다음**합니다.  
  
4.  에 **데이터 소스 선택** 의 페이지는 **클러스터 마법사**, 한 연결을 선택는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 시각화 하려는 모델이 있는 서버.  
  
5.  적절 한 마이닝 모델을 선택 하 고 클릭 **다음**합니다.  
  
     이 다이어그램 유형은 의사 결정 트리 또는 선형 회귀 알고리즘을 사용하여 만들어진 모델을 지원합니다.  
  
6.  에 **의사 결정 트리 선택** 페이지에서 표시할 개별 트리를 선택 합니다.  
  
     트리는 모델링한 특정 결과로 이끄는 상호 작용을 모델링하므로 모델에 여러 결과가 포함된 경우에도 트리를 한 번에 하나만 표시할 수 있습니다.  
  
7.  에 **의사 결정 트리 선택** 대화 상자에서 설정할 수도 있습니다 이러한 렌더링 옵션:  
  
     **최대 렌더링 깊이**  
     표시되는 노드 수를 제어하려면 이 옵션을 사용합니다.  
  
     의사 결정 트리가 매우 깊어서 페이지에 맞지 않는 다이어그램이 만들어질 수도 있습니다. 보다 중요한 가장 왼쪽의 노드에 초점을 맞추려면 이 컨트롤을 사용합니다.  
  
     기본값은 세 수준의 노드입니다.  
  
     **색을 선택 하 고 값에 대 한 텍스트를 표시 합니다.**  
     결과를 각각 나타낼 색을 선택합니다. 색을 지정하지 않으면 현재 비디오 테마 색을 사용하여 색이 자동으로 생성됩니다.  
  
8.  클릭 **고급** 의사 결정 트리 다이어그램의 노드 각각에 대해 다음 옵션을 사용자 지정할 수 있습니다.  
  
     **음영 변수** 및 **상태**  
     트리 다이어그램에 표시하려는 대상 결과를 선택합니다.  
  
     **히스토그램 표시**  
     해당 노드를 정의하는 규칙을 표시하는 차트를 각 노드에 추가합니다.  
  
     **레이블 표시**  
     히스토그램에 열 이름을 추가합니다.  
  
     **확률 표시**  
     각 값의 확률을 표시합니다.  
  
     **지지도 표시**  
     각 값에 대한 지지도를 표시합니다.  
  
     **바닥글 표시**  
     모든 표시된 값을 요약하는 바닥글을 추가합니다.  
  
     **머리글 표시**  
     열 머리글을 추가합니다.  
  
     **지지도가 없는 상태 표시**  
     누락 값을 표시할 수 있습니다.  
  
9. 클릭 **마침** 그래프를 만듭니다.  
  
    > [!WARNING]  
    >  일부 환경에서는 차트의 연결선이 Office 2013에서 렌더링되지 못할 수도 있습니다.  
  
## <a name="explore-and-modify-the-finished-diagram"></a>완성된 다이어그램 탐색 및 수정  
 완료 한 후의 **의사 결정 트리 Visio 셰이프 마법사**, Visio 예측 결과로 이끄는 규칙을 그래픽으로 표시 된 페이지의 트리 다이어그램을 만듭니다.  
  
 의사 결정 트리 다이어그램의 다음 컨트롤을 사용하여 셰이프를 계속 수정할 수 있습니다.  
  
#### <a name="using-the-decision-tree-option-menus"></a>의사 결정 트리 옵션 메뉴 사용  
  
1.  클릭는 **추가 기능** 리본, 및 데이터 마이닝 다이어그램으로 작업에 사용 되는 사용자 지정 도구 모음 중 하나를 표시 합니다.  
  
     **레이아웃**  
     현재 페이지에 맞도록 트리의 정렬을 최적화합니다.  
  
     **페이지 크기 조정**  
     이 컨트롤은 이전 HTML 버전용입니다. Visio 페이지 크기 조정 컨트롤을 대신 사용하십시오.  
  
     **설명**  
     트리의 노드가 선택된 경우 노드의 사례에 대한 세부 정보를 표시하려면 이 옵션을 클릭합니다.  
  
2.  사용 하 여는 **페이지 레이아웃 재지정** 옵션 Visio에서 **디자인** 다른 트리 레이아웃을 시험해 리본.  
  
3.  사용 하 여는 **커넥터** 옵션에 **디자인** 탭 트리에서 노드 간에 사용 되는 연결선을 변경 합니다.  
  
4.  사용 하 여는 **을 이동 및 확대/축소** 컨트롤는 **작업창** visio 영역 **보기** 리본 메뉴는 다이어그램의 특정 영역에 초점을 합니다.  
  
5.  트리에서 아무 노드나 마우스 오른쪽 단추로 클릭하고 의사 결정 트리 다이어그램과 관련된 다음 바로 가기 메뉴 옵션 중 하나를 선택합니다.  
  
     **페이지 레이아웃 개선**  
     페이지에 노드를 고르게 배치하고 모든 노드가 표시되도록 페이지 보기를 조정합니다.  
  
     **새 페이지로 자식 노드 이동**  
     현재 선택한 노드의 자식 노드를 새 페이지로 이동합니다.  
  
     **자식 노드 축소**  
     현재 선택한 노드의 자식 노드를 숨깁니다.  
  
     **자식 노드를 확장 합니다.**  
     현재 선택한 노드의 자식 노드를 표시합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Visio 데이터 마이닝 다이어그램 문제 해결 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  