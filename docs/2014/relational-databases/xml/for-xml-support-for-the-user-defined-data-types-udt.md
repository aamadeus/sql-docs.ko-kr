---
title: UDT(사용자 정의 데이터 형식)에 대한 FOR XML 지원 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
caps.latest.revision: 22
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: dff9ca624541aa632d4cc1b230377dd5e0ed9b7c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36091905"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a>사용자 정의 데이터 형식(UDT)에 대한 FOR XML 지원
  FOR XML은 CLR(공용 언어 런타임) UDT(사용자 정의 데이터 형식)를 지원하지 않습니다.  
  
 CLR 사용자 정의 데이터 형식으로 FOR XML을 사용하려면 데이터 형식에 XML 직렬화가 있는지 확인하고 FOR XML 선택 절의 XML로의 명시적 캐스트를 사용합니다.  
  
## <a name="see-also"></a>관련 항목  
 [다양한 SQL Server 데이터 형식에 대한 FOR XML 지원](for-xml-support-for-various-sql-server-data-types.md)  
  
  