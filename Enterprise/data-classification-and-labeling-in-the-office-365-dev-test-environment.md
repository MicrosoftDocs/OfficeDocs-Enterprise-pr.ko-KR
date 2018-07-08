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
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: '요약: 구성 및 시연 데이터 분류 하 고 Azure 정보 보호 (AIP) 클라이언트를 사용 하 여 Office 365 개발/테스트 환경에서 레이블을 지정 합니다.'
ms.openlocfilehash: f9674f5e2bac804f5bd23b5f67e733580c50450f
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188096"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="338fb-103">Office 365 개발/테스트 환경에서 데이터 분류 및 레이블 지정</span><span class="sxs-lookup"><span data-stu-id="338fb-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="338fb-104">**요약:** 구성 및 시연 데이터 분류 하 고 Azure 정보 보호 (AIP) 클라이언트를 사용 하 여 Office 365 개발/테스트 환경에서 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="338fb-p101">Azure 정보 보호 클라이언트를 사용 하면 Office 365의 SharePoint Online 폴더에 업로드 하기 전에 문서를 분류할 수 있습니다. 이 문서의 지침을 함께 Azure 정보 보호 클라이언트를 설치 및 데이터 분류를 시연 합니다. 자세한 내용은 [Azure 정보 보호](https://www.microsoft.com/cloud-platform/azure-information-protection)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="338fb-p101">The Azure Information Protection client allows you to classify a document before you upload it to a SharePoint Online folder in Office 365. With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification. For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="338fb-108">[여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="338fb-109">1 단계: Office 365 개발/테스트 환경을 구축합니다</span><span class="sxs-lookup"><span data-stu-id="338fb-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="338fb-110">[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)에 대 한 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="338fb-111">2 단계: Azure 정보 보호 평가판 구독 추가</span><span class="sxs-lookup"><span data-stu-id="338fb-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="338fb-p102">이 단계에서 Office 365 개발/테스트 환경에 Azure 정보 보호를 추가 하 고 사용자 계정에 대해 사용 하도록 설정 합니다. [Office 365와 EMS 개발/테스트 환경을](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)구성한 경우이 단계를 건너뜁니다. Enterprise 이동성 제품군 평가판 구독 Azure 정보 보호 라이선스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-p102">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts. If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase. The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="338fb-115">먼저, Azure 정보 보호 평가판 구독에 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="338fb-116">Azure 정보 보호 평가판 구독에 등록</span><span class="sxs-lookup"><span data-stu-id="338fb-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="338fb-117">Internet Explorer 또는 브라우저에서로 이동 [http://portal.office.com](http://portal.office.com) 와 Office 365 전역 관리자 계정을 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-117">In Internet Explorer or your browser, go to [http://portal.office.com](http://portal.office.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="338fb-118">**Microsoft Office 홈** 탭에서 **관리** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="338fb-119">Office 365 관리자 탭의 왼쪽된 탐색 영역에서 클릭 **대금 청구 > 구매 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="338fb-p103">**서비스 구매** 페이지 **Azure 정보 보호 프리미엄 P2** 항목을 찾습니다. 마우스 포인터로 하 고 **무료 평가판을 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="338fb-122">**주문 확인** 페이지에서 **지금 평가판 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="338fb-123">**주문 접수** 페이지에서 **계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="338fb-124">다음으로 모든 사용자 계정에 대 한 정보 보호 Azure 라이선스 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="338fb-125">Office 365 관리 센터 탭에서 **사용자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-125">On the Office 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="338fb-126">사용자 계정 목록에서 전역 관리자 계정에 선택한 다음 **제품 라이선스**에 대 한 **편집** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="338fb-127">**Azure 정보 보호 프리미엄 P2** **전환**에 대 한 제품 라이선스를 설정 하 고 **저장** 을 클릭 한 다음 **닫기** 를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="338fb-128">다른 사용자 계정 (사용자 1-사용자 5)에 대 한 2와 3 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="338fb-129">Office 365 개발/테스트 환경을 현재가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="338fb-130">Office 365 e 5 Enterprise 및 Azure 정보 보호 평가판 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="338fb-131">사용자 계정을 모두 Office 365 e 5 엔터프라이즈와 Azure 정보 보호를 사용 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="338fb-132">3 단계: 데이터 분류를 시연</span><span class="sxs-lookup"><span data-stu-id="338fb-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="338fb-133">이 단계에서 Azure 정보 보호 클라이언트와 기본 Azure 정보 보호 정책 구성 요소를 사용 하 여 데이터 분류를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="338fb-134">시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경을 사용 하는 경우에 CLIENT1에서 먼저 Office 2016를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="338fb-135">브라우저를 사용 하 고 [Azure 포털](http://portal.azure.com)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="338fb-136">클릭 **리소스 그룹 >** [자원 그룹 이름] **> CLIENT1 > 연결**합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="338fb-137">CLIENT1에서 Internet Explorer를 실행, Office 포털에서 이동 [http://portal.office.com](http://portal.office.com), 다음 User5 계정 이름과 암호를 사용 하 여 로그인 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://portal.office.com](http://portal.office.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="338fb-138">**Microsoft Office 홈** 탭에서 **Office 2016 설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="338fb-p104">메시지가 표시 되 고 클릭 하 여 **Yes** 사용자 계정 컨트롤 대화 상자가 나타나면 다운로드를 실행 합니다. Office를 설치 될 때까지 기다립니다. 완료 되 면 두번 **닫기를** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="338fb-142">다음으로 Azure 정보 보호 클라이언트를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="338fb-143">사용자가 브라우저 또는 Internet Explorer에서 [Microsoft Azure 정보 보호 다운로드 페이지](https://www.microsoft.com/download/details.aspx?id=53018)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="338fb-144">Office 365 개발/테스트 환경의 경량 버전을 사용 하는 경우 로컬 컴퓨터에서 브라우저를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="338fb-145">시뮬레이션 된 엔터프라이즈 Office 365 개발/테스트 환경을 사용 하는 경우 CLIENT1에서 Internet Explorer를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="338fb-146">**Microsoft Azure 정보 보호** 다운로드 페이지에서 **다운로드**를 클릭 하 고 **AzInfoProtection.exe**차례로 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="338fb-147">대화 상자가 나타나면 AzInfoProtection.exe를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="338fb-148">**Azure 정보 보호 설치** 클라이언트 상자에서 **동의 함**를클릭하고 **예** 사용자 계정 컨트롤 대화 상자가 나타나면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="338fb-149">**성공적으로 완료** 상자에서 클릭 **닫기.**</span><span class="sxs-lookup"><span data-stu-id="338fb-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="338fb-150">다음으로, 문서 분류를 보여줄 있습니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="338fb-151">작업 표시줄에서 **Word** 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="338fb-152">대화 상자가 나타나면 User5 계정 이름과 암호를 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="338fb-153">CLIENT1에서 Office 2016에서 방금 설치한는 **가장 먼저 수행할 작업 첫번째** 상자, **수락**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="338fb-154">**새 문서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="338fb-155">**홈** 탭과 문서 분류의 행에서 리본 메뉴의 **보호** 섹션을 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="338fb-156">빈 문서에서 텍스트를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="338fb-157">클릭 **파일 > 저장** **BeforeAIP**이름을 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="338fb-158">문서 클래스의 행을 **비밀**대 한 아래쪽 화살표를 클릭 하 고 **모든 회사**를 클릭 한 다음 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="338fb-159">클릭 **파일 > 다른이름으로** **AfterAIP**이름을 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="338fb-160">작업 표시줄에서 **파일 탐색기** 를 클릭 한 다음 **문서** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="338fb-p105">Note **BeforeAIP** 및 **AfterAIP** 문서의 다른 파일 크기입니다. AfterAIP 문서는 분류 정보를 제공 하기 때문에 큽니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-p105">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents. The AfterAIP document is larger because it contains the classification information.</span></span>
    
<span data-ttu-id="338fb-163">다음으로 모든 사용자가 지원 사이트 모음에 액세스 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="338fb-164">**Microsoft Office 홈** 탭에서 **SharePoint**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="338fb-165">**SharePoint** 탭에서 **지원 사이트 모음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="338fb-166">오른쪽 위에 있는 **설정** 아이콘을 클릭 하 고 **공유 대상을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="338fb-167">**공유 '지원 사이트 모음'** **고급**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="338fb-168">SharePoint 그룹의 목록에서 **지원 사이트 모음 구성원을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="338fb-169">**사용자 및 그룹** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="338fb-170">**'지원 사이트 모음' 공유** **모든 사용자**를 입력 하 고 **외부 사용자를 제외한 모든 사용자**를 클릭 한 다음이 클릭 한 다음 **공유.**</span><span class="sxs-lookup"><span data-stu-id="338fb-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="338fb-171">**사용자 및 그룹** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="338fb-172">다음으로 User5 계정을 사용 하 여 로그인 하 고 지원 사이트 모음의 문서 폴더를 AIP 암호로 보호 된 문서를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="338fb-173">오른쪽 위에 있는 **Microsoft Office 홈** 탭에서 사용자 아이콘을 클릭 한 다음 **로그 아웃**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="338fb-174">이동 [http://portal.office.com](http://portal.office.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-174">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="338fb-175">**Office 365 로그인** 페이지에서 User5 계정 이름을 클릭 하 고 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-175">On the **Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="338fb-176">**Microsoft Office 홈** 탭에서 클릭 **SharePoint > 사이트 모음을 지원**합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="338fb-177">**문서**, **업로드**를 클릭 하 고 **AfterAIP** 문서를 클릭 한 다음 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="338fb-178">지원 사이트 모음의 문서 폴더에 AfterAIP.docx이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="338fb-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="338fb-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="338fb-179">See Also</span></span>

[<span data-ttu-id="338fb-180">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="338fb-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="338fb-181">Office 365 및 EMS 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="338fb-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="338fb-182">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="338fb-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


