---
title: 다중 위치 환경 관리
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 다중 위치 환경의 SharePoint 및 OneDrive 서비스 관리에 대해 알아봅니다.
ms.openlocfilehash: 12da695b44c5102c985a8d64960b1d20e092c8cd
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "21550061"
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="58f10-103">다중 위치 환경 관리</span><span class="sxs-lookup"><span data-stu-id="58f10-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="58f10-104">OneDrive 및 SharePoint 서비스가 다중 위치 환경에서 작동하는 방식을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="58f10-105">OneDrive 관리자 환경</span><span class="sxs-lookup"><span data-stu-id="58f10-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="58f10-p101">[OneDrive 관리 센터](https://admin.onedrive.com)의 왼쪽 탐색 영역에는 지리적 위치를 보고 관리할 수 있는 지리적 위치 지도를 표시하는 **지리적 위치** 탭이 있습니다. 이 페이지에서 테넌트에 대한 지리적 위치를 추가하거나 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="58f10-108">분류</span><span class="sxs-lookup"><span data-stu-id="58f10-108">Taxonomy</span></span>

<span data-ttu-id="58f10-p102">회사에 대한 중앙 위치에 마스터가 호스트된 상태로, 여러 지리적 위치의 엔터프라이즈 관리 메타데이터에 대해 통합된 [분류](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC)를 지원합니다. 중앙 위치에서 전역 분류를 관리하고, 위치별 용어는 위성 지리적 위치의 불륨에만 추가하는 것이 좋습니다. 전역 분류는 위성 지리적 위치와 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="58f10-112">공유</span><span class="sxs-lookup"><span data-stu-id="58f10-112">Sharing</span></span>

<span data-ttu-id="58f10-p103">관리자는 해당 위치 각각에 대해 공유 정책을 설정하고 관리할 수 있습니다. 각 지리적 위치의 OneDrive 사이트에는 해당 지역별 공유 설정만 적용됩니다. (예를 들어 중앙 위치에 대해 [외부 공유](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)를 허용한 경우 위성 위치에는 허용할 수 없으며, 그 반대의 경우도 마찬가지입니다.) 공유 설정은 지리적 위치 간에 공유 제한을 구성하는 것을 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. (For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa.) Note that the sharing settings do not allow configuring sharing limitations between geo-locations.</span></span>

<span data-ttu-id="58f10-p104">OneDrive Multi-Geo의 경우, 공유 설정이 테넌트 전체에서 동기화되지 않으므로 각 지리적 위치에서 관리해야 합니다. 공유를 관리하려면 [OneDrive 관리 센터 공유 설정](https://admin.onedrive.com/?v=SharingSettings) 페이지를 참조하세요. 기본적으로 외부 공유는 각 위성 위치의 모든 사용자에게 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-p104">For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant. To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="58f10-119">사용자 프로필 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="58f10-119">User Profile Application</span></span>

<span data-ttu-id="58f10-p105">각 지리적 위치에는 [사용자 프로필 응용 프로그램](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723)이 있습니다. 각 사용자의 프로필 정보가 해당 지리적 위치에 호스트되며 해당 지리적 위치의 관리자가 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="58f10-p106">사용자 지정 프로필 속성이 있으면 지리적 위치 간에 동일한 프로필 스키마를 사용하고 모든 지리적 위치에 또는 필요할 때 사용자 지정 프로필 속성을 채우는 것이 좋습니다. 프로그래밍 방식으로 사용자 프로필 데이터를 채우는 방법에 대한 지침을 보려면 [사용자 프로필 대량 업데이트 API](https://docs.microsoft.com/ko-KR/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="58f10-p106">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed. For guidance regarding how to populate user profile data programmatically, please refer to the [Bulk User Profile Update API](https://docs.microsoft.com/ko-KR/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="58f10-124">BCS, 보안 저장소, 앱</span><span class="sxs-lookup"><span data-stu-id="58f10-124">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="58f10-125">BCS, 보안 저장소 및 앱은 모두 별도의 지리적 인스턴스를 유지하므로, SharePoint Online 관리자는 이러한 항목을 제공하려는 각 지리적 인스턴스에서 이러한 서비스를 관리하고 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-125">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="58f10-126">보안 및 준수 관리 센터</span><span class="sxs-lookup"><span data-stu-id="58f10-126">Security and Compliance Admin Center</span></span>

<span data-ttu-id="58f10-127">Multi-Geo 테넌트에 대해 하나의 중앙 준수 센터인 [Office 365 보안 및 준수 센터](https://protection.office.com/?rfr=AdminCenter\#/homepage)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-127">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="58f10-128">IP(정보 보호) DLP(데이터 손실 방지) 정책</span><span class="sxs-lookup"><span data-stu-id="58f10-128">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="58f10-p107">보안 및 준수 센터에서 비즈니스용 OneDrive에 대한 IP DLP 정책을 설정하고 필요에 따라 정책 범위를 전체 테넌트 또는 해당 사용자로 지정할 수 있습니다. 예를 들어, 위성 위치의 OneDrive 사용자에 대한 정책을 선택하려는 경우 해당 정책을 특정 OneDrive에 적용하고 사용자의 OneDrive URL을 입력합니다. DLP 정책 생성에 대한 일반 지침을 보려면 [데이터 손실 방지 정책 개요](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="58f10-p107">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="58f10-132">DLP 정책은 각 지리적 위치에 적용할 수 있는지에 따라 자동으로 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-132">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="58f10-133">지리적 위치에 모든 사용자에 대해 정보 보호 및 데이터 손실 방지 정책을 구현하는 방식은 UI에서 사용할 수 있는 옵션이 아니며, 대신 정책에 대해 적용 가능한 OneDrive 계정을 선택하거나 정책을 모든 OneDrive 계정에 전역적으로 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-133">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="58f10-134">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="58f10-134">eDiscovery</span></span> 

<span data-ttu-id="58f10-p108">기본적으로 eDiscovery 관리자 또는 다중 위치 테넌트의 관리자는 해당 테넌트의 중앙 위치에서만 eDiscovery를 수행할 수 있습니다. 위성 위치에 대한 eDiscovery를 수행할 수 있는 기능을 지원하기 위해 "Region"이라는 새로운 준수 보안 필터 매개 변수를 PowerShell을 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-p108">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="58f10-137">Office 365 전역 관리자는 다른 사용자들이 eDiscovery를 수행할 수 있도록 하기 위해 eDiscovery 관리자 권한을 할당해야 하며, 해당 준수 보안 필터에서 “Region” 매개 변수를 할당하여 eDiscovery 수행 지역을 위성 위치로 지정해야 합니다. 그렇지 않으면 해당 위성 위치에 대해 eDiscovery가 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-137">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="58f10-p109">특정 지리적 위치에 대해 eDiscovery 관리자(manager) 또는 관리자(administrator) 역할이 설정되면 해당 eDiscovery 관리자(manager) 또는 관리자(administrator)만 해당 지리적 위치에 있는 SharePoint 사이트 및 OneDrive 사이트에 대해 eDiscovery 검색 작업을 수행할 수 있습니다. eDiscovery 관리자(manager) 또는 관리자(administrator)가 지정된 지역 외부의 SharePoint 또는 OneDrive 사이트를 검색하려고 하면 결과가 반환되지 않습니다. 또한 지역에 대한 eDiscovery 관리자(manager) 또는 관리자(administrator)가 내보내기를 트리거할 경우 데이터가 해당 지역의 Azure 인스턴스로 내보내집니다. 이를 통해 제어 경계 너머로 콘텐츠가 내보내지지 않게 되므로 조직은 준수 상태를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-p109">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="58f10-142">eDiscovery 관리자가 여러 SharePoint 지역에 걸쳐 검색해야 할 경우 OneDrive 또는 SharePoint 사이트가 있는 대체 지역을 지정하는 eDiscovery 관리자에 대해 다른 사용자 계정을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-142">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="58f10-143"><strong>Multi-Geo 지원 지리적 위치</strong></span><span class="sxs-lookup"><span data-stu-id="58f10-143"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="58f10-144"><strong>SharePoint 내보낸 데이터에 대한 eDiscovery가 이 Azure Blob 데이터 위치에서 수행</strong></span><span class="sxs-lookup"><span data-stu-id="58f10-144"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="58f10-145"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="58f10-145"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="58f10-146">동남아시아 또는 동아시아 데이터 센터</span><span class="sxs-lookup"><span data-stu-id="58f10-146">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="58f10-147"><strong>AUS</strong></span><span class="sxs-lookup"><span data-stu-id="58f10-147"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="58f10-148">동남아시아 또는 동아시아 데이터 센터</span><span class="sxs-lookup"><span data-stu-id="58f10-148">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="58f10-149"><strong>CAN</strong></span><span class="sxs-lookup"><span data-stu-id="58f10-149"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="58f10-150">미국 데이터 센터</span><span class="sxs-lookup"><span data-stu-id="58f10-150">US datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="58f10-151"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="58f10-151"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="58f10-152">유럽 데이터 센터</span><span class="sxs-lookup"><span data-stu-id="58f10-152">Europe datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="58f10-153"><strong>FRA</strong></span><span class="sxs-lookup"><span data-stu-id="58f10-153"><strong>FRA</strong></span></span></td>
<td align="left"><span data-ttu-id="58f10-154">유럽 데이터 센터</span><span class="sxs-lookup"><span data-stu-id="58f10-154">Europe datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="58f10-155"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="58f10-155"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="58f10-156">유럽 데이터 센터</span><span class="sxs-lookup"><span data-stu-id="58f10-156">Europe datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="58f10-157"><strong>KOR</strong></span><span class="sxs-lookup"><span data-stu-id="58f10-157"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="58f10-158">동남아시아 또는 동아시아 데이터 센터</span><span class="sxs-lookup"><span data-stu-id="58f10-158">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="58f10-159"><strong>JPN </strong></span><span class="sxs-lookup"><span data-stu-id="58f10-159"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="58f10-160">동남아시아 또는 동아시아 데이터 센터</span><span class="sxs-lookup"><span data-stu-id="58f10-160">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="58f10-161"><strong>NAM</strong></span><span class="sxs-lookup"><span data-stu-id="58f10-161"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="58f10-162">미국 데이터 센터</span><span class="sxs-lookup"><span data-stu-id="58f10-162">US datacenters</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="58f10-163">지역에 대한 준수 보안 필터를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="58f10-163">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="58f10-164">Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-164">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="58f10-165">다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-165">Enter</span></span>  
    <span data-ttu-id="58f10-166">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="58f10-166">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="58f10-167">$a = Import-PSSession $s -AllowClobber</span><span class="sxs-lookup"><span data-stu-id="58f10-167">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="58f10-168">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="58f10-168">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="58f10-169">예: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="58f10-169">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="58f10-170">추가 매개 변수 및 구문에 대해서는 [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="58f10-170">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="58f10-171">감사 로그 검색</span><span class="sxs-lookup"><span data-stu-id="58f10-171">Audit log search</span></span>

<span data-ttu-id="58f10-p110">모든 지리적 위치에 대한 통합된 [감사 로그](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)를 Office 365 감사 로그 검색 페이지에서 사용할 수 있습니다. 여러 지역의 모든 감사 로그 항목을 볼 수 있습니다. 예를 들어, NAM 및 EUR 지역 사용자의 활동은 하나의 조직 보기에 표시되며, 기존 필터를 적용하여 특정 사용자 활동을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-p110">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
