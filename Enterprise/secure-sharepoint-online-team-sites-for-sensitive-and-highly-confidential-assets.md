---
title: 민감한 극비 자산에 대한 SharePoint Online 팀 사이트 보안
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: '요약: Contoso 중요 한 보호 및 기밀 사항이 SharePoint Online 팀 사이트에 대 한 더 쉽게을 구현 하는 방법 아직 보안 임원 및 해당 연구 (영문)에 대 한 공동 작업 가운데에 맞춥니다.'
ms.openlocfilehash: 23511e4156bb04e8bacf970913b00ed36e8ff9c8
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914863"
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a><span data-ttu-id="1dac5-103">민감한 극비 자산에 대한 SharePoint Online 팀 사이트 보안</span><span class="sxs-lookup"><span data-stu-id="1dac5-103">Secure SharePoint Online team sites for sensitive and highly confidential assets</span></span>

 <span data-ttu-id="1dac5-104">**요약:** 어떻게 구현 Contoso 중요 한 보호 및 기밀 사항이 SharePoint Online 팀 임원 및 해당 하는 리서치 센터에 대 한 보안 하면서도 쉽게, 공동 작업을 위한 사이트입니다.</span><span class="sxs-lookup"><span data-stu-id="1dac5-104">**Summary:** How Contoso implemented sensitive protection and highly confidential SharePoint Online team sites for easier, yet secure, collaboration for executives and its research centers.</span></span>
  
<span data-ttu-id="1dac5-p101">Contoso의 임원진 Office 365를 사용 하 고 임원 저장할 수에 관계 없이 공동 작업에 대 한 단일 위치에서 해당 파일을 저장 하려고 합니다. 마찬가지로, Contoso의 연구 부서-파리, 모스크바, 뉴욕, 베이징, 및 Bangalore 부서와-팀 간에 쉽게 액세스 하 고 더 개방 공동 작업에 대 한 클라우드로의 온-프레미스 디지털 자산을 전환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dac5-p101">The executive leadership of Contoso want to use Office 365 and store their files in a single location for collaboration, regardless of where an executive might be. Similarly, Contoso's research departments—with divisions in Paris, Moscow, New York, Beijing, and Bangalore—would like to transition their on-premises digital assets to the cloud for easier access and more open collaboration across teams.</span></span>
  
<span data-ttu-id="1dac5-p102">그러나 두이 경우 모두에서 이러한 리소스에 대 한 액세스를 보거나, IT 담당자가 관리 하는 사이트에 대 한 지속적인 사용 권한으로 변경할 수 있는 사용자의 하위 집합으로 제한 이어야 합니다. 또한 일부 자원은 실수로 또는 의도적으로 하는 경우에, 분산 암호화 해야 하며 보거나 해당 내용을 변경 하려면 액세스 권한이 없는 사용자에 게를 방지 하기 위해 사용 권한이.</span><span class="sxs-lookup"><span data-stu-id="1dac5-p102">However, in both of these cases, access to these resources must be restricted to the subset of people who are allowed to view or change them, with ongoing permissions for the site administered by IT staff. Additionally, even if some resources are intentionally or unintentionally distributed, they must be encrypted and have permissions to prevent those who do not have access to view or change their contents.</span></span>
  
<span data-ttu-id="1dac5-109">Contoso의 보안 및 SharePoint 관리자의 IT 부서 중요 한 보호 하 고 매우 기밀 SharePoint Online 팀 사이트를 사용 하 여 그림 1에 표시 된 것과 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dac5-109">Security and SharePoint administrators in Contoso's IT department decided to use sensitive protection and highly-confidential SharePoint Online team sites, as shown in Figure 1.</span></span>
  
<span data-ttu-id="1dac5-110">**중요 한 보호 및 기밀 사항이 SharePoint Online 팀 사이트의 그림 1: 비교**</span><span class="sxs-lookup"><span data-stu-id="1dac5-110">**Figure 1: Comparison of sensitive protection and highly confidential SharePoint Online team sites**</span></span>

![중요한 보호 및 높은 수준의 기밀 SharePoint Online 팀 사이트](media/Contoso-Poster/SP-Solution.png)
  
<span data-ttu-id="1dac5-112">자신의 임원 및 팀이 연구 (영문)에 대 한 보안 SharePoint Online 팀 사이트를 만들려면 다음이 단계를 사용 하는 Contoso 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dac5-112">Contoso used these steps to create secure SharePoint Online team sites for their executives and research teams:</span></span>
  
1. <span data-ttu-id="1dac5-113">**임원** 중요 한 SharePoint Online 팀 사이트 만들기</span><span class="sxs-lookup"><span data-stu-id="1dac5-113">Create an **Executives** sensitive SharePoint Online team site</span></span>
    
    <span data-ttu-id="1dac5-114">새 팀 사이트 편집 SharePoint 사용 권한 수준 및 SharePoint 관리자 계정의 작은 집합을 사용 하 여 모든 권한 권한 수준 가진 소유자로 구성원으로 중역에 대 한 기존 Azure Active Directory (AD) 그룹을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1dac5-114">The new team site uses existing Azure Active Directory (AD) groups for executives as members with the Edit SharePoint permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level.</span></span>
    
2. <span data-ttu-id="1dac5-115">임원 파일 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="1dac5-115">Migrate executives files</span></span>
    
    <span data-ttu-id="1dac5-116">새 임원 SharePoint Online 팀 사이트에 기존 온-프레미스 임원 파일 및 폴더를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dac5-116">Move existing on-premises executive files and folders to the new Executives SharePoint Online team site.</span></span>
    
3. <span data-ttu-id="1dac5-117">**리서치** 기밀 사항이 SharePoint Online 팀 사이트 만들기</span><span class="sxs-lookup"><span data-stu-id="1dac5-117">Create a **Research** highly confidential SharePoint Online team site</span></span>
    
    <span data-ttu-id="1dac5-p103">새 팀 사이트의 모든 권한 권한 수준 가진 소유자로 편집 사용 권한 수준 및 SharePoint 관리자 계정의 작은 집합을 사용 하 여 구성원으로 Azure AD 연구 팀 그룹을 기존를 사용합니다. 파일 연구에 할당 하는 AIP 레이블 하면 암호화 된 연구 (영문) 그룹의 구성원만 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dac5-p103">The new team site uses existing Azure AD research team groups as members with the Edit permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level. An AIP label assigned to research files ensures that they are encrypted and only members of a research group can open them.</span></span>
    
4. <span data-ttu-id="1dac5-120">리서치 파일 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="1dac5-120">Migrate research files</span></span>
    
    <span data-ttu-id="1dac5-121">연구 팀이 기존 온-프레미스 파일 및 폴더를 새 리서치 SharePoint Online 팀 사이트를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dac5-121">Move existing research team on-premises files and folders to the new Research SharePoint Online team site.</span></span>
    
<span data-ttu-id="1dac5-p104">결과 두 공동 작업 사이트 액세스 보안 및 SharePoint 관리자에 의해 제어 조밀 하 게 됩니다. 기밀 AIP 매우 레이블이 있는 파일에 대 한 리서치 팀 사이트 외부 배포 되는 경우에 이러한 암호화 되 고 연구 팀 구성원에 의해 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dac5-p104">The result is two collaboration sites whose access is tightly controlled by security and SharePoint administrators. For files with the Highly Confidential AIP label, even if they are distributed outside the Research team site, they are encrypted and can only be opened by a member of a research team.</span></span>
  
<span data-ttu-id="1dac5-124">자세한 내용은 [SharePoint Online 보안 사이트 및 파일을](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1dac5-124">For more information, see [Secure SharePoint Online sites and files](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).</span></span>
  
 <span data-ttu-id="1dac5-125">데모, 개념 증명 또는 개발/테스트 하면이 설정, [개발/테스트 환경에서 SharePoint Online 보안 사이트](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test)를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dac5-125">To set this up for demonstration, proof-of-concept, or dev/test, see [Secure SharePoint Online sites in a dev/test environment](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1dac5-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1dac5-126">See Also</span></span>

[<span data-ttu-id="1dac5-127">Contoso Corporation에 대 한 엔터프라이즈 시나리오</span><span class="sxs-lookup"><span data-stu-id="1dac5-127">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="1dac5-128">Microsoft 클라우드의 Contoso</span><span class="sxs-lookup"><span data-stu-id="1dac5-128">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="1dac5-129">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="1dac5-129">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="1dac5-130">데이터베이스를 늘이기</span><span class="sxs-lookup"><span data-stu-id="1dac5-130">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="1dac5-131">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="1dac5-131">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




