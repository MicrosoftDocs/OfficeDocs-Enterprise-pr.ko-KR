---
title: Microsoft 365 서비스 상태를 확인 하는 방법
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: 지원 서비스를 호출 하기 전에 Microsoft 365 서비스의 상태를 확인 하 여 활성 서비스가 중단 되었는지 확인 합니다.
ms.openlocfilehash: d937310faeaf5af63a6c36841d7a609006fc4ab5
ms.sourcegitcommit: 057f0fce08b41a00581fc4736cad89270129c703
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2020
ms.locfileid: "44266696"
---
# <a name="how-to-check-microsoft-365-service-health"></a>Microsoft 365 서비스 상태를 확인 하는 방법

[![관리 센터가 변경되고 있음을 알리는 레이블이며 aka.ms/aboutM365preview에서 자세한 내용을 확인할 수 있습니다.](media/O365-Admin-AdminCenterChanging.png)](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview?view=o365-worldwide)

[Microsoft 365 관리 센터](https://go.microsoft.com/fwlink/p/?linkid=2024339)의 **서비스 상태** 페이지에서 웹, YAMMER, Microsoft Dynamics CRM 및 모바일 장치 관리 클라우드 서비스를 포함 하는 microsoft 서비스의 상태를 볼 수 있습니다. 클라우드 서비스와 관련된 문제가 발생한 경우 지원 서비스에 문의하거나 문제 해결에 시간을 소비하기 전에 먼저 서비스 상태를 확인하여 이 문제가 현재 해결이 진행 중인 상태인 알려진 문제인지 확인할 수 있습니다.

서비스 포털에 로그인 할 수 없는 경우 [서비스 상태 페이지](https://status.office365.com) 를 사용 하 여 테 넌 트에 로그인 하지 못하도록 하는 알려진 문제를 확인할 수 있습니다.
  
### <a name="how-to-check-service-health"></a>서비스 상태 확인 방법

1. Microsoft 365 관리 센터로 이동 하 여 [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339) 관리자 계정으로 로그인 합니다.

    > [!NOTE]
    > 전역 관리자 또는 서비스 관리자 역할이 할당된 사용자는 서비스 상태를 볼 수 있습니다. Exchange, SharePoint 및 비즈니스용 Skype 관리자가 서비스 상태를 볼 수 있도록 하려면 이러한 관리자에게도 서비스 관리자 역할을 할당해야 합니다. 서비스 상태를 볼 수 있는 역할에 대 한 자세한 내용은 [정보 관리 역할](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide#roles-available-in-the-microsoft-365-admin-center)을 참조 하십시오.
  
2. 새 관리 센터를 사용 하지 않는 경우 **홈** 페이지에서 오른쪽 위 모서리에 있는 **새 관리 센터 사용해 보기** 를 선택 합니다.

3. 서비스 상태를 보려면 관리 센터에서 **상태**  >  **서비스 상태**를 이동 하거나 **홈 대시보드에서** **서비스 상태** 카드를 선택 합니다. 대시보드 카드에는 활성 서비스 문제가 있는지와 자세한 **서비스 상태** 페이지에 대 한 링크가 표시 됩니다.
  
4. **서비스 상태** 페이지에서 각 클라우드 서비스의 상태는 표 형식으로 표시 됩니다.

   ![View of current issues in service health](media/service-health-all-services.png)

**모든 서비스** 탭 (기본 보기)에는 모든 서비스와 해당 현재 상태가 표시 됩니다. 아이콘 및 **상태** 열은 각 서비스의 상태를 나타냅니다. 

현재 인시던트가 발생 하는 서비스에 대 한 보기를 필터링 하려면 페이지 맨 위에 있는 **인시던트** 탭을 선택 합니다. **권고** 탭을 선택 하면 현재 권고가 게시 된 서비스만 표시 됩니다. 

**기록** 탭에는 해결 된 사건 및 권고의 기록이 표시 됩니다.

Microsoft 365 서비스에 문제가 발생 하 여 **서비스 상태** 페이지에 표시 되지 않으면 **문제점 보고**를 선택 하 고 간단한 양식을 작성 하 여이에 대해 알려주십시오. Microsoft는 다른 조직에서 제공 하는 데이터 및 보고서를 살펴보고 문제가 광범위 하 게 진행 된 경우와 서비스에서 시작 되었는지 확인 합니다. 문제가 해결 된 경우 **서비스 상태** 페이지에 새 인시던트 또는 권고로 추가 하 여 확인을 추적할 수 있습니다. 30 분 이내에 목록에 표시 되지 않는 경우에는 지원 서비스에 문의 하 여 문제를 해결 해 보세요.

활성 인시던트의 테 넌 트 및 상태 변경에 영향을 주는 새 인시던트의 전자 메일 알림을 등록 하려면 **기본 설정을**선택 하 고 **전자 메일에서 me Service heath 알림 보내기를**클릭 한 후 다음을 지정 합니다.

- 최대 2 개의 전자 메일 주소
- 인시던트 또는 권고에 대해 알림을 사용할지 여부
- 알림을 받으려는 서비스

> [!TIP]
> 또한 모바일 장치에서 [Microsoft 365 Admin 앱](https://go.microsoft.com/fwlink/p/?linkid=627216) 을 사용 하 여 서비스 상태를 볼 수 있으며,이는 푸시 알림을 최신 상태로 유지 하는 데 유용한 방법입니다. 
  
### <a name="view-details-of-posted-service-health"></a>게시된 서비스 상태의 세부 정보 보기

**모든 서비스** 보기에서 서비스 상태를 선택 하면 권고 또는 사건에 대 한 요약 보기가 열립니다.
  
![서비스 advise를 보여 주는 스크린샷](media/service-health-advisory.png)

권고 또는 인시던트 요약은 다음 정보를 제공합니다.

- **제목** -문제에 대 한 요약입니다.
- **서비스** -영향을 받는 서비스의 이름입니다.
- **ID** -문제의 숫자 id입니다.
- **Status** -이 문제가 서비스에 미치는 영향
- **시작 시간** -문제가 시작 된 시간입니다.
- **Last updated** -서비스 상태 메시지가 마지막으로 업데이트 된 시간입니다. 솔루션을 적용 하는 과정의 진행 상태를 알 수 있도록 메시지를 자주 게시 합니다.

솔루션에서 작업 하는 동안 게시 된 모든 메시지 [기록을](#history) 비롯 하 여 문제에 대 한 자세한 정보를 표시 하는 문제 정보 페이지를 보려면 문제점 제목을 선택 합니다.

![문제 세부 정보를 보여 주는 스크린샷](media/service-health-advisory-detail.png)

### <a name="translate-service-health-details"></a>서비스 상태 세부 정보 번역

서비스 상태 설명은 실시간으로 게시되므로 해당 언어로 자동 번역되지 않으며 서비스 이벤트의 세부 정보는 영어로만 제공됩니다. 설명을 번역하려면 다음 단계를 수행합니다.
  
1. 1.[번역기](https://www.bing.com/translator/)로 이동합니다.

2. **서비스 상태** 페이지에서 인시던트 또는 권고를 선택합니다. **세부 정보 표시** 아래에서 문제에 대한 텍스트를 복사합니다.

3. 번역기에서 텍스트를 붙여넣고 **번역하기**을 선택합니다.

### <a name="definitions"></a>정의

대부분의 경우 서비스는 추가 정보 없이 정상 상태로 표시 됩니다. 서비스에 문제가 있으면 문제가 권고 또는 인시던트로 식별되고 현재 상태를 표시합니다.
  
> [!TIP]
> 계획된 유지 관리 이벤트는 서비스 상태에 표시되지 않습니다. **메시지 센터**를 통해 최신 상태를 유지함으로써 계획된 유지 관리 이벤트를 추적할 수 있습니다. 변경 계획으로 분류된 메시지로 필터링하여 변경이 발생하는 시기, 해당 효과 및 이러한 변경에 대해 준비하는 방법을 확인하세요. 자세한 내용은 [Microsoft 365의 메시지 센터를](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) 참조 하세요.
  
### <a name="incidents-and-advisories"></a>인시던트 및 권고

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|서비스에 권고가 표시되면 Microsoft에서 일부 사용자에게 영향을 미치는 문제를 알고 있지만, 서비스를 계속 사용할 수는 있습니다. 권고에는 일반적으로 문제에 대한 해결 방법이 있으며, 문제가 일시적으로 발생하는 것일 수 있거나 범위 및 사용자 영향에서 제한적입니다.  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|서비스에 활성 인시던트가 표시되면 이 인시던트가 중요 문제이며 서비스 또는 서비스의 주요 기능을 사용할 수 없습니다. 예를 들어 사용자가 전자 메일을 보내고 받을 수 없거나 로그인할 수 없습니다. 인시던트는 사용자에게 눈에 띄는 영향을 줍니다. 진행 중인 인시던트가 있는 경우 서비스 상태 대시보드에서 조사, 완화 노력 및 해결 확인과 관련된 업데이트를 제공합니다.  <br/> |

### <a name="status-definitions"></a>상태 정의

|**상태**|**정의**|
|:-----|:-----|
|**조사** | Microsoft에서 잠재적인 문제를 알고 있으며 문제의 상황과 영향의 범위에 대한 추가 정보를 수집하고 있습니다. |
|**서비스 저하** | Microsoft에서 서비스 또는 기능 사용에 영향을 줄 수 있는 문제가 있음을 확인했습니다. 서비스가 평소보다 느리게 작동하거나, 일시적인 중단이 발생하거나, 기능이 작동하지 않는 등의 경우에 이 상태가 표시될 수 있습니다. |
|**서비스 중단** | 문제가 사용자의 서비스 액세스 기능에 영향을 준다고 판단한 이 상태가 표시됩니다. 이 경우 문제가 중대하며 일관되게 재현될 수 있습니다. |
|**서비스를 복원하는 중** | 문제의 원인이 식별되었으며, Microsoft에서 수행할 정정 작업을 알고 있고 서비스를 다시 정상 상태로 복원하는 프로세스를 진행하고 있습니다. |
|**확장된 복구** | 이 상태는 대부분의 사용자에 대해 서비스를 복원하기 위한 정정 작업이 진행 중이지만, 영향을 받는 모든 시스템에 이를 적용하는 데 시간이 다소 소요될 것임을 나타냅니다. 영구적인 수정 사항을 적용하기 위해 대기하는 동안 영향을 줄이기 위해 임시 수정 사항을 적용한 경우에도 이 상태가 표시될 수 있습니다. |
|**조사 일시 중단됨** | 잠재적 문제에 대한 자세한 조사 결과, 추가 조사를 하기 위한 고객의 추가 정보가 필요한 경우 이 상태가 표시됩니다. 고객의 행동이 요구되는 경우 필요한 데이터나 로그를 알려드립니다. |
|**서비스 복원됨** | Microsoft에서 정정 작업이 기본 문제를 해결했으며 서비스가 정상 상태로 복원되었음을 확인했습니다. 문제를 확인하려면 문제 세부 정보를 확인하세요. |
|**가양성** | 자세한 조사가 완료 되 면 서비스가 정상 상태이 고 정상적으로 작동 하는 것으로 확인 된 것입니다. 서비스에 대 한 영향을 관찰 하거나 서비스 외부에서 발생 한 인시던트를 파악 하지 못했습니다. |
|**사후 문제 보고서 게시 됨** | Microsoft는 근본 원인 정보를 포함 하는 특정 문제와 유사한 문제가 다시 발생 하지 않도록 하는 다음 단계에 대 한 사후 문제 보고서를 게시 했습니다. |

### <a name="history"></a>기록

서비스 상태를 통해 현재 상태를 확인 하 고 최근 30 일 이내에 테 넌 트에 영향을 받은 모든 서비스 권고 및 인시던트 기록을 볼 수 있습니다. 모든 서비스의 이전 상태를 보려면 문제 정보 페이지에서 **기록 보기** 를 선택 합니다.
  
![Show link to health history](media/service-health-view-history.png)
  
선택한 시간 범위에서 게시된 모든 서비스 상태 메시지 목록이 다음과 같이 표시됩니다.
  
![View service health history](media/service-health-history.png)
  
모든 행을 확장 하 여 문제에 대 한 세부 정보를 표시 합니다.
  
가동 시간에 대 한 자세한 내용은 [Microsoft 365의 투명 작업](https://go.microsoft.com/fwlink/?linkid=848695)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[Microsoft 365 관리 센터의 활동 보고서](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)