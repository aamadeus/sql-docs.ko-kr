---
title: 데이터 정렬 및 CLR 통합 데이터 형식 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 40c4abad803424ac9b274045f699785b85689644
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069903"
---
# <a name="collation-and-clr-integration-data-types"></a>데이터 정렬 및 CLR 통합 데이터 형식
  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]에서는 `CompareInfo` 개체가 데이터 정렬을 처리합니다. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 문자열 API(응용 프로그래밍 인터페이스)는 현재 스레드의 `CompareInfo` 개체와 연결된 `CultureInfo` 속성을 사용하여 문자열 비교를 수행합니다. 기본 설정을 `CultureInfo` 개체의 기반이 되는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 컴퓨터는 Windows 로캘 설정 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 실행 합니다. `CultureInfo` 값을 비교할 때 `System.String`가 명시적으로 지정되지 않은 경우 이 설정에 따라 기본 비교 의미 체계가 달라집니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 데이터베이스 또는 서버 데이터 정렬에 대한 `CompareInfo` 속성을 명시적으로 변경하지 않습니다. 필요한 경우 사용자가 자신의 루틴에서 적절한 `CompareInfo` 속성을 설정해야 합니다.  
  
## <a name="parameter-collation"></a>매개 변수 데이터 정렬  
 CLR(공용 언어 런타임) 루틴을 만들 때 루틴에 바인딩된 CLR 메서드의 매개 변수가 `SQLString` 형식이면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 호출 루틴을 포함하는 데이터베이스의 기본 데이터 정렬로 매개 변수 인스턴스를 만듭니다. 매개 변수가 `SqlType`이 아닌 경우(예: `String`이 아닌 `SQLString`) 매개 변수에 데이터베이스의 데이터 정렬 정보가 연결되지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [.NET Framework의 SQL Server 데이터 형식](sql-server-data-types-in-the-net-framework.md)  
  
  
