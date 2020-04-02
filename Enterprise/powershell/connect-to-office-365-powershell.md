---
title: PowerShell Office 365에 연결
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/31/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Office 365 PowerShell을 통해 Office 365 조직에 연결하여 명령줄에서 관리 센터 작업을 수행합니다.
ms.openlocfilehash: 642016f734a2a9d7e490d5905a3ed93d7f330ca9
ms.sourcegitcommit: 7f025939c9dad676602bcd7693a8e356821fd456
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/31/2020
ms.locfileid: "43068760"
---
# <a name="connect-to-office-365-powershell"></a>PowerShell Office 365에 연결

Office 365 PowerShell을 사용하여 명령줄에서 Office 365 설정을 관리할 수 있습니다. Office 365 PowerShell에 연결하려면 필요한 소프트웨어를 설치하고 Office 365 조직에 연결하는 간단한 과정을 수행합니다. 

Office 365 및 관리자 계정, 그룹 및 라이선스에 연결하는 데 사용하는 두 가지 버전의 PowerShell 모듈이 있습니다.

- Azure Active Directory PowerShell for Graph(cmdlet의 이름에 **AzureAD** 포함)
- Windows PowerShell용 Microsoft Azure Active Directory 모듈(cmdlet의 이름에 **MSol** 포함) 

이 문서의 날짜를 기준으로, Azure Active Directory PowerShell for Graph 모듈이 사용자, 그룹 및 라이선스 관리를 위해 Windows PowerShell용 Microsoft Azure Active Directory 모듈을 완전히 대체하는 것은 아닙니다. 대부분의 경우, 두 버전을 사용해야 합니다. 동일한 컴퓨터에 두 버전을 안전하게 설치할 수 있습니다.

## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 사항은 무엇인가요?

다음 Windows 버전을 사용할 수 있습니다.
    
  - Windows 10, Windows 8.1, Windows 8 또는 Windows 7 서비스팩 1(SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 R2 SP1

    > [!NOTE]
    > Azure Active Directory PowerShell for Graph 모듈의 경우 PowerShell 버전 5.1 이상을 사용해야 합니다. Windows PowerShell용 Microsoft Azure Active Directory 모듈의 경우 PowerShell 버전 5.1 이상 PowerShell 버전 6 이하를 사용해야 합니다. PowerShell 버전 7은 사용할 수 없습니다. Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 및 Windows Server 2008 R2 SP1의 경우, [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616)을 다운로드하고 설치합니다.  
    
    > [!NOTE]
    > Windows 64비트 버전을 사용하세요. 32비트 버전의 Microsoft PowerShell용 Windows Azure Active Directory 모듈은 2014년 10월에 중단되었습니다.
    
이러한 절차는 Office 365 관리자 역할의 구성원인 사용자를 대상으로 합니다. 자세한 내용은 [Office 365 관리자 역할 정보](https://go.microsoft.com/fwlink/p/?LinkId=532367)를 참조하세요.


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>그런 다음, Azure Active Directory PowerShell for Graph 모듈에 연결합니다.

Azure Active Directory PowerShell for Graph 모듈의 명령에는 cmdlet 이름에 **AzureAD**가 있습니다. [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) 모듈 또는 [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1)을 설치할 수 있습니다.

Azure Active Directory PowerShell for Graph 모듈에서 새 cmdlet을 필요로 하는 프로시저의 경우, 이러한 단계를 사용해서 모듈을 설치하고 Office 365 구독에 연결할 수 있습니다.

>[!Note]
>Microsoft Windows의 여러 버전에 대한 지원 정보는 [Azure Active Directory PowerShell for Graph 모듈](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)을 참조하세요.
>

### <a name="step-1-install-required-software"></a>1단계: 필수 소프트웨어 설치

다음이 단계 연결할 때마다 하지 컴퓨터에 한 번만 필요 합니다. 주기적으로 최신 버전의 소프트웨어를 설치 하려면 필요할 수 있습니다.
  
1. 관리자 권한의 Windows PowerShell 명령 프롬프트를 엽니다(관리자 권한으로 Windows PowerShell 실행).
    
2. ** 관리자에서 Windows PowerShell** 명령 창에서 다음 명령을 실행합니다.
    
  ```powershell
  Install-Module -Name AzureAD
  ```

신뢰할 수 없는 리포지토리에서 모듈을 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>2단계: Office 365 구독을 위해 Azure AD에 연결

계정 이름 및 암호를 사용하여 또는 MFA(다중 요소 인증)을 사용하여 Office 365 구독을 위해 Azure AD에 연결하려면, Windows PowerShell 명령 프롬프트(관리자 권한이 아니어도 됨)에서 이 명령 중 하나를 실행하세요.

|||
|:-------|:-----|
| **Office 365 클라우드** | **명령** |
| Office 365 Worldwide(+GCC) | `Connect-AzureAD` |
| 21 Vianet이 운영하는 Office 365 | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 미국 국방부(DoD) 및 Office 365 미국 정부 GCC High | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

**계정에 로그인하세요** 대화 상자에서, Office 365 회사 또는 학교 계정 사용자 이름 및 암호를 입력한 다음, **확인**을 클릭하세요.

MFA를 사용하는 경우, 추가 대화 상자에 있는 지침을 따라서 추가 인증 정보(예: 확인 코드)를 제공하세요.

연결 후 [그래프 모듈용 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)의 cmdlet을 사용할 수 있습니다.
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell용 Microsoft Azure Active Directory 모듈에 연결

Windows PowerShell용 Microsoft Azure Active Directory 모듈의 명령에는 cmdlet 이름에 **Msol**이 있습니다.

PowerShell 버전 7 이상은 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. PowerShell 버전 7 이상의 경우 Azure Active Directory PowerShell for Graph 모듈 또는 Azure PowerShell을 사용해야 합니다.

PowerShell Core는 Windows PowerShell용 Microsoft Azure Active Directory 모듈 및 이름에 **Msol**이 있는 cmdlet을 지원하지 않습니다. 이러한 cmdlet을 계속 사용하려면 Windows PowerShell에서 이를 실행해야 합니다. 
    
### <a name="step-1-install-required-software"></a>1단계: 필수 소프트웨어 설치

다음이 단계 연결할 때마다 하지 컴퓨터에 한 번만 필요 합니다. 주기적으로 최신 버전의 소프트웨어를 설치 하려면 필요할 수 있습니다.
  
1.  64비트 버전의 Microsoft Online Services 로그인 도우미를 설치합니다.[IT 전문가용 Microsoft Online Services 로그인 도우미 RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)를 설치합니다.
    
2. 다음 단계에 따라 Windows PowerShell용 Microsoft Azure Active Directory 모듈을 설치합니다.
    
  - 관리자 권한의 Windows PowerShell 명령 프롬프트를 엽니다(관리자 권한으로 Windows PowerShell 실행).
  - **Install-Module MSOnline** 명령을 실행합니다.
  - NuGet 공급자를 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.
  - PSGallery에서 모듈을 설치할지 묻는 메시지가 표시되면 **Y**를 입력하고 Enter 키를 누릅니다.
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>2단계: Office 365 구독을 위해 Azure AD에 연결

계정 이름 및 암호를 사용하여 또는 MFA(다중 요소 인증)을 사용하여 Office 365 구독을 위해 Azure AD에 연결하려면, Windows PowerShell 명령 프롬프트(관리자 권한이 아니어도 됨)에서 이 명령 중 하나를 실행하세요.

|||
|:-------|:-----|
| **Office 365 클라우드** | **명령** |
| Office 365 Worldwide(+GCC) | `Connect-MsolService` |
| 21 Vianet이 운영하는 Office 365 | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Germany | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 미국 국방부(DoD) 및 Office 365 미국 정부 GCC High | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

**계정에 로그인하세요** 대화 상자에서, Office 365 회사 또는 학교 계정 사용자 이름 및 암호를 입력한 다음, **확인**을 클릭하세요.

MFA를 사용하는 경우, 추가 대화 상자에 있는 지침을 따라서 추가 인증 정보(예: 확인 코드)를 제공하세요.

### <a name="how-do-you-know-this-worked"></a>작동 여부는 어떻게 확인하나요?

어떠한 오류도 전송되지 않으면 성공적으로 연결되었음을 의미합니다. 빠른 테스트는 Office 365 cmdlet(예: **Get-MsolUser** )을 실행하여 결과를 확인하는 것입니다.
  
오류가 발생하면 다음 요구 사항을 확인합니다.
  
- **가장 흔한 문제는 암호를 잘못 입력한 경우입니다**. 2단계를 다시 실행합니다. 사용자 이름과 암호를 입력할 때 신중하게 확인합니다.
    
- **Windows PowerShell용 Microsoft Azure Active Directory 모듈을 사용하려면 컴퓨터에서 Microsoft .NET Framework 3.5.* x* 기능이 사용되도록 설정되어야 합니다.** 컴퓨터 최신 버전(예: 4 또는 4.5.* x*)이 설치되어 있을 수 있지만 이전 버전의 .NET Framework와의 호환성이 사용되거나 사용되지 않도록 설정되어 있을 수 있습니다. 자세한 내용은 다음 항목을 참조하세요.
    
  - Windows Server 2012 또는 Windows Server 2012 R2의 경우 [역할 및 기능 추가 마법사를 사용하여 .NET Framework 3.5를 사용 가능하도록 설정](https://go.microsoft.com/fwlink/p/?LinkId=532368)을 참조하세요.
    
  - Windows 7 또는 Windows Server 2008 R2의 경우 [Windows PowerShell용 Azure Active Directory 모듈을 열 수 없음](https://go.microsoft.com/fwlink/p/?LinkId=532370)을 참조하세요.

  - Windows 10, Windows 8.1 및 Windows 8의 경우, [Windows 10, Windows 8.1 및 Windows 8에 .NET Framework 3.5 설치](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)를 참조하세요.

  
- **사용자의 Microsoft PowerShell용 Windows Azure Active Directory 모듈 버전이 오래되었을 수 있습니다.** 확인하려면 Microsoft PowerShell용 Windows Azure Active Directory 모듈 또는 Office 365 PowerShell에서 다음 명령을 실행하세요.
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    반환된 버전 번호가 1.0.8070.2 값보다 낮은 경우 Microsoft PowerShell용 Windows Azure Active Directory 모듈을 제거한 후 1단계의 링크에서 최신 버전을 설치합니다.

- **연결 오류가 발생하면** ["Connect-MsolService: 형식의 예외가 발생했습니다." 오류](https://go.microsoft.com/fwlink/p/?LinkId=532377) 항목을 참조하세요.
    
- **"Get-Item: path를 찾을 수 없습니다" 라는 오류가 표시 되는 경우 다음 명령을 사용 합니다.** 

  ```powershell
  (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
 
```

## <a name="see-also"></a>참고 항목

- [Office 365 PowerShell 사용한 Office 365 관리](manage-office-365-with-office-365-powershell.md)
- [Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
- [단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
