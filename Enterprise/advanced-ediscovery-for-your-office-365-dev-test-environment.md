---
title: Office 365 개발/테스트 환경용 고급 eDiscovery
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: '요약: Office 365 개발/테스트 환경의 샘플 데이터로 Office 365 고급 eDiscovery를 구성하고 보여 줍니다.'
ms.openlocfilehash: 5f96f25f0ba953e45d6ab89d933f97c2c557a4e8
ms.sourcegitcommit: 6eb8a32c6899a884cb1c760cbfc134f427c8b6c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "34726234"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="c2fa0-103">Office 365 개발/테스트 환경용 고급 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="c2fa0-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="c2fa0-104">**요약:** Office 365 개발/테스트 환경의 샘플 데이터로 Office 365 고급 eDiscovery를 구성하고 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="c2fa0-105">Office 365 Advanced eDiscovery를 사용 하면 전자 메일 및 문서를 비롯 하 여 Office 365에 저장 된 데이터를 통해 관련 정보를 신속 하 게 찾고 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-105">Office 365 Advanced eDiscovery lets you quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents.</span></span> <span data-ttu-id="c2fa0-106">특히 소송 상황에서 엄청난 시간과 비용을 절약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-106">This can save enormous amounts of time and expense, especially in litigation situations.</span></span> <span data-ttu-id="c2fa0-107">자세한 내용은 [Office 365 고급 eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-107">For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="c2fa0-108">이 기사의 지침에 따라 가상 계약 분쟁에 대한 작은 데이터 집합을 만들고 고급 eDiscovery로 이를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="c2fa0-109">[여기](http://aka.ms/catlgstack)를 클릭하여 Office 365 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="c2fa0-110">1단계: Office 365 개발/테스트 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="c2fa0-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="c2fa0-111">최소 요구 사항에 따라 간단한 방법으로 고급 eDiscovery를 테스트 하려면 [Office 365 개발/테스트 환경의](office-365-dev-test-environment.md)2 단계 및 3 단계의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="c2fa0-112">시뮬레이트된 엔터프라이즈에서 고급 eDiscovery를 테스트 하려면 [Office 365 개발/테스트 환경에 대 한 DirSync](dirsync-for-your-office-365-dev-test-environment.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c2fa0-113">고급 eDiscovery를 테스트 하는 경우에는 AD DS (Active Directory 도메인 서비스) 포리스트의 인터넷 및 디렉터리 동기화에 연결 된 시뮬레이트된 인트라넷을 포함 하는 시뮬레이트된 엔터프라이즈 환경이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-113">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="c2fa0-114">일반적인 조직을 나타내는 환경에서 테스트 및 시험을 수행할 수 있도록 여기에 옵션으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-114">It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="c2fa0-115">2단계: 고급 eDiscovery의 예제 데이터 만들기</span><span class="sxs-lookup"><span data-stu-id="c2fa0-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="c2fa0-116">이 프로시저에서는 나중에 고급 eDiscovery 사례에서 분석할 전자 메일 메시지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="c2fa0-117">Internet Explorer를 열고 [https://outlook.com](https://outlook.com) [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)2 단계에서 만든 Outlook 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="c2fa0-118">경량 개발/테스트 환경을 사용하는 경우 Internet Explorer의 비공개 세션을 열고 로컬 컴퓨터에서 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="c2fa0-119">시뮬레이트된 엔터프라이즈 개발/테스트 환경을 사용 하는 경우 Azure portal ([https://portal.azure.com](https://portal.azure.com))을 사용 하 여 client1 가상 컴퓨터에 연결한 다음 client1에서 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="c2fa0-120">**Outlook 메일** 탭에서 **새 전자 메일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="c2fa0-121">**대상**에 평가판 구독의 User6 계정 전자 메일 주소 ( **User6 @** 를 입력 합니다.<organization name></span><span class="sxs-lookup"><span data-stu-id="c2fa0-121">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name></span></span> <span data-ttu-id="c2fa0-122">**. onmicrosoft.com**)</span><span class="sxs-lookup"><span data-stu-id="c2fa0-122">**.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="c2fa0-123">제목에 **테스트 전자 메일 1**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="c2fa0-124">본문에 **Tailspin 계약 초안**을 입력한 다음 **보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="c2fa0-125">**Outlook 메일** 탭에서 **새 전자 메일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="c2fa0-126">**받는 사람**에 평가판 구독의 User6 계정 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="c2fa0-127">제목에 **테스트 전자 메일 2**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="c2fa0-128">본문에 **Tailspin 점심 회의**를 입력한 다음 **보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="c2fa0-129">**Outlook 메일** 탭에서 **새 전자 메일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="c2fa0-130">**받는 사람**에 평가판 구독의 User6 계정 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="c2fa0-131">제목에 **테스트 전자 메일 3**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="c2fa0-132">본문에 **Tailspin 계약 불일치**를 입력한 다음 **보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="c2fa0-133">오른쪽 위 모서리에 있는 사용자 아이콘을 클릭한 다음 **로그아웃**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="c2fa0-134">새 탭을 열고 평가판 구독의 User6 계정 계정 이름과 암호를 사용[https://www.office.com](https://www.office.com)하 여 Office 365 portal ()에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-134">Open a new tab and sign in to the Office 365 portal ([https://www.office.com](https://www.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="c2fa0-135">**Office 365 포털** 탭에서 **메일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="c2fa0-136">**User6-outlook** 탭에서 User6가 Outlook 전자 메일 계정에서 세 개의 전자 메일을 모두 받았는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-136">On the **Mail - User6 - Outlook** tab, check that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="c2fa0-137">User6의 **Office 365 포털 탭**으로 다시 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="c2fa0-138">오른쪽 위 모서리에 있는 사용자 아이콘을 클릭한 다음 **로그아웃**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="c2fa0-139">이 프로시저에서는 나중에 고급 eDiscovery 사례에서 분석할 두 개의 Word 문서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="c2fa0-140">**Office** 페이지에서 **로그인**을 클릭하고 전역 관리자 계정의 자격 증명을 사용하여 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="c2fa0-141">새 탭에서 프로덕션 SharePoint 사이트의 URL에 액세스 합니다. **https://** <fictional organization name> **. sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="c2fa0-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="c2fa0-142">**프로덕션 사이트 모음** 탭의 **문서**에서 **새 문서 > Word 문서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="c2fa0-143">**Word** 페이지에서 **Tailspin 초안 계약**을 입력 하 고 제목에 **저장** 됨이 표시 될 때까지 기다린 다음 **Word** 페이지 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-143">On the **Word** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word** page tab.</span></span>
    
5. <span data-ttu-id="c2fa0-144">**프로덕션 사이트 모음** 탭의 **문서**에서 **새 문서 > Word 문서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="c2fa0-145">**Word** 탭에서 **Tailspin 계약 분쟁 정보**를 입력 하 고 제목에 **저장** 됨이 표시 되 면 **Word** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-145">On the **Word** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word** tab.</span></span>
    
7. <span data-ttu-id="c2fa0-146">**프로덕션 사이트 모음** 탭의 문서 목록에 **문서** 및 **문서1**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="c2fa0-147">**프로덕션 사이트 모음** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="c2fa0-148">3 단계: 법적 분쟁에 고급 eDiscovery 사용</span><span class="sxs-lookup"><span data-stu-id="c2fa0-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="c2fa0-149">안타깝게도 조직과 Tailspin Toys 간의 계약 분쟁이 법적 조치가 필요한 시점에 도달했습니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-149">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action.</span></span> <span data-ttu-id="c2fa0-150">이 절차에서는 "Tailspin 계약" 텍스트를 포함 하는 전자 메일 및 문서를 검색 하 고 분석 하기 위한 고급 eDiscovery 사례를 만들고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-150">In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="c2fa0-151">고급 eDiscovery를 사용하는 프로세스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="c2fa0-152">보안 &amp; 및 준수 센터에서 검색을 만들고 결과를 분석 한 다음 고급 eDiscovery의 결과를 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="c2fa0-153">고급 eDiscovery에서 사례를 만들고 구성한 다음 검색 결과를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="c2fa0-154">이 절차에서는 보안 &amp; 및 준수 센터에서 "Tailspin 계약"에 대 한 검색을 만들고 결과를 검토 한 다음 고급 eDiscovery의 결과를 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="c2fa0-155">**Office 365 포털** 탭에서 **관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="c2fa0-156">관리 센터 탭의 왼쪽 탐색 창에서 **관리 센터 > 준수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="c2fa0-157">**보안 &amp; 및 준수** 탭에서 **사용 권한을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="c2fa0-158">**사용 권한** 목록에서 **조직 관리**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="c2fa0-159">**역할 그룹** 창의 **구성원**에서 +기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="c2fa0-160">**구성원 선택** 창에서 관리자 계정의 이름을 두 번 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="c2fa0-161">**역할 그룹** 창에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="c2fa0-162">**사용 권한** 목록에서 **eDiscovery 관리자**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="c2fa0-163">**역할 그룹** 창의 **eDiscovery 관리자**에서 +기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="c2fa0-164">**구성원 선택** 창에서 관리자 계정의 이름을 두 번 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="c2fa0-165">**역할 그룹** 창에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="c2fa0-166">왼쪽 탐색 창에서 **검색 &amp; 조사 > 콘텐츠 검색**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="c2fa0-167">+기호를 클릭하여 검색을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="c2fa0-168">**새 검색** 창에서 **이름**에 **Tailspin 계약 검색**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="c2fa0-169">**어느 위치를 검색하시겠습니까?** 에서 **전체 검색**을 클릭하고 **Exchange**, **SharePoint** 및 **공용 폴더**를 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="c2fa0-170">**무엇을 검색하시겠습니까?** 에서 **Tailspin 계약**을 입력한 다음 **검색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="c2fa0-171">검색 목록에서 **Tailspin 계약 검색** 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="c2fa0-172">**Tailspin 계약 검색** 창의 **결과**에서 **검색 결과 미리 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-172">In the **Tailspin contract search** pane, click **Preview search results** under **Results**.</span></span> <span data-ttu-id="c2fa0-173">프로덕션 SharePoint 사이트에서 두 문서 ( **문서** 및 문서 1)를 나열 하는 창 \*\*\*\*, **테스트 전자 메일** 및 테스트 전자 메일 **3** 전자 메일을 User6에 게 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-173">You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6.</span></span> <span data-ttu-id="c2fa0-174">창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-174">Close the window.</span></span>
    
19. <span data-ttu-id="c2fa0-175">**콘텐츠 검색** 창의 **고급 eDiscovery를 사용한 결과 분석**에서 **분석 결과 미리 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="c2fa0-176">**Tailspin 계약 검색의 검색 결과 준비** 창에서 **준비**를 클릭하고 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="c2fa0-177">이 프로시저에서는 고급 eDiscovery의 새 사례를 만들고 Tailspin 계약 검색 결과를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="c2fa0-178">왼쪽 탐색 창의 \*\* &amp; 검색 조사\*\*에서 **eDiscovery** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="c2fa0-179">**eDiscovery** 창에서 **고급 eDiscovery로 이동**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="c2fa0-180">**고급 eDiscovery** 탭에서 +기호를 클릭하여 새 사례를 추가합니다. </span><span class="sxs-lookup"><span data-stu-id="c2fa0-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="c2fa0-p106">**사례 추가** 창에서 **이름**에 **Tailspin 계약 분쟁**을 입력한 다음 **확인**을 클릭합니다. 사례가 다 만들어질 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="c2fa0-183">목록에서 **Tailspin 계약 분쟁** 사례를 두 번 클릭합니다. </span><span class="sxs-lookup"><span data-stu-id="c2fa0-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="c2fa0-184">**컨테이너** 목록에서 **Tailspin 계약 검색** 컨테이너를 클릭 한 다음 **프로세스**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-184">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**.</span></span> <span data-ttu-id="c2fa0-185">처리가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-185">Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="c2fa0-186">창 하단에 **프로세스: 완료됨**이 표시되면 왼쪽 탐색 창에서 **프로세스 요약**을 클릭하여 요약을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="c2fa0-187">위쪽 탐색 창에서 **분석**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="c2fa0-188">**설정** 페이지에 있는 **테마**의 **최대 테마 수**에 **3**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="c2fa0-189">**분석**을 클릭하고 완료할 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-189">Click **Analyze** and wait for the analysis to complete.</span></span> <span data-ttu-id="c2fa0-190">대상 인구, 문서, 전자 메일 및 첨부 파일을 분석한 일련의 원형 차트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-190">You should see a series of pie charts with analysis of the target population, documents, emails, and attachments.</span></span> <span data-ttu-id="c2fa0-191">자세한 내용은 [분석 결과 보기](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-191">For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="c2fa0-192">이제 이 환경을 사용하여 새 콘텐츠, 새 검색 및 사례를 만들고 Office 365의 고급 eDiscovery를 추가로 실험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2fa0-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c2fa0-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2fa0-193">See Also</span></span>

[<span data-ttu-id="c2fa0-194">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="c2fa0-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="c2fa0-195">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="c2fa0-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="c2fa0-196">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="c2fa0-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="c2fa0-197">Office 365 개발/테스트 환경용 DirSync</span><span class="sxs-lookup"><span data-stu-id="c2fa0-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="c2fa0-198">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="c2fa0-198">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="c2fa0-199">Office 365 Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="c2fa0-199">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


