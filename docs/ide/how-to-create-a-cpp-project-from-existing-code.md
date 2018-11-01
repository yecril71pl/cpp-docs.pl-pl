---
title: 'Porady: tworzenie projektu C++ z istniejącego kodu'
ms.date: 11/04/2016
helpviewer_keywords:
- C++, creating projects from existing code
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
ms.openlocfilehash: dafd4e939444c581a76e9ccfcab4c3f6bbe819d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552506"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>Porady: tworzenie projektu C++ z istniejącego kodu

W programie Visual Studio, można przenosić istniejące pliki kodu do projektu Visual C++ przy użyciu **Utwórz nowy projekt z istniejących plików kodu** kreatora. Ten kreator nie jest dostępne w starszych wersjach Express programu Visual Studio. Ten kreator tworzy nowe rozwiązanie i projekt, który korzysta z systemu MSBuild do zarządzania plików źródłowych i konfiguracja kompilacji.

Przenoszenie istniejących plików kodu do projektu Visual C++ pozwala na korzystanie ze wszystkich funkcji zarządzania natywnego projektu MSBuild wbudowanego w IDE. Jeśli chcesz użyć istniejącego systemu kompilacji, takie jak nmake pliki reguł programu make, narzędzia CMake lub rozwiązania alternatywne, możesz użyć opcji Otwórz Folder. Aby uzyskać więcej informacji, zobacz [projekty Otwórz Folder w programie Visual C++](../ide/non-msbuild-projects.md). Obie opcje pozwalają używać funkcji środowiska IDE, takich jak [IntelliSense](/visualstudio/ide/using-intellisense) i [właściwości projektu](../ide/working-with-project-properties.md).

### <a name="to-create-a-c-project-from-existing-code"></a>Aby utworzyć projekt C++ z istniejącego kodu

1. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projekt z istniejącego kodu**.

1. Na pierwszej stronie **Utwórz nowy projekt z istniejących plików kodu** kreatora wybierz **Visual C++** w **jaki rodzaj projektu chcesz utworzyć** listy. Wybierz **dalej** aby kontynuować.

1. Określanie lokalizacji projektu i katalog dla plików źródłowych. Aby uzyskać więcej informacji na tej stronie, zobacz [Określ lokalizację projektu i plików źródłowych, utworzyć Kreator nowego projektu z istniejącego kodu pliki](../ide/specify-project-location-and-source-files.md). Wybierz **dalej** aby kontynuować.

1. Określ ustawienia projektu do użycia. Aby uzyskać więcej informacji na tej stronie, zobacz [Określ ustawienia projektu, utworzyć Kreator nowego projektu z istniejącego kodu pliki](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md). Wybierz **dalej** aby kontynuować.

1. Określ ustawienia konfiguracji debugowania do wykorzystania. Aby uzyskać więcej informacji na tej stronie, zobacz [Określ ustawienia konfiguracji debugowania, utworzyć Kreator nowego projektu z istniejącego kodu pliki](../ide/specify-debug-configuration-settings.md). Wybierz **dalej** aby kontynuować.

1. Określ ustawienia konfiguracji wydania do użycia. Aby uzyskać więcej informacji na tej stronie, zobacz [Określ ustawienia konfiguracji wydania, utworzyć Kreator nowego projektu z istniejącego kodu pliki](../ide/specify-release-configuration.md). Wybierz **Zakończ** można wygenerować nowy projekt.

## <a name="see-also"></a>Zobacz też

[Określanie lokalizacji projektu i plików źródłowych, Kreator Utwórz nowy projekt z istniejących plików z kodem](../ide/specify-project-location-and-source-files.md)<br>
[Określanie ustawień projektu, Kreator Utwórz nowy projekt z istniejących plików z kodem](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)<br>
[Określanie ustawień konfiguracji debugowania, Kreator Utwórz nowy projekt z istniejących plików z kodem](../ide/specify-debug-configuration-settings.md)<br>
[Określanie ustawień konfiguracji wydania, Kreator Utwórz nowy projekt z istniejących plików z kodem](../ide/specify-release-configuration.md)