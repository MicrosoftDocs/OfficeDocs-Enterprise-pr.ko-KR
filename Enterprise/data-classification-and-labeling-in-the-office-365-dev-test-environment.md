---
title: Office 365 개발/테스트 환경에서 데이터 분류 및 레이블 지정
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: '요약: Office 365 개발/테스트 환경에서 Azure Information Protection (aip) 클라이언트를 사용 하 여 데이터 분류 및 레이블을 구성 하 고 보여 줍니다.'
ms.openlocfilehash: 66bdbb74ae88e10d5aa4fce2173f9a2b88a15e9b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490071"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="afa80-103">Office 365 개발/테스트 환경에서 데이터 분류 및 레이블 지정</span><span class="sxs-lookup"><span data-stu-id="afa80-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="afa80-104">**요약:** Office 365 개발/테스트 환경에서 Azure Information Protection (aip) 클라이언트를 사용 하 여 데이터 분류 및 레이블을 구성 하 고 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="afa80-105">Azure Information Protection 클라이언트를 사용 하 여 문서를 Office 365의 SharePoint Online 폴더에 업로드 하기 전에 분류할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-105">The Azure Information Protection client lets you classify a document before you upload it to a SharePoint Online folder in Office 365.</span></span> <span data-ttu-id="afa80-106">이 문서의 지침을 사용 하 여 Azure Information Protection 클라이언트를 설치 하 고 데이터 분류를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-106">With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification.</span></span> <span data-ttu-id="afa80-107">자세한 내용은 [Azure information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="afa80-107">For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="afa80-108">[여기](http://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="afa80-109">1 단계: Office 365 개발/테스트 환경 구축</span><span class="sxs-lookup"><span data-stu-id="afa80-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="afa80-110">[Office 365 개발/테스트 환경의](office-365-dev-test-environment.md)지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="afa80-111">2 단계: Azure Information Protection 평가판 구독 추가</span><span class="sxs-lookup"><span data-stu-id="afa80-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="afa80-112">이 단계에서는 Azure Information Protection을 Office 365 개발/테스트 환경에 추가 하 고 사용자 계정에 대해 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-112">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts.</span></span> <span data-ttu-id="afa80-113">[Office 365 및 EMS 개발/테스트 환경을](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)구성한 경우에는이 단계를 건너뛰십시오.</span><span class="sxs-lookup"><span data-stu-id="afa80-113">If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase.</span></span> <span data-ttu-id="afa80-114">Enterprise Mobility Suite 평가판 구독에는 Azure Information Protection 라이선스가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-114">The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="afa80-115">먼저 Azure Information Protection 평가판 구독에 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="afa80-116">Azure Information Protection 평가판 구독 등록</span><span class="sxs-lookup"><span data-stu-id="afa80-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="afa80-117">Internet Explorer 또는 브라우저에서 Office 365 전역 관리자 [http://admin.microsoft.com](http://admin.microsoft.com) 계정으로 이동 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-117">In Internet Explorer or your browser, go to [http://admin.microsoft.com](http://admin.microsoft.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="afa80-118">**Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="afa80-119">Office 365 관리 탭의 왼쪽 탐색 창에서 **결제 > Purchase services**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="afa80-120">**서비스 구매** 페이지에서 **Azure Information Protection Premium P2** 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-120">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item.</span></span> <span data-ttu-id="afa80-121">마우스를 해당 사용자에 게 가리키고 **무료 평가판 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-121">Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="afa80-122">**주문 확인** 페이지에서 **지금 평가판 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="afa80-123">**주문 접수** 페이지에서 **계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="afa80-124">다음으로 모든 사용자 계정에 대해 Azure Information Protection 라이선스를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="afa80-125">Microsoft 365 관리 센터 탭에서 **사용자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-125">On the Microsoft 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="afa80-126">사용자 계정 목록에서 전역 관리자 계정을 선택 하 고 **제품 라이선스**에 대해 **편집** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="afa80-127">**Azure Information Protection Premium P2** 에 대 한 제품 라이선스를 \*\*\*\* 사용 하도록 설정 하 고 **저장을** 클릭 한 후 **닫기를** 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="afa80-128">다른 사용자 계정에 대해 2-3 단계를 반복 합니다 (사용자 1-사용자 5).</span><span class="sxs-lookup"><span data-stu-id="afa80-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="afa80-129">지금까지 Office 365 개발/테스트 환경에는 다음이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="afa80-130">Office 365 E5 Enterprise 및 Azure Information Protection 평가판 구독</span><span class="sxs-lookup"><span data-stu-id="afa80-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="afa80-131">모든 사용자 계정을 사용 하 여 Office 365 E5 Enterprise 및 Azure Information Protection을 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="afa80-132">3 단계: 데이터 분류 시연</span><span class="sxs-lookup"><span data-stu-id="afa80-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="afa80-133">이 단계에서는 azure information protection 클라이언트 및 기본 azure information protection 정책을 사용 하 여 데이터 분류를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="afa80-134">시뮬레이트된 enterprise Office 365 개발/테스트 환경을 사용 하는 경우 먼저 CLIENT1에 Office 2016을 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="afa80-135">브라우저를 사용 하 여 [Azure 포털로](http://portal.azure.com)이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="afa80-136">**리소스 그룹 >** [리소스 그룹 이름] **> CLIENT1 > Connect**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="afa80-137">CLIENT1에서 Internet Explorer를 실행 하 고에서 Office 포털로 [http://admin.microsoft.com](http://admin.microsoft.com)이동한 다음 User5 계정 이름 및 암호를 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="afa80-138">**Microsoft Office 홈** 탭에서 **Office 2016 설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="afa80-139">메시지가 표시 되 면 다운로드를 실행 하 고 사용자 계정 컨트롤에 따라 메시지가 표시 되 면 **예** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-139">Run the download when prompted and click **Yes** when prompted by User Account Control.</span></span> <span data-ttu-id="afa80-140">Office가 설치 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-140">Wait for Office to install.</span></span> <span data-ttu-id="afa80-141">완료 되 면 **닫기를** 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-141">When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="afa80-142">다음으로 Azure Information Protection 클라이언트를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="afa80-143">브라우저나 Internet Explorer에서 [Microsoft Azure Information Protection 다운로드 페이지로](https://www.microsoft.com/download/details.aspx?id=53018)이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="afa80-144">간단한 버전의 Office 365 개발/테스트 환경을 사용 하는 경우 로컬 컴퓨터에서 브라우저를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="afa80-145">시뮬레이트된 enterprise Office 365 개발/테스트 환경을 사용 하는 경우에는 CLIENT1에서 Internet Explorer를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="afa80-146">**Microsoft Azure Information Protection** 다운로드 페이지에서 **다운로드**를 클릭 하 고 **azinfoprotection.exe**을 클릭 한 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="afa80-147">메시지가 표시 되 면 azinfoprotection.exe를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="afa80-148">**Azure Information Protection 클라이언트 설치** 상자에서 **I agree (동의**)를 클릭 한 다음 사용자 계정 컨트롤에 따라 확인 메시지가 표시 되 면 **예** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="afa80-149">**성공적으로 완료 됨** 상자에서 **닫기를 클릭 합니다.**</span><span class="sxs-lookup"><span data-stu-id="afa80-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="afa80-150">다음으로 문서 분류를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="afa80-151">작업 표시줄에서 **Word** 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="afa80-152">메시지가 표시 되 면 User5 계정 이름 및 암호를 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="afa80-153">CLIENT1에 Office 2016을 설치한 경우 첫 번째 **작업** 상자에서 **수락**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="afa80-154">**새 문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="afa80-155">**홈** 탭에 있는 리본 메뉴의 **보호** 구역과 문서 분류의 행을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="afa80-156">새 문서에서 텍스트를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="afa80-157">**파일 > 저장**을 클릭 하 고 이름 **BeforeAIP**를 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="afa80-158">문서 클래스의 행에서 **Secret**의 아래쪽 화살표를 클릭 하 고 **모든 회사**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="afa80-159">**파일 > 다른 이름으로 저장**을 클릭 하 고 **afteraip**를 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="afa80-160">작업 표시줄에서 **파일 탐색기** 를 클릭 한 다음 **문서** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="afa80-161">**BeforeAIP** 및 **afteraip** 문서의 다양 한 파일 크기를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-161">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents.</span></span> <span data-ttu-id="afa80-162">이 문서에는 분류 정보가 있기 때문에 afteraip 문서가 더 커집니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-162">The AfterAIP document is larger because it has the classification information.</span></span>
    
<span data-ttu-id="afa80-163">다음으로, 모든 사용자가 지원 사이트 모음에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="afa80-164">**Microsoft Office 홈** 탭에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="afa80-165">**SharePoint** 탭에서 **사이트 모음 지원을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="afa80-166">오른쪽 위에 있는 **설정** 아이콘을 클릭 한 다음 **공유를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="afa80-167">**공유 ' 지원 사이트 모음 '** 에서 **고급**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="afa80-168">SharePoint 그룹 목록에서 **사이트 모음 구성원 지원을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="afa80-169">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="afa80-170">**공유 ' 지원 사이트 모음 '** 에 **모든 사람**을 입력 하 고 **외부 사용자를 제외한 모든 사람**을 클릭 한 다음 공유를 클릭 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="afa80-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="afa80-171">**사용자 및 그룹** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="afa80-172">다음으로, User5 계정으로 로그인 하 고 aip로 보호 된 문서를 지원 사이트 모음의 문서 폴더에 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="afa80-173">**Microsoft Office 홈** 탭의 오른쪽 위에서 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="afa80-174">[http://admin.microsoft.com](http://admin.microsoft.com)으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-174">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="afa80-175">**Office 365 로그인** 페이지에서 User5 계정 이름을 클릭 하 고 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-175">On the **Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="afa80-176">**Microsoft Office 홈** 탭에서 **SharePoint > 지원 사이트 모음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="afa80-177">**문서**, **업로드**, **afteraip** 문서를 차례로 클릭 한 다음 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="afa80-178">지원 사이트 모음의 문서 폴더에 afteraip가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="afa80-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="afa80-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="afa80-179">See Also</span></span>

[<span data-ttu-id="afa80-180">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="afa80-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="afa80-181">Office 365 및 EMS 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="afa80-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="afa80-182">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="afa80-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


