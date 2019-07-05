---
title: Przejdź C++ kodu w programie Visual Studio
description: Do poruszania się za pomocą różnych narzędzi w programie Visual Studio z C++ bazy kodu.
ms.date: 05/28/2019
ms.openlocfilehash: c2d3a1aa4a26cb820ff4a1e87d6eae88b1b8e739
ms.sourcegitcommit: 96f48079cdc402e4c2c1578d1f1eed4846a484dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2019
ms.locfileid: "67576526"
---
# <a name="navigate-c-code-in-visual-studio"></a>Przejdź C++ kodu w programie Visual Studio

Program Visual Studio udostępnia zestaw narzędzi, które służą do poruszania się Twojej bazy kodu, szybkie i skuteczne.

## <a name="open-an-included-file"></a>Otwórz dołączonego pliku

Kliknij prawym przyciskiem myszy `#include` dyrektywy i wybierz pozycję **przejdź do dokumentu**. Lub wybierz **F12** kursor znajduje się za pośrednictwem tego wiersza, aby otworzyć plik.

![C&#43; &#43; opcji menu przejść do dokumentu](../ide/media/go-to-document.png "przejdź do dokumentu")

## <a name="toggle-headercode-file"></a>Przełącz nagłówek/plik kodu

Możesz przełączać się między plik nagłówkowy i jego odpowiadający mu plik źródłowy. Kliknij prawym przyciskiem myszy w dowolnym miejscu w pliku i wybierz **Przełącz nagłówek/plik kodu**. Lub możesz wybrać **Ctrl + K**, **Ctrl + O**.

## <a name="go-to-definitiondeclaration"></a>Przejdź do deklaracji/definicji

Możesz przejść do definicji symbolu kodu przez kliknięcie prawym przyciskiem myszy w edytorze i wybierając polecenie **przejdź do definicji**, lub wybierając **F12**. Możesz przejść do deklaracji podobnie, klikając prawym przyciskiem myszy, aby otworzyć menu kontekstowe, lub wybierając **Ctrl + F12**.

![C&#43; &#43; przejdź do definicji](../ide/media/go-to-def.png "przejdź do definicji")

## <a name="go-to"></a>Przejdź do

**Przejdź do** odwołuje się do zestawu nawigacji funkcje, których każda oferuje określonego rodzaju wynik na podstawie filtrów można określić. 

Możesz otworzyć **przejdź do** z **Ctrl +** . Ta akcja tworzy pole wyszukiwania przez dokument, który jest edytowany.

![C&#43; &#43; przejdź do](../ide/media/go-to-cpp.png "przejdź do")

**Przejdź do** obejmuje te filtry wyszukiwania:

- **Go To Line** (**Ctrl+G**): Szybko przechodzić do różnych wiersza w bieżącym dokumencie.
- **Przejdź do wszystkich** (**Ctrl +** ) lub (**klawisze Ctrl + T**): Wyniki wyszukiwania zawierają wszystko, co następuje.
- **Przejdź do pliku** (**Ctrl 1, F**): Wyszukaj pliki w rozwiązaniu.
- **Przejdź do typu** (**Ctrl 1, T**): Wyniki wyszukiwania zawierają:
  - Klasy, struktury i wyliczeń.
  - Interfejsów i delegatów (tylko kod zarządzany).
- **Przejdź do elementu członkowskiego** (**Ctrl 1, M**): Wyniki wyszukiwania zawierają:
  - Zmienne globalne i funkcje globalne.
  - Zmienne składowe klasy i funkcje Członkowskie.
  - Stałe.
  - Elementy typu wyliczeniowego.
  - Właściwości i zdarzenia.
- **Go To Symbol** (**Ctrl 1, S**): Wyniki wyszukiwania zawierają:
  - Wyniki z z rzeczywistym użyciem dla typów, a następnie przejść do elementów członkowskich.
  - Wszystkie pozostałe C++ konstrukcji języka, takich jak makra.

Po pierwszym wywołaniu **przejdź do** z **Ctrl +** , **przejdź do wszystkich** jest aktywowana (bez filtrów w wynikach wyszukiwania). Możesz wybrać filtr, który ma, korzystając z przycisków obok pola wyszukiwania. Można wywoływać za pomocą jego odpowiedniego skrótu klawiaturowego określonego filtru. Wykonując tak otwiera **przejdź do** pole wyszukiwania za pomocą tego filtru wstępnie wybrane. Wszystkie skróty klawiaturowe są konfigurowane.

Aby zastosować filtr tekstu, należy uruchomić z zapytaniem wyszukiwania przy użyciu odpowiedniego znaku filtru następuje spacja. (**Przejdź do wiersza** Opcjonalnie można pominąć przestrzeni.) Dostępne są następujące filtry tekstu:

- Przejdź do wszystkich: (bez filtrowania tekst)
- Przejdź do numeru wiersza::
- Przejdź do pliku: f
- Przejdź do typu: t
- Przejdź do elementu członkowskiego: m
- Przejdź do symbolu: #

W poniższym przykładzie przedstawiono wyniki z *przejdź do plików* operację, używając filtra "f":

![C&#43; &#43; przejdź do Menu](../ide/media/vs2017-go-to-results.png "przejdź do Menu")

Aby wyświetlić listę filtrów tekstu, wpisz? następuje spacja. Możesz także będą mogli **przejdź do** polecenia za pomocą **Edytuj** menu. Jest to inny sposób, aby przypominać sobie głównego **przejdź do** skróty klawiaturowe.

![C&#43; &#43; przejdź do Menu](../ide/media/go-to-menu-cpp.png "przejdź do Menu")

## <a name="find-or-find-in-files"></a>Znajdź lub Znajdź w plikach

Można uruchomić wyszukiwanie na podstawie tekstu dla wszystkich elementów w rozwiązaniu z **znaleźć** (**Ctrl + F**) lub **Znajdź w plikach** (**Ctrl + Shift + F**).

**Znajdź** może zostać obniżone do wyboru, bieżącego dokumentu, wszystkie otwarte dokumenty, bieżący projekt lub całe rozwiązanie. Można użyć wyrażeń regularnych i zwykłego tekstu. To również wyodrębnić wszystkie dopasowania, automatycznie w środowisku IDE.

![C&#43; &#43; znaleźć](../ide/media/find-cpp.png "Znajdź")

**Znajdź w plikach** jest nieco bardziej wydajne **znaleźć** , wyświetla wyniki w **Find Results** okna. Można przeszukiwać zależności kodu zewnętrznego, filtrować według typów plików i nie tylko. 

![C&#43; &#43; Znajdź w plikach](../ide/media/find-in-files-cpp.png "Znajdź w plikach")

Możesz organizować **Znajdź w plikach** skutkuje dwa okna. Możesz dołączyć wyniki wyszukiwania w wielu ze sobą. Wybierz wynik, aby przejść do tej lokalizacji w pliku.

![C&#43; &#43; Znajdź w plikach](../ide/media/vs2017-find-in-files-results.png "Znajdź w plikach")

Aby uzyskać więcej informacji, zobacz [Znajdź w plikach](/visualstudio/ide/find-in-files) w dokumentacji programu Visual Studio.

## <a name="find-all-references"></a>Znajdź wszystkie odwołania

Aby znaleźć wszystkie użycia symbolu w bazie kodu, umieść karetkę na lub po symbolu, kliknij prawym przyciskiem myszy, a następnie wybierz **Znajdź wszystkie odwołania**. Można filtrować, sortować lub grupowanie wyników na wiele różnych sposobów. Wyniki wypełnić przyrostowo. Są one klasyfikowane operacja odczytu lub zapisu zobaczyć, co znajduje się w rozwiązania w przeciwieństwie do nagłówków systemu lub inne biblioteki.

![C&#43; &#43; Znajdź wszystkie odwołania](../ide/media/find-all-references-results-cpp.png "Znajdź wszystkie odwołania")

Grupowanie wyników według następujących kategorii:

- Projekt, a następnie definicja
- Tylko definicja
- Definicja, a następnie projekt
- Definicja, a następnie ścieżka
- Definicja, projekt, a następnie ścieżka

 #### <a name="filter-results"></a>Filtrowanie wyników

Aby filtrować wyniki, umieść kursor nad kolumny i wybierz ikonę filtrowania, które się pojawi. Możesz filtrować wyniki z pierwszej kolumny, aby ukryć elementów, takich jak parametry i komentarz odwołań, które możesz nie chcieć wyświetlić.

![C&#43; &#43; Znajdź wszystkie odwołania filtry](../ide/media/find-all-references-filters-cpp.png "Znajdź wszystkie odwołania filtry")

- **Potwierdzone wyniki**: Rzeczywisty kod odwołania do symbolu wyszukane. Na przykład wyszukiwanie funkcją składową o nazwie `Size` zwraca wszystkie odwołania do `Size` zgodnych zakres klasy, która definiuje `Size`.

- **Wyniki można użyć niepotwierdzonego**: Ten filtr jest domyślnie wyłączona, ponieważ dzięki niemu symbole, którego nazwa jest zgodna, ale nie rzeczywiste odwołania do symboli, którego szukasz. Na przykład w przypadku dwóch klas, w których każdy definiuje funkcja elementu członkowskiego, wywoływana `Size`, i uruchom wyszukiwanie `Size` na odwołanie z obiektu `Class1`, wszelkie odwołania do `Size` z `Class2` pojawiają się, jak można użyć niepotwierdzonego.

- **Nieprzetworzone wyniki**: **Znajdź wszystkie odwołania** operacji może potrwać do wykonania na większych bazach kodu, więc lista wyników zawiera "nieprzetworzone" wyniki w tym miejscu. Nieprzetworzone wyniki pasować do nazwy symbolu wyszukane, ale jeszcze nie został potwierdzony jako odniesienia rzeczywisty kod. Można włączyć ten filtr, aby uzyskać szybsze wyniki. Po prostu należy pamiętać, że niektóre wyniki mogą być rzeczywista odwołania.

 #### <a name="sort-results"></a>Sortowanie wyników

Wyniki można sortować według dowolnej kolumny, wybierając tej kolumny. Można przełączać się między kolejności rosnącej lub malejącej, wybierając kolumnę.

## <a name="navigation-bar"></a>Pasek nawigacji

Możesz przejść do definicji typu w pliku lub na typ elementów członkowskich, za pomocą **pasek nawigacyjny** to nad oknem edytora.

![C&#43; &#43; pasek nawigacyjny](../ide/media/navbar-cpp.png "pasek nawigacyjny")

## <a name="see-also"></a>Zobacz także

- [Dokładnie zapoznaj się C++ kodu](read-and-understand-code-cpp.md)</br>
- [Edytować i refaktoryzować C++ kodu](read-and-understand-code-cpp.md)</br>
- [Współpracuj z udziału na żywoC++](live-share-cpp.md)
