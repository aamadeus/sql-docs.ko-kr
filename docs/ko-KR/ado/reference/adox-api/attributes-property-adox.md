---
title: 특성 속성 (ADOX) | Microsoft Docs
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
- _Column::put_Attributes
- _Column::Attributes
- _Column::PutAttributes
- _Column::get_Attributes
- _Column::GetAttributes
helpviewer_keywords:
- Attributes property [ADOX]
ms.assetid: e3abb359-79a3-4c22-b3a8-2900817e0d23
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9956ab6277c6f209517d43fd4a14365fded2e27e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="attributes-property-adox"></a>특성 속성 (ADOX)
열 특징을 설명 합니다.  
  
## <a name="settings-and-return-values"></a>설정 및 반환 값  
 설정 하거나 반환는 **긴** 값입니다. 값이 나타내는 테이블의 특성을 지정 된 [열](../../../ado/reference/adox-api/column-object-adox.md) 개체입니다. 값의 조합 수 [ColumnAttributesEnum](../../../ado/reference/adox-api/columnattributesenum.md) 상수입니다. 기본값은 0 (**0**)가 아닌 **adColFixed** 나 **adColNullable**합니다.  
  
## <a name="applies-to"></a>적용 대상  
  
- [Column 개체(ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>관련 항목:  
 [Attributes 속성 예제(VB)](../../../ado/reference/adox-api/attributes-property-example-vb.md)