---
title: Określ ustawienia projektu, Kreator Utwórz nowy projekt z istniejących plików z kodem
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.importwiz.appsettings
helpviewer_keywords:
- Create New Project From Existing Code Files Wizard, project settings
ms.assetid: 9b8860c9-d35f-4f18-9565-2934d3d7f569
ms.openlocfilehash: f46436295e16d527718e59f1c4c199643f9e35ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522346"
---
# <a name="specify-project-settings-create-new-project-from-existing-code-files-wizard"></a>Określ ustawienia projektu, Kreator Utwórz nowy projekt z istniejących plików z kodem

Użyj tej strony kreator Utwórz nowy projekt z istniejących plików kodu, aby określić:

- Środowisko kompilacji dla nowego projektu

- Ustawienia, aby dopasować określonego typu nowy projekt, aby wygenerować kompilacji

## <a name="task-list"></a>Lista zadań

[Instrukcje: tworzenie projektu C++ z istniejącego kodu](../ide/how-to-create-a-cpp-project-from-existing-code.md)

## <a name="uielement-list"></a>Lista elementów UI

- **Używanie programu Visual Studio**

   Określa, aby użyć narzędzia do kompilacji, które znajdują się w programie Visual Studio do tworzenia nowego projektu. Ta opcja jest domyślnie wybrana.

- **Typ projektu**

   Określa typ projektu, który zostanie wygenerowany przez kreatora.

- **Projekt aplikacji Windows**

   Wskazuje, że kreator wygeneruje projekt służący do pliku wykonywalnego aplikacji Windows. Ta opcja jest dostępna z **typu projektu** pole listy rozwijanej.

- **Projekt aplikacji konsoli**

   Wskazuje, że kreator wygeneruje projekt aplikacji konsoli. Ta opcja jest dostępna z **typu projektu** pole listy rozwijanej.

- **Projekt dynamicznie łączonych bibliotek (DLL)**

   Wskazuje, że kreator wygeneruje projekt aplikacji biblioteki dołączanej dynamicznie puste. Ta opcja jest dostępna z **typu projektu** pole listy rozwijanej.

- **Projekt biblioteki statycznej (LIB)**

   Wskazuje, że kreator wygeneruje projekt aplikacji biblioteki statycznej. Ta opcja jest dostępna z **typu projektu** pole listy rozwijanej.

- **Dodaj obsługę ATL**

   Dodaje obsługę ATL do nowego projektu.

- **Dodawanie obsługi MFC**

   Dodaje obsługę MFC do nowego projektu.

- **Dodano obsługę środowiska uruchomieniowego języka wspólnego**

   Dodaje CLR programowania pomocy technicznej do nowego projektu.

- **Środowisko uruchomieniowe języka wspólnego**

   Określa nowy projekt, aby były zgodne z funkcjami CLR.

- **Środowisko uruchomieniowe języka wspólnego (stara składnia)**

   Określa nowy projekt, aby zachować zgodność z zarządzanych rozszerzeń dla składni języka C++, który jest składnia programowania CLR przed Visual C++ 2005.

- **Użyj zewnętrznego systemu kompilacji**

   Określa, aby użyć narzędzia do kompilacji, które nie są uwzględnione w programie Visual Studio do tworzenia nowego projektu. Po wybraniu tej opcji można określić wiersze poleceń kompilacji na **Określ ustawienia konfiguracji debugowania** i **Określ ustawienia konfiguracji wydania** stron.

   > [!NOTE]
   > Podczas **użycia zewnętrznego systemu kompilacji** opcja jest zaznaczona, IDE nie są kompilowane nowy projekt, więc /D, mogę, /FI, /AI lub /FU opcje nie są wymagane dla kompilacji. Jednak te opcje muszą być ustawione poprawnie aby technologia IntelliSense działała poprawnie.

## <a name="see-also"></a>Zobacz też

[Określanie ustawień konfiguracji debugowania, Kreator Utwórz nowy projekt z istniejących plików z kodem](../ide/specify-debug-configuration-settings.md)<br>
[Określanie ustawień konfiguracji wydania, Kreator Utwórz nowy projekt z istniejących plików z kodem](../ide/specify-release-configuration.md)