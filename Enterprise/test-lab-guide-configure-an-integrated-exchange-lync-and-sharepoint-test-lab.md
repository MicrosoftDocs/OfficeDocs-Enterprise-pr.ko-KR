---
title: 테스트 랩 가이드 통합 된 Exchange, Lync 및 SharePoint 테스트 랩 구성
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
f1.keywords:
- NOCSH
description: '요약: Exchange Server 2013, Lync Server 2013를 실행 하는 서버 및 SharePoint Server 2013를 실행 하는 서버를 실행 하는 서버가 포함 된 통합 테스트 랩을 만드는 방법을 알아봅니다.'
ms.openlocfilehash: bfb2e1be3b9bb401514e736d38a6f1a2944940f0
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996522"
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a>테스트 랩 가이드: 통합 된 Exchange, Lync 및 SharePoint 테스트 랩 구성

 Exchange Server 2013, Lync Server 2013 실행 서버 및 SharePoint Server 2013을 실행 하는 서버를 실행 하는 서버가 포함 된 통합 테스트 랩을 만드는 방법을 알아봅니다.
 
**통합 된 Exchange, Lync 및 SharePoint 테스트 랩 가이드 개요 비디오 시청**

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=8d1f00cc-b8b1-4394-9367-0cc9765e380a&AutoPlayVideo=false]
 
이 구성에서 생성 되는 테스트 랩 (세 가지 서버 유형 간의 서버 간 인증 포함)은 Exchange Server 2013, Lync Server 2013 실행 서버 및 SharePoint Server 2013을 실행 하는 서버를 사용 하는 여러 제품 시나리오 및 솔루션을 구축 하 고 보여 주는 데 사용할 수 있습니다.
  
이 문서에는 다음에 대 한 지침이 포함 되어 있습니다.
  
1. Windows Server 2012 기본 구성 테스트 랩 구성
    
2. 새 서버(SQL1)를 설치 및 구성합니다.
    
3. SQL1 서버에 SQL Server 2012을 설치 합니다.
    
4. CLIENT2 이라는 새 클라이언트 컴퓨터를 설치 및 구성 합니다.
    
5. E X 1에서 Exchange Server 2013 설치 및 구성
    
6. LYNC1 라는 새 서버를 설치 하 고 구성 합니다.
    
7. LYNC1에 Lync Server 2013 Standard Edition을 설치 합니다.
    
8. SP1에 SharePoint Server 2013을 설치 합니다.
    
9. E X 1, LYNC1 및 SP1 간의 통합을 구성 합니다.
    
Hyper-v에서이 테스트 랩을 구성 하는 방법에 대 한 자세한 내용은 [Windows Server 2012 hyper-v를 사용 하 여 통합 된 Exchange, Lync 및 SharePoint 테스트 랩 호스팅을](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx)참조 하십시오.
  
## <a name="download-the-test-lab-guide"></a>테스트 랩 가이드 다운로드

[테스트 랩 가이드: 통합 Exchange, Lync 및 SharePoint 테스트 랩 구성](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)
  
## <a name="see-also"></a>참고 항목

[테스트 랩 가이드](https://go.microsoft.com/fwlink/p/?LinkId=202817)




