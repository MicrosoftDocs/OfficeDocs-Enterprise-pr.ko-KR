---
title: 테스트 랩 가이드 통합 된 Exchange, Lync 및 SharePoint 테스트 랩 구성
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
description: '요약: Exchange Server 2013, Lync Server 2013를 실행 하는 서버 및 SharePoint Server 2013를 실행 하는 서버를 실행 하는 서버가 포함 된 통합 테스트 랩을 만드는 방법을 알아봅니다.'
ms.openlocfilehash: 58c7d5ad701471e87c5e6600af2f9a36ac374448
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070404"
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="ddd42-103">테스트 랩 가이드: 통합 된 Exchange, Lync 및 SharePoint 테스트 랩 구성</span><span class="sxs-lookup"><span data-stu-id="ddd42-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="ddd42-104">**요약:** Exchange Server 2013, Lync Server 2013 실행 서버 및 SharePoint Server 2013을 실행 하는 서버를 실행 하는 서버가 포함 된 통합 테스트 랩을 만드는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="ddd42-104">**Summary:** Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
 
<span data-ttu-id="ddd42-105">**통합 된 Exchange, Lync 및 SharePoint 테스트 랩 가이드 개요 비디오 시청**</span><span class="sxs-lookup"><span data-stu-id="ddd42-105">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=8d1f00cc-b8b1-4394-9367-0cc9765e380a&AutoPlayVideo=false]
 
<span data-ttu-id="ddd42-106">이 구성에서 생성 되는 테스트 랩 (세 가지 서버 유형 사이에 서버 간 인증을 포함)을 사용 하 여 Exchange Server 2013를 실행 하는 서버를 사용 하는 여러 제품 시나리오 및 솔루션을 구축 하 고 보여주는 데 사용할 수 있습니다. Lync Server 2013를 실행 하는 서버와 SharePoint Server 2013를 실행 하는 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="ddd42-106">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="ddd42-107">이 문서에는 다음에 대 한 지침이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddd42-107">This document contains instructions for:</span></span>
  
1. <span data-ttu-id="ddd42-108">Windows Server 2012 기본 구성 테스트 랩 구성</span><span class="sxs-lookup"><span data-stu-id="ddd42-108">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="ddd42-109">새 서버(SQL1)를 설치 및 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd42-109">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="ddd42-110">SQL1 서버에 SQL Server 2012을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd42-110">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="ddd42-111">CLIENT2 이라는 새 클라이언트 컴퓨터를 설치 및 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd42-111">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="ddd42-112">E X 1에서 Exchange Server 2013 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="ddd42-112">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="ddd42-113">LYNC1 라는 새 서버를 설치 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd42-113">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="ddd42-114">LYNC1에 Lync Server 2013 Standard Edition을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd42-114">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="ddd42-115">SP1에 SharePoint Server 2013을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd42-115">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="ddd42-116">E X 1, LYNC1 및 SP1 간의 통합을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddd42-116">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="ddd42-117">Hyper-v에서이 테스트 랩을 구성 하는 방법에 대 한 자세한 내용은 [Windows Server 2012 hyper-v를 사용 하 여 통합 된 Exchange, Lync 및 SharePoint 테스트 랩 호스팅을](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ddd42-117">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="ddd42-118">테스트 랩 가이드 다운로드</span><span class="sxs-lookup"><span data-stu-id="ddd42-118">Download the test lab guide</span></span>

<span data-ttu-id="ddd42-119">[테스트 랩 가이드: 통합 된 Exchange, Lync 및 SharePoint 테스트 랩 구성](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="ddd42-119">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ddd42-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ddd42-120">See Also</span></span>

[<span data-ttu-id="ddd42-121">테스트 랩 가이드</span><span class="sxs-lookup"><span data-stu-id="ddd42-121">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




