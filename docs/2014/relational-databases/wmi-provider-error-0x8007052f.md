---
title: WMI 오류 0x8007052f | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- 0x8007052f (WMI error)
ms.assetid: a33f12bd-15c4-42a8-b343-de44c3e87729
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 3634e8f3b32cb612ba3a28680b17f361171a38dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48204483"
---
# <a name="wmi-error-0x8007052f"></a>WMI 오류 0x8007052f
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|0x8007052f|  
|이벤트 원본|WMI 공급자 오류|  
|구성 요소|SQL Server 구성 관리자|  
|심볼 이름|NA|  
|메시지 텍스트|로그온 실패: 사용자 계정 제한입니다. 빈 암호 사용, 로그온 시간 제한 또는 정책 제한으로 인해 이러한 문제가 발생할 수 있습니다.|  
  
## <a name="explanation"></a>설명  
 이 오류는 Windows Server 클러스터 또는 Windows Server 도메인 컨트롤러에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가 실행 중일 때 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 네트워크 서비스, 로컬 서비스, 로컬 시스템과 같은 기본 제공 계정으로 전환할 경우 발생할 수 있습니다. Windows Server 클러스터 또는 Windows Server 도메인 컨트롤러에서는 기본 제공 계정으로 서비스를 실행하지 마십시오. 서비스 계정에 대한 권장 사항은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 온라인 설명서의 “Windows 서비스 계정 설정” 항목을 참조하십시오.  
  
## <a name="user-action"></a>사용자 동작  
 도메인 계정을 사용하도록 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 를 구성합니다.  
  
  
