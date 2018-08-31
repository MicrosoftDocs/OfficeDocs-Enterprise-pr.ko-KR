---
title: eDiscovery에 대한 파일 컬렉션 자동화
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: '요약: eDiscovery에 대 한 사용자의 컴퓨터에서 파일 컬렉션을 자동화 하는 방법에 알아봅니다.'
ms.openlocfilehash: 12d61d2c43a297001eecf463991654afbcfccb1a
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915753"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="271b9-103">eDiscovery에 대한 파일 컬렉션 자동화</span><span class="sxs-lookup"><span data-stu-id="271b9-103">Automate file collection for eDiscovery</span></span>

 <span data-ttu-id="271b9-104">**요약:** EDiscovery에 대 한 사용자의 컴퓨터에서 파일 컬렉션을 자동화 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-104">**Summary:** Learn how to automate file collection from user computers for eDiscovery.</span></span>
  
<span data-ttu-id="271b9-p101">모든 회사의 소송 또는 다른 유형의 법적 조치 액에 직면해 있습니다. 법률 부서 해당 노출 감소를 작동 하는 동안 소송 보존은 비즈니스 수명 주기의 사실입니다. 회사 법률 동작, 직면 하는 경우 모든 관련 된 법적 상황에서 승소 자료는 court을 상대 자문에 게 제공 하려면 법적 개시 하는 프로세스를 통해 필요한 있습니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p101">All companies face the potential of lawsuits or other types of legal action. While legal departments work to reduce that exposure, litigation is a fact of business life. When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="271b9-p102">eDiscovery은 기준이 회사 인벤토리에 포함, 검색, 식별, 보존, 필터링, 하 고 전자 양식으로 존재 하는 관련 된 법적 상황에서 승소 자료 수 있게 하는 프로세스입니다. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online 및 Exchange Online에 많은 양의 법적 상황에서 승소 콘텐츠를 보관할 수 있습니다. 버전에 따라 이러한 제품 eDiscovery를 지원할 수 있습니다 날짜와 전체에서 (Exchange Server를 통해 Lync) 포함 하 고, 보다 쉽게 인덱싱하려 법적 팀에 대 한 식별, 기다리는 주어진된 사례에 대 한 가장 관련성이 높은 콘텐츠를 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p102">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content. Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="271b9-p103">많은 수의 문서는 사용자의 (Custodians)에 저장 된 중앙 집중화 된 위치에 없는 로컬 컴퓨터입니다. 기본적으로 검색 하도록 SharePoint 2013에 대 한 없게 하 고 검색 될 수 없는 경우 eDiscovery에 포함 될 수 없습니다. 이 솔루션에서는 로그온 스크립트를 식별 하 고 사용자 컴퓨터에서 법적 상황에서 승소 자료 (영문)의 컬렉션을 자동화 하기 위한 System Center 조정자 2012 R2 및 Exchange 서버에 대 한 Windows PowerShell을 사용 하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p103">Many documents are stored on users' (Custodians) local computers, not in a centralized location. This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery. This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="271b9-114">이 솔루션에서 수행 하는 작업</span><span class="sxs-lookup"><span data-stu-id="271b9-114">What this solution does</span></span>

<span data-ttu-id="271b9-p104">이 솔루션을 사용 하 여 글로벌 보안 그룹, 그룹 정책 및 Windows PowerShell 스크립트를 찾고, 조사 하 고, 하 고, 숨겨진된 파일 공유에 사용자가 로컬 컴퓨터에서 콘텐츠 및 Outlook 개인 저장소 (PST) 파일을 수집 합니다. 여기에서 PST 파일을 Exchange Server 2013 또는 Exchange Online으로 가져올 수 있습니다. 모든 파일을 사용 하 여 다른 파일 공유에 실행 되는 System Center 조정자 2012 r 2 서 Microsoft Azure 장기 저장 및 SharePoint 2013 indexing 이동 후 됩니다. 다음에서는 eDiscovery 센터의 온-프레미스 SharePoint 2013 배포에서 또는 SharePoint Online에서 정기적으로 eDiscovery를 수행 하는 것 처럼 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p104">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share. From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online. All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013. You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="271b9-p105">이 솔루션 robocopy를 사용 하 여 중앙된 파일 공유에 더불어의 컴퓨터에서 파일을 복사 합니다. Robocopy에서는 해당 하는 파일 열기 또는 잠긴 것으로 모든 파일을 복사 하지 않으므로 더불어 열기 되어있는지 PST 파일을 비롯 한 수집 되지 않습니다. 해당 작업을 수동으로 수집 해야 합니다. 이 솔루션에서는 명시적으로 복사할 수 없는 파일을 식별 하는 목록 및 각 파일의 전체 경로와 제공지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p105">This solution uses robocopy to copy files from custodian's computers to a centralized file share. Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected. You will have to collect them manually. This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="271b9-123">다음 다이어그램에서는 모든 단계 및 솔루션의 요소 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-123">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![자동화된 파일 컬렉션 솔루션 개요](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="271b9-125">범례 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="271b9-125">****Legend****</span></span>||
|:-----|:-----|
|![자홍색 설명선 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="271b9-127">그룹 정책 개체 (GPO)를 만들고 컬렉션 로그온 스크립트와 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-127">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![자홍색 설명선 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="271b9-129">Custodians 그룹에만 GPO를 적용할 GPO 보안 필터를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-129">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![자홍색 설명선 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="271b9-131">프로그램 관리자가 로그온 하 고 컬렉션 로그온 스크립트를 호출 하는 GPO가 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-131">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![자홍색 설명선 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="271b9-133">컬렉션 로그온 스크립트는 재고를 파일에 대 한 검색 하 고 해당 위치를 녹음/녹화 Custodians 컴퓨터에서 모든 로컬에 연결 된 드라이브에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-133">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![자홍색 설명선 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="271b9-135">컬렉션 로그온 스크립트는 준비 서버에서 숨겨진된 파일 공유에 인벤토리에 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-135">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![자홍색 설명선 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="271b9-137">(옵션 A) Exchange Server 2013에 수집 된 PST 파일을 가져오려면 PST 가져오기 스크립트를 수동으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-137">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![자홍색 설명선 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="271b9-139">(옵션 B) Office 365 가져오기 도구 및 프로세스를 사용, Exchange Online에 수집 된 PST 파일을 가져올.</span><span class="sxs-lookup"><span data-stu-id="271b9-139">(Option B) Using the Office 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![자홍색 설명선 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="271b9-141">MoveToColdStorage System Center 조정자 2012 R2 실행 서와 장기 저장소에 대 한 Azure 파일 공유에 수집 된 모든 파일을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-141">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![자홍색 설명선 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="271b9-143">SharePoint 2013과 함께 콜드 저장소 파일 공유에서 파일을 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-143">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![자홍색 설명선 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="271b9-145">콘텐츠 콜드 저장소 및 온-프레미스 Exchange Server 2013에서 eDiscovery를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-145">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![자홍색 설명선 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="271b9-147">Office 365의 내용에 대해 eDiscovery를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-147">Perform eDiscovery on content in Office 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="271b9-148">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="271b9-148">Prerequisites</span></span>

<span data-ttu-id="271b9-p106">이 솔루션의 구성 하는의 가능성이 전체에서 및 구성 되어 있다고 eDiscovery에 대 한 생각 하는 경우 많은 요소를 가장 필요 합니다. 빌드 필요 없을 수도 있습니다 또는 특정 구성을 필요로 하는 것과 하겠습니다 제공 링크는 요소에 대 한 기본 구성을 수행 합니다. 솔루션 자체를 구성 하기 전에 현재 위치에서의 기본 구성은 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p106">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery. For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration. You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="271b9-152">기본 구성</span><span class="sxs-lookup"><span data-stu-id="271b9-152">Base configuration</span></span>

|<span data-ttu-id="271b9-153">**요소**</span><span class="sxs-lookup"><span data-stu-id="271b9-153">**Element**</span></span>|<span data-ttu-id="271b9-154">**링크**</span><span class="sxs-lookup"><span data-stu-id="271b9-154">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="271b9-155">Active Directory 도메인 서비스 (AD DS) 도메인</span><span class="sxs-lookup"><span data-stu-id="271b9-155">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="271b9-156">온-프레미스 네트워크에서 인터넷에 연결</span><span class="sxs-lookup"><span data-stu-id="271b9-156">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="271b9-157">SharePoint 2013 및 System Center 조정자 2012 r 2를 지원 하기 위해 SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="271b9-157">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="271b9-158">System Center 조정자-2012 배포</span><span class="sxs-lookup"><span data-stu-id="271b9-158">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="271b9-159">온-프레미스 또는 Azure eDiscovery (A 옵션에 대 한 필수)에 대 한 SharePoint 2013 기반</span><span class="sxs-lookup"><span data-stu-id="271b9-159">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="271b9-160">준비 단계에 대 한 온-프레미스 파일 공유 서버</span><span class="sxs-lookup"><span data-stu-id="271b9-160">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="271b9-161">온-프레미스 Exchange Server 2013 옵션 A PST 가져오기에 대 한</span><span class="sxs-lookup"><span data-stu-id="271b9-161">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="271b9-162">C u 5 (15.913.22) [c u 5](https://go.microsoft.com/fwlink/p/?LinkId=613426)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-162">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="271b9-163">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="271b9-163">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="271b9-164">System Center 조정자-2012 배포</span><span class="sxs-lookup"><span data-stu-id="271b9-164">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="271b9-165">Office 365 (계획 E3) Exchange Online 및 SharePoint Online (옵션 B에 필요)</span><span class="sxs-lookup"><span data-stu-id="271b9-165">Office 365 (E3 Plan) with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="271b9-166">Office 365 E3 구독에 대 한 등록 하려면 [Office 365 E3 구독](https://go.microsoft.com/fwlink/p/?LinkId=613504)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="271b9-166">To sign up for an Office 365 E3 subscription, see [Office 365 E3 subscription](https://go.microsoft.com/fwlink/p/?LinkId=613504).</span></span>  <br/> |
|<span data-ttu-id="271b9-167">가상 컴퓨터를 사용 하 여 azure 구독</span><span class="sxs-lookup"><span data-stu-id="271b9-167">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="271b9-168">Azure를 등록 하려면 [Windows Azure에 가입](https://go.microsoft.com/fwlink/p/?LinkId=512010) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="271b9-168">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="271b9-169">온-프레미스 네트워크 및 Azure 구독 간에 VPN 연결</span><span class="sxs-lookup"><span data-stu-id="271b9-169">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="271b9-170">Azure 구독 및 온-프레미스 네트워크 간에 VPN 터널을 설정 하려면 [Microsoft Azure 가상 네트워크에 연결 하는 온-프레미스 네트워크 연결](https://go.microsoft.com/fwlink/p/?LinkId=613507)을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-170">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="271b9-171">SharePoint 및 Exchange Server 2013와 선택적으로 Lync Server 2013에서 검색을 구성 하는 SharePoint 2013 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="271b9-171">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="271b9-172">이 방식 eDiscovery를 구성 하려면 [Configure eDiscovery in SharePoint Server 2013을](https://go.microsoft.com/fwlink/p/?LinkId=613508) 참조 하 고[테스트 랩 가이드: eDiscovery Exchange, Lync, SharePoint 및 Windows 파일 공유 테스트 랩에 대 한 구성](https://go.microsoft.com/fwlink/p/?LinkId=393130)합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-172">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="271b9-173">SharePoint Online 및 Exchange Online에 대 한 Office 365의 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="271b9-173">eDiscovery in Office 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="271b9-174">Office 365에서 eDiscovery를 구성 하려면 [SharePoint Online에서 eDiscovery 센터 설정](https://go.microsoft.com/fwlink/p/?LinkId=613628)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="271b9-174">To configure eDiscovery in Office 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="271b9-175">환경 구성</span><span class="sxs-lookup"><span data-stu-id="271b9-175">Configure the environment</span></span>

<span data-ttu-id="271b9-176">현재 위치에서의 기본 구성은 추가한 다음에 솔루션 자체를 구성 하려면 차지 코드로 미리 차 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-176">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="271b9-177">준비 파일 공유</span><span class="sxs-lookup"><span data-stu-id="271b9-177">Staging file share</span></span>

1. <span data-ttu-id="271b9-178">온-프레미스 도메인에서 Custodians 라는 글로벌 보안 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-178">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="271b9-p107">Custodians 컴퓨터에서 수집 되는 파일에 대 한 숨겨진된 파일 공유를 만듭니다. 온-프레미스 서버에 표시 되어야 합니다. 예, 준비를 호출 하는 서버에서의 경우 $ 라는 파일 공유를 만듭니다. **$** 이 숨겨진된 공유를 확인 하려면가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p107">Create a hidden file share for the files that are collected from Custodians computers. This should be on an on-premises server. For example, on a server called Staging, create a file share called Cases$. The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="271b9-183">다음과 같은 공유 사용 권한을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-183">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="271b9-184">Custodians: 변경, 읽기</span><span class="sxs-lookup"><span data-stu-id="271b9-184">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="271b9-185">관리자: 모든 권한</span><span class="sxs-lookup"><span data-stu-id="271b9-185">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="271b9-186">Exchange 신뢰할 수 있는 하위: 변경, 읽기</span><span class="sxs-lookup"><span data-stu-id="271b9-186">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="271b9-p108">**보안** 탭을 열고 Custodians 그룹 추가 **고급**을 클릭 합니다. Custodians 그룹에 대 한 다음 사용 권한을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p108">Open the **Security** tab, add the Custodians group, and click **Advanced**. Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="271b9-189">**종류: 거부**</span><span class="sxs-lookup"><span data-stu-id="271b9-189">**Type: Deny**</span></span>
    
  - <span data-ttu-id="271b9-190">**적용 대상:이 폴더, 하위 폴더 및 파일**</span><span class="sxs-lookup"><span data-stu-id="271b9-190">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="271b9-191">**고급 사용 권한** 을 클릭 하 고 다음을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-191">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="271b9-192">**읽기 특성**</span><span class="sxs-lookup"><span data-stu-id="271b9-192">**Read attributes**</span></span>
    
  - <span data-ttu-id="271b9-193">**확장된 특성 읽기**</span><span class="sxs-lookup"><span data-stu-id="271b9-193">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="271b9-194">**사용 권한 읽기**</span><span class="sxs-lookup"><span data-stu-id="271b9-194">**Read permissions**</span></span>
    
6. <span data-ttu-id="271b9-195">다음을 수행 하 여의 경우 $ 파일 공유에 액세스를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-195">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="271b9-196">Custodians 그룹에 사용자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-196">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="271b9-197">프로그램 파일의 경우 $ 폴더에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-197">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="271b9-p109">사용자로 준비 서버를 찾은 다음를 이동 예는 \\ \\에 어떤 공유를 사용할 수 있는 참조에 대 한 공유를 준비 합니다. 나열 된 **경우 $** 공유를 참조 하면 안됩니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p109">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available. You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="271b9-p110">탐색기로의 경우 $ 공유의 전체 경로 수동으로 입력 합니다. 이 경우 $ 공유를 열려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p110">Manually type the full path to the Cases$ share into Explorer. This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="271b9-p111">이전에 공유에 배치 파일을 열려고 시도 합니다. 이 작업은 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p111">Try to open the file you previously placed in the share. This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="271b9-204">로그온 스크립트</span><span class="sxs-lookup"><span data-stu-id="271b9-204">Logon script</span></span>

1. <span data-ttu-id="271b9-205">복사 하 여이 Windows PowerShell 스크립트를 메모장에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-205">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
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

2. <span data-ttu-id="271b9-206">위의 스크립트를 쉽게 c: 등을 찾을 수 있는 위치에 CollectionScript.ps1로 저장\\AFCScripts 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-206">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="271b9-p112">메모장에서 이동 기능을 사용 합니다. 필요에 따라 다음 변경 내용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p112">Use the Go To feature in Notepad. Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="271b9-209">**줄 번호**</span><span class="sxs-lookup"><span data-stu-id="271b9-209">**Line #**</span></span>|<span data-ttu-id="271b9-210">**필요한 변경 하려면**</span><span class="sxs-lookup"><span data-stu-id="271b9-210">**What you need to change**</span></span>|<span data-ttu-id="271b9-211">**필수/선택**</span><span class="sxs-lookup"><span data-stu-id="271b9-211">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="271b9-212">71</span><span class="sxs-lookup"><span data-stu-id="271b9-212">71</span></span>  <br/> |<span data-ttu-id="271b9-p113">**$FileTypes** 변수입니다. 스크립트를 조사 하 고 배열 변수에서를 수집 하려는 모든 파일 형식 확장명을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p113">**$FileTypes** variable. Include all the file type extensions that you want the script to inventory and collect in the array variable. </span></span><br/> |<span data-ttu-id="271b9-215">옵션</span><span class="sxs-lookup"><span data-stu-id="271b9-215">Optional</span></span>  <br/> |
|<span data-ttu-id="271b9-216">76 및 77</span><span class="sxs-lookup"><span data-stu-id="271b9-216">76 and 77</span></span>  <br/> |<span data-ttu-id="271b9-p114">요구에 맞게 변경 **$CaseNo** 변수 방식으로 작성 됩니다. 스크립트는 현재 날짜와 시간 캡처하고 사용자 이름을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p114">Change the way the **$CaseNo** variable is built to suit your needs. The script captures the current date and time and appends the user name to it. </span></span><br/> |<span data-ttu-id="271b9-219">옵션</span><span class="sxs-lookup"><span data-stu-id="271b9-219">Optional</span></span>  <br/> |
|<span data-ttu-id="271b9-220">80</span><span class="sxs-lookup"><span data-stu-id="271b9-220">80</span></span>  <br/> |<span data-ttu-id="271b9-221">**$CaseRootLocation** 변수를 설정 해야 준비 서버 컬렉션 파일 공유 ** \\ \\준비\\$의 경우**합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-221">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="271b9-222">필수</span><span class="sxs-lookup"><span data-stu-id="271b9-222">Required</span></span>  <br/> |
   
4. <span data-ttu-id="271b9-223">도메인 컨트롤러의 Netlogon 파일 공유에 CollectionScript.ps1 파일을 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-223">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="271b9-224">로그온 스크립트 및 Custodians 그룹에 대 한 GPO를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-224">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="271b9-225">항목을 [사용 하 여 시작, 종료, 로그온 및 그룹 정책에서 로그 오프 스크립트에서](https://go.microsoft.com/fwlink/p/?LinkId=614844)"사용자 로그온 스크립트를 할당 하는 방법" 섹션을 수행 하 여 Custodians 그룹에 대 한 로그온 스크립트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-225">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="271b9-226">**보안 필터링**에서 인증 된 사용자를 제거 하 고 Custodians 그룹을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-226">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="271b9-227">PST 가져오기 옵션 A, Exchange Server 2013에 대 한 스크립트</span><span class="sxs-lookup"><span data-stu-id="271b9-227">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="271b9-228">복사한 다음 Windows PowerShell 스크립트를 메모장에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-228">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
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
# This would be the format http://<exchange server FQDN>/Powershell

$ConnectionUri = 'http://h10-exch/PowerShell'
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

2. <span data-ttu-id="271b9-p115">쉽게 찾을 수 있는 위치에 PSTImportScript.ps1로 스크립트를 저장 합니다. 예제 및 손쉬운 사용에 대 한 호출 하 여 준비 서버에 폴더를 만들어 \\ \\준비\\AFCScripts에서 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p115">Save the script as PSTImportScript.ps1 in a location that's easy for you to find. For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="271b9-231">메모장에서 이동 기능을 사용 하 고 필요에 따라 다음 변경 내용을 확인 하십시오.</span><span class="sxs-lookup"><span data-stu-id="271b9-231">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="271b9-232">**줄 번호**</span><span class="sxs-lookup"><span data-stu-id="271b9-232">**Line #**</span></span>|<span data-ttu-id="271b9-233">**필요한 변경 하려면**</span><span class="sxs-lookup"><span data-stu-id="271b9-233">**What you need to change**</span></span>|<span data-ttu-id="271b9-234">**필수/선택**</span><span class="sxs-lookup"><span data-stu-id="271b9-234">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="271b9-235">12 </span><span class="sxs-lookup"><span data-stu-id="271b9-235">12</span></span>  <br/> |<span data-ttu-id="271b9-p116">**$FolderIdentifier** 태그 Pst로 가져오는 사서함 폴더를 지정 합니다. 필요한 경우이 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p116">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into. Change this if necessary. </span></span><br/> |<span data-ttu-id="271b9-238">옵션</span><span class="sxs-lookup"><span data-stu-id="271b9-238">Optional</span></span>  <br/> |
|<span data-ttu-id="271b9-239">17 </span><span class="sxs-lookup"><span data-stu-id="271b9-239">17</span></span>  <br/> |<span data-ttu-id="271b9-240">**$ConnectionUri** 를 자체 서버를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-240">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="271b9-p117">> [!IMPORTANT]> 다음을 확인 하면 **$ConnectionUri** 하지 https http 위치를 가리킵니다. Https로 작동 하지 않음:.</span><span class="sxs-lookup"><span data-stu-id="271b9-p117">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https. It won't work with https:.</span></span>          |<span data-ttu-id="271b9-243">필수</span><span class="sxs-lookup"><span data-stu-id="271b9-243">Required</span></span>  <br/> |
   
4. <span data-ttu-id="271b9-244">권한이 있는지 확인 Exchange 신뢰할 수 있는 하위 시스템 계정 읽기, 쓰기 및 실행 하는 \\ \\준비\\의 경우 $ 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-244">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="271b9-245">PST 가져오기 스크립트에는 다음 두 입력된 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-245">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="271b9-246">**$SourcePath** 같이 가져올 수 있도록 PST 파일의 위치 \\ \\준비\\$의 경우.</span><span class="sxs-lookup"><span data-stu-id="271b9-246">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="271b9-247">**$MailboxAlias** 가져온된 전자 메일 항목을 받을 수 있는 대상 사서함의 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-247">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="271b9-248">예: 경로에서 모든 PST 파일을 가져오려는 경우 \\Staging\Cases$ 별칭 eDiscoveryMailbox 인 사서함으로, 다음과 같은 스크립트를 실행할 것 `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-248">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="271b9-249">Exchange Online에 대 한 B, PST 가져오기 옵션</span><span class="sxs-lookup"><span data-stu-id="271b9-249">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="271b9-p118">사서함 구조에 가져온된 PST 파일을 배치를 만듭니다. Exchange Online의 사용자 사서함을 만드는 방법에 대 한 자세한 내용은[Exchange Online에서 사용자 사서함 만들기](https://go.microsoft.com/fwlink/p/?LinkId=615118)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="271b9-p118">Create the mailbox structure to place the imported PST files into. For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="271b9-252">콜드 저장소</span><span class="sxs-lookup"><span data-stu-id="271b9-252">Cold storage</span></span>

1. <span data-ttu-id="271b9-253">파일 공유에는 Azure 가상 컴퓨터 만들기, 수집된 된 모든 파일을 넣을, 예 \\ \\AZFile1\\ContentColdStorage 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-253">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="271b9-p119">기본 콘텐츠 액세스 계정에 최소한 부여 공유 및 모든 하위 폴더 및 파일에 읽기 권한을 합니다. SharePoint 2013의 검색을 구성 하는 방법에 대 한 자세한 내용은 참조 [Create SharePoint Server 2013에서 검색 서비스 응용 프로그램을 구성 하 고](https://go.microsoft.com/fwlink/p/?LinkId=614940)합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p119">Grant the default content access account at least Read permissions to the share and all subfolders and files. For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="271b9-256">PST 파일을 가져오는 것으로 예상 되는 경우 \\ \\AZFile1\\ContentColdStorage, 쓰기 및 실행 권한을 공유에 Exchange 신뢰할 수 있는 하위 시스템 읽기 권한을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-256">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="271b9-257">조정자</span><span class="sxs-lookup"><span data-stu-id="271b9-257">Orchestrator</span></span>

1. <span data-ttu-id="271b9-258">Microsoft 다운로드 센터에서[ MoveToColdStorage 실행 서](https://go.microsoft.com/fwlink/?LinkId=616095) 를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-258">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="271b9-p120">Open 되는 **실행 서 디자이너**의 **연결** 창에서로 실행 서 가져올 폴더를 클릭 합니다. **가져오기**를 클릭 하 고 **작업** 메뉴를 클릭 합니다. **가져오기** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p120">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into. Click the **Actions** menu, and the click **Import**. The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="271b9-262">**파일 위치** 상자에서 가져올, 실행 서의 경로 파일 이름을 입력 하거나 가져올 파일을 찾습니다 ( **...**) 줄임표 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-262">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="271b9-p121">**가져오기 실행 서** 및 **암호화 된 데이터를 가져오기 조정자를**선택 합니다. **카운터**, **일정**, **변수**, **컴퓨터 그룹**, **전역 구성 가져오기**및 **덮어쓰기 기존 전역 구성**의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p121">Select **Import runbooks** and **Import Orchestrator encrypted data**. Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="271b9-265">**마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-265">Click **Finish**.</span></span>
    
6. <span data-ttu-id="271b9-266">**MoveFilesToColdStorage** 실행 서를 다음과 같이 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-266">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="271b9-p122">**파일 이동** 작업- **원본 파일** 경로를 설정 컬렉션 파일 공유를 사용 하는 예 \\ \\준비\\$의 경우. 콜드 저장소 파일을 **대상 폴더** 를 공유, Azure의 예는 집합 \\ \\AZFile1\\ContentColdStorage 합니다. **고유한 이름으로 파일 만들기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p122">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$. Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage. Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="271b9-270">**폴더 삭제** 활동-설정의 **경로:** 컬렉션에 파일 공유, 예 \\ \\준비\\$의 경우\\*, 하 고 **모든 파일 및 하위 폴더를 삭제**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-270">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="271b9-271">[실행 서 배포](https://go.microsoft.com/fwlink/p/?LinkId=615120)의 절차를 사용 하 여 **MoveToColdStorage** 실행 서를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-271">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="271b9-272">SharePoint 온-프레미스 콜드 저장소에 대 한 검색</span><span class="sxs-lookup"><span data-stu-id="271b9-272">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="271b9-p123">예 Azure에서 콜드 저장소 공유에 대 한 SharePoint 2013 팜에서 새 콘텐츠 원본을 만들고 \\ \\AZFile1\\ContentColdStorage 합니다. 콘텐츠 원본 관리 하는 방법에 대 한 자세한 내용은 [추가, 편집 또는 SharePoint Server 2013에서 콘텐츠 원본을 삭제](https://go.microsoft.com/fwlink/p/?LinkId=615004) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="271b9-p123">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage. For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="271b9-p124">전체 크롤링을 시작 합니다. 자세한 내용은 참조, [시작, 일시 중지, 다시 시작 또는 SharePoint Server 2013에서 크롤링 중지](https://go.microsoft.com/fwlink/p/?LinkId=615005)합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p124">Start a full crawl. For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="271b9-277">솔루션을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="271b9-277">Using the solution</span></span>

<span data-ttu-id="271b9-p125">Exchange Server 2013 및 Exchange Online 모두로 PST 파일을 가져오려면 않으려면 가정 하 고,이 솔루션을 사용 하 여 다섯 가지 주요 단계로 있습니다. 이 섹션에서는 모두에 대 한 절차와 함께 제공 합니다. 다음을 수행 하는 솔루션 기본 상호 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p125">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online. This section provides you with the procedures for all of them. Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="271b9-281">Custodians 그룹의 사용자 멤버 자격을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-281">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="271b9-p126">로그온 스크립트에 의해 생성 된 로그 파일을 검토 합니다. FileCopyErrors.log 성공적으로 복사 되지 않은 모든 파일을 나열 합니다. 작업을 결정할 필요가</span><span class="sxs-lookup"><span data-stu-id="271b9-p126">Review the log files generated by the logon script. The FileCopyErrors.log lists all the files that were not successfully copied. You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="271b9-285">PST 가져오기 프로세스를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-285">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="271b9-286">콜드 저장소 모음 파일을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-286">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="271b9-p127">다른 모든 단계를이 솔루션에 특정 없습니다. SharePoint 2013 및 Office 365와 Azure에서 수행 하는 표준 관리 작업 됩니다. 이 솔루션 작동 회사의 요구에 따라 다음과 같이 해야하는 모든 지침을 제공 하지 않는 항목 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p127">All the other steps are not specific to this solution. They are standard administrative tasks that you perform in SharePoint 2013, and Office 365 and Azure. There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="271b9-290">사용자의 eDiscovery 사례 및 Custodians는 대/소문자와 연결 된 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-290">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="271b9-291">파일 컬렉션의 어떤 집합은 어떤 eDiscovery 사례와 연결을 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-291">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="271b9-292">가져오기 및 콜드 저장소 단계로 이동의 타이밍을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-292">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="271b9-293">Azure에서 사용 되는 파일 공간을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-293">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="271b9-294">Pst로 가져오는 사서함을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-294">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="271b9-295">백업 및 모든 온-프레미스 데이터를 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-295">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="271b9-296">더불어 관리</span><span class="sxs-lookup"><span data-stu-id="271b9-296">Custodian management</span></span>

- <span data-ttu-id="271b9-p128">개별 사용자에 대 한 자동화 된 파일 수집 프로세스를 시작 하려면 Custodians 그룹에 추가 합니다. 다음에 사용자가 로그온 하는 그룹 정책을 통해 Custodians 그룹에 할당 된 로그온 스크립트는 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p128">To start the automated file collection process for an individual user, add them to the Custodians group. The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="271b9-299">수집 된 파일을 모니터링 하 고 로그 파일 검토</span><span class="sxs-lookup"><span data-stu-id="271b9-299">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="271b9-p129">컬렉션 파일 공유, 예를 시청 \\ \\준비\\$의 경우\\*, 사용자 로부터 컬렉션 폴더에 대 한 합니다. 다음과 같은 서식이 지정 될 폴더의 이름: *yyyyMMddHHmm_UserName* 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p129">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user. The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="271b9-p130">컬렉션 완료 되 면 컬렉션 폴더를 열고 _Log 폴더로 이동 합니다. _Log 폴더에는 다음이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p130">When the collection is completed, open the collection folder, and browse to the _Log folder. In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="271b9-p131">사용자의 컴퓨터에서 같은 **A.xml**, **C.xml**모든 로컬 드라이브에 대 한 XML 파일입니다. 이 파일에는 after, 명명 된 robocopy 작업에 사용 되는 하는 인벤토리 드라이브에 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p131">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**. These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="271b9-p132">만 수집 스크립트 스크립트 자체에 정의 된 파일 형식에 대 한 인벤토리 파일에서 항목을 생성 합니다. 사용자의 컴퓨터에 있는 모든 파일에 대 한 인벤토리 항목을 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p132">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself. It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="271b9-p133">하나의 로그 파일을 실행 하는 각 컬렉션에 대 한 FileCopyErrors.log를 지정 합니다. 이 파일에 포함 파일 목록을 해당 robocopy 수 파일 컬렉션에 복사본이 아닌 공유, 등 \\ \\준비\\$의 경우\\*. 이 검토 하 고 이러한 누락 된 파일에 대해 수행할 동작을 결정 해야 합니다. 일반적으로 하나 수집 해야하는 수동으로 하려는 경우, 또는 필요 하지 않은 자신이 및 컬렉션에서 생략할 수 있습니다를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p133">One log file named FileCopyErrors.log for each collection run. This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*. You will need to review this and decide what actions to take for these missed files. Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="271b9-312">Exchange Server 2013에 대 한 PST 가져오기 옵션 A</span><span class="sxs-lookup"><span data-stu-id="271b9-312">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="271b9-p134">로그온 서버를 호스트 하는 컬렉션 파일 공유 같은 **준비**하 고 Windows PowerShell을 엽니다. Windows PowerShell을 시작 하는 방법에 대 한 자세한 내용은[Windows 서버에서 Windows PowerShell 시작](https://go.microsoft.com/fwlink/p/?LinkId=615115)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="271b9-p134">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell. For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="271b9-p135">제한 없음 실행 정책을 설정 합니다. 형식은 `Set-ExecutionPolicy Unrestricted -Scope Process` 에 Windows PowerShell 하 고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p135">Set the Execution policy to Unrestricted . Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="271b9-p136">PSTImportScript.ps1 파일을 실행 하 고 **$SourcePath** 및 **$MailboxAlias** 매개 변수를 제공 합니다. Windows PowerShell 스크립트를 실행 하는 방법에 대 한 자세한 내용은[스크립트 실행](https://go.microsoft.com/fwlink/p/?LinkID=615117)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="271b9-p136">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters. For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="271b9-319">오류에 대 한 출력을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-319">Review the output for errors.</span></span>
    
5. <span data-ttu-id="271b9-p137">동일한 사서함으로 동일 하 게 명명 된 PST 파일을 가져오려면 시도 하기 전에 사서함 가져오기 요청을 제거 해야 합니다. 이렇게 하려면 다음 명령을 실행: `Get-MailboxImportRequest | Remove-MailboxImportRequest`합니다. 큐에서 각 개별 요청을 제거 하 라는 메시지가 표시 됩니다. 필요에 따라 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p137">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request. Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. You will be prompted to remove each individual request from the queue. Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="271b9-324">Exchange Online에 대 한 PST 가져오기 옵션 B</span><span class="sxs-lookup"><span data-stu-id="271b9-324">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="271b9-325">Exchange Online에 수집 된 PST 파일을 시키려면 [Office 365 가져오기 서비스](https://go.microsoft.com/fwlink/p/?LinkId=614938)의 네트워크 업로드 섹션을 통해 Office 365에 가져오기 파일의 절차를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="271b9-325">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Office 365 through the network upload section of [Office 365 Import Service](https://go.microsoft.com/fwlink/p/?LinkId=614938).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="271b9-326">콜드 저장소로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-326">Move to cold storage</span></span>

1. <span data-ttu-id="271b9-327">절차를 사용 하 여[실행 중인 실행 서](https://go.microsoft.com/fwlink/p/?LinkId=615123)에 **MoveToColdStorage** 실행 서를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-327">Run the **MoveToColdStorage** runbook using the procedures in[Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="271b9-p138">조사식 같이 긴 용어 저장소에 대 한 사용 하는 Azure 파일 공유 \\ \\AZFile1\\ContentColdStorage 및 온-프레미스 컬렉션 파일 공유, \\ \\준비\\$의 경우. 확인할 수 있는 파일 및 폴더 콜드 저장소 파일 공유에 표시 되 고 컬렉션 파일 공유에서 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="271b9-p138">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$. You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="271b9-330">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="271b9-330">eDiscovery</span></span>

1. <span data-ttu-id="271b9-p139">일정으로 실행 하는 콜드 저장소 파일 공유의 전체 크롤링을 허용 하거나 크롤링을 시작 합니다. 전체 또는 증분 크롤링을 시작에 대 한 자세한 내용은 [시작, 일시 중지, 다시 시작 또는 SharePoint Server 2013에서 크롤링 중지](https://go.microsoft.com/fwlink/p/?LinkId=615005)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="271b9-p139">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl. For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="271b9-333">PST 파일 가져오기에 대 한 A 옵션을 사용 하는 경우 SharePoint 2013에서 eDiscovery 사례 만들기 또는 B. 옵션을 사용 하는 경우 SharePoint Online에서 eDiscovery 사례를 만들려면</span><span class="sxs-lookup"><span data-stu-id="271b9-333">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

