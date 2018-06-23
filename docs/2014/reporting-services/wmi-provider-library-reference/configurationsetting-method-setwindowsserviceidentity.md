---
title: SetWindowsServiceIdentity 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
caps.latest.revision: 19
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: fc3dfeafab01480fde7eb195363f46946de30ddd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36172094"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserverconfigurationsetting"></a>SetWindowsServiceIdentity 메서드(WMI MSReportServer_ConfigurationSetting)
  보고서 서버 Windows 서비스가 지정된 Windows 사용자로 실행되도록 하고 이 계정에 보고서 서버를 작동하기에 충분한 파일 시스템 사용 권한을 부여합니다.  
  
## <a name="syntax"></a>구문  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>매개 변수  
 *UseBuiltInAccount*  
 지정된 계정이 기본 제공 Windows 계정인지 여부를 나타냅니다.  
  
 *계정*  
 Windows 서비스를 실행하는 데 사용할 "DOMAIN\alias" 형식의 Windows 계정입니다.  
  
 *암호*  
 계정의 암호입니다.  
  
 *HRESULT*  
 [out] 호출의 성공 여부를 나타내는 값입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다. 0 값은 메서드 호출이 성공했음을 나타냅니다. 0 이외의 값은 오류가 발생했음을 나타냅니다.  
  
## <a name="remarks"></a>Remarks  
 때는 *UseBuiltInAccount* 로 설정 된 `true` Microsoft에서 실행 되 고 보고서 서버 [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] 또는 Windows XP의 경우 값은 *이름*, *도메인*, 및 *암호* 매개 변수는 무시 하 고 로컬 시스템 계정이 사용 됩니다.  
  
 경우는 *UseBuiltInAccount* 로 설정 된 `true` Windows Server 2003에서 실행 되 고 보고서 서버는 *도메인* 및 *암호* 속성은 무시 되 고 이름 필드에 "Builtin\NetworkService" 또는 "Builtin\System" 또는 "Builtin\LocalService"이 있어야 합니다.  
  
 SetWindowsServiceIdentity 메서드는 보고서 서버 설치 디렉터리에 있는 파일 및 폴더에 대한 파일 사용 권한을 설정합니다.  
  
 에 지정한 계정을 *계정* 매개 변수에 필요 `LogonAsService` windows에서 권한입니다. 이 권한은 메서드를 통해 지정된 계정에 부여됩니다.  
  
## <a name="requirements"></a>요구 사항  
 **네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>관련 항목  
 [MSReportServer_ConfigurationSetting 멤버](msreportserver-configurationsetting-members.md)  
  
  