---
title: Office 365 PowerShell을 사용하여 비즈니스용 Skype Online 관리
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 요약:Office 365 PowerShell을 사용하여 비즈니스용 Skype 온라인 정책, 사용자 단위 정책 및 모임 설정을 관리합니다.
ms.openlocfilehash: 4444483776141a3aa1f6e53b2f9bdcd7a5d28e1d
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106209"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="02f98-103">Office 365 PowerShell을 사용하여 비즈니스용 Skype Online 관리</span><span class="sxs-lookup"><span data-stu-id="02f98-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

<span data-ttu-id="02f98-104">비즈니스용 Skype 온라인 관리자의 기본 작업 중 하나는 정책을 관리하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="02f98-104">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="02f98-105">Office 365 관리 센터에서 이러한 작업 중 일부를 수행할 수 있지만 Office 365 PowerShell에서 훨씬 더 빠르고 쉽게 수행할 수 있는 작업도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02f98-105">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="02f98-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="02f98-106">Before you start</span></span>

<span data-ttu-id="02f98-107">[비즈니스용 Skype Online 커넥터 모듈](https://www.microsoft.com/download/details.aspx?id=39366)을 다운로드 하 여 설치한 다음 메시지가 표시 되 면 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="02f98-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="02f98-108">비즈니스용 Skype 온라인 관리자 계정 이름 및 암호를 사용 하 여 연결</span><span class="sxs-lookup"><span data-stu-id="02f98-108">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="02f98-109">Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="02f98-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="02f98-110">**Windows PowerShell 자격 증명 요청** 대화 상자에서 비즈니스용 Skype Online 관리자 계정 이름 및 암호를 입력 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="02f98-110">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="02f98-111">Multi-factor authentication을 사용 하 여 비즈니스용 Skype Online 관리자 계정을 사용 하 여 연결</span><span class="sxs-lookup"><span data-stu-id="02f98-111">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="02f98-112">Windows PowerShell 명령 프롬프트를 열고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="02f98-112">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="02f98-113">**CsOnlineSession** 명령에서 메시지가 표시 되 면 비즈니스용 Skype Online 관리자 계정 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="02f98-113">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="02f98-114">**계정에 로그인** 대화 상자에서 비즈니스용 Skype Online 관리자 암호를 입력 하 고 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="02f98-114">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="02f98-115">**계정에 로그인** 대화 상자의 지침에 따라 확인 코드와 같은 추가 인증 정보를 제공 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="02f98-115">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="02f98-116">자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="02f98-116">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="02f98-117">Office 365 PowerShell을 사용 하 여 온라인 비즈니스 정책을 용 Skype 관리</span><span class="sxs-lookup"><span data-stu-id="02f98-117">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="02f98-118">Office 365 powershell 비즈니스 온라인 정책에 대 한 사용자 당 Skype 할당</span><span class="sxs-lookup"><span data-stu-id="02f98-118">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="02f98-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="02f98-119">See also</span></span>

[<span data-ttu-id="02f98-120">Office 365 PowerShell 사용한 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="02f98-120">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="02f98-121">Office 365 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="02f98-121">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="02f98-122">비즈니스용 Skype PowerShell cmdlet 참조</span><span class="sxs-lookup"><span data-stu-id="02f98-122">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

