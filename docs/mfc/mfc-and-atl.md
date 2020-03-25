---
title: MFC i ATL
ms.date: 01/24/2018
ms.assetid: 31b1a3a8-4154-4c4a-af10-fafc23ecdc5c
ms.topic: overview
ms.openlocfilehash: 3a58e68925fd77d002400bfe9d1f2bd28c60f78c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214334"
---
# <a name="mfc-and-atl"></a>MFC i ATL

Microsoft Foundation Classes (MFC) udostępniają otokę zorientowaną C++ obiektowo w systemie Win32 do szybkiego tworzenia natywnych aplikacji klasycznych. Active Template Library (ATL) jest biblioteką otoki, która upraszcza projektowanie modelu COM i jest używana w szerokim stopniu do tworzenia formantów ActiveX.

Możesz tworzyć programy MFC lub ATL przy użyciu programu Visual Studio Community Edition lub nowszego. Wersje Express nie obsługują MFC ani ATL.

W programie Visual Studio 2015 Wizualizacja C++ jest składnikiem opcjonalnym, a składniki MFC i ATL są opcjonalnymi podskładnikami w wizualizacji. C++ Jeśli te składniki nie zostaną wybrane podczas pierwszej instalacji programu Visual Studio, zostanie wyświetlony monit o zainstalowanie ich przy pierwszej próbie utworzenia lub otwarcia projektu MFC lub ATL.

W programie Visual Studio 2017 i nowszych, MFC i ATL są opcjonalnymi podskładnikami w ramach **programowania C++ na pulpicie przy użyciu** obciążenia w programie Instalator programu Visual Studio. Obsługę ATL można zainstalować bez MFC lub połączonej obsługi MFC i ATL (MFC zależy od ATL). Aby uzyskać więcej informacji na temat obciążeń i składników, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[Aplikacje klasyczne MFC](../mfc/mfc-desktop-applications.md)|Microsoft Foundation Classes zapewnić cienkie otoki zorientowane obiektowo za pośrednictwem systemu Win32, aby umożliwić szybkie C++opracowywanie aplikacji graficznego interfejsu użytkownika w programie.|
|[Składniki ATL COM pulpitu](../atl/atl-com-desktop-components.md)|ATL udostępnia szablony klas i inne konstrukcje używane do uproszczenia tworzenia obiektów COM w C++programie.|
|[Klasy udostępnione ATL/MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Odwołania do [klasy CStringT](../atl-mfc-shared/reference/cstringt-class.md) i innych klas, które są współużytkowane przez MFC i ATL.|
|[Praca z plikami zasobów](../windows/working-with-resource-files.md)|Edytor zasobów umożliwia edytowanie zasobów interfejsu użytkownika, takich jak ciągi, obrazy i okna dialogowe.|
|[Język C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Temat nadrzędny dla całej C++ zawartości w bibliotece MSDN.|
