---
title: MFC i ATL
ms.date: 01/24/2018
ms.assetid: 31b1a3a8-4154-4c4a-af10-fafc23ecdc5c
ms.openlocfilehash: c2cfb77f0e3885e0b315ddfe38bf942ec157375a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58780252"
---
# <a name="mfc-and-atl"></a>MFC i ATL

Microsoft Foundation Classes (MFC) zapewnia otok obiektowy C++ Win32 umożliwia szybkie wdrażanie natywnych aplikacji komputerowych. Active Template Library (ATL) jest biblioteką otoki, która upraszcza tworzenie modelu COM i jest często używane do tworzenia kontrolek ActiveX.

Można tworzyć programy MFC lub ATL za pomocą programu Visual Studio Community Edition lub nowszy. Wersje Express nie obsługują kontenera MFC ani ATL.

W programie Visual Studio 2015 Visual C++ jest opcjonalny, a składniki MFC i ATL są opcjonalne składniki podrzędne w obszarze Visual C++. Jeśli nie wybierzesz tych składników podczas pierwszej instalacji programu Visual Studio, monit będą instalowane, gdy użytkownik podejmie próbę Utwórz lub Otwórz projekt ATL i MFC po raz pierwszy.

W programie Visual Studio 2017 i nowsze, MFC i ATL są opcjonalne składniki podrzędne w ramach **programowanie aplikacji klasycznych w języku C++** obciążenia w programie Instalatora programu Visual Studio. Można zainstalować funkcję obsługi ATL bez MFC lub obsługa MFC i ATL (MFC zależy od ATL) w połączeniu. Aby uzyskać więcej informacji na temat obciążeń i składników, zobacz [Install Visual Studio 2017](/visualstudio/install/install-visual-studio).

## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[Aplikacje dla Pulpitu MFC](../mfc/mfc-desktop-applications.md)|Klasy Microsoft Foundation udostępniają cienką otok obiektowy za pośrednictwem systemu Win32 w celu umożliwienia szybkiego opracowywania aplikacji GUI w języku C++.|
|[Składniki ATL COM pulpitu](../atl/atl-com-desktop-components.md)|ATL zawiera szablony klas oraz inne użycie konstrukcji, aby uprościć tworzenie obiektów COM w języku C++.|
|[Klasy współdzielone ATL/MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Odwołania do [CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md) i innych klas, które są współużytkowane przez MFC i ATL.|
|[Praca z plikami zasobów](../windows/working-with-resource-files.md)|Edytor zasobów umożliwia edytowanie zasobów interfejsu użytkownika, takich jak ciągi, obrazy i oknach dialogowych.|
|[Visual C++](../overview/visual-cpp-in-visual-studio.md)|Temat nadrzędny dla całej zawartości C++ w bibliotece MSDN.|