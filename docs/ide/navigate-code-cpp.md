---
title: Nawigowanie C++ po kodzie w programie Visual Studio
description: Użyj różnych narzędzi w programie Visual Studio, aby poruszać się po bazie C++ kodu.
ms.date: 05/28/2019
ms.openlocfilehash: 0877fe64e913ab394d9605b9ff0b9825febca793
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446603"
---
# <a name="navigate-c-code-in-visual-studio"></a>Nawigowanie C++ po kodzie w programie Visual Studio

Program Visual Studio udostępnia zestaw narzędzi, za pomocą których można szybko i wydajnie poruszać się po bazie kodu.

## <a name="open-an-included-file"></a>Otwórz dołączony plik

Kliknij prawym przyciskiem myszy dyrektywę `#include`, a następnie wybierz pozycję **Przejdź do dokumentu**. Lub wybierz **klawisz F12** z kursorem nad tym wierszem, aby otworzyć plik.

![&#43; &#43; Opcja menu Przejdź do dokumentu](../ide/media/go-to-document.png "Przejdź do dokumentu")

## <a name="toggle-headercode-file"></a>Przełącz nagłówek/plik kodu

Można przełączać się między plikiem nagłówka i odpowiadającym mu plikiem źródłowym. Kliknij prawym przyciskiem myszy w dowolnym miejscu w pliku i wybierz polecenie **Przełącz nagłówek/plik kodu**. Możesz też wybrać **kombinację klawiszy CTRL + K**, **Ctrl + O**.

## <a name="go-to-definitiondeclaration"></a>Przejdź do definicji/deklaracji

Możesz przejść do definicji symbolu kodu, klikając go prawym przyciskiem myszy w edytorze, a następnie wybierając pozycję **Przejdź do definicji**lub wybierając **klawisz F12**. Możesz przejść do deklaracji podobnie, klikając prawym przyciskiem myszy, aby otworzyć menu kontekstowe lub wybierając **klawisze Ctrl + F12**.

![C&#43; &#43; przejdź do definicji](../ide/media/go-to-def.png "Przejdź do definicji")

## <a name="go-to"></a>Przejdź do

**Przejdź do** programu odwołuje się do zestawu funkcji nawigacji, które każdy z nich dostarcza określonego rodzaju wyniki na podstawie określonych filtrów. 

Możesz otworzyć polecenie **Przejdź do** za pomocą **kombinacji klawiszy CTRL +,** . Ta akcja powoduje utworzenie pola wyszukiwania dla edytowanego dokumentu.

![C&#43; &#43; przejdź do](../ide/media/go-to-cpp.png "Przejdź do")

**Przejdź do** obejmuje następujące filtry wyszukiwania:

- **Przejdź do wiersza** (**Ctrl + G**): szybko przejdź do innego wiersza w bieżącym dokumencie.
- **Przejdź do wszystkich** (**Ctrl +,** ) lub (**Ctrl + T**): wyniki wyszukiwania obejmują wszystkie poniższe elementy.
- **Przejdź do pliku** (**Ctrl 1, F**): Wyszukaj pliki w rozwiązaniu.
- **Przejdź do typu** (**Ctrl 1, T**): wyniki wyszukiwania obejmują:
  - Klasy, struktury i wyliczenia.
  - Interfejsy i Delegaty (tylko kod zarządzany).
- **Przejdź do elementu członkowskiego** (**Ctrl 1, M**): wyniki wyszukiwania obejmują:
  - Zmienne globalne i funkcje globalne.
  - Zmienne składowe klasy i funkcje członkowskie.
  - Stałe.
  - Elementy enum.
  - Właściwości i zdarzenia.
- **Przejdź do symbolu** (**Ctrl 1, S**): wyniki wyszukiwania obejmują:
  - Wyniki z przejdź do typów i przejdź do elementów członkowskich.
  - Wszystkie pozostałe C++ konstrukcje języka, w tym makra.

Po pierwszym wywołaniu **Przejdź do** pozycji **Ctrl +** , **Przejdź do wszystkich** jest aktywowany (brak filtrów dla wyników wyszukiwania). Możesz wybrać odpowiedni filtr, używając przycisków obok pola wyszukiwania. Konkretny filtr można wywołać przy użyciu odpowiedniego skrótu klawiaturowego. Spowoduje to otwarcie pola wyszukiwania **Przejdź do** z zaznaczonym filtrem. Wszystkie skróty klawiaturowe można konfigurować.

Aby zastosować filtr tekstu, uruchom zapytanie wyszukiwania z odpowiednim znakiem filtru, a następnie spacją. (**Przejdź do wiersza** może opcjonalnie pominąć miejsce). Dostępne są następujące filtry tekstu:

- Przejdź do wszystkiego: (brak filtru tekstu)
- Przejdź do numeru wiersza::
- Przejdź do pliku: f
- Przejdź do typu: t
- Przejdź do elementu członkowskiego: m
- Przejdź do symbolu: #

Poniższy przykład pokazuje wyniki operacji *Przejdź do plików* przy użyciu filtru "f":

![C&#43; &#43; przejdź do menu](../ide/media/vs2017-go-to-results.png "Przejdź do menu")

Aby wyświetlić listę filtrów tekstu, wpisz a? następuje spacja. Możesz również uzyskać dostęp do poleceń **Przejdź do** za pomocą menu **Edycja** . Jest to inny sposób, aby przypomnieć sobie, że główne **przejście na** skróty klawiaturowe.

![C&#43; &#43; przejdź do menu](../ide/media/go-to-menu-cpp.png "Przejdź do menu")

## <a name="find-or-find-in-files"></a>Znajdź lub Znajdź w plikach

Możesz uruchomić wyszukiwanie tekstu dla wszystkich elementów w rozwiązaniu za pomocą **Znajdź** (**Ctrl + F**) lub **Znajdź w plikach** (**Ctrl + Shift + F**).

**Znajdź** można ograniczyć do wyboru, bieżący dokument, wszystkie otwarte dokumenty, bieżący projekt lub całe rozwiązanie. Można używać wyrażeń regularnych i zwykłego tekstu. Wyróżnia również wszystkie dopasowania automatycznie w IDE.

![Znajdowanie&#43; &#43; w języku C](../ide/media/find-cpp.png "Znajdowanie")

**Znajdź w plikach** to bardziej wydajna wersja **wyszukiwania** , która wyświetla wyniki w oknie **Znajdź wyniki** . Możesz przeszukiwać zależności kodu zewnętrznego, filtrować według typów plików i nie tylko. 

![&#43; &#43;](../ide/media/find-in-files-cpp.png "Znajdź w plikach")

**Znajdź w plikach** wyniki można organizować w dwóch oknach. Wyniki można dołączać z wielu wyszukiwań jednocześnie. Wybierz wynik, aby przejść do tej lokalizacji w pliku.

![&#43; &#43;](../ide/media/vs2017-find-in-files-results.png "Znajdź w plikach")

Aby uzyskać więcej informacji, zobacz sekcję [Znajdź w plikach](/visualstudio/ide/find-in-files) w dokumentacji programu Visual Studio.

## <a name="find-all-references"></a>Znajdź wszystkie odwołania

Aby znaleźć wszystkie użycia symbolu w bazie kodu, umieść karetkę w lub tuż po symbolu, kliknij prawym przyciskiem myszy, a następnie wybierz pozycję **Znajdź wszystkie odwołania**. Można filtrować, sortować lub grupować wyniki na wiele różnych sposobów. Wyniki są wypełniane przyrostowo. Są one klasyfikowane jako operacje odczytu lub zapisu, które pomagają zobaczyć, co znajduje się w rozwiązaniu, w przeciwieństwie do nagłówków systemowych lub innych bibliotek.

![Znajdź&#43; &#43; wszystkie odwołania w języku C](../ide/media/find-all-references-results-cpp.png "Znajdź wszystkie odwołania")

Wyniki można grupować według następujących kategorii:

- Projekt, a następnie definicja
- Tylko definicja
- Definicja, a następnie projekt
- Definicja, a następnie ścieżka
- Definicja, projekt, a następnie ścieżka

#### <a name="filter-results"></a>Filtrowanie wyników

Aby filtrować wyniki, umieść kursor nad kolumną i wybierz ikonę filtrowania, która pojawia się. Można filtrować wyniki z pierwszej kolumny, aby ukryć elementy, takie jak odwołania do ciągów i komentarzy, które mogą nie być widoczne.

![Filtry&#43; &#43; języka C Znajdź wszystkie odwołania](../ide/media/find-all-references-filters-cpp.png "Filtry Znajdź wszystkie odwołania")

- **Potwierdzone wyniki**: rzeczywiste odwołania do kodu do wyszukiwanego symbolu. Na przykład wyszukiwanie funkcji składowej o nazwie `Size` zwraca wszystkie odwołania do `Size`, które pasują do zakresu klasy, która definiuje `Size`.

- **Niepotwierdzone wyniki**: ten filtr jest domyślnie wyłączony, ponieważ pokazuje symbole, których nazwy są zgodne, ale nie są rzeczywistymi odwołaniami do wyszukiwanego symbolu. Na przykład jeśli istnieją dwie klasy, które definiują funkcję członkowską o nazwie `Size`i uruchamiasz wyszukiwanie `Size` na podstawie odwołania z obiektu `Class1`, wszystkie odwołania do `Size` z `Class2` są wyświetlane jako niepotwierdzone.

- **Nieprzetworzone wyniki**: operacja **Znajdź wszystkie odwołania** może zająć trochę czasu w przypadku większych baz kodu, dlatego na liście wyników w tym miejscu są wyświetlane wyniki "nieprzetworzone". Nieprzetworzone wyniki pasują do nazwy symbolu, którego szukasz, ale nie zostały jeszcze potwierdzone jako rzeczywiste odwołania do kodu. Możesz włączyć ten filtr, aby szybciej uzyskiwać wyniki. Należy pamiętać, że niektóre wyniki mogą nie być rzeczywistymi odwołaniami.

#### <a name="sort-results"></a>Sortowanie wyników

Wyniki można sortować według dowolnej kolumny, zaznaczając tę kolumnę. Można zamienić między kolejnością rosnącą lub malejącą, zaznaczając ją ponownie.

## <a name="navigation-bar"></a>Pasek nawigacji

Można przejść do definicji typu w pliku lub do typu elementów członkowskich przy użyciu **paska nawigacyjnego** , który znajduje się powyżej okna edytora.

![Pasek&#43; &#43; nawigacyjny języka C](../ide/media/navbar-cpp.png "Pasek nawigacji")

## <a name="see-also"></a>Zobacz też

- [Odczytuj i rozumiej C++ kod](read-and-understand-code-cpp.md)</br>
- [Edytuj i Refaktoryzacja C++ kodu](read-and-understand-code-cpp.md)</br>
- [Współpracuj z Live Shareami dlaC++](live-share-cpp.md)
