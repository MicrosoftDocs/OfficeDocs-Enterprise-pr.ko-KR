---
title: Office 365 IdFix 도구 설치 및 실행
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: office 365 idfix 도구를 설치 하 고 실행 하 여 office 365로 동기화 하기 전에 active directory를 정리 하는 방법을 알아봅니다.
ms.openlocfilehash: a35b2a476f2b30eccc955b980eda6315b146af27
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085407"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="c6548-103">Office 365 IdFix 도구 설치 및 실행</span><span class="sxs-lookup"><span data-stu-id="c6548-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="c6548-104">idfix는 Office 365로 동기화 하기 전에 디렉터리의 중복 및 서식 문제와 같은 오류를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="c6548-105">이 작업을 성공적으로 완료 하려면 Active Directory에서 사용자, 그룹 및 연락처 개체를 사용 하 여 작업 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="c6548-p101">이 작업을 완료할 수 없는 경우에는 몇 가지 다른 작업을 수행할 수 있습니다. 이러한 방법을 사용 하는 것이 쉬울 수도 있지만 더 오래 걸리거나 다른 단점이 있을 수 있습니다. 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p101">If you can't complete this task, there are a couple of other things you can do. These methods might be easier, but they might also take longer or have other drawbacks. They are:</span></span>
  
- <span data-ttu-id="c6548-p102">**idfix를 실행 하지 않고 디렉터리 동기화를 실행 합니다.** idfix 도구를 실행 하지 않고 디렉터리를 동기화 할 수는 있지만 권장 하지는 않습니다. 동기화 하기 전에 오류를 수정 하면 시간이 더 오래 걸리고 클라우드로 보다 원활한 전환이 제공 되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p102">**Run directory synchronization without running IdFix.** You can synchronize your directory without running the IdFix tool, but we don't recommend it. Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="c6548-p103">**컨설턴트를 고용합니다.** 전문가를 영입하면 사용자가 빠르게 시스템을 작동하고 디렉터리를 동기화하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p103">**Hire a consultant.** Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="c6548-114">IdFix를 실행하는 데 필요한 사항</span><span class="sxs-lookup"><span data-stu-id="c6548-114">What you need to run IdFix</span></span>

<span data-ttu-id="c6548-p104">idfix를 다운로드 하 고 실행 하는 가장 쉬운 방법은 도메인에 가입 된 컴퓨터에 설치 하는 것입니다. 필요한 경우 도메인 컨트롤러에서이를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p104">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain. You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="c6548-117">IdFix 하드웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c6548-117">IdFix hardware requirements</span></span>

<span data-ttu-id="c6548-118">idfix를 설치 하는 컴퓨터는 다음과 같은 최소 하드웨어 요구 사항을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-118">The computer where you install IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="c6548-119">4GB RAM</span><span class="sxs-lookup"><span data-stu-id="c6548-119">4 GB RAM</span></span>
- <span data-ttu-id="c6548-120">2gb의 하드 디스크 공간</span><span class="sxs-lookup"><span data-stu-id="c6548-120">2 GB of hard disk space</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="c6548-121">IdFix 소프트웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c6548-121">IdFix software requirements</span></span>

<span data-ttu-id="c6548-p105">idfix를 설치 하는 컴퓨터는 사용자를 Office 365와 동기화 하려는 동일한 Active Directory 도메인에 가입 되어 있어야 합니다. 또한 컴퓨터에 .net Framework 4.0이 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p105">The computer where you install IdFix needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365. The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="c6548-p106">windows server 2008 또는 windows server 2012를 실행 하는 경우에는 .net Framework가 이미 설치 되어 있을 것입니다. 그렇지 않으면 [다운로드 센터에서](https://go.microsoft.com/fwlink/p/?LinkId=400475) 또는 Windows Update를 통해 .net 4.0을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p106">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed. If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or via Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="c6548-126">IdFix 권한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c6548-126">IdFix permissions requirements</span></span>

<span data-ttu-id="c6548-127">IdFix를 실행하는 데 사용하는 사용자 계정은 디렉터리에 대해 읽기/쓰기 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="c6548-p107">사용자 계정이 이러한 요구 사항을 충족 하는지 확인 하는 방법을 모르는 경우에도 idfix를 설치 하 고 실행할 수 있습니다. 사용자 계정에 적절 한 사용 권한이 없는 경우에는 idfix에서 오류를 실행 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p107">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix. If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="c6548-130">IdFix 설치</span><span class="sxs-lookup"><span data-stu-id="c6548-130">Install IdFix</span></span>

<span data-ttu-id="c6548-131">idfix를 설치 하려면 **idfix**를 다운로드 하 고 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-131">To install IdFix, download and unzip **IdFix.exe**:</span></span> 
  
1. <span data-ttu-id="c6548-132">IdFix 도구를 설치하려는 컴퓨터에 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="c6548-133">[idfix DirSync 오류 수정 도구](https://go.microsoft.com/fwlink/?linkid=867219)에 대 한 Microsoft 다운로드 사이트로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="c6548-134">**다운로드**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="c6548-135">메시지가 표시 되 면 **실행**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="c6548-p108">**WinZip 자동 추출** 대화 상자의 **폴더에 대 한 압축 풀기** 텍스트 상자에서 idfix 도구를 설치 하려는 위치를 입력 하거나 찾습니다. 기본적으로 idfix는에 `C:\Deployment Tools\`설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p108">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool. By default, IdFix is installed into `C:\Deployment Tools\`.</span></span> 
    
6. <span data-ttu-id="c6548-138">**압축 풀기를**선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="c6548-139">IdFix 도구 실행</span><span class="sxs-lookup"><span data-stu-id="c6548-139">Run the IdFix tool</span></span>

<span data-ttu-id="c6548-140">IdFix를 설치한 후 이 도구를 실행하여 디렉터리의 문제를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="c6548-141">해당 디렉터리에 대해 읽기/쓰기 액세스 권한이 있는 계정을 사용하여 IdFix를 설치한 컴퓨터에 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="c6548-p109">파일 탐색기에서 idfix를 설치한 위치로 이동 합니다. 설치 중에 기본 폴더를 선택한 경우로 이동 `C:\Deployment Tools\IdFix`합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p109">In File Explorer, go to the location where you installed IdFix. If you chose the default folder during installation, go to `C:\Deployment Tools\IdFix`.</span></span>
    
3. <span data-ttu-id="c6548-144">**IdFix.exe**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-144">Double-click **IdFix.exe**.</span></span> 
    
    ![idfix .exe 파일을 선택 합니다.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="c6548-p110">기본적으로 idfix에서는 다중 테 넌 트 규칙 집합을 사용 하 여 디렉터리의 항목을 테스트 합니다. 이는 대부분의 Office 365 고객에 게 적합 한 규칙 집합입니다. 그러나 Office 365 전용 또는 itar (arm 규정의 해외 트래픽) 고객의 경우에는 대신 전용 규칙 집합을 사용 하도록 idfix를 구성할 수 있습니다. 어떤 종류의 고객 인지 잘 모르는 경우이 단계를 무시 해도 됩니다. 규칙 집합을 전용으로 설정 하려면 메뉴 모음에서 톱니 바퀴 아이콘을 클릭 한 다음 **전용**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p110">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory. This is the right rule set for most Office 365 customers. However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead. If you aren't sure what type of customer you are, you can safely skip this step. To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="c6548-151">**쿼리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-151">Choose **Query**.</span></span>
    
    ![idfix에서 쿼리를 선택 합니다.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="c6548-153">기본적으로 IdFix는 전체 디렉터리에서 오류를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="c6548-p111">디렉터리 크기에 따라 쿼리를 실행 하는 데 다소 시간이 걸릴 수 있습니다. 도구 주 창의 아래쪽에 있는 진행률을 볼 수 있습니다. **취소**를 클릭 한 경우 처음부터 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p111">Depending on the size of your directory, running the query can take a while. You can watch the progress at the bottom of the tool's main window. If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![idfix 쿼리 및 오류 수입니다.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="c6548-p112">idfix에서 쿼리를 완료 한 후 오류가 없으면 디렉터리를 동기화 할 수 있습니다. 디렉터리에 오류가 있는 경우 동기화 하기 전에 문제를 해결 하는 것이 좋습니다. 오류 유형과 각 문제를 해결 하는 데 가장 적합 한 방법에 대 한 구체적인 정보를 보려면이 항목 끝부분에 있는 링크를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c6548-p112">After IdFix completes the query, you can go ahead and synchronize your directory if there are no errors. If there are errors in your directory, it is recommended that you fix them before you synchronize. If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="c6548-161">동기화하기 전에 오류를 반드시 수정해야 하는 것은 아니지만 적어도 IdFix에서 반환한 오류를 모두 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="c6548-162">각 오류는 도구의 주 창에 별도의 행으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="c6548-p113">**UPDATE** 열에 표시되는 제안 변경 내용에 동의하는 경우 **ACTION** 열에서 IdFix를 통해 구현할 변경 내용을 선택하고 **적용**을 클릭합니다. **적용**을 클릭하면 디렉터리가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p113">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**. When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="c6548-p114">각 업데이트 후에는 **적용** 을 클릭할 필요가 없습니다. 대신, idfix를 클릭 하기 전에 몇 가지 \*\*\*\* 오류를 수정 하 여이를 모두 동시에 변경할 수 있습니다. 오류 유형을 나열 하는 열 맨 위에 있는 **오류** 를 클릭 하 여 오류 유형별로 오류를 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p114">You don't have to click **Apply** after each update. Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time. You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="c6548-p115">한 가지 전략은 동일한 유형의 모든 오류를 수정 하는 것입니다. 예를 들어 먼저 모든 중복 항목을 수정 하 고 적용 합니다. 그런 다음 문자 서식 오류 등을 수정 합니다. idfix 도구는 변경 내용을 적용할 때마다 사용자가 실수 한 경우 변경 내용을 취소 하는 데 사용할 수 있는 별도의 로그 파일을 만듭니다. [트랜잭션 로그](idfix-transaction-log.md) 는 idfix를 설치한 폴더에 저장 됩니다.  _c:\deployment_ 도구 \ id 기본적으로 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p115">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them. Next, fix the character format errors, and so on. Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake. The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.  _C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![idfix에서 오류를 수정.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="c6548-p116">디렉터리를 변경한 후에는 idfix를 다시 실행 하 여 수정한 내용에 새 오류가 발생 하지 않았는지 확인 합니다. 필요한 횟수 만큼 이러한 단계를 반복할 수 있습니다. 동기화 하기 전에 몇 번까지 프로세스를 진행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p116">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors. You can repeat these steps as many times as you need to. It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="c6548-177">검색을 구체화하거나 오류를 보다 깊이 분석하려는 경우 IdFix로 어떤 작업을 할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="c6548-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="c6548-178">좀 더 자세한 정보는 다음 항목에서 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="c6548-p117">[idfix 도구를 사용 하 여 Office 365과 동기화 하기 위한 디렉터리 특성을 준비](prepare-directory-attributes-for-synch-with-idfix.md) 합니다. 이 도구를 설치한 후에는이 항목으로 이동 하 여 도구 실행에 대 한 자세한 지침, 발생 하는 일반적인 오류, 제안 되는 수정 작업, 예제 및 많은 오류가 발생 했을 때 수행 해야 하는 상황에 대 한 모범 사례를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6548-p117">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) . After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="c6548-181">참조: IdFix 제외 및 지원 개체/특성</span><span class="sxs-lookup"><span data-stu-id="c6548-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="c6548-182">참조: Office 365 IdFix 트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="c6548-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="c6548-183">동영상 교육</span><span class="sxs-lookup"><span data-stu-id="c6548-183">Video training</span></span>

<span data-ttu-id="c6548-184">자세한 내용은 LinkedIn 학습을 통해 제공 되는이과에서 [idfix 도구 설치 및 사용](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c6548-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

