---
title: Mac용 Office의 네트워크 요청
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/9/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Mac 용 Office 응용 프로그램은 macOS 플랫폼에서 기본 앱 환경을 제공 합니다. 각 앱은 네트워크 액세스를 사용할 수 없는 경우의 상태를 비롯 하 여 다양 한 시나리오에서 작동 하도록 설계 되었습니다. 컴퓨터가 네트워크에 연결 되 면 응용 프로그램은 일련의 웹 기반 서비스에 자동으로 연결 하 여 향상 된 기능을 제공 합니다. 이 백서에서는 응용 프로그램에서 연결을 시도 하는 끝점과 Url 및 제공 되는 서비스에 대해 설명 합니다. 이 정보는 네트워크 구성 문제를 해결 하 고 네트워크 프록시 서버에 대 한 정책을 설정할 때 유용 합니다. 이 문서의 세부 정보는 Office 365 URL 및 주소 범위 문서를 보완 하기 위해 작성 되었습니다.
ms.openlocfilehash: 0493fcc0954456ed190791b089fe4e0a568e82d7
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069661"
---
# <a name="network-requests-in-office-for-mac"></a>Mac용 Office의 네트워크 요청

Mac 용 Office 응용 프로그램은 macOS 플랫폼에서 기본 앱 환경을 제공 합니다. 각 앱은 네트워크 액세스를 사용할 수 없는 경우의 상태를 비롯 하 여 다양 한 시나리오에서 작동 하도록 설계 되었습니다. 컴퓨터가 네트워크에 연결 되 면 응용 프로그램은 일련의 웹 기반 서비스에 자동으로 연결 하 여 향상 된 기능을 제공 합니다. 다음 정보는 응용 프로그램에서 연결을 시도 하는 끝점과 Url 및 제공 되는 서비스에 대해 설명 합니다. 이 정보는 네트워크 구성 문제를 해결 하 고 네트워크 프록시 서버에 대 한 정책을 설정할 때 유용 합니다. 이 문서의 세부 정보는 Microsoft Windows를 실행 하는 컴퓨터에 대 한 끝점을 포함 하는 [Office 365 URL 및 주소 범위 문서](urls-and-ip-address-ranges.md)를 보완 하기 위해 작성 되었습니다. 별도로 설명 하지 않은 경우이 문서의 정보는 정품 상점에서 일회성 구매로 제공 되는 mac 용 Office 2019 및 Mac 용 Office 2016에도 적용 됩니다. 

  
이 문서의 대부분은 네트워크 Url, 유형 및 해당 끝점에서 제공 하는 서비스 또는 기능의 설명을 자세히 설명 하는 표입니다. 각 Office 앱은 서비스 및 끝점 사용과 다를 수 있습니다. 아래 표에는 다음 앱이 정의 되어 있습니다.
  
- W: Word
- P: PowerPoint
- X: Excel
- O: Outlook
- N: OneNote
   
URL 형식은 다음과 같이 정의 됩니다.
  
- ST: Static-URL은 클라이언트 응용 프로그램에 하드 코딩 됩니다.
    
- SS: 세미 정적-URL은 웹 페이지 또는 리디렉터의 일부로 인코딩됩니다.
    
- CS: Config Service-Office 구성 서비스의 일부로 URL이 반환 됩니다.

    
## <a name="office-for-mac-default-configuration"></a>Mac 용 Office 기본 구성

 **설치 및 업데이트**
  
다음 네트워크 끝점은 Microsoft CDN (콘텐츠 배달 네트워크)에서 Mac 용 Office 설치 프로그램을 다운로드 하는 데 사용 됩니다.
  
|**URL**|**종류**|**설명**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Office 365 설치 포털은 최신 설치 패키지에 연결 서비스를 전달 합니다.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |대비  <br/> |콘텐츠 배달 네트워크의 설치 패키지 위치입니다.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |대비  <br/> |콘텐츠 배달 네트워크의 설치 패키지 위치입니다.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |Microsoft 자동 업데이트의 관리 제어 끝점  <br/> |
   
 **첫 번째 앱 시작**
  
다음 네트워크 끝점은 Office 앱을 처음 시작할 때 연결 됩니다. 이러한 끝점은 사용자에 게 향상 된 Office 기능을 제공 하며, 라이선스 유형 (볼륨 라이선스 설치 포함)에 관계 없이 Url에 연결 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |' Flighting ' 구성-기능을 간편 하 고 실험해 볼 수 있습니다.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |' Flighting ' 네트워크 구성 테스트  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |' Flighting ' 네트워크 구성 테스트  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 구성 서비스-서비스 끝점의 마스터 목록입니다.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office Rules 원격 분석 다운로드-원격 분석 서비스에 업로드할 데이터와 이벤트에 대해 클라이언트에 게 알립니다.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |Kn  <br/> |진단  <br/> |OneNote 원격 분석 서비스  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 원격 분석 업로드 보고-"Heartbeart" 및 오류 이벤트가 클라이언트에서 발생 하는 경우 원격 분석 서비스에 업로드 됩니다.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |진단  <br/> |Office Online Template Service-사용자에 게 온라인 문서 서식 파일을 제공 합니다.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |진단  <br/> |Office Templates 다운로드-PNG 서식 파일 이미지의 저장소입니다.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |진단  <br/> |Office 앱에 대 한 저장소 구성입니다.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |진단  <br/> |Office Document Integration Services 카탈로그 (서비스 및 끝점 목록) 및 홈 영역 검색  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |진단  <br/> |홈 영역 검색 v2 용 리소스 (15.40 이상)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft 자동 업데이트 매니페스트-업데이트를 사용할 수 있는지 여부를 확인 합니다.  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |대비  <br/> |Microsoft Ajax JavaScript 라이브러리  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |하드웨어  <br/> |대비  <br/> |Office 구성 및 리소스에 대 한 위키백과 앱  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |대비  <br/> |Office 구성 및 리소스에 대 한 Bing 지도 앱  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |대비  <br/> |사용자 그래프 Office 구성 및 리소스에 대 한 앱  <br/> |
|```https://www.onenote.com/```  <br/> |Kn  <br/> |ST  <br/> |OneNote에 대 한 새로운 콘텐츠입니다.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |Kn  <br/> |ST  <br/> |OneNote에 대 한 새 콘텐츠입니다.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |Kn  <br/> |대비  <br/> |OneNote의 새로운 기능 이미지  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |앱 내 지원 서비스  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |전자 메일 계정 검색 서비스입니다.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook 자동 검색  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Office 365 서비스의 Outlook 끝점입니다.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Outlook 추가 기능 아이콘  <br/> |
   
> [!NOTE]
> Office 구성 서비스는 Mac 뿐 아니라 모든 Microsoft Office 클라이언트에 대 한 자동 검색 서비스 역할을 합니다. 응답에서 반환 되는 끝점은 매우 드물게 변경 되지만 가능한 경우에도 가능 합니다. 
  
 **로그인**
  
클라우드 기반 저장소에 로그인 할 때 다음 네트워크 끝점에 연결 됩니다. 계정 유형에 따라 각 서비스에 연결할 수 있습니다. 예를 들면 다음과 같습니다.
  
- **MSA: Microsoft 계정** -일반적으로 소비자 및 정품 시나리오에 사용 됩니다. 
    
- **OrgID: 조직 계정** -일반적으로 상업용 시나리오에 사용 됩니다. 
    
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Windows 권한 부여 서비스  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 365 Login Service (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft 계정 로그인 서비스 (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |진단  <br/> |Microsoft 계정에 MSA (로그인 서비스 도우미)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |대비  <br/> |Office 365 로그인 브랜딩 (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |진단  <br/> |문서 및 위치 저장소 로케이터  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |진단  <br/> |MRU (최근에 사용한) 문서 서비스  <br/> |
   
> [!NOTE]
> 구독 기반 및 정품 라이선스의 경우 둘 다 로그인 하면 제품이 정품 인증 되 고 OneDrive와 같은 클라우드 리소스에 액세스할 수 있습니다. 볼륨 라이선스 설치의 경우에도 사용자에 게는 기본적으로 로그인 하 라는 메시지가 나타나지만, 제품이 이미 활성화 되 면 클라우드 리소스에 대 한 액세스에만 필요 합니다. 
  
 **정품 인증**
  
다음 네트워크 끝점은 Office 365 구독 및 정품 라이선스 정품 인증에 적용 됩니다. 특히 볼륨 라이선스 설치에는 적용 되지 않습니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |진단  <br/> |Office Licensing Service  <br/> |
   
 **새로운 기능 콘텐츠**
  
다음 네트워크 끝점은 Office 365 구독에만 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |대비  <br/> |새로운 JSON 페이지 콘텐츠  <br/> |
   
 **리서치 도구**
  
다음 네트워크 끝점은 Office 365 구독에만 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |하드웨어  <br/> |진단  <br/> |리서치 도구 웹 서비스  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |하드웨어  <br/> |진단  <br/> |리서치 도구 정적 콘텐츠  <br/> |
|```https://www.bing.com/```  <br/> |하드웨어  <br/> |진단  <br/> |리서치 도구 콘텐츠 공급자  <br/> |
   
 **스마트 조회**
  
다음 네트워크 끝점은 Office 365 구독 및 정품/볼륨 라이선스 정품 인증 둘 다에 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |진단  <br/> |Insights 웹 서비스  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |진단  <br/> |JQuery 라이브러리  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |진단  <br/> |JavaScript 라이브러리 지원  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |진단  <br/> |Insights 콘텐츠 공급자  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |진단  <br/> |Insights 콘텐츠 공급자  <br/> |
   
 **PowerPoint Designer**
  
다음 네트워크 끝점은 Office 365 구독에만 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |<  <br/> |진단  <br/> |PowerPoint Designer 웹 서비스  <br/> |
   
 **PowerPoint 빠른 시작**
  
다음 네트워크 끝점은 Office 365 구독에만 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |<  <br/> |진단  <br/> |PowerPoint 빠른 시작 web service  <br/> |
   
 **웃는 얼굴 보내기/Frown**
  
다음 네트워크 끝점은 Office 365 구독 및 정품/볼륨 라이선스 정품 인증 둘 다에 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |진단  <br/> |웃는 얼굴 서비스 보내기  <br/> |
   
 **지원 서비스에 문의**
  
다음 네트워크 끝점은 Office 365 구독 및 정품/볼륨 라이선스 정품 인증 둘 다에 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |진단  <br/> |지원 서비스에 문의  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |진단  <br/> |앱 내 지원 서비스  <br/> |
   
 **PDF로 저장**
  
다음 네트워크 끝점은 Office 365 구독 및 정품/볼륨 라이선스 정품 인증 둘 다에 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |하드웨어  <br/> |진단  <br/> |Word 문서 변환 서비스 (PDF)  <br/> |
   
 **Office 앱 (즉, 추가 기능)**
  
Office 앱 추가 기능을 신뢰할 수 있는 경우 다음 네트워크 끝점이 Office 365 구독 및 정품/볼륨 라이선스 정품 인증에 모두 적용 됩니다.
  
|**URL**|**앱**|**종류**|**설명**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |진단  <br/> |Office 앱 스토어 구성  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |하드웨어  <br/> |대비  <br/> |위키백과 앱 리소스  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |대비  <br/> |Bing 지도 앱 리소스  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |대비  <br/> |사용자 그래프 앱 리소스  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |대비  <br/> |Office 리디렉션 서비스  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |대비  <br/> |Office JavaScript 라이브러리  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |대비  <br/> |Office 앱에 대 한 원격 분석 및 보고 서비스  <br/> |
|```https://ajax.microsoft.com/```  <br/> |하드웨어  <br/> |대비  <br/> |Microsoft Ajax JavaScript 라이브러리  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |대비  <br/> |Microsoft Ajax JavaScript 라이브러리  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |대비  <br/> |Office JavaScript 라이브러리  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |대비  <br/> |지원 리소스  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |대비  <br/> |지원 리소스  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |대비  <br/> |지원 리소스  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |대비  <br/> |JavaScript 라이브러리  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |대비  <br/> |오류 보고  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |대비  <br/> |글꼴 리소스  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |대비  <br/> |원격 분석 서비스  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |대비  <br/> |원격 분석 보고  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |대비  <br/> |Microsoft Store 자산 라이브러리  <br/> |
|```https://*.wikipedia.org/```  <br/> |하드웨어  <br/> |대비  <br/> |위키백과 페이지 리소스  <br/> |
|```https://upload.wikimedia.org/```  <br/> |하드웨어  <br/> |대비  <br/> |위키백과 미디어 리소스  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |하드웨어  <br/> |대비  <br/> |위키백과 샌드박스 프레임  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |대비  <br/> |맵 서식 파일  <br/> |
   
 **안전한 링크**
  
다음 네트워크 끝점은 Office 365 구독 전용의 모든 Office 응용 프로그램에 적용 됩니다.
  
|**URL**|**종류**|**설명**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |진단  <br/> |Microsoft 안전한 링크 서비스  <br/> |
   
 **크래시 보고**
  
다음 네트워크 끝점은 Office 365 구독 및 정품/볼륨 라이선스 정품 인증 모두에 대해 모든 Office 응용 프로그램에 적용 됩니다. 프로세스가 예기치 않게 중단 되 면 보고서가 생성 되어 Watson 서비스로 전송 됩니다.
  
|**URL**|**종류**|**설명**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Microsoft 오류 보고 서비스  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Office 공동 작업 Insights 서비스  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>네트워크 요청 및 트래픽 줄이기에 대 한 옵션

Mac 용 Office의 기본 구성은 기능 측면에서, 컴퓨터를 최신 상태로 유지 하는 최상의 사용자 환경을 제공 합니다. 일부 시나리오에서는 응용 프로그램이 네트워크 끝점에 연결 하지 못하도록 할 수 있습니다. 이 섹션에서는이 작업을 수행 하기 위한 옵션에 대해 설명 합니다.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>클라우드 로그인 및 Office 추가 기능 사용 안 함
  
볼륨 라이선스 고객은 클라우드 기반 저장소에 문서를 저장 하는 엄격한 정책이 있을 수 있습니다. 다음 응용 프로그램 단위 기본 설정은 MSA/OrgID 로그인 및 Office 추가 기능에 대 한 액세스를 사용 하지 않도록 설정할 수 있습니다.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

사용자가 로그인 함수에 액세스 하려고 하면 네트워크 연결이 표시 되지 않는 오류가 표시 됩니다. 이 기본 설정은 온라인 정품 인증도 차단 하므로 볼륨 라이선스 설치에만 사용 해야 합니다. 특히이 기본 설정을 사용 하면 Office 응용 프로그램에서 다음 끝점에 액세스할 수 없습니다.
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- 위의 ' 로그인 ' 섹션에 나열 된 모든 끝점
    
- 위의 ' 스마트 조회 ' 섹션에 나열 된 모든 끝점
    
- 위의 ' 제품 정품 인증 ' 섹션에 나열 된 모든 끝점
    
- 위의 ' Office Apps (즉, 추가 기능) ' 섹션에 나열 된 모든 끝점
    
사용자에 대 한 전체 기능을 다시 설정 하려면 기본 설정을 ' 2 '로 설정 하거나 제거 합니다.
  
> [!NOTE]
> 이 기본 설정에서는 Office for Mac 빌드 15.25 [160726] 이상이 필요 합니다. 
  
### <a name="telemetry"></a>원격 분석 
  
Mac 용 Office는 정기적으로 Microsoft에 원격 분석 정보를 보냅니다. 데이터가 ' Nexus ' 끝점에 업로드 됩니다. 원격 분석 데이터는 엔지니어링 팀이 각 Office 앱의 상태 및 예기치 않은 동작을 평가 하는 데 도움이 됩니다. 원격 분석에는 다음과 같은 두 가지 범주가 있습니다.
  
- **하트 비트** 버전 및 라이선스 정보를 포함 합니다. 이 데이터는 앱을 시작할 때 즉시 전송 됩니다. 
    
- **사용 용도** 앱을 사용 하는 방법과 치명적이 지 않은 오류에 대 한 정보가 포함 됩니다. 이 데이터는 60 분 마다 전송 됩니다. 
    
Microsoft는 개인 정보를 매우 진지 하 게 사용 합니다. Microsoft의 데이터 수집 정책에 대 한 자세한 내용은 [https://privacy.microsoft.com](https://privacy.microsoft.com)를 참조 하세요. 응용 프로그램에서 ' Usage ' 원격 분석을 보내지 못하도록 하기 위해 **SendAllTelemetryEnabled** 기본 설정이 조정 될 수 있습니다. 기본 설정은 응용 프로그램별 이며 macOS 구성 프로필을 통해 설정 하거나 터미널에서 수동으로 설정할 수 있습니다. 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

하트 비트 원격 분석은 항상 전송 되며 사용 하지 않도록 설정할 수 없습니다.
  
### <a name="crash-reporting"></a>크래시 보고
  
치명적인 응용 프로그램 오류가 발생 하면 응용 프로그램에서 예기치 않게 종료 되 고 크래시 보고서가 ' Watson ' 서비스로 업로드 됩니다. 충돌 보고서는 호출 스택, 즉 응용 프로그램이 중단 될 때까지 처리 중 이었던 단계 목록으로 구성 됩니다. 이 단계를 수행 하면 엔지니어링 팀이 실패 한 정확한 기능과 그 이유를 확인할 수 있습니다.
  
경우에 따라 문서의 내용으로 인해 응용 프로그램이 중단 될 수 있습니다. 앱이 문서를 원인으로 식별 하는 경우 사용자에 게 호출 스택과 함께 문서도 보낼 수 있는지 확인 합니다. 사용자는이 질문에 대 한 정보를 선택할 수 있습니다. IT 관리자는 문서 전송에 대 한 엄격한 요구 사항을 충족 하 고 사용자 대신 문서를 보내지 않도록 결정할 수 있습니다. 문서를 보내지 않도록 설정 하 고 사용자에 게 확인 메시지를 표시 하지 않으려면 다음 기본 설정을 사용 합니다.
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> **SendAllTelemetryEnabled** 가 **FALSE**로 설정 된 경우 해당 프로세스에 대 한 모든 충돌 보고가 사용 하지 않도록 설정 됩니다. 사용 현황 원격 분석을 보내지 않고 충돌 보고를 사용 하도록 설정 하려면 다음 기본 설정을 지정 하면 됩니다.```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>업데이트
  
Microsoft는 정기적으로 Office for Mac 업데이트를 릴리스 합니다 (보통 한 달에 한 번). 사용자와 IT 관리자가 최신 보안 픽스를 설치할 수 있도록 컴퓨터를 최신 상태로 유지 하는 것이 적극 권장 합니다. IT 관리자가 컴퓨터 업데이트를 면밀 하 게 제어 하 고 관리 하려는 경우 다음 기본 설정을 지정 하 여 자동 업데이트 프로세스에서 제품 업데이트를 자동적으로 감지 하 고 제공 하지 못하도록 할 수 있습니다.
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>방화벽/프록시를 사용 하 여 요청 차단
  
조직에서 방화벽 또는 프록시 서버를 통해 Url에 대 한 요청을 차단 하는 경우이 문서에 나열 된 Url을 허용 또는 40X response (예: 403 또는 404)로 나열 하 여 구성 해야 합니다. Office 응용 프로그램은 40X 응답을 통해 리소스에 액세스 하지 못하는 문제를 적절 하 게 수락할 수 있으며, 단순히 연결을 삭제 하는 것 보다 빠른 사용자 환경을 제공 하므로 클라이언트에서 다시 시도 하 게 됩니다.
  
프록시 서버에서 인증을 요청 하는 경우 407 응답이 클라이언트에 반환 됩니다. 최상의 환경을 위해 Office for Mac 빌드 15.27 이상에 NTLM 및 Kerberos 서버 작업에 대 한 특정 수정 프로그램을 포함 하 고 있는지 확인 합니다.
  
  
## <a name="see-also"></a>참고 항목

[Office 365 URL 및 IP 주소 범위](urls-and-ip-address-ranges.md)

