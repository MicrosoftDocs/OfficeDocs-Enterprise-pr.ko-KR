---
title: Office 365 GCC High 및 DoD에 대 한 추가 네트워크 보안 요구 사항
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150m
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: '요약: Office 365 GCC High 및 DoD에는 추가 네트워크 보안 요구 사항이 있습니다.'
hideEdit: true
ms.openlocfilehash: a79204809787391065ac833d9a3872af4cdc1528
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "44371634"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a>Office 365 GCC High 및 DOD에 대 한 추가 네트워크 보안 요구 사항

*이 문서는 Office 365 GCC High, Office 365 DOD, Microsoft 365 GCC High 및 Microsoft 365 DOD에 적용 됩니다.*

Office 365 GCC High 및 DOD는 미국 정부 및 해당 공급자 및 계약자의 요구를 충족 하기 위한 안전한 클라우드 환경입니다.  이러한 클라우드 환경에는 서비스에 액세스할 수 있는 외부 끝점에 대 한 추가 네트워크 제한이 있습니다.

통합 된 id 또는 하이브리드 공존을 사용 하기 위한 GCC High 및 DOD 고객은 기존 온-프레미스 배포에 대 한 인바운드 및/또는 아웃 바운드 액세스를 허용 해야 합니다.  이러한 활동의 예는 다음과 같습니다.

* 페더레이션 id 사용 (Active Directory Federation Services 또는 유사 하 게 지원 되는 STS)
* 온-프레미스 Exchange Server 또는 비즈니스용 Skype 배포와 하이브리드 동시 사용
* 온-프레미스 시스템에서 기존 사용자 콘텐츠 마이그레이션

서비스가 온-프레미스 끝점과 통신할 수 있도록 하려면 네트워크 변경에 대 한 Office 365 엔지니어링 전자 메일을 보내야 **합니다** .

> [!WARNING]
> 모든 요청의 SLA는 **3 주** 이며 필요한 보안 및 준수 제어 및 배포 파이프라인으로 인해 촉진 될 수 없습니다.  여기에는 초기 온 보 딩 네트워크 요청과 서비스로 마이그레이션한 후의 변경 내용이 포함 됩니다.  네트워크 팀에서이 시간 표시 막대를 확인 하 여 계획 주기에 포함 해야 합니다.

다음 정보를 사용 하 여 [Office 365 정부 네트워크 허용 목록](mailto:o365gwlt@microsoft.com) 에 전자 메일을 보내 주시기 바랍니다.

* **대상**: [Office 365 정부 네트워크 허용 목록](mailto:o365gwlt@microsoft.com)
* **보낸**사람: 테 넌 트 관리자-보내는 전자 메일은 테 넌 트의 전역 관리자 연락처와 일치 **해야 합니다** .
* **전자 메일 제목**: OFFICE 365 GCC High Network 요청-contoso.onmicrosoft.us (이를 테 넌 트 이름으로 바꾸기)

메시지 본문에는 다음과 같은 데이터가 포함 되어야 합니다.

* Microsoft Online Services 테 넌 트 이름 (예: contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)
* 네트워크 변경 및 잘못 된 서브넷에 대 한 후속 통신을 위해 Microsoft에서 통신할 전자 메일 그룹입니다.
* 온-프레미스 배포와 함께 Microsoft 팀 하이브리드 공존을 사용할지 여부를 지정 합니다.
* 페더레이션 id 시스템 외부에서 액세스할 수 있는 URL (예: sts.contoso.com) 및 IP 주소 범위 (예: 10.1.1.0/28)
* CIDR 표기법의 온-프레미스 PKI 인증서 해지 목록 URL 및 IP 주소 범위
* CIDR 표기법으로 Exchange Server 온-프레미스 배포를 위한 외부에서 액세스할 수 있는 URL 및 IP 주소 범위
* CIDR 표기법에서 비즈니스용 Skype 온-프레미스 배포에 대 한 외부에서 액세스할 수 있는 URL 및 IP 주소 범위

보안 및 규정 준수를 위해서는 요청에 대 한 다음과 같은 제한 사항을 염두에 두십시오.

* 테 넌 트 당 4 개의 서브넷 제한이 있습니다.
* 서브넷은 CIDR 표기법 (예: 10.1.1.0/28) 이어야 합니다.
* 서브넷 범위는/24 보다 클 수 없습니다.
* 상업용 클라우드 서비스 (상업용 Office 365, Google G-제품군, Amazon Web Services 등)에 대 한 액세스를 허용 하는 요청을 수용할 **수 없습니다** .

Microsoft에서 요청을 받아서 승인한 후에는 3 주 동안 SLA를 제공 하 고이를 촉진 시킬 수 없습니다.  요청을 받았을 때 초기 승인이 수신 되 고 완료 된 후 최종 승인을 받게 됩니다.
