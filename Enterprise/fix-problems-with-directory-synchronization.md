---
title: Office 365의 디렉터리 동기화 문제 해결
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Office 365에서 디렉터리 동기화 문제의 일반적인 원인에 설명 하 고 문제를 해결 하 고 해결 하는데 몇 메서드를 제공 합니다.
ms.openlocfilehash: ad3b6e27439354a2ede9b1a4b100e0f9e06148d3
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541980"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>Office 365의 디렉터리 동기화 문제 해결

디렉터리 동기화를 통해 온-프레미스 사용자 및 그룹을 관리 하 고 추가, 삭제 및 클라우드로 변경 내용을 동기화를 계속 수 있습니다. 하지만 설치 프로그램은 더 복잡 하 고 문제의 원인을 파악 하기 어려운 경우가 있습니다. 잠재적인 문제를 식별 하 고 해결 하는데 도움이 되는 리소스가 제공 됩니다.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>잘못 된 경우 어떻게 알 수 있습니까?

잘못 된 것은 첫번째 해당할 Office 365 관리 센터에서 디렉터리 동기화 상태 타일 없음을 문제가 발생 하는 경우 표시 됩니다.
  
![디렉터리 동기화 상태 관리 센터 미리 보기에서 바둑판식으로 배열](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
또한 Office 365 테 넌 트에 디렉터리 동기화 오류가 발생 했는지 여부를 나타내는 (대체 전자 메일 및 관리 전자 메일을) 메일을 받습니다. 자세한 내용은 [Office 365에서 식별 디렉터리 동기화 오류](identify-directory-synchronization-errors.md)를 참조 하십시오.
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Azure Active Directory 연결 도구를 가져오는 방법

Office 365 관리 센터에서 이동 * * 사용자 * * \> **활성 사용자**입니다. **더 많은** 메뉴를 클릭 하 고 **디렉터리 동기화**를 선택 합니다. 
  
![더 많은 메뉴에서 디렉터리 동기화를 선택 합니다.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
이전 Office 365 관리 센터에서 **사용자** 에 게 이동 \> **활성 사용자**및 **Active Directory 동기화**옆에 있는 선택 **를 설정** 합니다. 
  
![Active Directory 동기화 옆에 있는 설정을 선택합니다](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
Azure AD 연결을 다운로드 하려면 [마법사의 지시](set-up-directory-synchronization.md) 를 따릅니다. 
  
여전히 Azure Active Directory 동기화 (DirSync)를 사용 하는 경우 수행을 설치 하려면 시스템 요구 사항에 대 한 내용은 [Azure Active Directory 동기화 도구 설치 및 Office 365에서 구성 마법사 오류 메시지 문제를 해결 하는 방법](https://go.microsoft.com/fwlink/p/?LinkId=396717) 에 대 한 정보 디렉터리 동기화, 필요한 권한 및 일반적인 오류를 해결 하는 방법입니다. 
  
Azure Active Directory 동기화에서 Azure AD 연결을 업데이트 하려면 [대 한 업그레이드 지침](https://go.microsoft.com/fwlink/p/?LinkId=733240)을 참조 하십시오.
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>문제가 발생 하는 Office 365에서 디렉터리 동기화 설정 하는 일반적인 해결

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**동기화 된 개체에 표시 되지 않거나 온라인으로 업데이트 또는 서비스에서 동기화 오류 보고서 나타남 합니다.**

- [Identity 동기화 및 복제 특성 복구](https://go.microsoft.com/fwlink/p/?LinkID=798300)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**Office 365 관리 센터에서 알림을 I 또는 최근 동기화 이벤트 된 하지 않은 자동된 전자 메일이 받고**
- [Azure AD 연결 연결 문제를 해결 합니다.](https://go.microsoft.com/fwlink/p/?LinkId=820597)
- [Azure AD 연결 계정 및 사용 권한](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD 연결 동기화: Azure AD 서비스 계정을 관리 하는 방법](https://go.microsoft.com/fwlink/p/?LinkId=820599)
- [Azure Active Directory 중지 되거나 사용자에 대 한 디렉터리 동기화는 사용자에 게 경고 메시지 동기화 하지 않은 하루 이상에 등록 하는](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**암호 해시 동기화 되지 않은 또는 최근 암호 해시 동기화 된 하지 않은 Office 365 관리 센터에서 알림을 표시**
- [Azure AD 연결 동기화를 사용 하 여 암호 해시 동기화를 구현합니다.](https://go.microsoft.com/fwlink/p/?LinkId=820600)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**개체 할당량을 초과 하는 알림이 표시**
- 서비스를 보호 하는 기본 제공 개체 할당량을 제공 됩니다. Office 365와 동기화 하는 디렉터리에 너무 많은 개체를 사용 하는 경우 프로그램 할당량을 늘릴 수를 [비즈니스 제품에 대 한 지원 되는 대화 상대](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) 게 해야 합니다.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**동기화되는 특성을 확인해야 함**
- 온-프레미스 및 클라우드 [오른쪽 여기](https://go.microsoft.com/fwlink/p/?LinkId=396719)간에 동기화 되는 모든 특성의 목록을 확인할 수 있습니다.

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**관리 하거나 클라우드로 동기화 된 개체를 제거할 수 없음**
- 클라우드에서 개체를 관리 준비가 되셨습니까? 또는 삭제 된 온-프레미스, 되었지만 클라우드에서 걸려 않은 개체는 다음과 같은? 이러한 문제를 해결 하는 방법에 대 한 정보를 [동기화 하는 동안 오류 문제를 해결](https://go.microsoft.com/fwlink/p/?linkid=842044) 와 지침에 대 한 [문서를 지원](https://go.microsoft.com/fwlink/p/?LinkId=396720) 하기에 수행 합니다.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**회사에서 동기화할 수 있는 개체 수가 초과되었다는 오류 메시지가 표시됨**
- 자세한 내용은이 문제에 대 한 [여기](https://go.microsoft.com/fwlink/p/?LinkId=396721)합니다.
   
## <a name="other-resources"></a>기타 리소스

- [중복 된 사용자 계정 이름을 수정 하는 스크립트](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [디렉터리 동기화를 위한 라우팅할 수 없는 도메인 (예:.local 도메인)를 준비 하는 방법](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [총 동기화 된 개체 수를 계산 하는 스크립트](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [AD FS 2.0 문제해결](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [PowerShell을 사용 하 여 메일 사용이 가능한 그룹에 대 한 빈 DisplayName 특성을 수정 하려면](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [PowerShell을 사용 하 여 중복 된 UPN을 수정 하려면](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [PowerShell을 사용 하 여 중복 된 전자 메일 주소를 수정 하려면](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>진단 도구

[IDFix 도구](prepare-directory-attributes-for-synch-with-idfix.md) 는 Office 365로 마이그레이션 준비 하는 과정에서 온-프레미스 Active Directory 환경에서 검색 및 identity 개체 및 특성의 업데이트 관리를 수행 하는데 사용 됩니다. IDFix는 Office 365 서비스와 디렉터리 동기화에 대 한 담당 하는 Active Directory 관리자를 위한 것입니다. 

Microsoft 다운로드 센터에서 [IDFix 도구를 다운로드](https://go.microsoft.com/fwlink/p/?LinkId=396718) 합니다.