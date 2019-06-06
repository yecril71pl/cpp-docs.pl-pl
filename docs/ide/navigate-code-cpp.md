---
title: Przejdź C++ kodu w programie Visual Studio
description: Do poruszania się za pomocą różnych narzędzi w programie Visual Studio z C++ bazy kodu.
ms.date: 05/28/2019
ms.openlocfilehash: 5f01307cc82fb1e61ba6fd0c922ea376279fba8b
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66743385"
---
# <a name="navigate-c-code-in-visual-studio"></a>Przejdź C++ kodu w programie Visual Studio

Program Visual Studio udostępnia zestaw narzędzi, które umożliwiają nawigowanie po Twojej bazy kodu, szybkie i skuteczne.

## <a name="open-an-included-file"></a>Otwórz dołączonego pliku

Kliknij prawym przyciskiem myszy `#include` dyrektywy i wybierz polecenie **przejdź do dokumentu**, lub naciśnij **F12** kursor znajduje się za pośrednictwem tego wiersza, aby otworzyć plik.

![C&#43; &#43; opcji menu przejść do dokumentu](../ide/media/go-to-document.png "przejdź do dokumentu")

## <a name="toggle-headercode-file"></a>Przełącz nagłówek/plik kodu

Możesz przełączać się między plik nagłówkowy i odpowiadający mu plik źródłowy, klikając prawym przyciskiem myszy w dowolnym miejscu w pliku i wybierając pozycję **Przełącz nagłówek / plik kodu** lub naciskając **Ctrl + K, Ctrl + O**.

## <a name="go-to-definitiondeclaration"></a>Przejdź do deklaracji/definicji

Możesz przejść do definicji symbolu kodu przez kliknięcie prawym przyciskiem myszy w edytorze, a następnie wybierając **przejdź do definicji**, lub naciskając **F12**. Możesz przejść do deklaracji podobnie z menu kontekstowego kliknij prawym przyciskiem myszy lub naciskając **Ctrl + F12**.

![C&#43; &#43; przejdź do definicji](../ide/media/go-to-def.png "przejdź do definicji")

## <a name="go-to"></a>Przejdź do

**Przejdź do** odwołuje się do zestawu nawigacji funkcje, których każda oferuje określonego rodzaju wynik na podstawie filtrów można określić. 

Możesz otworzyć **przejdź do** z **Ctrl +,** . Spowoduje to utworzenie pola wyszukiwania w dokumencie, który edytujesz.

![C&#43; &#43; przejdź do](../ide/media/go-to-cpp.png "przejdź do")

**Przejdź do** obejmuje te filtry wyszukiwania:

- **Przejdź do wiersza (Ctrl + G)** : szybko przechodzić do różnych wiersza w bieżącym dokumencie
- **Przejdź do wszystkich (Ctrl +,)** lub **(Ctrl + T)** : wyniki wyszukiwania zawierają wszystko, co jest poniżej
- **Przejdź do pliku (Ctrl-1, F)** : Wyszukaj pliki w rozwiązaniu
- **Przejdź do typu (Ctrl-1, T)** : wyniki wyszukiwania zawierają:
  - Klasy, struktury, wyliczenia
  - Interfejsów i delegatów (tylko kod zarządzany)
- **Przejdź do elementu członkowskiego (Ctrl-1, M)** : wyniki wyszukiwania zawierają:
  - Zmienne globalne i funkcje globalne
  - Zmienne składowe klasy i funkcje Członkowskie
  - Stałe
  - Elementy typu wyliczeniowego
  - Właściwości i zdarzenia
- **Przejdź do symbolu (Ctrl-1, S)** : wyniki wyszukiwania zawierają:
  - Wyniki z z rzeczywistym użyciem dla typów, a następnie przejść do elementów członkowskich
  - Wszystkie pozostałe C++ konstrukcji językowych, w tym makra

Po pierwszym wywołaniu **przejdź do** z **Ctrl +** , **przejdź do wszystkich** jest aktywowana (bez filtrów w wynikach wyszukiwania). Następnie możesz wybrać żądany filtr, korzystając z przycisków w polu tekstowym wyszukiwania. Można wywoływać za pomocą jego odpowiedniego skrótu klawiaturowego określonego filtru. Wykonując tak otwiera **przejdź do** pole wyszukiwania za pomocą tego filtru wstępnie wybrana. Wszystkie skróty klawiaturowe są konfigurowane.

Aby zastosować filtr tekstu, należy uruchomić z zapytaniem wyszukiwania przy użyciu odpowiedniego znaku filtru następuje spacja. (**Przejdź do wiersza** Opcjonalnie można pominąć przestrzeni.) Filtry tekstu dostępne są to:

- Przejdź do wszystkich: (bez filtrowania tekst)
- Przejdź do numeru wiersza::
- Przejdź do pliku: f
- Przejdź do typu: t
- Przejdź do elementu członkowskiego: m
- Przejdź do symbolu: #

W poniższym przykładzie przedstawiono wyniki z *przejdź do plików* operację, używając filtra 'f':

![C&#43; &#43; przejdź do Menu](../ide/media/vs2017-go-to-results.png "przejdź do Menu")

Aby wyświetlić listę filtrów tekstu, wpisz? następuje spacja. Można również przejść **przejdź do** polecenia za pomocą **Edytuj** menu. Jest to pamiętanie głównego przejdź do skróty klawiaturowe w inny sposób.

![C&#43; &#43; przejdź do Menu](../ide/media/go-to-menu-cpp.png "przejdź do Menu")

## <a name="find--find-in-files"></a>Znajdź / Znajdź w plikach

Można uruchomić wyszukiwanie na podstawie tekstu dla wszystkich elementów w rozwiązaniu z **Znajdź (Ctrl + F)** lub **Znajdź w plikach (Ctrl + Shift + F)** .

Znajdź może należeć do wyboru, bieżącego dokumentu, wszystkie otwarte dokumenty, bieżący projekt lub całe rozwiązanie zakresu. Można użyć wyrażeń regularnych, jak również w postaci zwykłego tekstu. To również wyodrębnić wszystkie dopasowania, automatycznie w środowisku IDE.

![C&#43; &#43; znaleźć](../ide/media/find-cpp.png "Znajdź")

**Znajdź w plikach** jest nieco bardziej wydajne **znaleźć** , wyświetla wyniki w **Find Results** okna. Można przeszukiwać zależności kodu zewnętrznego, filtrować według typów plików i nie tylko. 

![C&#43; &#43; Znajdź w plikach](../ide/media/find-in-files-cpp.png "Znajdź w plikach")

Możesz organizować **Znajdź w plikach** skutkuje dwa okna. Możesz dołączyć wyniki wyszukiwania w wielu ze sobą. Kliknij wynik, aby przejść do tej lokalizacji w pliku.

![C&#43; &#43; Znajdź w plikach](../ide/media/vs2017-find-in-files-results.png "Znajdź w plikach")

Aby uzyskać więcej informacji, zobacz [Znajdź w plikach](/visualstudio/ide/find-in-files) w dokumentacji programu Visual Studio.

## <a name="find-all-references"></a>Znajdź wszystkie odwołania

Aby znaleźć wszystkie użycia symbolu w bazie kodu, umieść karetkę na lub po symbolu, a następnie kliknij prawym przyciskiem myszy i wybierz **Znajdź wszystkie odwołania**. Można filtrować, sortować lub grupowanie wyników na wiele różnych sposobów. Wyniki wypełnić przyrostowo. Zalicza się, ponieważ operacja odczytu lub zapisu zobaczyć, co znajduje się w rozwiązania w przeciwieństwie do nagłówków systemu lub inne biblioteki.

![C&#43; &#43; Znajdź wszystkie odwołania](../ide/media/find-all-references-results-cpp.png "Znajdź wszystkie odwołania")

Grupowanie wyników według następujących kategorii:

- Projekt, a następnie definicja
- Tylko definicja
- Definicja, a następnie projekt
- Definicja, a następnie ścieżka
- Definicja, projekt, a następnie ścieżka

 #### <a name="filter-results"></a>Filtrowanie wyników

Do filtrowania wyników, umieść kursor nad kolumny i kliknij ikonę filtrowania, które się pojawi. Możesz filtrować wyniki z pierwszej kolumny, aby ukryć elementów, takich jak parametry i komentarz odwołań, które możesz nie chcieć wyświetlić.

![C&#43; &#43; Znajdź wszystkie odwołania filtry](../ide/media/find-all-references-filters-cpp.png "Znajdź wszystkie odwołania filtry")

- **Potwierdzone wyniki**: Rzeczywisty kod odwołania do symbolu wyszukane. Na przykład wyszukiwanie funkcją składową o nazwie `Size` będzie zwracać wszystkie odwołania do `Size` zgodnych zakres Definiowanie klasy `Size`.

- **Wyniki można użyć niepotwierdzonego**: Ten filtr jest domyślnie wyłączona, ponieważ dzięki niemu symbole, którego nazwa jest zgodna, ale nie są rzeczywiste odwołania do symboli, które są wyszukiwane. Na przykład w przypadku dwóch klas, w których każdy definiuje funkcja elementu członkowskiego, wywoływana `Size`, i uruchom wyszukiwanie `Size` na odwołanie z obiektu `Class1`, wszelkie odwołania do `Size` z `Class2` pojawiają się, jak można użyć niepotwierdzonego.

- **Nieprzetworzone wyniki**: **Znajdź wszystkie odwołania** operacji może potrwać do wykonania na większych bazach kodu, więc lista wyników zawiera "nieprzetworzone" wyniki w tym miejscu. Nieprzetworzone wyniki pasować do nazwy symbolu wyszukane, ale nie został potwierdzony jako odniesienia rzeczywisty kod. Można włączyć ten filtr, aby uzyskać szybsze wyniki. Po prostu należy pamiętać, że niektóre wyniki mogą być rzeczywista odwołania.

 #### <a name="sort-results"></a>Sortowanie wyników

Wyniki można sortować według dowolnej kolumny, klikając w tej kolumnie. Można przełączać się między rosnąco/malejąco zamówienia, klikając kolumnę.

## <a name="navigation-bar"></a>Pasek nawigacji

Możesz przejść do definicji typu w pliku lub na typ elementów członkowskich, za pomocą **pasek nawigacyjny** to nad oknem edytora.

![C&#43; &#43; pasek nawigacyjny](../ide/media/navbar-cpp.png "pasek nawigacyjny")

## <a name="see-also"></a>Zobacz też

[Dokładnie zapoznaj się C++ kodu](read-and-understand-code-cpp.md)</br>
[Edytować i refaktoryzować C++ kodu](read-and-understand-code-cpp.md)</br>
[Współpracuj z udziału na żywoC++](live-share-cpp.md)
