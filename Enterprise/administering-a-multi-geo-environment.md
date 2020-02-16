---
title: 다중 위치 환경 관리
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: 다중 위치 환경의 SharePoint 및 OneDrive 서비스 관리에 대해 알아봅니다.
ms.openlocfilehash: 483250f8956ba1220c29bb769abef187ac9ec53d
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2020
ms.locfileid: "41974030"
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="63a3a-103">다중 위치 환경 관리</span><span class="sxs-lookup"><span data-stu-id="63a3a-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="63a3a-104">Office 365 서비스가 다중 위치 환경에서 작동하는 방식을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-104">Here's a look at how Office 365 services work in a multi-geo environment.</span></span>

## <a name="audit-log-search"></a><span data-ttu-id="63a3a-105">감사 로그 검색</span><span class="sxs-lookup"><span data-stu-id="63a3a-105">Audit log search</span></span>

<span data-ttu-id="63a3a-106">모든 위성 위치에 대한 통합 [감사 로그](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)는 Office 365 감사 로그 검색 페이지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-106">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your satellite locations is available from the Office 365 audit log search page.</span></span> <span data-ttu-id="63a3a-107">여러 지역의 모든 감사 로그 항목을 볼 수 있습니다. 예를 들어, NAM 및 EUR 지역 사용자의 활동은 하나의 조직 보기에 표시되며, 기존 필터를 적용하여 특정 사용자 활동을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-107">You can see all the audit log entries from across geo locations, for example, NAM & EUR users' activities will show up in one org view and then you can apply existing filters to see specific user's activities.</span></span>

## <a name="bcs-secure-store-apps"></a><span data-ttu-id="63a3a-108">BCS, 보안 저장소, 앱</span><span class="sxs-lookup"><span data-stu-id="63a3a-108">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="63a3a-109">BCS, 보안 저장소 및 앱은 모두 각 위성 위치에서 별도의 인스턴스를 유지하므로, SharePoint Online 관리자는 이러한 서비스를 각 위성 위치와는 별도로 관리하고 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-109">BCS, Secure Store, and Apps all have separate instances in each satellite location, therefore the SharePoint Online administrator should manage and configure these services separately from each satellite location.</span></span>

## <a name="ediscovery"></a><span data-ttu-id="63a3a-110">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="63a3a-110">eDiscovery</span></span> 

<span data-ttu-id="63a3a-111">기본적으로 eDiscovery Manager 또는 다중 지역 테넌트의 관리자는 해당 거주자의 중앙 위치에서만 eDiscovery를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-111">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant.</span></span> <span data-ttu-id="63a3a-112">Office 365 전역 관리자는 다른 사용자들이 eDiscovery를 수행할 수 있도록 하기 위해 eDiscovery 관리자 권한을 할당해야 하며, 해당 준수 보안 필터에서 “Region” 매개 변수를 할당하여 eDiscovery 수행 지역을 위성 위치로 지정해야 합니다. 그렇지 않으면 해당 위성 위치에 대해 eDiscovery가 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-112">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span> <span data-ttu-id="63a3a-113">지역에 대한 준수 보안 필터를 구성하려면 [Office 365 다중 지역 eDiscovery의 구성](multi-geo-ediscovery-configuration.md) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63a3a-113">To configure the Compliance Security Filter for a Region, see [Configure Office 365 Multi-Geo eDiscovery](multi-geo-ediscovery-configuration.md).</span></span>

## <a name="exchange-mailboxes"></a><span data-ttu-id="63a3a-114">Exchange 사서함</span><span class="sxs-lookup"><span data-stu-id="63a3a-114">Exchange mailboxes</span></span>

<span data-ttu-id="63a3a-115">사용자의 Exchange 사서함은 PDL이 변경되면 자동으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-115">Users' Exchange mailboxes are moved automatically if their PDL is changed.</span></span> <span data-ttu-id="63a3a-116">새 사서함이 만들어지면 사용자의 PDL에 값이 설정되지 않은 경우 사용자의 PDL 또는 중앙 위치에 프로비저닝됩니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-116">When a new mailbox is created, it is provisioned to the user's PDL or to the central location if no value has been set for the user's PDL.</span></span>

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="63a3a-117">IP(정보 보호) DLP(데이터 손실 방지) 정책</span><span class="sxs-lookup"><span data-stu-id="63a3a-117">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="63a3a-118">보안 및 적합성 센터에서 비즈니스, SharePoint 및 Exchange 용 OneDrive에 대한 IP DLP 정책을 설정하고 필요에 따라 전체 테넌트 또는 해당 사용자에게 정책의 범위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-118">You can set your IP DLP policies for OneDrive for Business, SharePoint, and Exchange in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users.</span></span> <span data-ttu-id="63a3a-119">예를 들어 위성 위치에 있는 사용자에 대한 정책을 선택하려면 특정 OneDrive에 정책을 적용하고 사용자의 OneDrive URL을 입력하도록 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-119">For example: If you wish to select a policy for a user in a satellite location, select to apply the policy to a specific OneDrive and enter the user's OneDrive url.</span></span> <span data-ttu-id="63a3a-120">DLP 정책 생성에 대한 일반적인 지침은 [데이터 손실 방지 정책 개요](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63a3a-120">See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="63a3a-121">DLP 정책은 각 지리적 위치에 적용할 수 있는지에 따라 자동으로 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-121">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="63a3a-122">지리적 위치에 모든 사용자에 대해 정보 보호 및 데이터 손실 방지 정책을 구현하는 방식은 UI에서 사용할 수 있는 옵션이 아니며, 대신 정책에 대해 적용 가능한 계정을 선택하거나 정책을 모든 계정에 전역적으로 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-122">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable accounts for the policy or apply the policy globally to all accounts.</span></span>

## <a name="microsoft-flow"></a><span data-ttu-id="63a3a-123">Microsoft Flow</span><span class="sxs-lookup"><span data-stu-id="63a3a-123">Microsoft Flow</span></span>

<span data-ttu-id="63a3a-124">위성 위치에 대해 만들어진 흐름은 테넌트의 기본 지리적 위치에 있는 끝점을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-124">Flows created for the satellite location will use the end point located in the default geo location for the tenant.</span></span>  <span data-ttu-id="63a3a-125">Microsoft Flow는 다중 지역 서비스가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-125">Microsoft Flow is not a Multi-Geo service.</span></span> 

## <a name="microsoft-powerapps"></a><span data-ttu-id="63a3a-126">Microsoft PowerApps</span><span class="sxs-lookup"><span data-stu-id="63a3a-126">Microsoft PowerApps</span></span>

<span data-ttu-id="63a3a-127">위성 위치에 대해 만들어진 PowerApp은 테넌트의 중앙 위치에 있는 끝점을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-127">PowerApps created for the satellite location will use the end point located in the central location for the tenant.</span></span> <span data-ttu-id="63a3a-128">Microsoft PowerApps은 다중 지역 서비스가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-128">Microsoft PowerApps is not a Multi-Geo service.</span></span> 

## <a name="onedrive-administrator-experience"></a><span data-ttu-id="63a3a-129">OneDrive 관리자 환경</span><span class="sxs-lookup"><span data-stu-id="63a3a-129">OneDrive Administrator Experience</span></span>

<span data-ttu-id="63a3a-p107">[OneDrive 관리 센터](https://admin.onedrive.com)의 왼쪽 탐색 영역에는 지리적 위치를 보고 관리할 수 있는 지리적 위치 지도를 표시하는 **지리적 위치** 탭이 있습니다. 이 페이지에서 테넌트에 대한 지리적 위치를 추가하거나 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-p107">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

## <a name="security-and-compliance-admin-center"></a><span data-ttu-id="63a3a-132">보안 및 준수 관리 센터</span><span class="sxs-lookup"><span data-stu-id="63a3a-132">Security and Compliance Admin Center</span></span>

<span data-ttu-id="63a3a-133">Multi-Geo 테넌트에 대해 하나의 중앙 준수 센터인 [Office 365 보안 및 준수 센터](https://protection.office.com/?rfr=AdminCenter\#/homepage)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-133">There is one central compliance center for a multi-geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

## <a name="sharepoint-storage-quota"></a><span data-ttu-id="63a3a-134">SharePoint 저장소 할당량</span><span class="sxs-lookup"><span data-stu-id="63a3a-134">SharePoint storage quota</span></span>

<span data-ttu-id="63a3a-135">기본적으로 다중 지역 환경의 모든 지리적 위치는 사용 가능한 테넌트 저장소 할당량을 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-135">By default, all geo locations of a multi-geo environment share the available tenant storage quota.</span></span>  <span data-ttu-id="63a3a-136">특정 지리적 위치에 대해 특정 할당량을 할당하여 저장소 할당량을 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-136">You can also manage the storage quota by allocating a specific quota for a particular geo location.</span></span> <span data-ttu-id="63a3a-137">자세한 내용은 [다중 지역 환경에서 SharePoint 저장소 할당량](sharepoint-multi-geo-storage-quota.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63a3a-137">For more information, see [SharePoint storage quotas in multi-geo environments](sharepoint-multi-geo-storage-quota.md).</span></span>

## <a name="sharing"></a><span data-ttu-id="63a3a-138">공유</span><span class="sxs-lookup"><span data-stu-id="63a3a-138">Sharing</span></span>

<span data-ttu-id="63a3a-139">관리자는 각 위치에 대한 공유 정책을 설정하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-139">Administrators can set and manage sharing policies for each of their locations.</span></span> <span data-ttu-id="63a3a-140">각 지리적 위치에 있는 OneDrive 및 SharePoint 사이트는 해당 지리적 특정 공유 설정만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-140">The OneDrive and SharePoint sites in each geo location will honor only the corresponding geo specific sharing settings.</span></span> <span data-ttu-id="63a3a-141">(예를 들어, 중앙 위치에 대한 [외부 공유](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)는 허용하지만 위성 위치의 외부 공유나 그 반대에 대해서는 허용할 수 없습니다.) 공유 설정에서는 지리적 위치간에 공유 제한을 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-141">(For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa.) Note that the sharing settings do not allow configuring sharing limitations between geo locations.</span></span>

## <a name="taxonomy"></a><span data-ttu-id="63a3a-142">분류</span><span class="sxs-lookup"><span data-stu-id="63a3a-142">Taxonomy</span></span>

<span data-ttu-id="63a3a-143">우리는 지리적 위치에서 엔터프라이즈 관리 메타 데이터에 대한 통합 [분류](https://docs.microsoft.com/sharepoint/managed-metadata)를 지원하며 마스터는 회사의 중앙 위치에서 호스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-143">We support a unified [taxonomy](https://docs.microsoft.com/sharepoint/managed-metadata) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company.</span></span> <span data-ttu-id="63a3a-144">전역 분류를 중앙 위치에서 관리하고 위치 관련 용어만 위성 위치의 분류에 추가하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-144">We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite location's Taxonomy.</span></span> <span data-ttu-id="63a3a-145">전역 분류 용어는 위성 위치에 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-145">Global taxonomy terms will synchronize to the satellite locations.</span></span>

<span data-ttu-id="63a3a-146">자세한 내용 및 개발자 지침은 [다중 지역 테넌트의 메타 데이터 관리](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-managedmetadata)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63a3a-146">See [Manage metadata in a multi-geo tenant](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-managedmetadata) for additional details and for developer guidance.</span></span>

## <a name="user-profile-application"></a><span data-ttu-id="63a3a-147">사용자 프로필 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="63a3a-147">User Profile Application</span></span>

<span data-ttu-id="63a3a-148">[사용자 프로필 응용 프로그램](https://docs.microsoft.com/sharepoint/manage-user-profiles)은 각 지리적 위치에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-148">There is a [user profile application](https://docs.microsoft.com/sharepoint/manage-user-profiles) in each geo location.</span></span> <span data-ttu-id="63a3a-149">각 사용자의 프로필 정보는 지리적 위치에서 호스팅되며 해당 지리적 위치의 관리자가 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-149">Each user's profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="63a3a-150">사용자 정의 프로필 속성이 있으면 지리적 위치 간에 동일한 프로필 스키마를 사용하고 모든 지리적 위치에 또는 필요할 때 사용자 지정 프로필 속성을 채우는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-150">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed.</span></span> <span data-ttu-id="63a3a-151">프로그래밍 방식으로 사용자 프로필 데이터를 채우는 방법에 대한 지침은 [대량 사용자 프로필 업데이트 API](https://docs.microsoft.com/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63a3a-151">For guidance regarding how to populate user profile data programmatically, please refer to the [Bulk User Profile Update API](https://docs.microsoft.com/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).</span></span>

<span data-ttu-id="63a3a-152">자세한 내용 및 개발자 지침은 [다중 지역 테넌트의 사용자 프로필 작업](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-userprofileexperience)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63a3a-152">See [Work with user profiles in a multi-geo tenant](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-userprofileexperience) for additional details and for developer guidance.</span></span>

## <a name="video-portal"></a><span data-ttu-id="63a3a-153">비디오 포털</span><span class="sxs-lookup"><span data-stu-id="63a3a-153">Video Portal</span></span>

<span data-ttu-id="63a3a-154">다중 지역 테넌트의 경우 O365 비디오 포털은 기본 지역에서만 제공되며 모든 사용자는 해당 중앙 포털 URL로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-154">In a multi-geo tenant, the O365 Video Portal is served only from default geo and all users will be redirected to that central portal url.</span></span> <span data-ttu-id="63a3a-155">따라서 해당 지역의 RMS(원격 미디어 서비스)가 다음과 같이 중앙 위치를 기반으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-155">Hence, the Remote Media Service (RMS) for that region will be used, as follows based on your central location.</span></span>

<span data-ttu-id="63a3a-156">스트림은 현재 다음 지역에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-156">Stream is currently available in the following regions:</span></span>

- <span data-ttu-id="63a3a-157">북아메리카, 미국에서 호스팅 됨.</span><span class="sxs-lookup"><span data-stu-id="63a3a-157">North America, hosted in the United States</span></span> 
- <span data-ttu-id="63a3a-158">유럽</span><span class="sxs-lookup"><span data-stu-id="63a3a-158">Europe</span></span>
- <span data-ttu-id="63a3a-159">아시아 태평양</span><span class="sxs-lookup"><span data-stu-id="63a3a-159">Asia Pacific</span></span>

<span data-ttu-id="63a3a-160">그러나 현재 Office 365 비디오가 지원되는 다음 지역에서는 스트림을 아직 사용할 수 없으므로 이러한 로컬 인스턴스의 경우 지원되는 가장 가까운 지역에 있는 RMS를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63a3a-160">However, Stream is not yet available in the following regions that are currently supported for Office 365 Video, therefore for these local instances, we will use the RMS that is in the closest supported region.</span></span>

- <span data-ttu-id="63a3a-161">오스트레일리아</span><span class="sxs-lookup"><span data-stu-id="63a3a-161">Australia</span></span>
- <span data-ttu-id="63a3a-162">캐나다</span><span class="sxs-lookup"><span data-stu-id="63a3a-162">Canada</span></span>
- <span data-ttu-id="63a3a-163">인도</span><span class="sxs-lookup"><span data-stu-id="63a3a-163">India</span></span>
- <span data-ttu-id="63a3a-164">영국</span><span class="sxs-lookup"><span data-stu-id="63a3a-164">United Kingdom</span></span>
