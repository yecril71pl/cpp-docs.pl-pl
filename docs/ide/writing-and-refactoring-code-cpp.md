---
title: Edytuj i Refaktoryzacja C++ kodu w programie Visual Studio
description: Użyj edytora C++ kodu w programie Visual Studio do formatowania, nawigowania, zrozumienia i refaktoryzacji kodu.
ms.date: 05/31/2019
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
ms.topic: landing-page
ms.openlocfilehash: 255576bfc4a7eb78a660e5bfb05b0a97a7eb4c34
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221542"
---
# <a name="edit-and-refactor-c-code-in-visual-studio"></a>Edytuj i Refaktoryzacja C++ kodu w programie Visual Studio

Program Visual Studio udostępnia kilka narzędzi ułatwiających pisanie, edytowanie i refaktoryzację kodu.

##  <a name="intellisense"></a>IntelliSense

IntelliSense to zaawansowane narzędzie do uzupełniania kodu, które sugeruje symbole i fragmenty kodu w trakcie pisania. C++Funkcja IntelliSense w programie Visual Studio jest uruchamiana w czasie rzeczywistym, analizowanie bazy kodu podczas aktualizowania i udostępniania zaleceń. Gdy wpiszesz więcej znaków, lista zalecanych wyników zostanie zawężana.

![Lista&#43; &#43; rozwijana listy członków C](../ide/media/cpp-statement-completion.png)

Niektóre symbole są pomijane automatycznie, aby pomóc w zawężaniu wyników. Na przykład podczas uzyskiwania dostępu do elementów członkowskich obiektu klasy spoza klasy nie będzie można zobaczyć prywatnych członków domyślnie lub chronionych składowych (jeśli nie jesteś w kontekście klasy podrzędnej). Filtrowanie można dostosować za pomocą przycisków u dołu.

Po wybraniu symbolu z listy rozwijanej można uzupełnić go za pomocą **klawisza Tab**, **wprowadzić**lub jednego z innych znaków zatwierdzenia (domyślnie: {} [ ]().,:; +-*/% & | ^! =? @ #\)). Aby dodać lub usunąć znaki z tej listy, wyszukaj ciąg "IntelliSense" w obszarze **Szybkie uruchamianie** (Ctrl + Q) i wybierz **Edytor tekstu > opcji CC++ /> Advanced** . Opcja **zatwierdzania list elementów członkowskich** umożliwia dostosowanie listy przy użyciu żądanych zmian.

Opcja **tryb filtrowania listy składowych** określa, jakie rodzaje sugestii autouzupełniania funkcji IntelliSense są widoczne. Domyślnie jest ustawiona wartość **rozmyte**. W przypadku wyszukiwania rozmytego, jeśli masz symbol o nazwie *MyAwesomeClass*, możesz wpisać "Mac" i znaleźć klasę w sugestiach autouzupełniania. Algorytm rozmyte ustawia minimalny próg, który musi spełniać symbole, aby były widoczne na liście. Filtrowanie **inteligentne** wyświetla wszystkie symbole zawierające podciągi, które pasują do wpisanych informacji. Filtrowanie prefiksów wyszukuje ciągi zaczynające się od wpisanego typu.

Aby uzyskać więcej informacji C++ na temat technologii IntelliSense, zobacz [ C++ Visual IntelliSense](/visualstudio/ide/visual-cpp-intellisense) i [Konfigurowanie C++ projektu dla IntelliSense](/visualstudio/ide/visual-cpp-intellisense-configuration).

## <a name="intellicode"></a>IntelliCode

Rozszerzenia intellicode to funkcja IntelliSense z obsługą technologii AI. Najprawdopodobniej kandydujący znajduje się na górze listy uzupełniania. Zalecenia rozszerzenia intellicode są oparte na tysiącach projektów typu open source w usłudze GitHub z ponad 100 gwiazdkami. W połączeniu z kontekstem kodu, lista uzupełniania jest dostosowana do promowania typowych praktyk.

Podczas pisania C++rozszerzenia intellicode będzie pomagać w korzystaniu z popularnych bibliotek, C++ takich jak standardowa biblioteka. Kontekst kodu jest używany, aby najpierw dostarczyć najbardziej przydatne zalecenia. W poniższym przykładzie `size` funkcja członkowska jest często używana `sort` z funkcją, więc jest przedstawiona na górze listy wyników.

![&#43; C&#43; rozszerzenia intellicode](../ide/media/intellicode-cpp.png " rozszerzenia intellicodeC++ ")

::: moniker range="vs-2019"

W programie Visual Studio 2019 rozszerzenia intellicode jest dostępny jako składnik opcjonalny w obciążeniu  **C++ tworzenia aplikacji klasycznych** . Aby upewnić się, że rozszerzenia intellicode jest C++aktywny dla, przejdź do pozycji **Narzędzia** > **Opcje** > **rozszerzenia intellicode** > **Ogólne** i ustaw  **C++ model podstawowy** na **włączone**.

::: moniker-end

::: moniker range="vs-2017"

W programie Visual Studio 2017 rozszerzenia intellicode jest dostępny jako rozszerzenie w Visual Studio Marketplace.

::: moniker-end

## <a name="predictive-intellisense-experimental"></a>Funkcja IntelliSense predykcyjna (eksperymentalna)

Funkcja **IntelliSense predykcyjna** jest eksperymentalną funkcją, która korzysta z rozpoznawania kontekstowego, aby ograniczyć liczbę wyników wyświetlanych na liście rozwijanej IntelliSense. Algorytm stosuje dopasowanie typu, aby wyświetlić tylko te wyniki, które pasują do oczekiwanego typu. W najprostszym przypadku, jeśli wpiszesz `int x =` i wywołajesz listę rozwijaną IntelliSense, zobaczysz tylko liczby całkowite lub funkcje zwracające liczby całkowite. Ta funkcja jest domyślnie wyłączona, ponieważ nadal trwa tworzenie. Najlepiej sprawdza się w przypadku symboli globalnych; funkcje składowe nie są jeszcze obsługiwane. Można ją włączyć, wpisując "predykcyjne" w szybkim **uruchomieniu** lub wybierając**Opcje** >  **Narzędzia** > **Edytor** > tekstu > **C/C++** **eksperymentalny** **Włącz funkcję IntelliSense predykcyjną.**  > 

Aby zastąpić **predykcyjną funkcję IntelliSense** i wyświetlić dłuższą listę, naciśnij **klawisze Ctrl + J**. Jeśli funkcja **IntelliSense predykcyjna** jest włączona, wywołanie **klawiszy Ctrl + J** spowoduje usunięcie filtra predykcyjnego. Naciśnięcie **klawiszy Ctrl + J** ponownie usuwa filtr dostępności z listy elementów członkowskich, tam gdzie ma to zastosowanie. Przycisk ([+]) pod listą rozwijaną IntelliSense ma taki sam efekt jak **Ctrl + J**. Umieść kursor nad przyciskiem, aby zobaczyć informacje o tym, co jest wyświetlane.

![Funkcja&#43; &#43; IntelliSense predykcyjna języka C] Funkcja (../ide/media/predictive-intellisense-cpp.png "IntelliSense predykcyjna")

Poprzedni zrzut ekranu pokazuje kilka przycisków na liście rozwijanej. Umożliwiają one filtry IntelliSense dla różnych rodzajów wyników:

- Zmienne i stałe
- Funkcje
- Types
- Makra
- Wyliczenia
- Namespaces

Przycisk jest wyświetlany tylko wtedy, gdy jest on istotny dla bieżącej sesji IntelliSense. Zazwyczaj nie widzisz wszystkich przycisków w tym samym czasie.

## <a name="template-intellisense"></a>IntelliSense szablonu

Gdy karetka znajduje się wewnątrz definicji szablonu, pojawi się **pasek szablonu** , który umożliwia podanie przykładowych argumentów szablonu dla funkcji IntelliSense. 

![Szablon&#43; &#43; języka C IntelliSense przedstawia istniejące wystąpienia] Funkcja (../ide/media/template-intellisense-cpp-1.png "IntelliSense szablonów Wyświetla istniejące wystąpienia")

Kliknij ikonę **<T>** , aby rozwinąć/zwinąć **pasek szablonu**. Kliknij ikonę ołówka lub dwukrotnie kliknij **pasek szablonu** , aby otworzyć okno **Edycja** . 

![IntelliSense&#43; &#43; szablonu języka C](../ide/media/template-intellisense-cpp-3.png "IntelliSense szablonu")

Zmiany wprowadzone w oknie są stosowane bezpośrednio do kodu źródłowego, dzięki czemu można zobaczyć efekty w czasie rzeczywistym. 

Pasek szablonu może automatycznie wypełniać kandydatów w oparciu o wystąpienia w kodzie. Kliknij przycisk **Dodaj wszystkie istniejące wystąpienia** , aby wyświetlić listę wszystkich konkretnych argumentów, które zostały użyte do utworzenia wystąpienia szablonu w bazie kodu.

![Lista&#43; &#43; wyników IntelliSense szablonu C](../ide/media/template-intellisense-cpp-2.png "Lista wyników IntelliSense szablonu")

Okno w dolnej części edytora pokazuje, w jaki sposób znaleziono każde wystąpienie i jakie jego argumenty były.

![Mapa&#43; &#43; tworzenia wystąpienia IntelliSense szablonu C](../ide/media/template-intellisense-cpp-4.png "Mapa tworzenia wystąpień IntelliSense szablonu")

Informacje **paska szablonu** są traktowane jako specyficzne dla użytkownika. Jest on przechowywany w folderze. vs i nie jest przekazany do kontroli źródła.

##  <a name="error-squiggles-and-quick-fixes"></a>Zygzaki błędów i szybkie poprawki

Jeśli Edytor wykrywa problemy z kodem, spowoduje to dodanie kolorowych zygzaków w obszarze problemu. Czerwona zygzakowata oznacza kod, który nie kompiluje się. Zielone zygzaki wskazują inne rodzaje problemów, które nadal mogą być poważne. Możesz otworzyć okno **Lista błędów** , aby uzyskać więcej informacji o problemach.

W przypadku niektórych rodzajów błędów, a także wspólnych wzorców kodowania, Edytor będzie oferować **szybką poprawkę** w postaci żarówki, która pojawia się po umieszczeniu wskaźnika myszy na zygzaku. Kliknij strzałkę w dół, aby wyświetlić sugestie. 

W poniższym przykładzie zadeklarowano, `vector` ale nie znaleziono definicji, dlatego edytor oferuje niezbędny plik nagłówka:

![Szybka naprawa&#43; &#43; ] w języku C(../ide/media/quick-fix-for-header-cpp.png " C++ ")

Edytor oferuje również szybkie poprawki w przypadku niektórych możliwości refaktoryzacji. Na przykład, Jeśli deklarujesz klasę w pliku nagłówkowym, Visual Studio będzie oferować definicję dla niego w osobnym pliku. cpp. 

![Szybka naprawa&#43; &#43; ] w języku C(../ide/media/quick-fix.png " C++ ")

## <a name="change-tracking"></a>Śledzenie zmian

Po każdym wprowadzeniu zmian w pliku żółty pasek jest wyświetlany po lewej stronie, aby wskazać, że wprowadzono niezapisane zmiany. Po zapisaniu pliku pasek zmieni kolor na zielony. Zielone i żółte słupki są zachowywane, o ile dokument jest otwarty w edytorze. Reprezentują one zmiany wprowadzone od czasu ostatniego otwarcia dokumentu.

![Śledzenie&#43; &#43; zmian języka C](../ide/media/change-tracking-cpp.png "Śledzenie zmian")

## <a name="move-code"></a>Przenieś kod

Linie kodu można przenieść w górę i w dół, zaznaczając je, przytrzymując klawisz Alt i naciskając klawisze strzałek w **górę/w dół** .

##  <a name="insert-snippets"></a>Wstaw fragmenty kodu

Wstawka jest wstępnie zdefiniowanym fragmentem kodu źródłowego. Kliknij prawym przyciskiem myszy pojedynczy punkt lub w zaznaczonym tekście, aby wstawić fragment kodu lub otoczyć zaznaczony tekst fragmentem. Na poniższej ilustracji przedstawiono trzy kroki, aby umieścić wybraną instrukcję z pętlą for. Żółte wyróżnienia w końcowym obrazie są edytowalnymi polami dostępnymi za pomocą klawisza Tab. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).

![Lista&#43; &#43; rozwijana&#45;wstawiania fragmentów kodu w języku C](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

##  <a name="add-class"></a>Dodaj klasę

Dodaj nową klasę z menu **projekt** lub z menu kontekstowego w **Eksplorator rozwiązań**:

![Dodaj nową klasę w C&#43; ](../ide/media/vs2017-add-class.png "vs2015_cpp_add_class")

Można również użyć kreatora klas do modyfikacji lub przeanalizowania istniejącej klasy.

![Kreator&#43; &#43; klasy C](../ide/media/vs2017-class-wizard.png)

Aby uzyskać więcej informacji, zobacz [Dodawanie funkcji za pomocą kreatorów koduC++()](../ide/adding-functionality-with-code-wizards-cpp.md).

##  <a name="refactoring"></a>Refaktoryzacja

Refaktoryzacje są dostępne w menu kontekstowym szybkiej akcji lub przez kliknięcie żarówki w [](/visualstudio/ide/perform-quick-actions-with-light-bulbs) edytorze.  Niektóre znajdują się również w menu **edytuj > refaktoryzacji** .  Te funkcje obejmują:

* [Zmiana nazwy](refactoring/rename.md)
* [Wyodrębnianie funkcji](refactoring/extract-function.md)
* [Implementowanie czystych elementów wirtualnych](refactoring/implement-pure-virtuals.md)
* [Tworzenie deklaracji/definicji](refactoring/create-declaration-definition.md)
* [Przenoszenie definicji funkcji](refactoring/move-definition-location.md)
* [Konwertowanie na literał nieprzetworzonego ciągu](refactoring/convert-to-raw-string-literal.md)
* [Zmienianie podpisu](refactoring/change-signature.md)

## <a name="code-style-enforcement-with-clangformat-and-editorconfig"></a>Wymuszanie stylu kodu z ClangFormat i EditorConfig

Program Visual Studio 2017 lub nowszy zawiera wbudowaną obsługę [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html), popularnego narzędzia do formatowania kodu w C++ oparciu o Clang/LLVM. Wpisz "ClangFormat" w obszarze [szybkiego uruchamiania](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) , aby ustawić go tak, aby używał jednego z następujących popularnych formatów:

- LLVM
- Google
- Chrom
- Mozilla
- WebKit
- Visual Studio

Możesz również podać własny plik. Clang-format lub _clang-format, aby zastosować niestandardowe reguły do wszystkich plików kodu na tym samym poziomie lub poniżej.

Pliki są łatwo udostępniane za pośrednictwem kontroli źródła, więc można wymusić konwencje kodowania dla całego zespołu deweloperów.

![Format&#43; &#43; języka C Clang](../ide/media/clang-format-cpp.png "Format Clang")

Program Visual Studio 2017 i jego nowsze wersje obsługują również [EditorConfig](https://editorconfig.org/), które działają w podobny sposób. ClangFormat jednak ma więcej opcji stylu niż EditorConfig, w tym reguł, które są specyficzne dla C++. Za pomocą **EditorConfig**można tworzyć pliki **EditorConfig** i umieszczać je w różnych folderach bazy kodu w celu określenia stylów kodu dla tych folderów i ich podfolderów. Plik **. editorconfig** zastępuje wszystkie inne pliki **. editorconfig** w folderach nadrzędnych i zastępuje wszelkie ustawienia formatowania skonfigurowane za pośrednictwem**opcji** **narzędzi** > . Możesz ustawić reguły dla kart zamiast spacji, wcięcia rozmiaru i inne. Aby uzyskać więcej informacji, zobacz [Tworzenie przenośnych ustawień edytora niestandardowego z EditorConfig](/visualstudio/ide/create-portable-custom-editor-options).

## <a name="other-formatting-options"></a>Inne opcje formatowania

Pole wyszukiwania **szybkiego uruchamiania** zapewnia najszybszy sposób znalezienia ustawienia lub narzędzia. Znajduje się ona w menu głównym. Po prostu zacznij pisać, a lista autouzupełniania przefiltruje wyniki.

![Szybkie uruchamianie programu Visual Studio](../ide/media/vs2015_cpp_quick_launch.png "Szybkie uruchamianie")

Aby ustawić opcje formatowania, takie jak wcięcia, uzupełnianie nawiasów klamrowych i kolorowanie,C++ wpisz "formatowanie" w oknie **Szybkie uruchamianie** .

![C++Opcje formatowania](media/cpp-formatting-options.png)

Inne opcje formatowania można znaleźć w obszarze **Edytuj** > **Zaawansowane** w menu głównym.

![C++Zaawansowane opcje edycji](media/edit-advanced-cpp.png)

Opcje włączania i konfigurowania C++konkretnych funkcji edycji znajdują się w obszarze **Narzędzia** > **Opcje** > **Edytor** > tekstu**CC++/** . Po wybraniu opcji, która ma zostać ustawiona, możesz uzyskać więcej pomocy, naciskając klawisz **F1** , gdy okno dialogowe jest fokusem. Aby uzyskać ogólne opcje formatowania kodu, `Editor C++` wpisz polecenie **Szybkie uruchamianie**.

![Opcje > Visual Studio Tools](../ide/media/tools-options.png "Opcje edytora")

Funkcje eksperymentalne, które mogą lub nie mogą być uwzględnione w przyszłych wersjach programu Visual Studio, znajdują się w oknie dialogowym [eksperymentalnym edytora C++ tekstu](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental) . W programie Visual Studio 2017 i nowszych można włączyć funkcję **IntelliSense predykcyjną** w tym oknie dialogowym.

## <a name="see-also"></a>Zobacz też

[Odczytuj i rozumiej C++ kod](read-and-understand-code-cpp.md)</br>
[Nawigowanie C++ po bazie kodu w programie Visual Studio](navigate-code-cpp.md)</br>
[Współpracuj z Live Shareami dlaC++](live-share-cpp.md)