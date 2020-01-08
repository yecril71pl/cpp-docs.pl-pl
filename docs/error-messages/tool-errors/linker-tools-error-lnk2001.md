---
title: Błąd narzędzi konsolidatora LNK2001
ms.date: 12/19/2019
f1_keywords:
- LNK2001
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
ms.openlocfilehash: b6d1e53d8f057ddc93e2dfde65cb951d247dfcc0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302136"
---
# <a name="linker-tools-error-lnk2001"></a>Błąd narzędzi konsolidatora LNK2001

> nierozpoznany symbol zewnętrzny "*symbol*"

Skompilowany kod wykonuje odwołanie lub wywołanie do *symbolu*. Symbol nie jest zdefiniowany w żadnych bibliotekach ani plikach obiektów przeszukanych przez konsolidator.

Ten komunikat o błędzie następuje po błędzie krytycznym [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Aby naprawić błąd LNK1120, najpierw Napraw wszystkie błędy LNK2001 i LNK2019.

Istnieje wiele sposobów uzyskiwania błędów LNK2001. Wszystkie z nich obejmują *odwołanie* do funkcji lub zmiennej, których konsolidator nie może *rozpoznać*, lub znaleźć definicję dla. Kompilator może określić, kiedy kod nie *deklaruje* symbolu, ale nie *definiuje* go. Dzieje się tak, ponieważ definicja może znajdować się w innym pliku lub bibliotece źródłowej. Jeśli kod odwołuje się do symbolu, ale nigdy nie jest zdefiniowany, konsolidator generuje błąd.

## <a name="what-is-an-unresolved-external-symbol"></a>Co to jest nierozpoznany symbol zewnętrzny?

*Symbol* to wewnętrzna nazwa dla funkcji lub zmiennej globalnej. Jest to forma nazwy używana lub zdefiniowana w skompilowanym pliku lub bibliotece obiektu. Zmienna globalna jest zdefiniowana w pliku obiektu, w którym jest przypisywany magazyn. Funkcja jest zdefiniowana w pliku obiektu, w którym jest umieszczany skompilowany kod dla treści funkcji. *Symbol zewnętrzny* jest przywoływany w jednym pliku obiektu, ale zdefiniowany w innej bibliotece lub pliku obiektu. *Wyeksportowany symbol* jest taki, który jest udostępniany publicznie przez plik lub bibliotekę obiektów, która go definiuje.

Aby utworzyć aplikację lub bibliotekę DLL, każdy używany symbol musi mieć definicję. Konsolidator musi *rozwiązać*lub znaleźć definicję dopasowania dla, każdy symbol zewnętrzny, do którego odwołuje się każdy plik obiektu. Konsolidator generuje błąd, gdy nie może rozpoznać symbolu zewnętrznego. Oznacza to, że konsolidator nie może znaleźć pasującej definicji symbolu wyeksportowanego w żadnym z połączonych plików.

## <a name="compilation-and-link-issues"></a>Kompilacja i łączenie problemów

Ten błąd może wystąpić:

- Gdy projekt nie zawiera odwołania do biblioteki (. LIB) lub obiekt (. OBJ). Aby rozwiązać ten problem, Dodaj odwołanie do wymaganej biblioteki lub pliku obiektu do projektu. Aby uzyskać więcej informacji, zobacz [lib plików jako dane wejściowe konsolidatora](../../build/reference/dot-lib-files-as-linker-input.md).

- Gdy projekt zawiera odwołanie do biblioteki (. LIB) lub obiekt (. OBJ) plik, który z kolei wymaga symboli z innej biblioteki. Może się to zdarzyć nawet wtedy, gdy nie wywołasz funkcji, które powodują zależność. Aby rozwiązać ten problem, Dodaj odwołanie do innej biblioteki do projektu. Aby uzyskać więcej informacji, zobacz temat [Omówienie klasycznego modelu łączenia: Tworzenie symboli na potrzeby jazdy](https://devblogs.microsoft.com/oldnewthing/20130108-00/?p=5623).

- Jeśli używasz opcji [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) lub [/zl](../../build/reference/zl-omit-default-library-name.md) . Po określeniu tych opcji biblioteki zawierające wymagany kod nie są łączone do projektu, chyba że zostały jawnie dołączone. Aby rozwiązać ten problem, należy jawnie uwzględnić wszystkie biblioteki używane w wierszu polecenia linku. Jeśli podczas korzystania z tych opcji widzisz wiele brakujących nazw funkcji biblioteki CRT lub standardowej, jawnie Uwzględnij pliki bibliotek CRT i biblioteki standardowa w łączu.

- W przypadku kompilowania przy użyciu opcji **/CLR** . Brak odwołania do `.cctor`. Aby uzyskać więcej informacji na temat sposobu rozwiązania tego problemu, zobacz [Inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md).

- W przypadku łączenia się z bibliotekami trybu wydania podczas kompilowania wersji debugowania aplikacji. Podobnie, jeśli używasz opcji **/MTD** lub **/MDd** lub Zdefiniuj `_DEBUG` a następnie połącz się z bibliotekami wersji, należy oczekiwać wielu potencjalnych nierozwiązanych elementów zewnętrznych, między innymi problemami. Łączenie kompilacji w trybie wydania z bibliotekami debugowania powoduje także podobne problemy. Aby rozwiązać ten problem, upewnij się, że używasz bibliotek debugowania w kompilacjach do debugowania oraz w bibliotekach detalicznych w kompilacjach detalicznych.

- Jeśli Twój kod odwołuje się do symbolu z jednej wersji biblioteki, ale zostanie połączona inna wersja biblioteki. Ogólnie rzecz biorąc, nie można mieszać plików obiektów lub bibliotek, które są skompilowane dla różnych wersji kompilatora. Biblioteki dostarczane w jednej wersji mogą zawierać symbole, których nie można znaleźć w bibliotekach dołączonych do innych wersji. Aby rozwiązać ten problem, skompiluj wszystkie pliki obiektów i biblioteki z tą samą wersją kompilatora przed połączeniem ich ze sobą. Aby uzyskać więcej informacji, zobacz [ C++ zgodność binarna 2015-2019](../../porting/binary-compat-2015-2017.md).

- Jeśli ścieżki biblioteki są nieaktualne. **Narzędzia > opcje > projekty > okna dialogowe katalogów VC + +** , w obszarze Wybieranie **plików biblioteki** , umożliwiają zmianę kolejności wyszukiwania biblioteki. Folder konsolidatora w oknie dialogowym strony właściwości projektu może również zawierać ścieżki, które mogą być nieaktualne.

- Po zainstalowaniu nowego Windows SDK (prawdopodobnie z inną lokalizacją). Kolejność wyszukiwania biblioteki musi zostać zaktualizowana, aby wskazywała nową lokalizację. Zwykle należy umieścić ścieżkę do nowego zestawu SDK dołączania i katalogów lib przed domyślną lokalizacją wizualną C++ . Ponadto projekt zawierający osadzone ścieżki może nadal wskazywać na stare ścieżki, które są prawidłowe, ale nieaktualne. Zaktualizuj ścieżki nowych funkcji dodanych przez nową wersję, która została zainstalowana w innej lokalizacji.

- Jeśli kompilujesz w wierszu polecenia i utworzysz własne zmienne środowiskowe. Sprawdź, czy ścieżki do narzędzi, bibliotek i plików nagłówkowych przechodzą do spójnej wersji. Aby uzyskać więcej informacji, zobacz [Ustawianie zmiennych dotyczących ścieżki i środowiska dla kompilacji z wiersza polecenia](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)

## <a name="coding-issues"></a>Problemy z kodowaniem

Ten błąd może być spowodowany przez:

- Niezgodna wielkość liter w kodzie źródłowym lub pliku definicji modułu (. def). Na przykład, jeśli nazwasz zmienną `var1` w jednym C++ pliku źródłowym i spróbujesz uzyskać do niej dostęp jako `VAR1` w innym, ten błąd zostanie wygenerowany. Aby rozwiązać ten problem, użyj spójnie wpisanej nazwy i wielkości liter.

- Projekt korzystający z [funkcji wykreślania](../../error-messages/tool-errors/function-inlining-problems.md). Może wystąpić, gdy zdefiniujesz funkcje jako `inline` w pliku źródłowym, a nie w pliku nagłówkowym. Wbudowane funkcje nie mogą być widoczne poza plikiem źródłowym, który je definiuje. Aby rozwiązać ten problem, zdefiniuj wbudowane funkcje w nagłówkach, w których są one deklarowane.

- Wywoływanie funkcji C z C++ programu bez użycia deklaracji `extern "C"` dla funkcji języka c. Kompilator używa różnych wewnętrznych konwencji nazewnictwa symboli dla języków C C++ i Code. Wewnętrzna nazwa symbolu to element łączący, który jest wyszukiwany podczas rozpoznawania symboli. Aby rozwiązać ten problem, należy użyć otoki `extern "C"` wokół wszystkich deklaracji funkcji języka C używanych w C++ kodzie, co powoduje, że kompilator używa wewnętrznej konwencji nazewnictwa języka c dla tych symboli. Opcje kompilatora [/TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) i [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) powodują, że kompilator kompiluje pliki C++ odpowiednio lub C, niezależnie od tego, czym jest rozszerzenie nazwy pliku. Te opcje mogą spowodować, że wewnętrzne nazwy funkcji różnią się od oczekiwanych.

- Próba odwołująca się do funkcji lub danych, które nie mają powiązania zewnętrznego. W C++programie funkcje wbudowane i dane `const` mają połączenie wewnętrzne, chyba że są jawnie określone jako `extern`. Aby rozwiązać ten problem, użyj jawnych deklaracji `extern` w odniesieniu do symboli, do których odwołuje się poza Definiowanie pliku źródłowego.

- [Brakująca treść funkcji lub definicja zmiennej](../../error-messages/tool-errors/missing-function-body-or-variable.md) . Ten błąd jest typowy w przypadku deklarowania, ale nie definiowania zmiennych, funkcji ani klas w kodzie. Kompilator wymaga tylko prototypu funkcji lub `extern` deklaracji zmiennej do wygenerowania pliku obiektu bez błędu, ale konsolidator nie może rozpoznać wywołania funkcji ani odwołania do zmiennej, ponieważ nie istnieje kod funkcji ani zarezerwowane miejsce na zmiennej. Aby rozwiązać ten problem, upewnij się, że zdefiniowano każdą przywoływaną funkcję i zmienną w połączonym pliku źródłowym lub bibliotece.

- Wywołanie funkcji, które używa typów zwracanych i parametrów lub konwencji wywoływania, które nie pasują do tych w definicji funkcji. W C++ plikach obiektów [dekoracja nazwa](../../error-messages/tool-errors/name-decoration.md) koduje konwencję wywoływania, zakres klasy lub przestrzeni nazw oraz zwraca i typy parametrów funkcji. Zakodowany ciąg wchodzi w skład ostatniej nazwy funkcji dekoracyjnej. Ta nazwa jest używana przez konsolidator do rozpoznawania lub dopasowywania wywołań funkcji z innych plików obiektów. Aby rozwiązać ten problem, upewnij się, że w deklaracji funkcji, definicji i wywołań wszystkie używają tych samych zakresów, typów i konwencji wywoływania.

- C++kod wywoływany, gdy dołączysz prototyp funkcji w definicji klasy, ale nie [dołączysz implementacji](../../error-messages/tool-errors/missing-function-body-or-variable.md) funkcji. Aby rozwiązać ten problem, należy podać definicję wszystkich członków klasy, które są wywoływane.

- Próba wywołania czystej funkcji wirtualnej z abstrakcyjnej klasy podstawowej. Czysta funkcja wirtualna nie ma implementacji klasy bazowej. Aby rozwiązać ten problem, upewnij się, że są zaimplementowane wszystkie wywołane funkcje wirtualne.

- Próba użycia zmiennej zadeklarowanej w funkcji ([zmiennej lokalnej](../../error-messages/tool-errors/automatic-function-scope-variables.md)) poza zakresem tej funkcji. Aby rozwiązać ten problem, usuń odwołanie do zmiennej, która nie znajduje się w zakresie, lub Przenieś zmienną do wyższego zakresu.

- Podczas kompilowania wersji wydania projektu ATL, należy utworzyć komunikat, że wymagany jest kod uruchomienia CRT. Aby rozwiązać ten problem, wykonaj jedną z następujących czynności:

  - Usuń `_ATL_MIN_CRT` z listy preprocesora definiuje się, aby umożliwić dołączenie kodu uruchamiania CRT. Aby uzyskać więcej informacji, zobacz [Ogólne strony właściwości (projekt)](../../build/reference/general-property-page-project.md).

  - Jeśli to możliwe, Usuń wywołania funkcji CRT, które wymagają kodu uruchomienia CRT. Zamiast tego należy użyć ich odpowiedników Win32. Na przykład użyj `lstrcmp`, a nie `strcmp`. Znane funkcje, które wymagają kodu uruchomieniowego CRT, to niektóre funkcje ciągów i zmiennoprzecinkowych.

## <a name="consistency-issues"></a>Problemy ze spójnością

Obecnie nie ma standardowej [ C++ dekoracji nazw](../../error-messages/tool-errors/name-decoration.md) między dostawcami kompilatora, a nawet między różnymi wersjami tego samego kompilatora. Pliki obiektów skompilowane z różnymi kompilatorami mogą nie używać tego samego schematu nazewnictwa. Łączenie ich może spowodować wystąpienie błędu LNK2001.

[Mieszanie wbudowanych i niewbudowanych opcji kompilacji](../../error-messages/tool-errors/function-inlining-problems.md) w różnych modułach może spowodować wystąpienie LNK2001. Jeśli C++ biblioteka jest tworzona z włączonym wykreśleniem funkcji ( **/OB1** lub **/Ob2**), ale odpowiedni plik nagłówkowy opisujący funkcje ma wyłączone wyłączenie (bez słowa kluczowego `inline`), ten błąd wystąpi. Aby rozwiązać ten problem, zdefiniuj `inline` funkcji w pliku nagłówkowym, który znajduje się w innych plikach źródłowych.

Jeśli używasz dyrektywy kompilatora `#pragma inline_depth`, upewnij się, że ustawiono [wartość 2 lub większą](../../error-messages/tool-errors/function-inlining-problems.md), i upewnij się, że użyto również opcji kompilatora [/OB1](../../build/reference/ob-inline-function-expansion.md) lub [/Ob2](../../build/reference/ob-inline-function-expansion.md) .

Ten błąd może wystąpić, jeśli pominięto opcję łącza/NOENTRY podczas tworzenia biblioteki DLL tylko dla zasobów. Aby rozwiązać ten problem, Dodaj opcję/NOENTRY do polecenia link.

Ten błąd może wystąpić, jeśli w projekcie użyto nieprawidłowych ustawień/SUBSYSTEM lub/ENTRY. Przykładowo, jeśli piszesz aplikację konsolową i określisz/SUBSYSTEM: WINDOWS, zostanie wygenerowany nierozpoznany błąd zewnętrzny dla `WinMain`. Aby rozwiązać ten problem, upewnij się, że opcje są zgodne z opcjami typu projektu. Aby uzyskać więcej informacji na temat tych opcji i punktów wejścia, zobacz Opcje konsolidatora [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) i [/entry](../../build/reference/entry-entry-point-symbol.md) .

## <a name="exported-def-file-symbol-issues"></a>Problemy ze znakiem wyeksportowanego pliku. def

Ten błąd występuje, gdy nie znaleziono eksportu wymienionego w pliku. def. Może to być spowodowane faktem, że eksportowanie nie istnieje, jest napisane niepoprawnie lub C++ używa dekoracyjnych nazw. Plik. def nie przyjmuje nazw. Aby rozwiązać ten problem, Usuń niepotrzebne Eksporty i użyj deklaracji `extern "C"` w przypadku eksportowanych symboli.

## <a name="use-the-decorated-name-to-find-the-error"></a>Użyj nazwy dekoracyjnej, aby znaleźć błąd

C++ Kompilator i konsolidator używają [dekoracji nazw](../../error-messages/tool-errors/name-decoration.md), znanego również jako *name-dekorowanie*. Dekoracja nazw koduje dodatkowe informacje o typie zmiennej w nazwie symbolu. Nazwa symbolu funkcji koduje jej typ zwracany, typy parametrów, zakres i konwencję wywoływania. Ta dekoracyjna nazwa jest symbolem, który wyszukuje za pomocą konsolidatora, aby rozpoznać symbole zewnętrzne.

Błąd łącza może wynikać, jeśli deklaracja funkcji lub zmiennej nie jest *dokładnie* zgodna z definicją funkcji lub zmiennej. Wynika to z faktu, że jakakolwiek różnica będzie częścią nazwy symbolu do dopasowania. Ten błąd może wystąpić, nawet jeśli ten sam plik nagłówka jest używany zarówno w kodzie wywołującym, jak i w kodzie. Jeden ze sposobów może wystąpić w przypadku skompilowania plików źródłowych przy użyciu różnych flag kompilatora. Na przykład, jeśli kod jest kompilowany do użycia konwencji wywoływania `__vectorcall`, ale łączysz się z biblioteką, która oczekuje, że klienci będą wywoływać ją przy użyciu domyślnej `__cdecl` lub konwencji wywoływania `__fastcall`. W takim przypadku symbole nie są zgodne, ponieważ Konwencje wywoływania są różne.

Aby ułatwić znalezienie przyczyny problemu, komunikat o błędzie pokazuje dwie wersje nazwy. Wyświetla zarówno "przyjazną nazwę", nazwę używaną w kodzie źródłowym i nazwę dekoracyjną (w nawiasach). Nie musisz wiedzieć, jak interpretować nazwę dekoracyjną. Nadal można wyszukać i porównać z innymi nazwami dekoracyjnymi. Narzędzia wiersza polecenia mogą pomóc znaleźć i porównać oczekiwaną nazwę symbolu i rzeczywistą nazwę symbolu:

- Opcje [/exports](../../build/reference/dash-exports.md) i [/Symbols](../../build/reference/symbols.md) narzędzia wiersza polecenia polecenia DUMPBIN są przydatne w tym miejscu. Mogą one pomóc w ustaleniu, które symbole są zdefiniowane w pliku dll i plikach biblioteki. Możesz użyć listy symboli, aby sprawdzić, czy eksportowane dekoracyjne nazwy pasują do dekoracyjnych nazw, które wyszukuje konsolidator.

- W niektórych przypadkach konsolidator może zgłosić tylko dekoracyjną nazwę symbolu. Możesz użyć narzędzia wiersza polecenia UNDNAME, aby uzyskać niedekoracyjną postać nazwy dekoracyjnej.

## <a name="additional-resources"></a>Dodatkowe zasoby

Aby uzyskać więcej informacji, zobacz pytanie Stack Overflow ["co to jest błąd niezdefiniowanego odwołania/nierozpoznany symbol zewnętrzny i jak go naprawić?"](https://stackoverflow.com/q/12573816/2002113).
