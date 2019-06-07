---
title: Edytować i refaktoryzować C++ kodu w programie Visual Studio
description: Użyj C++ edytora kodu w programie Visual Studio do formatu, nawigowanie, zrozumieć i Refaktoryzuj swój kod.
ms.date: 05/31/2019
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
ms.openlocfilehash: d4a74608a95df0fdd461f55d26fee97332a66aa8
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66741627"
---
# <a name="edit-and-refactor-c-code-in-visual-studio"></a>Edytować i refaktoryzować C++ kodu w programie Visual Studio

Program Visual Studio udostępnia kilka narzędzi, które pomagają, dzięki czemu można tworzyć, edytować i Refaktoryzuj swój kod.

##  <a name="intellisense"></a>IntelliSense

Funkcja IntelliSense jest zaawansowane uzupełnianie narzędzie kodu sugerujące, symbole i fragmenty kodu dla Ciebie podczas wpisywania. C++IntelliSense w programie Visual Studio działa w czasie rzeczywistym, analizowanie Twojej bazy kodu w przypadku aktualizowania go, a także zalecenia. Podczas pisania większej liczby znaków, lista wyników zalecane zawęża obszar.

![C&#43; &#43; elementu członkowskiego listy rozwijanej](../ide/media/cpp-statement-completion.png)

Niektóre symbole są pomijane automatycznie ułatwiające Zawęź wyniki. Na przykład podczas uzyskiwania dostępu do członków obiektu klasy z poza klasy, nie będzie można zobaczyć prywatnych elementów członkowskich domyślnie oraz chronionych elementów członkowskich (Jeśli nie jesteś w kontekście klasy podrzędnej). Można dostosować, filtrowanie, korzystając z przycisków w dolnej części.

Po wybraniu symbolu z listy rozwijanej możesz automatycznego uzupełniania za pomocą **kartę**, **Enter**, lub jednego z innych znaków zatwierdzania (domyślnie: {} [ ](). ,:; +-* / % & | ^! =? @#\). Aby dodać lub usunąć znaki z tej listy, wyszukaj "IntelliSense" w **Szybkie uruchamianie** (Ctrl + Q) i wybierz polecenie **Edytor tekstu > C /C++ > Zaawansowane** opcji. **Znaki zatwierdzania List składowych** opcja umożliwia dostosowywanie listy zmian ma.

**Tryb filtrowania listy składowych** opcja określa, jakiego rodzaju sugestie dotyczące automatycznego uzupełniania IntelliSense, zostanie wyświetlony. Domyślnie jest ustawiona **Fuzzy**. W polu wyszukiwania rozmytego, jeśli symbol o nazwie *MyAwesomeClass*, można wpisać "MAC" i znaleźć klasy w Twoje sugestie funkcji autouzupełniania. Algorytm rozmyte Ustawia minimalny próg, które symbole muszą spełnić, aby widoczne na liście. **Inteligentne** filtrowania wyświetlane są wszystkie symbole zawierające podciągi, które odpowiadają, co to są typizowane. **Prefiks** filtrowania wyszukiwania ciągów, które zaczynają się od co to są typizowane.

Aby uzyskać więcej informacji na temat C++ funkcja IntelliSense, zobacz [Visual C++ IntelliSense](/visualstudio/ide/visual-cpp-intellisense) i [Konfiguruj C++ projektu dla technologii IntelliSense](/visualstudio/ide/visual-cpp-intellisense-configuration).

## <a name="intellicode"></a>IntelliCode

Rozszerzenie IntelliCode jest wspierane przez Sztuczną inteligencję IntelliSense. Umieszcza najprawdopodobniej kandydat na początku listy uzupełnianej. Zalecenia dotyczące IntelliCode są oparte na tysiące projektów typu open source w serwisie GitHub każdej z ponad 100 gwiazdek. W połączeniu z kontekstem Twojego kodu, na liście uzupełniania jest dostosowane do wspierania typowe rozwiązania.

Podczas zapisywania C++, pomoże IntelliCode, gdy przy użyciu popularnych bibliotek, takich jak C++ biblioteki standardowej. Zapewnienie najbardziej przydatne zalecenia, używany jest kontekst kodu. W poniższym przykładzie `size` funkcja członkowska jest często stosowana w przypadku `sort` funkcji, więc go jest udostępniane na początku listy wyników.

![C&#43; &#43; IntelliCode](../ide/media/intellicode-cpp.png " C++ IntelliCode")

::: moniker range="vs-2019"

W programie Visual Studio 2019 r, jest dostępny jako składnik opcjonalny w IntelliCode  **C++ programowanie aplikacji klasycznych** obciążenia. Aby upewnić się, że IntelliCode jest aktywny dla C++, przejdź do **narzędzia** > **opcje** > **IntelliCode**  >  **Ogólne** i ustaw  **C++ modelu bazowego** do **włączone**.

::: moniker-end

::: moniker range="vs-2017"

W programie Visual Studio 2017 rozszerzenie IntelliCode jest dostępna jako rozszerzenie programu Visual Studio Marketplace.

::: moniker-end

## <a name="predictive-intellisense-experimental"></a>Predictive IntelliSense (wersja eksperymentalna)

**Predictive IntelliSense** jest eksperymentalną funkcję, która używa świadomości kontekstowych na ograniczenie liczby wyniki wyświetlane na liście rozwijanej funkcji IntelliSense. Algorytm ma zastosowanie typu pasującego tak, aby pokazywał tylko tych wyników, które pasuje do oczekiwanego typu. W najprostszym przypadku, jeśli wpiszesz `int x =` i wywołania funkcji IntelliSense listy rozwijanej, zostanie wyświetlony tylko liczby całkowite lub funkcji zwracających liczb całkowitych. Ta funkcja jest wyłączona domyślnie ponieważ jest nadal w fazie projektowania. Działa najlepiej z symbole globalne; Funkcje Członkowskie nie są jeszcze obsługiwane. Można włączyć go, wpisując "Predykcyjnego" **Szybkie uruchamianie** lub przechodząc do **narzędzia** > **opcje** > **edytora tekstów**  >  **C /C++**  > **eksperymentalne** > **Włączanie Predictive IntelliSense**.

Aby zastąpić **Predictive IntelliSense** i Pokaż dłuższą listę, naciśnij klawisz **Ctrl + J**. Jeśli **Predictive IntelliSense** jest włączona, wywołując **Ctrl + J** usuwa filtr predykcyjne. Naciśnięcie klawisza **Ctrl + J** ponownie usuwa filtr ułatwień dostępu z listy członków powoduje stosownych. ([] +) Przycisku w obszarze technologii IntelliSense, lista rozwijana działa tak samo jak **Ctrl + J**. Umieść kursor nad przycisk aby wyświetlić informacje o co jest pokazywane.

![C&#43;&#43; Predictive IntelliSense](../ide/media/predictive-intellisense-cpp.png "Predictive IntelliSense")

Poprzedni zrzut ekranu przedstawia kilka przycisków w obszarze listy rozwijanej. Włącz te filtry IntelliSense dla różnych rodzajów wyniki:

- Stałe i zmienne
- Funkcje
- Types
- Makra
- Wyliczenia
- Namespaces

Przycisk jest wyświetlana tylko wtedy, gdy jest istotny dla bieżącej sesji IntelliSense. Zwykle nie ma wszystkie przyciski w tym samym czasie.

## <a name="template-intellisense"></a>Szablon funkcji IntelliSense

Podczas karetka znajduje się wewnątrz definicji szablonu **szablonu paska** pojawi się, który umożliwia podanie Przykładowe argumenty szablonu dla technologii IntelliSense. 

![C&#43; &#43; wystąpień istniejących technologii IntelliSense Show szablonu](../ide/media/template-intellisense-cpp-1.png "wystąpień istniejących technologii IntelliSense Show szablonu")

Kliknij przycisk **<T>** ikony Rozwiń/Zwiń **szablonu paska**. Kliknij ikonę ołówka, lub kliknij dwukrotnie **pasek szablonu** otworzyć **Edytuj** okna. 

![C&#43; &#43; IntelliSense szablonu](../ide/media/template-intellisense-cpp-3.png "szablonu funkcji IntelliSense")

Modyfikacje wprowadzone w oknie są stosowane bezpośrednio do kodu źródłowego, dzięki czemu można zobaczyć efekty w czasie rzeczywistym. 

Na pasku szablonu może automatycznie wypełniać kandydatów w oparciu wystąpień w kodzie. Kliknij pozycję **Dodaj wszystkie istniejące wystąpień** umożliwia wyświetlenie listy wszystkich konkretnych argumentów, które zostały użyte do utworzenia wystąpienia szablonu w całej bazy kodu.

![C&#43; &#43; IntelliSense szablonu listy wyników](../ide/media/template-intellisense-cpp-2.png "IntelliSense szablonu listy wyników")

Okno w dolnej części edytora pokazuje, gdzie znaleziono każdego wystąpienia i jakie są jej argumenty.

![C&#43; &#43; szablonu funkcji IntelliSense podczas tworzenia wystąpienia mapy](../ide/media/template-intellisense-cpp-4.png "szablonu funkcji IntelliSense podczas tworzenia wystąpienia mapy")

**Pasek szablonu** informacji jest traktowany jako specyficzne dla użytkownika. Ona znajduje się w folderze .vs i nie jest zobowiązana do kontroli źródła.

##  <a name="error-squiggles-and-quick-fixes"></a>Zygzaki sygnalizujące błędy i szybkich poprawek

Edytor wykrywa problemy z kodem, doda kolorowe faliste linie w obszarze problemu. Czerwone faliste linie wskazują kod, który nie będzie skompilować. Zielony faliste linie wskazują inne rodzaje problemów, które mogą być potencjalnie poważny. Możesz otworzyć **lista błędów** okna, aby uzyskać więcej informacji o problemach.

Dla niektórych rodzajów błędów, jak również jako typowych wzorców i Edytor zaoferuje **Quick Fix** w formie żarówki, która pojawia się, gdy kursor wężyk. Kliknij strzałkę w dół, aby zobaczyć sugestie. 

W poniższym przykładzie `vector` została zadeklarowana, ale nie odnaleziono definicji, więc edytor oferuje uwzględnić plik nagłówka konieczne:

![C&#43; &#43; szybkiej poprawki](../ide/media/quick-fix-for-header-cpp.png " C++ Quick Fix")

Edytor oferuje kilka możliwości refaktoryzacji szybkich poprawek. Na przykład jeśli zadeklarować klasy w pliku nagłówkowym programu Visual Studio oferuje do tworzenia definicji dla niego w pliku .cpp oddzielne. 

![C&#43; &#43; szybkiej poprawki](../ide/media/quick-fix.png " C++ Quick Fix")

## <a name="change-tracking"></a>Śledzenie zmian

Po każdym wprowadzeniu zmiany w pliku żółty pasek jest wyświetlany po lewej stronie, aby wskazać, że niezapisane zmiany zostały wprowadzone. Zapisując plik, pasek zmieni kolor na zielony. Paski zielony i żółtych zostaną zachowane, tak długo, jak dokument jest otwarty w edytorze. Reprezentują one zmiany wprowadzone od czasu ostatniego otwarcia dokumentu.

![C&#43; &#43; śledzenie zmian](../ide/media/change-tracking-cpp.png "śledzenie zmian")

## <a name="move-code"></a>Przenieś kod

Przenoszenie linii kodu i zmniejszana, wybierając je, trzymając naciśnięty klawisz Alt, a następnie naciśnij klawisz **/dół** klawiszy strzałek.

##  <a name="insert-snippets"></a>Wstawianie fragmentów kodu

Fragment kodu jest wstępnie zdefiniowanych fragmentem kodu źródłowego. Kliknij prawym przyciskiem myszy pojedynczy punkt lub przy wybranym tekście, wstawić framgent kodu lub przestrzenny, zaznaczony tekst fragmentem kodu. Na poniższej ilustracji przedstawiono trzy kroki, aby otoczyć wybranego sprawozdania z pętli for. Żółty światła w obrazie końcowym są edytowalne, do których dostęp przy użyciu klawisza tab. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).

![C&#43;&#43; Insert Snippet Drop&#45;down](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

##  <a name="add-class"></a>Dodaj klasę

Dodaj nową klasę z **projektu** menu lub z menu kontekstowego w **Eksploratora rozwiązań**:

![Dodaj nową klasę w języku C&#43;&#43;](../ide/media/vs2017-add-class.png "vs2015_cpp_add_class")

Można także użyć Kreatora klasy, aby zmodyfikować lub zbadać istniejącej klasy.

![C&#43; &#43; klasy Kreatora](../ide/media/vs2017-class-wizard.png)

Aby uzyskać więcej informacji, zobacz [Dodawanie funkcji za pomocą kreatorów kodu (C++)](../ide/adding-functionality-with-code-wizards-cpp.md).

##  <a name="refactoring"></a>Refaktoryzacja

Refaktoryzacje są dostępne z menu kontekstowego szybkich działań lub klikając [żarówki](/visualstudio/ide/perform-quick-actions-with-light-bulbs) w edytorze.  Niektóre również znajdują się w **Edytuj > Refaktoryzuj** menu.  Te funkcje obejmują:

* [Zmiana nazwy](refactoring/rename.md)
* [Wyodrębnianie funkcji](refactoring/extract-function.md)
* [Implementowanie czystych elementów wirtualnych](refactoring/implement-pure-virtuals.md)
* [Tworzenie deklaracji/definicji](refactoring/create-declaration-definition.md)
* [Przenoszenie definicji funkcji](refactoring/move-definition-location.md)
* [Konwertowanie na literał nieprzetworzonego ciągu](refactoring/convert-to-raw-string-literal.md)
* [Zmienianie podpisu](refactoring/change-signature.md)

## <a name="code-style-enforcement-with-clangformat-and-editorconfig"></a>Wymuszanie stylu kodu za pomocą narzędzia ClangFormat i wtyczki EditorConfig

Visual Studio 2017 i nowszym, który jest dostarczany z wbudowaną obsługą [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html), popularnych narzędzi Formatowanie kodu dla C++ oparte na Clang/maszyny wirtualnej niskiego poziomu. Wpisz "ClangFormat" w [Szybkie uruchamianie](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) można ustawić go do korzystania z jednego z tych typowych formatów:

- MASZYNY WIRTUALNEJ NISKIEGO POZIOMU
- Google
- Chrom
- Mozilla
- Aparatu WebKit
- Visual Studio

Można również dołączyć własnego pliku clang format lub _clang-format, aby zastosować niestandardowe reguły do wszystkich plikach kodu na tym samym poziomie lub niższy.

Pliki są łatwo możliwego do udostępnienia, za pomocą kontroli źródła, dzięki czemu można wymuszaniu Konwencji kodowania w całym zespole deweloperów całego.

![C&#43; &#43; Clang Format](../ide/media/clang-format-cpp.png "Clang formatu")

Obsługuje również w programie Visual Studio 2017 i nowszym [EditorConfig](https://editorconfig.org/), która działa w podobny sposób. Narzędzie ClangFormat, jednak ma więcej opcji stylu niż EditorConfig, w tym zasady, które są specyficzne dla C++. Za pomocą **EditorConfig**, możesz utworzyć **.editorconfig** pliki i umieszczenie ich w różnych folderach z Twojej bazy kodu w celu określenia style kodu dla tych folderów i ich podfolderów. **.Editorconfig** plik zastępuje inne **.editorconfig** pliki foldery nadrzędne i zastępuje wszelkie ustawienia formatowania skonfigurowane za pomocą **narzędzia**  >  **Opcje**. Można ustawić reguły dla karty, a miejsca do magazynowania, wielkość wcięcia i nie tylko. Aby uzyskać więcej informacji, zobacz [tworzenie przenośnych, niestandardowych ustawień edytora za pomocą wtyczki EditorConfig](/visualstudio/ide/create-portable-custom-editor-options).

## <a name="other-formatting-options"></a>Inne opcje formatowania

**Szybkie uruchamianie** pole wyszukiwania umożliwia szybkie można znaleźć ustawienia lub narzędzia. Znajduje się w menu głównym. Po prostu zacznij wpisywać i automatyczne uzupełnianie listy będzie filtrować wyniki.

![Szybkie uruchamianie programu Visual Studio](../ide/media/vs2015_cpp_quick_launch.png "szybkiego uruchamiania")

Aby ustawić opcje, takie jak wcięcia, uzupełnianie nawiasów i kolorowanie formatowania, wpisz "C++ formatowania" w **Szybkie uruchamianie** okna.

![Opcje formatowania dla języka C++](media/cpp-formatting-options.png)

Inne opcje formatowania znajdują się w obszarze **Edytuj** > **zaawansowane** w menu głównym.

![C++Zaawansowane opcje edytowania](media/edit-advanced-cpp.png)

Opcje umożliwia włączenie i skonfigurowanie C++-określonych funkcji edycji znajdują się w obszarze **narzędzia** > **opcje** > **edytora tekstów**  >  **C /C++** . Po wybraniu opcji chcesz ustawić, można uzyskać pomoc, naciskając klawisz **F1** gdy okno jest w trybie koncentracji uwagi. Dla kodu ogólne opcje formatowania, wpisz `Editor C++` do **Szybkie uruchamianie**.

![Program Visual Studio Tools > Opcje](../ide/media/tools-options.png "Opcje edytora")

Funkcji eksperymentalnych, które mogą lub nie mogą zostać zawarte w przyszłych wersjach programu Visual Studio, znajdują się w [eksperymentalne C++ edytora tekstów](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental) okna dialogowego. W programie Visual Studio 2017 i nowszych możesz włączyć **Predictive IntelliSense** w tym oknie dialogowym.

## <a name="see-also"></a>Zobacz też

[Dokładnie zapoznaj się C++ kodu](read-and-understand-code-cpp.md)</br>
[Przejdź z C++ kodu bazowego w programie Visual Studio](navigate-code-cpp.md)</br>
[Współpracuj z udziału na żywoC++](live-share-cpp.md)