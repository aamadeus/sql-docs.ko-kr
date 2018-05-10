---
title: StringFormatEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StringFormatEnum
helpviewer_keywords:
- StringFormatEnum enumeration [ADO]
ms.assetid: 28f7d1ec-092b-4323-a39d-d3f882c6c81a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8cca3873b45fc39eb0df3521ba9ca20941b7cdde
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="stringformatenum"></a>StringFormatEnum
검색할 때 형식을 지정는 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md) 문자열입니다.  
  
|상수|Value|Description|  
|--------------|-----------|-----------------|  
|**adClipString**|2|행을 구분 *RowDelimiter*, 별로 열 *ColumnDelimiter*, 및 null 값으로 *NullExpr*합니다. 세 매개 변수는 [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) 메서드에만 사용할 수는 *StringFormat* 의 **adClipString**합니다.|  
  
## <a name="adowfc-equivalent"></a>해당 하는 ADO/WFC  
 Package: **com.ms.wfc.data**  
  
|상수|  
|--------------|  
|AdoEnums.StringFormat.CLIPSTRING|  
  
## <a name="applies-to"></a>적용 대상  
 [GetString 메서드(ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)