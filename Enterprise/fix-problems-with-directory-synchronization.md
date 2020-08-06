---
title: Microsoft 365의 디렉터리 동기화 문제 해결
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Priority
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Office 365의 디렉터리 동기화 문제의 일반적인 원인을 설명하고 문제를 해결할 수 있는 몇 가지 방법을 제공합니다.
ms.openlocfilehash: faf0f061b8f2798054e63f3338b8076c0ec88f73
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "46570971"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Microsoft 365의 디렉터리 동기화 문제 해결

디렉터리 동기화를 수행하면 온프레미스에서 사용자와 그룹을 지속적으로 관리하고 추가, 삭제, 변경 내용을 클라우드로 동기화할 수 있습니다. 그러나 동기화를 설정하는 과정은 다소 복잡하며, 문제의 원인을 파악하기가 어려운 경우도 있습니다. 이와 같은 잠재적 문제를 식별하여 해결하는 데 도움이 되는 리소스를 소개합니다.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>문제가 있는 경우 어떻게 알 수 있나요?

문제가 있는 경우 이를 나타내는 첫 번째 표시는 Microsoft 365 관리 센터의 DirSync 상태 타일에 문제가 있음이 표시되는 것입니다.
  
또한 Microsoft 365로부터 테넌트에 디렉터리 동기화 오류가 발생했음을 나타내는 메일(대체 전자 메일 및 관리자 전자 메일로 전송됨)을 받게 됩니다. 자세한 내용은 [Microsoft 365의 디렉터리 동기화 오류 식별](identify-directory-synchronization-errors.md)을 참조하세요.
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Azure Active Directory Connect 도구는 어떻게 사용하나요?

[Microsoft 365 관리 센터](https://admin.microsoft.com)에서 **사용자** \> ** 활성 사용자**로 이동합니다. **더보기(세점)** 메뉴를 클릭하고 **디렉터리 동기화**를 선택합니다. 
  
[마법사의 안내](set-up-directory-synchronization.md)에 따라 Azure AD 연결을 다운로드합니다. 
  
아직 Azure Active Directory(Azure AD) 동기화 (DirSync)를 사용중이라면 dirsync 설치 시스템 요구사항, 필요한 권한 및 일반 오류 문제 해결 정보를 위하여 [Microsoft 365에서 Azure Active Directory 동기화 도구 설치 및 구성 마법사 오류 메시지 문제 해결 방법](https://go.microsoft.com/fwlink/p/?LinkId=396717)을 참조하세요. 
  
Azure AD 동기화 서비스에서 Azure AD Connect로 업데이트 하려면 [업그레이드 지침](https://go.microsoft.com/fwlink/p/?LinkId=733240)을 참조하세요.
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>Microsoft 365에서 발생하는 디렉터리 동기화 문제의 일반적인 원인 해결

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>동기화된 개체가 온라인에서 표시나 업데이트 되지 않거나 서비스로부터 동기화 오류 보고서를 받습니다.

- [ID 동기화 및 중복 특성 복원력 식별](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>관리 센터에 알림이 표시되거나, 최근 동기화 이벤트가 없다는 자동 전자 메일을 받습니다.
- [Azure AD Connect 연결 문제 해결](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect 계정 및 사용 권한](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD Connect 동기화: Azure AD 서비스 계정을 관리하는 방법](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Azure Active Directory에 대한 디렉터리 동기화가 중지되거나 동기화가 하루 이상 등록되지 않았다는 경고가 표시됩니다.](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>암호가 동기화되지 않거나, 관리 센터에 최근 암호 동기화가 없다는 알림이 표시됩니다
- [Azure AD Connect 동기화로 암호 동기화 구현](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>개체 할당량을 초과했다는 알림이 표시됩니다.
- 서비스를 보호를 위해 개체 할당량이 기본적으로 제공됩니다. 디렉터리에 Microsoft 365로 동기화해야 하는 개체가 너무 많은 경우에는 [비즈니스 제품 지원 문의](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)하여 할당량을 늘려야 합니다.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>동기화되는 특성을 확인해야 합니다.
- [여기](https://go.microsoft.com/fwlink/p/?LinkId=396719)에서 온-프레미스와 클라우드 간에 동기화되는 모든 특성 목록을 확인할 수 있습니다.

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>클라우드에 동기화된 개체를 관리하거나 제거할 수 없습니다.
- 클라우드에서만 개체를 관리할 준비가 되었습니까? 혹은 개체를 온프레미스에서는 삭제했는데 클라우드에는 남아 있습니까? 이 문제를 해결하는 방법에 대한 지침은 [동기화](https://go.microsoft.com/fwlink/p/?linkid=842044) 및 [지원 문서 오류 문제 해결](https://go.microsoft.com/fwlink/p/?LinkId=396720)을 참조 하세요.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>회사에서 동기화할 수 있는 개체 수가 초과되었다는 오류 메시지가 표시됨
- [여기](https://go.microsoft.com/fwlink/p/?LinkId=396721)에서 이 문제에 대해 자세히 알아볼 수 있습니다.
   
## <a name="other-resources"></a>다른 리소스

- [중복된 사용자 계정 이름을 수정하기 위한 스크립트](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [디렉터리 동기화를 위해 라우팅할 수 없는 도메인(예: .local 도메인)을 준비하는 방법](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [동기화된 총 개체 수를 계산하기 위한 스크립트](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [문제 해결 AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [PowerShell을 사용하여 메일 사용 가능 그룹의 빈 DisplayName 특성 수정](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [PowerShell을 사용하여 중복 UPN 수정](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [PowerShell을 사용하여 중복된 전자 메일 주소 수정](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
