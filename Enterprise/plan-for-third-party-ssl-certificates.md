---
title: Office 365용 타사 SSL 인증서 계획
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: '요약: AD FS, Exchange Online 서비스 및 Exchange 웹 서비스를 사용하는 Exchange 온-프레미스 및 하이브리드와 SSO에 필요한 SSL 인증서를 설명합니다.'
ms.openlocfilehash: 5092734c66f39583d32d4cd9f926e76ed794668b
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223020"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Office 365용 타사 SSL 인증서 계획

 **요약:** Exchange 온-프레미스 및 하이브리드, AD FS를 사용 하 여 SSO에 필요한 SSL 인증서를 설명 Exchange Online 서비스 및 Exchange 웹 서비스. 
  
클라이언트와 theOffice 365Office 365 환경 간의 통신을 암호화 하려면 인프라 서버에 타사 Secure Socket Layer (SSL) 인증서를 설치 해야 합니다.

||
|:-----|
| 이 문서는 [네트워크 계획 및 Office 365에 대 한 성능 조정](https://aka.ms/tune)의 일부입니다.|
   
인증서가 필요한 Office 365 구성 요소는 다음과 같습니다.
  
- Exchange 온-프레미스
    
- SSO(Single Sign-On). AD FS(Active Directory Federation Services) 페더레이션 서버 및 AD FS 페더레이션 서버 프록시에 모두 필요합니다.
    
- 자동 검색, 외부에서 Outlook 사용, 및 Exchange 웹 서비스 등의 Exchange Online 서비스
    
- Exchange 혼성 서버
    
## <a name="certificates-for-exchange-on-premises"></a>Exchange 온-프레미스용 인증서

디지털 인증서를 사용 하는 온-프레미스 Exchange 조직과 Exchange Online 간의 통신을 안전 하 게를 [인증서 요구 사항 이해](https://go.microsoft.com/fwlink/p/?LinkID=243657)TechNet 문서를 참조 하는 방법에 대 한 개요입니다.
  
## <a name="certificates-for-single-sign-on"></a>Single Sign-On용 인증서

단순한 single sign on 환경을 강력한 보안이 포함 된 사용자에 게을 제공 하려면 다음 표에 표시 된 인증서는 페더레이션 서버 또는 페더레이션 서버 프록시에 필요 합니다. 아래 표에 Active Directory Federation Services (AD FS)에 중점을 두고, 것 권한도 부여 [타사 id 공급자를 사용 하 여](https://go.microsoft.com/fwlink/?LinkId=532869)대 한 자세한 내용은 합니다.
  
||||
|:-----|:-----|:-----|
|**인증서 유형** <br/> |**설명** <br/> |**배포하기 전에 알아야 할 내용** <br/> |
|**SSL 인증서(서버 인증 인증서라고도 함)** <br/> |페더레이션 서버, 클라이언트 및 페더레이션 서버 프록시 컴퓨터 간의 통신을 보호하는 데 사용되는 표준 SSL 인증서입니다.  <br/> |AD FS에는 SSL 인증서가 필요합니다. 기본적으로 AD FS 기본 웹사이트에서 인터넷 정보 서비스 (IIS)에 대해 구성 된 SSL 인증서를 사용 합니다.<br/> 이 SSL 인증서의 주체 이름은 배포 하는 AD FS의 각 인스턴스에 대 한 페더레이션 서비스 (FS) 이름을 결정 하는데 사용 됩니다. 모든 새 CA (인증 기관)에 대 한 주체 이름을 선택 하는 것이 좋습니다.-최고 회사 또는 조직의 Office 365로의 이름을 나타내는 인증서를 발급 합니다. 이 이름은 인터넷 라우팅 가능 해야 합니다.<br/>**주의:** AD FS 하려면 점 없는 (약식 이름) 주체 이름이 SSL 인증서에 있어야 합니다.          </br> **권장 사항:** AD FS의 클라이언트에서이 인증서를 신뢰 해야, 때문에 공용 (타사) CA에서 또는 공개적으로 신뢰할 수 있는 루트;에 종속 되는 CA에서 발급 한 SSL 인증서를 사용 하는 것이 좋습니다. VeriSign, Thawte 등의 예입니다.  <br/> |
|**토큰 서명 인증서** <br/> |페더레이션 서버에서 발급 하며 해당 Office 365를 허용 하 고 유효성을 검사 하는 모든 토큰의 보안 서명에 사용 되는 표준 X.509 인증서입니다.  <br/> |토큰 서명 인증서는 FS에서 신뢰할 수 있는 루트에 연결 하는 개인 키를 포함 해야 합니다. 기본적으로 AD FS에는 자체 서명 된 인증서를 만듭니다. 그러나 조직의 필요에 따라 변경할 수 있습니다이 인증서를 CA에서 발급 한 인증서를 AD FS 관리 스냅인을 사용 하 여.<br/>**주의:** 토큰 서명 인증서가는 FS의 안정성과 중요 합니다. 인증서를 변경 하는 경우 Office 365 변경 알려야 합니다. 알림이 제공 되지 않은 경우 사용자가 Office 365 서비스 제품을 로그인 수는 없습니다.</br>**권장 사항:** AD FS에서 생성 되는 자체 서명 된 토큰 서명 인증서를 사용 하는 것이 좋습니다. 이렇게 하 여 관리이 인증서 하면 기본적으로 합니다. 예,이 인증서가 만료 바로, AD FS 새로운 자체 서명 된 인증서를이 생성 됩니다.<br/> |
   
페더레이션 서버 프록시의 경우 다음 표에서 설명하는 인증서가 필요합니다.
  
||||
|:-----|:-----|:-----|
|**인증서 유형** <br/> |**설명** <br/> |**배포하기 전에 알아야 할 내용** <br/> |
|SSL 인증서  <br/> |페더레이션 서버, 페더레이션 서버 프록시 및 인터넷 클라이언트 컴퓨터 간의 통신을 보호하는 데 사용되는 표준 SSL 인증서입니다.  <br/> |이 SSL 인증서를 성공적으로 AD FS 페더레이션 서버 프록시 구성 마법사를 실행 하기 전에 IIS의 기본 웹사이트에 바인딩해야 합니다.  <br/> 이 인증서의 주체 이름은 회사 네트워크의 페더레이션 서버에 대해 구성된 SSL 인증서의 주체 이름과 같아야 합니다.  <br/> **권장 사항:** 이 페더레이션 서버 프록시가 연결되는 페더레이션 서버에 대해 구성된 것과 같은 서버 인증 인증서를 사용하는 것이 좋습니다.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>자동 검색, 외부에서 Outlook 사용 및 Active Directory 동기화에 대 한 인증서

외부 연결 Exchange 2013, Exchange 2010, Exchange 2007 및 Exchange 2003 클라이언트 액세스 서버 (클래스) 자동 검색, 외부에서 Outlook 사용, 및 Active Directory 동기화 서비스에 대 한 보안 연결에 대 한 타사 SSL 인증서가 필요 합니다. 온-프레미스 환경에 설치 된이 인증서를 이미 있을 수도 있습니다.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Exchange 하이브리드 서버용 인증서

외부 연결 Exchange 하이브리드 서버 또는 서버 타사 SSL 인증서를 Exchange Online 서비스와의 보안 연결에 필요합니다. 타사 SSL 공급자에서이 인증서를 가져오려면 해야 합니다.
  
## <a name="office-365-certificate-chains"></a>Office 365 인증서 체인

이 문서는 인프라에 설치 해야할 수 인증서를 설명 합니다. 이 Office 365 서버에 설치 된 인증서에 대 한 자세한 내용은 [Office 365 인증서 체인](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)을 참조 하십시오.
  

