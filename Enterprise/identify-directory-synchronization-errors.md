---
title: Microsoft 365에서 디렉터리 동기화 오류 보기
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Microsoft 365 관리 센터에서 디렉터리 동기화 오류를 확인 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: d10abc29a08da4352d4c0779698e2062175008b4
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711648"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a><span data-ttu-id="fcb33-103">Microsoft 365에서 디렉터리 동기화 오류 보기</span><span class="sxs-lookup"><span data-stu-id="fcb33-103">View directory synchronization errors in Microsoft 365</span></span>

<span data-ttu-id="fcb33-104">[Microsoft 365 관리 센터](https://admin.microsoft.com)에서 디렉터리 동기화 오류를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcb33-104">You can view directory synchronization errors in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="fcb33-105">사용자 개체 오류만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcb33-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="fcb33-106">PowerShell을 사용 하 여 오류를 확인 하려면 [DirSyncProvisioningErrors를 사용 하 여 개체 확인](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fcb33-106">To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="fcb33-107">확인 후에는 [Microsoft 365에 대 한 디렉터리 동기화 문제 해결](fix-problems-with-directory-synchronization.md) 을 참조 하 여 식별 된 모든 문제를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcb33-107">After viewing, see [fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="fcb33-108">관리 센터에서 디렉터리 동기화 오류 보기</span><span class="sxs-lookup"><span data-stu-id="fcb33-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="fcb33-109">관리 센터에서 오류를 확인 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcb33-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="fcb33-110">회사 또는 학교 계정으로 Microsoft 365에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="fcb33-110">Sign in to Microsoft 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="fcb33-111">[관리 센터에 대 한](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcb33-111">Go to the [About the admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="fcb33-112">**홈** 페이지에 **DirSync 상태** 타일이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcb33-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![관리 센터 미리 보기의 DirSync 상태 타일](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="fcb33-114">타일에서 **DirSync 상태** 를 선택 하 여 **디렉터리 동기화 상태** 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcb33-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="fcb33-115">페이지 맨 아래에 DirSync 오류가 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcb33-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![디렉터리 동기화 상태 페이지에서 DirSync 개체 오류가 있는지 확인할 수 있습니다.](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="fcb33-117">디렉터리 동기화 오류에 대 한 자세한 보기로 이동 하려면 **DirSync 개체 오류를 찾음** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcb33-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="fcb33-118">또한 dirsync **상태** 타일에서 **dirsync 개체 오류가 발견** 되는 것을 선택한 경우 **dirsync 오류** 페이지로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcb33-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![DirSync 오류 페이지](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="fcb33-120">**DirSync 오류** 페이지에서 오류에 대 한 정보 및 문제 해결 방법에 대 한 팁이 포함 된 세부 정보 창을 표시 하려면 나열 된 오류 중 하나를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcb33-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
