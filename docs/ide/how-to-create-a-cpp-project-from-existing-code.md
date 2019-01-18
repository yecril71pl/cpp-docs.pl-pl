---
title: 'Instrukcje: Tworzenie projektu C++ z istniejącego kodu'
ms.date: 01/15/2019
helpviewer_keywords:
- C++, creating projects from existing code
- Create New Project From Existing Code Files Wizard, project settings
f1_keywords:
- vc.appwiz.importwiz.location
- vc.appwiz.importwiz.appsettings
- vc.appwiz.importwiz.debugsettings
- vc.appwiz.importwiz.releasesettings
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
ms.openlocfilehash: 975d49e216c9aeb3f94ad385ef096794a446289f
ms.sourcegitcommit: 2ebbf8093fadb9a1b78a4381439bcd5c01a89267
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397345"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>Instrukcje: Tworzenie projektu C++ z istniejącego kodu

W programie Visual Studio, można przenosić do projektu C++ przy użyciu istniejących plików kodu **Utwórz nowy projekt z istniejących plików kodu** kreatora. Ten kreator tworzy projekt rozwiązanie, który korzysta z systemu MSBuild do zarządzania plikami źródłowymi i konfiguracja kompilacji. Działa najlepiej z stosunkowo proste projektów, które nie mają hierarchii folderów złożonych. Kreator nie jest dostępne w starszych wersjach Express programu Visual Studio. 

Przenoszenie istniejących plików kodu do projektu w języku C++ umożliwia korzystanie z funkcji zarządzania projektu programu MSBuild w natywnych wbudowanego w IDE. Jeśli chcesz użyć istniejącego systemu kompilacji, takie jak nmake pliki reguł programu make, narzędzia CMake lub rozwiązania alternatywne, możesz zamiast tego użyj opcji Otwórz Folder lub narzędzia CMake. Aby uzyskać więcej informacji, zobacz [projekty Otwórz Folder w programie Visual C++](../ide/non-msbuild-projects.md) lub [projektów CMake w programie Visual Studio](../ide/cmake-tools-for-visual-cpp.md). Obie opcje pozwalają używać funkcji środowiska IDE, takich jak [IntelliSense](/visualstudio/ide/using-intellisense) i [właściwości projektu](../ide/working-with-project-properties.md).

### <a name="to-create-a-c-project-from-existing-code"></a>Aby utworzyć projekt C++ z istniejącego kodu

1. Na **pliku** menu, wybierz opcję **New** > **projekt z istniejącego kodu**.

1. Na pierwszej stronie **Utwórz nowy projekt z istniejących plików kodu** kreatora wybierz **Visual C++** w **jaki rodzaj projektu chcesz utworzyć?** listy. Wybierz **dalej** aby kontynuować.

1. Określanie lokalizacji projektu, katalog dla plików źródłowych i rodzajów plików, które kreator importuje do nowego projektu. Wybierz **dalej** aby kontynuować.

    | Ustawienie | Opis |
    | --- | --- |
    | **Lokalizacja pliku projektu** | Określa ścieżkę katalogu nowy projekt. Ta lokalizacja jest, gdy Kreator depozyty, wszystkie pliki (i podkatalogi) nowego projektu.<br/><br/>Wybierz **Przeglądaj** do wyświetlenia **lokalizacja pliku projektu** okna dialogowego. Przejdź do folderu, prawo i określ katalog, który zawiera nowy projekt. |
    | **Nazwa projektu** | Określa nazwę nowego projektu. Pliki projektu, które mają rozszerzenia pliku, takie jak vcxproj przyjmuje tej nazwy i istniejących plików kodu zachować ich oryginalną nazwę. |
    | **Dodaj pliki do projektu z tych folderów** | Sprawdź można ustawić, aby Kreator skopiował istniejących plików kodu z ich oryginalnego katalogów, (które są określone w polu listy poniżej tego formantu) do nowego projektu.<br/><br/>Sprawdź **Dodaj podfoldery** do określenia kopiowania plików kodu ze wszystkich podkatalogów do projektu. Katalogi są wymienione w **folderu** kolumny.<br/>-Wybierz **Dodaj** do wyświetlenia **Dodaj pliki do projektu z tego folderu** okno dialogowe, aby określić katalogi, w Kreatorze wyszukuje istniejących plików kodu.<br/>-Wybierz **Usuń** można usunąć ścieżkę katalogu wybrane w polu listy.<br/><br/>W **typy plików do dodania do projektu** Określ rodzaje plików, które Kreator dodaje do nowego projektu na podstawie rozszerzeń danego pliku. Rozszerzenia plików są poprzedzone znakiem symbol wieloznaczny gwiazdka i są rozdzielane na liście rozszerzeń plików średnikiem. |
    | **Pokaż wszystkie pliki w Eksploratorze rozwiązań** | Określa, że wszystkie pliki w nowym projekcie jako widoczny i wyświetlane w **Eksploratora rozwiązań** okna. Ta opcja jest domyślnie włączona. |

    ![Lokalizacja projektu](media/location.png)

1. Określ ustawienia projektu, aby używać takich jak środowisko kompilacji dla nowego projektu i ustawienia kompilacji, aby były zgodne określonego typu nowy projekt do wygenerowania. Wybierz **dalej** aby kontynuować.

    | Ustawienie | Opis |
    | --- | --- |
    | **Use Visual Studio** | Określa, aby użyć narzędzia do kompilacji, które znajdują się w programie Visual Studio do tworzenia nowego projektu. Ta opcja jest domyślnie wybrana.<br/><br/>Wybierz **typu projektu** do określania typu projektu, Kreator generuje. Wybierz **projekt aplikacji Windows**, **projekt aplikacji konsoli**, **projekt dynamicznie łączonych bibliotek (DLL)**, lub **biblioteka statyczna (LIB) Projekt**.<br/><br/>Sprawdź **Dodaj obsługę ATL** do Dodaj obsługę ATL do nowego projektu.<br/><br/>Sprawdź **dodać obsługę MFC** dodać obsługę MFC do nowego projektu.<br/><br/>Sprawdź **obsługę środowiska uruchomieniowego języka wspólnego** dodać CLR programowania pomocy technicznej do projektu. Wybierz **Obsługa środowiska uruchomieniowego języka wspólnego** typu zgodności, takie jak **środowiska uruchomieniowego języka wspólnego (stara składnia)** pod kątem zgodności z zarządzanych rozszerzeń dla składni języka C++, CLR programowania składnię przed Visual C++ 2005. |
    | **Użyj zewnętrznego systemu kompilacji** | Określa, aby użyć narzędzia do kompilacji, które nie są uwzględnione w programie Visual Studio do tworzenia nowego projektu. Po wybraniu tej opcji można określić wiersze poleceń kompilacji na **Określ ustawienia konfiguracji debugowania** i **Określ ustawienia konfiguracji wydania** stron. |

    ![Ustawienia projektu](media/settings.png)

    > [!NOTE]
    > Gdy **użycia zewnętrznego systemu kompilacji** opcja jest zaznaczona, IDE nie da się skompilować projektu, więc /D, / I, /FI, /AI lub /FU opcje nie są wymagane dla kompilacji. Jednak te opcje muszą być ustawione poprawnie aby technologia IntelliSense działała poprawnie.

1. Określ ustawienia konfiguracji debugowania do wykorzystania. Wybierz **dalej** aby kontynuować.

    | Ustawienie | Opis |
    | --- | --- |
    | **Wiersz polecenia kompilacji** | Określa wiersz polecenia, który tworzy projekt. Wprowadź nazwę kompilator (oraz wszelkich przełączników lub argumentów) lub skrypty kompilacji, chcesz użyć do skompilowania projektu. |
    | **Ponownie skompiluj wiersza polecenia** | Określa wiersz polecenia, która odtwarza nowy projekt. |
    | **Wiersz poleceń oczyszczenia** | Określa wiersz polecenia, aby usunąć pliki obsługi, generowane przez narzędzia do kompilacji dla projektu. |
    | **Dane wyjściowe (na potrzeby debugowania)** | Określa ścieżkę katalogu plików wyjściowych dla konfiguracji debugowania projektu. |
    | **Definicje preprocesora (/ D)** | Definiuje symbole preprocesora dla projektu, zobacz [/D (definicje preprocesora)](../build/reference/d-preprocessor-definitions.md). |
    | **Ścieżka wyszukiwania plików dołączanych (/ I)** | Określa ścieżki katalogu, kompilator szuka rozwiązania przekazany do preprocesora dyrektyw odwołania do pliku w projekcie, zobacz [/I (dodatkowe katalogi dołączenia)](../build/reference/i-additional-include-directories.md). |
    | **Wymuszone załączone pliki (/FI)** | Określa pliki nagłówkowe przetwarzania podczas kompilowania projektu, zobacz [/FI (nazwij wymuszone obejmują plik)](../build/reference/fi-name-forced-include-file.md). |
    | **Ścieżka wyszukiwania zestawu .NET (/ AI)** | Określa ścieżki katalogu, które kompilator wyszukuje rozwiązania przekazany do preprocesora dyrektywy odwołania do zestawów .NET w projekcie, zobacz [/AI (Określ katalogi metadanych)](../build/reference/ai-specify-metadata-directories.md). |
    | **Wymuszone użycie zestawów .NET (/ FU)** | Określa zestawy .NET do przetworzenia podczas kompilowania projektu, zobacz [/FU (nazwij wymuszone #using)](../build/reference/fu-name-forced-hash-using-file.md). |

    ![Konfiguracja projektu](media/config.png)

    > [!NOTE]
    > **Kompilacji**, **odbudować**, **czysty** wiersza polecenia i **danych wyjściowych (debugowanie)** tylko w przypadku włączenia ustawień, jeśli **użycia zewnętrznego systemu kompilacji** zaznaczona jest opcja **Określ ustawienia projektu** strony.

1. Określ ustawienia konfiguracji wydania do użycia, te ustawienia są takie same jak ustawienia konfiguracji debugowania. Wybierz **Zakończ** można wygenerować nowy projekt.

    > [!NOTE]
    > W tym miejscu możesz sprawdzić **taki sam jak konfiguracja debugowania** do określenia, czy kreator wygeneruje ustawienia konfiguracji wydania projektu identyczne do ustawienia projektu dla konfiguracji debugowania. Ta opcja jest zaznaczona domyślnie. Wszystkie inne opcje na tej stronie są nieaktywne, chyba że zaznaczenie tego pola wyboru.
