---
title: 비즈니스 다중-지리적으로 분산 테 넌 트 구성에 대 한 OneDrive
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: OneDrive에 대 한 비즈니스 다중-지리적으로 분산을 구성 하는 방법에 알아봅니다.
ms.openlocfilehash: 56268acd319684ecb713e674b8accbe311d08dce
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="bc9e4-103">비즈니스 다중-지리적으로 분산 테 넌 트 구성에 대 한 OneDrive</span><span class="sxs-lookup"><span data-stu-id="bc9e4-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="bc9e4-p101">OneDrive에 대 한 테 넌 트에 대 한 비즈니스 다중-지리적으로 분산을 구성 하기 전에 반드시 [OneDrive에 대 한 비즈니스 다중-지리적으로 분산에 대 한 계획](plan-for-multi-geo.md)을 읽어야 합니다. 이 문서의 단계를 수행 하려면 사용 하려는 위치와 해당 위치에 대 한 프로 비전 할 테스트 사용자 목록이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="bc9e4-106">테 넌 트에 Office 365 계획의 다중-지리적으로 분산 기능 추가</span><span class="sxs-lookup"><span data-stu-id="bc9e4-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="bc9e4-p102">OneDrive에 대 한 비즈니스 다중-지리적으로 분산을 사용 하려면 _Office 365의 다중-지리적으로 분산 기능_ 계획을 해야 합니다. 이 계획 테 넌 트에 추가할 계정 팀과 함께 작동 합니다. 계정 팀 적절 한 라이선스 전문가와 연결 하 고 구성 하는 테 넌 트를 가져올 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="bc9e4-p103">_Office 365의 다중-지리적으로 분산 기능_ 계획 하는 내용의 사용자 수준 서비스 계획입니다. 위성 위치를 호스트 하려는 각 사용자에 게 라이선스가 필요 합니다. 위성 위치에서 사용자를 추가할 때는 시간에 따른 추가 라이선스를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="bc9e4-113">_Office 365의 다중-지리적으로 분산 기능_ 계획 테 넌 트이 프로비저닝 되었으며, **지리적 위치** 탭 [OneDrive 관리 센터](https://admin.onedrive.com)에서 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a><span data-ttu-id="bc9e4-114">테 넌 트에 데이터 위치 허용 (ADL)을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-114">Set the Allowed Data Locations (ADL) to your tenant</span></span>

<span data-ttu-id="bc9e4-p104">비즈니스용 OneDrive를 사용 하 여 저장할 SharePoint에 대해 허용 되는 데이터 위치 각 지리적 위치에 대 한 설정 해야 합니다. 사용 가능한 지리적 위치는 다음 표와에서 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p104">You must set an Allowed Data Location for SharePoint for each geo-location where you want to use OneDrive for Business. Available geo-locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="bc9e4-117"><strong>위치</strong></span><span class="sxs-lookup"><span data-stu-id="bc9e4-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="bc9e4-118"><strong>코드</strong></span><span class="sxs-lookup"><span data-stu-id="bc9e4-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="bc9e4-119">북미</span><span class="sxs-lookup"><span data-stu-id="bc9e4-119">North America</span></span></td>
<td align="left"><span data-ttu-id="bc9e4-120">이름</span><span class="sxs-lookup"><span data-stu-id="bc9e4-120">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc9e4-121">유럽 동쪽 중간 / / 아프리카</span><span class="sxs-lookup"><span data-stu-id="bc9e4-121">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="bc9e4-122">EUR</span><span class="sxs-lookup"><span data-stu-id="bc9e4-122">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc9e4-123">아시아 태평양</span><span class="sxs-lookup"><span data-stu-id="bc9e4-123">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="bc9e4-124">APC</span><span class="sxs-lookup"><span data-stu-id="bc9e4-124">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc9e4-125">오스트레일리아</span><span class="sxs-lookup"><span data-stu-id="bc9e4-125">Australia</span></span></td>
<td align="left"><span data-ttu-id="bc9e4-126">오스트레일리아</span><span class="sxs-lookup"><span data-stu-id="bc9e4-126">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc9e4-127">일본</span><span class="sxs-lookup"><span data-stu-id="bc9e4-127">Japan</span></span></td>
<td align="left"><span data-ttu-id="bc9e4-128">일본어</span><span class="sxs-lookup"><span data-stu-id="bc9e4-128">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc9e4-129">캐나다</span><span class="sxs-lookup"><span data-stu-id="bc9e4-129">Canada</span></span></td>
<td align="left"><span data-ttu-id="bc9e4-130">수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-130">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc9e4-131">영국</span><span class="sxs-lookup"><span data-stu-id="bc9e4-131">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="bc9e4-132">GBR</span><span class="sxs-lookup"><span data-stu-id="bc9e4-132">GBR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc9e4-133">한국</span><span class="sxs-lookup"><span data-stu-id="bc9e4-133">Korea</span></span></td>
<td align="left"><span data-ttu-id="bc9e4-134">KOR</span><span class="sxs-lookup"><span data-stu-id="bc9e4-134">KOR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="bc9e4-135">위성 지리적 위치를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="bc9e4-135">To add a satellite geo location</span></span>

1. <span data-ttu-id="bc9e4-136">[OneDrive 관리 센터](https://admin.onedrive.com)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-136">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="bc9e4-137">**지리적으로 분산 위치** 탭으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-137">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="bc9e4-138">**위치 추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-138">Click **Add location**.</span></span>

4. <span data-ttu-id="bc9e4-139">을 추가할 위치를 선택 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-139">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="bc9e4-140">지리적으로 분산 위치와 함께 사용 하려는 도메인을 입력 하 고 **추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-140">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="bc9e4-141">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-141">Click **Close**.</span></span>

<span data-ttu-id="bc9e4-p105">프로 비전 최대 걸릴 수 있습니다는 몇 시간에서 테 넌 트의 크기에 따라 72 시간입니다. 위성 위치의 프로 비전 완료 되 면 전자 메일 확인을 메시지가 나타납니다. 새로운 지리적 위치 OneDrive 관리 센터의 **지리적 위치** 탭에서 지도에 파란색으로 표시 되 면 해당 지리적 위치에 사용자의 기본 데이터 위치를 설정 하려면 작업을 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="bc9e4-p106">새 위성 지리적 위치 기본 설정으로 설정 됩니다. 이렇게 하면 로컬 규정 준수 요구 사항에 따라 해당 지리적 위치를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="bc9e4-147">사용자의 기본 설정된 데이터의 위치 설정</span><span class="sxs-lookup"><span data-stu-id="bc9e4-147">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="bc9e4-p107">필요한 데이터 위치를 사용 하도록 설정한 후에 적절 한 데이터 위치를 사용 하 여 사용자 계정을 업데이트할 수 있습니다. 기본 데이터 위치에 남아 있는 경우 해당 사용자 하는 경우에 모든 사용자에 대 한 기본 설정된 데이터 위치를 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="bc9e4-150">다중-지리적으로 분산 기능 광범위 한 조직에 배포 하기 전에 테스트 사용자 또는 소규모 사용자 그룹에 대 한 유효성 검사를 시작 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-150">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="bc9e4-p108">AAD에는 두 유형의 사용자 개체: 클라우드 사용자와 동기화 된 사용자만. 사용자 유형의 사용자에 대 한 적절 한 지침을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="bc9e4-153">사용자의 기본 설정 데이터 위치 AD 연결을 사용 하 여 동기화</span><span class="sxs-lookup"><span data-stu-id="bc9e4-153">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="bc9e4-p109">Azure Active Directory (AAD)는 온-프레미스 Active Directory (AD) 시스템에서 회사의 사용자는 동기화 하는 경우 자신의 PreferredDataLocation은 AD에 입력 하 고 AAD와 동기화 해야 합니다. 과정에 따라 [Azure AD 연결 동기화: 변경 내용을 기본 구성으로](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) 기본 설정 구성 하려면 데이터 위치 동기화에서 온-프레미스 AD AAD 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="bc9e4-156">표준 사용자 만들기 워크플로의 일부로 사용자의 기본 설정 된 데이터의 위치를 설정를 포함 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-156">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bc9e4-p110">프로 비전 onedrive에 없는 새 사용자에 대 한 사용자의 PDL가 사용자가 비즈니스용 OneDrive에 로그인 하기 전에 전파 하는 변경 내용에 대 한 AAD에 동기화 됨 후 24 시간 이상 기다립니다. (기본 설정된 데이터를 설정 위치는 사용자가 자신의 OneDrive 비즈니스에 대 한 프로 비전 하려면 로그인 하기 전에 되도록 사용자의 새 OneDrive 올바른 위치에 프로 비전 할 됩니다.)</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="bc9e4-159">클라우드 사용자만 기본적으로 사용 되는 데이터 위치 설정</span><span class="sxs-lookup"><span data-stu-id="bc9e4-159">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="bc9e4-160">회사의 사용자가 동기화 되지 않으면는 온-프레미스 Active Directory (AD) 시스템을 Azure Active Directory (AAD) 하는 경우 Office 365 또는 AAD를 만들 때 사용한 누구나 다음 PDL 설정 해야 AAD PowerShell을 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-160">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="bc9e4-p111">이 섹션의 절차에는 [Microsoft Azure Active Directory 모듈에 대 한 Windows PowerShell 모듈](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)필요합니다. 이미 설치 된 AAD PowerShell 하는 경우 최신 버전으로 업데이트를 확인 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="bc9e4-163">Windows PowerShell 용 Microsoft Azure Active Directory 모듈을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-163">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="bc9e4-164">실행 `Connect-MsolService` 테 넌 트에 대 한 전역 관리자 자격 증명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-164">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="bc9e4-p112">각 사용자에 대 한 기본 설정된 데이터 위치를 설정 하려면 [이와](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet을 사용 합니다. 예를 들어:</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p112">Use the [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="bc9e4-p113">기본 데이터 위치 Get-msoluser cmdlet을 사용 하 여 제대로 업데이트 되었는지 확인 하려면 확인할 수 있습니다. 예를 들어:</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

<span data-ttu-id="bc9e4-169">표준 사용자 만들기 워크플로의 일부로 사용자의 기본 설정 된 데이터의 위치를 설정를 포함 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-169">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bc9e4-p114">프로 비전 onedrive에 없는 새 사용자에 대 한 사용자의 PDL 전파 하는 사용자가 SharePoint OneDrive에 로그인 하기 전에 변경에 대해 설정 된 후 24 시간 이상 기다립니다. (기본 설정된 데이터를 설정 위치는 사용자가 자신의 OneDrive 비즈니스에 대 한 프로 비전 하려면 로그인 하기 전에 되도록 사용자의 새 OneDrive 올바른 위치에 프로 비전 할 됩니다.)</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="bc9e4-172">OneDrive 프로 비전 및 PDL의 영향</span><span class="sxs-lookup"><span data-stu-id="bc9e4-172">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="bc9e4-p115">사용자가 이미 테 넌 트에서 만든 OneDrive 사이트를 하는 경우 자신의 PDL 설정 자동으로 움직이지 않습니다가 기존 OneDrive 합니다. 사용자의 OneDrive를 이동 하려면 참조 [비즈니스 지리적으로 분산 이동에 대 한 OneDrive](move-onedrive-between-geo-locations.md) 하십시오 지리적 위치 간에 이동 OneDrive의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="bc9e4-175">사용자는 테 넌 트 내의 OneDrive 사이트가 없는 경우 OneDrive는 구축할 하 여 자신의 PDL 값에 따라에서 사용자에 대 한 PDL 회사의 허용 되는 데이터 위치 (ADLs) 중 하 나와 일치 하는 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-175">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="bc9e4-176">다중-지리적으로 분산 검색 구성</span><span class="sxs-lookup"><span data-stu-id="bc9e4-176">Configuring Multi-Geo search</span></span>

<span data-ttu-id="bc9e4-177">다중-지리적으로 분산 테 넌 트 어디에서 든 지 결과 반환 하도록 검색 쿼리를 허용 집계 검색 기능에는 테 넌 트 내의 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-177">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="bc9e4-178">기본적으로 각 검색 인덱스의 관련 지리적 위치에 위치 하는 경우에 이러한 진입점에서 검색할 집계 결과 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-178">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="bc9e4-179">비즈니스용 OneDrive</span><span class="sxs-lookup"><span data-stu-id="bc9e4-179">OneDrive for business</span></span>

- <span data-ttu-id="bc9e4-180">Delve</span><span class="sxs-lookup"><span data-stu-id="bc9e4-180">Delve</span></span>

- <span data-ttu-id="bc9e4-181">SharePoint 홈</span><span class="sxs-lookup"><span data-stu-id="bc9e4-181">SharePoint Home</span></span>

- <span data-ttu-id="bc9e4-182">검색 센터</span><span class="sxs-lookup"><span data-stu-id="bc9e4-182">Search Center</span></span>

<span data-ttu-id="bc9e4-183">또한 SharePoint 검색 API를 사용 하 여 사용자 지정 검색 응용 프로그램에 대 한 다중-지리적으로 분산 검색 기능을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-183">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="bc9e4-184">모든 제한 및 차이점을 포함 하는 지침에 대 한 [OneDrive에 대 한 비즈니스 다중-지리적으로 분산에 대 한 검색 구성](configure-search-for-multi-geo.md) 을 검토 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-184">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="bc9e4-185">OneDrive 비즈니스 다중-지리적으로 분산 구성에 대 한 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="bc9e4-185">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="bc9e4-p116">다음은 광범위 하 게를 배포 하기 전에 OneDrive에 대 한 비즈니스 다중-지리적으로 분산 회사에 유효성 검사 계획에 포함 하는 것이 좋을 일부 기본 사용 사례입니다. 이러한 테스트 및 회사와 관련 된 모든 추가 사용 사례를 완료 한 후에 초기 파일럿 그룹에 사용자 추가 (영문) 이동 하려면 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="bc9e4-188">**비즈니스용 OneDrive**</span><span class="sxs-lookup"><span data-stu-id="bc9e4-188">**OneDrive for Business**</span></span>

<span data-ttu-id="bc9e4-p117">Office 365 응용 프로그램 시작 관리자에서 OneDrive를 선택 하 고 확인 자동으로 사용자의 PDL에 따라 사용자에 대 한 적절 한 지리적 위치에 전달 됩니다. 비즈니스용 OneDrive 해당 위치에 프로 비전 하는 것을 시작 이제 해야 합니다. 일단 프로 비전된 try 업로드 하 고 일부 문서를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="bc9e4-192">**OneDrive 모바일 응용 프로그램**</span><span class="sxs-lookup"><span data-stu-id="bc9e4-192">**OneDrive Mobile App**</span></span>

<span data-ttu-id="bc9e4-p118">테스트 계정 자격 증명을 사용 하 여 OneDrive 모바일 앱에 로그인 합니다. 비즈니스 파일 비즈니스용 OneDrive를 볼 수 있는 하 고 이러한 모바일 장치에서 상호작용할 수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="bc9e4-195">**OneDrive 동기화 클라이언트**</span><span class="sxs-lookup"><span data-stu-id="bc9e4-195">**OneDrive sync client**</span></span>

<span data-ttu-id="bc9e4-p119">OneDrive 동기화 클라이언트는 자동으로 로그인 할 때 비즈니스 지리적 위치에 대 한 OneDrive을 검색 하는지 확인 합니다. 동기화 클라이언트를 다운로드 해야 하는 경우에 OneDrive 라이브러리에서 **동기화** 클릭 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="bc9e4-198">**Office 응용 프로그램**</span><span class="sxs-lookup"><span data-stu-id="bc9e4-198">**Office applications**</span></span>

<span data-ttu-id="bc9e4-p120">Word와 같은 Office 응용 프로그램에서 로그인 하 여 비즈니스용 OneDrive에 액세스할 수 있는지 확인 합니다. Office 응용 프로그램 및 선택 엽니다 "OneDrive- <TenantName>"입니다. Office는 OneDrive 위치를 검색 하 고 파일을 열 수를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="bc9e4-202">**Sharing**</span><span class="sxs-lookup"><span data-stu-id="bc9e4-202">**Sharing**</span></span>

<span data-ttu-id="bc9e4-p121">OneDrive 파일 공유를 시도 합니다. 사용자 선택에서는 설명의 지리적 위치에 관계 없이 모든 SharePoint online 사용자를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9e4-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
