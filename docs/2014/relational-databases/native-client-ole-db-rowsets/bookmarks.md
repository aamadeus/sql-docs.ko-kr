---
title: 책갈피 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6bc03a966ecd3d467f66d41f5ba8318b47b95f71
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36186303"
---
# <a name="bookmarks"></a>책갈피
  소비자는 책갈피를 사용하여 신속하게 특정 행으로 돌아갈 수 있습니다. 즉, 소비자는 책갈피 값을 바탕으로 행에 임의로 액세스할 수 있습니다. 책갈피 열은 행 집합의 0번 열입니다. 소비자는 바인딩 구조의 dwFlag 필드 값을 DBCOLUMNSINFO_ISBOOKMARK로 설정하여 해당 열이 책갈피로 사용되는 행임을 지정합니다. 소비자는 또한 행 집합 속성 DBPROP_BOOKMARKS를 VARIANT_TRUE로 설정합니다. 이렇게 하면 행 집합에 0번 열을 지정할 수 있습니다. **irowsetlocate:: Getrowsat** 메서드는 다음 책갈피에서 오프셋으로 지정 된 행부터 행을 인출 하는 데 사용 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [행 집합](rowsets.md)  
  
  