---
title: Odczytywanie i rozumienie kodu języka C++ w programie Visual Studio
description: Użyj edytora kodu Języka C++ w programie Visual Studio, aby sformatować i zrozumieć kod.
ms.date: 05/28/2019
ms.openlocfilehash: 9ed0a20fb73e4cc976392bc5e5f698f9658a0b48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377301"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>Odczytywanie i rozumienie kodu języka C++ w programie Visual Studio

Edytor kodu Języka C++ i ide programu Visual Studio zapewniają wiele pomocy kodowania. Niektóre są unikatowe dla języka C++, a niektóre są zasadniczo takie same dla wszystkich języków programu Visual Studio. Aby uzyskać więcej informacji na temat udostępnionych funkcji, zobacz [Pisanie kodu w Edytorze kodu i tekstu](/visualstudio/ide/writing-code-in-the-code-and-text-editor).  

## <a name="colorization"></a>Kolorowania

Visual Studio koloruje elementy składni, aby odróżnić typy symboli, takich jak słowa kluczowe języka, nazwy typów, nazwy zmiennych, parametry funkcji, literały ciągów i tak dalej.

![Kolorowanie kodu](../ide/media/code-outline-colorization.png "Koloryzacja języka C++")

Nieużywane kodu (na przykład kod pod #if 0) jest bardziej wyblakłe w kolorze.

![Nieaktywny kod](../ide/media/inactive-code-cpp.png "Nieaktywny kod języka C++")

Kolory można dostosować, wpisując "Czcionki" w **trybie Szybkie uruchamianie,** a następnie wybierając **opcję Czcionki i kolory**. W oknie dialogowym **Czcionki i kolory** przewiń w dół do opcji C/C++, a następnie wybierz niestandardową czcionkę i/lub kolor.

## <a name="outlining"></a>Tworzenie konspektu

Kliknij prawym przyciskiem myszy w dowolnym miejscu pliku kodu źródłowego i wybierz pozycję **Konspekt,** aby zwinąć lub rozwinąć bloki kodu i/lub niestandardowe regiony, aby ułatwić przeglądanie tylko kodu, który Cię interesuje. Aby uzyskać więcej informacji, zobacz [Tworzenie przedstawiające](/visualstudio/ide/outlining).

![C&#43;&#43; nakreślenie](../ide/media/vs2015_cpp_outlining.png "Tworzenie konspektu")

Po umieszczeniu kursora przed nawiasem klamrowym ,,{" lub "}", edytor podświetla jego pasujący odpowiednik.

Inne opcje tworzenia zamieci znajdują się w obszarze **Edytuj** > **zamiejczenie** w menu głównym.

## <a name="line-numbers"></a>Numery wierszy

Numery wierszy można dodać do projektu, przechodząc do**Edytora** > tekstu**Opcje** >  **narzędzi** > Wszystkie języki**ogólne** lub**wyszukując** > "liczba wierszy" z **szybkim uruchomieniem (Ctrl + Q)**. Numery wierszy można ustawić tylko dla wszystkich języków lub dla określonych języków, w tym języka C++.

## <a name="scroll-and-zoom"></a>Przewijanie i powiększanie

Możesz powiększać lub pomniejszać w edytorze, naciskając klawisz **Ctrl** i przewijając za pomocą kółka myszy. Można również powiększyć, używając ustawienia powiększenia w lewym dolnym rogu.

![C&#43;&#43; kontrola powiększenia](../ide/media/zoom-control.png "Kontrolka powiększenia")

Tryb **mapy** paska przewijania umożliwia szybkie przewijanie i przeglądanie pliku kodu bez opuszczania bieżącej lokalizacji. Możesz kliknąć dowolne miejsce na mapie kodu, aby przejść bezpośrednio do tej lokalizacji.

![Mapa kodu w&#43;&#43;C](../ide/media/vs2015-cpp-code-map.png "Mapa kodu")

Aby włączyć **tryb mapy,** wpisz "mapa" w polu wyszukiwania **Szybkie uruchamianie** na głównym pasku narzędzi i wybierz pozycję **Użyj trybu przewijania mapy**. Aby uzyskać więcej informacji, zobacz [Jak: Śledzenie kodu przez dostosowanie paska przewijania](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

Gdy **tryb mapy** jest wyłączony, pasek przewijania nadal wyróżnia zmiany wprowadzone w pliku. Zielony oznacza zapisane zmiany, a żółty oznacza niezapisane zmiany.

## <a name="quick-info-and-parameter-info"></a>Szybkie informacje i informacje o parametrach

Umieść wskaźnik myszy na dowolnej zmiennej, funkcji lub innym symbolu, aby uzyskać informacje o niej, w tym deklarację i wszelkie komentarze, które znajdują się tuż przed nią.

::: moniker range="vs-2019"

![Szybkie informacje w&#43;&#43;C](../ide/media/quick-info-vs2019.png "Szybkie informacje")

Etykietka narzędzia **Szybkie informacje** ma łącze **Wyszukaj w trybie online.** Przejdź do widoku**Options** > **Edytor tekstu Edytor tekstu** >  **Narzędzia** > **C++,** > **View** aby określić dostawcę wyszukiwania.

Jeśli w kodzie występuje błąd, można na niego najechać kursorem, a **szybkie informacje** wyświetli komunikat o błędzie. Komunikat o błędzie można również znaleźć w oknie Lista błędów.

![Szybkie informacje o błędzie](../ide/media/quickinfo-on-error.png "Szybkie informacje o błędzie")

::: moniker-end

::: moniker range="<=vs-2017"

![Szybkie informacje w&#43;&#43;C](../ide/media/quick-info.png "Szybkie informacje")

Jeśli w kodzie występuje błąd, można na niego najechać kursorem, a **szybkie informacje** wyświetli komunikat o błędzie. Komunikat o błędzie można również znaleźć w oknie **Lista błędów.**

![Szybkie informacje o błędzie](../ide/media/quickinfo-on-error.png "Szybkie informacje o błędzie")

::: moniker-end

Podczas wywoływania **funkcji, Parametr Info** pokazuje typy parametrów i kolejność, w jakiej są oczekiwane.

![Informacje o parametrach w&#43;&#43;C](../ide/media/parameter-info.png "Informacje o parametrach")

## <a name="peek-definition"></a>Podejrzyj definicję

Umieść wskaźnik myszy na deklaracji zmiennej lub funkcji, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Peek Definition,** aby wyświetlić wbudowany widok jej definicji bez nawigowania z dala od bieżącej lokalizacji. Aby uzyskać więcej informacji, zobacz [Peek Definition (Alt+F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![C&#43;&#43; Definicja wglądu](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

## <a name="f1-help"></a>Pomoc F1

Umieść kursor na lub tuż po dowolnym typie, słowie kluczowym lub funkcji i naciśnij **klawisz F1,** aby przejść bezpośrednio do odpowiedniego tematu referencyjnego na docs.microsoft.com. **F1** działa również na elementy na liście błędów i w wielu oknach dialogowych.

## <a name="class-view"></a>Widok klas

**Widok klasy** wyświetla przeszukiwalny zestaw drzew wszystkich symboli kodu oraz ich zakres i hierarchie nadrzędne/podrzędne, uporządkowane na podstawie projektu. Widok **klasy** jest wyświetlany w **ustawieniach widoku klasy** (kliknij ikonę pola zębatego u góry okna).

![Widok klasy w&#43;&#43;C](../ide/media/class-view.png "Widok klas")

## <a name="generate-graph-of-include-files"></a>Generowanie wykresu plików dołączanych

Kliknij prawym przyciskiem myszy plik kodu w projekcie i wybierz pozycję **Generuj wykres dołączanych plików,** aby wyświetlić wykres, którego pliki są dołączane przez inne pliki.

![C&#43;&#43; wykres plików dołączanych](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>Wyświetlanie hierarchii połączeń

Kliknij prawym przyciskiem myszy dowolne wywołanie funkcji i wyświetl rekursywną listę wszystkich funkcji, które wywołuje, oraz wszystkie funkcje, które go wywołują. Każdą funkcję na liście można rozwinąć w ten sam sposób. Aby uzyskać więcej informacji, zobacz [Hierarchia połączeń](/visualstudio/ide/reference/call-hierarchy).

![C&#43;&#43; hierarchia połączeń](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>Zobacz też

[Kod edycji i refaktoryzacji (C++)](writing-and-refactoring-code-cpp.md)</br>
[Poruszanie się po bazie kodu języka C++ w programie Visual Studio](navigate-code-cpp.md)</br>
[Współpraca z udostępnianiem na żywo dla języka C++](live-share-cpp.md)
