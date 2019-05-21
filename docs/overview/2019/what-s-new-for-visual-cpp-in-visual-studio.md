---
title: Co nowego w języku C++ w Visual Studio 2019 r.
ms.date: 05/13/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 19eaa9d4ed1cf12e721825f998fa674363eda488
ms.sourcegitcommit: 61121faf879cc581a4d39e4baccabf7cf1f673a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934142"
---
# <a name="whats-new-for-c-in-visual-studio-2019"></a>Co nowego w języku C++ w Visual Studio 2019 r.

Visual Studio 2019 obejmuje wiele aktualizacji i poprawek dotyczących środowiska Microsoft C++. Usunięto wiele usterek i problemów w kompilatorze i narzędziach, wiele przesłanych przez klientów za pośrednictwem [Zgłoś Problem](/visualstudio/how-to-report-a-problem-with-visual-studio-2017) i [sugestię](https://developercommunity.visualstudio.com/spaces/62/index.html) opcji w obszarze **Wyślij opinię**. Dziękujemy za zgłaszanie usterek! Aby uzyskać więcej informacji na temat what's new in całego programu Visual Studio, odwiedź stronę [What's new in Visual Studio](/visualstudio/ide/whats-new-visual-studio-2019).

## <a name="c-compiler"></a>kompilator C++

- Rozszerzona obsługa funkcji C ++ 17 i poprawki do poprawności, a także obsługę eksperymentalną funkcji C ++ 20 takich jak moduły i procedur wspólnych. Aby uzyskać szczegółowe informacje, zobacz [ulepszenia zgodności języka C++ w Visual Studio 2019](../cpp-conformance-improvements.md).

- `/std:c++latest` Teraz opcja powoduje dołączenie funkcji C ++ 20, które nie są zawsze kompletne, łącznie z obsługą początkowej dla operatora 20 C ++ \<= > pojazdu ("kosmicznego") dla trzykierunkowe porównywanie.

- Przełącznik kompilatora C++ `/Gm` jest już przestarzały. Rozważ wyłączenie `/Gm` przełącznika w skrypcie kompilacji, jeśli jest jawnie zdefiniowany. Jednakże można także zignorować ostrzeżenie o zakończeniu obsługi dla `/Gm`, ponieważ nie są traktowane jako błąd, gdy za pomocą "Traktuj ostrzeżenia jako błędy" (`/WX`).

- Po rozpoczęciu MSVC implementowania funkcji z języka C ++ 20 standardowy projekt w obszarze `/std:c++latest` flagi `/std:c++latest` jest teraz niezgodna z `/clr` (wszystkie odmian) `/ZW`, i `/Gm`. W programie Visual Studio 2019 r, użyj `/std:c++17` lub `/std:c++14` tryby podczas kompilowania za pomocą `/clr`, `/ZW` lub `/Gm` (ale zobacz poprzedni punkt).

- Prekompilowane nagłówki nie są już generowane domyślnie dla konsoli C++ i aplikacji klasycznych.

### <a name="codegen-security-diagnostics-and-versioning"></a>Generowanie kodu, zabezpieczeń, diagnostyki i przechowywania wersji

Lepsza analiza przy użyciu `/Qspectre` do udzielania pomocy środki zaradcze dla luki Spectre wariantu 1 (CVE-2017-5753). Aby uzyskać więcej informacji, zobacz [krokami zaradczymi dla luki Spectre w MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>Ulepszenia standardowej biblioteki języka C++

- Implementacja dodatkowe funkcje języka C ++ 17 i C ++ biblioteki 20 i poprawność poprawki. Aby uzyskać szczegółowe informacje, zobacz [ulepszenia zgodności języka C++ w Visual Studio 2019](../cpp-conformance-improvements.md).

- Clang-Format została zastosowana do C++ nagłówki standardowej biblioteki w celu zapewnienia lepszej czytelności.

- Ponieważ program Visual Studio teraz obsługuje tylko mój kod dla C++, standardowej biblioteki nie musi już podać niestandardowy mechanizm `std::function` i `std::visit` aby osiągnąć ten sam efekt. Usunięcie tej maszyny w dużym stopniu nie ma żadnych efektów widoczny dla użytkownika, z tą różnicą, że kompilator nie generuje diagnostyki, które wskazują na problemy w wierszu 15732480 lub 16707566 z \<type_traits > lub \<wariantu >.

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>Ulepszenia wydajności lub przepływności kompilator i standardową bibliotekę

- Ulepszenia przepływności, w tym sposób konsolidator obsługi We/Wy, kompilacji i połącz czas tworzenia i scalanie typu PDB.

- Dodano wsparcie podstawowe dla OpenMP SIMD wektoryzacji. Można je włączyć za pomocą nowego przełącznika kompilatora `-openmp:experimental`. Ta opcja umożliwia oznaczony za pomocą pętli `#pragma omp simd` do potencjalnie zwektoryzowana. Nie jest gwarantowana wektoryzacji i pętli z adnotacjami, ale nie jest zwektoryzowana zostanie wyświetlone ostrzeżenie, zgłaszane. Klauzule SIMD, nie są obsługiwane, są one po prostu ignorowane zgłosił ostrzeżenie.

- Dodano nowy przełącznik wiersza polecenia wbudowanie `-Ob3`, która jest nieco bardziej agresywnego `-Ob2`. `-O2` (Optymalizuj dane binarne dla szybkości) nadal oznacza `-Ob2` domyślnie. Jeśli okaże się, kompilator wystarczająco agresywnie nie wbudowanych, należy wziąć pod uwagę przekazywanie `-O2 -Ob3`.

- Aby zapewnić obsługę wektoryzacji pętli for z wywołania do funkcji bibliotek matematycznych i niektórych innych operacji, takich jak dzielenie liczby całkowitej ręcznie, Dodaliśmy obsługę funkcji wewnętrznych krótkich wektorów matematyczne biblioteki (SVML). Te funkcje obliczeniowe odpowiedniki wektor 128-bitowego, 256-bitowego lub 512-bitowe. Aby uzyskać definicje obsługiwanych funkcji, zobacz [Intel Intrinsic Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML) (Przewodnik wewnętrzny firmy Intel).

- Nowe i ulepszone optymalizacje:

  - Składania stałej i arytmetyczne definiowaniu wyrażeń przy użyciu funkcji wewnętrznych wektora SIMD, float i liczba całkowita formularzy.

  - Bardziej zaawansowanych analiz do wyodrębniania informacji z przepływu sterowania (instrukcji if/else/switch) do usunięcia gałęzi zawsze okazał się być prawdziwe lub fałszywe.

  - Ulepszone funkcji memset odwijania do zastosowania instrukcjami wektor SSE2.

  - Ulepszone usuwania kopii bezcelowe struct/class, szczególnie w przypadku programów C++, przekazywane przez wartość.

  - Ulepszona Optymalizacja kodu za pomocą `memmove`, takich jak `std::copy` lub `std::vector` i `std::string` konstrukcji.

- Zoptymalizowane pod kątem fizycznego projektu biblioteki standardowej w celu uniknięcia kompilowanie części biblioteki standardowej nie # dyrektywy #include Wycinanie w wysokości równej połowie czas kompilacji pusty plik, który zawiera tylko \<wektor >. W wyniku tej zmiany możesz może być konieczne dodanie # dyrektywy dla nagłówków, które zostały wcześniej pośrednio zawarte include. Na przykład, kod, który używa `std::out_of_range` teraz może być konieczne #include \<stdexcept >. Kod, który używa operatora wstawiania strumień może być konieczne #include \<ostream >. Korzyścią jest translacja tylko jednostek, które faktycznie przy użyciu \<stdexcept > lub \<ostream > składniki płacić przepływności kosztów do kompilowania ich.

- `if constexpr` została zastosowana w większej liczbie miejsc w standardowej bibliotece ulepszoną przepływność i rozmiar zmniejszenie kodu podczas operacji kopiowania, permutacji, takich jak wstecznego i Obróć i biblioteki algorytmów równoległych. 

- Standardowa biblioteka teraz używa wewnętrznie `if constexpr` zmniejszyć czasy kompilacji, nawet w tryb C ++ 14.

- Dynamiczne łączenie wykrywania dla biblioteki algorytmów równoległych już środowisko uruchomieniowe przechowuje całą stronę tablicy wskaźników funkcji. Oznaczenie tej pamięci tylko do odczytu został uznany za nie są już odpowiednie ze względów bezpieczeństwa.

- `std::thread`jego Konstruktor nie jest już oczekuje na uruchomienie wątku, a nie jest już wstawienia, wywołuje wiele warstw w funkcji, od podstawowej biblioteki języka C `_beginthreadex` i dostarczony obiekt możliwy do wywołania. Wcześniej `std::thread` 6 funkcje między put `_beginthreadex` i dostarczony obiekt możliwy do wywołania została zmniejszona do 3 tylko (2, które są po prostu `std::invoke`). To również rozwiązuje usterki zasłoniętej chronometrażu gdzie `std::thread`firmy powodujący zawieszanie konstruktora, jeśli zegar systemowy zmienione dokładnie w momencie `std::thread` został on utworzony.

- Naprawiono regresję wydajności w `std::hash` , wprowadziliśmy podczas implementowania `std::hash<std::filesystem::path>`.

- W kilku miejscach, w których korzysta teraz z biblioteki standardowej destruktory zamiast efektywnej bloków, aby osiągnąć poprawności. Skutkuje to lepszej interakcji debuger; wyjątki, które throw za pomocą biblioteki standardowej, w których to dotyczy lokalizacji będą teraz wyświetlane jako zgłaszane z ich oryginalnego lokalizacją throw, a nie naszych Zgłoś ponownie. Nie wszystkie bloki catch standardowej biblioteki zostały wyeliminowane; Oczekujemy, że liczba bloków catch obniżenie w kolejnych wersjach MSVC.

- Suboptymalny generowanie kodu w `std::bitset` spowodowane przez warunkowe throw wewnątrz noexcept funkcji został naprawiony, uwzględniając zgłaszanie ścieżkę.

- `std::list` i `std::unordered_*` rodziny korzystanie z Iteratory debugowanie w wielu miejscach.

- Kilka `std::list` elementy członkowskie zostały zmienione na ponowne użycie listy węzłów, jeśli jest to możliwe, zamiast cofanie przydziału i zmienianie ich alokacji. Na przykład, biorąc pod uwagę `list<int>` już o rozmiarze 3, wywołanie `assign(4, 1729)` teraz zastąpić liczby całkowite w pierwszym węzłów listy 3 i przydzielić jeden nowy węzeł listy z wartością 1729, zamiast dealokowanie wszystkie listy 3 węzły, a następnie przydzielanie 4 nowe listy węzłów s wartością 1729.

- Wszystkie wywołania biblioteki standardowej `erase(begin(), end())` zostały zmienione na `clear()`.

- `std::vector` teraz jest inicjowany i usuwa elementy efektywniej w niektórych przypadkach.

- Ulepszenia `std::variant` się bardziej Optymalizator przyjazne, co lepiej wygenerowanego kodu. Wbudowanie kodu jest teraz znacznie lepiej korzystać z `std::visit`.

## <a name="c-ide"></a>Środowisko IDE języka C++

### <a name="live-share-c-support"></a>Na żywo obsługi języka C++ udziału

[Na żywo udziału](/visualstudio/liveshare/) obsługuje obecnie C++, co pozwoli deweloperom współpracować w czasie rzeczywistym za pomocą programu Visual Studio lub Visual Studio Code. Aby uzyskać więcej informacji, zobacz [ogłoszenie funkcja udostępniania na żywo dla języka C++: Współpraca i udostępnianie w czasie rzeczywistym](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>Rozszerzenie IntelliCode dla języka C++

Rozszerzenie IntelliCode to opcjonalna rozszerzenia (dodany jako składnik obciążenia 16.1), korzystającą z własną rozbudowane szkolenia i kontekst kodu put, co to są najbardziej prawdopodobne do użycia na początku listy uzupełnianej. Często można to wyeliminować potrzebę przewiń listę w dół. Dla języka C++ IntelliCode zawiera większość pomocy w przypadku przy użyciu popularnych bibliotek, takich jak biblioteki standardowej. Aby uzyskać więcej informacji, zobacz [AI-Assisted kod zakończenia sugestie osiągnięcie C++ za pomocą IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

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

**Visual Studio 2019 version 16.1**

### <a name="quickinfo-improvements"></a>Ulepszenia skrócone informacje

Etykietki narzędzia Szybkie informacje uwzględnia teraz kolorowanie semantyczne edytora. Ponadto wprowadzono nową **Wyszukaj Online** łącze, które umożliwia wyszukiwanie dokumentów online dowiedzieć się więcej na temat konstrukcji kodu aktywowanego. Dla kodu graficzni red linku udostępnionego przez szybkie informacje wyszuka błąd w trybie online. Dzięki temu nie trzeba ponownie wpisz komunikat w przeglądarce. Aby uzyskać więcej informacji, zobacz [szybkie ulepszenia informacji w programie Visual Studio 2019 r.: Kolorowanie i wyszukaj w trybie Online](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/).

### <a name="intellicode-available-in-c-workload"></a>Rozszerzenie IntelliCode dostępne w C++ obciążenia

Rozszerzenie IntelliCode obecnie dostarczany jako opcjonalny składnik **programowanie aplikacji klasycznych przy użyciu C++**  obciążenia. Aby uzyskać więcej informacji, zobacz [Improved C++ IntelliCode jest teraz dostarczany z Visual Studio 2019](https://devblogs.microsoft.com/cppblog/).

## <a name="cmake-support"></a>Obsługa CMake

- Obsługa CMake 3,14

- Program Visual Studio teraz otworzyć istniejące narzędzia CMake pamięci podręcznych generowane przez zewnętrznych narzędzi, takich jak CMakeGUI, niestandardowej kompilacji meta systemów lub skrypty kompilacji, które wywołują cmake.exe samodzielnie.

- Zwiększono wydajność funkcji IntelliSense.

- Nowy edytor ustawień jest alternatywą dla ręcznego edytowania pliku CMakeSettings.json i udostępniają niektóre parzystości CMakeGUI.

- Program Visual Studio pomaga bootstrap oferowanych programowania C++ za pomocą narzędzia CMake w systemie Linux został określony poprzez wykrycie Jeśli masz zgodnej wersji CMake na maszynie z systemem Linux, a nie na zainstalowanie aplikacji za Ciebie.

- Niezgodne ustawienia w pliku cmakesettings na pozycji, takich jak architektury niezgodnego lub niezgodne ustawienia generatora CMake, Pokaż faliste linie w edytorze kodu JSON i błędy na liście błędów.

- W projektach CMake otwieranych w środowisku IDE po uruchomieniu polecenia `vcpkg integrate install` automatycznie jest wykrywany i włączany łańcuch narzędzi vcpkg. To zachowanie można wyłączyć, określając pusty plik łańcucha narzędzi w pliku CMakeSettings.

- W projektach CMake domyślnie jest teraz włączane debugowanie Tylko mój kod.

- Ostrzeżenia analizy statycznej można teraz przetwarzać w tle i wyświetlać w edytorze projektów CMake.

- Co twórz i Konfiguruj komunikaty "begin" i "end" dla projektów CMake i pomoc techniczna dla programu Visual Studio postęp kompilacji interfejsu użytkownika. Ponadto ma teraz ustawienie szczegółowości CMake **Narzędzia > Opcje** dostosować poziom szczegółów komunikatów kompilacji i konfiguracji narzędzia CMake w oknie danych wyjściowych.

- `cmakeToolchain` Ustawienie jest teraz obsługiwana w pliku CMakeSettings.json, aby określić kompilatorach bez konieczności ręcznego modyfikowania wiersza polecenia narzędzia CMake.

- Nowy **kompilacji wszystkie** skrótu w menu **Ctrl + Shift + B**.

**Visual Studio 2019 version 16.1**

- Zintegrowana obsługa edycji, kompilowania i debugowania projektów CMake z wewnątrz platformy Clang/maszyny wirtualnej niskiego poziomu. Aby uzyskać więcej informacji, zobacz [Clang/LLVM obsługi w programie Visual Studio](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/).

## <a name="linux-and-wsl"></a>Linux i WSL

**Visual Studio 2019 version 16.1**

- Obsługa [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) w projektach dla wielu platform Linux i narzędzia CMake. Aby uzyskać więcej informacji, zobacz [AddressSanitizer (ASan) w przypadku obciążeń systemu Linux w programie Visual Studio 2019](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/).

- Zintegrowana obsługa programu Visual Studio przy użyciu C++ z podsystemu Windows dla systemu Linux (WSL). Aby uzyskać więcej informacji, zobacz [ C++ za pomocą programu Visual Studio 2019 r i podsystemu Windows dla systemu Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

## <a name="incredibuild-integration"></a>IncrediBuild integracji

IncrediBuild jest dołączone jako składnik opcjonalny w **programowanie aplikacji klasycznych przy użyciu C++**  obciążenia. Monitor kompilacji IncrediBuild jest w pełni zintegrowana w środowisku IDE programu Visual Studio. Aby uzyskać więcej informacji, zobacz [wizualizować kompilacji za pomocą monitora kompilacji i Visual Studio 2019 r firmy IncrediBuild](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/).
 
## <a name="debugging"></a>Debugowanie

- Dla aplikacji C++ z systemem Windows pliki PDB teraz załadować w oddzielnym procesie 64-bitowych. Ta zmiana dotyczy szeroką gamę awarie spowodowane przez debuger brakować pamięci podczas debugowania aplikacji, które zawierają dużą liczbę moduły i pliki PDB.

- Wyszukiwanie jest włączone w **Obejrzyj**, **Autos**, i **lokalne** systemu windows.

## <a name="windows-desktop-development-with-c"></a>Programowanie aplikacji klasycznych Windows w języku C++

- Te kreatory C++ ATL/MFC nie są już dostępne:

  - Kreator 1.0 składnika ATL COM +
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

- Nowe eksperymentalne reguły ConcurrencyCheck dobrze znanych typów biblioteki standardowej z \<mutex > nagłówka. Aby uzyskać więcej informacji, zobacz [współbieżności analizy kodu w programie Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/).

- Zaktualizowany częściową implementację programu [sprawdzania profilu okres istnienia](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/), który wykrywa delegujące wskaźników i odwołań. Aby uzyskać więcej informacji, zobacz [okres istnienia Profile Update w wersji 2 (wersja zapoznawcza) 2019 r w usłudze Visual Studio](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/).

- Powiązane w koprocedury sprawdzeń, m.in. C26138 C26810, C26811 i reguły eksperymentalne C26800. Aby uzyskać więcej informacji, zobacz [nowy kod analizy sprawdza, czy w programie Visual Studio 2019: Użyj po przenoszenia i wspólną](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/).

**Visual Studio 2019 version 16.1**

Nowe szybkich poprawek dla niezainicjowanej zmiennej. Aby uzyskać więcej informacji, zobacz [nowy kod analizy szybkich poprawek dla niezainicjowanej pamięci (C6001) i użyj przed ostrzeżenia init (C26494)](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/).

## <a name="unit-testing"></a>Testowanie jednostek

Szablon zarządzanego projektu testowego w języku C++ nie jest już dostępny. Aby kontynuować, przy użyciu struktury testowej C++ zarządzane w istniejących projektów. W przypadku nowych testów jednostkowych, zastanów się nad użyciem struktur natywnych testów, dla których program Visual Studio udostępnia szablony (MSTest, platformy Google Test) lub zarządzany C# szablonu projektu testu.
