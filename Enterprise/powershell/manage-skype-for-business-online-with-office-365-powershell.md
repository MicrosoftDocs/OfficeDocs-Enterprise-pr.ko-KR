---
title: PowerShell을 통해 비즈니스용 Skype Oline 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 요약:. Microsoft 365용 PowerShell을 사용하여 Skype for Business Online 정책, 사용자별 정책 및 모임 설정을 관리할 수 있습니다.
ms.openlocfilehash: 10587dad171c3df9de6985ad314bc1791080b8a1
ms.sourcegitcommit: 839236443410eb804372c4aae969ac9a82ba683b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2020
ms.locfileid: "46592212"
---
# <a name="manage-skype-for-business-online-with-powershell"></a><span data-ttu-id="72274-103">PowerShell을 통해 비즈니스용 Skype Oline 관리</span><span class="sxs-lookup"><span data-stu-id="72274-103">Manage Skype for Business Online with PowerShell</span></span>

<span data-ttu-id="72274-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="72274-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="72274-105">비즈니스용 Skype Online 관리자의 기본 작업 중 하나는 정책을 관리하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="72274-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="72274-106">Office 365 관리 센터에서 이러한 작업 중 일부를 수행할 수 있지만 PowerShell에서 훨씬 더 빠르고 쉽게 수행할 수 있는 작업도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72274-106">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="72274-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="72274-107">Before you start</span></span>

<span data-ttu-id="72274-108">[비즈니스용 Skype Online 커넥터 모듈](https://www.microsoft.com/download/details.aspx?id=39366)를 다운로드하여 설치하고 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="72274-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="72274-109">비즈니스용 Skype Online 관리자 계정 이름 및 암호를 사용하여 연결</span><span class="sxs-lookup"><span data-stu-id="72274-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="72274-110">Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="72274-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. <span data-ttu-id="72274-111">**Windows PowerShell 자격 증명 요청** 대화 상자에서 Skype for Business Online 관리자 계정 이름과 암호를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72274-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="72274-112">다중 요소 인증으로 Skype for Business Online 관리자 계정을 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="72274-112">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="72274-113">Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="72274-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. <span data-ttu-id="72274-114">**New-CsOnlineSession** 명령에 메시지가 표시되면 비즈니스용 Skype Online 관리자 계정 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="72274-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="72274-115">**계정에 로그인** 대화 상자에서 비즈니스용 Skype Online 관리자r 암호를 입력한 다음 **로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72274-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="72274-116">**계정에 로그인** 대화 상자의 지침에 따라 확인 코드와 같은 추가 인증 정보를 제공한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72274-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="72274-117">자세한 내용은 아래 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="72274-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="72274-118">PowerShell을 사용하여 온라인 비즈니스 정책용 Skype 관리</span><span class="sxs-lookup"><span data-stu-id="72274-118">Manage Skype for Business Online policies with PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="72274-119">Powershell 비즈니스 온라인 정책에 대 한 사용자당 Skype 할당</span><span class="sxs-lookup"><span data-stu-id="72274-119">Assign per-user Skype for Business Online policies with PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="72274-120">기타 참고 항목</span><span class="sxs-lookup"><span data-stu-id="72274-120">See also</span></span>

[<span data-ttu-id="72274-121">PowerShell로 Microsoft 365 관리</span><span class="sxs-lookup"><span data-stu-id="72274-121">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="72274-122">Microsoft 365 용 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="72274-122">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="72274-123">비즈니스용 Skype Online PowerShell cmdlet 참조자료</span><span class="sxs-lookup"><span data-stu-id="72274-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

