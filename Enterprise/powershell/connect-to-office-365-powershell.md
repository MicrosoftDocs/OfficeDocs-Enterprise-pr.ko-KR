---
title: PowerShell Office 365에 연결
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: '요약: Office 365 PowerShell을 사용 하 여 명령줄에서 관리 센터 작업을 수행 하 여 Office 365 조직에 연결 합니다.'
ms.openlocfilehash: ae0449611703759105d92a706cf78ba4a58ad4b2
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897201"
---
# <a name="connect-to-office-365-powershell"></a>PowerShell Office 365에 연결

 **요약:** Office 365 PowerShell을 사용 하 여 명령줄에서 관리 작업을 수행 하 여 Office 365 조직에 연결 합니다.
  
Office 365 PowerShell를 사용 하면 명령줄에서 Office 365 설정을 관리할 수 있습니다. 필요한 소프트웨어를 설치 하 고 다음 Office 365 조직에 연결 과정은 Office 365 PowerShell에 연결 합니다. 

Office 365에 연결 하 고 사용자 계정, 그룹 및 라이선스 관리를 사용 하는 PowerShell 모듈의 두 버전 가지가 있습니다.

- Azure PowerShell Active Directory 그래프 (cmdlet 이름에 **AzureAD** 포함)에 대 한 
- Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell (cmdlet 이름에 **MSol** 포함) 

이 문서의 날짜 그래프 모듈에 대 한 Active Directory Azure PowerShell 완전히 해도 사용자, 그룹 및 라이선스 관리에 대 한 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell 모듈의 cmdlet의 기능 . 대부분의 경우에서 두 버전을 사용 하 여 지정 해야 합니다. 안전 하 게 동일한 컴퓨터에 두 버전을 설치할 수 있습니다.

> [!TIP]
> **PowerShell을 처음 사용하시나요?** [PowerShell의 비디오 개요](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)를 보고 LinkedIn Learning을 통해 가져올 수 있습니다. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

- 예상 완료 시간: 5분
    
- 다음 Windows 버전을 사용할 수 있습니다.
    
  - 10 Windows, Windows 8.1, Windows 8 또는 Windows 7 서비스 팩 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Windows 64비트 버전을 사용하세요. 32비트 버전의 Microsoft PowerShell용 Windows Azure Active Directory 모듈은 2014년 10월에 중단되었습니다.
    
-  이 절차는 Office 365 관리자 역할의 구성원 인 사용자를 위한것입니다. 자세한 내용은 [Office 365에 대 한 관리자 역할](https://go.microsoft.com/fwlink/p/?LinkId=532367)을 참조 하십시오.


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>그래프 모듈에 대 한 Active Directory Azure PowerShell을 사용 하 여 연결

Cmdlet 이름에 **AzureAD** 를 포함 하는 [그래프에 대 한 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) 모듈에 명령 합니다.

그래프 모듈에 대 한 Azure Active Directory PowerShell에서 새 cmdlet을 필요로 하는 절차에 대 한 모듈을 설치 하 고 Office 365 구독에 연결 하려면 다음이 단계를 사용 합니다.

>[!Note]
>다른 버전의 Microsoft Windows에 대 한 지원에 대 한 정보에 대 한 [그래프 모듈에 대 한 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) 를 참조 합니다.
>

### <a name="step-1-install-required-software"></a>1단계: 필수 소프트웨어 설치

다음이 단계 연결할 때마다 하지 컴퓨터에 한 번만 필요 합니다. 주기적으로 최신 버전의 소프트웨어를 설치 하려면 필요할 수 있습니다.
  
1. 관리자 권한의 Windows PowerShell 명령 프롬프트를 엽니다(관리자 권한으로 Windows PowerShell 실행).
    
2. ** 관리자에서 Windows PowerShell** 명령 창에서 다음 명령을 실행합니다.
    
  ```
  Install-Module -Name AzureAD
  ```

신뢰할 수 없는 리포지토리에서 모듈을 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>2 단계: Office 365 구독에 대 한 Azure AD에 연결

*다단계 인증 (MFA)* 또는 계정 이름 및 암호를 사용한 Office 365 구독에 대 한 Azure AD에 연결할 (없는 상승 된 되도록) Windows PowerShell 명령 프롬프트에서 다음이 명령 중 하나를 실행 합니다.

|||
|:-------|:-----|
| **Office 365 클라우드** | **명령** |
| Office 365 전세계 (+ GCC) | `Connect-AzureAD` |
| Office 365에서 21 Vianet 운영 | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 미국 정부 DoD 및 Office 365 미국 정부 GCC 높음 | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

**계정에 로그인** 대화 상자에서 Office 365 작업 또는 학교 계정 사용자 이름 및 암호를 입력 한 다음 **확인**을 클릭 합니다.

MFA를 사용 하는 경우 지침에 따라 추가 대화 상자에서을 확인 코드 등의 더 많은 인증 정보를 제공 합니다.


를 연결한 후 [그래프 모듈에 대 한 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)에 대 한 새 cmdlet을 사용할 수 있습니다.
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈에 연결

Windows PowerShell용 Microsoft Azure Active Directory 모듈의 명령에는 cmdlet 이름에 **Msol**이 있습니다.
    
### <a name="step-1-install-required-software"></a>1단계: 필수 소프트웨어 설치

다음이 단계 연결할 때마다 하지 컴퓨터에 한 번만 필요 합니다. 주기적으로 최신 버전의 소프트웨어를 설치 하려면 필요할 수 있습니다.
  
1.  64비트 버전의 Microsoft Online Services 로그인 도우미를 설치합니다.[IT 전문가용 Microsoft Online Services 로그인 도우미 RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)를 설치합니다.
    
2. 다음 단계에 따라 Windows PowerShell용 Microsoft Azure Active Directory 모듈을 설치합니다.
    
  - 관리자 권한의 Windows PowerShell 명령 프롬프트를 엽니다(관리자 권한으로 Windows PowerShell 실행).
  - **Install-Module MSOnline** 명령을 실행합니다.
  - NuGet 공급자를 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.
  - PSGallery에서 모듈을 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>2 단계: Office 365 구독에 대 한 Azure AD에 연결

*다단계 인증 (MFA)* 또는 계정 이름 및 암호를 사용한 Office 365 구독에 대 한 Azure AD에 연결할 (없는 상승 된 되도록) Windows PowerShell 명령 프롬프트에서 다음이 명령 중 하나를 실행 합니다.

|||
|:-------|:-----|
| **Office 365 클라우드** | **명령** |
| Office 365 전세계 (+ GCC) | `Connect-MsolService` |
| Office 365에서 21 Vianet 운영 | `Connect-MsolService -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-MsolService -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 미국 정부 DoD 및 Office 365 미국 정부 GCC 높음 | `Connect-MsolService -AzureEnvironmentName USGovernment` |
|||

**계정에 로그인** 대화 상자에서 Office 365 작업 또는 학교 계정 사용자 이름 및 암호를 입력 한 다음 **확인**을 클릭 합니다.

MFA를 사용 하는 경우 지침에 따라 추가 대화 상자에서을 확인 코드 등의 더 많은 인증 정보를 제공 합니다.

### <a name="how-do-you-know-this-worked"></a>작동 여부는 어떻게 확인하나요?

어떠한 오류도 전송되지 않으면 성공적으로 연결되었음을 의미합니다. 빠른 테스트는 Office 365 cmdlet(예: **Get-MsolUser** )을 실행하여 결과를 확인하는 것입니다.
  
오류가 발생하면 다음 요구 사항을 확인합니다.
  
- **일반적인 문제는 잘못 된 암호는**입니다. 2 단계를 다시 실행 합니다. 및 입력 하면 사용자 이름 및 암호를 살펴보아야 합니다.
    
- **Windows PowerShell용 Microsoft Azure Active Directory 모듈을 사용하려면 컴퓨터에서 Microsoft .NET Framework 3.5.* x* 기능이 사용되도록 설정되어야 합니다.** 컴퓨터 최신 버전(예: 4 또는 4.5.* x*)이 설치되어 있을 수 있지만 이전 버전의 .NET Framework와의 호환성이 사용되거나 사용되지 않도록 설정되어 있을 수 있습니다. 자세한 내용은 다음 항목을 참조하세요.
    
  - Windows Server 2012 또는 Windows Server 2012 R2의 경우 [역할 및 기능 추가 마법사를 사용하여 .NET Framework 3.5를 사용 가능하도록 설정](https://go.microsoft.com/fwlink/p/?LinkId=532368)을 참조하세요.
    
  - Windows 7 또는 Windows Server 2008 R2의 경우 [Windows PowerShell용 Azure Active Directory 모듈을 열 수 없음](https://go.microsoft.com/fwlink/p/?LinkId=532370)을 참조하세요.

  - Windows 10, Windows 8.1 및 Windows 8의 경우 [Windows 10, Windows 8.1 및 Windows 8에서.NET Framework 3.5를 설치](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10) 를 참조합니다

  
- **사용자의 Microsoft PowerShell용 Windows Azure Active Directory 모듈 버전이 오래되었을 수 있습니다.** 확인하려면 Microsoft PowerShell용 Windows Azure Active Directory 모듈 또는 Office 365 PowerShell에서 다음 명령을 실행하세요.
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    반환된 버전 번호가 1.0.8070.2 값보다 낮은 경우 Microsoft PowerShell용 Windows Azure Active Directory 모듈을 제거한 후 1단계의 링크에서 최신 버전을 설치합니다.
    
- **연결 오류가 발생하면** ["Connect-MsolService: 형식의 예외가 발생했습니다." 오류](https://go.microsoft.com/fwlink/p/?LinkId=532377) 항목을 참조하세요.
    

## <a name="see-also"></a>참고 항목

- [Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
- [Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
- [단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결 합니다.](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

