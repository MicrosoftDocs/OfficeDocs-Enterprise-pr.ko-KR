---
title: Office 365 비디오의 office 365 테 넌 트 격리
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
f1.keywords:
- NOCSH
description: '요약: Office 365 비디오의 테 넌 트 격리에 대 한 설명입니다.'
ms.openlocfilehash: c7fb97180fbe6c96d2849be7725958a788309558
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843659"
---
# <a name="tenant-isolation-in-office-365-video"></a>Office 365 비디오에서 테넌트 격리

> [!NOTE]
> Office 365 비디오가 Microsoft Stream으로 대체 됩니다. 비디오 공동 작업에 대 한 인텔리전스를 추가 하 고 현재 Office 365 비디오 고객의 전환 계획에 대해 자세히 알아보려면 [Office 365 비디오에서 Stream으로 마이그레이션을](https://docs.microsoft.com/stream/)참조 하세요.

## <a name="introduction"></a>소개

Azure Storage는 Office 365 비디오 및 Sway를 포함 하 여 여러 Office 365 서비스에 대 한 데이터를 저장 하는 데 사용 됩니다. Azure Storage에는 구조화 되지 않은 데이터를 저장 하는 데 사용 되는 고도로 확장 가능한 REST 기반 클라우드 개체 저장소 인 Blob 저장소가 포함 되어 있습니다. Azure Storage에서는 간단한 액세스 제어 모델을 사용 합니다. 각 Azure 구독에서는 하나 이상의 저장소 계정을 만들 수 있습니다. 각 저장소 계정에는 해당 저장소 계정의 모든 데이터에 대 한 액세스를 제어 하는 데 사용 되는 단일 비밀 키가 있습니다. 이는 저장소가 응용 프로그램에 연결 되어 있고 해당 응용 프로그램에 연결 된 데이터에 대 한 모든 권한이 있는 일반적인 시나리오를 지원 합니다. 예를 들어 Sway는 Azure Storage에 콘텐츠를 저장 합니다. Sway에 대 한 모든 고객 콘텐츠는 공유 Azure storage 계정에 저장 됩니다. 각 사용자의 콘텐츠는 Azure storage의 blob에 있는 별도의 디렉터리 트리에 있습니다.

고객 환경에 대 한 액세스를 관리 하는 시스템 (예: Azure Portal, SMAPI 등)은 Microsoft에서 운영 하는 Azure 응용 프로그램 내에서 격리 됩니다. 이는 고객 액세스 인프라와 고객 응용 프로그램 및 저장소 계층을 논리적으로 구분 하는 것입니다.

## <a name="tenant-isolation-in-office-365-video"></a>Office 365 비디오에서 테넌트 격리

[Office 365 video](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6) 는 조직에서 비디오 콘텐츠를 게시, 공유 및 검색할 수 있는 고도로 안전한 조직 차원의 대상을 제공 하는 엔터프라이즈 포털입니다. Office 365 비디오에서 각 테 넌 트의 비디오는 모든 위치에서 격리 되 고 암호화 되며, 조직의 동영상에 대 한 액세스 및 사용 권한이 있는 인증 된 사용자만 사용할 수 있습니다. Office 365 비디오에서는 다음과 같은 기술을 조합 하 여 사용 합니다.

- SharePoint Online은 비디오 파일 및 메타 데이터 (비디오 제목, 설명 등)를 저장 하는 데 사용 됩니다. 또한 보안 및 준수 계층 (인증 포함) 및 검색 기능을 제공 합니다.
- Azure 미디어 서비스는 트랜스 코딩, 적응 스트리밍, 보안 배달 (AES 암호화 사용) 및 축소판 기능을 제공 합니다.

[Azure Media Services](https://azure.microsoft.com/services/media-services/) 는 클라우드에서 종단 간 미디어 워크플로를 사용 하도록 설정 하기 위한 플랫폼 수준의 서비스 제공입니다. 이 플랫폼은 업로드, 인코딩, 암호화 (PlayReady 사용) 및 전 세계 Azure 데이터 센터를 통한 미디어 전달을 위한 REST API를 제공 합니다.

모든 Office 365 비디오의 업로드는 HTTPS를 통해 발생 합니다. 비디오 파일이 업로드 되 면 SharePoint Online에 저장 되 고 파일의 복사본이 Azure 미디어 서비스에 암호화 된 채널을 통해 전송 됩니다. Azure Media Services에서는 비디오를 시청 환경에 최적화 된 여러 형식 (예: 모바일, 낮은 대역폭, 고대역폭 등)으로 코드. 이러한 파일은 업로드 중에 가져온 원본 파일과 함께 Azure Blob storage에 저장 됩니다. 파일은 재생용 Common Encryption 패키징 알고리즘 (또는 이전 PlayReady 버전)에 따라 AES 128을 사용 하 여 암호화 되 고 Azure Blob storage에 저장 되기 전에 AES 256 storage Encryption을 사용 하 여 암호화 됩니다. (Azure Media Services 클라이언트 SDK를 사용 하 여 고객은 사용 되는 암호화를 제어할 수 있습니다. 예를 들어, 고객은 Azure Blob storage를 업로드 하기 전에 AES 256 (Azure Media Services storage encryption)를 높은 가치 미디어 자산에 적용할 수 있습니다.

또한 Azure Media Services는 암호화 된 채널을 통해 축소판 메타 데이터와 함께 SharePoint Online으로 전송 되는 비디오의 축소판 그림을 생성 합니다.
