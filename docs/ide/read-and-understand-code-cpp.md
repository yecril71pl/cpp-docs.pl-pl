---
title: Odczytywanie i poznawanie kodu C++ w programie Visual Studio
description: Użyj edytora kodu C++ w programie Visual Studio, aby sformatować i zrozumieć swój kod.
ms.date: 05/28/2019
ms.openlocfilehash: 3da4224592cabd11e449fa4be395eba046c0e554
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686144"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>Odczytywanie i poznawanie kodu C++ w programie Visual Studio

Edytor kodu C++ i środowisko IDE programu Visual Studio zapewniają wiele narzędzi do kodowania. Niektóre z nich są unikatowe dla języka C++, a niektóre są zasadniczo takie same dla wszystkich języków programu Visual Studio. Aby uzyskać więcej informacji o funkcjach udostępnionych, zobacz [pisanie kodu w edytorze kodu i tekstu](/visualstudio/ide/writing-code-in-the-code-and-text-editor).  

## <a name="colorization"></a>Kolorowanie

Program Visual Studio koloruje elementy składni w celu rozróżnienia typów symboli, takich jak słowa kluczowe języka, nazwy typów, nazwy zmiennych, parametry funkcji, literały ciągów i tak dalej.

![Kolorowanie kodu](../ide/media/code-outline-colorization.png "Kolorowanie języka C++")

Nieużywany kod (taki jak kod w #if 0) jest bardziej wyblakły kolorem.

![Nieaktywny kod](../ide/media/inactive-code-cpp.png "Nieaktywny kod języka C++")

Kolory można dostosować, wpisując "Fonts" ( **Szybkie uruchamianie**), a następnie wybierając **czcionkę i kolory**. W oknie dialogowym **czcionki i kolory** przewiń w dół do opcji C/C++, a następnie wybierz niestandardową czcionkę i/lub kolor.

## <a name="outlining"></a>Tworzenie konspektu

Kliknij prawym przyciskiem myszy w dowolnym miejscu w pliku kodu źródłowego i wybierz opcję **Konspekt** , aby zwinąć lub rozwinąć bloki kodu i/lub regiony niestandardowe, aby ułatwić przeglądanie tylko kodu, który Cię interesuje. Aby uzyskać więcej informacji, zobacz [Tworzenie konspektu](/visualstudio/ide/outlining).

![Konspekt języka C&#43;&#43; ](../ide/media/vs2015_cpp_outlining.png "Tworzenie konspektu")

Gdy umieścisz kursor przed nawiasem klamrowym, "{" lub "}", Edytor wyróżnia swój pasujący odpowiednik.

Inne opcje tworzenia konspektu znajdują się w obszarze **Edytuj**  >  **Konspekt** w menu głównym.

## <a name="line-numbers"></a>Numery wierszy

Możesz dodać numery wierszy do projektu, przechodząc do opcji **Narzędzia**  >  **Options**  >  **Edytor tekstu**  >  **wszystkie języki**  >  **Ogólne** lub wyszukując "wiersz num" przy użyciu **szybkiego uruchamiania (Ctrl + Q)**. Numery wierszy można ustawić dla wszystkich języków lub tylko dla określonych języków, w tym C++.

## <a name="scroll-and-zoom"></a>Przewiń i Powiększ

Możesz powiększyć lub pomniejszyć w edytorze, naciskając klawisz **Ctrl** i przewijając kółkiem myszy. Możesz również powiększać, używając ustawienia powiększenia w lewym dolnym rogu.

![Kontrolka powiększenia języka C&#43;&#43; ](../ide/media/zoom-control.png "Kontrolka powiększenia")

**Tryb mapy** ScrollBar umożliwia szybkie przewijanie i przeglądanie pliku kodu bez opuszczania bieżącej lokalizacji. Możesz kliknąć w dowolnym miejscu mapy kodu, aby przejść bezpośrednio do tej lokalizacji.

![Mapa kodu w języku C&#43;&#43;](../ide/media/vs2015-cpp-code-map.png "Mapa kodu")

Aby włączyć **tryb mapowania**, wpisz "map" w polu wyszukiwania **szybkiego uruchamiania** na głównym pasku narzędzi i wybierz opcję **Użyj trybu Scroll map**. Aby uzyskać więcej informacji, zobacz [jak: śledzić kod przez dostosowanie paska przewijania](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

Gdy **tryb mapy** jest wyłączony, pasek przewijania nadal wyróżnia zmiany wprowadzone w pliku. Zielony oznacza zapisane zmiany i żółty wskazuje niezapisane zmiany.

## <a name="quick-info-and-parameter-info"></a>Szybkie informacje i informacje o parametrach

Umieść kursor nad dowolną zmienną, funkcją lub innym symbolem, aby uzyskać informacje na jego temat, w tym deklarację i wszelkie komentarze, które znajdują się przed nim.

::: moniker range="vs-2019"

![Zrzut ekranu przedstawiający etykietka Szybka podpowiedź w programie Visual Studio 2019.](../ide/media/quick-info-vs2019.png "Szybkie informacje")

Etykietka narzędzia **szybkie informacje** zawiera link **wyszukiwania online** . Przejdź do pozycji **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  **C++**  >  **Widok** , aby określić dostawcę wyszukiwania.

Jeśli wystąpi błąd w kodzie, możesz umieścić wskaźnik myszy nad nim, a w oknie **szybkie informacje** zostanie wyświetlony komunikat o błędzie. Komunikat o błędzie można również znaleźć w oknie Lista błędów.

![Szybkie informacje o błędzie](../ide/media/quickinfo-on-error.png "Szybkie informacje o błędzie")

::: moniker-end

::: moniker range="<=vs-2017"

![Zrzut ekranu przedstawiający etykietka Szybka podpowiedź w programie Visual Studio 2017.](../ide/media/quick-info.png "Szybkie informacje")

Jeśli wystąpi błąd w kodzie, możesz umieścić wskaźnik myszy nad nim, a w oknie **szybkie informacje** zostanie wyświetlony komunikat o błędzie. Komunikat o błędzie można również znaleźć w oknie **Lista błędów** .

![Szybkie informacje o błędzie](../ide/media/quickinfo-on-error.png "Szybkie informacje o błędzie")

::: moniker-end

Gdy wywołujesz funkcję, **Informacje o parametrach** przedstawiają typy parametrów i kolejność, w jakiej są oczekiwane.

![Informacje o parametrach w języku C&#43;&#43;](../ide/media/parameter-info.png "Informacje o parametrach")

## <a name="peek-definition"></a>Podejrzyj definicję

Umieść kursor nad deklaracją zmiennej lub funkcji, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **wgląd do definicji** , aby wyświetlić wbudowany widok jego definicji bez nawigowania w bieżącej lokalizacji. Aby uzyskać więcej informacji, zobacz [wgląd do definicji (Alt + F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![Definicja wglądu w&#43;&#43; języka C](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

## <a name="f1-help"></a>Pomoc F1

Umieść kursor na lub zaraz po dowolnym typie, słowie kluczowym lub funkcji, a następnie naciśnij klawisz **F1** , aby przejść bezpośrednio do odpowiedniego tematu referencyjnego w witrynie docs.Microsoft.com. **F1** działa również w przypadku elementów na liście błędów i w wielu oknach dialogowych.

## <a name="class-view"></a>Widok klas

**Widok klasy** Wyświetla zestaw drzew z możliwością wyszukiwania dla wszystkich symboli kodu oraz ich zakres i hierarchie nadrzędny/podrzędny, zorganizowane na podstawie projektu. Można skonfigurować, jakie **Widok klasy** są wyświetlane z poziomu **Widok klasy ustawień** (kliknij ikonę koła zębatego w górnej części okna).

![Widok klasy w języku C&#43;&#43;](../ide/media/class-view.png "Widok klas")

## <a name="generate-graph-of-include-files"></a>Generowanie grafu plików dołączanych

Kliknij prawym przyciskiem myszy plik kodu w projekcie i wybierz polecenie **Generuj Graf plików dołączanych** , aby zobaczyć Graf, które pliki są dołączone przez inne pliki.

![&#43;&#43; grafu plików dołączanych](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>Wyświetl hierarchię wywołań

Kliknij prawym przyciskiem myszy każde wywołanie funkcji i Wyświetl listę cykliczną wszystkich funkcji, które wywołuje, oraz wszystkie funkcje, które je wywołują. Każda funkcja na liście może być rozwinięta w ten sam sposób. Aby uzyskać więcej informacji, zobacz temat [Hierarchia wywołań](/visualstudio/ide/reference/call-hierarchy).

![Hierarchia wywołań języka C&#43;&#43; ](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>Zobacz też

[Edytuj i Refaktoryzacja kodu (C++)](writing-and-refactoring-code-cpp.md)</br>
[Nawigowanie po bazie kodu C++ w programie Visual Studio](navigate-code-cpp.md)</br>
[Współpraca z Live Shareami dla języka C++](live-share-cpp.md)
