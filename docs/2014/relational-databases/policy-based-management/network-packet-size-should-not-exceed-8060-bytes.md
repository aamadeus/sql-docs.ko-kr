---
title: 네트워크 패킷 크기는 8060바이트를 초과할 수 없음 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1a4e25b746305cc3f8575f167cc9a216491ac55f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126203"
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>네트워크 패킷 크기는 8060바이트를 초과할 수 없음
  sp_configure 'network packet size'에 지정된 값 또는 로그인된 사용자의 네트워크 패킷 크기가 8060바이트보다 큰 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 서로 다른 메모리 할당 작업을 수행합니다. 그 결과 버퍼 풀에 예약되지 않는 프로세스 가상 주소 공간이 증가할 수 있습니다.  
  
## <a name="best-practices-recommendations"></a>최선의 구현 방법 권장 사항  
 네트워크 패킷 크기는 8060바이트를 초과하면 안 됩니다.  
  
## <a name="for-more-information"></a>참조 항목  
 [Microsoft 기술 자료 문서 903002](http://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>관련 항목  
 [정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
