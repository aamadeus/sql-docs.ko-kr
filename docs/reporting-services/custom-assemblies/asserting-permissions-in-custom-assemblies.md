---
title: "사용자 지정 어셈블리에서 권한 어설션 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- secure calls [Reporting Services]
- custom assemblies [Reporting Services], permissions
- permission sets [Reporting Services]
- asserting permissions
- permissions [Reporting Services], custom assemblies
- limited permission sets
- security configuration files [Reporting Services]
ms.assetid: 3afb9631-f15e-405e-990b-ee102828f298
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 12e12b61a6b2a2a6a58bb88dd3c4f47c2a6eab22
ms.contentlocale: ko-kr
ms.lasthandoff: 06/22/2017

---
# <a name="asserting-permissions-in-custom-assemblies"></a>사용자 지정 어셈블리에서 권한 어설션
  기본적으로 사용자 지정 어셈블리 코드는 제한 된으로 실행 **실행** 사용 권한 집합입니다. 경우에 따라 보안 시스템 내에서 보호된 리소스(파일, 레지스트리 등)에 대한 보안 호출을 하는 사용자 지정 어셈블리를 구현하고자 할 수 있습니다. 이렇게 하려면 다음 작업을 수행해야 합니다.  
  
1.  코드에서 보안 호출을 하는 데 필요한 정확한 권한을 식별합니다. 이 메서드는 일부의 경우는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 라이브러리에이 정보는 메서드 설명서에 포함 되어야 합니다.  
  
2.  사용자 지정 어셈블리에 필요한 권한을 부여하기 위해 보고서 서버 정책 구성 파일을 수정합니다. 보안 정책 구성 파일에 대 한 자세한 내용은 참조 [를 사용 하 여 Reporting Services 보안 정책 파일](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md)합니다.  
  
3.  필요한 권한을 보안 호출이 이루어지는 메서드의 일부로 어설션합니다. 보고서 서버에서 호출 하는 사용자 지정 어셈블리 코드를 실행 하는 보고서 식 호스트 어셈블리의 일부인 때문에 이것이 필요 **실행** 기본적으로 사용 권한. **실행** 사용 권한 집합을 사용 하면 코드를 실행 하려면 있지만 보호 된 리소스를 사용할 수는 없습니다.  
  
4.  사용 하 여 사용자 지정 어셈블리 표시 **AllowPartiallyTrustedCallersAttribute** 강력한 이름의 서명 된 경우. 사용자 지정 어셈블리는 기본적으로 부여 되지 않은 있는 보고서 식 호스트 어셈블리의 일부인 보고서 식에서 호출 되므로이 작업이 필요 **FullTrust**; "부분적으로 신뢰할 수 있는" 호출자 즉 합니다. 자세한 내용은 참조 [이름의 사용자 지정 어셈블리](../../reporting-services/custom-assemblies/using-strong-named-custom-assemblies.md)합니다.  
  
## <a name="implementing-a-secure-call"></a>보안 호출 구현  
 정책 구성 파일을 수정하여 어셈블리별 권한을 부여할 수 있습니다. 예를 들어, 통화 변환을 처리하도록 사용자 지정 어셈블리를 작성하는 경우 파일에서 현재 통화 환율을 읽어야 합니다. 환율 정보를 검색 하려면는 추가 보안 권한을 추가 해야 **FileIOPermission**, 권한 집합 어셈블리에 있습니다. 정책 구성 파일에서 다음 추가 항목을 입력할 수 있습니다.  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="CurrencyRatesFilePermissionSet"  
   Description="A special permission set that grants read access to my currency rates file.">  
      <IPermission class="FileIOPermission"  
         version="1"  
         Read="C:\CurrencyRates.xml"/>  
      <IPermission class="SecurityPermission"  
         version="1"  
         Flags="Execution, Assertion"/>  
</PermissionSet>  
```  
  
 그런 다음 해당 권한 집합을 참조하는 코드 그룹을 추가합니다.  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="CurrencyRatesFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\MSSQL\Reporting Services\ReportServer\bin\CurrencyConversion.dll"/>  
</CodeGroup>  
```  
  
 코드에 올바른 권한이 부여되려면 사용자 지정 어셈블리 코드 내에서 권한을 어설션해야 합니다. 예를 들어, XML 파일 C:\CurrencyRates.xml에 읽기 전용 액세스 권한을 추가하려면 다음 코드를 메서드에 추가해야 합니다.  
  
```  
// C#  
FileIOPermission permission = new FileIOPermission(FileIOPermissionAccess.Read, @"C:\CurrencyRates.xml");  
try  
{  
   permission.Assert();  
   // Load the XML currency rates file  
   XmlDocument doc = new XmlDocument();  
   doc.Load(@"C:\CurrencyRates.xml");  
...  
```  
  
 또한 어설션을 메서드 특성 형태로 추가할 수도 있습니다.  
  
```  
[FileIOPermissionAttribute(SecurityAction.Assert, Read=@"C:\CurrencyRates.xml")]  
```  
  
 자세한 내용은 .NET Framework 개발자 가이드의 ".NET Framework Security(.NET Framework 보안)"를 참조하십시오.  
  
## <a name="see-also"></a>관련 항목:  
 [보고서에 사용자 지정 어셈블리 사용](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  