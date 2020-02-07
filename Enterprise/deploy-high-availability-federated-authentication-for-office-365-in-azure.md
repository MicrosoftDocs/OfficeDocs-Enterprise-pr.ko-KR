---
title: Azure에서 Office 365용 고가용성 페더레이션 인증 배포
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: '요약: Microsoft Azure에서 Office 365 구독에 대한 고가용성 페더레이션 인증을 구성합니다.'
ms.openlocfilehash: af73f75b7ac1e3151ddb5c55acdf49a48f784e95
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840525"
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a>Azure에서 Office 365용 고가용성 페더레이션 인증 배포

이 문서에는 다음과 같은 가상 컴퓨터를 사용하여 Azure 인프라 서비스에서 Microsoft Office 365에 대한 고가용성 페더레이션 인증을 배포하기 위한 단계별 지침 관련 링크가 포함되어 있습니다.
  
- 웹 응용 프로그램 프록시 서버 2개
    
- AD FS(Active Directory Federation Services) 서버 2개
    
- 복제본 도메인 컨트롤러 2개
    
- Azure AD Connect를 실행하는 디렉터리 동기화 서버 1개
    
다음은 각 서버에 대해 자리 표시자 이름이 사용된 구성입니다.
  
**Azure에서 Office 365 인프라용 고가용성 페더레이션 인증**

![Azure에서 고가용성 Office 365 페더레이션 인증 인프라의 최종 구성.](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
모든 가상 컴퓨터는 단일 프레미스 간 Azure VNet(가상 네트워크)에 있습니다. 
  
> [!NOTE]
> 개별 사용자의 페더레이션 인증은 온-프레미스 리소스를 사용하지 않습니다. 그러나 프레미스 간 연결을 사용할 수 없게 되는 경우 VNet의 도메인 컨트롤러가 온-프레미스 Active Directory Domain Services(AD DS)에서 만든 사용자 계정 및 그룹에 대한 업데이트를 받을 수 없게 됩니다. 이 문제가 발생하지 않도록 하려면 프레미스 간 연결을 위한 고가용성을 구성하면 됩니다. 자세한 내용은 [항상 사용 가능한 프레미스 간 및 VNet 간 연결](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)을 참조하세요.
  
특정 역할에 대한 각 쌍의 가상 컴퓨터는 자체 서브넷 및 가용성 집합에 포함됩니다.
  
> [!NOTE]
> 이 VNet이 온-프레미스 네트워크에 연결되어 있으므로 이 구성에는 jumpbox 또는 관리 서브넷의 가상 컴퓨터 모니터링이 포함되지 않습니다. 자세한 내용은 [N 계층 아키텍처에 대해 Windows VM 실행](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm)을 참조하세요. 
  
이 구성을 완료하면 모든 Office 365 사용자에 대한 페더레이션 인증을 가지게 됩니다. 즉, 사용자가 Office 365 계정 대신 자신의 AD DS 자격 증명을 사용하여 로그인할 수 있습니다. 페더레이션 인증 인프라는 온-프레미스 경계 네트워크 대신 Azure 인프라 서비스에 더욱 쉽게 배포되는 중복 서버 집합을 사용합니다.
  
## <a name="bill-of-materials"></a>제품 구성 정보(BOM)

이 기본 구성에는 다음과 같은 Azure 서비스 및 구성 요소 집합이 필요합니다.
  
- 가상 컴퓨터 7개
    
- 4개의 서브넷이 있는 프레미스 간 가상 네트워크 1개
    
- 리소스 그룹 4개
    
- 가용성 집합 3개
    
- Azure 구독 1개
    
다음은 이 구성의 가상 컴퓨터 및 해당 기본 크기입니다.
  
|**항목**|**가상 컴퓨터 설명**|**Azure 갤러리 이미지**|**기본 크기**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |첫 번째 도메인 컨트롤러  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|2.  <br/> |두 번째 도메인 컨트롤러  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|3.  <br/> |Azure AD Connect 서버  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|4.  <br/> |첫 번째 AD FS 서버  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|5.  <br/> |두 번째 AD FS 서버  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|6.  <br/> |첫 번째 웹 응용 프로그램 프록시 서버  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|7.  <br/> |두 번째 웹 응용 프로그램 프록시 서버  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
   
이러한 구성에 대한 예상 비용을 계산하려면 [Azure 가격 계산기](https://azure.microsoft.com/pricing/calculator/)를 참조하세요.
  
## <a name="phases-of-deployment"></a>배포 단계

이 작업은 다음과 같은 단계로 배포됩니다.
  
- [1단계: Azure 구성](high-availability-federated-authentication-phase-1-configure-azure.md). 리소스 그룹, 저장소 계정, 가용성 집합 및 프레미스 간 가상 네트워크를 만듭니다.
    
- [2단계: 도메인 컨트롤러 구성](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) 복제본 AD DS 도메인 컨트롤러를 디렉터리 동기화 서버를 만들고 구성합니다.
    
- [3단계: AD FS 서버 구성](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). 2개의 AD FS 서버를 만들고 구성합니다.
    
- [4단계: 웹 응용 프로그램 프록시 구성](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). 2개의 웹 응용 프로그램 프록시 서버를 만들고 구성합니다.
    
- [5단계: Office 365용 페더레이션 인증 구성](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Office 365 구독에 대한 페더레이션 인증을 구성합니다.
    
이러한 문서에서는 Azure 인프라 서비스의 Office 365용 고가용성 페더레이션 인증 기능을 만들기 위해 미리 정의된 아키텍처에 대한 단계별 규범 지침을 제공합니다. 다음 사항에 유의해야 합니다.
  
- 숙련된 AD FS 구현자인 경우 3~4단계의 지침을 적용하고 본인의 요구에 가장 적합한 서버 집합을 구축합니다.
    
- 기존 프레미스 간 가상 네트워크와 함께 기존 Azure 하이브리드 클라우드 배포가 이미 있는 경우에는 1-2단계의 지침을 적용하거나 건너뛰고, 적절한 서브넷에 AD FS 및 웹 응용 프로그램 프록시 서버를 배치합니다.
    
개발/테스트 환경 또는 이 구성의 개념 증명을 구축하려면 [Office 365 개발/테스트 환경에 대 한 페더레이션된 id](federated-identity-for-your-office-365-dev-test-environment.md)를 참조하세요.
  
## <a name="next-step"></a>다음 단계

[1단계: Azure 구성](high-availability-federated-authentication-phase-1-configure-azure.md)으로 이 작업의 구성을 시작합니다. 
  
