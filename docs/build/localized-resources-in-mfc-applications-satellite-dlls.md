---
title: 'Zlokalizowane zasoby w aplikacjach MFC: Satelitarne biblioteki dll'
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
ms.openlocfilehash: c593d0bae6fc23cfd765116c44b07caa2a6d8ccf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821329"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>Zlokalizowane zasoby w aplikacjach MFC: Satelitarne biblioteki dll

MFC w wersji 7.0 lub nowszy zapewnia rozszerzoną obsługę satelitarnej biblioteki dll, funkcja, która pomaga w tworzeniu aplikacji zlokalizowanej w wielu językach. Satelitarne biblioteki DLL jest [DLL tylko dla zasobów](creating-a-resource-only-dll.md) zawierający zasoby aplikacji są zlokalizowane dla określonego języka. Po rozpoczęciu wykonywania aplikacji MFC automatycznie ładuje zlokalizowany najbardziej odpowiednie dla środowiska. Na przykład może mieć aplikacji przy użyciu języka angielskiego zasobów przy użyciu dwóch satelickich bibliotek DLL, zawierające francuska tłumaczenie zasobów, a drugi zawierający niemieckiego tłumaczenia. Po uruchomieniu aplikacji w języku angielskim systemie używa zasobów w języku angielskim. Jeśli działa w systemie, francuskim, używa zasobów francuskim. Jeśli działa w systemie, niemieckim, używa zasobów niemieckim.

Do obsługi zlokalizowanych zasobów w aplikacji MFC, MFC próbuje załadować satelitarną bibliotekę DLL zawierającą zasoby zlokalizowane dla określonego języka. Biblioteki DLL Satellite są nazywane *ApplicationNameXXX*.dll, gdzie *ApplicationName* nazywa się .exe lub .dll, za pomocą MFC, i *XXX* jest trzyliterowy kod języka zasoby (na przykład "ENU" lub "(DEU)").

MFC próbuje załadować biblioteki DLL zasobów dla każdego z następujących języków, w kolejności, zatrzymując się, gdy zostanie znaleziony:

1. Bieżący użytkownik domyślny język interfejsu użytkownika, ponieważ zwrócony z interfejsu API Win32 GetUserDefaultUILanguage().

1. Bieżący użytkownik w domyślny język interfejsu użytkownika, bez żadnych szczególnych podjęzyk (czyli ENC [kanadyjski angielskiej] staje się ENU [US English]).

1. System domyślny język interfejsu użytkownika, zwrócone z interfejsu API GetSystemDefaultUILanguage(). Na innych platformach jest to język systemu operacyjnego, sam.

1. System domyślny język interfejsu użytkownika, bez żadnych szczególnych podjęzyk.

1. Język fałszywych 3-literowy kod LOC.

MFC nie może znaleźć wszystkie satelitarne bibliotek DLL, używa, niezależnie od zasobów znajdują się w samej aplikacji.

Na przykład załóżmy, że aplikacja LangExample.exe używa biblioteki MFC i działa na wielu systemu interfejsu użytkownika. język interfejsu użytkownika systemu jest ENU [US Angielski] i FRC [francuski kanadyjski] ustawiony jest język interfejsu użytkownika bieżącego użytkownika. MFC szuka następujących bibliotek DLL w następującej kolejności:

1. LangExampleFRC.dll (język interfejsu użytkownika dla użytkownika).

1. LangExampleFRA.dll (język Interfejsu użytkownika bez podjęzyk, w tym przykładzie francuski (Francja).

1. LangExampleENU.dll (język interfejsu użytkownika systemu).

1. LangExampleLOC.dll.

Jeśli nie zostaną znalezione żadne z tych bibliotek DLL, MFC wykorzystuje zasoby w LangExample.exe.

## <a name="see-also"></a>Zobacz także

[Biblioteki DLL w programie Visual C++](dlls-in-visual-cpp.md)<br/>
[TN057: Lokalizacja składników MFC](../mfc/tn057-localization-of-mfc-components.md)
