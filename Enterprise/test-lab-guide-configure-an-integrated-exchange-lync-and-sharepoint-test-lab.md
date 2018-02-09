---
title: "통합 된 Exchange 랩 가이드 구성 테스트, Lync 및 SharePoint 테스트 랩"
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
description: "요약: Exchange Server 2013을 실행 하는 서버, Lync Server 2013을 실행 하는 서버 및 SharePoint Server 2013을 실행 하는 서버를 포함 하는 통합 된 테스트 랩을 만들고 하는 방법에 알아봅니다."
ms.openlocfilehash: 4bc9c48782c7693368c304f5f9d5bae56242111d
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="c94ff-103">테스트 랩 가이드: 통합된 Exchange, Lync 및 SharePoint 테스트 랩 구성</span><span class="sxs-lookup"><span data-stu-id="c94ff-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="c94ff-104">**요약:** Exchange Server 2013을 실행 하는 서버, Lync Server 2013을 실행 하는 서버 및 SharePoint Server 2013을 실행 하는 서버를 포함 하는 통합 된 테스트 랩을 만들고 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c94ff-104">**Summary:** Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="c94ff-105">확장 구성 하 고 다중 제품 시나리오 및 Exchange Server 2013을 실행 하는 서버를 사용 하는 솔루션을 시연 하는 세 유형의 서버 간에 서버-서버 인증을 포함 하는이 구성의 결과로 발생 하는 테스트 랩을 사용할 수는 Lync Server 2013을 실행 하는 서버와 SharePoint Server 2013을 실행 하는 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="c94ff-105">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="c94ff-106">이 문서에는 다음 작업을 위한 지침이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c94ff-106">This document contains instructions for the following:</span></span>
  
1. <span data-ttu-id="c94ff-107">Windows Server 2012 기본 구성 테스트 랩을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c94ff-107">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="c94ff-108">새 서버(SQL1)를 설치 및 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c94ff-108">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="c94ff-109">S q l 1 서버에 SQL Server 2012를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="c94ff-109">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="c94ff-110">명명 된 CLIENT2 설치 및 새 클라이언트 컴퓨터를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c94ff-110">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="c94ff-111">설치 및 e x 1에서 Exchange Server 2013을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c94ff-111">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="c94ff-112">새 서버 설치 및 구성에 LYNC1 라는 합니다.</span><span class="sxs-lookup"><span data-stu-id="c94ff-112">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="c94ff-113">LYNC1에 Lync Server 2013 Standard Edition을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c94ff-113">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="c94ff-114">S p 1에서 SharePoint Server 2013을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="c94ff-114">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="c94ff-115">E x 1, LYNC1, s p 1과의 통합을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c94ff-115">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="c94ff-116">**통합 된 Exchange, Lync 및 SharePoint 테스트 랩 가이드 개요 동영상 보기**</span><span class="sxs-lookup"><span data-stu-id="c94ff-116">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

![동영상(재생 단추) 아이콘](images/mod_icon_video_M.png)
  
<span data-ttu-id="c94ff-118">Hyper-v에서이 테스트 랩을 구성 하는 방법에 대 한 정보를 [호스팅 통합된 Exchange, Lync 및 SharePoint 테스트 랩와 Windows Server 2012 Hyper-v를](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c94ff-118">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="c94ff-119">테스트 랩 가이드 다운로드</span><span class="sxs-lookup"><span data-stu-id="c94ff-119">Download the test lab guide</span></span>

<span data-ttu-id="c94ff-120">[테스트 랩 가이드:는 통합 된 Exchange, Lync 및 SharePoint 테스트 랩 구성](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="c94ff-120">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c94ff-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c94ff-121">See Also</span></span>

[<span data-ttu-id="c94ff-122">테스트 랩 가이드</span><span class="sxs-lookup"><span data-stu-id="c94ff-122">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




