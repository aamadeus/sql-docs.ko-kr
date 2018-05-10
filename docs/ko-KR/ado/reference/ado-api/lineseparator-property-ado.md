---
title: LineSeparator 속성 (ADO) | Microsoft Docs
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
- _Stream::LineSeparator
helpviewer_keywords:
- LineSeparator property [ADO]
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f46f6cdf8b3c8fccf9da41818aaeb2fb63fefbe6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="lineseparator-property-ado"></a>LineSeparator 속성 (ADO)
텍스트에 줄 구분 기호로 사용할 이진 문자 나타냅니다 [스트림](../../../ado/reference/ado-api/stream-object-ado.md) 개체입니다.  
  
## <a name="settings-and-return-values"></a>설정 및 반환 값  
 설정 하거나 반환는 [LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md) 에 사용 되는 줄 구분 기호 문자를 나타내는 값의 **스트림**합니다. 기본값은 **adCRLF**합니다.  
  
## <a name="remarks"></a>주의  
 **LineSeparator** 텍스트의 콘텐츠를 읽을 때 줄을 해석 하는 데 사용 **스트림**합니다. 선으로 건너뛸 수 있습니다는 [SkipLine](../../../ado/reference/ado-api/skipline-method.md) 메서드.  
  
 **LineSeparator** 텍스트에만 사용 됩니다 **스트림** 개체 ([형식](../../../ado/reference/ado-api/type-property-ado-stream.md) 은 **adTypeText**). 이 속성은 무시 **형식** 은 **adTypeBinary**합니다.  
  
## <a name="applies-to"></a>적용 대상  
 [스트림 개체(ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>관련 항목:  
 [스트림 개체(ADO)](../../../ado/reference/ado-api/stream-object-ado.md)