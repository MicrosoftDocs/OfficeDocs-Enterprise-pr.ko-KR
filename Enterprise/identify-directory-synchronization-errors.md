---
title: Office 365에서 디렉터리 동기화 오류를 표시 합니다.
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Office 365 관리 센터에서 디렉터리 동기화 오류를 표시 하는 방법에 알아봅니다.
ms.openlocfilehash: 8beeeebbb24936abd7c93f4c04c0fa4e27c85c12
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327340"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="fe88c-103">Office 365에서 디렉터리 동기화 오류를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe88c-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="fe88c-p101">Office 365 관리 센터에서 디렉터리 동기화 오류를 볼 수 있습니다. 사용자 개체 오류만 표시 됩니다. PowerShell을 사용 하 여 오류를 표시 하려면 [DirSyncProvisioningErrors 사용 하 여 식별 개체](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fe88c-p101">You can view directory synchronization errors in the Office 365 admin center. Only the User object errors are displayed. To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="fe88c-107">보기, 후 식별 된 문제를 해결 하려면 [Office 365에 대 한 디렉터리 동기화를 통해 문제를 해결](fix-problems-with-directory-synchronization.md) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fe88c-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="fe88c-108">관리 센터에서 사용 되는 디렉터리 동기화 오류 보기</span><span class="sxs-lookup"><span data-stu-id="fe88c-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="fe88c-109">관리 센터에서 모든 오류를 보려면:</span><span class="sxs-lookup"><span data-stu-id="fe88c-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="fe88c-110">회사 또는 학교 계정으로 Office 365에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="fe88c-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="fe88c-111">[Office 365에 대 한 관리 센터](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe88c-111">Go to the [About the Office 365 admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="fe88c-112">**홈** 페이지에서 **디렉터리 동기화 상태** 타일을 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe88c-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![디렉터리 동기화 상태 관리 센터 미리 보기에서 바둑판식으로 배열](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="fe88c-114">타일을에서 **디렉터리 동기화 상태** 페이지로 이동 하려면 **디렉터리 동기화 상태** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe88c-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="fe88c-115">페이지 아래쪽에서 디렉터리 동기화 오류가 있는 경우를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe88c-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![디렉터리 동기화 상태 페이지에서 볼 수 있습니다 DirSync 개체 오류가 있는 경우](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="fe88c-117">디렉터리 동기화 오류가 자세한 보기로 이동 하려면 **DirSync 개체 오류를 발견 하는 것** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe88c-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="fe88c-118">**디렉터리 동기화 상태** 타일 **DirSync 개체 오류를 발견 하는 것** 을 선택 하는 경우 **디렉터리 동기화 오류** 페이지로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe88c-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![디렉터리 동기화 오류 페이지](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="fe88c-120">**디렉터리 동기화 오류** 페이지에서 세부 정보 창에 오류 및 수정 하는 방법에 대 한 팁에 대 한 정보를 표시 하려면 나열 된 오류 중 하나를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe88c-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
