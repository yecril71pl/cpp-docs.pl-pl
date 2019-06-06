---
title: Dokładnie zapoznaj się C++ kodu w programie Visual Studio
description: Użyj C++ edytora kodu w programie Visual Studio do formatowania i rozumienie kodu.
ms.date: 05/28/2019
ms.openlocfilehash: c5e4d7f3e53ef37649e3635d11cf99b10cb8a7ee
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66743382"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>Dokładnie zapoznaj się C++ kodu w programie Visual Studio

C++ Edytora kodu i środowiska IDE programu Visual Studio zapewnia wiele pomoce kodowania. Niektóre są unikatowe dla języka C++, a niektóre są zasadniczo takie same dla wszystkich języków Visual Studio. Aby uzyskać więcej informacji o funkcjach udostępnionych, zobacz [pisanie kodu w edytorze tekstu i kodu](/visualstudio/ide/writing-code-in-the-code-and-text-editor).  

## <a name="colorization"></a>Kolorowanie

Program Visual Studio kolorowania składni elementów do rozróżniania między typami symbole, takie jak słowa kluczowe języka, nazwy typów, nazw zmiennych, parametrów funkcji, literały ciągów i tak dalej.

![Kolorowaniu kodu](../ide/media/code-outline-colorization.png " C++ kolorowania")

 Nieużywany kod (na przykład kod #if 0) jest bardziej pojawił się kolorów.

 ![Nieaktywny kod](../ide/media/inactive-code-cpp.png " C++ nieaktywnego kodu")

Można dostosować kolory, wpisując "Czcionki" **Szybkie uruchamianie**, a następnie wybierając **czcionki i kolory**. W **czcionki i kolory** okna dialogowego przewiń w dół do C /C++ opcje, a następnie wybierz polecenie niestandardowej czcionki i/lub kolor.

## <a name="outlining"></a>Tworzenie konspektu

Kliknij prawym przyciskiem myszy w dowolnym miejscu w pliku kodu źródłowego, a następnie wybierz **konspekt** Aby zwinąć lub rozwinąć bloków kodu i/lub niestandardowych regionów, aby ułatwić przeglądanie kodu, Cię interesuje. Aby uzyskać więcej informacji, zobacz [konspekt](/visualstudio/ide/outlining).

![C&#43; &#43; konspekt](../ide/media/vs2015_cpp_outlining.png "konspekt")

Gdy umieścisz kursor przed nawias klamrowy "{" lub "}", Edytor wyróżnia jego odpowiednika dopasowania.

Inne opcje konspektu znajdują się w obszarze **Edytuj** > **konspekt** w menu głównym.

## <a name="line-numbers"></a>Numery wierszy

Numery wierszy można dodać do projektu, przechodząc do **narzędzia** > **opcje** > **edytora tekstów** > **wszystkie Języki** > **ogólne** lub wyszukując "numerowanie wierszy" za pomocą **szybkiego uruchamiania (Ctrl + Q)** . Numery wierszy można ustawić dla wszystkich języków lub dla określonych języków, w tym C++.

## <a name="scroll-and-zoom"></a>Przewijanie i powiększanie

Można powiększyć lub w edytorze, naciskając klawisz **Ctrl** klucz i przewijanie przy użyciu kółka myszy. Ponadto można powiększyć przy użyciu ustawienie powiększenia w lewym dolnym rogu.

![C&#43; &#43; powiększenie](../ide/media/zoom-control.png "powiększenia")

Pasek przewijania **tryb mapy** pozwala szybko przewiń i przeglądać pliku z kodem bez opuszczania Twojej bieżącej lokalizacji. Możesz kliknąć dowolne miejsce na mapie kodu, aby przejść bezpośrednio do tej lokalizacji.

![Mapa w języku C kodu&#43;&#43;](../ide/media/vs2015-cpp-code-map.png "Mapa kodu")

Aby włączyć **tryb mapy**, wpisz "mapy" **Szybkie uruchamianie** polu wyszukiwania na głównym pasku narzędzi i wybierz polecenie **trybie przewijania mapy**. Aby uzyskać więcej informacji, zobacz [jak: Śledzenie kodu przez dostosowania paska przewijania](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

Gdy **tryb mapy** jest wyłączone, pasek przewijania wyróżnia nadal zmiany wprowadzone w pliku. Zielony oznacza zapisane zmiany i żółty oznacza niezapisane zmiany.

## <a name="quick-info-and-parameter-info"></a>Szybkie informacje i informacje o parametrach

Umieść kursor nad dowolnej zmiennej, funkcji lub innych symboli, aby uzyskać informacje o tym, w tym deklaracji i wszelkie komentarze, znajdujących się po prostu poprzedzającym go.

::: moniker range="vs-2019"

![Szybkie informacje w języku C&#43;&#43;](../ide/media/quick-info-vs2019.png "szybkie informacje")

**Quick Info** etykietki narzędzia ma **Wyszukaj Online** łącza. Przejdź do **narzędzia** > **opcje** > **edytora tekstów**  >  **C++**  >  **Widoku** Aby określić dostawcę wyszukiwania. 

Jeśli w kodzie występuje błąd, możesz umieścić kursor go i **Quick Info** wyświetli komunikat o błędzie. Komunikat o błędzie może również znaleźć w oknie Lista błędów.

![Szybkie informacje na temat błędu](../ide/media/quickinfo-on-error.png "szybkie informacje na temat błędu")

::: moniker-end

::: moniker range="<=vs-2017"

![Szybkie informacje w języku C&#43;&#43;](../ide/media/quick-info.png "szybkie informacje")

Jeśli w kodzie występuje błąd, możesz umieścić kursor go i **Quick Info** wyświetli komunikat o błędzie. Możesz również znaleźć komunikat o błędzie w **lista błędów** okna.

![Szybkie informacje na temat błędu](../ide/media/quickinfo-on-error.png "szybkie informacje na temat błędu")

::: moniker-end

Po wywołaniu funkcji, **Parameter Info** Wyświetla typy parametrów i kolejności, w którym są oczekiwane.

![Informacje o parametrach w C&#43;&#43;](../ide/media/parameter-info.png "informacje o parametrach")

## <a name="peek-definition"></a>Zobacz definicję

Umieść kursor nad zmienną lub funkcję deklaracji, kliknij prawym przyciskiem myszy, następnie wybierz **Peek Definition** Aby wyświetlić widok wbudowane jego definicja bez konieczności opuszczania Twojej bieżącej lokalizacji. Aby uzyskać więcej informacji, zobacz [zobacz definicję (Alt + F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![C&#43;&#43; Peek Definition](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

##  <a name="f1-help"></a>Pomoc F1

Umieść kursor na lub po prostu po typu, słowo kluczowe lub funkcji i naciśnij klawisz **F1** przechodzić bezpośrednio do temat istotne informacje w witrynie docs.microsoft.com. **F1** działa również na elementy na liście błędów, a wiele okien dialogowych.

## <a name="class-view"></a>Widok klas

**Widok klas** Wyświetla można wyszukiwać zestaw drzew wszystkie symbole kodu i ich zakres i nadrzędny/podrzędny hierarchie organizowane w poszczególnych projektów. Można skonfigurować, jakie **Widok klas** Wyświetla z **widok klasy: ustawienia** (kliknij ikonę Pole koła zębatego w górnej części okna).

![Widok w języku C klasy&#43;&#43;](../ide/media/class-view.png "Widok klas")

## <a name="generate-graph-of-include-files"></a>Generowanie grafu plików dołączanych

Kliknij prawym przyciskiem myszy plik kodu w projekcie, a następnie wybierz **Generowanie grafu plików dołączanych** wyświetlić wykres, które pliki zostały dołączone przez inne pliki.

![C&#43; &#43; grafu plików dołączanych](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>Pokaż hierarchię wywołań

Kliknij prawym przyciskiem myszy na każde wywołanie funkcji i wyświetlanie listy wszystkich funkcji wywoływanych przez niego, a wszystkie funkcje, które ją wywołują cykliczne. Każda funkcja na liście można rozwijać w taki sam sposób. Aby uzyskać więcej informacji, zobacz [hierarchię wywołań,](/visualstudio/ide/reference/call-hierarchy).

![C&#43;&#43; Call Hierarchy](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>Zobacz też

[Edytuj i refaktoryzacji kodu (C++)](writing-and-refactoring-code-cpp.md)</br>
[Przejdź z C++ kodu bazowego w programie Visual Studio](navigate-code-cpp.md)</br>
[Współpracuj z udziału na żywoC++](live-share-cpp.md)
