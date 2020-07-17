---
title: Microsoft 365 IdFix 도구 다운로드 및 실행
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
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
description: Microsoft 365로 동기화 하기 전에 AD DS (Active Directory 도메인 서비스)를 정리 하는 데 도움이 되는 Microsoft 365 IdFix 도구를 다운로드 하 고 실행 하는 방법을 설명 합니다.
ms.openlocfilehash: c4df63e6162b1d53cb7a45f046542443177b25ff
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774863"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a><span data-ttu-id="ca413-103">Microsoft 365 IdFix 도구 다운로드 및 실행</span><span class="sxs-lookup"><span data-stu-id="ca413-103">Download and run the Microsoft 365 IdFix tool</span></span>

<span data-ttu-id="ca413-104">*이 문서는 Microsoft 365 Enterprise 및 Office 365 Enterprise에 모두 적용 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="ca413-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="ca413-105">IdFix는 Microsoft 365으로 동기화 하기 전에 AD DS (Active Directory 도메인 서비스) 도메인의 중복 및 서식 문제와 같은 오류를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-105">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Microsoft 365.</span></span> 
  
<span data-ttu-id="ca413-106">이 작업을 성공적으로 완료 하려면 AD DS에서 사용자, 그룹 및 연락처 개체를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-106">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="ca413-107">이 작업을 완료할 수 없는 경우에는 몇 가지 다른 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-107">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="ca413-108">이러한 방법을 사용 하는 것이 쉬울 수도 있지만 더 오래 걸리거나 다른 단점이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-108">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="ca413-109">해당 지식 영역은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-109">They are:</span></span>
  
- <span data-ttu-id="ca413-110">**IdFix를 실행 하지 않고 디렉터리 동기화 실행**</span><span class="sxs-lookup"><span data-stu-id="ca413-110">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="ca413-111">IdFix 도구를 사용 하지 않고 디렉터리를 동기화 할 수는 있지만 권장 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-111">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="ca413-112">동기화 하기 전에 오류를 수정 하면 시간이 더 오래 걸리고 클라우드로 보다 원활한 전환이 제공 되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-112">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="ca413-113">**컨설턴트 고용**</span><span class="sxs-lookup"><span data-stu-id="ca413-113">**Hire a consultant**</span></span> 

  <span data-ttu-id="ca413-114">전문가의 도움을 받아 사용자의 작업을 빠르게 수행 하 고 디렉터리를 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-114">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="ca413-115">IdFix를 실행 하는 데 필요한 사항</span><span class="sxs-lookup"><span data-stu-id="ca413-115">What you need to run IdFix</span></span>

<span data-ttu-id="ca413-116">IdFix를 설치 하 고 실행 하는 가장 쉬운 방법은 AD DS 도메인에 가입 된 컴퓨터에 다운로드 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-116">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="ca413-117">필요한 경우 도메인 컨트롤러에서이를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-117">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="ca413-118">IdFix 하드웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ca413-118">IdFix hardware requirements</span></span>

<span data-ttu-id="ca413-119">IdFix를 다운로드 하는 컴퓨터는 다음과 같은 최소 하드웨어 요구 사항을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-119">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="ca413-120">4GB RAM</span><span class="sxs-lookup"><span data-stu-id="ca413-120">4 GB RAM</span></span>
- <span data-ttu-id="ca413-121">2gb의 하드 디스크 공간</span><span class="sxs-lookup"><span data-stu-id="ca413-121">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="ca413-122">IdFix 소프트웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ca413-122">IdFix software requirements</span></span>

<span data-ttu-id="ca413-123">IdFix를 다운로드 하는 컴퓨터는 사용자를 Microsoft 365와 동기화 하려는 동일한 AD DS 도메인에 가입 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-123">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Microsoft 365.</span></span> 

<span data-ttu-id="ca413-124">또한 컴퓨터에 .NET Framework 4.0이 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-124">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="ca413-125">Windows Server 2008 이상 버전을 실행 하는 경우에는 .NET Framework가 이미 설치 되어 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-125">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="ca413-126">그렇지 않으면 [다운로드 센터에서](https://go.microsoft.com/fwlink/p/?LinkId=400475) 또는 Windows Update를 사용 하 여 .net 4.0을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-126">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="ca413-127">IdFix 사용 권한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ca413-127">IdFix permissions requirements</span></span>

<span data-ttu-id="ca413-128">IdFix를 실행 하는 데 사용 하는 사용자 계정에는 AD DS 도메인에 대 한 읽기 및 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-128">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="ca413-129">사용자 계정이 이러한 요구 사항을 충족 하 고 있는지 확인 하는 방법을 모르는 경우에도 IdFix를 다운로드 하 고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-129">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="ca413-130">사용자 계정에 적절 한 사용 권한이 없는 경우에는 IdFix에서 오류를 실행 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-130">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="ca413-131">IdFix 다운로드 및 압축 풀기</span><span class="sxs-lookup"><span data-stu-id="ca413-131">Download and extract IdFix</span></span>

<span data-ttu-id="ca413-132">다음 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-132">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="ca413-133">IdFix 도구를 실행 하려는 컴퓨터에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-133">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="ca413-134">[Idfix DirSync 오류 수정 도구](https://github.com/microsoft/idfix) 사이트로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-134">Go to the [IdFix DirSync Error Remediation Tool](https://github.com/microsoft/idfix) site.</span></span>
    
3. <span data-ttu-id="ca413-135">**ClickOnce 실행** 섹션에서 **시작** 을 클릭 하 여 zip 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-135">Click **launch** in the **ClickOnce Launch** section to download the zip file.</span></span> <span data-ttu-id="ca413-136">Zip 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-136">Open the zip file.</span></span>
    
4. <span data-ttu-id="ca413-137">**Idfix** 창에서 **추출을**선택한 다음 **모두 압축을 풉니다**.</span><span class="sxs-lookup"><span data-stu-id="ca413-137">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="ca413-138">기본적으로 IdFix는로 추출 됩니다 `C:\Users\<your user name>\Documents\IdFix` .</span><span class="sxs-lookup"><span data-stu-id="ca413-138">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
5. <span data-ttu-id="ca413-139">**추출**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-139">Choose **Extract**.</span></span>

<span data-ttu-id="ca413-140">현재 버전의 Windows와 인터넷 브라우저에 따라 단계가 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-140">Your steps might vary based on your version of Windows and your Internet browser.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="ca413-141">IdFix 도구 실행</span><span class="sxs-lookup"><span data-stu-id="ca413-141">Run the IdFix tool</span></span>

<span data-ttu-id="ca413-142">IdFix를 다운로드 하 고 추출한 후에는이를 실행 하 여 AD DS 도메인에서 문제를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-142">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="ca413-143">AD DS 도메인에 대 한 읽기/쓰기 권한이 있는 계정을 사용 하 여 IdFix를 다운로드 한 컴퓨터에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-143">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="ca413-144">파일 탐색기에서 IdFix를 추출한 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-144">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="ca413-145">추출 중에 기본 폴더를 선택한 경우로 이동 `C:\Users\<your user name>\Documents\IdFix` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-145">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="ca413-146">**IdFix.exe**를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-146">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="ca413-147">기본적으로 IdFix에서는 다중 테 넌 트 규칙 집합을 사용 하 여 디렉터리의 항목을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-147">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="ca413-148">이는 대부분의 Microsoft 365 고객에 게 적합 한 규칙 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-148">This is the right rule set for most Microsoft 365 customers.</span></span> <span data-ttu-id="ca413-149">단, ITAR (무장 규정) 고객의 Microsoft 365 전용 또는 국제 트래픽의 경우 대신 전용 규칙 집합을 사용 하도록 IdFix를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-149">However, if you are a Microsoft 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="ca413-150">어떤 종류의 고객 인지 잘 모르는 경우이 단계를 무시 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-150">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="ca413-151">규칙 집합을 전용으로 설정 하려면 메뉴 모음에서 톱니 바퀴 아이콘을 클릭 한 다음 **전용**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-151">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="ca413-152">**쿼리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-152">Choose **Query**.</span></span>
    
    ![IdFix에서 쿼리를 선택 합니다.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="ca413-154">기본적으로 IdFix는 전체 디렉터리에서 오류를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-154">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="ca413-155">디렉터리 크기에 따라 쿼리를 실행 하는 데 다소 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-155">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="ca413-156">도구 주 창의 아래쪽에 있는 진행률을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-156">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="ca413-157">**취소**를 클릭 한 경우 처음부터 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-157">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="ca413-158">IdFix가 쿼리를 완료 하 고 나면 오류가 없으면 디렉터리를 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-158">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="ca413-159">디렉터리에 오류가 있는 경우 동기화 하기 전에 문제를 해결 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="ca413-160">자세한 내용은 [prepare directory attributes For Microsoft 365를](prepare-directory-attributes-for-synch-with-idfix.md) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca413-160">See [prepare directory attributes for synchronization with Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="ca413-161">동기화 하기 전에 오류를 반드시 수정 해야 하는 것은 아니며, IdFix에서 반환한 오류를 모두 검토 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="ca413-162">각 오류는 도구의 주 창에 별도의 행으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="ca413-163">**업데이트** 열에 제안 된 변경 내용에 동의 하는 경우 **작업** 열에서 idfix에서 변경을 구현 하기 위해 수행할 작업을 선택 하 고 **적용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="ca413-164">**적용**을 클릭 하면 도구에서 디렉터리를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="ca413-165">각 업데이트 후에는 **적용** 을 클릭할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="ca413-166">대신, IdFix를 클릭 하기 전에 몇 가지 오류를 **수정 하 여** 이를 모두 동시에 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="ca413-167">오류 유형을 나열 하는 열 맨 위에 있는 **오류** 를 클릭 하 여 오류 유형별로 오류를 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="ca413-168">한 가지 전략은 동일한 유형의 모든 오류를 수정 하는 것입니다. 예를 들어 먼저 모든 중복 항목을 수정 하 고 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="ca413-169">그런 다음 문자 서식 오류 등을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="ca413-170">IdFix 도구는 변경 내용을 적용할 때마다 사용자가 실수 한 경우 변경 내용을 취소 하는 데 사용할 수 있는 별도의 로그 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="ca413-171">[트랜잭션 로그](idfix-transaction-log.md) 는 idfix를 추출한 폴더 (기본적으로 _C:\Users \<your user name> \documents\idfix_ )에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-171">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![IdFix에서 오류를 수정.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="ca413-173">디렉터리를 변경한 후에는 IdFix를 다시 실행 하 여 수정한 내용에 새 오류가 발생 하지 않았는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-173">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="ca413-174">필요한 횟수 만큼 이러한 단계를 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-174">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="ca413-175">동기화 하기 전에 몇 번까지 프로세스를 진행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ca413-175">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="ca413-176">IdFix에 대 한 추가 리소스</span><span class="sxs-lookup"><span data-stu-id="ca413-176">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="ca413-177">IdFix 제외 및 지원 개체/특성</span><span class="sxs-lookup"><span data-stu-id="ca413-177">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="ca413-178">Microsoft 365 IdFix 트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="ca413-178">Microsoft 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
