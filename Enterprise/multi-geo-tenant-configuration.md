---
title: 비즈니스용 OneDrive Multi-Geo 테넌트 구성
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: 비즈니스용 OneDrive Multi-Geo를 구성하는 방법을 알아봅니다.
ms.openlocfilehash: 29e69fa6e5a9715360b61024ee41dee4cd4b95b1
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="995ca-103">비즈니스용 OneDrive Multi-Geo 테넌트 구성</span><span class="sxs-lookup"><span data-stu-id="995ca-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="995ca-p101">비즈니스용 OneDrive Multi-Geo에 대한 테넌트를 구성하기 전에 [비즈니스용 OneDrive Multi-Geo 계획](plan-for-multi-geo.md)을 읽어야 합니다. 이 문서에 나와 있는 단계를 수행하려면 사용하도록 설정하려는 위치와 해당 위치에 대해 프로비전할 테스트 사용자 목록이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="995ca-106">테넌트에 Office 365 요금제의 Multi-Geo 기능 추가</span><span class="sxs-lookup"><span data-stu-id="995ca-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="995ca-p102">비즈니스용 OneDrive Multi-Geo를 사용하려면 _Office 365의 Multi-Geo 기능_ 요금제가 필요합니다. 계정 팀과 공조하여 테넌트에 이 요금제를 추가합니다. 계정 팀은 귀하를 적절한 라이선스 전문가에게 연결하여 테넌트가 구성될 수 있게 해드릴 것입니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="995ca-p103">_Office 365의 Multi-Geo 기능_ 요금제는 사용자 수준 서비스 요금제입니다. 따라서 위성 위치에 호스트하려는 각 사용자를 위해 라이선스가 필요합니다. 시간에 따라 위성 위치에 사용자를 추가하면서 라이선스를 더 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="995ca-113">테넌트가 _Office 365의 Multi-Geo 기능_ 요금제로 프로비전되면 [OneDrive 관리 센터](https://admin.onedrive.com)에서 **지리적 위치** 탭을 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a><span data-ttu-id="995ca-114">ADL(허용 데이터 위치)을 테넌트로 설정</span><span class="sxs-lookup"><span data-stu-id="995ca-114">Set the Allowed Data Locations (ADL) to your tenant</span></span>

<span data-ttu-id="995ca-p104">비즈니스용 OneDrive를 사용하려는 각 지리적 위치에 대해 SharePoint의 허용 데이터 위치를 설정해야 합니다. 사용 가능한 지리적 위치는 다음 표에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p104">You must set an Allowed Data Location for SharePoint for each geo-location where you want to use OneDrive for Business. Available geo-locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="995ca-117"><strong>위치</strong></span><span class="sxs-lookup"><span data-stu-id="995ca-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="995ca-118"><strong>코드</strong></span><span class="sxs-lookup"><span data-stu-id="995ca-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="995ca-119">북미</span><span class="sxs-lookup"><span data-stu-id="995ca-119">North America</span></span></td>
<td align="left"><span data-ttu-id="995ca-120">NAM</span><span class="sxs-lookup"><span data-stu-id="995ca-120">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="995ca-121">유럽/중동/아프리카</span><span class="sxs-lookup"><span data-stu-id="995ca-121">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="995ca-122">EUR</span><span class="sxs-lookup"><span data-stu-id="995ca-122">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="995ca-123">아시아 태평양</span><span class="sxs-lookup"><span data-stu-id="995ca-123">Asia/Pacific</span></span></td>
<td align="left"><span data-ttu-id="995ca-124">APC</span><span class="sxs-lookup"><span data-stu-id="995ca-124">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="995ca-125">오스트레일리아</span><span class="sxs-lookup"><span data-stu-id="995ca-125">Australia</span></span></td>
<td align="left"><span data-ttu-id="995ca-126">AUS</span><span class="sxs-lookup"><span data-stu-id="995ca-126">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="995ca-127">일본</span><span class="sxs-lookup"><span data-stu-id="995ca-127">Japan</span></span></td>
<td align="left"><span data-ttu-id="995ca-128">JPN</span><span class="sxs-lookup"><span data-stu-id="995ca-128">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="995ca-129">캐나다</span><span class="sxs-lookup"><span data-stu-id="995ca-129">Canada</span></span></td>
<td align="left"><span data-ttu-id="995ca-130">CAN</span><span class="sxs-lookup"><span data-stu-id="995ca-130">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="995ca-131">영국</span><span class="sxs-lookup"><span data-stu-id="995ca-131">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="995ca-132">GBR</span><span class="sxs-lookup"><span data-stu-id="995ca-132">GBR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="995ca-133">한국</span><span class="sxs-lookup"><span data-stu-id="995ca-133">Korea</span></span></td>
<td align="left"><span data-ttu-id="995ca-134">KOR</span><span class="sxs-lookup"><span data-stu-id="995ca-134">KOR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="995ca-135">위성 지리적 위치를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="995ca-135">To add a satellite geo location</span></span>

1. <span data-ttu-id="995ca-136">[OneDrive 관리 센터](https://admin.onedrive.com)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-136">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="995ca-137">**지리적 위치** 탭으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-137">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="995ca-138">**위치 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-138">Click **Add location**.</span></span>

4. <span data-ttu-id="995ca-139">추가하려는 위치를 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-139">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="995ca-140">지리적 위치에서 사용할 도메인을 입력한 후 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-140">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="995ca-141">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-141">Click **Close**.</span></span>

<span data-ttu-id="995ca-p105">테넌트의 크기에 따라 프로비전하는 데 몇 시간에서 72시간까지 걸릴 수 있습니다. 위성 위치의 프로비전이 완료되면 전자 메일 확인이 수신됩니다. 새 지리적 위치가 OneDrive 관리 센터의 **지리적 위치** 탭의 지도에 파란색으로 표시되면 사용자의 기본 설정 데이터 위치를 해당 지리적 위치로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="995ca-p106">새 위성 지리적 위치가 기본 설정으로 지정됩니다. 이 경우 해당 지리적 위치를 로컬 준수 요구에 적절하게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="995ca-147">사용자의 기본 설정 데이터 위치 지정</span><span class="sxs-lookup"><span data-stu-id="995ca-147">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="995ca-p107">필요한 데이터 위치를 사용하도록 설정한 경우, 해당 데이터 위치를 사용하도록 사용자 계정을 업데이트할 수 있습니다. 해당 사용자가 기본 데이터 위치에 있더라도, 모든 사용자의 기본 설정 데이터 위치를 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="995ca-150">Multi-Geo 기능을 보다 광범위한 조직으로 롤아웃하기 전에 테스트 사용자 또는 소규모의 사용자 그룹을 사용하여 유효성 검사를 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-150">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="995ca-p108">AAD에는 두 가지 유형의 사용자 개체인, 클라우드 전용 사용자와 동기화된 사용자가 있습니다. 사용자 유형에 적합한 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="995ca-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="995ca-153">AD Connect를 사용하여 사용자의 기본 설정 데이터 위치 동기화</span><span class="sxs-lookup"><span data-stu-id="995ca-153">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="995ca-p109">회사의 사용자가 온-프레미스 AD (Active Directory) 시스템에서 AAD(Azure Active Directory)로 동기화되면 해당 PreferredDataLocation이 AD에 입력되고 AAD와 동기화됩니다. [Azure AD Connect 동기화: 기본 구성 변경](https://docs.microsoft.com/ko-KR/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration)의 프로세스에 따라 온-프레미스 AD에서 AAD로의 기본 설정 데이터 위치 동기화를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/ko-KR/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="995ca-156">표준 사용자 만들기 워크플로의 일환으로, 사용자의 기본 설정 데이터 위치를 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-156">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="995ca-p110">OneDrive가 프로비전되지 않은 새로운 사용자의 경우, 사용자의 PDL이 AAD와 동기화된 후에 변경 내용이 전파될 수 있게 24시간 넘게 기다렸다가 사용자가 비즈니스용 OneDrive에 로그인하도록 합니다. 사용자가 로그인하여 비즈니스용 OneDrive를 프로비전하기 전에 기본 설정 데이터 위치를 지정하면 사용자의 새 OneDrive가 올바른 위치에 프로비전됩니다.)</span><span class="sxs-lookup"><span data-stu-id="995ca-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="995ca-159">클라우드 전용 사용자를 위한 기본 설정 데이터 위치 지정</span><span class="sxs-lookup"><span data-stu-id="995ca-159">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="995ca-160">회사의 사용자가 온-프레미스 AD(Active Directory) 시스템에서 AAD(Azure Active Directory)로 동기화되지 않을 경우, 즉 Office 365 또는 AAD에서 생성될 경우 AAD PowerShell을 사용하여 PDL을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-160">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="995ca-p111">이 섹션의 절차를 수행하려면 [Windows PowerShell용 Microsoft Azure Active Directory 모듈](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)이 필요합니다. AAD PowerShell이 이미 설치된 경우 최신 버전으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="995ca-163">Windows PowerShell용 Microsoft Azure Active Directory 모듈을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-163">Step 2: Open the Windows Azure Active Directory Module for Windows PowerShell</span></span>

2.  <span data-ttu-id="995ca-164">`Connect-MsolService`를 실행하고 테넌트에 대한 전역 관리자 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-164">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="995ca-p112">[Set-MsolUser](https://docs.microsoft.com/ko-KR/powershell/msonline/v1/set-msoluser) cmdlet을 사용하여 각 사용자에 대한 기본 설정 데이터 위치를 지정합니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p112">Use the [Set-MsolUser](https://docs.microsoft.com/ko-KR/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="995ca-p113">Get-MsolUser cmdlet을 사용하여 기본 데이터 위치가 적절히 업데이트되었는지 확인할 수 있습니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

<span data-ttu-id="995ca-169">표준 사용자 만들기 워크플로의 일환으로, 사용자의 기본 설정 데이터 위치를 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-169">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="995ca-p114">OneDrive가 프로비전되지 않은 새로운 사용자의 경우, 사용자의 PDL이 설정된 후에 변경 내용이 전파될 수 있게 24시간 넘게 기다렸다가 사용자가 SharePoint OneDrive에 로그인하도록 합니다. 사용자가 로그인하여 비즈니스용 OneDrive를 프로비전하기 전에 기본 설정 데이터 위치를 지정하면 사용자의 새 OneDrive가 올바른 위치에 프로비전됩니다.)</span><span class="sxs-lookup"><span data-stu-id="995ca-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="995ca-172">OneDrive 프로비전 및 PDL의 영향</span><span class="sxs-lookup"><span data-stu-id="995ca-172">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="995ca-p115">사용자의 OneDrive 사이트가 이미 테넌트에 만들어진 경우 해당 PDL을 설정해도 기존 OneDrive가 자동으로 이동되지 않습니다. 사용자의 OneDrive를 이동하려면 [비즈니스용 OneDrive 지리적 이동](move-onedrive-between-geo-locations.md)을 참조하세요. 또한 두 지리적 위치 간의 OneDrive 이동 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="995ca-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="995ca-175">테넌트 내에 OneDrive 사이트가 없으면 해당 사용자의 PDL가 회사의 ADL(허용 데이터 위치) 중 하나와 일치한다고 가정할 경우 해당 PDL 값에 따라 OneDrive가 프로비전됩니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-175">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="995ca-176">Multi-Geo 검색 구성</span><span class="sxs-lookup"><span data-stu-id="995ca-176">Configuring Multi-Geo search</span></span>

<span data-ttu-id="995ca-177">Multi-Geo 테넌트에는 검색 쿼리가 테넌트 내의 어디에서든지 결과를 반환할 수 있도록 하는 집계 검색 기능이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-177">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="995ca-178">기본적으로 각 검색 인덱스가 관련 지리적 위치 내에 있더라도, 이러한 진입점에서 검색을 수행하면 집계 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-178">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="995ca-179">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="995ca-179">OneDrive for Business</span></span>

- <span data-ttu-id="995ca-180">Delve</span><span class="sxs-lookup"><span data-stu-id="995ca-180">Delve</span></span>

- <span data-ttu-id="995ca-181">SharePoint 홈</span><span class="sxs-lookup"><span data-stu-id="995ca-181">SharePoint Home</span></span>

- <span data-ttu-id="995ca-182">검색 센터</span><span class="sxs-lookup"><span data-stu-id="995ca-182">Search Center</span></span>

<span data-ttu-id="995ca-183">또한 SharePoint 검색 API를 사용하는 사용자 지정 검색 응용 프로그램에 대해 Multi-Geo 검색 기능을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-183">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="995ca-184">제한 사항 및 차이점을 비롯한 지침을 보려면 [비즈니스용 OneDrive Multi-Geo 검색 구성](configure-search-for-multi-geo.md)을 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="995ca-184">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="995ca-185">비즈니스용 OneDrive Multi-Geo 구성 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="995ca-185">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="995ca-p116">다음은 비즈니스용 OneDrive Multi-Geo를 회사에 광범위하게 롤아웃하기 전에 유효성 검사 계획에 포함할 수 있는 몇 가지 기본적인 사용 사례입니다. 이러한 테스트와 회사에 적합한 추가 사용 사례를 완료했으면 초기 파일럿 그룹에 사용자를 추가하는 작업을 계속하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="995ca-188">**비즈니스용 OneDrive**</span><span class="sxs-lookup"><span data-stu-id="995ca-188">**OneDrive for Business**</span></span>

<span data-ttu-id="995ca-p117">Office 365 앱 시작 관리자에서 OneDrive를 선택하고, 사용자의 PDL에 따라 사용자에 대해 적절한 지리적 위치로 자동으로 이동되는지 확인합니다. 비즈니스용 OneDrive는 해당 위치에서 프로비전을 시작합니다. 프로비전이 끝나면 일부 문서를 업로드 및 다운로드해보세요.</span><span class="sxs-lookup"><span data-stu-id="995ca-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="995ca-192">**OneDrive 모바일 앱**</span><span class="sxs-lookup"><span data-stu-id="995ca-192">**OneDrive Mobile App**</span></span>

<span data-ttu-id="995ca-p118">테스트 계정 자격 증명을 사용하여 OneDrive 모바일 앱에 로그인합니다. 비즈니스용 OneDrive 파일을 볼 수 있고, 모바일 장치에서 해당 파일과 상호 작용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="995ca-195">**OneDrive 동기화 클라이언트**</span><span class="sxs-lookup"><span data-stu-id="995ca-195">**OneDrive Sync Client**</span></span>

<span data-ttu-id="995ca-p119">OneDrive 동기화 클라이언트가 로그인 시 비즈니스용 OneDrive 지리적 위치를 자동으로 감지하는지 확인합니다. 동기화 클라이언트를 다운로드해야 할 경우 OneDrive 라이브러리에서 **동기화**를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="995ca-198">**Office 응용 프로그램**</span><span class="sxs-lookup"><span data-stu-id="995ca-198">**Office Applications**</span></span>

<span data-ttu-id="995ca-p120">Word와 같은 Office 응용 프로그램에서 로그인하여 비즈니스용 OneDrive에 액세스할 수 있는지 확인합니다. Office 응용 프로그램을 열고 "OneDrive- <TenantName>"을 선택합니다. Office에서 사용자의 OneDrive 위치가 감지되고 열 수 있는 파일이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="995ca-202">**공유**</span><span class="sxs-lookup"><span data-stu-id="995ca-202">**Sharing**</span></span>

<span data-ttu-id="995ca-p121">OneDrive 파일을 공유해 보세요. 사용자 선택 기능에는 모든 SharePoint Online 사용자가 해당 지리적 위치에 관계없이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="995ca-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
