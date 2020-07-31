---
title: Microsoft 365 IdFix 도구 다운로드 및 실행
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Priority
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_HRCSetupAADConnectIDFixLM617036
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Microsoft 365에 동기화 하기 전에 Microsoft 365 IdFix 도구를 다운로드 및 실행하여 AD DS(Active Directory 도메인 서비스)를 정리하는 방법.
ms.openlocfilehash: beef13857ad00806cc3e62aedd7a1b3c48bfe4c0
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502663"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a><span data-ttu-id="c1059-103">Microsoft 365 IdFix 도구 다운로드 및 실행</span><span class="sxs-lookup"><span data-stu-id="c1059-103">Download and run the Microsoft 365 IdFix tool</span></span>

<span data-ttu-id="c1059-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="c1059-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="c1059-105">IdFix는 Microsoft 365에 동기화 하기 전에 ADAS(Active Directory Domain Service) 도메인에서 복제 및 형식 문제 같은 오류를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-105">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Microsoft 365.</span></span> 
  
<span data-ttu-id="c1059-106">작업을 완료하려면 AD DS에서 사용자 그룹 및 연락처 개채를 능숙하게 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-106">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="c1059-107">이 작업을 완료할 수 없는 경우 몇 가지 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-107">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="c1059-108">이 방법이 더 쉬울 수도 있지만 시간이 더 걸리거나 다른 단점이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-108">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="c1059-109">다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-109">They are:</span></span>
  
- <span data-ttu-id="c1059-110">**IdFix 없이 디렉터리 동기화 실행**</span><span class="sxs-lookup"><span data-stu-id="c1059-110">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="c1059-111">IdFix 도구를 실행하지 않고 디렉터리를 동기화 할 수 있지만 권장되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-111">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="c1059-112">동기화하기 전에 오류를 수정하면 시간이 덜 들고 클라우드로의 전환이 더 원활해지기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-112">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="c1059-113">**컨설턴트 고용**</span><span class="sxs-lookup"><span data-stu-id="c1059-113">**Hire a consultant**</span></span> 

  <span data-ttu-id="c1059-114">전문가를 영입하면 사용자가 빠르게 시스템을 작동하고 디렉터리를 동기화하는데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-114">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="c1059-115">IdFix를 실행하는 데 필요한 사항</span><span class="sxs-lookup"><span data-stu-id="c1059-115">What you need to run IdFix</span></span>

<span data-ttu-id="c1059-116">IdFix를 작동시키는 가장 쉬운 방법은 AD DS 도메인에 가입한 컴퓨터에 설치하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-116">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="c1059-117">원할 경우 도메인 컨트롤러에서 실행할 수 있지만 필수 사항은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-117">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="c1059-118">IdFix 하드웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c1059-118">IdFix hardware requirements</span></span>

<span data-ttu-id="c1059-119">IdFix를 다운로드하는 컴퓨터는 다음과 같은 하드웨어 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-119">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="c1059-120">4GB RAM</span><span class="sxs-lookup"><span data-stu-id="c1059-120">4 GB RAM</span></span>
- <span data-ttu-id="c1059-121">2GB 하드 드라이브 용량</span><span class="sxs-lookup"><span data-stu-id="c1059-121">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="c1059-122">IdFix 소프트웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c1059-122">IdFix software requirements</span></span>

<span data-ttu-id="c1059-123">IdFix를 다운로드하는 컴퓨터는 Microsoft 365에 사용자를 동기화 하고자 하는 동일한 AD DS 도메인에 가입되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-123">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Microsoft 365.</span></span> 

<span data-ttu-id="c1059-124">또한 이 컴퓨터에는 .NET Framework 4.0이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-124">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="c1059-125">Windows Server 2008 이후 버전을 실행하는 경우라면 .NET Framework도 이미 설치되어 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-125">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="c1059-126">없는 경우 [다운로드 센터 또는 Windows Update를 사용하여 .NET 4.0를 다운로드](https://go.microsoft.com/fwlink/p/?LinkId=400475) 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-126">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="c1059-127">IdFix 권한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c1059-127">IdFix permissions requirements</span></span>

<span data-ttu-id="c1059-128">IdFix를 실행하는 데 사용하는 사용자 계정은 AD DS에 읽고 쓰는 액세스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-128">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="c1059-129">사용자 계정이 이러한 요구 사항을 충족하는지 여부를 모르거나 확인 방법을 몰라도 여전히 IdFix를 설치하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-129">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="c1059-130">사용자 계정에 적절한 권한이 없는 경우 IdFix를 실행하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-130">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="c1059-131">IdFix 다운로드 및 추출</span><span class="sxs-lookup"><span data-stu-id="c1059-131">Download and extract IdFix</span></span>

<span data-ttu-id="c1059-132">이 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-132">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="c1059-133">IdFix 도구를 설치하려는 컴퓨터에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-133">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="c1059-134">[IdFix DirSync 오류 수정 관리 도구](https://github.com/microsoft/idfix) 사이트로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-134">Go to the [IdFix DirSync Error Remediation Tool](https://github.com/microsoft/idfix) site.</span></span>
    
3. <span data-ttu-id="c1059-135">**ClickOnce 시작** 섹션에서 **시작**을 클릭하여 zip 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-135">Click **launch** in the **ClickOnce Launch** section to download the zip file.</span></span> <span data-ttu-id="c1059-136">Zip 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-136">Open the zip file.</span></span>
    
4. <span data-ttu-id="c1059-137">**IdFix** 창에서 **추출**을 선택한 다음 **모두 추출**합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-137">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="c1059-138">기본적으로 IdFix는 `C:\Users\<your user name>\Documents\IdFix`에 추출됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-138">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
5. <span data-ttu-id="c1059-139">**추출**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-139">Choose **Extract**.</span></span>

<span data-ttu-id="c1059-140">해당 버전의 Windows와 인터넷 브라우저에 따라 단계가 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-140">Your steps might vary based on your version of Windows and your Internet browser.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="c1059-141">IdFix 도구 실행</span><span class="sxs-lookup"><span data-stu-id="c1059-141">Run the IdFix tool</span></span>

<span data-ttu-id="c1059-142">IdFix를 다운로드 하 고 추출한 후 이를 실행하여 AD DS 도메인의 문제를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-142">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="c1059-143">AD DS 도메인에 읽기/쓰기 액세스 권한이 있는 계정을 사용하여 IdFix를 설치한 컴퓨터에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-143">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="c1059-144">파일 탐색기에서 IdFix를 설치한 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-144">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="c1059-145">추출 중에 기본 폴더를 선택한 경우 `C:\Users\<your user name>\Documents\IdFix`으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-145">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="c1059-146">**IdFix.exe**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-146">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="c1059-147">기본적으로 IdFix에서는 다중 테넌트 규칙 집합을 사용하여 디렉터리의 항목을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-147">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="c1059-148">이 규칙 집합은 대부분의 Microsoft 365 고객에게 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-148">This is the right rule set for most Microsoft 365 customers.</span></span> <span data-ttu-id="c1059-149">그렇지만 Microsoft 365 전용 또는 ITAR(International Traffic in Arms Regulations) 고객인 경우 전용 규칙 집합을 대신 사용하도록 IdFix를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-149">However, if you are a Microsoft 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="c1059-150">본인이 어떤 유형의 고객인지 잘 모를 경우 이 단계를 건너뛰어도 무방합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-150">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="c1059-151">규칙 집합을 전용으로 설정하려면 메뉴 모음에서 기어 아이콘을 클릭하고 **전용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-151">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="c1059-152">**쿼리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-152">Choose **Query**.</span></span>
    
    ![IdFix에서 쿼리를 선택합니다.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="c1059-154">기본적으로 IdFix는 전체 디렉터리에서 오류를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-154">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="c1059-155">디렉터리의 크기에 따라 쿼리를 실행하는 데 다소 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-155">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="c1059-156">도구의 기본 창 아래쪽에서 진행률을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-156">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="c1059-157">**취소**를 클릭한 경우 맨 처음부터 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-157">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="c1059-158">IdFix가 쿼리를 완료하고 디렉터리에 오류가 없으면 계속해서 디렉터리를 동기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-158">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="c1059-159">디렉터리에 문제가 있는 경우 먼저 수정한 후 동기화하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="c1059-160">자세한 정보는 [Microsoft 365에 대한 디렉터리 속성 준비](prepare-directory-attributes-for-synch-with-idfix.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1059-160">See [prepare directory attributes for synchronization with Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="c1059-161">동기화 하기 전에 오류를 반드시 수정해야 하는 것은 아니지만 적어도 IdFix에서 반환한 오류를 모두 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="c1059-162">각각의 오류는 도구의 주 창에서 개별 행으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="c1059-163">**업데이트** 열에 표시되는 제안 변경 내용에 동의하는 경우 **작업** 열에서 IdFix를 통해 구현할 변경 내용을 선택하고 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="c1059-164">**적용**을 클릭하면 도구에서 디렉터리에 변경 내용을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="c1059-165">업데이트를 할 때마다 **적용**을 클릭할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="c1059-166">대신 **적용**을 클릭하기 전에 몇 가지 오류를 수정하면 IdFix에서 모든 오류가 동시에 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="c1059-167">오류 유형이 나열된 열의 맨 위에서 **오류**를 클릭하여 오류 유형을 기준으로 오류를 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="c1059-168">한 가지 전략은 동일한 유형의 모든 오류를 수정하는 것입니다. 예를 들어 모든 중복 항목을 먼저 수정한 다음 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="c1059-169">그런 다음 문자 형식 오류를 수정하고 적용하는 방식으로 계속 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="c1059-170">변경 내용을 적용할 때마다 IdFix 도구에서는 사용자가 실수한 경우 변경을 실행 취소하는 데 사용할 수 있는 별도의 로그 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="c1059-171">[transaction log](idfix-transaction-log.md)는 IdFix를 추출한 폴더에 저장 됩니다(기본적으로 _C:\Users\<your user name>\Documents\IdFix_).</span><span class="sxs-lookup"><span data-stu-id="c1059-171">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![IdFix의 오류 수정](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="c1059-173">디렉터리를 모두 변경한 후에는 IdFix를 다시 실행하여 수정한 내용이 새로운 오류를 발생하지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-173">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="c1059-174">이러한 단계를 필요한 만큼 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-174">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="c1059-175">동기화하기 전에 이 프로세스를 몇 번 진행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1059-175">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="c1059-176">IdFx에 대한 추가 리소스</span><span class="sxs-lookup"><span data-stu-id="c1059-176">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="c1059-177">IdFix 제외 및 지원 개체 및 특성</span><span class="sxs-lookup"><span data-stu-id="c1059-177">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="c1059-178">Microsoft 365 IdFix 트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="c1059-178">Microsoft 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
