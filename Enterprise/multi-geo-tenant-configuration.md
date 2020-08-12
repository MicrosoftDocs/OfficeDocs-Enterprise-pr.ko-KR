---
title: Microsoft 365 Multi-Geo 테넌트 구성
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- SPO_Content
- Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
localization_priority: Priority
description: 이 문서에서는 위성 위치를 추가하고 Microsoft 365 Multi-Geo용 테넌트를 구성하는 방법을 알아봅니다.
ms.openlocfilehash: 53a339c9bc709920adb55992d44be2f6280fffcd
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606794"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a><span data-ttu-id="b6535-103">Microsoft 365 Multi-Geo 테넌트 구성</span><span class="sxs-lookup"><span data-stu-id="b6535-103">Microsoft 365 Multi-Geo tenant configuration</span></span>

<span data-ttu-id="b6535-104">Microsoft 365 Multi-Geo에 대한 테넌트를 구성하기 전에 [Microsoft 365 Multi-Geo 계획](plan-for-multi-geo.md)을 꼭 읽으세요.</span><span class="sxs-lookup"><span data-stu-id="b6535-104">Before you configure your tenant for Microsoft 365 Multi-Geo, be sure you have read [Plan for Microsoft 365 Multi-Geo](plan-for-multi-geo.md).</span></span> <span data-ttu-id="b6535-105">이 문서에 나온 단계를 수행하려면 위성 위치로 사용할 지리적 위치 목록과 해당 위치를 제공하려는 테스트 사용자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-105">To follow the steps in this article, you'll need a list of the geo locations that you want to enable as satellite locations, and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a><span data-ttu-id="b6535-106">테넌트에 Microsoft 365 요금제의 Multi-Geo 기능 추가</span><span class="sxs-lookup"><span data-stu-id="b6535-106">Add the Multi-Geo Capabilities in your Microsoft 365 plan to your tenant</span></span>

<span data-ttu-id="b6535-107">Microsoft 365 Multi-Geo를 사용하려면 _Microsoft 365 요금제에서 Multi-Geo 기능_ 요금제가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-107">To use Microsoft 365 Multi-Geo, you need the _Multi-Geo Capabilities in Microsoft 365_ plan.</span></span> <span data-ttu-id="b6535-108">계정 팀과 협력하여 테넌트에 이 요금제를 추가하십시오.</span><span class="sxs-lookup"><span data-stu-id="b6535-108">Work with your account team to add this plan to your tenant.</span></span> <span data-ttu-id="b6535-109">귀하의 계정 팀이 귀하를 적절한 라이센스 전문가와 연결시켜 테넌트를 구성할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-109">Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="b6535-p103">_Microsoft 365의 Multi-Geo 기능_ 요금제는 사용자 수준 서비스 요금제입니다. 따라서 위성 위치에 호스트하려는 각 사용자를 위해 라이선스가 필요합니다. 시간에 따라 위성 위치에 사용자를 추가하면서 라이선스를 더 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-p103">Note that the _Multi-Geo Capabilities in Microsoft 365_ plan are a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="b6535-113">테넌트가 _Microsoft 365의 Multi-Geo 기능_ 요금제로 프로비저닝되면 OneDrive 및 SharePoint 관리 센터에서 **지리적 위치** 탭을 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Microsoft 365_ plan, the **Geo locations** tab will become available in the OneDrive and SharePoint admin centers.</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="b6535-114">테넌트에 위성 위치 추가</span><span class="sxs-lookup"><span data-stu-id="b6535-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="b6535-115">데이터를 저장할 지리적 위치마다 위성 위치를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-115">You must add a satellite location for each geo location where you want to store data.</span></span> <span data-ttu-id="b6535-116">다음 표에는 사용 가능한 지역 위치가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-116">Available geo locations are shown in the following table:</span></span>

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![SharePoint 관리 센터의 지리적 위치 페이지 스크린샷](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="b6535-118">위성 위치를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="b6535-118">To add a satellite location</span></span>

1. <span data-ttu-id="b6535-119">SharePoint 관리 센터를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-119">Open the SharePoint admin center.</span></span>

2. <span data-ttu-id="b6535-120">**지리적 위치** 탭으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-120">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="b6535-121">**위치 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-121">Click **Add location**.</span></span>

4. <span data-ttu-id="b6535-122">추가하려는 위치를 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-122">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="b6535-123">지리적 위치에서 사용할 도메인을 입력한 후 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-123">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="b6535-124">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-124">Click **Close**.</span></span>

<span data-ttu-id="b6535-p105">테넌트의 크기에 따라 프로비전하는 데 몇 시간에서 72시간까지 걸릴 수 있습니다. 위성 위치의 프로비전이 완료되면 이메일 확인이 수신됩니다. 새 지리적 위치가 OneDrive 관리 센터의 **지리적 위치** 탭의 지도에 파란색으로 표시되면 사용자의 기본 설정 데이터 위치를 해당 지리적 위치로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="b6535-p106">새 위성 위치가 기본 설정으로 지정됩니다. 이 경우 해당 위성 위치를 로컬 준수 요구에 적절하게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-p106">Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="b6535-130">사용자의 기본 설정 데이터 위치 지정</span><span class="sxs-lookup"><span data-stu-id="b6535-130">Setting users' preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="b6535-p107">필요한 위성 위치를 사용하도록 설정한 경우, 해당 기본 설정 데이터 위치를 사용하도록 사용자 계정을 업데이트할 수 있습니다. 해당 사용자가 기본 데이터 위치에 있더라도, 모든 사용자의 중앙 위치를 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-p107">Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6535-133">사용자의 기본 데이터 위치가 위성 위치 또는 중앙 위치로 구성되지 않은 위치로 설정된 경우 OneDrive, SharePoint 사이트 및 그룹 사서함을 프로비저닝할 때 시스템이 중앙 위치로 기본 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-133">If a user's preferred data location is set to a location that has not been configured as a satellite location or the central location, the system will default to the central location when provisioning OneDrive and SharePoint sites and Group mailboxes.</span></span>

> [!TIP]
> <span data-ttu-id="b6535-134">Multi-Geo를 보다 광범위한 조직으로 롤아웃하기 전에 테스트 사용자 또는 소규모의 사용자 그룹을 사용하여 유효성 검사를 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-134">We recommend that you begin validations with a test user or small group of users before rolling out multi-geo to your broader organization.</span></span>

<span data-ttu-id="b6535-135">Azure Active Directory(Azure AD)에는 두 가지 유형의 사용자 개체(클라우드 전용 사용자 및 동기화된 사용자)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-135">In Azure Active Directory (Azure AD) there are two types of user objects: cloud only users and synchronized users.</span></span> <span data-ttu-id="b6535-136">사용자 유형에 해당하는 지침을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="b6535-136">Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a><span data-ttu-id="b6535-137">Azure AD Connect를 사용하여 사용자의 기본 설정 데이터 위치 동기화</span><span class="sxs-lookup"><span data-stu-id="b6535-137">Synchronize user's Preferred Data Location using Azure AD Connect</span></span> 

<span data-ttu-id="b6535-138">회사의 사용자가 온-프레미스 Active Directory 시스템에서 Azure AD로 동기화되는 경우, 해당 PreferredDataLocation을 AD에 채워야 하며 Azure AD로 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-138">If your company's users are synchronized from an on-premises Active Directory system to Azure AD, their PreferredDataLocation must be populated in AD and synchronized to Azure AD.</span></span>

<span data-ttu-id="b6535-139">[Azure Active Directory 연결 동기화: Microsoft 365 리소스에 대한 기본 데이터 위치 동기화](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) 벌차를 따라 온-프레미스 Active Directory 도메인 서비스 (AD DS)에서 Azure AD로의 기본 데이터 위치 동기화를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-139">Follow the process in [Azure Active Directory Connect sync: Configure preferred data location for Microsoft 365 resources](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) to configure Preferred Data Location sync from your on-premises Active Directory Domain Services (AD DS) to Azure AD.</span></span>

<span data-ttu-id="b6535-140">표준 사용자 만들기 워크플로의 일환으로, 사용자의 기본 설정 데이터 위치를 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-140">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6535-141">OneDrive를 프로비저닝하지 않은 신규 사용자의 경우, 사용자의 PDL이 Azure AD에 동기화 된 후 최소 24시간 동안 기다렸다가 사용자가 비즈니스용 OneDrive에 로그인하기 전에 변경 내용이 전파되도록 기다리십시오.</span><span class="sxs-lookup"><span data-stu-id="b6535-141">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to Azure AD for the changes to propagate before the user logs in to OneDrive for Business.</span></span> <span data-ttu-id="b6535-142">(비즈니스용 OneDrive를 프로비저닝하기 위해 사용자가 로그인하기 전에 기본 데이터 위치를 설정하면 사용자의 새 OneDrive가 올바른 위치에 프로비저닝됩니다.)</span><span class="sxs-lookup"><span data-stu-id="b6535-142">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="b6535-143">클라우드 전용 사용자를 위한 기본 설정 데이터 위치 지정</span><span class="sxs-lookup"><span data-stu-id="b6535-143">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="b6535-144">회사의 사용자가 온-프레미스 Active Directory 시스템에서 Azure AD로 동기화되지 않을 경우, 즉 Microsoft 365 또는 AAD에서 생성될 경우 Windows PowerShell용 Azure Active Directory 모듈을 사용하여 PDL을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-144">If your company's users are not synchronized from an on-premises Active Directory system to Azure AD, meaning they are created in Microsoft 365 or Azure AD, then the PDL must be set using the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

<span data-ttu-id="b6535-145">이 항목의 절차는 [Wiindows PowerShell 모듈용 Microsoft Azure Active Directory 모듈](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)을 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-145">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0).</span></span> <span data-ttu-id="b6535-146">이 모듈이 이미 설치 되어 있는 경우에는 최신 버전으로 업데이트를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="b6535-146">If you already have this module installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="b6535-147">테넌트에 대한 전역 관리자 자격 증명으로 [연결 및 로그인](/powershell/connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)</span><span class="sxs-lookup"><span data-stu-id="b6535-147">[Connect and sign in](/powershell/connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) with a set of global administrator credentials for your tenant.</span></span>

2.  <span data-ttu-id="b6535-p111">[Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet을 사용하여 각 사용자에 대한 기본 설정 데이터 위치를 지정합니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-p111">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="b6535-p112">Get-MsolUser cmdlet을 사용하여 기본 데이터 위치가 적절히 업데이트되었는지 확인할 수 있습니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-p112">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![set-msoluser를 보여주는 PowerShell 창의 스크린 샷](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="b6535-153">사용자의 기본 데이터 위치를 표준 사용자 생성 작업 과정의 일부로 포함하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-153">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6535-154">OneDrive가 프로비전닝되지 않은 새 사용자의 경우, 사용자가 OneDrive에 로그인하기 전에 변경 사항이 적용되도록 사용자의 PDL이 설정된 후 최소 24시간을 기다리십시오.</span><span class="sxs-lookup"><span data-stu-id="b6535-154">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to OneDrive.</span></span> <span data-ttu-id="b6535-155">(비즈니스용 OneDrive를 프로비저닝하기 위해 사용자가 로그인하기 전에 기본 데이터 위치를 설정하면 사용자의 새 OneDrive가 올바른 위치에 프로비저닝됩니다.)</span><span class="sxs-lookup"><span data-stu-id="b6535-155">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="b6535-156">OneDrive 프로비전 및 PDL의 영향</span><span class="sxs-lookup"><span data-stu-id="b6535-156">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="b6535-157">사용자가 이미 테넌트에 OneDrive 사이트를 만든 경우 PDL을 설정해도 기존 OneDrive가 자동으로 이동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-157">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive.</span></span> <span data-ttu-id="b6535-158">사용자의 OneDrive를 이동하려면 [비즈니스 지역 이동을 위한 OneDrive](move-onedrive-between-geo-locations.md)를 참조하십시오. 지리적 위치 간에 OneDrive를 이동하기에 있는 지침을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="b6535-158">To move a user's OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span> <span data-ttu-id="b6535-159">(참고로 사용자의 Exchange 사서함은 사용자의 PDL을 설정할 때 자동으로 이동합니다.)</span><span class="sxs-lookup"><span data-stu-id="b6535-159">(Note that the user's Exchange mailbox does move automatically when you set the user's PDL.)</span></span>

<span data-ttu-id="b6535-160">테넌트 내에 OneDrive 사이트가 없으면 해당 사용자의 PDL가 회사의 위성 위치 중 하나와 일치한다고 가정할 경우 해당 PDL 값에 따라 OneDrive가 프로비전됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-160">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company's satellite locations.</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="b6535-161">Multi-Geo 검색 구성</span><span class="sxs-lookup"><span data-stu-id="b6535-161">Configuring Multi-Geo search</span></span>

<span data-ttu-id="b6535-162">Multi-Geo 테넌트에는 검색 쿼리가 테넌트 내의 어디에서든지 결과를 반환할 수 있도록 하는 집계 검색 기능이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-162">Your multi-geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="b6535-163">기본적으로 각 검색 인덱스가 관련 지리적 위치 내에 있더라도, 이러한 진입점에서 검색을 수행하면 집계 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-163">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="b6535-164">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="b6535-164">OneDrive for Business</span></span>

- <span data-ttu-id="b6535-165">Delve</span><span class="sxs-lookup"><span data-stu-id="b6535-165">Delve</span></span>

- <span data-ttu-id="b6535-166">SharePoint 홈</span><span class="sxs-lookup"><span data-stu-id="b6535-166">SharePoint Home</span></span>

- <span data-ttu-id="b6535-167">검색 센터</span><span class="sxs-lookup"><span data-stu-id="b6535-167">Search Center</span></span>

<span data-ttu-id="b6535-168">또한 SharePoint 검색 API를 사용하는 사용자 지정 검색 응용 프로그램에 대해 Multi-Geo 검색 기능을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-168">Additionally, multi-geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="b6535-169">제한 사항 및 차이점을 비롯한 지침을 보려면 [비즈니스용 OneDrive Multi-Geo 검색 구성](configure-search-for-multi-geo.md)을 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="b6535-169">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a><span data-ttu-id="b6535-170">Microsoft 365 Multi-Geo 구성의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="b6535-170">Validating the Microsoft 365 Multi-Geo configuration</span></span>

<span data-ttu-id="b6535-171">Microsoft 365 Multi-Geo를 회사에 널리 도입하기 전에 유효성 검사 계획에 포함시킬 수 있는 몇 가지 기본적인 사용 사례는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-171">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out Microsoft 365 Multi-Geo to your company.</span></span> <span data-ttu-id="b6535-172">이 테스트와 회사와 관련된 추가 사용 사례를 완료하면 초기 파일럿 그룹의 사용자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-172">Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="b6535-173">**비즈니스용 OneDrive**</span><span class="sxs-lookup"><span data-stu-id="b6535-173">**OneDrive for Business**</span></span>

<span data-ttu-id="b6535-174">Microsoft 365 앱 시작 관리자에서 OneDrive를 선택하고 사용자의 PDL에 따라 사용자의 적절한 지리적 위치로 자동 연결되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-174">Select OneDrive from the Microsoft 365 app launcher and confirm that you are automatically directed to the appropriate geo location for the user, based on the user's PDL.</span></span> <span data-ttu-id="b6535-175">이제 비즈니스용 OneDrive는 해당 위치에서 프로비저닝을 시작해야합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-175">OneDrive for Business should now begin provisioning at that location.</span></span> <span data-ttu-id="b6535-176">프로비저닝이 완료되면 일부 문서를 업로드하고 다운로드하십시오.</span><span class="sxs-lookup"><span data-stu-id="b6535-176">Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="b6535-177">**OneDrive 모바일 앱**</span><span class="sxs-lookup"><span data-stu-id="b6535-177">**OneDrive Mobile App**</span></span>

<span data-ttu-id="b6535-178">테스트 계정 자격 증명을 사용하여 OneDrive 모바일 앱에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-178">Log into your OneDrive mobile App with your test account credentials.</span></span> <span data-ttu-id="b6535-179">비즈니스용 OneDrive 파일을 볼 수 있고, 모바일 장치에서 해당 파일과 상호 작용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-179">Confirm that you can see your OneDrive for Business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="b6535-180">**OneDrive 동기화 클라이언트**</span><span class="sxs-lookup"><span data-stu-id="b6535-180">**OneDrive sync client**</span></span>

<span data-ttu-id="b6535-p118">OneDrive 동기화 클라이언트가 로그인 시 비즈니스용 OneDrive 지리적 위치를 자동으로 감지하는지 확인합니다. 동기화 클라이언트를 다운로드해야 할 경우 OneDrive 라이브러리에서 **동기화**를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-p118">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="b6535-183">**Office 응용 프로그램**</span><span class="sxs-lookup"><span data-stu-id="b6535-183">**Office applications**</span></span>

<span data-ttu-id="b6535-p119">Word와 같은 Office 응용 프로그램에서 로그인하여 비즈니스용 OneDrive에 액세스할 수 있는지 확인합니다. Office 응용 프로그램을 열고 "OneDrive- <TenantName>"을 선택합니다. Office에서 사용자의 OneDrive 위치가 감지되고 열 수 있는 파일이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-p119">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="b6535-187">**공유**</span><span class="sxs-lookup"><span data-stu-id="b6535-187">**Sharing**</span></span>

<span data-ttu-id="b6535-p120">OneDrive 파일을 공유해 보세요. 사용자 선택 기능에는 모든 SharePoint Online 사용자가 해당 지리적 위치에 관계없이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6535-p120">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.</span></span>
