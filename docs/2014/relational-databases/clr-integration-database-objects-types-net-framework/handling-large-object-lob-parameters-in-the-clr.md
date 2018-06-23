---
title: CLR의 LOB (Large Object) 매개 변수 처리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 58b2e188a69799dd0b8d36958a7059d5cfcc09f9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36184505"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>CLR의 LOB(Large Object) 매개 변수 처리
  LOB(Large Object) 이진 형식(`SqlBytes`) 및 LOB 문자 형식(`SqlChars`) 매개 변수는 각각 `varbinary(max)`와 `nvarchar(max)`를 사용하여 전달합니다. 이러한 형식을 사용하면 값 전체를 관리되는 공간에 복사하는 대신 데이터베이스의 LOB 값을 CLR(공용 언어 런타임) 루틴에 스트리밍할 수 있습니다. `SqlBinary` 및 `SqlString`은 작은 이진 및 문자열 값에만 사용해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [.NET Framework의 SQL Server 데이터 형식](sql-server-data-types-in-the-net-framework.md)  
  
  