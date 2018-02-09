---
title: "SharePoint Server 2013을 사용 하 여 Microsoft Azure의 인터넷 사이트"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: "요약: SharePoint Server 2013을 사용 하는 인터넷 사이트 Azure 인프라 서비스에서 호스트 되 여 활용 합니다. 이 문서에서는 디자인 하 고이 솔루션을 구현 하기 위한 리소스를 제공 합니다."
ms.openlocfilehash: 44bf53477c502c89dfae32abf59e1ac0c3120f8e
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>SharePoint Server 2013을 사용 하 여 Microsoft Azure의 인터넷 사이트

 **요약:** SharePoint Server 2013을 사용 하는 인터넷 사이트 Azure 인프라 서비스에서 호스트 되 여 활용 합니다. 이 문서에서는 디자인 하 고이 솔루션을 구현 하기 위한 리소스를 제공 합니다.
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a>인터넷 사이트를 위한 Azure 인프라 서비스를 사용 하 여

Microsoft Azure SharePoint Server 2013에 따라 인터넷 사이트를 호스팅하기 위한 주목할 옵션을 제공 합니다. 장점은 다음과 같습니다.
  
- 인프라를 구축 하는 대신 뛰어난 사이트의 개발에 초점을 맞춥니다.
    
- 유연성에 및 조정 하 여 필요에 따라 기반 솔루션을 확장 합니다.
    
- 필요 하 고 사용 되는 리소스에 대해서만 지불 합니다.
    
- Azure Active Directory 사용자 계정에 대 한을 활용 합니다.
    
- 상세 보고 및 분석 예: Office 365에서 현재 사용할 수 없는 기능을 추가 합니다.
    
## <a name="resources"></a>리소스

기술에 대 한 다음 그림 및 문서를 디자인 하 고 SharePoint Server 2013을 사용 하 여 Azure의 인터넷 사이트를 구현 하는 방법에 대 한 정보를 제공 합니다.
  
|**리소스**|**자세한 내용**|
|:-----|:-----|
|**Azure의 SharePoint Server 2013 인터넷 사이트** <br/> [![SharePoint를 사용 하 여 Azure의 인터넷 사이트의 이미지](images/MS_AZ_SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552) <br/> ![PDF 파일](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552) \| [ ![Visio 파일](images/ITPro_Other_VisioIcon.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)   <br/> |주요 디자인 활동을 간략하게 소개 하 고 Azure의 인터넷 사이트에 대 한 선택 하려는 아키텍처를 권장 하는이 아키텍처 모델입니다.  <br/> |
|**이 디자인 예제: SharePoint Server 2013에 대 한 Azure의 인터넷 사이트** <br/> [![이 디자인 예제 이미지: SharePoint 2013에 대 한 Microsoft Azure의 인터넷 사이트](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549) <br/> ![PDF 파일](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549) \| ![Visio 파일](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)   <br/> |시작 지점으로이 디자인 예제를 사용 하 여 자신의 아키텍처에 대 한.  <br/> |
|**[SharePoint 2013에 대 한 Microsoft Azure 아키텍처](microsoft-azure-architectures-for-sharepoint-2013.md)** <br/> |이 문서에서는 호스트 SharePoint 솔루션을 Azure 아키텍처를 디자인 하는 방법에 설명 합니다.  <br/> |
|**[SharePoint 2013 인증에 대 한 Microsoft Azure Active Directory를 사용 하 여](using-microsoft-azure-active-directory-for-sharepoint-2013-authentication.md)** <br/> |SharePoint 2013 팜에서 Azure AD를 구성 하기 위한 단계별 지침입니다.  <br/> |
   
**토론에 참가**

|**문의처**|**설명**|
|:-----|:-----|
|**클라우드 채택 콘텐츠 합니까 필요 합니까?** <br/> |여러 Microsoft 클라우드 플랫폼 및 서비스에 걸쳐 있는 클라우드 채택에 대 한 콘텐츠를 만듭니다. 보겠습니다 작업을 알 사용해 클라우드 채택 콘텐츠를 구상할 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)에 전자 메일을 발송 하 여 특정 콘텐츠를 요청 합니다.<br/> |
|**클라우드 채택 토론에 참가** <br/> |클라우드 기반 솔루션에 열정을 갖고 인 경우에는 클라우드 채택 자문 보드 (CAAB) Microsoft 콘텐츠 개발자, 업계 전문가는 전세계 어디에서 고객의 더 큰, 생생한 커뮤니티와 연결할에 참가 하는 것이 좋습니다. 참가, Microsoft 기술 커뮤니티의 [CAAB (클라우드 채택 자문 위원회) 공간](https://aka.ms/caab) 의 구성원으로 자신을 추가 하 고[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)에서 빠른 전자 메일을 보내주시기 합니다. 누구나 [CAAB 블로그 (영문)](https://blogs.technet.com/b/solutions_advisory_board/)에서 커뮤니티 관련 콘텐츠를 읽을 수 있습니다. 그러나 CAAB 구성원에 게 새 클라우드 채택 리소스 및 솔루션에 설명 하는 개인 웨 초대장을 가져옵니다.<br/> |
|**여기에서 참조 하 여 아트 가져오기** <br/> |이 문서에서 참조 하는 이미지의 편집 가능한 복사본을 원하는 귀하에 게 보내야 기꺼이 표시 됩니다. URL 및 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)는 이미지의 제목을 포함 하 여 요청을 전자 메일로 보냅니다.<br/> |
   
## <a name="see-also"></a>참고 항목

[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)



