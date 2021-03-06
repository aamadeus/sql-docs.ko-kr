---
title: 리소스 관리자 리소스 풀 | Microsoft 문서
ms.custom: ''
ms.date: 10/20/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool
- resource pool [SQL Server], overview
- resource pool [SQL Server]
ms.assetid: 306b6278-e54f-42e6-b746-95a9315e0cbe
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e53c61ed06282553be01d383753b8a45db56de8b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47624891"
---
# <a name="resource-governor-resource-pool"></a>리소스 관리자 리소스 풀
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스 관리자에서 리소스 풀은 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스의 물리적 리소스의 하위 집합을 나타냅니다. 리소스 관리자를 사용하면 들어오는 응용 프로그램 요청이 리소스 풀에서 사용할 수 있는 CPU, 물리적 IO 및 메모리 양을 제한할 수 있습니다. 각 리소스 풀에는 하나 이상의 작업 그룹이 포함될 수 있습니다. 세션이 시작되면 리소스 관리자 분류자가 세션을 특정 작업 그룹에 할당하고 세션은 작업 그룹에 할당된 리소스를 사용하여 실행해야 합니다.  
  
## <a name="resource-pool-concepts"></a>리소스 풀 개념  
 리소스 풀 또는 풀은 서버의 물리적 리소스를 나타냅니다. 풀은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 내부의 가상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴트로 간주할 수 있습니다. 풀은 두 부분으로 구성되어 있는데, 최소 리소스 예약을 사용하는 한 부분은 다른 풀과 겹치지 않고 가능한 최대 리소스 소비를 지원하는 다른 한 부분은 다른 풀과 공유됩니다. 각 리소스(CPU, 메모리, 물리적 IO)에 대해 다음 설정 중 하나 이상을 지정하여 풀 리소스를 정의합니다.  
  
-   **MIN_CPU_PERCENT 및 MAX_CPU_PERCENT**  
  
     이 설정은 CPU 경합이 있을 때 리소스 풀의 모든 요청에 대해 보장되는 최소 및 최대 평균 CPU 대역폭입니다. 이 설정을 사용하면 각 작업의 요구 사항을 기준으로 여러 작업에 대해 예측 가능한 CPU 리소스 사용량을 설정할 수 있습니다. 예를 들어 회사의 영업부와 마케팅 부서가 동일한 데이터베이스를 공유한다고 가정해 보겠습니다. 영업부에는 우선 순위가 높은 쿼리를 사용하는 CPU 집약적 작업이 있습니다. 마케팅 부서에도 CPU 집약적 작업이 있지만 쿼리 우선 순위가 더 낮습니다. 이 경우 두 부서에 대해 별도의 리소스 풀을 만든 후 영업부 리소스 풀은 *최소* CPU 비율을 70으로 지정하고 마케팅 부서 리소스 풀은 *최대* CPU 비율을 30%로 지정할 수 있습니다. 이렇게 하면 영업부 작업은 필요한 CPU 리소스를 받을 수 있고 마케팅 부서 작업은 영업부 작업의 CPU 수요와 격리됩니다. 최대 CPU 비율은 편의적 최대값입니다. 사용 가능한 CPU 용량이 있으면 100% 모두 작업에 사용됩니다. 즉, CPU 리소스 경합이 있을 때만 최대값이 적용됩니다. 이 예에서는 필요한 경우 영업부 작업이 차단되고 마케팅 부서 작업에 CPU의 100%가 모두 사용될 수 있습니다.  
  
-   **CAP_CPU_PERCENT**  
  
     이 설정은 리소스 풀의 모든 요청에 대한 CPU 대역폭 하드 상한입니다. 풀에 연결된 작업이 CPU_CPU_PERCENT 값보다 큰 값이 아닌 MAX_CPU_PERCENT 값보다 큰 CPU 용량(사용 가능한 경우)을 사용할 수 있습니다. 위의 예로 돌아가, 마케팅 부서가 리소스 사용 비용을 환불 받는다고 가정해 보겠습니다. 마케팅 부서는 예측 가능한 요금 청구를 원하며 30% 이상의 CPU에 대해서는 비용을 지불하지 않고자 합니다. 이 경우 마케팅 리소스 풀에 대해 CAP_CPU_PERCENT를 30으로 설정하면 됩니다.  
  
-   **MIN_MEMORY_PERCENT 및 MAX_MEMORY_PERCENT**  
  
     이 설정은 리소스 풀에 예약된 최소 및 최대 메모리 양이며 다른 리소스 풀과 공유될 수 없습니다. 이때 참조되는 메모리는 버퍼 풀 메모리(예: 데이터 및 인덱스 페이지)가 아니라 쿼리 실행 부여 메모리입니다. 풀의 최소 메모리 값을 설정하면 해당 리소스 풀에서 실행될 수 있는 모든 요청에 대해 지정한 비율만큼의 메모리가 사용되도록 보장할 수 있습니다. 이는 이 설정을 MIN_CPU_PERCENT와 구별하는 중요한 요소인데, 이 경우 지정된 리소스 풀에 해당 풀에 속한 작업 그룹의 요청이 없을 때에도 풀에 메모리가 남아 있을 수 있기 때문입니다. 활성 요청이 없는 경우에도 남아 있는 메모리를 다른 풀에서 사용할 수 없기 때문에 이 설정을 사용할 때는 신중을 기해야 합니다. 풀의 최대 메모리 값 설정은 풀에서 요청이 실행될 때 전체 메모리 중 이 비율 이상은 사용할 수 없음을 의미합니다.  
  
-   **AFFINITY**  
  
     이 설정을 사용하면 하나 이상의 스케줄러 또는 NUMA 노드에 대해 리소스 풀의 선호도를 설정하여 CPU 리소스를 더 효과적으로 격리할 수 있습니다. 위의 영업부 및 마케팅 부서 시나리오로 돌아가, 영업부에 더 격리된 환경이 필요하며 항상 CPU 코어의 100%를 사용하려 한다고 가정해 보겠습니다. AFFINITY 옵션을 사용하면 영업부 작업과 마케팅 부서 작업을 서로 다른 CPU에 예약할 수 있습니다. 마케팅 풀에 대한 CAP_CPU_PERCENT가 설정되어 있다고 가정할 경우 마케팅 부서 작업에는 계속 한 코어의 최대 30%가 사용되지만 영업부 작업에는 다른 코어의 100%가 사용됩니다. 영업부 작업과 마케팅 부서 작업이 관련이 있는 한 두 작업은 격리된 두 시스템에서 실행됩니다.  
  
-   **MIN_IOPS_PER_VOLUME 및 MAX_IOPS_PER_VOLUME**  
  
     이 설정은 리소스 풀에 대한 디스크 볼륨당 최소 및 최대 물리적 IOPS(초당 I/O 작업)입니다. 이 설정을 사용하면 지정된 리소스 풀의 사용자 스레드에 대해 발생하는 물리적 IO를 제어할 수 있습니다. 예를 들어 영업부는 몇 가지 월말 보고서를 큰 규모의 일괄 처리로 생성합니다. 이러한 일괄 처리의 쿼리는 디스크 볼륨을 포화시키고 데이터베이스에서 우선 순위가 높은 다른 작업의 성능에 영향을 줄 수 있는 IO를 생성할 수 있습니다. 이 작업을 격리하기 위해 영업부 리소스 풀의 MIN_IOPS_PER_VOLUME을 20으로 설정하고 MAX_IOPS_PER_VOLUME을 100으로 설정하여 작업에 대해 발생할 수 있는 IO 수준을 제어할 수 있습니다.  
  
CPU 또는 메모리를 구성할 때 모든 풀의 MIN 값의 합은 서버 리소스의 100%를 초과할 수 없습니다. 또한 CPU 또는 메모리를 구성할 때 MAX 및 CAP 값은 MIN과 100%(포함) 사이의 임의 값으로 설정할 수 있습니다.  
  
풀에 0이 아닌 MIN이 정의되어 있으면 다른 풀의 유효한 MAX 값이 다시 조정됩니다. 다른 풀의 MIN 값 합계와 풀의 구성된 MAX 값의 최소값을 100%에서 뺍니다.  
  
다음 표에서는 위의 몇 가지 개념에 대해 설명하고 내부 풀, 기본 풀 및 사용자 정의 풀 두 개에 대한 설정을 보여 줍니다. 
  
|풀 이름|MIN % 설정|MAX % 설정|계산된 유효한 MAX %|계산된 공유 %|설명|  
|---------------|-------------------|-------------------|--------------------------------|-------------------------|-------------|  
|내부|0|100|100|0|유효 MAX % 및 공유 %는 내부 풀에 적용할 수 없습니다.|  
|기본|0|100|30|30|유효 MAX 값은 min(100,100-(20+50)) = 30으로 계산됩니다. 계산된 공유 백분율(%)은 유효 MAX - MIN = 30입니다.|  
|풀 1|20|100|50|30|유효 MAX 값은 min(100,100-50) = 50으로 계산됩니다. 계산된 공유 백분율(%)은 유효 MAX - MIN = 30입니다.|  
|풀 2|50|70|70|20|유효 MAX 값은 min(70,100-20) = 70으로 계산됩니다. 계산된 공유 백분율(%)은 유효 MAX - MIN = 20입니다.|  
다음 공식은 위의 표에서 유효한 MAX % 및 공유 %를 계산하는 데 사용됩니다.  
  
-   Min(X,Y)은 X와 Y 중에서 더 작은 값을 의미합니다.  
  
-   Sum(X)은 모든 풀에서 X 값의 합계를 의미합니다.  
  
-   총 공유 % = 100 - sum(MIN %)  
  
-   유효한 MAX % = min(X,Y)  
  
-   공유 % = 유효한 MAX % - MIN %  

위의 표를 계속 사용하여 다른 풀이 만들어질 때 발생하는 조정 작업을 보다 자세히 설명할 수 있습니다. 이 풀은 풀 3이며 MIN %가 5로 설정되어 있습니다.  
  
|풀 이름|MIN % 설정|MAX % 설정|계산된 유효한 MAX %|계산된 공유 %|설명|  
|---------------|-------------------|-------------------|--------------------------------|-------------------------|-------------|  
|내부|0|100|100|0|유효 MAX % 및 공유 %는 내부 풀에 적용할 수 없습니다.|  
|기본|0|100|25|25|유효 MAX 값은 min(100,100-(20+50+5)) = 25로 계산됩니다. 계산된 공유 백분율(%)은 유효 MAX - MIN = 25입니다.|  
|풀 1|20|100|45|25|유효 MAX 값은 min(100,100-55) = 45로 계산됩니다. 계산된 공유 백분율(%)은 유효 MAX - MIN = 25입니다.|  
|풀 2|50|70|70|20|유효 MAX 값은 min(70,100-25) = 70으로 계산됩니다. 계산된 공유 백분율(%)은 유효 MAX - MIN = 20입니다.|  
|풀 3|5|100|30|25|유효 MAX 값은 min(100,100-70) = 30으로 계산됩니다. 계산된 공유 백분율(%)은 유효 MAX - MIN = 25입니다.|  
  
 풀의 공유 부분은 리소스가 사용 가능한 경우 사용 가능한 리소스가 이동할 수 있는 위치를 나타내는 데 사용됩니다. 그러나 사용된 리소스는 지정된 풀로 이동하지만 공유되지는 않습니다. 따라서 지정된 풀에 요청이 없고 이 풀에 구성된 리소스를 다른 풀에 사용할 수 있는 경우 리소스 활용도가 높아질 수 있습니다.  
  
 다음은 몇 가지 극단적인 풀 구성 사례입니다.  
  
-   모든 풀은 서버 리소스의 100%를 나타내는 최소값을 정의합니다. 이 경우 유효한 최대값은 최소값과 같습니다. 이것은 지정된 풀 내부에서 리소스가 소비되는지 여부에 관계없이 서버 리소스를 겹치지 않는 부분으로 분할하는 것과 같습니다.  
  
-   모든 풀은 최소값으로 0을 갖습니다. 모든 풀은 사용 가능한 리소스를 서로 차지하기 위해 경쟁하며 최종 크기가 각 풀의 리소스 소비에 따라 결정됩니다. 정책과 같은 다른 요소는 최종 풀 크기를 구체화하는 데 사용됩니다.  
  
리소스 관리자는 두 개의 리소스 풀, 내부 풀과 기본 풀을 미리 정의합니다. 하지만 풀을 추가할 수도 있습니다.  
  
**내부 풀**  
  
내부 풀은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 자체에서 소비한 리소스를 나타냅니다. 이 풀은 항상 내부 그룹만 포함하며 어떤 식으로든 변경할 수 없습니다. 내부 풀에서는 리소스를 제한 없이 소비할 수 있습니다. 풀의 모든 작업은 서버가 작동하는 데 있어서 중요한 것으로 간주되며, 리소스 관리자를 사용하면 다른 풀에 설정된 제한을 위반하더라도 다른 풀의 리소스를 내부 풀에 사용할 수 있습니다.  
  
> [!NOTE]  
>  내부 풀 및 내부 그룹 리소스 사용량은 전체 리소스 사용량에서 차감되지 않습니다. 백분율은 사용 가능한 전체 리소스를 기준으로 계산됩니다.  
  
**기본 풀**  
  
기본 풀은 미리 정의된 첫 번째 사용자 풀입니다. 구성에 관계없이 기본 풀은 기본 그룹만 포함합니다. 기본 풀은 만들거나 삭제할 수는 없지만 변경할 수는 있습니다. 기본 풀은 기본 그룹 외에 사용자 정의 그룹을 포함할 수 있습니다. [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (으)로 시작하면 루틴 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 작업에 대한 기본 리소스 및 R 스크립트 실행과 같은 외부 프로세스에 대한 기본 외부 리소스 풀이 있습니다.  
  
> [!NOTE]  
>  기본 그룹은 변경할 수는 있지만 기본 풀 밖으로 이동할 수는 없습니다.  
  
**외부 풀**  
  
사용자는 외부 풀을 정의하여 외부 프로세스에 대한 리소스를 정의할 수 있습니다. R 서비스의 경우 이는 특히 `rterm.exe`, `BxlServer.exe` 및 생성된 다른 프로세스를 관리합니다.  
  
**사용자 정의 리소스 풀**  
  
사용자 정의 리소스 풀은 환경의 특정 작업에 대해 만드는 풀입니다. 리소스 관리자는 리소스 풀을 생성, 변경, 삭제하는 DDL 문을 제공합니다.  
  
## <a name="resource-pool-tasks"></a>리소스 풀 태스크  
  
|태스크 설명|항목|  
|----------------------|-----------|  
|리소스 풀을 만드는 방법에 대해 설명합니다.|[리소스 풀 만들기](../../relational-databases/resource-governor/create-a-resource-pool.md)|  
|리소스 풀 설정을 변경하는 방법에 대해 설명합니다.|[리소스 풀 설정 변경](../../relational-databases/resource-governor/change-resource-pool-settings.md)|  
|리소스 풀을 삭제하는 방법에 대해 설명합니다.|[리소스 풀 삭제](../../relational-databases/resource-governor/delete-a-resource-pool.md)|  
  
## <a name="see-also"></a>참고 항목  
 [관리](../../relational-databases/resource-governor/resource-governor.md)   
 [리소스 관리자 작업 그룹](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [리소스 관리자 분류자 함수](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [템플릿을 사용하여 리소스 관리자 구성](../../relational-databases/resource-governor/configure-resource-governor-using-a-template.md)   
 [리소스 관리자 속성 보기](../../relational-databases/resource-governor/view-resource-governor-properties.md)  
  
  
