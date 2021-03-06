---
title: '3단계: 3단원 자습서 패키지 테스트 | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ca00f40146d5019f770e3141d3961e40ed526ccc
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51559162"
---
# <a name="lesson-3-3---testing-the-lesson-3-tutorial-package"></a>3-3단원 - 3단원 자습서 패키지 테스트
이 태스크에서는 Lesson 3.dtsx 패키지를 실행합니다. 패키지를 실행하면 이벤트 로그 창에 로그 파일에 기록된 로그 항목이 나열됩니다. 패키지 실행을 끝낸 후 로그 공급자가 생성한 로그 파일 내용을 확인합니다.  
  
## <a name="checking-the-package-layout"></a>패키지 레이아웃 확인  
패키지를 테스트하려면 먼저 3단원 패키지의 제어 흐름과 데이터 흐름에 다음 다이어그램에 표시된 개체가 있는지 확인해야 합니다. 제어 흐름은 2단원의 제어 흐름과 동일해야 합니다. 데이터 흐름은 1-2단원의 데이터 흐름과 동일해야 합니다.  
  
**제어 흐름**  
  
![패키지의 제어 흐름](../integration-services/media/task4lesson2control.gif "패키지의 제어 흐름")  
  
**데이터 흐름**  
  
![패키지의 데이터 흐름](../integration-services/media/task9lesson1data.gif "패키지의 데이터 흐름")  
  
### <a name="to-run-the-lesson-3-tutorial-package"></a>3단원 자습서 패키지를 실행하려면  
  
1.  SSIS 메뉴에서 이벤트 로그를 클릭합니다.  
  
2.  **디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.  
  
3.  패키지의 실행이 완료된 후에 **디버그** 메뉴에서 **디버깅 중지**를 클릭합니다.  
  
### <a name="to-examine-the-generated-log-file"></a>생성된 로그 파일을 검토하려면  
  
-   메모장이나 다른 텍스트 편집기를 사용하여 TutorialLog.log 파일을 엽니다.  
  
-   **PipelineExecutionPlan** 및 **PipelineExecutionTrees** 이벤트에 대해 생성된 정보의 의미 체계가 이 자습서의 범위를 초과하더라도 **SSIS 로그 구성** 대화 상자의 **자세히** 탭에 지정된 정보 필드가 첫 번째 줄에 표시됩니다. 또한 Foreach 루프가 반복될 때마다 선택한 두 이벤트 PipelineExecutionPlan과 PipelineExecutionTrees가 로그되어 있는 것을 확인할 수 있습니다.  
  
## <a name="next-lesson"></a>다음 단원  
[4단원: SSIS를 사용하여 오류 흐름 리디렉션 추가](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  
  
