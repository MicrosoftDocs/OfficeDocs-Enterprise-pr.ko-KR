---
title: Office 365용 타사 SSL 인증서 계획
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.date: 05/15/2019
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: '요약: AD FS, Exchange Online 서비스 및 Exchange 웹 서비스를 사용 하는 Exchange 온-프레미스 및 하이브리드, SSO에 필요한 SSL 인증서에 대해 설명 합니다.'
ms.openlocfilehash: a28acae142f97a52f7c6db8e5a7d93049b2876cc
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841735"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Office 365용 타사 SSL 인증서 계획

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

클라이언트와 Office 365 환경 간의 통신을 암호화 하려면 인프라 서버에 타사 SSL (Secure sockets Layer) 인증서가 설치 되어 있어야 합니다.

||
|:-----|
| 이 문서는 [Office 365의 네트워크 계획 및 성능 조정](https://aka.ms/tune)의 일부입니다.|
   
다음 Office 365 구성 요소에 대 한 인증서가 필요 합니다.
  
- Exchange 온-프레미스
    
- SSO (Active Directory Federation Services) 페더레이션 서버 및 AD FS 페더레이션 서버 프록시 모두에 사용 됩니다.
    
- 자동 검색, 외부에서 Outlook 사용, Exchange 웹 서비스 등의 exchange Online 서비스
    
- Exchange 하이브리드 서버
    
## <a name="certificates-for-exchange-on-premises"></a>Exchange 온-프레미스 용 인증서

디지털 인증서를 사용 하 여 온-프레미스 Exchange 조직과 Exchange Online 보안 간의 통신을 수행 하는 방법에 대 한 개요는 [인증서 요구 사항 이해](https://go.microsoft.com/fwlink/p/?LinkID=243657)TechNet 문서를 참조 하십시오.
  
## <a name="certificates-for-single-sign-on"></a>Single Sign-on 용 인증서

강력한 보안이 포함 된 단순한 single sign-on 환경을 사용자에 게 제공 하기 위해 페더레이션 서버 또는 페더레이션 서버 프록시에 다음 표에 나와 있는 인증서가 필요 합니다. 아래 표에서는 AD FS (Active Directory Federation Services)에 대해 설명 하며 타사 [id 공급자를 사용 하](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility)는 방법에 대 한 자세한 내용도 제공 합니다.
  
||||
|:-----|:-----|:-----|
|**인증서 유형** <br/> |**설명** <br/> |**배포 하기 전에 알아야 할 사항** <br/> |
|**SSL 인증서 (서버 인증 인증서 라고도 함)** <br/> |페더레이션 서버, 클라이언트 및 페더레이션 서버 프록시 컴퓨터 간의 통신을 보호 하는 데 사용 되는 표준 SSL 인증서입니다.  <br/> |AD FS에 SSL 인증서가 필요 합니다. 기본적으로 AD FS는 IIS (인터넷 정보 서비스)의 기본 웹 사이트에 대해 구성 된 SSL 인증서를 사용 합니다.  <br/> 이 SSL 인증서의 주체 이름은 배포 하는 각 AD FS 인스턴스에 대 한 FS (페더레이션 서비스) 이름을 확인 하는 데 사용 됩니다. 회사 또는 조직의 이름을 Office 365에서 가장 잘 나타내는 새 CA (인증 기관) 인증서의 주체 이름을 선택 하는 것이 좋습니다. 이 이름은 인터넷 경로를 지정할 수 있어야 합니다.  <br/>**주의:** AD FS를 사용 하려면이 SSL 인증서에 점 없는 (약식 이름) 주체 이름이 없어야 합니다.          <br/> **권장 사항:** 이 인증서는 AD FS의 클라이언트에서 신뢰할 수 있어야 하므로 공용 (타사) CA 또는 공개적으로 신뢰할 수 있는 루트의 하위 CA에서 발급 한 SSL 인증서를 사용 하는 것이 좋습니다. 예를 들어 VeriSign 또는 Thawte를 들 있습니다.  <br/> |
|**토큰 서명 인증서** <br/> |페더레이션 서버에서 발급 하는 모든 토큰에 안전 하 게 서명을 하는 데 사용 되 고, Office 365에서 수락 하 고 유효성을 검사 하는 표준 x.509 인증서입니다.  <br/> |토큰 서명 인증서에는 FS의 신뢰할 수 있는 루트에 연결 되는 개인 키가 포함 되어야 합니다. 기본적으로 AD FS는 자체 서명 된 인증서를 만듭니다. 그러나 조직의 요구 사항에 따라 AD FS 관리 스냅인을 사용 하 여이 인증서를 CA 발급 인증서로 변경할 수 있습니다.  <br/>**주의:** 토큰 서명 인증서는 ADFS 안정성에 중요 합니다. 인증서가 변경 되 면 변경 내용을 Office 365에 알려야 합니다. 알림이 제공 되지 않으면 사용자가 Office 365 서비스 제품에 로그인 할 수 없습니다.<br/>**권장 사항:** AD FS에서 생성 된 자체 서명 된 토큰 서명 인증서를 사용 하는 것이 좋습니다. 이렇게 하면 기본적으로이 인증서가 관리 됩니다. 예를 들어이 인증서가 만료 되려고 하면 AD FS는 자체 서명 된 새 인증서를 생성 합니다.  <br/> |
   
페더레이션 서버 프록시에는 다음 표에 설명 된 인증서가 필요 합니다.
  
||||
|:-----|:-----|:-----|
|**인증서 유형** <br/> |**설명** <br/> |**배포 하기 전에 알아야 할 사항** <br/> |
|SSL 인증서  <br/> |페더레이션 서버, 페더레이션 서버 프록시 및 인터넷 클라이언트 컴퓨터 간의 통신을 보호 하는 데 사용 되는 표준 SSL 인증서입니다.  <br/> |AD FS 페더레이션 서버 프록시 구성 마법사를 성공적으로 실행 하려면 먼저이 SSL 인증서를 IIS의 기본 웹 사이트에 바인딩해야 합니다.  <br/> 이 인증서의 주체 이름은 회사 네트워크의 페더레이션 서버에 구성 된 SSL 인증서와 동일 해야 합니다.  <br/> **권장 사항:** 이 페더레이션 서버 프록시가 연결 되는 페더레이션 서버에 대해 구성 된 것과 동일한 서버 인증 인증서를 사용 하는 것이 좋습니다.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>자동 검색, 외부에서 Outlook 사용 및 Active Directory 동기화를 위한 인증서

외부 연결 Exchange 2013, Exchange 2010, Exchange 2007 및 Exchange 2003 클라이언트 액세스 서버 (CASs)에는 자동 검색, 외부에서 Outlook 사용 및 Active Directory 동기화 서비스를 위한 보안 연결을 위한 타사 SSL 인증서가 필요 합니다. 이 인증서가 온-프레미스 환경에 이미 설치 되어 있을 수 있습니다.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Exchange 하이브리드 서버용 인증서

외부 연결 Exchange 하이브리드 서버에는 Exchange Online 서비스와의 보안 연결용 타사 SSL 인증서가 필요 합니다. 타사 SSL 공급자에서이 인증서를 받아야 합니다.
  
## <a name="office-365-certificate-chains"></a>Office 365 인증서 체인

이 문서에서는 인프라에 설치 해야 할 수 있는 인증서에 대해 설명 합니다. Office 365 서버에 설치 된 인증서에 대 한 자세한 내용은 [office 365 인증서 체인](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)을 참조 하십시오.
  
## <a name="see-also"></a>참고 항목

[Microsoft 365 Enterprise 개요](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
