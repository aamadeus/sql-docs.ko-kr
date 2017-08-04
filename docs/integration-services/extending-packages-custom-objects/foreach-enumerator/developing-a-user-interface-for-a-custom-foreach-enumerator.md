---
title: "사용자 지정 ForEach 열거자에 대 한 사용자 인터페이스 개발 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom user interface [Integration Services], custom foreach enumerators
- custom foreach enumerators [Integration Services], developing custom user interface
ms.assetid: 8aa4aa80-c9ba-42b3-ba87-ae5ea5d3cac3
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e743464fcf482ea51f0cde78d692b367c2be525b
ms.contentlocale: ko-kr
ms.lasthandoff: 08/03/2017

---
# <a name="developing-a-user-interface-for-a-custom-foreach-enumerator"></a>사용자 지정 ForEach 열거자의 사용자 인터페이스 개발
  기본 클래스의 속성 및 메서드 구현을 재정의하여 사용자 지정 기능을 제공한 후 Foreach 열거자에 대한 사용자 지정 사용자 인터페이스를 만들 수 있습니다. 사용자 지정 사용자 인터페이스를 만들지 않을 경우 사용자는 속성 창에서만 새 사용자 지정 Foreach 열거자를 구성할 수 있습니다.  
  
 사용자 지정 사용자 인터페이스 프로젝트 또는 어셈블리에서는 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>를 구현하는 클래스를 만듭니다. 이 클래스는 일반적으로 다른 Windows Forms 컨트롤을 호스트할 복합 컨트롤을 만드는 데 사용 되는 System.Windows.Forms.UserControl에서 파생 됩니다. 만들어야 하는 컨트롤에 표시 되는 **열거자 구성** 부문의 문제는 **컬렉션** 탭은 **Foreach 루프 편집기**합니다.  
  
> [!IMPORTANT]  
>  사용자 지정 사용자 인터페이스 서명 및 빌드하고 전역 어셈블리 캐시에서에 설명 된 대로 설치 후 [건물, Deploying, and 사용자 지정 개체 디버깅](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)에서이 클래스의 정규화 된 이름을 제공 해야는 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> 의 속성은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>합니다.  
  
## <a name="coding-the-user-interface-control-class"></a>사용자 인터페이스 컨트롤 클래스 코딩  
  
### <a name="initializing-the-user-interface"></a>사용자 인터페이스 초기화  
 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> 메서드를 재정의하여 호스트 개체에 대한 참조와 패키지에 정의된 연결 관리자 및 변수의 컬렉션에 대한 참조를 캐시할 수 있습니다.  
  
### <a name="setting-properties-on-the-user-interface-control"></a>사용자 인터페이스 컨트롤의 속성 설정  
 사용자 인터페이스 클래스 파생 되는 UserControl 클래스를 다른 Windows Forms 컨트롤을 호스팅하는 합성 컨트롤로 사용이 됩니다. 이 클래스는 다른 컨트롤을 호스팅하므로 Windows Forms 응용 프로그램에서와 같이 컨트롤을 끌어 놓은 다음 정렬하고 해당 속성을 설정하고 런타임에 해당 이벤트에 응답하여 사용자 지정 인터페이스를 디자인할 수 있습니다.  
  
### <a name="saving-settings"></a>설정 저장  
 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> 메서드를 재정의하여 사용자가 편집기를 닫을 때 컨트롤에서 선택한 값을 열거자의 속성에 복사할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [사용자 지정 Foreach 열거자 만들기](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/creating-a-custom-foreach-enumerator.md)   
 [사용자 지정 Foreach 열거자 코딩](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/coding-a-custom-foreach-enumerator.md)  
  
  