---
title: 메모리 액세스에 최적화된 파일 그룹 | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 14106cc9-816b-493a-bcb9-fe66a1cd4630
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cd1a637bdf40202e5c8a973be8f4ae68f415cde8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076565"
---
# <a name="the-memory-optimized-filegroup"></a>메모리 액세스에 최적화된 파일 그룹
  메모리 최적화 테이블을 만들려면 먼저 메모리 최적화 파일 그룹을 만들어야 합니다. 메모리 최적화 파일 그룹에는 컨테이너가 하나 이상 포함되어 있고, 각 컨테이너에는 데이터 파일이나 델타 파일, 또는 둘 다 포함되어 있습니다.  
  
 SCHEMA_ONLY 테이블의 데이터 행이 유지되지 않고 메모리 최적화 테이블의 메타데이터와 고유하게 컴파일된 저장 프로시저가 기존 카탈로그에 저장되지만 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 엔진에는 메모리 최적화 테이블이 있는 데이터베이스에 대한 균일한 환경을 제공하기 위해 SCHEMA_ONLY 메모리 최적화 테이블에 대해 메모리 최적화 파일 그룹이 여전히 필요합니다.  
  
 메모리 최적화 파일 그룹은 다음과 같은 차이를 두고 파일 스트림 파일 그룹을 기반으로 합니다.  
  
-   데이터베이스당 하나의 메모리 최적화 파일 그룹만 만들 수 있습니다. 파일 그룹을 포함된 memory_optimized_data로 명시적으로 표시해야 합니다. 데이터베이스를 만들 때 파일 그룹을 만들거나 나중에 추가할 수 있습니다.  
  
    ```  
    ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA  
    ```  
  
-   MEMORY_OPTIMIZED_DATA 파일 그룹에 하나 이상의 컨테이너를 추가해야 합니다. 이는 아래와 같이 함수의 반환값을 데이터 프레임으로 바로 변환하는 데 사용할 수 있음을 나타냅니다.  
  
    ```  
    ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod  
    ```  
  
-   메모리 최적화 파일 그룹을 만들기 위해 파일 스트림을 사용할 필요가 없습니다([FILESTREAM 사용 및 구성](../blob/enable-and-configure-filestream.md)). 파일 스트림에 대한 매핑을 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 엔진이 수행합니다.  
  
-   새 컨테이너를 메모리 최적화 파일 그룹에 추가할 수 있습니다. 메모리 최적화 내구성이 있는 테이블에 필요한 저장소를 확장하고 여러 컨테이너 간에 IO를 분산하기 위해 새 컨테이너가 필요할 수 있습니다.  
  
-   메모리 최적화 파일 그룹이 포함된 데이터 이동은 AlwaysOn 가용성 그룹 구성에 최적화되어 있습니다. 보조 복제본에 전송되는 파일 스트림 파일과는 달리 메모리 최적화 파일 그룹 내에 있는 검사점 파일(데이터 및 델타)은 보조 복제본에 전송되지 않습니다. 보조 복제본에서 트랜잭션 로그를 사용하여 데이터 및 델타 파일이 생성됩니다.  
  
 다음은 메모리 최적화 파일 그룹의 제한 사항입니다.  
  
-   메모리 최적화 파일 그룹을 만들었으면 데이터베이스를 삭제하는 방식으로만 제거할 수 있습니다. 프로덕션 환경에서 메모리 최적화 파일 그룹을 제거하지 않아도 됩니다.  
  
-   비어 있지 않은 컨테이너를 제거하거나 데이터 및 델타 파일 쌍을 메모리 최적화 파일 그룹의 다른 컨테이너로 이동할 수 없습니다.  
  
-   컨테이너에 MAXSIZE를 지정할 수 없습니다.  
  
## <a name="configuring-a-memory-optimized-filegroup"></a>메모리 액세스에 최적화된 파일 그룹 구성  
 메모리 최적화 파일 그룹에 여러 컨테이너를 만들고 다른 드라이브에 분산하여 메모리에 데이터를 스트리밍하는 더 많은 대역폭을 얻어야 합니다.  
  
 저장소를 구성할 때 메모리 최적화 내구성이 있는 테이블 크기의 4배 정도의 여유 디스크 공간을 제공해야 합니다. IO 하위 시스템이 작업에 필요한 IOPS를 지원하는지 확인해야 합니다. 제공된 IOPS에 데이터 및 델타 파일 쌍이 채워지는 경우 저장 및 병합 작업 계정에 대한 IOPS의 3배가 필요합니다. 메모리 최적화 파일 그룹에 하나 이상의 컨테이너를 추가하여 저장소 용량 및 IOPS를 추가할 수 있습니다.  
  
 여러 컨테이너에서 여러 드라이브 시나리오, 데이터 및 델타 파일이 라운드 로빈 방식으로 컨테이너에 할당됩니다. 첫 번째 데이터 파일이 첫 번째 컨테이너에서 할당되고 델타 파일이 다음 컨테이너에서 할당되고 이러한 할당 방식이 반복됩니다. 홀수 개수의 드라이브가 있고 각각이 한 컨테이너에 매핑된 경우 이러한 할당 체계가 데이터 및 델타 파일을 컨테이너에 동등하게 배포합니다. 그러나 짝수 개수의 드라이브가 있고 각각이 컨테이너에 매핑된 경우 홀수 개 드라이브에 매핑된 데이터 파일과 짝수 개 드라이브에 매핑된 델타 파일 저장소가 불균형을 이룰 수 있습니다. 복구 시 균형된 IO 스트림을 얻으려면 아래 예에 명시된 대로 데이터 및 델타 파일 쌍을 같은 스핀들/저장소에 두세요.  
  
 **예:** 두 컨테이너를 사용 하 여 메모리 최적화 파일 그룹을는 것이 좋습니다: 드라이브 X와 Y 드라이브에서 컨테이너 2에 1 컨테이너입니다. 데이터 및 델타 파일 할당이 라운드 로빈 방식으로 수행 됩니다, 되므로 컨테이너 1에만 데이터 파일 수 있고 컨테이너 2는만 델타 파일을 데이터 파일로 초당 입/출력 작업 뿐만 아니라 저장소에 불균형 상태 지 속성에 델타 파일 보다 훨씬 큽니다. 데이터 및 델타 파일이 드라이브 X와 Y 균일 하 게 배포 하려면 두 개가 아닌 4 개의 컨테이너가 만들고 처음 두 컨테이너를 드라이브 X 및 다음 두 컨테이너를 드라이브 Y에 매핑하십시오. 라운드 로빈 할당을 사용 하 여 첫 번째 데이터 및 델타 파일을 첫 번째 할당할 컨테이너 1과 컨테이너-2에서 각각 드라이브 X에 매핑되는 합니다. 마찬가지로, 다음 데이터 및 델타 파일은 컨테이너-3과 드라이브 Y에 매핑된 컨테이너-4에서 할당 됩니다. 이 두 드라이브 간에 데이터 및 델타 파일을 균일 하 게 배포할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [메모리 액세스에 최적화된 개체의 저장소 만들기 및 관리](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
