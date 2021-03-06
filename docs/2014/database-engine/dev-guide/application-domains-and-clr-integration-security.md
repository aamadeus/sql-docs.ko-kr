---
title: 응용 프로그램 도메인 및 CLR 통합 보안 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- application domains [CLR integration]
ms.assetid: 54ee904e-e21a-4ee7-b4ad-a6f6f71bd473
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 34814ab19f96ff7e6232638ef4446b05b5b41ba3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102351"
---
# <a name="application-domains-and-clr-integration-security"></a>응용 프로그램 도메인 및 CLR 통합 보안
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 동일한 응용 프로그램 도메인의 동일한 소유자에 속하는 어셈블리를 로드합니다. 동일한 응용 프로그램 도메인에서 실행되는 어셈블리 집합으로 인해 어셈블리는 .NET Framework 리플렉션 응용 프로그래밍 인터페이스나 다른 수단을 사용하여 실행 시 서로를 검색할 수 있으며 런타임에 바인딩된 방식으로 어셈블리를 호출할 수 있습니다. 이러한 호출은 동일한 소유자에 속하는 어셈블리에 대해 수행되기 때문에 해당 호출에 대해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용 권한이 검사되지 않습니다. 응용 프로그램 도메인의 어셈블리 배치 체계는 주로 확장성, 보안 및 격리 목적에 맞게 디자인되어 있으며 이후 릴리스에서 변경될 수 있습니다. 따라서 런타임에 바인딩 메커니즘을 통해 동일한 응용 프로그램 도메인의 어셈블리를 찾는 것은 피해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [CLR 통합 보안](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
