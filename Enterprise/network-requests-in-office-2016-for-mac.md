---
title: Mac용 Office 2016의 네트워크 요청
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Mac 응용 프로그램에 대 한 office 2016 macOS 플랫폼에서 네이티브 app 경험을 제공 합니다. 각 응용 프로그램은 다양 한 네트워크 액세스 금지 사용할 수 있는 경우에 상태를 포함 하 여 시나리오에서에서 작동 하도록 설계 되었습니다. 컴퓨터 네트워크와 연결 된 경우 응용 프로그램은 자동으로 일련의 향상 된 기능을 제공 하도록 웹 기반 서비스에 연결 합니다. 이 백서에는 끝점 및 응용 프로그램을 연결을 시도 하는 Url 및 제공 하는 서비스에 설명 합니다. 이 정보는 문제를 해결 네트워크 구성 문제 및 네트워크 프록시 서버에 대 한 정책을 설정 하는 경우에 유용 합니다. 이 문서에서 세부 정보는 Office 365 URL 및 주소 범위 문서를 보완 하기 위한 것입니다.
ms.openlocfilehash: b94b77a0ff8cd37b0fa1c881ba590853615bfe93
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542163"
---
# <a name="network-requests-in-office-2016-for-mac"></a>Mac용 Office 2016의 네트워크 요청

Mac 응용 프로그램에 대 한 office 2016 macOS 플랫폼에서 네이티브 app 경험을 제공 합니다. 각 응용 프로그램은 다양 한 네트워크 액세스 금지 사용할 수 있는 경우에 상태를 포함 하 여 시나리오에서에서 작동 하도록 설계 되었습니다. 컴퓨터 네트워크와 연결 된 경우 응용 프로그램은 자동으로 일련의 향상 된 기능을 제공 하도록 웹 기반 서비스에 연결 합니다. 이 백서에는 끝점 및 응용 프로그램을 연결을 시도 하는 Url 및 제공 하는 서비스에 설명 합니다. 이 정보는 네트워크 프록시 서버에 대 한 정책 설정 및 네트워크 구성 문제를 해결할 때 유용 합니다. 이 문서에서 세부 정보는 [Office 365 URL 및 주소 범위 문서](urls-and-ip-address-ranges.md), Microsoft Windows를 실행 하는 컴퓨터에 대 한 끝점을 포함 하는 보완 하기 위한 것입니다.
  
이 문서는 대부분은 네트워크 Url, 형식 및 설명 서비스 또는 해당 끝점에서 제공 하는 기능을 자세히 설명 하는 테이블입니다. 각 Office 응용 프로그램의 해당 서비스 및 끝점 사용법에 다를 수 있습니다. 다음 응용 프로그램은 아래 표에 정의 됩니다.
  
- W: Word
- P: PowerPoint
- X: Excel
- O: outlook
- N: OneNote
   
URL 형식은 다음과 같이 정의 됩니다.
  
- ST: 클라이언트 응용 프로그램으로 하드 코드 된 정적-URL입니다.
    
- SS: 세미콜론 정적-URL은 웹 페이지 또는 리디렉터의 일부분으로 인코딩됩니다.
    
- CS: Config 서비스-URL이 포함 된 Office 구성 서비스의 일부로
    
## <a name="office-2016-for-mac-default-configuration"></a>Mac 기본 구성에 대 한 office 2016

 **설치 및 업데이트**
  
다음 네트워크 끝점은 Mac 설치 프로그램에 대 한 Office 2016 Microsoft 콘텐츠 배달 네트워크 (CDN)에서 다운로드 하는데 사용 됩니다.
  
|**URL**|**종류**|**설명**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Office 365 설치 포털 앞으로 최신 설치 패키지에 서비스를 연결 합니다.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |콘텐츠 배달 네트워크에 있는 설치 패키지의 위치입니다.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |콘텐츠 배달 네트워크에 있는 설치 패키지의 위치입니다.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |Microsoft 자동 업데이트에 대 한 관리 제어 끝점  <br/> |
   
 **첫번째 응용 프로그램 실행**
  
다음 네트워크 끝점에 게는 Office 응용 프로그램의 첫번째 실행에 연결 합니다. 이러한 끝점을 사용자에 대 한 향상 된 Office 기능을 제공 하 고 Url 라이선스 유형 (볼륨 라이선스 설치 포함)에 관계 없이 연결 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' 구성-기능 빛 수직 확장 토폴로지와 실험을 허용 합니다.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' 네트워크 구성 테스트  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' 네트워크 구성 테스트  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 구성 서비스-서비스 끝점 목록을 마스터입니다.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 원격 분석 규칙 다운로드-어떤 데이터와 원격 분석 서비스에 업로드 하는 이벤트에 대 한 클라이언트를 알립니다.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |OneNote 원격 분석 서비스  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 원격 분석 보고-"Heartbeart"를 업로드 하 고 원격 분석 서비스에 업로드 되는 클라이언트에서 발생 하는 오류 이벤트입니다.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office Online 서식 파일 서비스-온라인 문서 서식 파일 사용자에 게 제공 합니다.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Office 서식 파일 다운로드-PNG 서식 파일 이미지를 저장 합니다.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office 응용 프로그램에 대 한 구성을 저장 합니다.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office 문서 Integration Services 카탈로그 (서비스 및 끝점의 목록) 및 홈 영역 검색 합니다.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |홈 영역 검색 v2 (15.40 및 이상)에 대 한 리소스  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft AutoUpdate 매니페스트-사용할 수 있는 업데이트가 있는지 확인 합니다.  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Microsoft Ajax JavaScript 라이브러리  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Office 구성 및 리소스에 대 한 위키피디아 앱입니다.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Office 구성 및 리소스에 대 한 Bing 지도 앱입니다.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |사람들이 Office 구성 및 리소스에 대 한 응용 프로그램을 그래프입니다.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |OneNote에 대 한 새 콘텐츠 란 합니다.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |OneNote에 대 한 새 콘텐츠가 포함 되었습니다.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |OneNote에 대 한 새로운 이미지 이란 합니다.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |서비스 응용 프로그램에서 지원 합니다.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |전자 메일 계정 검색 서비스입니다.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook 자동 검색  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Office 365 서비스에 대 한 outlook 끝점입니다.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Outlook 추가 기능에 대 한 아이콘입니다.  <br/> |
   
> [!NOTE]
> Office 구성 서비스 역할 자동 검색 서비스를 모든 Microsoft Office 클라이언트에 대 한, 뿐아니라 for mac입니다. 에 대 한 응답으로 반환 하는 끝점 '는 준 정적 매우 빈번 하지는 않지만 여전히 가능한 변경 됩니다. 
  
 **로그인**
  
클라우드 기반 저장소에 로그인 할 때 다음 네트워크 끝점 연결 됩니다. 사용자 계정 유형에 따라 다른 서비스에 연결할 수 있습니다. 예를 들어:
  
- **MSA: Microsoft 계정** -소비자 및 소매 시나리오에 대 한 일반적으로 사용 
    
- **OrgID: 조직 계정** -상업용 시나리오에 대 한 일반적으로 사용 
    
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Windows 권한 부여 서비스  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 365 로그인 서비스 (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft 계정 로그인 서비스 (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Microsoft 계정 로그인 서비스 도우미 (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Office 365 로그인 (OrgID) 브랜딩 (영문)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |문서 및 위치 저장소 로케이터  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |대부분 MRU (최근에 사용한) 문서 서비스  <br/> |
   
> [!NOTE]
> 구독 기반 및 정품 라이선스에 대 한 모두에 서명 하 고 활성화 하는 제품 및 OneDrive 같은 클라우드 리소스에 액세스할 수 있도록 합니다. 볼륨 라이선스 설치의 경우 사용자는 여전히 하 라는 메시지가 로그인 (기본적으로) 있지만 이것은 제품이 이미 활성화 된 클라우드 리소스에 액세스 하기 위해 필요 합니다. 
  
 **제품 정품 인증**
  
다음 네트워크 끝점 소매 라이선스 및 Office 365 구독 정품 인증에 적용 됩니다. 특히이 적용 되지 않습니다 볼륨 라이선스 설치에.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Office Licensing Service  <br/> |
   
 **새 콘텐츠 란**
  
다음 네트워크 끝점을 사용 하는 Office 365 구독에만 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |새 JSON 페이지 콘텐츠 란 합니다.  <br/> |
   
 **리서치 도구**
  
다음 네트워크 끝점 모두 Office 365 구독에 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |연구원 웹 서비스  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |연구원 정적 콘텐츠  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |연구원 콘텐츠 공급자  <br/> |
   
 **스마트 조회**
  
다음 네트워크 끝점 모두 Office 365 구독 및 소매/볼륨 라이선스 정품 인증에 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |인 사이트 웹 서비스  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |JQuery 라이브러리  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |JavaScript 라이브러리를 지원합니다.  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |인 사이트 콘텐츠 공급자  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |인 사이트 콘텐츠 공급자  <br/> |
   
 **PowerPoint Designer**
  
다음 네트워크 끝점을 사용 하는 Office 365 구독에만 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint 디자이너 웹 서비스  <br/> |
   
 **PowerPoint 빠른 시작**
  
다음 네트워크 끝점을 사용 하는 Office 365 구독에만 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint QuickStarter 웹 서비스  <br/> |
   
 **Smile/찡그린 얼굴 보내기**
  
다음 네트워크 끝점 모두 Office 365 구독 및 소매/볼륨 라이선스 정품 인증에 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |Smile 서비스 보내기  <br/> |
   
 **고객 지원에 문의**
  
다음 네트워크 끝점 모두 Office 365 구독 및 소매/볼륨 라이선스 정품 인증에 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |지원 서비스에 문의  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |응용 프로그램에서 지원 서비스  <br/> |
   
 **PDF로 저장**
  
다음 네트워크 끝점 모두 Office 365 구독 및 소매/볼륨 라이선스 정품 인증에 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Word 문서 변환 서비스 (PDF)  <br/> |
   
 **Office 응용 프로그램 (명시적 추가 기능)**
  
다음 네트워크 끝점을 사용 하는 경우 Office 응용 프로그램 추가 기능에 신뢰할 수 있는 Office 365 구독 및 소매/볼륨 라이선스를 모두 정품 인증에 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Office 응용 프로그램 저장소 구성  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |위키피디아 app 리소스  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing 지도 앱 리소스  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |사람들이 그래프 app 리소스  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Office 리디렉션 서비스  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Office JavaScript 라이브러리  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |원격 분석 및 Office 응용 프로그램에 대 한 보고 서비스  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Microsoft Ajax JavaScript 라이브러리  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Microsoft Ajax JavaScript 라이브러리  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Office JavaScript 라이브러리  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |지원 리소스  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |지원 리소스  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |지원 리소스  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |JavaScript 라이브러리  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |오류 보고  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |글꼴 리소스  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |원격 분석 서비스  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |원격 분석 보고  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Microsoft 저장소 자산 라이브러리  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |위키피디아 페이지 리소스  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |위키피디아 미디어 리소스  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |위키피디아 샌드박스 프레임  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |지도 서식 파일  <br/> |
   
 **안전한 링크**
  
다음 네트워크 끝점 Office 2016 응용 프로그램에 적용 됩니다.
  
|**URL**|**종류**|**설명**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Microsoft 안전 하 게 보호 링크 서비스  <br/> |
   
 **보고 충돌**
  
다음 네트워크 끝점 모든 Office 2016 응용 프로그램 및 라이선스 종류에 적용 됩니다. 프로세스를 예기치 않게 충돌, 보고서가 생성 및 Watson 서비스에 전송 합니다.
  
|**URL**|**종류**|**설명**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Microsoft 오류 보고 서비스  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Office 공동 작업 정보 서비스  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>네트워크 요청 및 트래픽을 줄이기 위한 옵션

Mac 용 Office 2016의 기본 구성을 모두이 컴퓨터를 최신 상태로 유지 하 고 기능 면에서 최상의 사용자 경험을 제공 합니다. 일부 시나리오에서는 응용 프로그램이 네트워크 끝점에 연결 하지 못하도록 하는 것이 좋습니다. 이 섹션에서는 이러한 작업에 대 한 옵션에 설명 합니다.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>클라우드에 로그인 하 고 Office 추가 기능을 사용 하지 않도록 설정
  
볼륨 라이선스 고객 클라우드 기반 저장소에 문서를 저장 하는 방법에 대 한 엄격한 정책이 있을 수 있습니다. 다음 응용 프로그램 별로 기본 설정, MSA/OrgID 기호를 사용 하지 않도록 설정 하 고 Office 추가 기능에 대 한 액세스를 설정할 수 있습니다.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

사용자를 로그인 함수에 액세스 하려고 하는 경우이 매개 변수가 네트워크 연결이 없는 오류가 표시 됩니다. 이 기본 설정은 온라인 제품 정품 인증을 차단 하기 때문에 볼륨 라이선스 설치에 사용 해야 합니다. 특히이 기본 설정을 사용 하 여 다음 끝점에 액세스 하지 못하도록 Office 응용 프로그램 되지 것입니다.
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- 위의 ' 로그인 ' 않으려면 섹션에 나열 된 모든 끝점입니다.
    
- 위의 ' 스마트 조회 ' 섹션에 나열 된 모든 끝점입니다.
    
- 위의 ' 제품 정품 인증 ' 섹션에 나열 된 모든 끝점입니다.
    
- 위의 ' Office Apps (명시적 추가 기능)' 섹션에 나열 된 모든 끝점입니다.
    
'2'에 대 한 기본 설정을 설정 하거나 사용자에 대 한 전체 기능을 다시 설정 하려면 하거나 제거 합니다.
  
> [!NOTE]
> 이 기본 설정은 빌드 15.25 [160726] Mac 용 Office 2016 필요 이상입니다. 
  
### <a name="telemetry"></a>원격 분석
  
Mac 용 office 2016 정기적으로 Microsoft에 다시 원격 분석 정보를 보냅니다. 데이터 '원활한 연결' 끝점으로 업로드 됩니다. 원격 분석 데이터 상태 및 각 Office 응용 프로그램의 모든 예기치 않은 동작을 평가 엔지니어링 팀 도움이 됩니다. 원격 분석의 두 범주 가지가 있습니다.
  
- **하트 비트** 버전 및 라이선스 정보를 포함 합니다. 이 데이터는 응용 프로그램 시작 시 즉시 전송 됩니다. 
    
- **사용 현황** 응용 프로그램 사용 하는 방법에 대 한 정보 및 치명적이 지 않은 오류를 포함 합니다. 이 데이터는 60 분 마다 전송 됩니다. 
    
Microsoft는 개인을 매우 심각 하 게 수행합니다. Microsoft의 데이터 수집 정책에 대 한 읽을 수 있는 [https://privacy.microsoft.com](https://privacy.microsoft.com)합니다. 응용 프로그램에서 '사용 현황' 원격 분석을 보내지 않으려면 **SendAllTelemetryEnabled** 기본 설정을 조정할 수 있습니다. 기본 설정을 응용 프로그램당 이며 macOS 구성 프로필을 통해 또는 수동으로 터미널에서 설정할 수 있습니다. 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

하트 비트 원격 분석 전송 항상 되 고 사용 하지 않도록 설정할 수 없습니다.
  
### <a name="crash-reporting"></a>보고 충돌
  
치명적인 응용 프로그램 오류가 발생 하는 경우 응용 프로그램을 종료 및 크래시 보고서 'Watson' 서비스에 업로드 예기치 않게 됩니다. 크래시 보고서는 호출 스택을 응용 프로그램이 충돌에 이르는 처리 된 단계 목록이 있는 이루어져 있습니다. 이러한 단계는 엔지니어링 팀에 실패 한 정확한 함수를 식별 하는 데 도움이 및 그 이유입니다.
  
일부 경우에는 문서의 내용을 충돌 하는 응용 프로그램을 로설정하면 합니다. 앱 원인으로 문서를 식별 하는 경우 이름을 묻는 메시지가 사용자 하는 경우는를 호출 스택 함께 문서를 보낼 수도 있습니다. 사용자가이 질문에 대 한 적절된 한 선택을 설정할 수 있습니다. IT 관리자가 문서를 전송 하는 방법에 대 한 요구 사항이 엄격한 있고 문서를 보내지 않음 하는 사용자를 대신 하 여 결정 될 수 있습니다. 문서 전송 되지 않도록 방지 하 고 사용자에 게 프롬프트를 표시 하지 않으려면 다음 기본 설정을 설정할 수 있습니다.
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> **SendAllTelemetryEnabled** 가 **FALSE**로 설정 하는 경우 모든 프로세스가 비활성화 되었는지에 대 한 보고 충돌 합니다. 사용 현황 원격 분석을 보내지 않고 크래시 보고를 사용 하도록 설정 하려면 다음 기본 설정이 설정할 수 있습니다.```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>업데이트
  
Microsoft는 정기적으로 (일반적으로 매월) Mac 업데이트를 위한 Office 2016를 해제합니다. 사용자가 것을 적극 권장 하 고 컴퓨터를 최신 보안 픽스를 확인 하려면 최신 상태로 유지 하는 IT 관리자가 설치 됩니다. IT 관리자가 밀접 하 게 제어 하 고 컴퓨터 업데이트를 관리 하려는 경우 다음 기본 설정에서 자동으로 감지 하 고 제품 업데이트를 제공 하는 자동 업데이트 프로세스를 방지 하기 위해 설정할 수 있습니다.
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>방화벽/프록시를 사용 하 여 요청을 차단합니다.
  
방화벽 또는 프록시 서버를 통해 Url에 조직 블록을 요청 하는 경우 해야 차단 또는 허용로이 문서에 나열 된 Url을 구성 하는 40 X 응답 (예: 403 또는 404)가 표시 합니다. 40 X 응답 정상적으로 리소스에 액세스할 수 없으면을 수락 하 고 Office 응용 프로그램을 선택 하면 하 고 연결을 차례 대로 포함 될 다시 시도 하는 클라이언트를 단순히 삭제 하는 중 보다 더 빠른 사용자 경험을 제공 합니다.
  
프록시 서버에 인증이 필요한 경우 407 응답 클라이언트에 반환 됩니다. 최상의 환경을 사용 하는 경우 Office 2016 빌드 15.27 이상 NTLM 및 Kerberos 서버 (영문)에 대 한 특정 픽스를 포함 해야 합니다.
  
  
## <a name="see-also"></a>참고 항목

[Office 365 URL 및 IP 주소 범위](urls-and-ip-address-ranges.md)

