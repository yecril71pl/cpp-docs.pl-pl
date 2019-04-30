---
title: Pisanie i Refaktoryzacja kodu (C++)
ms.date: 04/30/2018
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
ms.openlocfilehash: bc839a759d2ff3f403ca001ab32702d3fe27833e
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345245"
---
# <a name="writing-and-refactoring-code-c"></a>Pisanie i Refaktoryzacja kodu (C++)

Edytor kodu Visual C++ oraz środowiska IDE i zapewniają wiele pomoce kodowania. Niektóre są unikatowe dla języka C++, a niektóre są zasadniczo takie same dla wszystkich języków Visual Studio. Aby uzyskać więcej informacji o funkcjach udostępnionych, zobacz [pisanie kodu w edytorze tekstu i kodu](/visualstudio/ide/writing-code-in-the-code-and-text-editor). Opcje umożliwia włączenie i skonfigurowanie funkcji specyficznych dla języka C++ znajdują się w obszarze **narzędzia &#124; opcje &#124; edytora tekstów &#124; C/C++**. Po wybraniu opcji chcesz ustawić, można uzyskać pomoc, naciskając klawisz **F1** gdy okno jest w trybie koncentracji uwagi. Dla kodu ogólne opcje formatowania, wpisz `Editor C++` do **szybkiego uruchamiania**.

Funkcji eksperymentalnych, które mogą lub nie mogą zostać zawarte w przyszłych wersjach programu Visual Studio, znajdują się w [eksperymentalne C++ edytora tekstów](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental) okna dialogowego. W programie Visual Studio 2017 można włączyć **Predictive IntelliSense** w tym oknie dialogowym.

## <a name="adding-new-files"></a>Dodanie nowych plików

Aby dodać nowe pliki do projektu, kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań, a następnie wybierz **Dodaj &#124; New**.

## <a name="formatting-options"></a>Opcje formatowania

Aby ustawić opcje, takie jak wcięcia, uzupełnianie nawiasów i kolorowanie formatowania, wpisz "C++ formatowania" w **szybkiego uruchamiania** okna. Visual Studio 2017 w wersji 15.7 lub nowszej obsługuje narzędzie ClangFormat. Możesz skonfigurować go w [strona właściwości formatowania dla języka C/C++](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting) w obszarze **narzędzia &#124; opcje &#124; edytora tekstów &#124; C/C++ &#124; formatowanie**.

![Opcje formatowania dla języka C++](media/cpp-formatting-options.png)

## <a name="intellisense"></a>IntelliSense

Technologia IntelliSense jest nazwą zestawu funkcji, które zawierają wbudowane informacje dotyczące elementów członkowskich, typy i przeciążenia funkcji. Na poniższej ilustracji przedstawiono listy elementów członkowskich listy rozwijanej, która pojawia się podczas wpisywania. Klawisz tab do wprowadzania tekstu zaznaczonego elementu w pliku kodu.

![C&#43; &#43; elementu członkowskiego listy rozwijanej](../ide/media/vs2015_cpp_statement_completion.png "vs2015_cpp_statement_completion")

Aby uzyskać pełne informacje, zobacz [Visual C++ IntelliSense](/visualstudio/ide/visual-cpp-intellisense).

## <a name="insert-snippets"></a>Wstawianie fragmentów kodu

Fragment kodu jest wstępnie zdefiniowanych fragmentem kodu źródłowego. Kliknij prawym przyciskiem myszy pojedynczy punkt lub przy wybranym tekście, wstawić framgent kodu lub przestrzenny, zaznaczony tekst fragmentem kodu. Na poniższej ilustracji przedstawiono trzy kroki, aby otoczyć wybranego sprawozdania z pętli for. Żółty światła w obrazie końcowym są edytowalne, do których dostęp przy użyciu klawisza tab. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).

![Visual C&#43;&#43; Insert Snippet Drop&#45;down](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

## <a name="add-class"></a>Dodaj klasę

Dodaj nową klasę z **projektu** menu za pomocą Kreatora klas.

![Dodaj nową klasę w języku Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_class.png "vs2015_cpp_add_class")

Można także użyć Kreatora klasy, aby zmodyfikować lub zbadać istniejącej klasy.

![Visual C&#43;&#43; Class Wizard](../ide/media/vs2015_cpp_class_wizard.png "vs2015_cpp_class_wizard")

Aby uzyskać więcej informacji, zobacz [Dodawanie funkcji za pomocą kreatorów kodu (C++)](../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="refactoring"></a>Refaktoryzacja

Refaktoryzacje są dostępne z menu kontekstowego szybkich działań lub klikając [żarówki](/visualstudio/ide/perform-quick-actions-with-light-bulbs) w edytorze.  Niektóre również znajdują się w **Edytuj > Refaktoryzuj** menu.  Te funkcje obejmują:

* [Zmiana nazwy](refactoring/rename.md)
* [Wyodrębnianie funkcji](refactoring/extract-function.md)
* [Implementowanie czystych elementów wirtualnych](refactoring/implement-pure-virtuals.md)
* [Tworzenie deklaracji/definicji](refactoring/create-declaration-definition.md)
* [Przenoszenie definicji funkcji](refactoring/move-definition-location.md)
* [Konwertowanie na literał nieprzetworzonego ciągu](refactoring/convert-to-raw-string-literal.md)
* [Zmienianie podpisu](refactoring/change-signature.md)

## <a name="navigate-and-understand"></a>Nawigowanie i zrozumienie

Visual C++ udostępnia wiele funkcji nawigacji w kodzie z innymi językami. Aby uzyskać więcej informacji, zobacz [nawigowanie do kodu](/visualstudio/ide/navigating-code) i [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).

## <a name="quickinfo"></a>Skrócone informacje

Umieść kursor nad zmienną, aby wyświetlić informacje o typie.

![Visual C&#43;&#43; QuickInfo](../ide/media/vs2015_cpp_quickinfo.png "vs2015_cpp_quickInfo")

## <a name="open-document-navigate-to-header"></a>Otwórz dokument (Przejdź do nagłówka)

Kliknij prawym przyciskiem myszy nazwę nagłówka w `#include` dyrektywy i Otwórz plik nagłówkowy.

![Program Visual C&#43; &#43; opcji menu Otwórz dokument](../ide/media/vs2015_cpp_open_document.png "vs2015_cpp_open_document")

## <a name="peek-definition"></a>Zobacz definicję

Umieść kursor nad zmienną lub funkcję deklaracji, kliknij prawym przyciskiem myszy, następnie wybierz **Peek Definition** Aby wyświetlić widok wbudowane jego definicji. Aby uzyskać więcej informacji, zobacz [zobacz definicję (Alt + F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![Visual C&#43;&#43; Peek Definition](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

## <a name="go-to-definition"></a>Przejdź do definicji

Umieść kursor nad zmienną lub funkcję deklaracji, kliknij prawym przyciskiem myszy, następnie wybierz **przejdź do definicji** można otworzyć dokumentu, gdy obiekt jest zdefiniowany.

## <a name="view-call-hierarchy"></a>Pokaż hierarchię wywołań

Kliknij prawym przyciskiem myszy na każde wywołanie funkcji i wyświetlania listy resursive wszystkie funkcje, które wywołuje metodę i wszystkie funkcje, które ją wywołują. Każda funkcja na liście można rozwijać w taki sam sposób. Aby uzyskać więcej informacji, zobacz [hierarchię wywołań,](/visualstudio/ide/reference/call-hierarchy).

![Visual C&#43;&#43; Call Hierarchy](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="toggle-header--code-file"></a>Przełącz nagłówek / plik kodu

Kliknij prawym przyciskiem myszy i wybierz polecenie **Przełącz nagłówek / plik kodu** się przełączać między plik nagłówkowy i jego skojarzony plik kodu.

## <a name="outlining"></a>Tworzenie konspektu

Kliknij prawym przyciskiem myszy w dowolnym miejscu w pliku kodu źródłowego, a następnie wybierz **konspekt** Aby zwinąć lub rozwinąć definicje i/lub niestandardowych regionów, aby ułatwić przeglądanie tylko te części, które Cię interesuje. Aby uzyskać więcej informacji, zobacz [konspekt](/visualstudio/ide/outlining).

![Visual C&#43;&#43; Outlining](../ide/media/vs2015_cpp_outlining.png "vs2015_cpp_outlining")

## <a name="scrollbar-map-mode"></a>Tryb mapy paska przewijania

Tryb mapy paska przewijania pozwala szybko przewiń i przeglądać pliku z kodem bez opuszczania faktycznie Twojej bieżącej lokalizacji. Lub kliknij w dowolnym miejscu na mapie kodu, aby przejść bezpośrednio do tej lokalizacji. Aby uzyskać więcej informacji, zobacz [jak: Śledzenie kodu przez dostosowania paska przewijania](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

![Mapa w języku Visual C kodu&#43;&#43;](../ide/media/vs2015_cpp_code_map.png "vs2015_cpp_code_map")

## <a name="generate-graph-of-include-files"></a>Generowanie grafu plików dołączanych

Kliknij prawym przyciskiem myszy plik kodu w projekcie, a następnie wybierz **Generowanie grafu plików dołączanych** wyświetlić wykres, które pliki zostały dołączone przez inne pliki.

![Program Visual C&#43; &#43; grafu plików dołączanych](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="f1-help"></a>Pomoc F1

Umieść kursor na lub po prostu po dowolnego typu, słowo kluczowe lub funkcji, a następnie naciśnij klawisz F1, aby przejść do tematu odpowiednie odwołania w witrynie docs.microsoft.com. F1 działa również na elementy na liście błędów, a wiele okien dialogowych.

## <a name="quick-launch"></a>Szybkie uruchamianie

Aby łatwo przejść do dowolnego okna lub narzędzia w programie Visual Studio, należy po prostu wpisz jego nazwę w oknie szybkiego uruchamiania w prawym górnym rogu interfejsu użytkownika. Listy autouzupełniania będzie filtrować podczas wpisywania.

![Visual Studio Quick Launch](../ide/media/vs2015_cpp_quick_launch.png "vs2015_cpp_quick_launch")
