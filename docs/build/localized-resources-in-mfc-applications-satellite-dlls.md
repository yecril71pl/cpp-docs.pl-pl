---
title: 'Zasoby zlokalizowane w aplikacjach MFC: biblioteki DLL Satellite'
ms.date: 11/04/2016
helpviewer_keywords:
- multiple language support [C++]
- localization [C++], MFC resources
- localized resources [C++]
- MFC DLLs [C++], localizing
- DLLs [C++], localizing MFC
- resources [MFC], localizing
- resource-only DLLs [C++]
- resource-only DLLs [C++], MFC applications
- satellite DLLs [C++]
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
ms.openlocfilehash: 1f512cc17832564b5eb530b97f8bfb2642c43d43
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220742"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>Zasoby zlokalizowane w aplikacjach MFC: biblioteki DLL Satellite

MFC w wersji 7,0 lub nowszej oferuje rozszerzoną obsługę satelitarnych bibliotek DLL, która pomaga w tworzeniu aplikacji zlokalizowanych w wielu językach. Satelitarna Biblioteka DLL jest [biblioteką DLL](creating-a-resource-only-dll.md) , która zawiera zasoby aplikacji zlokalizowane dla określonego języka. Po rozpoczęciu wykonywania aplikacji MFC automatycznie ładuje zlokalizowane zasoby najbardziej odpowiednie dla środowiska. Na przykład możesz mieć aplikację z zasobami języka angielskiego z dwiema satelitarnymi bibliotekami DLL, z których jedna zawiera francuskie tłumaczenie zasobów i drugi zawierający tłumaczenie w języku niemieckim. Gdy aplikacja jest uruchamiana w systemie języka angielskiego, używa zasobów w języku angielskim. W przypadku uruchomienia w systemie francuskim program korzysta z zasobów francuskich; w przypadku uruchomienia w systemie niemieckim program korzysta z zasobów niemieckich.

Aby można było obsługiwać zlokalizowane zasoby w aplikacji MFC, MFC próbuje załadować satelickiej biblioteki DLL zawierającej zasoby zlokalizowane do określonego języka. Satelitarne biblioteki DLL są nazywane *ApplicationNameXXX*. dll, gdzie *ApplicationName* jest nazwą pliku. exe lub. dll przy użyciu MFC, a *XXX* to kod składający się z trzech liter dla języka zasobów (na przykład "PLK" lub "DEU").

MFC próbuje załadować bibliotekę DLL zasobów dla każdego z następujących języków w kolejności, zatrzymując ją po znalezieniu:

1. Domyślny język interfejsu użytkownika bieżącego użytkownika, który został zwrócony z GetUserDefaultUILanguage () Win32 API.

1. Domyolny język interfejsu użytkownika bieżącego użytkownika, bez żadnego określonego języka (czyli ENC [kanadyjski angielski], zostanie plk [angielski (Stany Zjednoczone)]).

1. Domyślny język interfejsu użytkownika systemu, który został zwrócony z interfejsu API GetSystemDefaultUILanguage (). Na innych platformach jest to język samego systemu operacyjnego.

1. Domyślny język interfejsu użytkownika systemu, bez żadnego określonego języka.

1. Fałszywy język z 3-literowym kodem LOC.

Jeśli MFC nie odnajdzie żadnych satelitarnych bibliotek DLL, używa wszelkich zasobów zawartych w samej aplikacji.

Załóżmy na przykład, że aplikacja LangExample. exe używa MFC i działa w systemie wielu interfejsów użytkownika; język interfejsu użytkownika systemu to plk [angielski (Stany Zjednoczone), a bieżący język interfejsu użytkownika jest ustawiony na FRC [kanadyjski francuski]. MFC wyszukuje następujące biblioteki DLL w następującej kolejności:

1. LangExampleFRC. dll (język UI użytkownika).

1. LangExampleFRA. dll (język interfejsu użytkownika (bez języka), w tym przykładzie francuskim (Francja).

1. LangExampleENU. dll (język interfejsu użytkownika systemu).

1. LangExampleLOC. dll.

Jeśli żadna z tych bibliotek DLL nie zostanie znaleziona, MFC używa zasobów w LangExample. exe.

## <a name="see-also"></a>Zobacz też

[Tworzenie bibliotek DLL C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)<br/>
[TN057: lokalizacja składników MFC](../mfc/tn057-localization-of-mfc-components.md)
