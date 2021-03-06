---
title: 큰 상수는 호환성 모드 90 이상에서 큰 값 유형으로 형식화 된 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- binary constants
- CHARINDEX function
- constants
- character string constants
- PATINDEX function
ms.assetid: 6e309fa0-5fb9-45a1-9739-f13fae525bfe
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a12a0972ee754c8f9070122902a64c3e92eb05f2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185283"
---
# <a name="large-constants-are-typed-as-large-value-types-in-90-or-later-compatibility-modes"></a>호환성 모드 90 이상에서 큰 상수는 큰 값 유형으로 처리됩니다.
  업그레이드 관리자가 큰 상수를 검색했습니다. 크기가 8,000바이트 이상인 문자열 상수와 이진 상수는 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서 큰 개체 데이터 형식으로 처리됩니다. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 큰 문자, 유니코드 및 이진 상수가 큰 값 유형으로 처리됩니다.  
  
## <a name="component"></a>구성 요소  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 CHARINDEX 및 PATINDEX와 같은 문자열 함수를 8,000바이트보다 큰 문자열 상수나 이진 상수와 함께 사용하면 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서는 오류 번호 8116이 반환되고 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 오류 번호 8152가 반환됩니다.  
  
 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서 문자열 함수를 `text`, `ntext` 및 `image` 데이터 형식과 함께 사용하면 오류 번호 8116이 반환됩니다.  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 큰 상수가 각각 `varchar(max)`, `nvarchar(max)` 및 `varbinary(max)` 데이터 형식으로 처리됩니다. 이러한 데이터 형식은 문자열 함수와 호환됩니다.  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 CHARINDEX 및 PATINDEX와 같은 문자열 함수가 검색할 문자 시퀀스가 포함된 문자열이 8,000바이트보다 작다고 간주하기 때문에 CHARINDEX 및 PATINDEX에 대해 오류 번호 8152가 반환됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 엔진 업그레이드 문제](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 업그레이드 관리자 &#91;새로 만들기&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
