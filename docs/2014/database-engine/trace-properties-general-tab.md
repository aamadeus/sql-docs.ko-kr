---
title: 추적 속성 (일반 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.pro.traceproperties.general.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: 25227268-143b-477e-aac9-8268bcaf2078
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8d92a51eaca0f98624ea6174a56448b383c1744a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36185668"
---
# <a name="trace-properties-general-tab"></a>추적 속성(일반 탭)
  **추적 속성** 대화 상자의 **일반** 탭을 사용하여 추적의 속성을 확인하거나 지정할 수 있습니다.  
  
## <a name="options"></a>변수  
 **추적 이름**  
 추적 이름을 지정합니다.  
  
 **추적 공급자 이름**  
 추적되는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스의 이름을 표시합니다. 이 필드에는 연결할 때 지정한 서버의 이름이 자동으로 채워집니다. 추적 공급자의 이름을 변경하려면 **취소** 를 클릭하여 대화 상자를 닫은 다음 새 추적을 시작합니다.  
  
 **추적 공급자 유형**  
 추적을 제공하는 서버 유형을 표시합니다. **추적 공급자 유형** 필드는 추적 정의 파일에 의해 자동으로 채워집니다. 이 필드는 수정할 수 없습니다.  
  
 **version**  
 추적을 제공하는 서버 버전을 표시합니다. **버전** 필드는 추적 정의 파일에 의해 자동으로 채워집니다. 이 필드는 수정할 수 없습니다.  
  
 **템플릿 사용**  
 템플릿 디렉터리에서 템플릿을 선택합니다. 이 디렉터리에는 기본 템플릿 및 현재 추적 공급자 유형을 위해 만들어진 사용자 정의 템플릿이 있습니다.  
  
 **파일에 저장**  
 추적 데이터를 .trc 파일에 캡처합니다. 추적 데이터를 저장하면 나중에 검토 및 분석 작업에 유용합니다.  
  
 **최대 파일 크기 설정(MB)**  
 추적 데이터를 파일에 저장하려면 추적 파일의 최대 크기를 지정해야 합니다. 기본값은 5MB입니다. 최대 크기는 파일이 저장된 파일 시스템이 NTFS인지 FAT인지에 따라 달라집니다.  
  
 \<그래픽 > **다른 이름으로 저장**  
 파일을 저장하려고 선택한 후에는 이 아이콘을 선택하여 파일 이름을 변경할 수 있습니다.  
  
 **파일 롤오버 사용**  
 최대 파일 크기에 도달했을 때 추적 데이터를 보관할 추가 파일을 만들려면 선택합니다. 각각의 새 파일 이름에는 원래의 .trc 파일 이름 뒤에 순서대로 번호가 매겨집니다. 예를 들어 최대 파일 크기에 도달하면 **NewTrace.trc** 가 닫히고 **NewTrace_1.trc**, **NewTrace_2.trc**등의 새 파일이 순서대로 열립니다. 추적 내용을 파일에 저장하면 파일 롤오버 옵션이 기본적으로 선택됩니다.  
  
 **서버에서 추적 데이터 처리**  
 추적을 실행하는 서버가 추적 데이터를 처리하도록 지정합니다. 이 옵션을 사용하면 추적으로 인해 발생하는 성능 오버헤드를 줄일 수 있습니다. 이 확인란을 선택하면 스트레스 상태에서도 모든 이벤트가 추적됩니다. 이 확인란의 선택을 취소하면 SQL Server 프로파일러가 처리를 수행하게 되고 스트레스 상태에서 몇몇 이벤트는 추적되지 않을 수 있습니다.  
  
 **테이블에 저장**  
 추적 데이터를 데이터베이스 테이블에 캡처합니다. 추적 데이터를 저장하면 나중에 검토 및 분석 작업에 유용합니다. 추적 데이터를 테이블에 저장하면 추적이 저장될 서버에 상당한 오버헤드가 발생할 수 있습니다. 가능하면 추적되는 서버에 추적 테이블을 저장하지 않도록 합니다.  
  
 \<그래픽 > **대상 테이블**  
 추적 데이터를 데이터베이스 테이블에 저장하도록 선택한 후에는 이 아이콘을 선택하여 테이블 이름을 변경할 수 있습니다.  
  
 **최대 행 수 설정(천 단위)**  
 데이터를 저장할 행의 최대 개수를 지정합니다. 기본값은 1000입니다.  
  
 **추적 중지 시간 설정**  
 추적을 끝내고 닫을 날짜와 시간을 설정합니다.  
  
## <a name="see-also"></a>관련 항목  
 [추적 만들기&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  