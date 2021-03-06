---
title: 메모리 액세스에 최적화된 테이블에 대한 검사점 작업 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 47975bd5-373f-43cd-946a-da8e8088b610
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ddcdec0f624c1d6f70c57e593eaf9da66cbe0419
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48208983"
---
# <a name="checkpoint-operation-for-memory-optimized-tables"></a>메모리 액세스에 최적화된 테이블에 대한 검사점 작업
  트랜잭션 로그의 활성 부분을 처리하기 위해서는 데이터 및 델타 파일에서 메모리 최적화 데이터에 대한 검사점이 정기적으로 설정되어야 합니다. 검사점을 사용하면 메모리 최적화 테이블이 마지막으로 성공한 검사점으로 복원되거나 복구될 수 있으며, 이때 메모리 최적화 테이블을 업데이트하여 복구를 완료하기 위해 트랜잭션 로그의 활성 부분이 적용됩니다. 디스크 기반 테이블의 검사점 작업과 메모리 최적화 테이블의 검사점 작업은 전혀 다른 작업입니다. 아래에서는 디스크 기반 테이블과 메모리 최적화 테이블의 서로 다른 시나리오 및 검사점 동작에 대해 설명합니다.  
  
## <a name="manual-checkpoint"></a>수동 검사점  
 수동 검사점을 실행하면 디스크 기반 테이블 및 메모리 최적화 테이블에 대한 검사점이 닫힙니다. 또한 부분적으로 채워졌을 수도 있는 활성 데이터 파일이 닫힙니다.  
  
## <a name="automatic-checkpoint"></a>자동 검사점  
 데이터가 지속되는 방식의 차이 때문에 자동 검사점은 디스크 기반 테이블과 메모리 최적화 테이블에 대해 다르게 구현됩니다.  
  
 디스크 기반 테이블의 경우 복구 간격 구성 옵션을 기반으로 자동 검사점이 확인됩니다(자세한 내용은 [데이터베이스의 대상 복구 시간 변경&#40;SQL Server&#41;](../logs/change-the-target-recovery-time-of-a-database-sql-server.md) 참조).  
  
 메모리 최적화 테이블의 경우 마지막 검사점 이후 트랜잭션 로그 파일이 512MB보다 커질 때 자동 검사점이 확인됩니다. 512MB에는 디스크 기반 및 메모리 최적화 테이블 모두에 대한 트랜잭션 로그 기록이 포함됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [메모리 액세스에 최적화된 개체의 저장소 만들기 및 관리](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
