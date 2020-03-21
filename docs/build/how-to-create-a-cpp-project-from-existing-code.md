---
title: 'Porady: tworzenie projektu C++ z istniejącego kodu'
ms.date: 05/06/2019
helpviewer_keywords:
- C++, creating projects from existing code
- Create New Project From Existing Code Files Wizard, project settings
f1_keywords:
- vc.appwiz.importwiz.location
- vc.appwiz.importwiz.appsettings
- vc.appwiz.importwiz.debugsettings
- vc.appwiz.importwiz.releasesettings
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
ms.openlocfilehash: 5e59230186380b787c95dbe08914bcd9d3ca2407
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078553"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>Porady: tworzenie projektu C++ z istniejącego kodu

W programie Visual Studio można przenieść istniejące pliki kodu do C++ projektu za pomocą kreatora **tworzenia nowego projektu z istniejących plików z kodem** . Ten Kreator tworzy rozwiązanie projektu, które używa systemu MSBuild do zarządzania plikami źródłowymi i konfiguracją kompilacji. Najlepiej sprawdza się w przypadku stosunkowo prostych projektów, które nie mają złożonych hierarchii folderów. Kreator nie jest dostępny w starszych wersjach Express programu Visual Studio.

Przenoszenie istniejących plików kodu do C++ projektu umożliwia korzystanie z natywnych funkcji zarządzania projektami programu MSBuild wbudowanych w środowisko IDE. Jeśli wolisz używać istniejącego systemu kompilacji, takiego jak NMAKE reguł programu make, CMake lub alternatyw, możesz zamiast tego użyć opcji Otwórz folder lub CMake. Aby uzyskać więcej informacji, zobacz [Otwieranie projektów folderu C++ dla](open-folder-projects-cpp.md) lub [CMAKE projektów w programie Visual Studio](cmake-projects-in-visual-studio.md). Obie opcje pozwalają korzystać z funkcji środowiska IDE, takich jak [IntelliSense](/visualstudio/ide/using-intellisense) i [właściwości projektu](working-with-project-properties.md).

### <a name="to-create-a-c-project-from-existing-code"></a>Aby utworzyć projekt C++ z istniejącego kodu

1. W menu **plik** wybierz pozycję **Nowy** projekt > **z istniejącego kodu**.

1. Określ lokalizację projektu, katalog dla plików źródłowych i rodzaje plików, które Kreator importuje do nowego projektu. Wybierz pozycję **dalej** , aby kontynuować.

    | Ustawienie | Opis |
    | --- | --- |
    | **Lokalizacja pliku projektu** | Określa ścieżkę katalogu nowego projektu. Ta lokalizacja polega na tym, że Kreator złoży wszystkie pliki (i podkatalogi) nowego projektu.<br/><br/>Wybierz przycisk **Przeglądaj** , aby wyświetlić okno dialogowe **Lokalizacja pliku projektu** . Przejdź do odpowiedniego folderu i określ katalog, który zawiera nowy projekt. |
    | **Nazwa projektu** | Określa nazwę nowego projektu. Pliki projektu, które mają rozszerzenia plików, takie jak. vcxproj, przyjmują tę nazwę i istniejące pliki kodu zachowują swoją oryginalną nazwę. |
    | **Dodaj pliki do projektu z tych folderów** | Zaznacz, aby skonfigurować kreatora do kopiowania istniejących plików kodu z ich oryginalnych katalogów (które są określone w polu listy poniżej tego formantu) do nowego projektu.<br/><br/>Zaznacz opcję **Dodaj podfoldery** , aby określić kopiowanie plików kodu ze wszystkich podkatalogów do projektu. Katalogi są wymienione w kolumnie **folder** .<br/>-Wybierz pozycję **Dodaj** , aby wyświetlić okno dialogowe **Dodaj pliki do projektu z tego folderu** , aby określić katalogi, w których Kreator szuka istniejących plików kodu.<br/>-Wybierz pozycję **Usuń** , aby usunąć ścieżkę katalogu wybraną w polu listy.<br/><br/>W polu **typy plików, które mają zostać dodane do pola projekt** , określ rodzaje plików, które Kreator dodaje do nowego projektu na podstawie danego rozszerzenia pliku. Rozszerzenia plików są poprzedzone symbolem wieloznacznym gwiazdki i są rozdzielane na liście rozszerzeń plików średnikami. |
    | **Pokaż wszystkie pliki w Eksplorator rozwiązań** | Określa, że wszystkie pliki w nowym projekcie mają być widoczne i wyświetlane w oknie **Eksplorator rozwiązań** . Ta opcja jest domyślnie włączona. |

    ![Lokalizacja projektu](media/location.png)

1. Określ ustawienia projektu, które mają być używane, takie jak środowisko kompilacji dla nowego projektu i ustawienia kompilacji, aby odpowiadały określonemu typowi nowego projektu do wygenerowania. Wybierz pozycję **dalej** , aby kontynuować.

    | Ustawienie | Opis |
    | --- | --- |
    | **Korzystanie z programu Visual Studio** | Określa, aby użyć narzędzi do kompilacji, które są zawarte w programie Visual Studio do tworzenia nowego projektu. Ta opcja jest domyślnie wybrana.<br/><br/>Wybierz **Typ projektu** , aby określić typ projektu, który zostanie wygenerowany przez kreatora. Wybierz projekt **aplikacji systemu Windows**, projekt **aplikacji konsolowej**, **projekt dynamicznie połączony biblioteki (dll)** lub **projektu Biblioteka statyczna (lib)** .<br/><br/>Zaznacz opcję **Dodaj obsługę biblioteki ATL** , aby dodać obsługę ATL do nowego projektu.<br/><br/>Zaznacz opcję **Dodaj obsługę dla MFC** , aby dodać obsługę MFC do nowego projektu.<br/><br/>Zaznacz opcję **Dodaj obsługę środowiska uruchomieniowego języka wspólnego** , aby dodać obsługę programowania CLR do projektu. Wybierz opcję **Obsługa środowiska uruchomieniowego** CLR dla typu zgodności, na przykład **środowisko uruchomieniowe języka wspólnego (stara składnia)** , aby zapewnić C++ zgodność z rozszerzeniami zarządzanymi dla składni, składnię programowania dla środowiska wykonawczego przed programem Visual Studio 2005. |
    | **Użyj zewnętrznego systemu kompilacji** | Określa, aby używać narzędzi kompilacji, które nie są uwzględnione w programie Visual Studio do tworzenia nowego projektu. Po wybraniu tej opcji można określić wiersze poleceń kompilacji na stronie **Określanie ustawień konfiguracji debugowania** i **Określanie ustawień konfiguracji wydania** . |

    ![Ustawienia projektu](media/settings.png)

    > [!NOTE]
    > Gdy zaznaczona jest opcja **Użyj zewnętrznego systemu kompilacji** , IDE nie kompiluje projektu, więc opcje/D,/I,/Fi,/AI lub/Fu nie są wymagane do kompilacji. Jednak te opcje muszą być poprawnie ustawione, aby funkcja IntelliSense działała prawidłowo.

1. Określ ustawienia konfiguracji debugowania do użycia. Wybierz pozycję **dalej** , aby kontynuować.

    | Ustawienie | Opis |
    | --- | --- |
    | **Wiersz polecenia kompilacji** | Określa wiersz polecenia, który kompiluje projekt. Wprowadź nazwę kompilatora (wraz z dowolnymi przełącznikami lub argumentami) lub skrypty kompilacji, których chcesz użyć do skompilowania projektu. |
    | **Ponownie skompiluj wiersz polecenia** | Określa wiersz polecenia, który ponownie kompiluje nowy projekt. |
    | **Wyczyść wiersz polecenia** | Określa wiersz polecenia do usuwania plików obsługi generowanych przez narzędzia kompilacji dla projektu. |
    | **Dane wyjściowe (na potrzeby debugowania)** | Określa ścieżkę katalogu plików wyjściowych dla konfiguracji debugowania projektu. |
    | **Definicje preprocesora (/D)** | Definiuje symbole preprocesora dla projektu, zobacz [/d (Definicje preprocesora)](../build/reference/d-preprocessor-definitions.md). |
    | **Ścieżka wyszukiwania dołączania (/I)** | Określa ścieżki katalogów, które kompilator wyszukuje w celu rozpoznania odwołań do plików przesłanych do dyrektyw preprocesora w projekcie, zobacz [/i (Dodatkowe katalogi dołączane)](../build/reference/i-additional-include-directories.md). |
    | **Wymuszone pliki dołączone (/FI)** | Określa pliki nagłówkowe do przetworzenia podczas kompilowania projektu, zobacz [/Fi (nazwa pliku wymuszonego dołączenia)](../build/reference/fi-name-forced-include-file.md). |
    | **Ścieżka wyszukiwania zestawu .NET (/AI)** | Określa ścieżki katalogów, które kompilator przeszukuje w celu rozpoznania odwołań do zestawów .NET przekazaną do dyrektyw preprocesora w projekcie, zobacz [/AI (Określ katalogi metadanych)](../build/reference/ai-specify-metadata-directories.md). |
    | **Wymuszone użycie zestawów .NET (/FU)** | Określa zestawy .NET do przetworzenia podczas kompilowania projektu, zobacz [/Fu (Name force #using File)](../build/reference/fu-name-forced-hash-using-file.md). |

    ![Konfiguracja projektu](media/config.png)

    > [!NOTE]
    > Ustawienia **Build**, **Build**, **Clean** Command i **Output (for debug)** są włączone tylko w przypadku wybrania opcji **Użyj zewnętrznego systemu kompilacji** na stronie **Określanie ustawień projektu** .

1. Określ ustawienia konfiguracji wydania, które mają być używane, te ustawienia są takie same jak ustawienia konfiguracji debugowania. Wybierz pozycję **Zakończ** , aby wygenerować nowy projekt.

    > [!NOTE]
    > W tym miejscu możesz sprawdzić, **jak Konfiguracja debugowania** , aby określić, że Kreator będzie generować ustawienia projektu konfiguracji wydania identyczne z ustawieniami projektu konfiguracji debugowania. Ta opcja jest domyślnie zaznaczona. Wszystkie inne opcje na tej stronie są nieaktywne, o ile nie zostanie ono odszukane.
