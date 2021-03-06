---
title: 새 세션 대화 상자를 사용 하 여 확장된 이벤트 세션 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.SSMS.XEDISPLAY.GROUPING.F1
- SQL12.SSMS.XEDISPLAY.AGGREGATION.F1
- SQL12.SSMS.XEDISPLAY.NEWMERGEDCOLUMN.F1
- SQL12.SSMS.XENEWEVENTSESSION.GENERAL.F1
- SQL12.SSMS.XEDISPLAY.EDITCOLUMNS.F1
- SQL12.SSMS.XEDISPLAY.FILTERS.F1
helpviewer_keywords:
- Extended Events Dialog Box
ms.assetid: 6b2244bc-df6a-4b0a-990e-ddd8d42f7907
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0bfce6c45fcfefd214511c994b3d87fd34bf8282
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150613"
---
# <a name="create-an-extended-events-session-using-the-new-session-dialog"></a>새 세션 대화 상자를 사용하여 확장 이벤트 세션 만들기
  새 세션 대화 상자에서는 데이터를 캡처, 표시 및 분석하는 확장 이벤트 세션을 정의할 수 있습니다. 새 세션 대화 상자에는 모든 확장 이벤트 기능이 표시됩니다.  
  
 [새 세션 마법사](../ssms/object/object-explorer.md) 에서는 또한 대부분의 확장 이벤트 기능을 지원하는 확장 이벤트 세션을 정의할 수 있습니다.  
  
## <a name="before-you-begin"></a>시작하기 전 주의 사항  
 새 세션 대화 상자를 열려면 개체 탐색기에서 **관리** 노드를 확장하고 **확장 이벤트**를 확장합니다. **세션**을 마우스 오른쪽 단추로 클릭하고 **새 세션**을 클릭합니다.  
  
##  <a name="BeforeYouBegin"></a> 사용 권한  
 확장 이벤트 세션을 만들려면 ALTER ANY EVENT SESSION 권한이 있어야 합니다.  
  
## <a name="to-create-an-extended-events-session-using-the-new-session-dialog"></a>새 세션 대화 상자를 사용하여 확장 이벤트 세션을 만들려면  
 **일반** 페이지를 사용하여 템플릿을 선택하고 이벤트 세션을 예약할 수 있습니다.  
  
#### <a name="to-select-a-template-and-schedule-an-event-session"></a>템플릿을 선택하고 이벤트 세션을 예약하려면  
  
1.  개체 탐색기에서 **관리** 노드를 확장하고 **확장 이벤트**를 확장합니다. **세션**을 마우스 오른쪽 단추로 클릭하고 **새 세션**을 클릭합니다.  
  
2.  **일반** 페이지의 **세션 이름** 상자에 이벤트 세션에 대한 의미 있는 이름을 입력합니다.  
  
3.  **템플릿** 상자의 드롭다운 목록에서 사용할 템플릿을 선택합니다.  
  
     일반적인 문제를 위해 디자인된 미리 구성된 템플릿 집합에서 선택하거나, **파일 원본** 을 선택하여 이전 세션 정의에서 내보낸 템플릿 파일을 사용할 수 있습니다. 템플릿을 적용한 후 세션의 구성을 변경할 수도 있습니다.  
  
4.  서버를 시작할 때 세션을 시작하려면 **일정** 섹션에서 **서버 시작 시 이벤트 세션 시작** 확인란을 선택합니다.  
  
     세션을 만든 후 세션을 시작하려면 **세션을 만든 후 즉시 이벤트 세션 시작** 확인란을 선택합니다.  
  
5.  이벤트 세션의 라이브 데이터를 확인하려면 **캡처 시 화면에서 라이브 데이터 감시**를 클릭합니다. 라이브 데이터는 세션이 만들어진 후 즉시 추적을 표시하기 시작합니다.  
  
6.  여러 태스크에 걸쳐 작업을 추적하려면 **인과 관계 추적** 섹션에서 **이벤트 관계 추적** 확인란을 선택합니다.  
  
     인과 관계 추적에 대한 자세한 내용은 [SQL Server Extended Events Sessions](../relational-databases/extended-events/sql-server-extended-events-sessions.md) 항목의 "세션 내용 및 특징"을 참조하세요.  
  
     세션에 이벤트를 추가하려면 **페이지 선택** 섹션에서 **이벤트**를 클릭합니다.  
  
    > [!NOTE]  
    >  이벤트 세션 만들기를 완료할 때까지 **확인** 을 클릭하지 마세요.  
  
 **이벤트** 페이지를 사용하여 세션에 대해 캡처할 이벤트를 찾아 추가할 수 있습니다.  
  
#### <a name="to-add-events-to-a-session"></a>세션에 이벤트를 추가하려면  
  
1.  새 세션 대화 상자의 **페이지 선택** 섹션에서 **이벤트**를 선택합니다.  
  
2.  **이벤트** 페이지에서 **선택** 을 클릭합니다. 이미 **캡처할 이벤트 선택** 화면이 표시되어 있는 경우에는 **선택** 단추가 흐리게 표시됩니다.  
  
     **이벤트 라이브러리** 상자에 검색할 텍스트를 입력하여 테이블의 단어를 검색할 수 있습니다. 예를 들어 **lock_acquired** 이벤트를 찾으려면 **lock** 또는 **lock acquire**를 입력합니다.  
  
3.  **이벤트 라이브러리** 섹션의 드롭다운 목록에서 캡처할 이벤트의 검색 방법을 선택합니다. 예를 들어 이벤트 이름을 검색하거나 이벤트 이름과 설명을 검색할 수 있습니다. **검색** 상자에 검색 조건을 입력합니다.  
  
    > [!NOTE]  
    >  **디버그** 채널의 이벤트는 기본적으로 숨겨져 있습니다. 디버그 이벤트를 표시하려면 **채널** 드롭다운 목록에서 **디버그** 를 선택합니다.  
  
     선택한 이벤트의 세부 정보가 세부 정보 창의 **이벤트 라이브러리**아래에 표시됩니다.  
  
     이벤트는 이름을 기준으로 사전순으로 정렬됩니다. 적절한 열 제목을 클릭하여 다른 이벤트 세부 정보를 기준으로 정렬할 수도 있습니다. 예를 들어 **범주** 또는 **채널** 열을 기준으로 정렬할 수 있습니다.  
  
4.  캡처할 이벤트를 선택하고 오른쪽 화살표를 클릭하여 이벤트를 **선택한 이벤트** 섹션으로 이동합니다.  
  
    > [!NOTE]  
    >  Ctrl 또는 Shift 키를 사용하여 **이벤트 라이브러리** 에서 여러 이벤트를 한 번에 선택할 수 있습니다.  
  
     선택한 이벤트를 구성하려면 **구성**을 클릭합니다.  
  
    > [!NOTE]  
    >  이벤트 세션 만들기를 완료할 때까지 **확인** 을 클릭하지 마세요.  
  
 **데이터 저장소** 페이지를 사용하여 이벤트 세션에 대상을 추가할 수 있습니다. 대상은 이벤트 데이터를 저장하며, 나중에 세션의 이벤트 데이터를 보고 집계하기 위해 이벤트를 파일에 저장하는 등의 동작을 수행할 수 있습니다. 확장 이벤트 대상에 대한 자세한 내용은 [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md)을 참조하세요.  
  
 확장 이벤트 세션에 사용할 수 있는 대상은 다음과 같습니다.  
  
-   **etw_classic_sync_target**. SQL Server 이벤트와 Windows 운영 체제 또는 응용 프로그램 이벤트 데이터의 상관 관계를 파악하는 데 사용합니다.  
  
-   **event_counter**. 확장 이벤트 세션이 시작된 후 발생하는 지정된 모든 이벤트의 수를 셉니다. 전체 이벤트 컬렉션의 오버헤드를 증가시키지 않으면서 작업 특성에 대한 정보를 얻는 데 사용합니다.  
  
-   **event_file**. 완료된 메모리 버퍼에서 디스크로 이벤트 세션 출력을 쓰는 데 사용합니다.  
  
-   **histogram**: 지정된 이벤트 열 또는 동작을 기반으로 지정된 이벤트가 발생한 횟수를 계산하는 데 사용합니다.  
  
-   **pair_matching**. 쌍을 이루는 집합에서 지정된 쌍 이벤트가 발생하지 않는 경우를 확인하는 데 사용합니다.  
  
-   **ring_buffer**. FIFO(선입선출) 또는 이벤트별 FIFO 방식으로 메모리에 이벤트 데이터를 저장하는 데 사용합니다.  
  
#### <a name="to-configure-global-fields-for-a-session"></a>세션에 대한 전역 필드를 구성하려면  
  
1.  **이벤트** 페이지에서 이벤트 세션에 추가할 이벤트를 선택하고 **구성**을 클릭합니다.  
  
     **구성**을 클릭하면 **이벤트 라이브러리** 섹션이 축소되고 **선택한 이벤트** 섹션이 페이지의 왼쪽으로 슬라이딩(sliding)됩니다. 이벤트를 구성하는 데 사용하는 **이벤트 구성 옵션** 섹션은 페이지의 오른쪽에 나타납니다. 이 페이지의 탭을 사용하여 이벤트 세션에 대한 동작을 구성합니다.  
  
2.  **전역 필드** 탭에서 선택한 이벤트에 적용할 필드를 선택합니다.  
  
     각 이벤트에 대해 여러 필드를 선택할 수 있습니다.  
  
    > [!NOTE]  
    >  이미 선택한 두 개의 이벤트에 구성된 동작이 서로 다른 경우 확장 이벤트는 부분적으로 확인된 동작을 표시합니다. 사용하도록 설정한 동작을 빠르게 찾으려면 확인란 위의 열 머리글을 클릭하여 사용/사용 안 함 상태를 기준으로 정렬합니다.  
  
3.  **필터** 탭에서 조건자라고도 하는 필터를 적용하여 캡처할 이벤트를 제한합니다.  
  
     선택한 이벤트에 필터가 적용되면 열에 확인 표시가 나타납니다.  
  
    > [!NOTE]  
    >  Ctrl 또는 Shift 키를 사용하여 필터를 적용할 이벤트를 여러 개 선택할 수 있습니다. 그러나 구성할 때는 일반적인 이벤트 필드만 나타납니다. 선택한 두 개의 이벤트에 이미 서로 다른 필터가 구성되어 있는 경우에는 필터가 나타나지 않습니다. 필터를 다시 구성하면 기존 필터 값을 덮어쓰게 됩니다.  
  
    > [!NOTE]  
    >  필터에 대한 그룹 절을 구성한 경우 결과를 저장하면 중복 괄호가 필터에서 제거됩니다. 예를 들어 필터 그룹 **Clause 1** 및 **Clause 2**를 만든 경우 절 주위에 괄호가 나타납니다. 필터를 저장하면 중복 괄호가 제거됩니다. 괄호가 제거되어도 필터 논리에는 영향이 없습니다.  
  
4.  **이벤트 필드** 탭에서 선택한 이벤트에 적용할 이벤트 필드를 선택합니다.  
  
     이벤트에는 항상 수집되는 여러 필드가 포함됩니다. 이러한 필드는 **이벤트 필드** 탭에 확인란 없이 표시됩니다. 이벤트에는 기본적으로 수집되지 않는 선택적 필드가 포함될 수도 있습니다. 예를 들어 비용이 많이 드는 선택적 필드는 선택되지 않습니다. 또한 선택적 필드는 **이벤트 필드** 탭에 확인란과 함께 나열됩니다. 선택적 필드를 수집하려면 선택적 필드 앞에 있는 확인란을 선택합니다.  
  
    > [!NOTE]  
    >  이벤트 필드 옵션에는 캡처되어 추적 결과에 나타날 필드가 표시됩니다. 확장 이벤트에는 이벤트 필드의 데이터 형식만 표시됩니다. 예를 들어 읽기 전용 이벤트 필드는 표시되지 않습니다. 두 개 이상의 이벤트를 선택하면 새 세션 대화 상자의 **이벤트 필드** 탭이 비어 있게 됩니다.  
  
5.  이벤트 세션에 대상을 추가하려면 **페이지 선택** 섹션에서 **데이터 저장소**를 선택합니다.  
  
    > [!NOTE]  
    >  이벤트 세션 만들기를 완료할 때까지 **확인** 을 클릭하지 마세요.  
  
#### <a name="to-add-targets-to-an-event-session"></a>이벤트 세션에 대상을 추가하려면  
  
1.  새 세션 대화 상자의 **페이지 선택** 섹션에서 **데이터 저장소**를 선택합니다.  
  
2.  **데이터 저장소** 페이지의 드롭다운 목록에서 대상 유형을 선택합니다.  
  
     대상 유형을 선택하면 대상 설명이 표시됩니다. 한 번에 하나의 대상만 추가할 수 있습니다. 세션에 대상을 이미 추가한 경우 해당 대상은 드롭다운 목록에 나타나지 않습니다.  
  
3.  **추가** 를 클릭하여 이벤트 세션의 대상을 추가합니다. 대상을 제거하려면 **제거**를 클릭합니다.  
  
     대상 속성은 선택하는 대상에 따라 **대상** 섹션에 나타납니다.  
  
4.  선택하는 대상에 따라 지정할 수 있는 속성은 다음과 같습니다.  
  
    |대상|대상 속성|  
    |------------|-----------------------|  
    |**etw_classic_sync_target**|**서버의 세션 로그 파일 이름**: 서버의 로그 파일 이름 및 디렉터리를 입력하거나, **찾아보기** 를 클릭하여 로그 파일을 찾아 선택합니다.<br /><br /> **최대 로그 파일 크기**: ETW(Windows용 이벤트 추적) 이벤트의 최대 로그 파일 크기를 입력합니다. 기본값은 20MB입니다. 드롭다운 목록에서 다른 저장 단위를 선택할 수 있습니다.<br /><br /> **버퍼 크기**: 이벤트 세션의 메모리 내 버퍼 크기를 입력합니다. 기본값은 128KB입니다. 드롭다운 목록에서 다른 저장 단위를 선택할 수 있습니다.<br /><br /> **세션 이름**: 의미 있는 ETW 세션 이름을 입력합니다.<br /><br /> **ETW에 쓰기 오류 시 다시 시도**: ETW 하위 시스템에 이벤트 게시를 다시 시도하려면 이 확인란을 선택합니다.<br /><br /> **최대 다시 시도 횟수**: 이벤트를 삭제하기 전에 ETW 하위 시스템에 이벤트 게시를 다시 시도할 최대 횟수를 입력합니다. 기본 다시 시도 횟수는 0입니다. 이 대상 속성의 경우 0은 다시 시도하지 않음을 의미합니다.|  
    |**event_counter**|이벤트 카운터에 대한 대상 속성은 없습니다.|  
    |**event_file**|**서버의 파일 이름**: 서버의 디렉터리 및 대상 파일 이름을 입력하거나, **찾아보기** 를 클릭하여 대상 파일을 찾아 선택합니다.<br /><br /> **최대 파일 크기**: 파일 대상의 최대 파일 크기를 지정합니다. 최대 파일 크기를 지정하지 않으면 디스크가 가득 찰 때까지 파일 크기가 계속 커집니다. 기본 파일 크기는 1GB입니다. 드롭다운 목록에서 다른 저장 단위를 선택할 수 있습니다.<br /><br /> **파일 롤오버 사용**: 파일 대상에 대해 파일 롤오버를 사용하도록 설정하려면 이 확인란을 선택합니다.<br /><br /> **최대 파일 수**: 파일 시스템에 보관할 최대 파일 수를 입력합니다.|  
    |**히스토그램**|**필터링할 이벤트**: 드롭다운 목록에서 필터링할 이벤트를 선택합니다. 이벤트 세션에 있는 모든 이벤트를 필터링할 수 있습니다. 선택할 수도 있습니다  **\<없음 >** 모든 이벤트와 동작의 기준 버킷을 포함할 드롭 다운 목록에서.<br /><br /> **버킷 기준: 동작** 데이터 원본으로 사용되는 동작 이름을 버킷의 기준으로 하려면 이 옵션을 선택한 다음 드롭다운 목록에서 동작을 선택합니다.<br /><br /> **버킷 기준: 필드** 데이터 원본으로 사용되는 이벤트 필드를 버킷의 기준으로 하려면 이 옵션을 선택한 다음 드롭다운 목록에서 필드를 선택합니다.<br /><br /> **최대 버킷 수**: 보관할 최대 버킷 수를 입력합니다. 이 값에 도달하면 이벤트 세션에서 기존 버킷에 속하지 않는 새 이벤트는 무시됩니다.|  
    |**pair_matching**|**이벤트: 시작** 드롭다운 목록에서 쌍을 이루는 시퀀스의 시작 이벤트를 지정하는 이벤트 이름을 선택합니다.<br /><br /> **이벤트: 종료** 드롭다운 목록에서 쌍을 이루는 시퀀스의 종료 이벤트를 지정하는 이벤트 이름을 선택합니다.<br /><br /> **필드 및 동작: 시작**. 드롭다운 목록에서 쌍을 이루는 시퀀스의 시작 필드 및/또는 동작을 선택합니다.<br /><br /> **필드 및 동작: 종료**. 드롭다운 목록에서 쌍을 이루는 시퀀스의 종료 필드 및/또는 동작을 선택합니다.<br /><br /> **메모리 부족 시 쌍을 이루지 않는 새 이벤트 삭제**: 컴퓨터의 메모리가 부족할 때 pair_matching 대상에 대한 이벤트 수집을 중지하려면 이 확인란을 선택합니다. 메모리 부족이 해결되면 이벤트 수집이 다시 시작됩니다.<br /><br /> **최대 고아 이벤트**: 메모리에 유지할 최대 고아 이벤트 수를 지정합니다.|  
    |**ring_buffer**|**유지할 이벤트 수**: 위쪽 및 아래쪽 화살표를 사용하여 유지할 이벤트 수를 지정합니다. 기본값은 1000입니다.<br /><br /> **최대 버퍼 메모리 크기**: 사용할 최대 메모리 크기를 입력합니다. 이 값에 도달하면 기존 이벤트가 삭제됩니다. 기본 메모리 크기는 0MB입니다. 이는 제한이 없음을 의미합니다. 드롭다운 목록에서 다른 저장 단위를 선택할 수 있습니다.<br /><br /> **버퍼가 꽉 차면 유형당 지정한 개수의 이벤트 유지**: 버퍼에 각 유형의 이벤트를 지정된 수로 유지하려면 이 옵션을 선택합니다.<br /><br /> **유형당 유지할 이벤트 수**: 버퍼에 유지할 각 유형의 기본 설정 이벤트 수를 입력합니다.|  
  
5.  고급 구성 속성을 설정하려면 **페이지 선택** 섹션에서 **고급** 을 선택합니다.  
  
    > [!NOTE]  
    >  이벤트 세션 만들기를 완료할 때까지 **확인** 을 클릭하지 마세요.  
  
#### <a name="to-set-advanced-configurations"></a>고급 구성을 설정하려면  
  
1.  새 세션 대화 상자의 **페이지 선택** 섹션에서 **고급**을 선택합니다.  
  
2.  **고급** 페이지에서 다음 작업을 수행하여 이벤트 세션에 대한 **이벤트 보존 모드** 옵션을 지정합니다.  
  
    1.  **단일 이벤트 손실**: 단일 이벤트의 손실을 허용하려면 이 옵션을 선택합니다.  
  
    2.  **여러 이벤트 손실**: 여러 이벤트의 손실을 허용하려면 이 옵션을 선택합니다.  
  
    3.  **이벤트 손실 없음**: 이벤트 손실을 방지하려면 이 옵션을 선택합니다. 이 옵션은 선택하지 않는 것이 좋습니다.  
  
        > [!NOTE]  
        >  **sqlos.wait_info** 이벤트와 같은 일부 이벤트는 **이벤트 손실 없음** 이벤트 보존 모드와 호환되지 않습니다.  
  
3.  이벤트 세션에 대한 **최대 디스패치 대기 시간** 옵션을 지정하려면 다음 작업을 수행합니다.  
  
    1.  **초**: 최대 디스패치 대기 시간을 늘리거나 줄이려면 이 옵션을 선택합니다. 위쪽 및 아래쪽 화살표를 사용하여 최대 디스패치 대기 시간을 초 단위로 지정합니다.  
  
    2.  **제한 없음**: 버퍼가 가득 찬 경우에만 이벤트를 디스패치하려면 이 옵션을 선택합니다.  
  
4.  **최대 메모리 크기** 상자에 최대 메모리 크기를 입력합니다. 이 값에 도달하면 기존 이벤트가 삭제됩니다. 드롭다운 목록에서 다른 저장 단위를 선택할 수 있습니다.  
  
5.  **최대 메모리 크기** 에 포함하기에는 너무 큰 이벤트를 저장하기 위한 최대 이벤트 크기를 **최대 이벤트 크기**상자에 입력합니다. 매우 큰 이벤트를 수집하지 않는 경우에는 이 옵션을 구성할 필요가 없습니다. 드롭다운 목록에서 다른 저장 단위를 선택할 수 있습니다.  
  
6.  이벤트 세션에 대한 **메모리 파티션 모드** 옵션을 지정하려면 다음 작업을 수행합니다.  
  
    1.  **없음**. 메모리 파티션 모드를 지정하지 않으려면 이 옵션을 선택합니다.  
  
    2.  **노드당**: 노드별로 메모리를 파티션하려면 이 옵션을 선택합니다.  
  
    3.  **CPU당**: CPU별로 메모리를 파티션하려면 이 옵션을 선택합니다.  
  
 이전 세션 속성의 구성 기본값을 복원하려면 **기본값 복원**을 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [쿼리 편집기를 사용 하 여 확장된 이벤트 세션 만들기](../../2014/database-engine/create-an-extended-events-session-using-query-editor.md)   
 [마법사를 사용 하 여 확장된 이벤트 세션 만들기 &#40;개체 탐색기&#41;](../ssms/object/object-explorer.md)   
 [확장 이벤트 세션 스크립팅](../../2014/database-engine/script-an-extended-event-session.md)  
  
  
