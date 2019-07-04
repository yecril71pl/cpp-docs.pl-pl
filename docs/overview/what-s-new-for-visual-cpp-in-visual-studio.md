---
title: Co nowego w języku C++ w programie Visual Studio
ms.date: 07/02/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: f02c5878f5f741c216499f619bfd1392483bfa86
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552344"
---
# <a name="whats-new-for-c-in-visual-studio"></a>Co nowego w języku C++ w programie Visual Studio

::: moniker range=">=vs-2019"

Visual Studio 2019 obejmuje wiele aktualizacji i poprawek dotyczących środowiska Microsoft C++. Usunięto wiele usterek i problemów z kompilatora i narzędzi. Wiele z tych problemów zostały przesłane przez klientów za pośrednictwem [Zgłoś Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019) i [sugestię](https://developercommunity.visualstudio.com/spaces/62/index.html) opcji w obszarze **Wyślij opinię**. Dziękujemy za zgłaszanie usterek! Aby uzyskać więcej informacji na temat what's new in całego programu Visual Studio, odwiedź stronę [What's new in Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019). Aby uzyskać informacji na temat nowości w C++ w programie Visual Studio 2017, zobacz [What's new for C++ w programie Visual Studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017). Instrukcje dotyczące Nowości dla C++ w programie Visual Studio 2015 i wcześniejszych wersjach, zobacz [Visual C++ co to jest nowy 2003 2015 r](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>kompilator C++

- Rozszerzona obsługa funkcji C ++ 17 i poprawki do poprawności, a także obsługę eksperymentalną funkcji C ++ 20 takich jak moduły i procedur wspólnych. Aby uzyskać szczegółowe informacje, zobacz [ulepszenia zgodności języka C++ w Visual Studio 2019](cpp-conformance-improvements.md).

- `/std:c++latest` Teraz opcja powoduje dołączenie funkcji C ++ 20, które nie są zawsze kompletne, łącznie z obsługą początkowej dla operatora 20 C ++ \<= > pojazdu ("kosmicznego") dla trzykierunkowe porównywanie.

- C++ Przełącznika kompilatora `/Gm` jest już przestarzały. Rozważ wyłączenie `/Gm` przełącznika w skrypcie kompilacji, jeśli jest jawnie zdefiniowany. Jednakże można także zignorować ostrzeżenie o zakończeniu obsługi dla `/Gm`, ponieważ nie są traktowane jako błąd, gdy za pomocą "Traktuj ostrzeżenia jako błędy" (`/WX`).

- Po rozpoczęciu MSVC implementowania funkcji z języka C ++ 20 standardowy projekt w obszarze `/std:c++latest` flagi `/std:c++latest` jest teraz niezgodna z `/clr` (wszystkie odmian) `/ZW`, i `/Gm`. W programie Visual Studio 2019 r, użyj `/std:c++17` lub `/std:c++14` tryby podczas kompilowania za pomocą `/clr`, `/ZW`, lub `/Gm` (ale zobacz poprzedni punkt).

- Prekompilowane nagłówki nie są już generowane domyślnie dla konsoli C++ i aplikacji klasycznych.

### <a name="codegen-security-diagnostics-and-versioning"></a>Generowanie kodu, zabezpieczeń, diagnostyki i przechowywania wersji

Lepsza analiza przy użyciu `/Qspectre` do udzielania pomocy środki zaradcze dla luki Spectre wariantu 1 (CVE-2017-5753). Aby uzyskać więcej informacji, zobacz [krokami zaradczymi dla luki Spectre w MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>C++ulepszenia standardowej biblioteki

- Implementacja dodatkowe funkcje języka C ++ 17 i C ++ biblioteki 20 i poprawność poprawki. Aby uzyskać szczegółowe informacje, zobacz [ulepszenia zgodności języka C++ w Visual Studio 2019](cpp-conformance-improvements.md).

- Clang-Format została zastosowana do C++ nagłówki standardowej biblioteki w celu zapewnienia lepszej czytelności.

- Ponieważ program Visual Studio teraz obsługuje tylko mój kod dla C++, standardowej biblioteki nie musi już podać niestandardowy mechanizm `std::function` i `std::visit` aby osiągnąć ten sam efekt. Usunięcie tej maszyny stopniu nie ma żadnych efektów widoczny dla użytkownika. Jedynym wyjątkiem jest, kompilator nie generuje diagnostyki, które wskazują na problemy w wierszu 15732480 lub 16707566 z \<type_traits > lub \<wariantu >.

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>Ulepszenia wydajności lub przepływności kompilator i standardową bibliotekę

- Ulepszenia przepływności, w tym sposób konsolidator obsługi We/Wy, kompilacji i połącz czas tworzenia i scalanie typu PDB.

- Dodano wsparcie podstawowe dla OpenMP SIMD wektoryzacji. Można je włączyć za pomocą nowego przełącznika kompilatora `-openmp:experimental`. Ta opcja umożliwia oznaczony za pomocą pętli `#pragma omp simd` do potencjalnie zwektoryzowana. Nie jest gwarantowana wektoryzacji i pętli z adnotacjami, ale nie jest zwektoryzowana zostanie wyświetlone ostrzeżenie, zgłaszane. Klauzule SIMD, nie są obsługiwane; są one ignorowane i ostrzeżenie jest zgłaszane.

- Dodano nowy przełącznik wiersza polecenia wbudowanie `-Ob3`, która jest nieco bardziej agresywnego `-Ob2`. `-O2` (Optymalizuj dane binarne dla szybkości) nadal oznacza `-Ob2` domyślnie. Jeśli okaże się, kompilator wystarczająco agresywnie nie wbudowanych, należy wziąć pod uwagę przekazywanie `-O2 -Ob3`.

- Aby zapewnić obsługę wektoryzacji pętli for z wywołania do funkcji bibliotek matematycznych i niektórych innych operacji, takich jak dzielenie liczby całkowitej ręcznie, Dodaliśmy obsługę funkcji wewnętrznych krótkich wektorów matematyczne biblioteki (SVML). Te funkcje obliczeniowe odpowiedniki wektor 128-bitowego, 256-bitowego lub 512-bitowe. Aby uzyskać definicje obsługiwanych funkcji, zobacz [Intel Intrinsic Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML) (Przewodnik wewnętrzny firmy Intel).

- Nowe i ulepszone optymalizacje:

  - Składania stałej i arytmetyczne definiowaniu wyrażeń przy użyciu funkcji wewnętrznych wektora SIMD, float i liczba całkowita formularzy.

  - Bardziej zaawansowanych analiz do wyodrębniania informacji z przepływu sterowania (instrukcji if/else/switch) do usunięcia gałęzi zawsze okazał się być prawdziwe lub fałszywe.

  - Ulepszone funkcji memset odwijania do zastosowania instrukcjami wektor SSE2.

  - Ulepszone usuwania kopii bezcelowe struct/class, szczególnie w przypadku programów C++, przekazywane przez wartość.

  - Ulepszona Optymalizacja kodu za pomocą `memmove`, takich jak `std::copy` lub `std::vector` i `std::string` konstrukcji.

- Zoptymalizowane pod kątem projektu fizycznego standardowej biblioteki w celu uniknięcia kompilowanie części biblioteki standardowej, nie są bezpośrednio dołączone. Ta zmiana skrócenie czasu kompilacji, pustego pliku, który zawiera tylko \<wektor > o połowę. W rezultacie, użytkownik może być konieczne dodanie `#include` dyrektywy dla nagłówków, które zostały wcześniej pośrednio zawarte. Na przykład, kod, który używa `std::out_of_range` teraz może być konieczne dodanie `#include <stdexcept>`. Kod, który używa operatora wstawiania strumienia teraz może być konieczne dodanie `#include <ostream>`. Korzyścią jest translacja tylko jednostek, które faktycznie przy użyciu \<stdexcept > lub \<ostream > składniki płacić przepływności kosztów do kompilowania ich.

- `if constexpr` została zastosowana w większej liczbie miejsc w standardowej bibliotece ulepszoną przepływność i rozmiar zmniejszenie kodu podczas operacji kopiowania, permutacji, takich jak wstecznego i Obróć i biblioteki algorytmów równoległych.

- Standardowa biblioteka teraz używa wewnętrznie `if constexpr` zmniejszyć czasy kompilacji, nawet w tryb C ++ 14.

- Dynamiczne łączenie wykrywania dla biblioteki algorytmów równoległych już środowisko uruchomieniowe przechowuje całą stronę tablicy wskaźników funkcji. Oznaczenie tej pamięci tylko do odczytu został uznany za nie są już odpowiednie ze względów bezpieczeństwa.

- `std::thread`jego Konstruktor nie jest już oczekuje na uruchomienie wątku, a nie jest już wstawienia, wywołuje wiele warstw w funkcji, od podstawowej biblioteki języka C `_beginthreadex` i dostarczony obiekt możliwy do wywołania. Wcześniej `std::thread` 6 funkcje między put `_beginthreadex` i dostarczony obiekt możliwy do wywołania została zmniejszona do 3 tylko (2, które są po prostu `std::invoke`). Ta zmiana rozwiązuje również usterkę zasłoniętej chronometrażu gdzie `std::thread` powodujący zawieszanie konstruktora, jeśli zegar systemowy zmienione dokładnie w momencie `std::thread` został on utworzony.

- Naprawiono regresję wydajności w `std::hash` , wprowadziliśmy podczas implementowania `std::hash<std::filesystem::path>`.

- Standardowa biblioteka używa teraz destruktory zamiast bloki catch w kilku miejscach do osiągnięcia poprawności. Ta zmiana powoduje lepszej interakcji debugera: Wyjątki Generowanie za pomocą biblioteki standardowej w lokalizacjach, do których to dotyczy teraz wyświetlani z etykietą jest zgłaszana z ich oryginalne throw lokacji, a nie naszych Zgłoś ponownie. Nie wszystkie bloki catch standardowej biblioteki zostały wyeliminowane; Oczekujemy, że liczba bloków catch obniżenie w nowszych wersjach MSVC.

- Suboptymalny generowanie kodu w `std::bitset` spowodowane przez warunkowe throw wewnątrz noexcept funkcji został naprawiony, uwzględniając zgłaszanie ścieżkę.

- `std::list` i `std::unordered_*` rodziny korzystanie z Iteratory debugowanie w wielu miejscach.

- Kilka `std::list` elementy członkowskie zostały zmienione na ponowne użycie listy węzłów, jeśli jest to możliwe, zamiast cofanie przydziału i zmienianie ich alokacji. Na przykład, biorąc pod uwagę `list<int>` już o rozmiarze 3, wywołanie `assign(4, 1729)` teraz zastępuje liczby całkowite w pierwszym węzłów listy 3 i przydziela jeden nowy węzeł listy z wartością 1729.

- Wszystkie wywołania biblioteki standardowej `erase(begin(), end())` zostały zmienione na `clear()`.

- `std::vector` teraz jest inicjowany i usuwa elementy efektywniej w niektórych przypadkach.

- Ulepszenia `std::variant` się bardziej Optymalizator przyjazne, co lepiej wygenerowanego kodu. Wbudowanie kodu jest teraz znacznie lepiej korzystać z `std::visit`.

## <a name="c-ide"></a>Środowisko IDE języka C++

### <a name="live-share-c-support"></a>Na żywo obsługi języka C++ udziału

[Na żywo udziału](/visualstudio/liveshare/) obsługuje obecnie C++, co pozwoli deweloperom współpracować w czasie rzeczywistym za pomocą programu Visual Studio lub Visual Studio Code. Aby uzyskać więcej informacji, zobacz [ogłoszenie funkcja udostępniania na żywo dla języka C++: Współpraca i udostępnianie w czasie rzeczywistym](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>Rozszerzenie IntelliCode dla języka C++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 wersji 16.1

Rozszerzenie IntelliCode to opcjonalne rozszerzenie korzystającą z własną rozbudowane szkolenia i kontekst kodu put, co to są najbardziej prawdopodobne do użycia na początku listy uzupełnianej. Często można to wyeliminować potrzebę przewiń listę w dół. Aby uzyskać C++, IntelliCode zapewnia najbardziej pomoc, gdy przy użyciu popularnych bibliotek, takich jak biblioteki standardowej. Jest on dostępny jako składnik obciążenie w Instalatorze. Aby uzyskać więcej informacji, zobacz [AI-Assisted kod zakończenia sugestie osiągnięcie C++ za pomocą IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

### <a name="template-intellisense"></a>Szablon funkcji IntelliSense

**Pasek szablonu** używa teraz **wgląd w oknie** interfejsu użytkownika, a nie okno modalne obsługuje zagnieżdżone szablony i wstępnie wypełnia żadnych argumentów domyślnych do **wgląd w oknie**. Aby uzyskać więcej informacji, zobacz [szablonu ulepszeń funkcji IntelliSense dla programu Visual Studio 2019 r w wersji zapoznawczej 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/). A **ostatnio używane** liście rozwijanej **pasek szablonu** umożliwia szybkie przełączanie się między zestawami poprzedniej próbki argumentów.

### <a name="new-start-window-experience"></a>Nowe środowisko okna uruchamiania

Podczas uruchamiania IDE, nowe okno Start pojawia się z opcjami, aby otworzyć ostatnich projektów, klonowanie kodu z kontrolą źródła, otwórz kod lokalny jako rozwiązanie lub folder lub Utwórz nowy projekt. Okno dialogowe nowego projektu została przejrzana również w interfejsie wyszukiwania i filtrowania.

### <a name="new-names-for-some-project-templates"></a>Nowe nazwy dla niektórych szablonów projektu

Zmodyfikowaliśmy kilka nazwy szablonów projektu i opisy, aby dopasować przy użyciu zaktualizowanych okna dialogowego Nowy projekt.

### <a name="various-productivity-improvements"></a>Różne udoskonalenia dotyczące produktywności

Visual Studio 2019 obejmuje następujące funkcje, które ułatwi kodowania łatwiejsze i bardziej intuicyjne działanie:

- Szybkich poprawek dla:
  - Dodaj brakujące #include
  - Wartość NULL na wartość nullptr
  - Dodaj Brak średnika
  - Rozwiązanie Brak przestrzeni nazw lub zakresu
  - Zastąp operandy nieprawidłowy operator pośredni (\* do & a & do \*)
- Szybkie informacje w bloku, umieszczając kursor myszy na zamykający nawias klamrowy
- Zobacz nagłówek / plik kodu
- Przejdź do definicji #include otwiera plik

Aby uzyskać więcej informacji, zobacz [udoskonalenia dotyczące produktywności języka C++ w programie Visual Studio 2019 r w wersji zapoznawczej 2](https://devblogs.microsoft.com/cppblog/c-productivity-improvements-in-visual-studio-2019-preview-2/).

### <a name="quickinfo-improvements"></a>Ulepszenia skrócone informacje

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 wersji 16.1

Etykietki narzędzia Szybkie informacje uwzględnia teraz kolorowanie semantyczne edytora. Ponadto wprowadzono nową **Wyszukaj Online** łącze, które umożliwia wyszukiwanie dokumentów online dowiedzieć się więcej na temat konstrukcji kodu aktywowanego. Dla kodu graficzni red linku udostępnionego przez szybkie informacje wyszuka błąd w trybie online. Dzięki temu nie trzeba ponownie wpisz komunikat w przeglądarce. Aby uzyskać więcej informacji, zobacz [szybkie ulepszenia informacji w programie Visual Studio 2019 r.: Kolorowanie i wyszukaj w trybie Online](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/).

### <a name="intellicode-available-in-c-workload"></a>Rozszerzenie IntelliCode dostępne w C++ obciążenia

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 wersji 16.1

Rozszerzenie IntelliCode obecnie dostarczany jako opcjonalny składnik **programowanie aplikacji klasycznych przy użyciu C++**  obciążenia. Aby uzyskać więcej informacji, zobacz [Improved C++ IntelliCode jest teraz dostarczany z Visual Studio 2019](https://devblogs.microsoft.com/cppblog/improved-c-intellicode-now-ships-with-visual-studio-2019/).

## <a name="cmake-support"></a>Obsługa CMake

- Obsługa CMake 3,14

- Program Visual Studio teraz otworzyć istniejące narzędzia CMake pamięci podręcznych generowane przez zewnętrznych narzędzi, takich jak CMakeGUI, niestandardowej kompilacji meta systemów lub skrypty kompilacji, które wywołują cmake.exe samodzielnie.

- Zwiększono wydajność funkcji IntelliSense.

- Nowy edytor ustawień jest alternatywą dla ręcznego edytowania pliku CMakeSettings.json i udostępniają niektóre parzystości CMakeGUI.

- Program Visual Studio ułatwia rozpoczęcie programowania w języku C++ za pomocą narzędzia CMake w systemie Linux, wykrywając, czy na komputerze z systemem Linux znajduje się zgodna wersja narzędzia CMake. W przeciwnym razie umożliwia jej zainstalowanie dla Ciebie.

- Niezgodne ustawienia w pliku cmakesettings na pozycji, takich jak architektury niezgodnego lub niezgodne ustawienia generatora CMake, Pokaż faliste linie w edytorze kodu JSON i błędy na liście błędów.

- W projektach CMake otwieranych w środowisku IDE po uruchomieniu polecenia `vcpkg integrate install` automatycznie jest wykrywany i włączany łańcuch narzędzi vcpkg. To zachowanie można wyłączyć, określając pusty plik łańcucha narzędzi w pliku CMakeSettings.

- W projektach CMake domyślnie jest teraz włączane debugowanie Tylko mój kod.

- Ostrzeżenia analizy statycznej można teraz przetwarzać w tle i wyświetlać w edytorze projektów CMake.

- Co twórz i Konfiguruj komunikaty "begin" i "end" dla projektów CMake i pomoc techniczna dla programu Visual Studio postęp kompilacji interfejsu użytkownika. Ponadto ma teraz ustawienie szczegółowości CMake **Narzędzia > Opcje** dostosować poziom szczegółów komunikatów kompilacji i konfiguracji narzędzia CMake w oknie danych wyjściowych.

- `cmakeToolchain` Ustawienie jest teraz obsługiwana w pliku CMakeSettings.json, aby określić kompilatorach bez konieczności ręcznego modyfikowania wiersza polecenia narzędzia CMake.

- Nowy **kompilacji wszystkie** skrótu w menu **Ctrl + Shift + B**.

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 wersji 16.1

- Zintegrowana obsługa edycji, kompilowania i debugowania projektów CMake z wewnątrz platformy Clang/maszyny wirtualnej niskiego poziomu. Aby uzyskać więcej informacji, zobacz [Clang/LLVM obsługi w programie Visual Studio](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/).

## <a name="linux-and-the-windows-subsystem-for-linux"></a>Linux i podsystem Windows dla systemu Linux

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 wersji 16.1

- Obsługa [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) w projektach dla wielu platform Linux i narzędzia CMake. Aby uzyskać więcej informacji, zobacz [AddressSanitizer (ASan) w przypadku obciążeń systemu Linux w programie Visual Studio 2019](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/).

- Zintegrowana obsługa programu Visual Studio przy użyciu C++ z podsystemu Windows dla systemu Linux (WSL). Aby uzyskać więcej informacji, zobacz [ C++ za pomocą programu Visual Studio 2019 r i podsystemu Windows dla systemu Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

## <a name="incredibuild-integration"></a>IncrediBuild integracji

IncrediBuild jest dołączone jako składnik opcjonalny w **programowanie aplikacji klasycznych przy użyciu C++**  obciążenia. Monitor kompilacji IncrediBuild jest w pełni zintegrowana w środowisku IDE programu Visual Studio. Aby uzyskać więcej informacji, zobacz [wizualizować kompilacji za pomocą monitora kompilacji i Visual Studio 2019 r firmy IncrediBuild](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/).

## <a name="debugging"></a>Debugowanie

- Dla aplikacji C++ z systemem Windows pliki PDB teraz załadować w oddzielnym procesie 64-bitowych. Ta zmiana dotyczy szeroką gamę awarie spowodowane przez debuger brakować pamięci podczas debugowania aplikacji, które zawierają dużą liczbę moduły i pliki PDB.

- Wyszukiwanie jest włączone w **Obejrzyj**, **Autos**, i **lokalne** systemu windows.

## <a name="windows-desktop-development-with-c"></a>Programowanie aplikacji klasycznych Windows w języku C++

- Te kreatory C++ ATL/MFC nie są już dostępne:

  - Kreator składników ATL COM+ 1.0
  - Kreator składników stron Active Server ATL
  - Kreator dostawcy interfejsu OLE DB ATL
  - Kreator strony właściwości ATL
  - Kreator konsumenta OLE DB ATL
  - Odbiorca MFC ODBC
  - Klasa MFC z formantu ActiveX
  - Klasa MFC z biblioteki typów.

  Przykładowy kod dla tych technologii jest archiwizowane w Microsoft Docs i repozytorium VCSamples GitHub.

- Zestaw Windows 8.1 SDK nie jest już dostępny w instalatorze programu Visual Studio. Zalecamy uaktualnienie projektów w języku C++ na najnowszy zestaw Windows 10 SDK. W przypadku twardych zależności w 8.1, możesz pobrać go z archiwum zestaw Windows SDK.

- Obsługa systemu Windows XP nie będzie już dostępna w najnowszym zestawie narzędzi języka C++. XP określania wartości docelowej za pomocą kompilatora MSVC poziom programu VS 2017 i biblioteki jest nadal obsługiwane i można ją zainstalować za pomocą "Poszczególne składniki".

- Nasza dokumentacja aktywnie zniechęca do użycia modułów scalania w przypadku wdrożenia środowiska uruchomieniowego Visual C++. Przenosimy dodatkowego kroku tej wersji programu oznaczania naszych MSMs jako przestarzałe. Rozważ migrację wdrożenia centralnego VCRuntime z plików MSM do pakietu redystrybucyjnego.

## <a name="mobile-development-with-c-android-and-ios"></a>Tworzenie aplikacji mobilnych przy użyciu języka C++ (systemy Android i iOS)

Środowiskiem systemu Android dla języka C++ jest teraz domyślnie zestaw SDK 25 dla systemu Android i zestaw NDK 16b dla systemu Android.

## <a name="clangc2-platform-toolset"></a>Zestaw narzędzi platformy clang/C2

Składnik eksperymentalne Clang/C2 zostało usunięte. Zestaw narzędzi MSVC na użytek pełną zgodność ze standardami języka C++ z `/permissive-` i `/std:c++17`, lub łańcucha narzędzi Clang/LLVM dla Windows.

## <a name="code-analysis"></a>Analiza kodu

- Analiza kodu działa teraz automatycznie w tle. Ostrzeżenia są wyświetlane podczas pisania jako zielone podkreślenia w edytorze. Aby uzyskać więcej informacji, zobacz [analizy kodu w edytorze w programie Visual Studio 2019 r w wersji zapoznawczej 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/).

- Nowe reguły ConcurrencyCheck eksperymentalnych, dla typów biblioteki standardowej dobrze znanych z \<mutex > nagłówka. Aby uzyskać więcej informacji, zobacz [współbieżności analizy kodu w programie Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/).

- Zaktualizowany częściową implementację programu [sprawdzania profilu okres istnienia](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/), który wykrywa delegujące wskaźników i odwołań. Aby uzyskać więcej informacji, zobacz [okres istnienia Profile Update w wersji 2 (wersja zapoznawcza) 2019 r w usłudze Visual Studio](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/).

- Powiązane w koprocedury sprawdzeń, m.in. C26138 C26810, C26811 i reguły eksperymentalne C26800. Aby uzyskać więcej informacji, zobacz [nowy kod analizy sprawdza, czy w programie Visual Studio 2019: Użyj po przenoszenia i wspólną](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/).

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 wersji 16.1

- Nowe szybkich poprawek dla niezainicjowanej zmiennej. Aby uzyskać więcej informacji, zobacz [nowy kod analizy szybkich poprawek dla niezainicjowanej pamięci (C6001) i użyj przed ostrzeżenia init (C26494)](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/).

## <a name="unit-testing"></a>Testowanie jednostek

Szablon zarządzanego projektu testowego w języku C++ nie jest już dostępny. Aby kontynuować, przy użyciu struktury testowej C++ zarządzane w istniejących projektów. W przypadku nowych testów jednostkowych, zastanów się nad użyciem struktur natywnych testów, dla których program Visual Studio udostępnia szablony (MSTest, platformy Google Test) lub zarządzany C# szablonu projektu testu.

::: moniker-end

::: moniker range="=vs-2017"

Visual Studio 2017 obejmuje wiele aktualizacji i poprawek dotyczących środowiska języka C++. Już firma Microsoft usunęła ponad 250 usterek i zgłoszonych problemów w kompilatorze i narzędziach, wiele przesłanych przez klientów za pośrednictwem [zgłosić Problem i przekaż sugestię](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2017) opcji w obszarze **Wyślij opinię**. Dziękujemy za zgłaszanie usterek! Aby uzyskać więcej informacji na temat what's new in całego programu Visual Studio, zobacz [What's new in Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017?view=vs-2017). Aby uzyskać informacji na temat nowości w C++ w Visual Studio 2019 r, zobacz [What's new for C++ w programie Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Instrukcje dotyczące Nowości dla C++ w programie Visual Studio 2015 i wcześniejszych wersjach, zobacz [Visual C++ co to jest nowy 2003 2015 r](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>kompilator C++

### <a name="c-conformance-improvements"></a>Ulepszenia zgodności języka C++

W tej wersji zaktualizowaliśmy standardową bibliotekę i kompilator języka C++ o rozszerzoną obsługę funkcji języka C ++ 11 i C ++ 14, a także wstępną obsługę niektórych funkcji, które mają zostać uwzględnione w standardowym języku C ++ 17. Aby uzyskać szczegółowe informacje, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

Kompilator obsługuje około 75% funkcji, które są nowością w programie C ++ 17, w tym wiązania strukturyzowane, `constexpr` lambdy, `if constexpr`, zmienne wbudowane, złożyć wyrażenia i dodawanie `noexcept` do systemu typów. Te funkcje są dostępne w obszarze **/STD: c ++ 17** opcji. Aby uzyskać więcej informacji, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio 2017](cpp-conformance-improvements.md)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

Zestaw narzędzi kompilatora MSVC w wersji 15.7 programu Visual Studio jest teraz zgodny ze standardem C++. Aby uzyskać więcej informacji, zobacz [Announcing: MSVC jest zgodny ze standardem C++](https://devblogs.microsoft.com/cppblog/announcing-msvc-conforms-to-the-c-standard/) i [zgodność języka C++ firmy Microsoft](../visual-cpp-language-conformance.md).

### <a name="new-compiler-options"></a>Nowe opcje kompilatora

- [/ permissive-](../build/reference/permissive-standards-conformance.md): Włącz wszystkie rygorystyczne standardy zgodność-opcje kompilatora i Wyłącz większość rozszerzeń kompilatora specyficzne dla firmy Microsoft (ale nie `__declspec(dllimport)`, na przykład). Ta opcja jest włączona domyślnie w programie Visual Studio 2017 w wersji 15.5.  **/ Permissive-** tryb zgodności obejmuje obsługę dwufazowe wyszukiwanie nazw. Aby uzyskać więcej informacji, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio](cpp-conformance-improvements.md).

- [/ Diagnostics](../build/reference/diagnostics-compiler-diagnostic-options.md): Włącz wyświetlanie numer wiersza, numer wiersza i kolumny, lub numer wiersza i kolumny i karetki w ramach linii kodu, gdzie znaleziono diagnostycznych błąd lub ostrzeżenie.

- [/debug:fastlink](../build/reference/debug-generate-debug-info.md): Włącz do 30% szybciej konsolidowania przyrostowego czasu (w porównaniu. Visual Studio 2015), kopiując nie wszystkie informacje w pliku PDB debugowania. Plik PDB wskazuje zamiast tego informacje debugowania dla plików obiektów i biblioteki, użyty do utworzenia pliku wykonywalnego. Zobacz [C++ szybciej tworzyć cyklu w programie VS "15" z fastlink](https://devblogs.microsoft.com/cppblog/faster-c-build-cycle-in-vs-15-with-debugfastlink/) i [zalecenia dotyczące szybkości C++ kompilacje w programie Visual Studio](https://devblogs.microsoft.com/cppblog/recommendations-to-speed-c-builds-in-visual-studio/).

- Program Visual Studio 2017 umożliwia używanie [/SDL](../build/reference/sdl-enable-additional-security-checks.md) z [/ await](../build/reference/await-enable-coroutine-support.md). Firma Microsoft usunęła [usunęliśmy](../build/reference/rtc-run-time-error-checks.md) ograniczenie koprocedur.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15.3

- [/ STD: c ++ 14 i/STD: c ++ najnowsze](../build/reference/std-specify-language-standard-version.md): Te opcje kompilatora umożliwiają zgadzaj się na określonych wersji zestawu kodów ISO C++ języku programowania w projekcie. Nowy projekt funkcje warstwy standardowa jest chroniony przez większość **/STD: c ++ najnowsze** opcji.

- [/ STD: c ++ 17](../build/reference/std-specify-language-standard-version.md) udostępnia zestaw funkcji C ++ 17 implementowane przez kompilator. Ta opcja powoduje wyłączenie kompilatora i biblioteki standardowej obsługi funkcji, które zostały zmienione lub nowych wersjach pracy roboczą i wad aktualizacje C++ Standard po C ++ 17. Aby włączyć te funkcje, użyj **/STD: c ++ najnowsze**.

### <a name="codegen-security-diagnostics-and-versioning"></a>Generowanie kodu, zabezpieczeń, diagnostyki i przechowywania wersji

Ta wersja oferuje kilka ulepszeń w optymalizacji, generowania kodu, przechowywanie wersji zestawu narzędzi i diagnostyki. Do istotnych ulepszeń należą:

- Generowanie ulepszone kodu pętli: Obsługa automatycznej wektoryzacji dzielenia stałych liczb całkowitych, Lepsza identyfikacja wzorców funkcji memset.
- Ulepszone kodu zabezpieczeń: Ulepszona emisja diagnostyki kompilatora przepełnienia buforu, a [/GUARD: CF](../build/reference/guard-enable-control-flow-guard.md) teraz osłony instrukcje switch, które generują tabele przeskoków.
- Przechowywanie wersji: Wartość wbudowane makro preprocesora  **\_MSC\_VER** jest teraz monotonicznie aktualizowana przy każdej aktualizacji zestawu narzędzi Visual C++. Aby uzyskać więcej informacji, zobacz [Visual C++ w wersji kompilatora](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/).
- Nowy układ narzędzi: Kompilator i narzędzia powiązanych kompilacji ma nową strukturę lokalizacji i katalog na komputerze deweloperskim. Nowy układ umożliwia instalacje side-by-side wielu wersji kompilatora. Aby uzyskać więcej informacji, zobacz [układ narzędzia kompilatora w programie Visual Studio 2017](https://devblogs.microsoft.com/cppblog/compiler-tools-layout-in-visual-studio-15/).
- Ulepszona diagnostyka: W oknie danych wyjściowych zawiera obecnie kolumnę gdzie występuje błąd. Aby uzyskać więcej informacji, zobacz [ulepszenia diagnostyki kompilatora języka C++ w programie VS "15" Preview 5](https://devblogs.microsoft.com/cppblog/c-compiler-diagnostics-improvements-in-vs-15-rc/).
- Korzystając z procedur wspólnych eksperymentalne słowo kluczowe **uzyskanie** (dostępne w obszarze **/ await** opcja) została usunięta. Zaktualizować swój kod w celu zastosowania `co_yield` zamiast tego. Aby uzyskać więcej informacji, zobacz [ `yield` słowo kluczowe, aby stać się `co_yield` w programie VS 2017](https://devblogs.microsoft.com/cppblog/yield-keyword-to-become-co_yield-in-vs-2017/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15.3

Dodatkowe ulepszenia diagnostyki w kompilatorze. Aby uzyskać więcej informacji, zobacz [ulepszenia diagnostyki w programie Visual Studio 2017 15.3.0](https://devblogs.microsoft.com/cppblog/diagnostic-improvements-in-vs2017-15-3-0/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

Visual C++ runtime wydajności w dalszym ciągu poprawić ze względu na lepszą jakość wygenerowanego kodu. Teraz po prostu kompilację kodu, a aplikacja działa szybciej. Niektóre optymalizacje kompilatora są całkiem nowe, takich jak wektoryzację magazynów warunkowych wartości skalarnych, łączenie wywołań `sin(x)` i `cos(x)` w nowym `sincos(x)`i eliminowania nadmiarowe instrukcji od optymalizatora architektury SSA. Inne optymalizacje kompilatora są ulepszeniami istniejących funkcji, takich jak heurystyki Diagnostyka wektoryzowania automatycznego wyrażeń warunkowych, lepszej optymalizacji pętli i generowanie kodu minimalnej/maksymalnej float. Konsolidator ma nowy i szybsze **/OPT: ICF** implementacji, co może spowodować szybsze % do 9 w czasie konsolidacji i istnieją inne poprawki wydajności w łączenie przyrostowe. Aby uzyskać więcej informacji, zobacz [od (optymalizacje)](../build/reference/opt-optimizations.md) i [/incremental (Link przyrostowo)](../build/reference/incremental-link-incrementally.md).

Microsoft C++ kompilator obsługuje rozszerzenia AVX-512 firmy Intel, w tym instrukcje dotyczące długości wektora, które udostępniają nowe funkcje w AVX-512 do 128-bitowe i 256-bitowego rejestrach.

[/Zc:noexceptTypes-](../build/reference/zc-noexcepttypes.md) opcji może służyć do przywrócenia do języka C ++ 14 wersji `noexcept` podczas korzystania z języka C ++ 17 trybu ogólnie rzecz biorąc. Ta opcja pozwala zaktualizować kodzie źródłowym, aby były zgodne ze C ++ 17, bez konieczności ponownego zapisania wszystkie swoje `throw()` kodu w tym samym czasie. Aby uzyskać więcej informacji, zobacz [usuwanie specyfikacji wyjątków dynamicznych i noexcept](cpp-conformance-improvements.md#noexcept_removal).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Nowy przełącznik [/qspectre](../build/reference/qspectre.md) aby ułatwić uniknięcie przed atakami kanału po stronie wykonywania spekulacyjnego. Aby uzyskać więcej informacji, zobacz [krokami zaradczymi dla luki spectre w MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).
- Nowe ostrzeżenie diagnostycznych zaradcze dla luki Spectre. Aby uzyskać więcej informacji, zobacz [diagnostyczne w Visual Studio 2017 w wersji 15.7 w wersji zapoznawczej 4 krokami zaradczymi dla luki](https://devblogs.microsoft.com/cppblog/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/).
- Nową wartość dla /Zc, **użyciem**, pozwala rozwiązać raportowanie C++ standardową pomoc techniczną. Na przykład, gdy przełącznik jest ustawiona i kompilator jest w/STD: c ++ 17 tryb rozwija wartość **201703 L**. Aby uzyskać więcej informacji, zobacz [MSVC teraz poprawnie raporty __cplusplus](https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/).

## <a name="c-standard-library"></a>C++Standardowa biblioteka

### <a name="correctness-improvements"></a>Ulepszenia poprawność

##### <a name="visual-studio-2017-rtm-version-150"></a>Visual Studio 2017 RTM (version 15.0)

- Drobne `basic_string` `_ITERATOR_DEBUG_LEVEL != 0` ulepszenia diagnostyki. Wyzwolenie kontroli IDL w maszynie ciągu zgłasza teraz określone zachowanie, które spowodowało wyzwolenie. Na przykład zamiast komunikatu „iterator ciągu nie umożliwia wyłuskiwania” otrzymasz komunikat „nie można wyłuskać iteratora ciągu, ponieważ jest on poza zakresem (np. iterator końca)”.
- Naprawiono `std::promise` operator przypisania przenoszenia, który mógł wcześniej spowodować zablokowanie kodu.
- Naprawiono błędy kompilatora przy użyciu `atomic<T*>` niejawnej konwersji `T*`.
- `pointer_traits<Ptr>` wykrywa teraz prawidłowo `Ptr::rebind<U>`.
- Naprawiono Brak `const` kwalifikator w `move_iterator` operator odejmowania.
- Naprawiono ciche Generowanie nieprawidłowego kodu dla stanowych przydzielających definiowanych przez użytkownika żądających `propagate_on_container_copy_assignment` i `propagate_on_container_move_assignment`.
- `atomic<T>` Toleruje obecnie przeciążony `operator&()`.
- Nieco Ulepszona diagnostyka kompilatora dla niepoprawne `bind()` wywołania.

Aby uzyskać pełną listę ulepszeń biblioteki standardowej w programie Visual Studio 2017 RTM, zobacz C++ wpis w blogu zespołu [standardowe biblioteki poprawki w programie VS 2017 RTM](https://devblogs.microsoft.com/cppblog/stl-fixes-in-vs-2017-rtm/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15.3

- Kontenery standardowej biblioteki teraz clamp ich `max_size()` do `numeric_limits<difference_type>::max()` zamiast `max()` z `size_type`. Ta zmiana zapewnia, że wynik `distance()` na iteratorach z tego kontenera jest stałego w typie zwracanym `distance()`.
- Naprawiono Brak specjalizacji `auto_ptr<void>`.
- `for_each_n()`, `generate_n()`, I `search_n()` algorytmy poprzednio kompilacja nie powiodła się Jeśli długość argumentu nie jest typem całkowitym; teraz próba przekonwertować długości niecałkowitoliczbowego Iteratory `difference_type`.
- `normal_distribution<float>` już nie emituje ostrzeżenia w standardowej bibliotece o zawężanie z podwójnej precyzji do liczb zmiennoprzecinkowych.
- Rozwiązano niektóre `basic_string` operacje, które są używane `npos` zamiast `max_size()` podczas sprawdzania, czy przekroczono maksymalny rozmiar.
- `condition_variable::wait_for(lock, relative_time, predicate)` oczekiwania przez cały czas względne w przypadku wznawiania fałszywe. Teraz po upływie jednego interwał względne czasu.
- `future::get()` teraz unieważnia `future`, ponieważ wymaga standard.
- `iterator_traits<void *>` kiedyś poważny błąd, ponieważ próbowała ona formularza `void&`; teraz prawidłowo staje się pustą strukturę, zezwalając na używanie `iterator_traits` w "jest iteratorem" SFINAE warunków.
- Kilka ostrzeżeń zgłaszanych przez Clang **- wsystem — nagłówki** zostały rozwiązane.
- Również stała "Specyfikacja wyjątku w deklaracji niezgodna poprzedniej deklaracji" zgłoszony przez Clang **- Wmicrosoft — wyjątek specyfikacja**.
- Także Naprawiono mem inicjatora listy szeregowania ostrzeżęnia zgłoszone przez Clang i C1XX.
- Nieuporządkowane kontenery nie zamienić ich funkcje skrótu lub predykatów, gdy same kontenery zostały zamienione. Teraz im.
- Wiele operacji wymiany kontenera są teraz oznaczone `noexcept` (jak nasze biblioteki standardowej nigdy nie zamierza wyjątku podczas wykrywania non -`propagate_on_container_swap` alokatora niż równe niezdefiniowane zachowanie warunku).
- Wiele `vector<bool>` operacje, zostały oznaczone `noexcept`.
- Biblioteka standardowa teraz będzie wymuszać pasującego alokatora `value_type` (trybem C ++ 17) o rezygnacji z wyjście.
- Rozwiązano niektóre warunki, w przypadku, gdy samoobsługowego-range-insert into `basic_string` będzie szyfrują zawartości ciągów. (Uwaga: samoobsługowego-range-insert into wektorów nadal jest zabronione przez standardowe.)
- `basic_string::shrink_to_fit()` nie jest już jest zależna od alokatora `propagate_on_container_swap`.
- `std::decay` teraz obsługuje abominable funkcji typów, oznacza to, że funkcja typy, które są kwalifikowane stałych nietrwałych i/lub kwalifikowana ref.
- Zmienione dyrektyw rozróżnianie wielkości liter dla prawidłowego i ukośników poprawy przenoszenia.
- Naprawiono ostrzeżenie C4061 "moduł wyliczający"*modułu wyliczającego*'w przełączniku Enum'*wyliczenie*"nie jest jawnie obsługiwany przez etykietę case". To ostrzeżenie jest wyłączone domyślnie i została ustalona jako wyjątek do biblioteki standardowej zasady ogólne ostrzeżenia. (Standardowa biblioteka jest **/W4** czyszczenie, ale nie próbuje się **/Wall** czyste. Wiele ostrzeżeń wyłączone domyślnie są bardzo hałas i nie są przeznaczone do użycia w regularnych odstępach czasu.)
- Ulepszone `std::list` Debuguj testy. Listy wyboru teraz tworzyć Iteratory `operator->()`, i `list::unique()` teraz oznacza Iteratory, jako unieważnione.
- Naprawiono metaprogramowanie w używa alokatora `tuple`.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

- `std::partition` teraz wywołania razy predykatu N zamiast N + 1 godziny jako standard wymaga.
- Próbuje uniknąć Magiczna statyka w wersji 15.3 zostały naprawione w wersji 15.5.
- `std::atomic<T>` nie wymaga już `T` być konstrukcyjną domyślny.
- Algorytmy sterty trwać logarytmiczna nie jest już do potwierdzenia liniowo, że dane wejściowe są w rzeczywistości sterty po włączeniu debugowania iteratora.
- `__declspec(allocator)` teraz jest chroniony dla C1XX tylko zapobiec ostrzeżenia z Clang, który nie rozpoznaje tego declspec.
- `basic_string::npos` jest teraz dostępny jako stałą czasu kompilacji.
- `std::allocator` w trybie C ++ 17 teraz poprawnie obsługuje alokację typów nadmiernie wyrównanych, oznacza to, typów wyrównanie, w których jest większa niż `max_align_t`, chyba że wyłączone przez **/Zc:alignedNew-** .  Na przykład wektorami typów obiektów z 16-bajtowy lub 32-bajtowego wyrównania teraz są dobrze wyrównane do instrukcji SSE i AVX.

### <a name="conformance-improvements"></a>Ulepszenia zgodności

- Dodaliśmy \<wszelkie\>, \<string_view\>, `apply()`, `make_from_tuple()`.
- Dodano \<opcjonalne\>, \<wariant\>, `shared_ptr::weak_type`, i \<cstdalign\>.
- Włączone C ++ 14 `constexpr` w `min(initializer_list)`, `max(initializer_list)`, i `minmax(initializer_list)`, i `min_element()`, `max_element()`, i `minmax_element()`.

Aby uzyskać więcej informacji, zobacz [Visual C++ zgodność języka](../visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15.3

- Kilka dodatkowych funkcji C ++ 17 zostały zaimplementowane. Aby uzyskać więcej informacji, zobacz [Visual zgodność języka C++](cpp-conformance-improvements.md#improvements_153).
- Zaimplementowane P0602R0 "variant i opcjonalne powinien Propagacja triviality kopiowania/przenoszenia".
- Standardowa biblioteka oficjalnie Toleruje obecnie dynamiczne RTTI wyłączone za pomocą [trakcie](../build/reference/gr-enable-run-time-type-information.md) opcji. Zarówno `dynamic_pointer_cast()` i `rethrow_if_nested()` natury wymagają `dynamic_cast`, więc biblioteka standardowa teraz oznacza je jako `=delete` w obszarze **trakcie**.
- Nawet gdy RTTI dynamicznych została wyłączona za pomocą **trakcie**, "RTTI statyczne" w postaci `typeid(SomeType)` są nadal dostępne i obsługuje kilka składników biblioteki standardowej. Biblioteka standardowa obsługuje teraz, ta funkcja jest wyłączona, za pośrednictwem **/D\_HAS, Health\_STATYCZNE\_RTTI = 0**. Ta flaga powoduje również wyłączenie `std::any`, `target()` i `target_type()` funkcje elementów członkowskich `std::function`i `get_deleter()` funkcji elementu członkowskiego friend `std::shared_ptr` i `std::weak_ptr`.
- Standardowa biblioteka używa teraz C ++ 14 `constexpr` bezwarunkowo, zamiast warunkowo zdefiniowanych makra.
- Standardowa biblioteka używa teraz szablony aliasów wewnętrznie.
- Korzysta teraz z biblioteki standardowej `nullptr` wewnętrznie, zamiast z `nullptr_t{}`. (Wewnętrznego użycia wartości NULL została zlikwidowana. Użycie wewnętrznego 0 jako wartość null jest oczyszczany stopniowo.)
- Korzysta teraz z biblioteki standardowej `std::move()` wewnętrznie, zamiast stylistically niewłaściwie `std::forward()`.
- Zmienione `static_assert(false, "message")` do `#error message`. Ta zmiana zwiększa diagnostyki kompilatora, ponieważ `#error` natychmiast zatrzymuje kompilację.
- Standardowa biblioteka nie jest już oznacza funkcji jako `__declspec(dllimport)`. Konsolidator nowoczesnych technologii nie wymaga już go.
- Wyodrębnione SFINAE na domyślne argumenty szablonu, który skrócony zaśmiecania w porównaniu do typy zwracane i typy argumentów funkcji.
- Debugowania ewidencjonuje \<losowych\> teraz używać zwykle maszyny biblioteki standardowej, zamiast funkcji wewnętrznej `_Rng_abort()` której wywołać `fputs()` do **stderr**. Implementacja tej funkcji jest są zachowywane dla zgodność binarną, ale została usunięta w przyszłych wersjach niezgodne dane binarne w standardowej biblioteki.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

- Kilka funkcji standardowej biblioteki zostały dodane, przestarzałe lub usunięte zgodnie z standardzie C ++ 17. Aby uzyskać więcej informacji, zobacz [ C++ ulepszenia zgodności w programie Visual Studio](cpp-conformance-improvements.md#improvements_155).
- Eksperymentalna Obsługa następujące algorytmy równoległe:
  - `all_of`
  - `any_of`
  - `for_each`
  - `for_each_n`
  - `none_of`
  - `reduce`
  - `replace`
  - `replace_if`
  - `sort`
- Podpisy dla następujących algorytmy równoległe są dodane, ale nie została zrównoleglona w tej chwili; Profilowanie wykazało, że żadne korzyści w przekształcają algorytmy, które tylko przenieść lub permute — elementy:
  - `copy`
  - `copy_n`
  - `fill`
  - `fill_n`
  - `move`
  - `reverse`
  - `reverse_copy`
  - `rotate`
  - `rotate_copy`
  - `swap_ranges`

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 wersja 15.6

- \<memory_resource>
- Podstawowe informacje dotyczące biblioteki w wersji 1
- Usuwanie `polymorphic_allocator` przypisania
- Usprawnienie Wnioskowanie argumentu szablonu klasy

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Pomoc techniczna dotycząca algorytmów równoległych nie jest już eksperymentalne
- nową metodę implementacji \<filesystem >
- podstawowe ciąg konwersje (częściowa Obsługa)
- `std::launder()`
- `std::byte`
- `hypot(x,y,z)`
- unikanie niepotrzebnych zanikania
- Funkcje matematyczne specjalne
- `constexpr char_traits`
- Wnioskowanie przewodniki dotyczące biblioteki standardowej

Aby uzyskać więcej informacji, zobacz [Visual C++ zgodność języka](../visual-cpp-language-conformance.md).

### <a name="performance-and-throughput-fixes"></a>Wydajność i przepływność poprawki

- Wprowadzone `basic_string::find(char)` przeciąża wywołanie tylko `traits::find` po. Wcześniej została zaimplementowana jako ogólne wyszukiwanie ciągu o długości 1.
- `basic_string::operator==` teraz sprawdza, czy rozmiar ciągu przed porównaniem zawartości ciągów.
- Usunięto formant sprzężenia w `basic_string`, który był trudny Optymalizator kompilatora do analizy. Dla wszystkich krótkich ciągów wywoływanie `reserve` nadal ma niezerowy koszt bezczynności.
- `std::vector` został sprawdzony pod kątem prawidłowości i wydajności: Tworzenie aliasów podczas wstawiania i emplace — operacji jest teraz poprawnie obsługiwane zgodnie z wymaganiami standardu, gwarancja silnego wyjątku jest teraz udostępniany, gdy jest to wymagane przez Standard za pomocą `move_if_noexcept()` i innych Logika, wstawianie i emplace — wykonaj mniej operacji na elementach.
- C++ Biblioteki standardowej unika obecnie wyłuskiwania swobodnych pustych wskaźników.
- Ulepszone `weak_ptr::lock()` wydajności.
- Aby zwiększyć przepływność kompilatora C++ nagłówki standardowej biblioteki unikają teraz włączania deklaracji dla zbędnych funkcji wewnętrznych kompilatora.
- Zwiększona wydajność `std::string` i `std::wstring` konstruktorów przenoszenia więcej niż trzy razy.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15.3

- Pracował wokół interakcji z `noexcept` który uniemożliwił wbudowanie `std::atomic` implementacją na funkcje korzystające ze strukturą obsługi wyjątków (SEH).
- Zmienione, biblioteka standardowa przez wewnętrzny `_Deallocate()` funkcję, aby zoptymalizować do mniejszego kodu, dzięki któremu można wbudowana w większej liczbie miejsc.
- Zmienione `std::try_lock()` do użycia rozwinięcie pakietu zamiast rekursji.
- Ulepszone `std::lock()` algorytm uniknięcia zakleszczenia `lock()` operacji zamiast rotowania na `try_lock()` na wszystkich blokad.
- Włączono optymalizacji nazwanej zwracanej wartości w `system_category::message()`.
- `conjunction` i `disjunction` teraz wystąpienia N + 1 typów, zamiast 2N + 2 typy.
- `std::function` już nie tworzy wystąpienie programu przydzielania maszyn pomocy technicznej dla każdego typu wymazanego możliwy do wywołania, usprawnienie przepływności i zmniejszenie rozmiaru .obj w programach, które wiele odrębnych wyrażenia lambda można przekazać `std::function`.
- `allocator_traits<std::allocator>` zawiera ręcznie śródwierszowych `std::allocator` operacji, zmniejszyć rozmiar kodu w kodzie, który wchodzi w interakcję z `std::allocator` za pośrednictwem `allocator_traits` tylko (czyli w większość kodu).
- C ++ 11 interfejs minimalnych teraz odbywa się za pośrednictwem wywołania biblioteki standardowej `allocator_traits` bezpośrednio, zamiast zawijania alokator w Wewnętrzna klasa `_Wrap_alloc`. Ta zmiana zmniejsza rozmiar kod generowany dla obsługi alokatora, zwiększa możliwości optymalizatorowi przeglądanie informacji o kontenery standardowej biblioteki w niektórych przypadkach i zapewnia to lepszy proces debugowania (ponieważ spowoduje to wyświetlenie z typ programu przydzielania, a nie `_Wrap_alloc<your_allocator_type>`w debugerze).
- Usunięte metaprogramowanie, aby dostosować `allocator::reference`, buforów, które faktycznie nie są dozwolone do dostosowywania. (Buforów ułatwia kontenery, użyj swobodnych pustych wskaźników, ale nie ozdobnych odwołania.)
- Fronton kompilatora został prowadzone do odkodowania Iteratory debugowania w zakresie pętli for opierających, poprawia wydajność debugowania kompilacji.
- `basic_string` Ścieżki wewnętrznego zmniejszania dla `shrink_to_fit()` i `reserve()` nie jest już w ścieżce relokacja operacji, zmniejszyć rozmiar kodu dla wszystkich członków mutujące.
- `basic_string` Wewnętrzny rozwój ścieżka nie jest już w ścieżce `shrink_to_fit()`.
- `basic_string` Mutujące operacje teraz są rozkładane na — przydzielanie szybkiej ścieżki i alokowania funkcje powolną ścieżkę, dzięki czemu jest bardziej prawdopodobne w przypadku często spotykana Ponowna alokacja nie był śródwierszowy do obiektów wywołujących.
- `basic_string` Mutacja operacje po konstrukcji ponownie przydzielane buforów w żądanym stanie, a nie zmiany rozmiaru w miejscu. Na przykład wstawiania na początku ciągu teraz przenosi zawartości po wstawieniu dokładnie jeden raz (szczegółów lub do nowo przydzielonego buforu), zamiast dwa razy w przypadku reallocating (do nowo przydzielonego buforu, a następnie w dół).
- Operacje w przypadku wywoływania biblioteki standardowej C \<ciąg\> teraz w pamięci podręcznej `errno` adres do usunięcia powtarzanych interakcji z protokołem TLS.
- Uproszczony `is_pointer` implementacji.
- Zmianie na podstawie funkcji wyrażenie SFINAE do `struct` i `void_t`— na podstawie.
- Algorytmami standardowej biblioteki unikają teraz postincrementing Iteratory.
- Obcięcie stałej ostrzeżenia podczas korzystania z puli buforów 32-bitowych w 64-bitowych systemach.
- `std::vector` Dzięki ponownemu wykorzystaniu buforu, gdy jest to możliwe jest teraz bardziej efektywne w przypadku innych alokatora równe POCMA bez przeniesienia przypisania.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

- `basic_string<char16_t>` teraz angażuje takie same `memcmp`, `memcpy`i podobnie optymalizacje, `basic_string<wchar_t>` angażuje.
- Ograniczenie Optymalizator, które uniemożliwił wskaźników do funkcji miałyby śródwierszowych, udostępniane przez naszą pracę "należy unikać kopiowania funkcje" w programie Visual Studio 2015 Update 3, zostały pracował w całym, przywracanie wydajność `lower_bound(iter, iter, function pointer)`.
- Obciążenie debugowania iteratora w kolejności weryfikacji danych wejściowych `includes`, `set_difference`, `set_symmetric_difference`, i `set_union` został skrócony przez Odkodowywanie Iteratory przed zaewidencjonowaniem, order.
- `std::inplace_merge` teraz nakłada się na elementy, które znajdują się już w miejscu.
- Konstruowanie `std::random_device` już nie tworzy, a następnie niszczy `std::string`.
- `std::equal` i `std::partition` miał wątkowości Szybkie przebieg optymalizacji, która zapisuje porównanie iteratora.
- Gdy `std::reverse` jest przekazywany wskaźników do kopiowania `T`, teraz spowoduje wysłanie pisma odręcznego implementacji zwektoryzowane.
- `std::fill`, `std::equal`, i `std::lexicographical_compare` zostały prowadzone jak zostać wysłane żądanie `memset` i `memcmp` dla `std::byte` i `gsl::byte` (i inne typy wyliczeniowe przypominające znak i Wylicz klasy). Ponieważ `std::copy` wywołuje przy użyciu `is_trivially_copyable`, nie potrzebujesz, wszelkie zmiany.
- Standardowa biblioteka nie zawiera już destruktory nawiasów klamrowych pusty, którego jedynym zachowanie było typów innych niż przypadku zniszczalnych.

## <a name="other-libraries"></a>Inne biblioteki

### <a name="open-source-library-support"></a>Obsługa bibliotek typu open-source

**Vcpkg** to narzędzie wiersza polecenia typu open source, które znacząco upraszcza proces pobierania i tworzenia typu open-source C++ statycznej biblioteki i biblioteki dll w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [vcpkg: Menedżer pakietów dla języka C++](../build/vcpkg.md).

### <a name="cpprest-sdk-290"></a>Zestaw SDK CPPRest 2.9.0

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

CPPRestSDK, internetowy interfejs API dla wielu platform w języku C++, został zaktualizowany do wersji 2.9.0. Aby uzyskać więcej informacji, zobacz [CppRestSDK 2.9.0 jest dostępna w witrynie GitHub](https://devblogs.microsoft.com/cppblog/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

- Jeszcze inny zbiór poprawek zgodności wyszukiwania nazw
- Istniejące konstruktory przenoszenia i Przenieś operatory przypisania są teraz prawidłowo oznaczone jako niezgłaszające
- Unsuppress prawidłowe ostrzeżenie C4640 o bezpiecznym wątkowo programu w pliku atlstr.h
- Wątkowo inicjowanie lokalnych danych statycznych było automatycznie wyłączone w zestawie narzędzi XP podczas tworzenia biblioteki DLL przy użyciu biblioteki ATL, ale obecnie nie jest. Możesz dodać **threadsafeinit** w ustawieniach projektu, jeśli wymagane jest posiadanie wątkowo inicjowanie.

### <a name="visual-c-runtime"></a>Środowisko uruchomieniowe Visual C++

- Nowy nagłówek "cfguard.h" dla symboli ochrony przepływu sterowania.

## <a name="c-ide"></a>Środowisko IDE języka C++

- Wydajność wprowadzania zmian w konfiguracji jest teraz lepsza w przypadku natywnych projektów w języku C++ i o wiele lepsza w projektach C++/CLI. Jeśli Konfiguracja rozwiązania została aktywowana po raz pierwszy, będzie teraz szybsza i wszystkie nowsze aktywacje konfiguracji rozwiązania będą prawie natychmiastowe.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15.3

- Ponownie napisano kilka kreatorów projektu i kodów w stylu okna dialogowego podpisu.
- **Dodaj klasę** teraz powoduje bezpośrednie uruchomienie Kreatora dodawania klasy. Wszystkie inne elementy, które zostały wcześniej w tym miejscu są teraz dostępne w obszarze **Dodaj > Nowy element**.
- Projekty Win32 należą teraz w ramach **pulpitu Windows** kategorii **nowy projekt** okna dialogowego.
- **Konsoli Windows** i **aplikacja komputerowa** szablony teraz tworzenie projektów bez wyświetlania kreatora. Jest dostępny nowy **kreatora pulpitu Windows** w tej samej kategorii, który wyświetla te same opcje co stary **Aplikacja konsoli Win32** kreatora.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

Kilka operacji w języku C++, które używają aparatu funkcji IntelliSense dla refaktoryzacji i nawigowanie po kodzie działają dużo szybciej. Następujące numery opierają się na rozwiązanie Visual Studio chrom z projektami 3500:

|||
|-|-|
|Funkcja|Zwiększenie wydajności|
|Zmień nazwę|5.3 x|
|Zmień podpis |4,5 x|
|Znajdź wszystkie odwołania|4,7 x|

Język C++ obsługuje teraz Ctrl + kliknięcie **przejdź do definicji**, dzięki łatwo myszy nawigacji do definicji. Wizualizator struktury z dodatkiem Service pack Productivity Power Tools jest teraz również domyślnie w ramach produktu.

## <a name="intellisense"></a>IntelliSense

- Nowy aparat bazy danych oparty na SQLite jest teraz używany domyślnie. Przyspieszy to operacje bazy danych, takie jak **przejdź do definicji** i **Znajdź wszystkie odwołania**oraz znacznie skróci czas początkowego analizowania rozwiązania. To ustawienie zostało przeniesione do **Narzędzia > Opcje > Edytor tekstu > C/C++ > Zaawansowane** (wcześniej było dostępne w obszarze... C/C++ | Eksperymentalne).

- Poprawiliśmy wydajność funkcji IntelliSense dla projektów i plików, które nie używa prekompilowanych nagłówków — zostanie utworzony automatyczny prekompilowany nagłówek w bieżącym pliku dla nagłówków.

- Do listy błędów dodaliśmy filtrowanie błędów i pomoc dotyczącą błędów funkcji IntelliSense. Kliknięcie kolumny błędów umożliwia teraz filtrowanie. Ponadto kliknięcie konkretnego błędu lub naciśnięcie klawisza F1 uruchamia wyszukiwanie online dotyczące danego komunikatu o błędzie.

  ![Lista błędów](media/ErrorList1.png "Lista błędów")

  ![Filtrowana lista błędów](media/ErrorList2.png "Filtrowana lista błędów")

- Dodano możliwość filtrowania listy elementów członkowskich według rodzaju.

  ![Filtrowanie listy elementów członkowskich](media/mlfiltering.png "Filtrowanie listy elementów członkowskich")

- Dodano nową eksperymentalną funkcję Predictive IntelliSense, która pozwala na kontekstowe filtrowanie pozycji wyświetlanych na liście elementów członkowskich. Aby uzyskać więcej informacji, zobacz [ C++ ulepszeń funkcji IntelliSense - Predictive IntelliSense i filtrowanie](https://devblogs.microsoft.com/cppblog/c-intellisense-improvements-predictive-intellisense-filtering/).
- **Znajdź wszystkie odwołania** (Shift + F12) teraz pomaga obejść, nawet w przypadku złożonych bazach kodu. Umożliwia zaawansowane grupowanie, filtrowanie, sortowanie, wyszukiwanie w ramach wyników i (w przypadku niektórych języków) kolorowanie, dzięki czemu można uzyskać świadomość odwołaniami. Aby uzyskać C++, nowy interfejs użytkownika zawiera informacje na temat tego, czy firma Microsoft jest odczytujemy ze zmiennej czy zapisujemy do zmiennej.
- Funkcja zmiany kropki na strzałkę IntelliSense została przeniesiona z doświadczalnych do zaawansowanych i teraz jest domyślnie włączona. Funkcje edytora **rozwiń zakresy** i **rozwiń pierwszeństwo** również zostały przeniesione z doświadczalnych do zaawansowanych.
- Eksperymentalne funkcje refaktoryzacji **Zmień podpis** i **Wyodrębnij funkcję** są teraz dostępne domyślnie.
- Dodano eksperymentalną funkcję "Szybsze ładowanie projektu" dla C++ projektów. Gdy następnym razem otworzysz C++ projektu, będzie on ładować się szybciej, a po jej załaduje *znacznie* szybciej!
- Niektóre z tych funkcji są wspólne dla innych języków, a niektóre są specyficzne dla języka C++. Aby uzyskać więcej informacji o tych nowych funkcjach, zobacz [Announcing Visual Studio "15" (wersja zapoznawcza) 5](https://devblogs.microsoft.com/visualstudio/announcing-visual-studio-15-preview-5/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Obsługa dodane do narzędzia ClangFormat. Aby uzyskać więcej informacji, zobacz [obsługę formatu ClangFormat w programie Visual Studio 2017](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/).

## <a name="non-msbuild-projects-with-open-folder"></a>Projekty inne niż MSBuild z Otwórz Folder

Program Visual Studio 2017 wprowadzono **Otwórz Folder** funkcji, która umożliwia kodu, kompilacji i debugowania w folderze zawierające kod źródłowy, bez konieczności tworzenia żadnych rozwiązań lub projektów. Teraz jest znacznie prostsze rozpocząć pracę z programem Visual Studio, nawet jeśli projekt nie jest projektem opartych na platformie MSBuild. Za pomocą **Otwórz Folder**, uzyskasz dostęp do zaawansowanych kod, zrozumienie, edytowania, kompilowania i debugowania możliwości udostępnianych przez program Visual Studio już dla projektów programu MSBuild. Aby uzyskać więcej informacji, zobacz [Otwórz Folder projektów w języku C++](../build/open-folder-projects-cpp.md).

- Ulepszenia obsługi polecenia Otwórz folder. Środowisko można dostosować za pomocą tych plików JSON:
  - CppProperties.json dostosowuje obsługę funkcji IntelliSense i przeglądania.
  - Tasks.json dostosowuje kroki kompilacji.
  - Launch.json dostosowuje obsługę debugowania.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15.3

- Ulepszona obsługa środowiska kompilacji, takie jak rozwiązań MinGW i Cygwin i Kompilatory języka alternatywne. Aby uzyskać więcej informacji, zobacz [przy użyciu rozwiązań MinGW i Cygwin przy użyciu języka Visual C++ i otwórz Folder](https://devblogs.microsoft.com/cppblog/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Dodano obsługę definiowania zmiennych środowiskowych globalnych i specyficznych dla konfiguracji w plikach CppProperties.json i pliku CMakeSettings.json. Te zmienne środowiskowe mogą być używane przez konfiguracje debugowania definiowane w pliku launch.vs.json i zadań podrzędnych w pliku tasks.vs.json. Aby uzyskać więcej informacji, zobacz [Dostosowywanie środowiska Visual C++ i otwórz Folder](https://devblogs.microsoft.com/cppblog/customizing-your-environment-with-visual-c-and-open-folder/).
- Ulepszona obsługa generatora Ninja CMake, w tym możliwość platformami 64-bitowych.

## <a name="cmake-support-via-open-folder"></a>Obsługa CMake za pośrednictwem otwartego folderu

Program Visual Studio 2017 wprowadzono obsługę za pomocą projektów CMake, bez konwersji do MSBuild pliki projektu (.vcxproj). Aby uzyskać więcej informacji, zobacz [projektów CMake w programie Visual Studio](../build/cmake-projects-in-visual-studio.md). Otwarcie projektu CMake za pomocą **Otwórz Folder** automatycznie skonfiguruje środowisko dla języka C++, edytowania, kompilowania i debugowania.

- Funkcji C++ IntelliSense działa bez konieczności tworzenia pliku CppProperties.json w folderze głównym. Ponadto dodaliśmy nowe listy rozwijane, aby użytkownicy mogli łatwo przełączać się między konfiguracjami dostarczonymi przez pliki CMake i CppProperties.json.

- Dalsza konfiguracja jest obsługiwana przy użyciu pliku CMakeSettings.json, który znajduje się w tym samym folderze co plik CMakeLists.txt.

  ![Cmake Otwórz folder](media/cmake-cpp.png "CMake Otwórz folder")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15.3

- Obsługa dodane dla generatora Ninja narzędzia CMake.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

- Obsługa dodane do importowania dostępnych pamięci podręcznych narzędzia CMake.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

- Dodano obsługę narzędzia CMake 3.11, analizy kodu w projektach CMake, widok elementów docelowych w Eksploratorze rozwiązań, Opcje generowania pamięci podręcznej i kompilacja pojedynczego pliku. Aby uzyskać więcej informacji, zobacz [Obsługa CMake w programie Visual Studio](https://devblogs.microsoft.com/cppblog/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) i [projektów CMake w programie Visual Studio](../build/cmake-projects-in-visual-studio.md).

## <a name="windows-desktop-development-with-c"></a>Programowanie aplikacji klasycznych Windows w języku C++

Zapewniamy obecnie bardziej zaawansowane środowisko instalacji oryginalnego obciążenia C++. Dodaliśmy możliwe do wybrania składniki pozwalające na zainstalowanie tylko tych narzędzi, których potrzebujesz. Rozmiary wskazanej instalacji składników pokazane w Instalatorze interfejsu użytkownika nie są dokładne i zaniżają całkowity rozmiar.

Aby pomyślnie tworzyć projekty Win32 w obciążeniu C++ dla komputerów stacjonarnych, musisz zainstalować zarówno zestaw narzędzi, jak i zestaw SDK systemu Windows. Instalowanie zalecanych (zaznaczonych) składników **VC ++ 2017 narzędzi w wersji 141 (x86, x64)** i **zestawu Windows 10 SDK (10.0.nnnnn)** się upewnić, że działa. Jeśli potrzebne narzędzia nie są zainstalowane, projekty nie zostanie pomyślnie utworzony, a następnie zatrzyma kreatora.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

(Wcześniej dostępny jako autonomiczny produkt) Visual C++ Build tools są teraz uwzględnione jako obciążenie w Instalatorze programu Visual Studio. To obciążenie instaluje tylko narzędzia wymagane do kompilowania projektów języka C++, bez konieczności instalowania programu Visual Studio IDE. Uwzględniane są zarówno w wersji 140, jak i w wersji 141 zestawy narzędzi. Narzędzi w wersji 141 zawiera najnowszych ulepszeń w programie Visual Studio 2017 w wersji 15.5. Aby uzyskać więcej informacji, zobacz [Visual Studio Build Tools zawierają teraz programu VS 2017 i zestawy narzędzi MSVC VS2015](https://devblogs.microsoft.com/cppblog/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Programowanie dla systemu Linux przy użyciu języka C++

Popularne rozszerzenie [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) stanowi obecnie cześć programu Visual Studio. Ta instalacja zawiera wszystko, czego potrzebujesz do tworzenia i debugowania aplikacji w języku C++ działających w środowisku systemu Linux.

##### <a name="visual-studio-2017-version-152"></a>Visual Studio 2017 wersja 15.2

Wprowadzono ulepszenia w wizualizacji do udostępniania i typ kodu między platformami. Aby uzyskać więcej informacji, zobacz [ulepszenia języka Linux C++ dla wielu platform kod, udostępnianie i typ wizualizacji](https://devblogs.microsoft.com/cppblog/linux-cross-platform-and-type-visualization/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

- Obciążenie systemu Linux została dodana obsługa **rsync** jako alternatywę dla **sftp** synchronizowania plików do zdalnej maszyny z systemem Linux.
- Dodano obsługę wielu kompilacji przeznaczonych dla mikrokontrolerów ARM. Aby ją włączyć w instalacji, wybierz opcję **Linux development przy użyciu C++**  obciążenia i wybierz opcję dla **osadzonych i IoT rozwoju**. Ta opcja dodaje marki i kompilatora GCC ARM cross tools kompilacji do instalacji. Aby uzyskać więcej informacji, zobacz [kompilatorów GCC dla procesorów ARM Cross kompilacji, w programie Visual Studio](https://devblogs.microsoft.com/cppblog/arm-gcc-cross-compilation-in-visual-studio/).
- Obsługa dodane do narzędzia CMake. Teraz możesz pracować na istniejącej bazy kodu CMake bez konieczności konwertowania go do projektu programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md).
- Obsługa dodane do uruchamiania zadania zdalne. Ta funkcja umożliwia uruchamianie dowolnego polecenia w systemie zdalnym, który jest zdefiniowany w Menedżerze połączeń programu Visual Studio. Zadania zdalne udostępniają również możliwość kopiowania plików do systemu zdalnego.
Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Różne ulepszenia scenariusze obciążeń systemu Linux. Aby uzyskać więcej informacji, zobacz [ulepszenia obciążeniu C++ dla systemu Linux w systemie projektu, w oknie konsoli systemu Linux, polecenia rsync i Dołącz do procesu](https://devblogs.microsoft.com/cppblog/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).
- Funkcja IntelliSense dla nagłówków w zdalnych połączeń z systemem Linux. Aby uzyskać więcej informacji, zobacz [technologii IntelliSense dla zdalnych nagłówków Linux](https://devblogs.microsoft.com/cppblog/intellisense-for-remote-linux-headers/) i [Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Programowanie gier w języku C++

Pełnych możliwości języka C++ można użyć do tworzenia profesjonalnych gier obsługiwanych przy użyciu zestawu funkcji DirectX lub Cocos2d.

## <a name="mobile-development-with-c-android-and-ios"></a>Tworzenie aplikacji mobilnych przy użyciu języka C++ (systemy Android i iOS)

Program Visual Studio umożliwia obecnie programowanie i debugowanie aplikacji mobilnych przeznaczonych dla systemów Android oraz iOS.

## <a name="universal-windows-apps"></a>Aplikacje uniwersalne systemu Windows

Język C++ stanowi składnik opcjonalny obciążenia Aplikacja uniwersalna systemu Windows.  Obecnie uaktualnianie projektów C++ należy wykonywać ręcznie. Jeśli otworzysz w wersji 140 platformy uniwersalnej Windows projektu w programie Visual Studio 2017, musisz wybrać narzędzi platformy w wersji 141 na stronach właściwości projektu, jeśli nie masz zainstalowanego programu Visual Studio 2015.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nowe opcje dla języka C++ na uniwersalnej platformy Windows (UWP)

Masz teraz nowe opcje zapisywania i pakowania aplikacji w języku C++ platformy uniwersalnej Windows i Windows Store: Infrastrukturę Desktop Bridge pakietu istniejących aplikacji pulpitu lub obiektu COM dla wdrożenia za pośrednictwem Store Windows lub za pośrednictwem istniejących kanałów za pośrednictwem ładowania bezpośredniego. Nowe funkcje w systemie Windows 10 umożliwiają dodawanie funkcji platformy uniwersalnej systemu Windows do swojej aplikacji klasycznej na różne sposoby. Aby uzyskać więcej informacji, zobacz [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

A **projekt pakietu aplikacji Windows** szablonu projektu zostanie dodany, która znacząco upraszcza pakowania aplikacje klasyczne w języku Desktop Bridge. Jest on dostępny w obszarze **pliku | Nowe | Projekt | Zainstalowane | Wizualne C++ | Platforma Universal Windows**. Aby uzyskać więcej informacji, zobacz [pakietu aplikacji przy użyciu programu Visual Studio (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Jeśli piszesz nowy kod, możesz teraz użyć C++/WinRT, standardowy C++ projekcji języka dla Windows implementowanej wyłącznie w plikach nagłówkowych. Ona umożliwia zarówno tworzenie i używanie interfejsów API środowiska wykonawczego Windows przy użyciu dowolnej zgodnych ze standardami kompilator języka C++. C++/ WinRT ma na celu zapewnienie C++ deweloperom najwyższej jakości dostęp do nowoczesnego interfejsu Windows API. Aby uzyskać więcej informacji, zobacz [ C++/WinRT: Nowoczesne C++ dla środowiska uruchomieniowego Windows](https://moderncpp.com/).

Począwszy od kompilacji 17025 Windows SDK Insider Preview C++/WinRT znajduje się w zestawie Windows SDK. Aby uzyskać więcej informacji, zobacz [ C++/WinRT jest teraz dołączone do zestawu Windows SDK](https://devblogs.microsoft.com/cppblog/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="clangc2-platform-toolset"></a>Zestaw narzędzi platformy clang/C2

Zestaw narzędzi Clang/C2 dostarczany z programem Visual Studio 2017 obsługuje teraz **/bigobj** przełącznika, który jest kluczowy podczas kompilowania dużych projektów. Oferuje on również kilka ważnych poprawek, zarówno we frontonie, jak i zapleczu kompilatora.

## <a name="c-code-analysis"></a>Analiza kodu C++

Podstawowe narzędzia do sprawdzania kodu C++ wymuszające stosowanie [podstawowych wytycznych dotyczących języka C++](https://github.com/isocpp/CppCoreGuidelines) są obecnie dystrybuowane z programem Visual Studio. Po prostu włącz narzędzia do sprawdzania w **rozszerzenia analizy kodu** strony, strony właściwości projektu i rozszerzenia zostaną uwzględnione podczas uruchamiania analizy kodu. Aby uzyskać więcej informacji, zobacz [przy użyciu narzędzia do sprawdzania podstawowych wytycznych dotyczących języka C++](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Strona właściwości CppCoreCheck")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15.3

- Obsługa dodane do reguł związanych z zarządzaniem zasobami.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

- Nowe C++ obejmują sprawdzanie w podstawowych wytycznych dotyczących poprawności wskaźnika inteligentnego, poprawnego użycia inicjatorów globalnych i użycia flag konstrukcji, takich jak `goto` i zły rzutowania.

- Niektóre numery ostrzeżeń, które można znaleźć w wersji 15.3, nie są już dostępne w wersji 15.5. Ostrzeżenia te zostały zastąpione bardziej szczegółowymi operacjami sprawdzania.

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 wersja 15.6

- Obsługa dodane do pojedynczego pliku analiz i poprawę wydajności analizy w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [statycznej analizy ulepszenia dla języka C++ dla Visual Studio 2017 15.6 w wersji zapoznawczej 2](https://devblogs.microsoft.com/cppblog/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Dodane do pomocy technicznej [/ analyze: ruleset](../build/reference/analyze-code-analysis.md), który umożliwia określenie reguł analizy kodu, aby uruchomić.
- Dodano dodatkowe reguły z podstawowych wytycznych dotyczących języka C++ obsługę.  Aby uzyskać więcej informacji, zobacz [przy użyciu narzędzia do sprawdzania podstawowych wytycznych dotyczących języka C++](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing"></a>Testowanie jednostek

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

Adapter testowy Google i Boost.Test karty są teraz dostępne jako składniki **programowanie aplikacji klasycznych w języku C++** obciążenia i są zintegrowane z **Eksplorator testów**. Obsługa narzędzia CTest jest dodawany do projektów Cmake (za pomocą otwartego folderu), mimo że pełna integracja z **Eksplorator testów** nie jest jeszcze dostępna. Aby uzyskać więcej informacji, zobacz [pisanie testów jednostkowych dla języka C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp).

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 wersja 15.6

- Dodano obsługę dynamicznej biblioteki Boost.Test pomocy technicznej.
- Szablon elementu Boost.Test jest teraz dostępna w środowisku IDE.

Aby uzyskać więcej informacji, zobacz [Boost.Test Unit Testing: Dynamiczna obsługa bibliotek i nowego szablonu elementu](https://devblogs.microsoft.com/cppblog/boost-test-unit-testing-dynamic-library-support-and-new-item-template/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

[Funkcja CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) mechanizmu dodanego do C++ projektów testów jednostkowych. Aby uzyskać więcej informacji, zobacz [ogłoszenie CodeLens dla testów jednostkowych C++](https://devblogs.microsoft.com/cppblog/announcing-codelens-for-c-unit-testing/).

## <a name="visual-studio-graphics-diagnostics"></a>Visual Studio diagnostyki grafiki

Visual Studio diagnostyki grafiki jest zestaw narzędzi do rejestrowania i analizowania problemów renderowania i wydajności w aplikacjach Direct3D. Funkcje diagnostyki grafiki, może służyć z aplikacjami, które działają lokalnie na komputerze z systemem Windows, w emulatorze urządzenia Windows lub na zdalnym komputerze lub urządzeniu.

- **Dane wejściowe i wyjściowe dla programów do cieniowania geometrii i wierzchołka:** Możliwość wyświetlania danych wejściowych i wyjściowych programów do cieniowania wierzchołków i programów do cieniowania geometrii jest jedną z najbardziej pożądanych funkcji, i jest teraz obsługiwana w narzędziach. Po prostu wybierz etap programu VS lub GS w widoku etapy potoku, aby rozpocząć sprawdzanie danych wejściowych i wyjściowych w tabeli poniżej.

  ![Dane wejściowe/wyjściowe dla programów do cieniowania](media/io-shaders.png)

- **Wyszukiwanie i filtrowanie w tabeli obiektu:** Zapewnia szybki i łatwy sposób znaleźć zasoby, których szukasz.

  ![Wyszukaj](media/search.png)

- **Historia zasobów:** Ten nowy widok zapewnia uproszczony sposób wyświetlania historii całego modyfikacja zasobu, ponieważ został on użyty podczas renderowania przechwyconej ramki. Aby wywołać historii dla dowolnego zasobu, po prostu kliknij ikonę zegara, obok hiperłącze żadnych zasobów.

  ![Historia zasobów](media/resource-history.png)

  Spowoduje to wyświetlenie nowej **Historia zasobów** okna narzędzi, wypełniony historii zmian zasobu.

  ![Zmiana historię zasobu](media/resource-history-change.png)

  Jeśli Twoje przechwycenia za pomocą wywołania pełny stos przechwytywania włączone (**programu Visual Studio > Narzędzia > Opcje** w obszarze **Graphics Diagnostics**), kontekst każdego zdarzenia zmiany można szybko określić, a następnie i kontrolowane w projekcie programu Visual Studio.

- **Statystyka interfejsu API:** Wyświetl podsumowanie wysokiego poziomu użycia interfejsu API w sieci ramki. Jest przydatne do odnajdywania co wywołań, mogą nie okazuje się, należy na wszystkich lub wywołania, które wykonujesz zbyt dużej ilości. W tym oknie jest dostępna za pośrednictwem **Widok > Statystyka interfejsu API** w analizatora grafiki programu Visual Studio.

  ![Statystyka interfejsu API](media/api-stats.png)

- **Statystyki pamięci:** Wyświetl, ile pamięci sterownik jest przydzielanie zasobów tworzenie w ramce. W tym oknie jest dostępna za pośrednictwem **Widok > Statystyki pamięci** w **analizatora grafiki programu Visual Studio**. Dane mogą być kopiowane do pliku CSV do wyświetlenia w arkuszu kalkulacyjnym, klikając prawym przyciskiem myszy i wybierając pozycję **Kopiuj wszystko**.

  ![Statystyka pamięci](media/memory-stats.png)

- **Weryfikacja ramki:** Nowa lista błędów i ostrzeżeń pozwala łatwo można przejść do listy zdarzeń oparte na potencjalnych problemów wykrytych przez warstwę debugowania Direct3D. Kliknij przycisk **Widok > Weryfikacja ramki** w analizatora grafiki programu Visual Studio, aby otworzyć okno. Następnie kliknij przycisk **Uruchom weryfikację** można rozpocząć analizy. Może upłynąć kilka minut, w zależności od złożoności ramki.

  ![Weryfikacja ramki](media/frame-validation.png)

- **Analiza klatek D3D12:** Analiza klatek umożliwia analizowanie wydajności wywołania rysowania kierowanych eksperymentami "co jeśli". Przejdź na kartę analizy klatek i przeprowadzać analizę, aby wyświetlić raport. Aby uzyskać więcej informacji, obejrzyj [GoingNative 25: Analiza klatek grafiki programu Visual Studio](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) wideo.

  ![Analiza klatek](media/frame-analysis.png)

- **Ulepszenia użycia procesora GPU:** Otwórz ślady mogą być wykonywane za pomocą profilera użycie procesora GPU w usłudze Visual Studio przy użyciu widoku GPU lub narzędziu Analizator wydajności Windows (WPA) dla bardziej szczegółowej analizy. Jeśli masz zestaw narzędzi wydajności Windows, które zostały zainstalowane, istnieją dwa hiperłącza, jeden dla WPA i inny wpis dla widoku procesora GPU, w prawym dolnym rogu sesja — omówienie.

  ![Użycie procesora GPU](media/gpu-usage.png)

  Ślady otwierane w widoku GPU za pośrednictwem tego łącza pomocy technicznej synchronizowane powiększanie i przesuwanie na osi czasu między VS i wyświetlanie procesora GPU. Pole wyboru w programie VS jest używana do kontroli, czy włączona jest synchronizacja, czy nie.

  ![Wyświetl procesora GPU](media/gpu-view.png)

::: moniker-end

::: moniker range="=vs-2015"

Aby uzyskać pełną listę nowości pojawiły się za pomocą programu Visual Studio 2015 Update 3, zobacz [Visual C++ co to jest nowy 2003 2015 r](/cpp/porting/visual-cpp-what-s-new-2003-through-2015). Aby uzyskać więcej informacji na temat nowości we wszystkich programu Visual Studio 2015, zobacz informacje o wersji połączonej z usługą [Historia Visual Studio 2015 Release Notes](/visualstudio/releasenotes/vs2015-version-history). Aby uzyskać informacji na temat nowości w C++ w Visual Studio 2019 r, zobacz [What's new for C++ w programie Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Aby uzyskać informacji na temat nowości w C++ w programie Visual Studio 2017, zobacz [What's new for C++ w programie Visual Studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017).

::: moniker-end
