---
title: EDiscovery에 대 한 파일 컬렉션 자동화
ms.author: chrfox
author: chrfox
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: '요약: eDiscovery를 위해 사용자 컴퓨터에서 파일 컬렉션을 자동화 하는 방법을 알아봅니다.'
ms.openlocfilehash: ccea04f4573a16750f588295fca5621d5abd8498
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077721"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="0d947-103">EDiscovery에 대 한 파일 컬렉션 자동화</span><span class="sxs-lookup"><span data-stu-id="0d947-103">Automate file collection for eDiscovery</span></span>

 <span data-ttu-id="0d947-104">**요약:** EDiscovery에 대 한 사용자 컴퓨터에서 파일 컬렉션을 자동화 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-104">**Summary:** Learn how to automate file collection from user computers for eDiscovery.</span></span>
  
<span data-ttu-id="0d947-105">모든 회사에는 소송 또는 기타 법적 작업 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-105">All companies face the potential of lawsuits or other types of legal action.</span></span> <span data-ttu-id="0d947-106">법적 부서는 이러한 노출을 줄이기 위해 노력 하지만, 소송은 비즈니스 수명에 대 한 사실입니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-106">While legal departments work to reduce that exposure, litigation is a fact of business life.</span></span> <span data-ttu-id="0d947-107">회사는 법적 조치를 취할 때 법률 검색 프로세스를 통해 모든 관련 documentary 자료를 경기장 및 상반 되는 자문 위원에 게 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-107">When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="0d947-108">eDiscovery는 회사에서 전자 양식에 있는 관련 documentary 자료를 재고, 검색, 식별, 보존, 필터링 및 사용 가능 하 게 하는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-108">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form.</span></span> <span data-ttu-id="0d947-109">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online 및 Exchange Online에는 많은 양의 documentary 콘텐츠가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-109">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content.</span></span> <span data-ttu-id="0d947-110">버전에 따라 이러한 제품은 eDiscovery 및 현재 위치 유지 (Lync to Exchange Server)를 지원할 수 있으므로 법률 팀이 지정 된 사례에 대해 가장 관련성이 높은 콘텐츠를 보다 쉽게 색인화 하 고 식별 하 고 유지 하 고 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-110">Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="0d947-111">많은 문서가 사용자 (Custodians) 로컬 컴퓨터에 중앙 위치에 저장 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-111">Many documents are stored on users' (Custodians) local computers, not in a centralized location.</span></span> <span data-ttu-id="0d947-112">이를 통해 SharePoint 2013에서 검색을 수행할 수 없으며, 검색이 불가능 한 경우 eDiscovery에 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-112">This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery.</span></span> <span data-ttu-id="0d947-113">이 솔루션은 Exchange Server 용 로그온 스크립트, System Center Orchestrator 2012 R2 및 Windows PowerShell을 사용 하 여 사용자 컴퓨터에서 documentary 자료의 식별 및 컬렉션을 자동화 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-113">This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="0d947-114">솔루션에서 수행 하는 작업</span><span class="sxs-lookup"><span data-stu-id="0d947-114">What this solution does</span></span>

<span data-ttu-id="0d947-115">이 솔루션은 전역 보안 그룹, 그룹 정책 및 Windows PowerShell 스크립트를 사용 하 여 사용자 로컬 컴퓨터에서 숨겨진 파일 공유로의 콘텐츠 및 Outlook 개인 저장소 (PST) 파일을 찾고, 재고를 관리 하 고 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-115">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share.</span></span> <span data-ttu-id="0d947-116">여기서는 PST 파일을 Exchange Server 2013 또는 Exchange Online으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-116">From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online.</span></span> <span data-ttu-id="0d947-117">그런 다음 SharePoint 2013에서 장기간 저장 하 고 인덱싱하기 위해 System Center Orchestrator 2012 R2 runbook을 사용 하 여 Microsoft Azure의 다른 파일 공유로 모든 파일을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-117">All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013.</span></span> <span data-ttu-id="0d947-118">그런 다음 정기적으로 eDiscovery를 수행 하는 동안 온-프레미스 SharePoint 2013 배포 또는 SharePoint Online에서 eDiscovery 센터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-118">You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="0d947-119">이 솔루션은 robocopy를 사용 하 여 custodian의 컴퓨터에서 중앙 집중식 파일 공유로 파일을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-119">This solution uses robocopy to copy files from custodian's computers to a centralized file share.</span></span> <span data-ttu-id="0d947-120">Robocopy는 열려 있거나 잠겨 있는 파일을 복사 하지 않으므로 PST 파일을 포함 하 여 custodian에서 열린 파일은 수집 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-120">Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected.</span></span> <span data-ttu-id="0d947-121">이러한 항목은 수동으로 수집 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-121">You will have to collect them manually.</span></span> <span data-ttu-id="0d947-122">이 솔루션은 복사할 수 없는 파일과 각 파일의 전체 경로를 명시적으로 식별 하는 목록을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-122">This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="0d947-123">다음 다이어그램에서는 솔루션의 모든 단계와 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-123">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![자동화 된 파일 모음 솔루션 개요](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="0d947-125">범례 \* \* \* \*</span><span class="sxs-lookup"><span data-stu-id="0d947-125">\*\*\*\*Legend\*\*\*\*</span></span>||
|:-----|:-----|
|![자홍 설명선 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="0d947-127">GPO (그룹 정책 개체)를 만든 후 컬렉션 로그온 스크립트와 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-127">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![자홍 설명선 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="0d947-129">Gpo 보안 필터를 구성 하 여 Custodians 그룹에만 GPO를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-129">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![자홍 설명선 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="0d947-131">Custodian가 로그온 되 고 GPO가 실행 되어 컬렉션 로그온 스크립트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-131">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![자홍 설명선 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="0d947-133">컬렉션 로그온 스크립트는 Custodians 컴퓨터의 로컬로 연결 된 모든 드라이브를 인벤토리 하 고, 원하는 파일을 검색 하 고, 해당 위치를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-133">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![자홍 설명선 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="0d947-135">컬렉션 로그온 스크립트는 인벤토리에 포함 된 파일을 준비 서버에 있는 숨겨진 파일 공유에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-135">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![자홍 통화](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="0d947-137">(옵션 A) PST 가져오기 스크립트를 수동으로 실행 하 여 수집 된 PST 파일을 Exchange Server 2013로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-137">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![자홍 설명선 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="0d947-139">(옵션 B) Office 365 가져오기 도구와 프로세스를 사용 하 여 수집 된 PST 파일을 Exchange Online으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-139">(Option B) Using the Office 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![자홍 설명선 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="0d947-141">MoveToColdStorage System Center Orchestrator 2012 R2 runbook을 사용 하 여 수집 된 모든 파일을 장기 저장소에 대 한 Azure 파일 공유로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-141">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![자홍 설명선 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="0d947-143">SharePoint 2013의 콜드 저장소 파일 공유에 있는 파일을 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-143">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![자홍 설명선 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="0d947-145">콜드 저장소 및 온-프레미스 Exchange Server 2013의 콘텐츠에서 eDiscovery를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-145">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![자홍 설명선 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="0d947-147">Office 365에서 콘텐츠에 대 한 eDiscovery를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-147">Perform eDiscovery on content in Office 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="0d947-148">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0d947-148">Prerequisites</span></span>

<span data-ttu-id="0d947-149">이 솔루션을 구성 하려면 대부분의 요소가 필요 하며, eDiscovery에 대해 생각 하는 경우에는 대부분의 요소를 사용 하 고 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-149">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery.</span></span> <span data-ttu-id="0d947-150">특정 구성이 필요 하지 않을 수 있는 요소에 대해서는 기본 구성을 구축 하는 데 필요한 링크를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-150">For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration.</span></span> <span data-ttu-id="0d947-151">솔루션 자체를 구성 하기 전에 기본 구성을 그대로 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-151">You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="0d947-152">기본 구성</span><span class="sxs-lookup"><span data-stu-id="0d947-152">Base configuration</span></span>

|<span data-ttu-id="0d947-153">**요소**</span><span class="sxs-lookup"><span data-stu-id="0d947-153">**Element**</span></span>|<span data-ttu-id="0d947-154">**링크**</span><span class="sxs-lookup"><span data-stu-id="0d947-154">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="0d947-155">AD DS (Active Directory 도메인 서비스) 도메인</span><span class="sxs-lookup"><span data-stu-id="0d947-155">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="0d947-156">온-프레미스 네트워크 로부터의 인터넷 연결</span><span class="sxs-lookup"><span data-stu-id="0d947-156">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="0d947-157">SharePoint 2013 및 System Center Orchestrator 2012 R2를 지원 하기 위한 SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="0d947-157">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="0d947-158">System Center Orchestrator-2012 배포</span><span class="sxs-lookup"><span data-stu-id="0d947-158">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="0d947-159">EDiscovery에 대 한 온-프레미스 또는 Azure 기반 SharePoint 2013 (옵션 A에 필요)</span><span class="sxs-lookup"><span data-stu-id="0d947-159">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="0d947-160">준비를 위해 온-프레미스 파일 공유 서버</span><span class="sxs-lookup"><span data-stu-id="0d947-160">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="0d947-161">PST 가져오기를 위한 온-프레미스 Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="0d947-161">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="0d947-162">CU5 (15.913.22)은 [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-162">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="0d947-163">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="0d947-163">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="0d947-164">System Center Orchestrator-2012 배포</span><span class="sxs-lookup"><span data-stu-id="0d947-164">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="0d947-165">Exchange Online 및 SharePoint Online을 사용 하는 Office 365 (E3 계획) (옵션 B에 필요 함)</span><span class="sxs-lookup"><span data-stu-id="0d947-165">Office 365 (E3 Plan) with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="0d947-166">Office 365 E3 구독에 등록 하려면 [office 365 e3 구독](https://go.microsoft.com/fwlink/p/?LinkId=613504)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d947-166">To sign up for an Office 365 E3 subscription, see [Office 365 E3 subscription](https://go.microsoft.com/fwlink/p/?LinkId=613504).</span></span>  <br/> |
|<span data-ttu-id="0d947-167">가상 컴퓨터를 사용한 Azure 구독</span><span class="sxs-lookup"><span data-stu-id="0d947-167">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="0d947-168">Azure에 등록 하려면 [Windows Azure 구독을](https://go.microsoft.com/fwlink/p/?LinkId=512010) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d947-168">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="0d947-169">온-프레미스 네트워크와 Azure 구독 간의 VPN 연결</span><span class="sxs-lookup"><span data-stu-id="0d947-169">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="0d947-170">Azure 구독과 온-프레미스 네트워크 간에 VPN 터널을 설정 하려면 [온-프레미스 네트워크를 Microsoft Azure virtual network에 연결](https://go.microsoft.com/fwlink/p/?LinkId=613507)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0d947-170">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="0d947-171">Sharepoint 2013 eDiscovery는 SharePoint 및 Exchange Server 2013 및 선택적 Lync Server 2013에서 검색 하도록 구성 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-171">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="0d947-172">이 방식으로 eDiscovery를 구성 하려면 [Configure ediscovery In SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) 및[test Lab Guide: Exchange, Lync, SharePoint 및 Windows 파일 공유 테스트 랩에 대해](https://go.microsoft.com/fwlink/p/?LinkId=393130)ediscovery 구성을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0d947-172">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="0d947-173">SharePoint Online 및 Exchange Online에 대 한 Office 365의 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="0d947-173">eDiscovery in Office 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="0d947-174">Office 365에서 eDiscovery를 구성 하려면 [SharePoint Online에서 Ediscovery 센터 설정을](https://go.microsoft.com/fwlink/p/?LinkId=613628)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d947-174">To configure eDiscovery in Office 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="0d947-175">환경 구성</span><span class="sxs-lookup"><span data-stu-id="0d947-175">Configure the environment</span></span>

<span data-ttu-id="0d947-176">기본 구성을 설정 했으므로 이제 솔루션 자체를 구성 하기 전에 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-176">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="0d947-177">준비 파일 공유</span><span class="sxs-lookup"><span data-stu-id="0d947-177">Staging file share</span></span>

1. <span data-ttu-id="0d947-178">온-프레미스 도메인에서 Custodians 라는 전역 보안 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-178">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="0d947-179">Custodians 컴퓨터에서 수집 된 파일에 대 한 숨겨진 파일 공유를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-179">Create a hidden file share for the files that are collected from Custodians computers.</span></span> <span data-ttu-id="0d947-180">이는 온-프레미스 서버에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-180">This should be on an on-premises server.</span></span> <span data-ttu-id="0d947-181">예를 들어 준비 라는 서버에서 Case $ 라는 파일 공유를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-181">For example, on a server called Staging, create a file share called Cases$.</span></span> <span data-ttu-id="0d947-182">**$** 은이를 숨겨진 공유로 설정 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-182">The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="0d947-183">다음 공유 사용 권한을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-183">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="0d947-184">Custodians: Change, Read</span><span class="sxs-lookup"><span data-stu-id="0d947-184">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="0d947-185">관리자: 모든 권한</span><span class="sxs-lookup"><span data-stu-id="0d947-185">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="0d947-186">신뢰할 수 있는 Exchange 하위 시스템: 변경, 읽기</span><span class="sxs-lookup"><span data-stu-id="0d947-186">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="0d947-187">**보안** 탭을 열고 Custodians 그룹을 추가한 다음 **고급**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-187">Open the **Security** tab, add the Custodians group, and click **Advanced**.</span></span> <span data-ttu-id="0d947-188">Custodians 그룹에 대해 다음 사용 권한을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-188">Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="0d947-189">**유형: Deny**</span><span class="sxs-lookup"><span data-stu-id="0d947-189">**Type: Deny**</span></span>
    
  - <span data-ttu-id="0d947-190">**적용 대상: 현재 폴더, 하위 폴더 및 파일**</span><span class="sxs-lookup"><span data-stu-id="0d947-190">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="0d947-191">**고급 사용 권한을** 클릭 하 고 다음을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-191">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="0d947-192">**특성 읽기**</span><span class="sxs-lookup"><span data-stu-id="0d947-192">**Read attributes**</span></span>
    
  - <span data-ttu-id="0d947-193">**확장 된 특성 읽기**</span><span class="sxs-lookup"><span data-stu-id="0d947-193">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="0d947-194">**사용 권한 읽기**</span><span class="sxs-lookup"><span data-stu-id="0d947-194">**Read permissions**</span></span>
    
6. <span data-ttu-id="0d947-195">다음을 수행 하 여 사례 $ 파일 공유에 대 한 액세스를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-195">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="0d947-196">Custodians 그룹에 사용자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-196">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="0d947-197">서비스 케이스 $ 폴더에 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-197">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="0d947-198">사용자는 준비 서버로 이동 하 여 (예: \\ \\준비 공유로 이동) 사용 가능한 공유를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-198">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available.</span></span> <span data-ttu-id="0d947-199">$ Share가 나열 되어 있는 **경우** 는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-199">You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="0d947-200">서비스 케이스 공유에 대 한 전체 경로를 탐색기에 수동으로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-200">Manually type the full path to the Cases$ share into Explorer.</span></span> <span data-ttu-id="0d947-201">그러면 사례 $ 공유가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-201">This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="0d947-202">이전에 공유에 추가한 파일을 열어 봅니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-202">Try to open the file you previously placed in the share.</span></span> <span data-ttu-id="0d947-203">이는 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-203">This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="0d947-204">로그온 스크립트</span><span class="sxs-lookup"><span data-stu-id="0d947-204">Logon script</span></span>

1. <span data-ttu-id="0d947-205">다음 Windows PowerShell 스크립트를 복사 하 여 메모장에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-205">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. <span data-ttu-id="0d947-206">위의 스크립트를 CollectionScript로 저장 합니다. \ C:\\afcscripts와 같이 쉽게 찾을 수 있는 위치에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-206">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="0d947-207">메모장에서 이동 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-207">Use the Go To feature in Notepad.</span></span> <span data-ttu-id="0d947-208">필요에 따라 다음 사항을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-208">Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="0d947-209">**줄 번호**</span><span class="sxs-lookup"><span data-stu-id="0d947-209">**Line #**</span></span>|<span data-ttu-id="0d947-210">**변경 해야 하는 내용**</span><span class="sxs-lookup"><span data-stu-id="0d947-210">**What you need to change**</span></span>|<span data-ttu-id="0d947-211">**Required/optional**</span><span class="sxs-lookup"><span data-stu-id="0d947-211">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="0d947-212">71</span><span class="sxs-lookup"><span data-stu-id="0d947-212">71</span></span>  <br/> |<span data-ttu-id="0d947-213">**$FileTypes** 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-213">**$FileTypes** variable.</span></span> <span data-ttu-id="0d947-214">스크립트에서 인벤토리 및 수집할 모든 파일 형식 확장명을 배열 변수에 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-214">Include all the file type extensions that you want the script to inventory and collect in the array variable.</span></span> <br/> |<span data-ttu-id="0d947-215">옵션</span><span class="sxs-lookup"><span data-stu-id="0d947-215">Optional</span></span>  <br/> |
|<span data-ttu-id="0d947-216">76 및 77</span><span class="sxs-lookup"><span data-stu-id="0d947-216">76 and 77</span></span>  <br/> |<span data-ttu-id="0d947-217">사용자의 요구에 맞게 **$CaseNo** 변수가 작성 되는 방식을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-217">Change the way the **$CaseNo** variable is built to suit your needs.</span></span> <span data-ttu-id="0d947-218">이 스크립트는 현재 날짜와 시간을 캡처하여 사용자 이름을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-218">The script captures the current date and time and appends the user name to it.</span></span> <br/> |<span data-ttu-id="0d947-219">옵션</span><span class="sxs-lookup"><span data-stu-id="0d947-219">Optional</span></span>  <br/> |
|<span data-ttu-id="0d947-220">80</span><span class="sxs-lookup"><span data-stu-id="0d947-220">80</span></span>  <br/> |<span data-ttu-id="0d947-221">\*\* \\ \\준비\\사례 $\*\* 와 같은 **$CaseRootLocation** 변수를 준비 서버 모음 파일 공유로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-221">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="0d947-222">필수</span><span class="sxs-lookup"><span data-stu-id="0d947-222">Required</span></span>  <br/> |
   
4. <span data-ttu-id="0d947-223">도메인 컨트롤러의 Netlogon 파일 공유에 CollectionScript. ps1 파일을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-223">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="0d947-224">로그온 스크립트 및 Custodians 그룹에 대해 GPO를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-224">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="0d947-225">[그룹 정책의 시작, 종료, 로그온 및 로그 오프 스크립트 사용](https://go.microsoft.com/fwlink/p/?LinkId=614844)항목의 "사용자 로그온 스크립트를 할당 하는 방법" 섹션을 따라 Custodians 그룹에 대 한 로그온 스크립트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-225">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="0d947-226">**보안 필터링**에서 인증 된 사용자를 제거 하 고 Custodians 그룹을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-226">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="0d947-227">PST 가져오기 옵션 A, Exchange Server 2013에 대 한 스크립트</span><span class="sxs-lookup"><span data-stu-id="0d947-227">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="0d947-228">다음 Windows PowerShell 스크립트를 복사 하 여 메모장에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-228">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. <span data-ttu-id="0d947-229">스크립트를 쉽게 찾을 수 있는 위치에 PSTImportScript로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-229">Save the script as PSTImportScript.ps1 in a location that's easy for you to find.</span></span> <span data-ttu-id="0d947-230">예를 들어 간편 하 게 사용할 수 있도록 준비 서버에서 준비 \\ \\\\afcscripts 라는 폴더를 만들고 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-230">For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="0d947-231">필요에 따라 메모장에서 이동 기능을 사용 하 고 다음 사항을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-231">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="0d947-232">**줄 번호**</span><span class="sxs-lookup"><span data-stu-id="0d947-232">**Line #**</span></span>|<span data-ttu-id="0d947-233">**변경 해야 하는 내용**</span><span class="sxs-lookup"><span data-stu-id="0d947-233">**What you need to change**</span></span>|<span data-ttu-id="0d947-234">**Required/optional**</span><span class="sxs-lookup"><span data-stu-id="0d947-234">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="0d947-235">12 </span><span class="sxs-lookup"><span data-stu-id="0d947-235">12</span></span>  <br/> |<span data-ttu-id="0d947-236">**$FolderIdentifier** pst를 가져올 사서함 폴더에 태그를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-236">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into.</span></span> <span data-ttu-id="0d947-237">필요한 경우이를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-237">Change this if necessary.</span></span> <br/> |<span data-ttu-id="0d947-238">옵션</span><span class="sxs-lookup"><span data-stu-id="0d947-238">Optional</span></span>  <br/> |
|<span data-ttu-id="0d947-239">17 </span><span class="sxs-lookup"><span data-stu-id="0d947-239">17</span></span>  <br/> |<span data-ttu-id="0d947-240">**$ConnectionUri** 를 자체 서버로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-240">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="0d947-241">> [!IMPORTANT]**$ConnectionUri**> https가 아닌 http 위치를 가리키는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-241">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https.</span></span> <span data-ttu-id="0d947-242">Https:로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-242">It won't work with https:.</span></span>          |<span data-ttu-id="0d947-243">필수</span><span class="sxs-lookup"><span data-stu-id="0d947-243">Required</span></span>  <br/> |
   
4. <span data-ttu-id="0d947-244">Exchange 신뢰할 수 있는 하위 시스템 계정에 \\ \\준비\\사례 $ 공유에 대 한 읽기, 쓰기 및 실행 권한이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-244">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="0d947-245">PST 가져오기 스크립트에는 다음과 같은 두 개의 입력 매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-245">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="0d947-246">**$SourcePath** 가져올 PST 파일의 위치 (예: \\ \\Staging\\사례 $)입니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-246">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="0d947-247">**$MailboxAlias** 가져온 전자 메일 항목을 받을 대상 사서함의 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-247">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="0d947-248">예를 들어 Staging\Cases $ 경로 \\에서 별칭이 ediscoverymailbox 인 사서함으로 모든 PST 파일을 가져오려면 다음과 같은 스크립트를 실행 합니다. `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`</span><span class="sxs-lookup"><span data-stu-id="0d947-248">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="0d947-249">PST 가져오기 옵션 B, Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0d947-249">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="0d947-250">가져온 PST 파일을 배치할 사서함 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-250">Create the mailbox structure to place the imported PST files into.</span></span> <span data-ttu-id="0d947-251">Exchange Online에서 사용자 사서함을 만드는 방법에 대 한 자세한 내용은[Exchange online에서 사용자 사서함 만들기](https://go.microsoft.com/fwlink/p/?LinkId=615118)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d947-251">For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="0d947-252">콜드 저장소</span><span class="sxs-lookup"><span data-stu-id="0d947-252">Cold storage</span></span>

1. <span data-ttu-id="0d947-253">수집 된 모든 파일이 저장 될 Azure Virtual Machine 파일 공유 (예: \\ \\AZFile1\\contentcoldstorage)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-253">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="0d947-254">기본 콘텐츠 액세스 계정에 최소한 공유 및 모든 하위 폴더와 파일에 대 한 읽기 권한을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-254">Grant the default content access account at least Read permissions to the share and all subfolders and files.</span></span> <span data-ttu-id="0d947-255">SharePoint 2013 검색을 구성 하는 방법에 대 한 자세한 내용은 [Create and configure a Search service application In Sharepoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0d947-255">For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="0d947-256">\\ \\AZFile1\\contentcoldstorage에서 PST 파일을 가져오는 것이 예상 되는 경우 Exchange의 신뢰할 수 있는 하위 시스템 읽기, 쓰기 및 실행 권한을 공유에 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-256">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="0d947-257">자가</span><span class="sxs-lookup"><span data-stu-id="0d947-257">Orchestrator</span></span>

1. <span data-ttu-id="0d947-258">Microsoft 다운로드 센터에서[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) 을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-258">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="0d947-259">**Runbook Designer**를 열고 **연결** 창에서 runbook을 가져올 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-259">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into.</span></span> <span data-ttu-id="0d947-260">**작업** 메뉴를 클릭 하 고 **가져오기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-260">Click the **Actions** menu, and the click **Import**.</span></span> <span data-ttu-id="0d947-261">**가져오기** 대화 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-261">The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="0d947-262">**파일 위치** 상자에 가져올 runbook의 경로 및 파일 이름을 입력 하거나, 줄임표 ( **...**)를 클릭 하 여 가져올 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-262">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="0d947-263">**Runbook 가져오기를** 선택 하 고 **Orchestrator Encrypted data를 가져옵니다**.</span><span class="sxs-lookup"><span data-stu-id="0d947-263">Select **Import runbooks** and **Import Orchestrator encrypted data**.</span></span> <span data-ttu-id="0d947-264">**카운터**, **일정**, **변수**, **컴퓨터 그룹**, **전역 구성 가져오기**및 **기존 전역 구성 덮어쓰기**의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-264">Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="0d947-265">**마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-265">Click **Finish**.</span></span>
    
6. <span data-ttu-id="0d947-266">**MoveFilesToColdStorage** runbook을 다음과 같이 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-266">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="0d947-267">**파일 이동** 작업- **원본 파일** 경로를 모음 파일 공유 (예: \\ \\준비\\사례 $)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-267">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="0d947-268">Azure에서 **대상 폴더** 를 콜드 저장소 파일 공유 (예: \\ \\AZFile1\\contentcoldstorage)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-268">Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="0d947-269">**고유한 이름을 사용 하 여 파일 만들기를**선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-269">Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="0d947-270">**폴더 활동 삭제** - **경로** 를 모음 파일 공유 ( \\ \\예:\\준비 사례 $\\*)로 설정 하 고 **모든 파일 및 하위 폴더 삭제**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-270">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="0d947-271">[Runbook 배포](https://go.microsoft.com/fwlink/p/?LinkId=615120)의 절차에 따라 **MoveToColdStorage** runbook을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-271">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="0d947-272">콜드 저장소에 대 한 SharePoint 온-프레미스 검색</span><span class="sxs-lookup"><span data-stu-id="0d947-272">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="0d947-273">Azure의 콜드 저장소 공유에 대 한 SharePoint 2013 팜에서 새 콘텐츠 원본을 만듭니다 (예: \\ \\AZFile1\\contentcoldstorage).</span><span class="sxs-lookup"><span data-stu-id="0d947-273">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="0d947-274">콘텐츠 원본을 관리 하는 방법에 대 한 자세한 내용은 [Add, edit, or delete a content source In SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d947-274">For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="0d947-275">전체 크롤링을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-275">Start a full crawl.</span></span> <span data-ttu-id="0d947-276">자세한 내용은 [SharePoint Server 2013에서 크롤링 시작, 일시 중지, 다시 시작 또는 중지](https://go.microsoft.com/fwlink/p/?LinkId=615005)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d947-276">For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="0d947-277">솔루션 사용</span><span class="sxs-lookup"><span data-stu-id="0d947-277">Using the solution</span></span>

<span data-ttu-id="0d947-278">이 솔루션을 사용 하는 경우에는 다섯 가지 주요 단계로, PST 파일을 Exchange Server 2013 및 Exchange Online 둘 다로 가져오지 않으려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-278">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online.</span></span> <span data-ttu-id="0d947-279">이 섹션에서는 모든 기능에 대 한 절차를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-279">This section provides you with the procedures for all of them.</span></span> <span data-ttu-id="0d947-280">솔루션과의 기본 상호 작용은 다음과 같은 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-280">Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="0d947-281">Custodians 그룹에서 사용자 구성원 자격을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-281">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="0d947-282">로그온 스크립트에 의해 생성 된 로그 파일을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-282">Review the log files generated by the logon script.</span></span> <span data-ttu-id="0d947-283">FileCopyErrors에는 성공적으로 복사 되지 않은 모든 파일이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-283">The FileCopyErrors.log lists all the files that were not successfully copied.</span></span> <span data-ttu-id="0d947-284">원하는 작업을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-284">You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="0d947-285">PST 가져오기 프로세스 관리</span><span class="sxs-lookup"><span data-stu-id="0d947-285">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="0d947-286">모음 파일을 콜드 저장소로 이동</span><span class="sxs-lookup"><span data-stu-id="0d947-286">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="0d947-287">다른 모든 단계는이 솔루션에 국한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-287">All the other steps are not specific to this solution.</span></span> <span data-ttu-id="0d947-288">SharePoint 2013 및 Office 365 및 Azure에서 수행 하는 표준 관리 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-288">They are standard administrative tasks that you perform in SharePoint 2013, and Office 365 and Azure.</span></span> <span data-ttu-id="0d947-289">이 솔루션은 회사의 요구 사항에 따라 다음과 같이 작업을 수행 하는 데 필요한 지침을 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-289">There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="0d947-290">EDiscovery 사례 및 해당 사례와 연결 된 Custodians을 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-290">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="0d947-291">EDiscovery 사례와 연결 되는 파일 모음 집합 추적</span><span class="sxs-lookup"><span data-stu-id="0d947-291">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="0d947-292">가져오기 타이밍을 조정 하 고 콜드 저장소 단계로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-292">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="0d947-293">Azure에서 사용 되는 파일 공간 관리</span><span class="sxs-lookup"><span data-stu-id="0d947-293">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="0d947-294">Pst를 가져올 사서함 관리</span><span class="sxs-lookup"><span data-stu-id="0d947-294">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="0d947-295">모든 온-프레미스 데이터의 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="0d947-295">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="0d947-296">Custodian 관리</span><span class="sxs-lookup"><span data-stu-id="0d947-296">Custodian management</span></span>

- <span data-ttu-id="0d947-297">개별 사용자에 대 한 자동 파일 수집 프로세스를 시작 하려면 Custodians 그룹에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-297">To start the automated file collection process for an individual user, add them to the Custodians group.</span></span> <span data-ttu-id="0d947-298">다음 번에 사용자가 로그온 하면 그룹 정책을 통해 Custodians 그룹에 할당 된 로그온 스크립트가 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-298">The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="0d947-299">수집 된 파일 모니터링 및 로그 파일 검토</span><span class="sxs-lookup"><span data-stu-id="0d947-299">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="0d947-300">사용자의 컬렉션 폴더에 대 한 모음 \\ \\파일\\공유 (\\예: 준비 사례 $ \*)를 시청 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-300">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user.</span></span> <span data-ttu-id="0d947-301">폴더의 이름은 *yyyyMMddHHmm_UserName* 다음과 같이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-301">The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="0d947-302">수집이 완료 되 면 모음 폴더를 열고 _Log 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-302">When the collection is completed, open the collection folder, and browse to the _Log folder.</span></span> <span data-ttu-id="0d947-303">_Log 폴더에는 다음이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-303">In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="0d947-304">사용자 컴퓨터의 모든 로컬 드라이브 (예: **.xml**, **C .xml**)에 대 한 XML 파일 하나</span><span class="sxs-lookup"><span data-stu-id="0d947-304">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**.</span></span> <span data-ttu-id="0d947-305">이러한 파일에는 이름이 다음과 같이 지정 된 인벤토리 드라이브가 포함 되며 robocopy 작업에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-305">These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="0d947-306">컬렉션 스크립트는 스크립트 자체에 정의한 파일 형식에 대 한 인벤토리 파일에만 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-306">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself.</span></span> <span data-ttu-id="0d947-307">사용자 컴퓨터의 모든 파일에 대 한 인벤토리 항목을 만들지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-307">It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="0d947-308">각 컬렉션에 대해 FileCopyErrors 라는 로그 파일 하나를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-308">One log file named FileCopyErrors.log for each collection run.</span></span> <span data-ttu-id="0d947-309">이 \\ \\파일에는\\서비스 케이스 $\\*와 같이 robocopy에서 파일 모음 공유로 복사할 수 없는 파일 목록이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-309">This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*.</span></span> <span data-ttu-id="0d947-310">이를 검토 하 고 이러한 누락 된 파일에 대해 수행할 작업을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-310">You will need to review this and decide what actions to take for these missed files.</span></span> <span data-ttu-id="0d947-311">일반적으로 필요한 경우 수동으로 수집 해야 하며, 필요 하지 않을 수 있으므로 컬렉션에서 생략할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-311">Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="0d947-312">Exchange Server 2013에 대 한 PST 가져오기 옵션</span><span class="sxs-lookup"><span data-stu-id="0d947-312">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="0d947-313">모음 파일 공유를 호스트 하는 서버에 로그온 하 고 (예: **Staging**) Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-313">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell.</span></span> <span data-ttu-id="0d947-314">Windows PowerShell을 시작 하는 방법에 대 한 자세한 내용은[Windows Server에서 Windows Powershell 시작](https://go.microsoft.com/fwlink/p/?LinkId=615115)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0d947-314">For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="0d947-315">실행 정책을 무제한으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-315">Set the Execution policy to Unrestricted .</span></span> <span data-ttu-id="0d947-316">Windows `Set-ExecutionPolicy Unrestricted -Scope Process` PowerShell에 입력 한 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-316">Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="0d947-317">PSTImportScript 파일을 실행 하 고 **$SourcePath** 및 **$MailboxAlias** 매개 변수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-317">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters.</span></span> <span data-ttu-id="0d947-318">Windows PowerShell 스크립트를 실행 하는 방법에 대 한 자세한 내용은[실행 스크립트](https://go.microsoft.com/fwlink/p/?LinkID=615117)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0d947-318">For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="0d947-319">오류에 대 한 출력을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-319">Review the output for errors.</span></span>
    
5. <span data-ttu-id="0d947-320">같은 이름의 PST 파일을 같은 사서함에 가져오기 전에 사서함 가져오기 요청을 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-320">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request.</span></span> <span data-ttu-id="0d947-321">다음 명령을 실행 하 여이 작업을 `Get-MailboxImportRequest | Remove-MailboxImportRequest`수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-321">Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`.</span></span> <span data-ttu-id="0d947-322">큐에서 개별 요청을 모두 제거할지 묻는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-322">You will be prompted to remove each individual request from the queue.</span></span> <span data-ttu-id="0d947-323">필요에 따라 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-323">Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="0d947-324">PST 가져오기 옵션 B, Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0d947-324">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="0d947-325">수집 된 PST 파일을 Exchange Online에 배치 하려면 [office 365 가져오기 서비스](https://go.microsoft.com/fwlink/p/?LinkId=614938)의 네트워크 업로드 섹션에서 파일을 office 365로 가져오기의 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-325">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Office 365 through the network upload section of [Office 365 Import Service](https://go.microsoft.com/fwlink/p/?LinkId=614938).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="0d947-326">콜드 저장소로 이동</span><span class="sxs-lookup"><span data-stu-id="0d947-326">Move to cold storage</span></span>

1. <span data-ttu-id="0d947-327">[실행 중인 runbook](https://go.microsoft.com/fwlink/p/?LinkId=615123)의 절차에 따라 **MoveToColdStorage** runbook을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-327">Run the **MoveToColdStorage** runbook using the procedures in[Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="0d947-328">장기 저장소 (예 \\ \\\\: AZFile1 contentcoldstorage 및 온-프레미스 모음 파일 공유)에 사용 중인 Azure 파일 공유 (예: \\ \\준비\\사례 $)를 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d947-328">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="0d947-329">파일 및 폴더가 콜드 저장소 파일 공유에 표시 되 고 모음 파일 공유에서 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-329">You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="0d947-330">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="0d947-330">eDiscovery</span></span>

1. <span data-ttu-id="0d947-331">콜드 저장소 파일 공유의 전체 크롤링을 일정으로 실행 하거나 크롤링을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-331">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl.</span></span> <span data-ttu-id="0d947-332">전체 또는 증분 크롤링 시작에 대 한 자세한 내용은 [SharePoint Server 2013에서 크롤링 시작, 일시 중지, 다시 시작 또는 중지](https://go.microsoft.com/fwlink/p/?LinkId=615005)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d947-332">For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="0d947-333">PST 파일에 A 옵션을 사용 하 여 SharePoint 2013에서 eDiscovery 사례를 만들거나, 옵션 B를 사용한 경우 SharePoint Online에서 eDiscovery 사례를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d947-333">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

