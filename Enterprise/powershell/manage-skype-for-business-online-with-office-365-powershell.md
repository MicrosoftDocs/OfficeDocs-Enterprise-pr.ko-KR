---
title: Office 365 PowerShell을 사용하여 비즈니스용 Skype Online 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 요약:Office 365 PowerShell을 사용하여 비즈니스용 Skype 온라인 정책, 사용자 단위 정책 및 모임 설정을 관리합니다.
ms.openlocfilehash: f490131491a026961b0a5db312df5780483eadd9
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319239"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="d84e8-103">Office 365 PowerShell을 사용하여 비즈니스용 Skype Online 관리</span><span class="sxs-lookup"><span data-stu-id="d84e8-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

 <span data-ttu-id="d84e8-104">**요약:** Office 365 PowerShell을 사용하여 비즈니스용 Skype 온라인 정책, 사용자 단위 정책 및 모임 설정을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="d84e8-104">**Summary:** Use Office 365 PowerShell to manage Skype for Business Online policies, per-user policies, and meeting settings.</span></span>
  
<span data-ttu-id="d84e8-p101">정책 관리는 비즈니스 온라인 관리자에 대 한 모든 Skype의 기본 작업 중 하나입니다. Office 365 관리 센터에서 이러한 작업에 대해 작업을 수행할 수 있습니다, 있지만 훨씬 더 쉽고 빠르게 Office 365 PowerShell에서 다른 작업은 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d84e8-p101">One of the primary tasks of any Skype for Business Online administrator is managing policies. Although you can accomplish some of these tasks in the Office 365 Admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="d84e8-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d84e8-107">Before you start</span></span>

<span data-ttu-id="d84e8-108">다운로드 하 고 [비즈니스 온라인 커넥터 모듈에 대 한 Skype](https://www.microsoft.com/en-us/download/details.aspx?id=39366)설치 하 고 컴퓨터를 다시 시작 하 라는 메시지를 표시 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="d84e8-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="d84e8-109">온라인 비즈니스 관리자의 계정 이름 및 암호를 Skype를 사용 하 여 연결</span><span class="sxs-lookup"><span data-stu-id="d84e8-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="d84e8-110">Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d84e8-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="d84e8-111">**Windows PowerShell 자격 증명 요청** 대화 상자에서 사용자 Skype 비즈니스 온라인 관리자 계정 이름 및 암호를 입력 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d84e8-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="d84e8-112">다단계 인증을 사용 하는 비즈니스 온라인 관리자 계정에 대 한 Skype를 사용 하 여 연결</span><span class="sxs-lookup"><span data-stu-id="d84e8-112">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="d84e8-113">Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d84e8-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="d84e8-114">**새로 만들기 CsOnlineSession** 명령에 의해 대화 상자가 나타나면 비즈니스 온라인 관리자 계정 이름에 대 한 사용자 Skype를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d84e8-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="d84e8-115">**사용자의 계정에 로그인** 대화 상자에서 온라인 비즈니스 관리자 암호에 대 한 사용자 Skype를 입력 하 고 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d84e8-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="d84e8-116">지침에 따라 **사용자의 계정에 로그인** 대화 상자에서을 확인 코드와 같은 추가 인증 정보를 제공 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d84e8-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="d84e8-117">자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d84e8-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="d84e8-118">Office 365 PowerShell을 사용 하 여 온라인 비즈니스 정책을 용 Skype 관리</span><span class="sxs-lookup"><span data-stu-id="d84e8-118">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="d84e8-119">Office 365 powershell 비즈니스 온라인 정책에 대 한 사용자 당 Skype 할당</span><span class="sxs-lookup"><span data-stu-id="d84e8-119">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="d84e8-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d84e8-120">See also</span></span>

[<span data-ttu-id="d84e8-121">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="d84e8-121">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d84e8-122">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="d84e8-122">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

