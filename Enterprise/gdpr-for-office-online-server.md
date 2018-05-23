---
title: Office Online Server 및 Office Web Apps Server GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 온-프레미스 Exchange Server에서 GDPR 요구 사항을 해결하는 방법을 알아보세요.
ms.openlocfilehash: 9ae7220573a4592314eb4ef4bd58e4ec09a94d77
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-office-web-apps-server-and-office-online-server"></a><span data-ttu-id="ed8be-103">Office Web Apps Server 및 Office Online Server GDPR</span><span class="sxs-lookup"><span data-stu-id="ed8be-103">GDPR for Office Web Apps Server and Office Online Server</span></span>

<span data-ttu-id="ed8be-p101">Office Online Server 및 Office Web Apps Server 원격 분석 데이터는 ULS 로그의 형식으로 저장됩니다. [ULS 뷰어](https://www.microsoft.com/en-us/download/details.aspx?id=44020)를 사용하여 온-프레미스 테넌트에서 ULS 로그를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-p101">Office Online Server and Office Web Apps Server telemetry data is stored in the form of ULS logs. You can use [ULS Viewer](https://www.microsoft.com/en-us/download/details.aspx?id=44020) to view ULS logs from your on-premises tenant.</span></span>

<span data-ttu-id="ed8be-p102">모든 로그 줄에는 CorrelationID가 있습니다. 관련된 로그 줄은 동일한 CorrelationID를 공유합니다. 각 CorrelationID는 단일 SessionID에 연결되고, 한 개의 SessionID는 많은 CorrelationID에 관련되어 있을 수 있습니다. 각 SessionID는 단일 UserID에 연결되어 있을 수 있지만 일부 세션은 익명으로 만들어져 연결된 UserID가 없을 수 있습니다. 그러므로 특정 사용자와 연결된 데이터를 확인하려면 단일 UserID에서 해당 사용자와 연결된 SessionID로 매핑하고, 이러한 SessionID에서 연결된 CorrelationID로 매핑하고, 이러한 CorrelationID에서 이러한 상관 관계에 있는 모든 로그로 매핑할 수 있습니다. 여러 ID 간의 관계는 아래 다이어그램을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ed8be-p102">Every log line contains a CorrelationID. Related log lines share the same CorrelationID. Each CorrelationID is tied to a single SessionID, and one SessionID may be related to many CorrelationIDs. Each SessionID may be related to a single UserID, although some sessions can be anonymous and therefore not have an associated UserID. In order to determine what data is associated with a particular user, it is therefore possible to map from a single UserID to the SessionIDs associated with that user, from those SessionIDs to the associated CorrelationIDs, and from those CorrelationIDs to all the logs in those correlations. See the below diagram for the relationship between the different IDs.</span></span>

![](media/gdpr-for-office-online-server_image1.jpg)

## <a name="gathering-logs"></a><span data-ttu-id="ed8be-112">로그 수집</span><span class="sxs-lookup"><span data-stu-id="ed8be-112">Gathering Logs</span></span>

<span data-ttu-id="ed8be-p103">예를 들어 UserID 1과 연결된 모든 로그를 수집하기 위한 첫 번째 단계로 UserID 1과 연결된 모든 세션(즉, SessionID 1 및 SessionID 2)을 수집합니다. 다음 단계로는 SessionID 1(즉, CorrelationID 1, 2, 3) 및 SessionID 2(즉, CorrelationID 4)와 연결된 모든 상관 관계를 수집합니다. 마지막으로 목록의 각 상관 관계와 연결된 모든 로그를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-p103">In order to gather all logs associated with UserID 1, for example, the first step would be to gather all sessions associated with UserID 1 (i.e. SessionID 1 and SessionID2). The next step would be to gather all correlations associated with SessionID 1 (i.e. CorrelationIDs 1, 2, and 3) and with SessionID 2 (i.e. CorrelationID 4). Finally, gather all logs associated with each of the correlations in the list.</span></span>

1.  <span data-ttu-id="ed8be-116">UlsViewer를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-116">Launch UlsViewer</span></span>

2.  <span data-ttu-id="ed8be-117">의도한 시간 프레임에 해당하는 uls 로그를 엽니다. ULS 로그는 %PROGRAMDATA%\\Microsoft\\OfficeWebApps\\데이터\\로그\\ULS에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-117">Open up the uls log corresponding to the intended timeframe; ULS logs are stored in %PROGRAMDATA%\\Microsoft\\OfficeWebApps\\Data\\Logs\\ULS</span></span>

3.  <span data-ttu-id="ed8be-118">편집 | 필터 수정을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-118">Edit | Modify Filter</span></span>

4.  <span data-ttu-id="ed8be-119">다음과 같은 필터를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-119">Apply a filter that is:</span></span>

    -   <span data-ttu-id="ed8be-120">EventID가 apr3y와 같음 또는</span><span class="sxs-lookup"><span data-stu-id="ed8be-120">EventID equals apr3y Or</span></span>

    -   <span data-ttu-id="ed8be-121">EventID가 bp2d6과 같음</span><span class="sxs-lookup"><span data-stu-id="ed8be-121">EventID equals bp2d6</span></span>

5.  <span data-ttu-id="ed8be-122">해시된 UserId는 이러한 두 이벤트 중 하나의 Message에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-122">Hashed UserIds will be in the Message of either one of these two events</span></span>

6.  <span data-ttu-id="ed8be-123">apr3y의 경우 Message에는 UserID 값과 PUID 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-123">For apr3y, the Message will contain a UserID value and a PUID value</span></span>

7.  <span data-ttu-id="ed8be-p104">bp2d6의 경우 Message에는 여러 정보가 포함됩니다. LoggableUserId 값 필드는 해시된 UserID입니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-p104">For bp2d6, the Message will contain quite a bit of information. The LoggableUserId Value field is the hashed UserID.</span></span>

8.  <span data-ttu-id="ed8be-126">해시된 UserId를 이러한 두 태그 중 하나에서 가져오면 ULSViewer에서 해당 행의 WacSessionId 값에는 해당 사용자와 연결된 WacSessionId가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-126">Once the hashed UserId is obtained from either of these two tags, the WacSessionId value of that row in ULSViewer will contain the WacSessionId associated with that user</span></span>

9.  <span data-ttu-id="ed8be-127">해당 사용자와 연결된 모든 WacSessionId 값을 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-127">Collect all of the WacSessionId values associated with the user in question</span></span>

10. <span data-ttu-id="ed8be-128">모든 EventId의 필터가 "xmnv"와 같습니다. Message는 목록에서 첫 번째 WacSessionId의 "UserSessionId=\<WacSessionId\>"와 같습니다(필터의 \<WacSessionId\>를 사용자의 WacSessionId로 바꿈).</span><span class="sxs-lookup"><span data-stu-id="ed8be-128">Filter for all EventId equals "xmnv", Message equals "UserSessionId=\<WacSessionId\>" for the first WacSessionId in the list (replacing the \<WacSessionId\> part of the filter with your WacSessionId)</span></span>

11. <span data-ttu-id="ed8be-129">해당 WacSessionId와 일치하는 모든 Correlation 값을 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-129">Collect all values of Correlation that match that WacSessionId</span></span>

12. <span data-ttu-id="ed8be-130">해당 사용자에 대해 목록에 있는 모든 WacSessionId 값에 10~11단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-130">Repeat steps 10-11 for all values of WacSessionId in your list for the user in question</span></span>

13. <span data-ttu-id="ed8be-131">모든 Correlation의 필터가 목록의 첫 번째 Correlation과 같게 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-131">Filter for all Correlation equals the first Correlation in your list</span></span>

14. <span data-ttu-id="ed8be-132">해당 Correlation과 일치하는 모든 로그를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-132">Collect all logs matching that Correlation</span></span>

15. <span data-ttu-id="ed8be-133">해당 사용자에 대해 목록에 있는 모든 Correlation 값에 13~14단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-133">Repeat steps 13-14 for all values of Correlation in your list for the user in question</span></span>

## <a name="types-of-data"></a><span data-ttu-id="ed8be-134">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="ed8be-134">Types of Data</span></span>

<span data-ttu-id="ed8be-p105">Office Online 로그는 다양한 형식의 데이터를 포함합니다. 다음은 ULS 로그에 포함될 수 있는 데이터의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="ed8be-p105">Office Online logs contain a variety of different types of data. The following are examples of the data that ULS logs may contain:</span></span>

-   <span data-ttu-id="ed8be-137">제품을 사용하는 동안 발생한 문제의 오류 코드</span><span class="sxs-lookup"><span data-stu-id="ed8be-137">Error codes for issues encountered during use of the product</span></span>

-   <span data-ttu-id="ed8be-138">단추 클릭 및 앱 사용에 대한 다른 데이터들</span><span class="sxs-lookup"><span data-stu-id="ed8be-138">Button clicks and other pieces of data about app usage</span></span>

-   <span data-ttu-id="ed8be-139">앱 및/또는 앱 내의 특정 기능에 대한 성능 데이터</span><span class="sxs-lookup"><span data-stu-id="ed8be-139">Performance data about the app and/or particular features within the app</span></span>

-   <span data-ttu-id="ed8be-140">사용자의 컴퓨터 위치에 대한 일반적인 위치 정보(예: IP 주소에서 파생된 국가/지역, 시/도), 하지만 정확한 지리적 위치는 배제</span><span class="sxs-lookup"><span data-stu-id="ed8be-140">General location information about where the user’s computer is (e.g. country / region, state, and city, derived from the IP address), but not precise geolocation</span></span>

-   <span data-ttu-id="ed8be-141">브라우저(예: 브라우저 이름 및 버전) 및 컴퓨터(예: 데이터 OS 유형 및 버전)에 대한 기본 메타데이터</span><span class="sxs-lookup"><span data-stu-id="ed8be-141">Basic metadata about the browser, e.g. browser name and version, and the computer, e.g. OS type and version</span></span>

-   <span data-ttu-id="ed8be-142">문서 호스트(예: OneDrive, SharePoint, Exchange)에서 보낸 오류 메시지</span><span class="sxs-lookup"><span data-stu-id="ed8be-142">Error messages from the document host (e.g. OneDrive, SharePoint, Exchange)</span></span>

-   <span data-ttu-id="ed8be-143">사용자가 수행한 작업과 관련 없는, 앱 내부 프로세스에 대한 정보</span><span class="sxs-lookup"><span data-stu-id="ed8be-143">Information about processes internal to the app, unrelated to any action the user has taken</span></span>
