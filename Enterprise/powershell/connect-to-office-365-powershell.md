---
title: "PowerShell Office 365에 연결"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- DecEntMigration
- apr17entnews
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "요약: Office 365 PowerShell을 사용 하 여 명령줄에서 Office 365 관리 센터 작업을 수행 하 여 Office 365 조직에 연결 합니다."
ms.openlocfilehash: 3ac368a3d3584c15e1d0c26104616e8258a78e7b
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-office-365-powershell"></a>PowerShell Office 365에 연결

 **요약:** Office 365 PowerShell을 사용 하 여 명령줄에서 Office 365 관리 작업을 수행 하 여 Office 365 조직에 연결 합니다.
  
Office 365 PowerShell을 사용 하면 명령줄에서 Office 365 설정을 관리할 수 있습니다. 3 단계 과정 필요한 소프트웨어를 설치, 필요한 소프트웨어를 실행 한 다음 Office 365 조직에 연결 위치를 Office 365 PowerShell에 연결 합니다. 

Note는 이러한 연결 지침은 [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113)항목의 것과 동일 합니다.
  
> [!TIP]
> **PowerShell의 새로운 기능?** [PowerShell 비디오 개요 (영문)](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), LinkedIn 학습에 의해 제공자를 참조 하십시오. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>시작하기 전에 알아야 할 내용

- 예상 완료 시간: 5분
    
- 다음 Windows 버전을 사용할 수 있습니다.
    
  - 10 Windows, Windows 8.1, Windows 8 또는 Windows 7 서비스 팩 1 (SP1) 
    
  - Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >64 비트 버전의 Windows 사용 합니다. 32 비트 버전의 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell에 대 한 지원 2014 년 10 월에에서 중단 되었습니다.
    
-  Office 365 작동 또는 학교 계정을 사용 하는 이러한 절차에 대 한 요구를 Office 365 관리자 역할의 구성원 이어야 합니다. 자세한 내용은 [Office 365에 대 한 관리자 역할](https://go.microsoft.com/fwlink/p/?LinkId=532367)을 참조 하십시오.
    
## <a name="step-1-install-required-software"></a>1단계: 필수 소프트웨어 설치

다음이 단계 연결할 때마다 하지 컴퓨터에 한 번만 필요 합니다. 주기적으로 최신 버전의 소프트웨어를 설치 하려면 필요할 수 있습니다.
  
1.  64 비트 버전의 Microsoft Online Services 로그인 도우미 설치: [IT 전문가 RTW에 대 한 Microsoft Online Services 로그인 도우미](https://go.microsoft.com/fwlink/p/?LinkId=286152)합니다.
    
2. 이러한 단계는 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell의 64 비트 버전을 설치 합니다.
    
  - [Azure Active Directory 연결](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185) 웹 페이지를 엽니다.
    
  - 페이지의 맨 아래에 **다운로드에서 파일** 을에서 **AdministrationConfig-V1.1.166.0-GA.msi** 파일에 대 한 **다운로드** 를 클릭 하 고 설치 합니다.
    
## <a name="step-2-open-the-windows-azure-active-directory-module"></a>2단계: Windows Azure Active Directory 모듈 열기

1. 찾기 및 Windows의 버전에 따라 다음 방법 중 하나를 사용 하 여 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell을 엽니다.
    
  - **시작 메뉴** 바탕 화면에서 **시작**을 클릭 하 고 Azure를 입력 합니다.
    
  - **No 시작 메뉴** 이러한 방법 중 하나를 사용 하 여 검색 forAzure 합니다.
    
  - 시작 화면에서 빈 영역을 클릭 하 고 Azure를 입력 합니다.
    
  - 바탕 화면 또는 시작 화면에서 Windows 키 + Q를 누릅니다. 검색 참을 Azure를 입력 합니다.
    
  - 바탕 화면 또는 시작 화면에서 커서를 오른쪽 위 모서리 또는 살짝 참을 표시 하려면 화면 오른쪽 가장자리에서 왼쪽으로 이동 합니다. 검색 참을 선택 하 고 **Azure**를 입력 합니다.
    
2. 결과에서 **Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell**을 클릭 합니다.
    
## <a name="step-3-connect-to-your-office-365-subscription"></a>3 단계: Office 365 구독에 연결
<a name="step3"> </a>

연결 하는 *계정 이름 및 암호* :
  
1. **Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell** 명령 창에 다음 명령을 실행 합니다.
    
  ```
  $UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
  ```

2. **Windows PowerShell 자격 증명 요청** 대화 상자에서 Office 365 작업 또는 학교 계정 사용자 이름 및 암호를 입력 한 다음 **확인**을 클릭 합니다.
    
*다단계 인증 (MFA)* 와 연결 합니다.
  
1. **Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell** 명령 창에 다음 명령을 실행 합니다.
    
  ```
  Connect-MsolService
  ```

2. **PowerShell Azure Active Directory** 대화 상자에서 Office 365 작업 또는 학교 계정 사용자 이름 및 암호를 입력 한 다음 **로그인**을 클릭 합니다.
    
3. 확인 코드와 같은 추가 인증 정보를 제공 하려면 **PowerShell Azure Active Directory** 대화 상자의 지침에 따라 하 고 **로그인**을 클릭 합니다.
    
## <a name="how-do-you-know-this-worked"></a>작동 여부는 어떻게 확인합니까?
<a name="step3"> </a>

모든 오류가 하지 않으면 하는 경우 성공적으로 연결한 합니다. Office 365 cmdlet을 실행 하는 빠른 테스트는- **Get-msoluser** 예-하 고 결과 참조 하십시오.
  
오류가 발생하면 다음 요구 사항을 확인합니다.
  
- **일반적인 문제는 잘못 된 암호는**입니다. 3 단계를 다시 실행 합니다. 및 입력 하면 사용자 이름 및 암호를 살펴보아야 합니다.
    
- **Azure Active Directory 모듈 PowerShell 용 Microsoft Windows를 실행 하려면 Microsoft.NET Framework 3.5 합니다. 사용자의 컴퓨터에서 _x_ 기능이 활성화 되어**합니다. 사용자의 컴퓨터에 최신 버전이 설치 (예: 4 또는 4.5 것 같습니다. _x_),.NET Framework의 이전 버전과 호환성 수 사용 하거나 사용 하지 않도록 이전 버전과 하지만 합니다. 자세한 내용은 다음 항목을 참조 하십시오.
    
  - Windows Server 2012 또는 Windows Server 2012 r 2에 대 한 [역할 및 추가 기능 마법사를 사용 하 여.NET Framework 3.5 활성화](https://go.microsoft.com/fwlink/p/?LinkId=532368) 를 참조 하십시오.
    
  - Windows 8 또는 Windows 8.1 [Windows 8 또는 8.1에서.NET Framework 3.5를 설치](https://go.microsoft.com/fwlink/p/?LinkId=532369) 를 참조합니다
    
  - Windows 7 또는 Windows Server 2008 r 2에 대 한 참조 [는 Azure Active Directory에 대 한 Windows PowerShell 모듈을 열 수 없습니다](https://go.microsoft.com/fwlink/p/?LinkId=532370)
    
- **버전의 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell에 최신이 아닐 수 있습니다.** 을 확인 하려면 Office 365 PowerShell 또는 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell에서 다음 명령을 실행 합니다.
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    반환 되는 버전 번호를 1.0.8070.2 값 보다 작은 경우 Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell을 제거 하 고 1 단계에서에서 링크에서 최신 버전을 설치 합니다.
    
- **연결 오류 메시지가 표시 되는 경우이 항목을 참조:** ["Connect-msolservice: 유형의 예외가 발생 했습니다" 오류](https://go.microsoft.com/fwlink/p/?LinkId=532377)합니다.
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a>Azure Active Directory V2 PowerShell 모듈을 사용하 여 연결
<a name="ConnectV2"> </a>

[Azure Active Directory V2 PowerShell 모듈](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)의 새 cmdlet를 필요로 하는 절차에 대해 다음이 단계를 사용 하 여 모듈을 설치 하 고 Office 365 구독에 연결 하려면:
  
1. 관리자 권한의 Windows PowerShell 명령 프롬프트를 엽니다(관리자 권한으로 Windows PowerShell 실행).
    
2. **관리자: Windows PowerShell** 명령 창에서는이 명령을 실행 합니다.
    
  ```
  Install-Module -Name AzureAD 
  ```

신뢰할 수 있는 저장소에서 모듈을 설치 하는 방법에 대 한 메시지가 표시 되 면 **Y** 를 입력 하 고 ENTER 키를 누릅니다.
    
3. 새로운 모듈 설치가 완료되면 이러한 명령을 사용하여 Office 365 구독에 연결합니다.
    
  -  수 있는 *계정 이름 및 암호* :
    
  ```
  $UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
  ```

 **Windows PowerShell 자격 증명 요청** 대화 상자에서 Office 365 작업 또는 학교 계정 사용자 이름 및 암호를 입력 한 다음 **확인**을 클릭 합니다.
    
  - *다단계 인증 (MFA)* :
    
  ```
  Connect-AzureAD
  ```

**PowerShell Azure Active Directory** 대화 상자에서 Office 365 작업 또는 학교 계정 사용자 이름 및 암호를 입력 한 다음 **로그인**을 클릭 합니다.
    
확인 코드와 같은 추가 인증 정보를 제공 하려면 **PowerShell Azure Active Directory** 대화 상자의 지침에 따라 하 고 **로그인**을 클릭 합니다.
    
를 연결한 후 [Azure Active Directory V2 PowerShell 모듈](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)에 대 한 새 cmdlet을 사용할 수 있습니다.
  
## <a name="see-also"></a>See also

#### 

[Office 365 PowerShell로 Office 365 관리](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 시작](getting-started-with-office-365-powershell.md)
  
[단일 Windows PowerShell 창에서 모든 Office 365 서비스에 연결](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
#### 

[Get-자격 증명](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[연결 MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

