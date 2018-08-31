---
title: Contoso Corporation에 대 한 보안
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: '요약: Contoso이 Microsoft의 클라우드 서비스의 기능을 위해 보안 요구 사항이 매핑되어야 하 고 클라우드 보안 준비에 대 한 경로 결정 하는 방법을 이해 합니다.'
ms.openlocfilehash: 722c01995c95c36b9975b0682858c38063f79d2c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914833"
---
# <a name="security-for-the-contoso-corporation"></a>Contoso Corporation에 대 한 보안

 **요약:** Contoso이 Microsoft의 클라우드 서비스의 기능을 위해 보안 요구 사항이 매핑되어야 하 고 클라우드 보안 준비에 대 한 경로 결정 하는 방법을 이해 합니다.
  
Contoso는 자신의 정보 보안 및 보호 하는 방법에 대 한 심각한 합니다. 클라우드 포함 한 IT 인프라, 전환할 때가 온-프레미스 보안 요구 사항을 지원 하 고 Microsoft의 클라우드 서비스에서 구현 하는 된 있는지 수행 합니다.
  
## <a name="contosos-security-requirements-in-the-cloud"></a>클라우드에서 Contoso의 보안 요구 사항

클라우드를 위한 Contoso의 보안 요구 사항은 다음과 같습니다.
  
- 클라우드 리소스에 대 한 강력한 인증
    
    클라우드 리소스 액세스를 인증 해야 하 고, 활용 하 여 가능한 경우에 다단계 인증 합니다.
    
- 인터넷을 통해 트래픽에 대 한 암호화
    
    인터넷을 통해 전송 되는 없음 데이터는 일반 텍스트 형식입니다. 항상 HTTPS 연결, IPsec 또는 다른 끝-데이터 암호화 방법을 사용 합니다.
    
- 클라우드에서 보관 된 데이터에 대 한 암호화
    
    또는 다른 곳에서 클라우드 디스크에 저장 된 모든 데이터를 암호화 된 형식에서 이어야 합니다.
    
- 최소 권한 액세스에 대 한 Acl
    
    계정 권한 클라우드에서 리소스 및 작업을 수행 하기 수 있는 항목에 액세스 하려면 최소 권한 지침을 따라야 합니다.
    
## <a name="contosos-data-sensitivity-classification"></a>Contoso의 데이터 민감도 분류

정보를 사용 하 여 Microsoft의 [데이터 분류 도구 키트](https://msdn.microsoft.com/library/hh204743.aspx)에, Contoso 자신의 데이터에 대 한 분석을 수행 하 고 다음 수준을 결정 합니다.
  
|**수준 1: 낮은 비즈니스 가치**|**수준 2: 중간 규모 비즈니스 가치**|**수준 3: 높은 비즈니스 가치**|
|:-----|:-----|:-----|
|데이터를 암호화와 인증 된 사용자만 사용할 수 있는  <br/> 온-프레미스 및 클라우드 기반 저장소 및 Office 365와 같은 작업에 저장 된 모든 데이터를 제공 합니다. 서비스 및 클라이언트 장치 사이 전송 및 서비스에 상주 하는 동안 데이터가 암호화 됩니다.  <br/> 수준 1 데이터의 예는 일반적인 비즈니스 통신 (전자 메일) 및 관리, 판매에 대 한 파일 및 작업자를 지원 합니다.  <br/> |수준 1을 더한 값 강력한 인증 및 데이터 손실 방지  <br/> 강력한 인증 SMS 유효성 검사 규칙이 다단계 인증을 포함합니다. 데이터 손실 방지를 사용 하면 중요 또는 중요 한 정보는 온-프레미스 네트워크 외부 이동 하지 않습니다.  <br/> 수준 2 데이터의 예로 재무 및 법적 정보 및 새 제품에 대 한 데이터를 연구 및 개발 합니다.  <br/> |수준 2와 가장 높은 수준의 암호화, 인증 및 감사  <br/> 가장 높은 수준의 보관 하 고 클라우드, 국가별 규정 준수 데이터에 대 한 암호화 다단계 인증 스마트 카드 및 세분화 된 감사 및 경고와 함께 나타냅니다.  <br/> 수준 3 데이터의 예로 고객 및 파트너 개인 식별 정보 및 제품 엔지니어링 사양 독점 제조 기술입니다.  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a>Contoso의 데이터 수준을 Microsoft 클라우드 서비스 및 기능에 매핑

다음 표에서 Microsoft의 클라우드 서비스에서 Contoso의 데이터 수준 기능에 대 한 매핑이 보여줍니다.
  
||**SaaS**|**Azure PaaS**|**Azure IaaS**|
|:-----|:-----|:-----|:-----|
|수준 1: 낮은 비즈니스 가치  <br/> | 모든 연결에 대 한 HTTPS <br/>  작동 중단 시 암호화 <br/> | HTTPS 연결에만 지원 합니다. <br/>  Azure에 저장 된 파일을 암호화 합니다. <br/> | 서버 액세스에 대 한 HTTPS 또는 IPsec 필요 <br/>  Azure 디스크 암호화 <br/> |
|수준 2: 중간 규모 비즈니스 가치  <br/> | Azure AD 다단계 인증 (MFA) SMS 사용 <br/> | Azure 키 볼트를 사용 하 여 암호화 키에 대 한 <br/>  SMS 사용 하는 azure AD MFA <br/> | SMS 사용 하는 MFA <br/> |
|수준 3: 높은 비즈니스 가치  <br/> | Azure 권한 관리 시스템 (RMS) <br/>  스마트 카드와 함께 azure AD MFA <br/>  Intune 조건부 액세스 <br/> | Azure RMS <br/>  스마트 카드와 함께 azure AD MFA <br/> | 스마트 카드와 함께 MFA <br/> |
   
## <a name="contosos-information-policies"></a>Contoso의 정보 정책

다음 표에 Contoso의 정보 정책입니다.
  
||**액세스**|**데이터 보존**|**정보 보호**|
|:-----|:-----|:-----|:-----|
|수준 1: 낮은 비즈니스 가치  <br/> | 모두에 대 한 액세스를 허용 합니다. <br/> |6개월  <br/> |암호화를 사용 하 여  <br/> |
|수준 2: 중간 규모 비즈니스 가치  <br/> | Contoso 직원, 하청 및 파트너에 대 한 액세스를 허용 합니다. <br/>  MFA, TLS 및 MAM를 사용 하 여 <br/> |2년  <br/> |데이터 무결성을 위해 해시 값을 사용 합니다.  <br/> |
|수준 3: 높은 비즈니스 가치  <br/> | 임원 및 엔지니어링, 제조에 잠재 고객에 대 한 액세스를 허용 합니다. <br/>  관리 되는 네트워크 장치와 RMS <br/> |7 년  <br/> |부인 방지에 대 한 디지털 서명 사용  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a>클라우드 보안 준비에 대 한 Contoso의 경로

Microsoft 클라우드를 위한 보안을 준비 하려면 다음 단계를 사용 하는 Contoso 합니다.
  
1. 관리자 계정을 클라우드를 위한 최적화
    
    Contoso 않은 기존 Windows Server AD 관리자 계정의 전자 광범위 한 검토 하 고 일련의 클라우드 관리자 계정 및 그룹을 설정 합니다.
    
2. 세 수준으로 데이터 분류 분석을 수행 합니다.
    
    Contoso 신중 하 게 검토를 수행 하 고 Contoso의 가장 중요 한 데이터를 보호 하는 기능을 제공 하는 Microsoft 클라우드를 결정 하는데 사용 된 세 수준을 결정 합니다.
    
3. 데이터 수준에 대 한 액세스, 보존 및 정보 보호 정책 결정
    
    데이터 수준에 따라, Contoso는 클라우드로 이동 하는 향후 IT 작업을 사용 하는데 사용 되는 자세한 요구 사항을 결정 합니다.
    
## <a name="contosos-use-of-office-365-security-best-practices"></a>Contoso의 사용 하 여 Office 365 보안에 대 한 유용한 정보

Office 365 보안 모범 사례에 따라 Contoso의 보안 관리자 및 IT 부서 배포한 다음 합니다.
  
- **매우 강력한 암호를 가진 전역 관리자 계정 전용**
    
    대신 일상적인 사용자 계정에 전역 관리자 역할을 할당을 보다 Contoso는 만들기, 3 매우 강력한 암호를 가진 전역 관리자 계정 전용입니다. 특정 관리 작업에 대 한만 수행 되는 전역 관리자 계정을 사용 하 여 서명 하 고 암호는 지정 된 직원에 게만 알려져 있습니다. Contoso의 보안 관리자가 해당 IT 사용자의 작업 함수 및 책임에 적절 한 계정에 관리자 역할을 할당 합니다.
    
    자세한 내용은 [Office 365에 대 한 관리자 역할](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)을 참조 하십시오.
    
- **중요 한 사용자 계정에 대 한다 단계 인증 (MFA)**
    
    MFA는 사용자를 전화 통화, 텍스트 메시지 또는 올바르게 자신의 암호를 입력 한 후 스마트 전화기에서 전자 app 알림을 확인을 요구 하 여 로그인 프로세스에 추가 계층의 보호를 추가 합니다. MFA와 계정 암호가 손상 된 경우에 Office 365 사용자 계정 허가 되지 않은 로그인에 대해 보호 됩니다.
    
  - Office 365 구독의 손상을 보호 하기 위해 Contoso MFA 모든 세 전역 관리자 계정에 사용할 수 있습니다.
    
  - 공격자는 조직에서 신뢰할 수 있는 사용자의 자격 증명을 침해 및 악의적인 전자 메일을 보내는 피싱 공격 으로부터 보호 하기 위해 Contoso 임원 직원을 포함 하 여 관리자에 대 한 모든 사용자 계정에서 MFA을 사용 하도록 설정 합니다.
    
    자세한 내용은 [Office 365 배포에 대 한 다중 요소 인증에 대 한 계획](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba) 을 참조합니다
    
- **고급 보안 관리 (ASM)**
    
    ASM 사용 하 여 비정상적인 활동을 모니터링 하는 정책을 구성 합니다. IT 관리자는 많은 양의 데이터를 다운로드 하는 등의 비정상적인 또는 위험한 사용자 동작의 알림을 받을 수 있도록 ASM와 경고를 설정 하는 Contoso 보안 관리자가 다중이 로그인 시도 또는 알 수 없거나 위험한 IP 주소에서 로그인을 실패 했습니다.
    
    자세한 내용은 [개요 (영문)의 고급 보안 Office 365의에서 관리 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)를 참조 하십시오.
    
- **안전한 전자 메일 흐름 및 사서함 감사 로깅**
    
    Contoso 보안 전문가 Exchange Online Protection 및 고급 위협 보호 ATP ()를 사용 하 여 알 수 없는 맬웨어, 바이러스 및 전자 메일을 통해 전송 되는 악성 Url 보호 하기 위해 됩니다. Contoso에 활성화 된 사서함 감사 메시지를 전송 하는 사용자 사서함 및 사서함 소유자, 위임된 된 사용자 또는 관리자에 의해 수행 되는 다른 작업에 로그인 사용자를 확인 하려면 로깅을 수도 있습니다.
    
    자세한 내용은 다음 항목을 참조하십시오. 
    
  - [Office 365 전자 메일 스팸 방지 보호 기능](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [안전한 첨부 파일 및 안전한 링크를 위한 Advanced Threat Protection](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [Office 365에서 사서함 감사 사용](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- **데이터 손실 방지 (DLP)**
    
    Contoso가의 중요 한 데이터를 식별 하 고 Exchange Online, SharePoint Online 및 OneDrive 사용자가 실수로 또는 의도적으로 데이터를 공유 하는 것을 방지 하기에 대 한 DLP 정책을 구성 합니다. 
    
    자세한 내용은 [데이터 손실 방지 정책 개요](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)를 참조하세요.
    
## <a name="see-also"></a>참고 항목

[Microsoft 클라우드의 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 클라우드 IT 아키텍처 리소스](microsoft-cloud-it-architecture-resources.md)

[Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스](https://sway.com/FJ2xsyWtkJc2taRD)
  
[Office 365에 대한 보안 모범 사례](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




