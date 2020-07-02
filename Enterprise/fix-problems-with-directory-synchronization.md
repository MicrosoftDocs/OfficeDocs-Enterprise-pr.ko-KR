---
title: Microsoft 365의 디렉터리 동기화 문제 해결
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
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
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Office 365에서 발생 하는 디렉터리 동기화 문제의 일반적인 원인에 대해 설명 하 고 이러한 문제를 해결 하는 데 도움이 되는 몇 가지 방법을 제공 합니다.
ms.openlocfilehash: d9e390a7230499f724ebbdae592264a850dd9418
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998036"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Microsoft 365의 디렉터리 동기화 문제 해결

디렉터리 동기화를 사용 하면 온-프레미스에서 사용자 및 그룹을 계속 관리 하 고 추가, 삭제 및 변경 내용을 클라우드로 동기화 할 수 있습니다. 그러나 설치 프로그램은 다소 복잡 하며 때때로 문제의 원인을 파악 하기 어려울 수 있습니다. Microsoft는 잠재적인 문제를 파악 하 고 해결 하는 데 도움이 되는 리소스를 제공 합니다.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>무엇이 잘못 되었는지 어떻게 알 수 있나요?

무언가가 잘못 되었음을 나타내는 첫 번째 방법은 Microsoft 365 관리 센터의 DirSync 상태 타일이 문제가 있음을 나타낼 때입니다.
  
또한 테 넌 트에서 디렉터리 동기화 오류가 발생 했음을 나타내는 Microsoft 365에서 전자 메일 및 관리자 전자 메일에 대 한 메일을 받게 됩니다. 자세한 내용은 [Microsoft 365에서 디렉터리 동기화 오류 파악를](identify-directory-synchronization-errors.md)참조 하세요.
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Azure Active Directory Connect 도구를 가져오려면 어떻게 해야 합니까?

[Microsoft 365 관리 센터](https://admin.microsoft.com)에서 **사용자** \> **활성 사용자**로 이동 합니다. **기타** 메뉴 (세 개의 점선)를 클릭 하 고 **디렉터리 동기화**를 선택 합니다. 
  
[마법사의 지침](set-up-directory-synchronization.md) 에 따라 Azure AD Connect를 다운로드 합니다. 
  
여전히 Azure AD (Active Directory) 동기화 (DirSync)를 사용 하는 경우 dirsync 설치를 위한 시스템 요구 사항, 필요한 권한 및 일반적인 오류를 해결 하는 방법에 대 한 자세한 내용은 [Microsoft 365의 Azure Active Directory 동기화 도구 설치 및 구성 마법사 오류 메시지 문제 해결 방법을](https://go.microsoft.com/fwlink/p/?LinkId=396717) 확인 하세요. 
  
Azure ad Sync에서 Azure AD Connect로 업데이트 하려면 [업그레이드 지침](https://go.microsoft.com/fwlink/p/?LinkId=733240)을 참조 하세요.
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>Microsoft 365에서 디렉터리 동기화 문제의 일반적인 원인 해결

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**동기화 된 개체가 표시 되지 않거나 온라인으로 업데이트 되지 않거나, 서비스에서 동기화 오류 보고서를 가져옵니다.**

- [ID 동기화 및 중복 특성 복원력](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**관리 센터에 경고가 있거나 최근 동기화 이벤트가 없는 자동 전자 메일을 받는 경우**
- [Azure AD Connect 연결 문제 해결](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect 계정 및 사용 권한](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD Connect 동기화: Azure AD 서비스 계정을 관리하는 방법](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Azure Active Directory에 대한 디렉터리 동기화가 중지되거나 동기화가 하루 이상 등록되지 않았다는 경고가 표시됩니다.](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**암호 해시가 동기화 되지 않거나 최근 암호 해시 동기화가 아직 없는 경우 관리 센터에서 경고가 표시 됨**
- [Azure AD Connect 동기화로 암호 동기화 구현](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**개체 할당량이 초과 되었음을 알리는 경고가 표시 됨**
- 서비스를 보호 하는 데 도움이 되는 기본 제공 개체 할당량이 있습니다. 디렉터리에 Microsoft 365와 동기화 해야 하는 개체가 너무 많은 경우에는 [비즈니스 제품 지원에 문의](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) 하 여 할당량을 늘려야 합니다.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**동기화 되는 특성을 확인 해야 합니다.**
- 온-프레미스와 클라우드 간에 동기화 되는 모든 특성의 목록을 [여기](https://go.microsoft.com/fwlink/p/?LinkId=396719)에서 확인할 수 있습니다.

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**클라우드와 동기화 된 개체를 관리 하거나 제거할 수 없습니다.**
- 클라우드에서만 개체를 관리할 준비가 되셨습니까? 또는 온-프레미스에서 삭제 되었지만 클라우드에서는 개체가 없습니까? 이러한 문제를 해결 하는 방법에 대 한 지침은 동기화 및 [지원 문서](https://go.microsoft.com/fwlink/p/?LinkId=396720) 에서이 [문제 해결 오류](https://go.microsoft.com/fwlink/p/?linkid=842044) 를 참조 하세요.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**회사에서 동기화 할 수 있는 개체 수가 초과 되었다는 오류 메시지가 표시 됨**
- [여기](https://go.microsoft.com/fwlink/p/?LinkId=396721)에서이 문제에 대 한 자세한 내용을 확인할 수 있습니다.
   
## <a name="other-resources"></a>기타 리소스

- [Script to fix duplicate user principal names](https://go.microsoft.com/fwlink/p/?LinkId=396725)(중복된 사용자 계정 이름을 수정하기 위한 스크립트)
    
- [디렉터리 동기화를 위해 라우팅할 수 없는 도메인 (예: 로컬 도메인)을 준비 하는 방법](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [동기화 된 총 개체 수를 계산할 스크립트입니다.](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [AD FS 2.0 문제 해결](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [PowerShell을 사용 하 여 메일 사용이 가능한 그룹에 대 한 빈 DisplayName 특성 수정](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [PowerShell을 사용 하 여 중복 UPN 수정](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [PowerShell을 사용 하 여 중복 전자 메일 주소 수정](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>진단 도구

[Idfix 도구](prepare-directory-attributes-for-synch-with-idfix.md) 는 Microsoft 365로의 마이그레이션을 준비 하기 위해 온-프레미스 Active Directory 환경에서 id 개체 및 해당 특성의 검색 및 관리를 수행 하는 데 사용 됩니다. IDFix는 Microsoft 365 서비스와의 디렉터리 동기화를 담당 하는 Active Directory 관리자를 위한 것입니다. 

Microsoft 다운로드 센터에서 [IDFix 도구를 다운로드](https://go.microsoft.com/fwlink/p/?LinkId=396718) 합니다.