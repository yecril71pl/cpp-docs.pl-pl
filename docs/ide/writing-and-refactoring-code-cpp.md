---
title: Zapisywanie i refaktoryzacji kodu (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/30/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 000428ce3975dab108387ddb598bddf4a89fcfdd
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="writing-and-refactoring-code-c"></a>Zapisywanie i refaktoryzacji kodu (C++)

Edytor kodu Visual C++ i IDE zapewniają wiele pomocy kodowania. Niektóre są unikatowe dla języka C++, a niektóre są zasadniczo takie same dla wszystkich języków Visual Studio. Aby uzyskać więcej informacji o funkcjach udostępnionego, zobacz [pisanie kodu w edytorze kodu i tekstu](/visualstudio/ide/writing-code-in-the-code-and-text-editor). Opcje dotyczące włączania i konfigurowania funkcji specyficznych dla języka C++ znajdują się w obszarze **narzędzia &#124; opcje &#124; Edytor tekstu &#124; C/C++**. Po wybraniu opcji, które chcesz ustawić, można uzyskać więcej pomocy, naciskając **F1** gdy okno jest aktywny. Dla opcji formatowania kodu ogólne, wpisz `Editor C++` do **szybkiego uruchamiania**.

Eksperymentalne funkcje, które mogą lub nie może być zawarta w przyszłych wersjach programu Visual Studio, znajdują się w [eksperymentalne C++ Edytor tekstu](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental) okna dialogowego. W programie Visual Studio 2017 można włączyć **predykcyjnej Intellisense** w tym oknie dialogowym.

## <a name="adding-new-files"></a>Dodawanie nowych plików

Aby dodać nowe pliki do projektu, kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz polecenie **Dodaj &#124; nowy**.

## <a name="formatting-options"></a>Opcje formatowania

Aby ustawić opcje, takie jak wcięcia, nawias klamrowy uzupełniania i kolorowania formatowania, wpisz "C++ formatowania" w **szybkiego uruchamiania** okna. Visual Studio 2017 wersji 15.7 lub nowszym obsługuje ClangFormat. Można skonfigurować w [strony właściwości formatowania C/C++](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting) w obszarze **narzędzia &#124; opcje &#124; Edytor tekstu &#124; C/C++ &#124; formatowanie**.

![Opcje formatowania C++](media/cpp-formatting-options.png)

## <a name="intellisense"></a>IntelliSense

IntelliSense jest nazwą zestawu funkcji, które zawierają wbudowane informacje dotyczące elementów członkowskich, typy i przeciążenia funkcji. Na poniższej ilustracji przedstawiono listy członków listy rozwijanej jest wyświetlany podczas pisania. Klawisza tab do wprowadzania tekstu zaznaczonego elementu w pliku kodu.

![C&#43; &#43; element członkowski listy rozwijanej](../ide/media/vs2015_cpp_statement_completion.png "vs2015_cpp_statement_completion")

Aby uzyskać pełne informacje, zobacz [Intellisense dla programu Visual C++](/visualstudio/ide/visual-cpp-intellisense).

## <a name="insert-snippets"></a>Wstawienia fragmentów kodu

Fragment jest wstępnie zdefiniowanych fragment kodu źródłowego. Kliknij prawym przyciskiem myszy na pojedynczy punkt lub wstawić fragment lub przestrzenny fragment do zaznaczonego tekstu zaznaczonego tekstu. Na poniższej ilustracji przedstawiono trzy kroki otaczającego wybranego instrukcji z pętli for. Żółty prezentuje obrazie końcowym są edytowalne pola, które dostępu przy pomocy klawisza tab. Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).

![Visual C&#43; &#43; wstawić fragment porzucić&#45;dół](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

## <a name="add-class"></a>Dodaj klasę

Dodaj nową klasę z **projektu** menu za pomocą Kreatora klasy.

![Dodaj nową klasę w języku Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_class.png "vs2015_cpp_add_class")

Można także użyć Kreatora klasy, aby zmodyfikować lub zbadać istniejącej klasy.

![Visual C&#43; &#43; klasy kreatora](../ide/media/vs2015_cpp_class_wizard.png "vs2015_cpp_class_wizard")

Aby uzyskać więcej informacji, zobacz [Dodawanie funkcji z użyciem kreatorów kodu (C++)](../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="refactoring"></a>Refaktoryzacja

Refaktoryzacje są dostępne w menu kontekstowe akcji szybkiego lub klikając [żarówki](/visualstudio/ide/perform-quick-actions-with-light-bulbs) w edytorze.  Niektóre uwzględniono również w **Edytuj > Refaktoryzuj** menu.  Te funkcje obejmują:

* [Zmiana nazwy](refactoring/rename.md)
* [Wyodrębnianie funkcji](refactoring/extract-function.md)
* [Implementowanie czystych elementów wirtualnych](refactoring/implement-pure-virtuals.md)
* [Tworzenie deklaracji/definicji](refactoring/create-declaration-definition.md)
* [Przenoszenie definicji funkcji](refactoring/move-definition-location.md)
* [Konwertowanie na literał nieprzetworzonego ciągu](refactoring/convert-to-raw-string-literal.md)
* [Zmienianie podpisu](refactoring/change-signature.md)

## <a name="navigate-and-understand"></a>Nawigacji i zrozumienia

Visual C++ udostępnia wiele funkcji nawigacji kodu z innych języków. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie](/visualstudio/ide/navigating-code) i [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).

## <a name="quickinfo"></a>Skrócone informacje

Umieść wskaźnik myszy zmienną, aby wyświetlić informacje o typie.

![Visual C&#43;&#43; QuickInfo](../ide/media/vs2015_cpp_quickinfo.png "vs2015_cpp_quickInfo")

## <a name="open-document-navigate-to-header"></a>Otwórz dokument (Przejdź do nagłówka)

Kliknij prawym przyciskiem myszy nazwę nagłówka w `#include` dyrektywy i Otwórz plik nagłówka.

![Visual C&#43; &#43; opcji menu Otwórz dokument](../ide/media/vs2015_cpp_open_document.png "vs2015_cpp_open_document")

## <a name="peek-definition"></a>Definicji wglądu

Umieść kursor nad zmienną lub funkcję deklaracji, kliknij prawym przyciskiem myszy, następnie wybierz **definicji wglądu** Aby wyświetlić widok wbudowanego jego definicji. Aby uzyskać więcej informacji, zobacz [definicji wglądu (Alt + F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![Visual C&#43; &#43; wgląd definicji](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

## <a name="go-to-definition"></a>Przejdź do definicji

Umieść kursor nad zmienną lub funkcję deklaracji, kliknij prawym przyciskiem myszy, następnie wybierz **przejdź do definicji** otworzyć dokument, w którym zdefiniowana jest obiekt.

## <a name="view-call-hierarchy"></a>Wyświetlanie hierarchii wywołań

Kliknij prawym przyciskiem myszy każde wywołanie funkcji i wyświetlanie listy resursive wszystkie funkcje, które wywołuje i wszystkie funkcje, które wywołują go. Każda funkcja na liście można rozszerzać w taki sam sposób. Aby uzyskać więcej informacji, zobacz [hierarchii wywołań](/visualstudio/ide/reference/call-hierarchy).

![Visual C&#43; &#43; Hierarchia wywołań](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="toggle-header--code-file"></a>Przełącznik nagłówek / plik kodu

Kliknij prawym przyciskiem myszy i wybierz polecenie **przełącznik nagłówek / plik kodu** można przełączać się między plikiem nagłówka i jego plik skojarzony kod.

## <a name="outlining"></a>Tworzenie konspektu

Kliknij prawym przyciskiem myszy w dowolnym miejscu w pliku kodu źródłowego i wybierz polecenie **Tworzenie konspektu** można zwijać i rozwijać definicje i/lub niestandardowych regionów ułatwiające Przeglądaj tylko części planuje się. Aby uzyskać więcej informacji, zobacz [Tworzenie konspektu](/visualstudio/ide/outlining).

![Visual C&#43; &#43; zwijania](../ide/media/vs2015_cpp_outlining.png "vs2015_cpp_outlining")

## <a name="scrollbar-map-mode"></a>Tryb mapy paska przewijania

Pasek przewijania mapy tryb umożliwia szybko przewiń i przejdź do pliku kodu bez opuszczania faktycznie bieżącej lokalizacji. Lub kliknij w dowolnym miejscu na mapie kodu, aby przejść bezpośrednio do tej lokalizacji. Aby uzyskać więcej informacji, zobacz [porady: śledzenie kodu dostosowując pasek przewijania](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

![Kod mapy w języku Visual C&#43;&#43;](../ide/media/vs2015_cpp_code_map.png "vs2015_cpp_code_map")

## <a name="generate-graph-of-include-files"></a>Generowanie grafu plików dołączanych

Kliknij prawym przyciskiem myszy plik kodu w projekcie i wybierz polecenie **Generowanie grafu plików dołączanych** wyświetlić wykresu, którego pliki znajdują się w innych plików.

![Visual C&#43; &#43; grafu plików dołączanych](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="f1-help"></a>Pomoc F1

Umieść kursor na lub zaraz po dowolnego typu, słowo kluczowe lub funkcji, a następnie naciśnij klawisz F1, aby przejść bezpośrednio do odpowiednich temacie w witrynie docs.microsoft.com. F1 również działa na elementy na liście błędów i wiele okien dialogowych.

## <a name="quick-launch"></a>Szybkie uruchamianie

Aby łatwo przejść do okna ani narzędzia w programie Visual Studio, po prostu wpisz jego nazwę w oknie Szybkie uruchamianie w prawym górnym rogu interfejsu użytkownika. Na liście automatycznego uzupełniania spowoduje filtrowanie podczas pisania.

![Szybkie uruchamianie programu Visual Studio](../ide/media/vs2015_cpp_quick_launch.png "vs2015_cpp_quick_launch")
