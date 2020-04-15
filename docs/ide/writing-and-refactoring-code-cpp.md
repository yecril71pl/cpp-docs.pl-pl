---
title: Edytowanie i refaktoryzator kodu C++ w programie Visual Studio
description: Użyj edytora kodu Języka C++ w programie Visual Studio, aby sformatować, nawigować, zrozumieć i refaktoryzować kod.
ms.date: 05/31/2019
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
ms.topic: overview
ms.openlocfilehash: 070c79e02f6e05adeda5f17a0dde02afdf22703b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353740"
---
# <a name="edit-and-refactor-c-code-in-visual-studio"></a>Edytowanie i refaktoryzator kodu C++ w programie Visual Studio

Visual Studio udostępnia kilka narzędzi ułatwiających pisanie, edytowanie i refaktoryzowanie kodu.

## <a name="intellisense"></a>IntelliSense

IntelliSense to potężne narzędzie do uzupełniania kodu, które sugeruje symbole i fragmenty kodu podczas pisania. C++ IntelliSense w programie Visual Studio działa w czasie rzeczywistym, analizując swoją bazę kodu podczas aktualizowania go i dostarczanie zaleceń. W miarę wpisania większej liczby znaków lista zalecanych wyników zawęża się.

![C&#43;&#43; lista członków rozwijana](../ide/media/cpp-statement-completion.png)

Niektóre symbole są pomijane automatycznie, aby zawęzić wyniki. Na przykład podczas uzyskiwania dostępu do członków obiektu klasy spoza klasy, nie będzie można zobaczyć prywatnych elementów członkowskich domyślnie lub chronionych elementów członkowskich (jeśli nie jesteś w kontekście klasy podrzędnej). Filtrowanie można dostosować za pomocą przycisków u dołu.

Po wybraniu symbolu z listy rozwijanej można go automatycznie uzupełnić za pomocą **klawisza Tab**, `{ } [ ] ( ) . , : ; + - * / % & | ^ ! = ? @ # \` **Enter**lub jednego z pozostałych znaków zatwierdzania (domyślnie: ). Aby dodać lub usunąć znaki z tej listy, wyszukaj hasło "IntelliSense" w **trybie Szybkie uruchamianie** (Ctrl + Q) i wybierz opcję **Edytor tekstu > C/C++ > Opcja Zaawansowane.** Opcja **Znaki zatwierdzania listy elementów członkowskich** umożliwia dostosowanie listy za pomocą żądanych zmian.

Opcja **Tryb filtrowania listy członków** określa, jakie rodzaje sugestii autouzupełniania IntelliSense są widoczne. Domyślnie jest ustawiona na **Rozmyte**. W wyszukiwaniu rozmytym, jeśli masz symbol o nazwie *MyAwesomeClass*, możesz wpisać "MAC" i znaleźć klasę w sugestiach autouzupełniania. Algorytm rozmyte ustawia minimalny próg, który symbole muszą spełniać, aby pokazać się na liście. **Inteligentne** filtrowanie wyświetla wszystkie symbole zawierające podciągi, które pasują do wpisanego tekstu. **Filtrowanie prefiksów** wyszukuje ciągi, które zaczynają się od wpisywanych.

Aby uzyskać więcej informacji na temat programu IntelliSense języka C++ , zobacz [Visual C++ IntelliSense](/visualstudio/ide/visual-cpp-intellisense) i [Konfigurowanie projektu C++ dla programu IntelliSense](/visualstudio/ide/visual-cpp-intellisense-configuration).

## <a name="intellicode"></a>IntelliCode

IntelliCode jest intelliSense wspomagany przez AI. To stawia najbardziej prawdopodobne kandydata na górze listy ukończenia. Zalecenia IntelliCode są oparte na tysiącach projektów open source na GitHub każdy z ponad 100 gwiazdek. W połączeniu z kontekstem kodu lista uzupełnień jest dostosowana do promowania typowych praktyk.

Podczas pisania języka C++, IntelliCode pomoże podczas korzystania z popularnych bibliotek, takich jak Biblioteka standardowa Języka C++. Kontekst kodu jest używany do zapewnienia najbardziej przydatnych zaleceń pierwszy. W poniższym przykładzie `size` funkcja elementu członkowskiego `sort` jest często używana z funkcją, więc jest rzut y na początku listy wyników.

![C&#43;&#43; IntelliCode](../ide/media/intellicode-cpp.png "C++ IntelliCode")

::: moniker range="vs-2019"

W programie Visual Studio 2019 intellicode jest dostępny jako opcjonalny składnik w obciążeniu **deweloperów pulpitu C++.** Aby upewnić się, że intellicode jest aktywny dla języka C++, przejdź do**opcji** >  **narzędzia** > **IntelliCode** > **General** i ustaw model podstawowy **Języka C++** na **Włączone**.

::: moniker-end

::: moniker range="vs-2017"

W programie Visual Studio 2017 intellicode jest dostępny jako rozszerzenie w portalu Visual Studio Marketplace.

::: moniker-end

## <a name="predictive-intellisense-experimental"></a>Predictive IntelliSense (eksperymentalny)

**Predictive IntelliSense** to eksperymentalna funkcja, która wykorzystuje świadomość kontekstową do ograniczenia liczby wyników wyświetlanych na liście rozwijanej IntelliSense. Algorytm stosuje dopasowywanie typów, dzięki czemu pokazuje tylko te wyniki, które odpowiadają typowi oczekiwanemu. W najprostszym przypadku, jeśli `int x =` wpiszesz i wywołasz listy rozwijanej IntelliSense, zobaczysz tylko liczby całkowite lub funkcje zwracające liczby całkowite. Ta funkcja jest domyślnie wyłączona, ponieważ jest nadal w fazie rozwoju. Najlepiej współpracuje z symbolami globalnymi; funkcje członkowskie nie są jeszcze obsługiwane. Możesz go włączyć, wpisując "Predictive" w **trybie Szybkie uruchamianie** lub przechodząc do **programu Tools** > **Options** > **Text Editor** > **C/C++** > **Experimental** > **Enable Predictive IntelliSense**.

Aby zastąpić **predictive IntelliSense** i wyświetlić dłuższą listę, naciśnij **klawisze Ctrl + J**. Jeśli **predictive IntelliSense** jest włączony, wywołanie **ctrl + J** usuwa filtr Predykcyjne. Naciśnięcie **klawisza Ctrl + J** ponownie powoduje usunięcie filtru ułatwień dostępu z wyników listy elementów członkowskich, w stosownych przypadkach. Przycisk ([+]) na liście rozwijanej IntelliSense działa tak samo, jak **Ctrl + J**. Umieść wskaźnik myszy na przycisku, aby wyświetlić informacje o tym, co jest wyświetlane.

![C&#43;&#43; Predictive IntelliSense](../ide/media/predictive-intellisense-cpp.png "Predykcyjne IntelliSense")

Na poprzednim zrzucie ekranu przedstawiono kilka przycisków pod listą rozwijanej. Umożliwiają one filtry IntelliSense dla różnych rodzajów wyników:

- Zmienne i stałe
- Funkcje
- Types
- Makra
- Wyliczenia
- Namespaces

Przycisk jest wyświetlany tylko wtedy, gdy jest odpowiedni dla bieżącej sesji IntelliSense. Zazwyczaj nie są widoczne wszystkie przyciski w tym samym czasie.

## <a name="template-intellisense"></a>Szablon IntelliSense

Gdy daszek znajduje się wewnątrz definicji szablonu, pojawia się **pasek szablonu,** który umożliwia podanie przykładowych argumentów szablonu dla intellisense.

![Szablon&#43;&#43; C IntelliSense Pokaż istniejące wystąpienia](../ide/media/template-intellisense-cpp-1.png "Szablon IntelliSense Pokaż istniejące wystąpienia")

Kliknij ikonę ** \<T>,** aby rozwinąć/zwinąć **pasek szablonu**. Kliknij ikonę ołówka lub kliknij dwukrotnie **pasek szablonu,** aby otworzyć okno **Edycja.**

![Szablon&#43;&#43; C IntelliSense](../ide/media/template-intellisense-cpp-3.png "Szablon IntelliSense")

Zmiany wprowadzone w oknie są stosowane bezpośrednio do kodu źródłowego, dzięki czemu można zobaczyć efekty w czasie rzeczywistym.

Pasek szablonów może automatycznie wypełniać kandydatów na podstawie wystąpienia w kodzie. Kliknij **dodaj wszystkie istniejące wystąpienia,** aby wyświetlić listę wszystkich konkretnych argumentów, które zostały użyte do wystąpienia szablonu w całej bazie kodu.

![Lista wyników&#43;&#43; szablonu C IntelliSense](../ide/media/template-intellisense-cpp-2.png "Lista wyników intellisense szablonu")

Okno w dolnej części edytora pokazuje, gdzie znaleziono każde wystąpienie i jakie były jego argumenty.

![Mapa wystąpienia&#43;&#43; szablonu&#43;&#43; języka IntelliSense](../ide/media/template-intellisense-cpp-4.png "Mapa wystąpienia usługi IntelliSense szablonu")

Informacje o **pasku szablonu** są traktowane jako specyficzne dla użytkownika. Jest on przechowywany w folderze .vs i nie jest zobowiązana do kontroli źródła.

## <a name="error-squiggles-and-quick-fixes"></a>Błędy squiggles i szybkie poprawki

Jeśli edytor wykryje problemy z kodem, doda kolorowe falisty pod problemem. Czerwone squiggles wskazują kod, który nie będzie kompilować. Zielone faliszki wskazują na inne rodzaje problemów, które mogą być nadal potencjalnie poważne. Okno Lista **błędów** można otworzyć, aby uzyskać więcej informacji na temat problemów.

W przypadku niektórych rodzajów błędów, a także typowych wzorców kodowania, edytor zaoferuje **szybką poprawkę** w postaci żarówki, która pojawia się po najechaniu kursorem na faliste. Kliknij strzałkę w dół, aby wyświetlić sugestie.

W poniższym przykładzie został zadeklarowany, `vector` ale nie znaleziono definicji, więc edytor oferuje dołączenie niezbędnego pliku nagłówka:

![C&#43;&#43; szybka poprawka](../ide/media/quick-fix-for-header-cpp.png "Szybka poprawka języka C++")

Edytor oferuje również szybkie poprawki dla niektórych możliwości refaktoryzacji. Na przykład jeśli deklarujesz klasę w pliku nagłówka, visual studio zaoferuje utworzenie definicji dla niego w oddzielnym pliku cpp.

![C&#43;&#43; szybka poprawka](../ide/media/quick-fix.png "Szybka poprawka języka C++")

## <a name="change-tracking"></a>Śledzenie zmian

Za każdym razem, gdy zmieniasz plik, po lewej stronie pojawia się żółty pasek wskazujący, że wprowadzono niezapisane zmiany. Po zapisaniu pliku pasek zmieni kolor na zielony. Zielone i żółte paski są zachowywane tak długo, jak długo dokument jest otwarty w edytorze. Reprezentują one zmiany wprowadzone od ostatniego otwarcia dokumentu.

![C&#43;&#43; śledzenie zmian](../ide/media/change-tracking-cpp.png "Śledzenie zmian")

## <a name="move-code"></a>Przenieś kod

Linie kodu można przesuwać w górę i w dół, zaznaczając je, przytrzymując klawisz Alt i naciskając klawisze strzałek **w górę/w dół.**

## <a name="insert-snippets"></a>Wstawianie urywków

Fragment kodu jest wstępnie zdefiniowanym fragmentem kodu źródłowego. Kliknij prawym przyciskiem myszy pojedynczy punkt lub zaznaczony tekst, aby wstawić fragment kodu lub otoczyć zaznaczony tekst fragmentem kodu. Na poniższej ilustracji przedstawiono trzy kroki do otoczyć wybraną instrukcję pętlą for. Żółte podświetlenia na obrazie końcowym to edytowalne pola, do których uzyskujesz dostęp za pomocą klawisza tab. Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).

![C&#43;&#43; wstawienie&#45;upuszczania fragmentu kodu w dół](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

## <a name="add-class"></a>Dodaj klasę

Dodaj nową klasę z menu **Projekt** lub z menu kontekstowego w **Eksploratorze rozwiązań:**

![Dodaj nową klasę w&#43;&#43;C](../ide/media/vs2017-add-class.png "vs2015_cpp_add_class")

Można również użyć Kreatora klas, aby zmodyfikować lub zbadać istniejącą klasę.

![Kreator&#43;&#43; C](../ide/media/vs2017-class-wizard.png)

Aby uzyskać więcej informacji, zobacz [Dodawanie funkcji za pomocą kreatorów kodu (C++)](../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="refactoring"></a>Refaktoryzacja

Refaktoryzowania są dostępne w menu kontekstowym Szybka akcja lub po kliknięciu [żarówki](/visualstudio/ide/perform-quick-actions-with-light-bulbs) w edytorze.  Niektóre z nich znajdują się również w menu **Edytuj > Refaktoryzator.**  Między innymi są to następujące funkcje:

- [Zmień nazwę](refactoring/rename.md)
- [Wyodrębnianie funkcji](refactoring/extract-function.md)
- [Implementowanie czystych elementów wirtualnych](refactoring/implement-pure-virtuals.md)
- [Tworzenie deklaracji/definicji](refactoring/create-declaration-definition.md)
- [Przenoszenie definicji funkcji](refactoring/move-definition-location.md)
- [Konwertowanie na literał nieprzetworzonego ciągu](refactoring/convert-to-raw-string-literal.md)
- [Zmienianie podpisu](refactoring/change-signature.md)

## <a name="code-style-enforcement-with-clangformat-and-editorconfig"></a>Wymuszanie stylu kodu za pomocą ClangFormat i EditorConfig

Visual Studio 2017 i nowsze jest wyposażony w wbudowaną obsługę [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html), popularne narzędzie do formatowania kodu dla języka C++ na podstawie Clang/LLVM. Wpisz "ClangFormat" w [trybie Szybkie uruchamianie,](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) aby ustawić go na jeden z następujących popularnych formatów:

- LLVM (właśc.
- Google
- Chromu
- Mozilla
- Webkit
- Visual Studio

Można również podać własny plik w formacie .clang lub _clang formatu, aby zastosować reguły niestandardowe do wszystkich plików kodu na tym samym poziomie lub poniżej.

Pliki można łatwo udostępniać za pomocą kontroli źródła, dzięki czemu można wymusić konwencje kodowania w całym zespole deweloperów.

![C&#43;&#43; Clang Format](../ide/media/clang-format-cpp.png "Clang Format")

Visual Studio 2017 i nowsze obsługuje również [EditorConfig](https://editorconfig.org/), który działa w podobny sposób. ClangFormat ma jednak więcej opcji stylu niż EditorConfig, w tym reguły, które są specyficzne dla języka C++. Z **EditorConfig**, można utworzyć pliki **.editorconfig** i umieścić je w różnych folderach bazy kodu, aby określić style kodu dla tych folderów i ich podfolderów. Plik **.editorconfig** zastępuje inne pliki **.editorconfig** w folderach nadrzędnych i zastępuje wszelkie ustawienia formatowania skonfigurowane za pomocą**opcji** **Narzędzia** > . Można ustawić reguły dla kart vs. spacje, rozmiar wcięci i więcej. Aby uzyskać więcej informacji, zobacz [Tworzenie przenośnych, niestandardowych ustawień edytora za pomocą programu EditorConfig](/visualstudio/ide/create-portable-custom-editor-options).

## <a name="other-formatting-options"></a>Inne opcje formatowania

Pole wyszukiwania **Szybkie uruchamianie** zapewnia najszybszy sposób znalezienia ustawienia lub narzędzia. Znajduje się on w menu głównym. Wystarczy rozpocząć wpisywanie, a lista automatycznego uzupełniania odfiltruje wyniki.

![Szybkie uruchamianie programu Visual Studio](../ide/media/vs2015_cpp_quick_launch.png "Szybkie uruchamianie")

Aby ustawić opcje formatowania, takie jak wcięcie, uzupełnianie nawiasów klamrowych i kolorowanie, wpisz "Formatowanie języka C++" w oknie **Szybkie uruchamianie.**

![Opcje formatowania języka C++](media/cpp-formatting-options.png)

Inne opcje formatowania znajdują się w obszarze **Edytuj** > **zaawansowane** w menu głównym.

![Zaawansowane opcje edycji języka C++](media/edit-advanced-cpp.png)

Opcje włączania i konfigurowania funkcji edycji specyficznych dla języka C++znajdują się w obszarze**Opcje** >  **narzędzi** > **Edytor** > tekstu**C/C++**. Po wybraniu opcji, którą chcesz ustawić, możesz uzyskać więcej pomocy, naciskając **klawisz F1,** gdy okno dialogowe jest w centrum uwagi. Aby uzyskać ogólne opcje `Editor C++` formatowania kodu, wpisz pozycję **Szybkie uruchamianie**.

![Opcje > narzędzi programu Visual Studio](../ide/media/tools-options.png "Opcje edytora")

Funkcje eksperymentalne, które mogą lub nie mogą być zawarte w przyszłej wersji programu Visual Studio, znajdują się w [edytorze tekstu C++ Eksperymentalne](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental) okno dialogowe. W programie Visual Studio 2017 i nowszych można włączyć **predictive IntelliSense** w tym oknie dialogowym.

## <a name="see-also"></a>Zobacz też

[Czytanie i interpretacja kodu w języku C++](read-and-understand-code-cpp.md)</br>
[Poruszanie się po bazie kodu języka C++ w programie Visual Studio](navigate-code-cpp.md)</br>
[Współpraca z udostępnianiem na żywo dla języka C++](live-share-cpp.md)
