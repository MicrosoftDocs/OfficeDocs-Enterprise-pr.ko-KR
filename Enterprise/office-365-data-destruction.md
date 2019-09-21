---
title: Office 365 데이터 소멸
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Office 365 데이터 센터 디스크 드라이브 및 서버의 재활용, 폐기 또는 폐기에 대 한 Microsoft 정책 개요
ms.openlocfilehash: 41971cc690d0e1560f2cf7f5bc3ad544e8dab5c6
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067643"
---
# <a name="office-365-data-destruction"></a>Office 365 데이터 소멸

## <a name="physical-data-destruction"></a>실제 데이터 소멸

Microsoft는 디스크 드라이브의 재활용 및 폐기, 서버 장애 또는 더 이상 중지를 해결 하는 표준 정책을 데이터 처리 합니다. Microsoft는 Office 365 디스크 드라이브를 다시 사용 하기 전에 국가 표준 및 기술 특별 게시 800-88 ([미디어 삭제에 대 한 NIST SP 800-88 지침](http://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-88r1.pdf))와 일치 하는 실제 삭제 프로세스를 수행 합니다. Office 365의 모든 디스크 드라이브는 BitLocker 볼륨 수준 암호화를 사용 하 여 암호화 되므로 NIST SP 800-88 준수 지우기는 기술적으로 필요 하지 않습니다. 그렇지만 Microsoft는이 프로세스를 수행 합니다.

Office 365 데이터 센터 내에서 사용 되는 실패 한 디스크는 물리적으로 파괴 되 고 ISO 프로세스를 통해 감사 됩니다. 자산 유형에 따라 적절 한 폐기 방법이 결정 됩니다. 삭제할 수 없는 하드 드라이브의 경우 Microsoft는 소멸 프로세스를 사용 하 여 미디어를 파기 하 고 정보 복구를 렌더링 합니다. 예를 들어 디스크는 물리적으로 파괴 되거나, pulverized 또는 incinerated입니다. Microsoft는 모든 소멸 레코드를 보존 하 고 Office 365 내에서 다시 사용 되는 서버에 대 한 유사한 삭제 프로세스를 수행 합니다. 이러한 지침은 electronic 및 실제 삭제가 모두 포함 됩니다.

각 데이터 센터는 현장 물리적 소멸 프로세스를 사용 하 여 해당 디스크를 삭제 합니다. 디스크를 삭제 하도록 지정 된 저장소 미디어에 대 한 보안 계급는 데이터 센터의 각 영역에 있습니다. 각 보안 함 스테이션에는 비디오 모니터링 감시 기능이 있습니다. 삭제 함이 약 50% 용량에 도달 하면 사이트 서비스 팀이 실제 보안 팀에 연락 하 여 제거를 조정 합니다. 사이트 서비스 담당자 및 보안 Office 보안 삭제 함을 제거 하 고 지정 된 보안 저장소 영역에 배치 합니다. 삭제 중의 데이터 베어링 장치 처리를 관리 하는 정책 및 절차는 소멸을 위해 승인 된 기계 상태를 확인 하는 절차를 포함 하 여 주기적으로 테스트 됩니다.

데이터 폐기 프로세스에서 디스크는 NIST 800-88 (가능한 경우)과 호환 되는 방식으로 지워지고, 산업용 분쇄기 및 물리적으로 demolished에 놓이게 됩니다. Microsoft는 전송 중에 전송할의 체인에 대 한 NIST SP 800-88 일관성 있는 정리/삭제, 자산 파괴, 암호화, 정확한 인벤토리, 추적 및 보호 기능을 사용 하 여 데이터 센터를 유지 하는 자산의 책임을 관리 합니다. 이 프로세스는 닫힌 회로 텔레비전을 통해 모니터링 되며, 완료 시 파기 인증서가 발급 됩니다.

Microsoft는 EPS ( [익스트림 프로토콜 솔루션](http://www.enterprisedataerasure.com/) )에서 데이터 지우기 단위를 사용 합니다. EPS 소프트웨어는 정리 및 삭제/보안 지우기에 대 한 NIST SP 800-88 요구 사항을 지원 합니다. 정리 또는 폐기 전에 Microsoft asset manager에서 인벤토리가 만들어집니다. 공급 업체가 파괴에 사용 되는 경우 공급 업체가 자산 관리자에 의해 유효성이 검사 되는 각 자산의 파괴에 대 한 인증서를 제공 합니다.

## <a name="virtual-data-destruction"></a>가상 데이터 소멸

Microsoft는 데이터의 효과적인 가상 소멸을 해결 하는 데이터 처리 정책 및 절차를 포함 하 여 서비스 테 넌 트 간에 데이터가 부적절 하 게 공유 되는 것을 방지 하 고 서비스에서 하드 삭제 후에도 액세스할 수 있도록 합니다. 기본 실제 저장소가 다시 할당 된 경우에도 한 테 넌 트의 서비스에서 삭제 된 데이터는 다른 서비스 테 넌 트에서 액세스할 수 없습니다. 이는 가상 환경, 각 서비스 테 넌 트 내에서 응용 프로그램의 활성 삭제 동작 (예: [페이지 비우기](https://docs.microsoft.com/office365/securitycompliance/office-365-exchange-online-data-deletion#page-zeroing)) 및 필수 항목을 확장 하는 데 사용 되는 여러 가상화 및 조각화 기술에 대 한 복합 효과의 결과입니다. 미디어 및 응용 프로그램 콘텐츠 암호화 프로세스