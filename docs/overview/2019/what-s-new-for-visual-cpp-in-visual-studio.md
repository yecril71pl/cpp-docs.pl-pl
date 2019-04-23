---
title: Co nowego w języku C++ w Visual Studio 2019 r.
ms.date: 04/02/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 493b96a8ce3359cc18287adbae8cbd6c374671ec
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779497"
---
<!--NOTE all https:// links to docs.microsoft.com need to be converted to site-relative links prior to publishing-->

# <a name="whats-new-for-c-in-visual-studio-2019"></a>Co nowego w języku C++ w Visual Studio 2019 r.

Visual Studio 2019 obejmuje wiele aktualizacji i poprawek dotyczących środowiska Microsoft C++. Firma Microsoft już usunięto wiele usterek i zgłoszonych problemów w kompilatorze i narzędziach, wiele przesłanych przez klientów za pośrednictwem witryny [Zgłoś Problem](/visualstudio/how-to-report-a-problem-with-visual-studio-2017) i [sugestię](https://developercommunity.visualstudio.com/spaces/62/index.html) opcji w obszarze **Prześlijopinię**. Dziękujemy za zgłaszanie usterek! Aby uzyskać więcej informacji na temat what's new in całego programu Visual Studio, odwiedź stronę [What's new in Visual Studio](/visualstudio/ide/whats-new-visual-studio-2019).

## <a name="c-compiler"></a>kompilator C++

- `/std:c++latest` Teraz opcja powoduje dołączenie funkcji C ++ 20, które nie są zawsze kompletne, łącznie z obsługą początkowej dla języka C ++ 20 operatora <> = ("pojazdu kosmicznego") dla trzykierunkowe porównywanie.

- [P0941R2 — makra feature-test](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html) zostanie zakończone, z obsługą `__has_cpp_attribute`. Makra Feature-test są obsługiwane we wszystkich trybach pracy standardowych.

- [C ++ 20 P1008R1 - zabronienia agregacji za pomocą zgłoszonych przez użytkownika konstruktorów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf) jest również zakończona.

- Rozszerzona obsługa funkcji C ++ 17, a także obsługę eksperymentalną funkcji C ++ 20 takich jak moduły i procedur wspólnych. Aby uzyskać szczegółowe informacje, zobacz [ulepszenia zgodności języka C++ w Visual Studio 2019](../cpp-conformance-improvements.md).

- Przełącznik kompilatora C++ `/Gm` jest już przestarzały. Rozważ wyłączenie `/Gm` przełącznika w skrypcie kompilacji, jeśli jest jawnie zdefiniowany. Jednakże można także zignorować ostrzeżenie o zakończeniu obsługi dla `/Gm`, ponieważ nie są traktowane jako błąd, gdy za pomocą "Traktuj ostrzeżenia jako błędy" (`/WX`).

- Prekompilowane nagłówki nie są już generowane domyślnie dla konsoli C++ i aplikacji klasycznych.

### <a name="codegen-security-diagnostics-and-versioning"></a>Generowanie kodu, zabezpieczeń, diagnostyki i przechowywania wersji

Lepsza analiza przy użyciu `/Qspectre` do udzielania pomocy środki zaradcze dla luki Spectre wariantu 1 (CVE-2017-5753). Aby uzyskać więcej informacji, zobacz [krokami zaradczymi dla luki Spectre w MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>Ulepszenia standardowej biblioteki języka C++

- [C++ 20 P0550R2 \(remove_cvref)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf) zostało zakończone.

- C ++ 17 \<charconv > została ulepszona to_chars() zmiennoprzecinkowe: najkrótszej chars_format::fixed jest 60 80% szybsze procesory, a chars_format::hex najkrótszej/dokładności zostało zakończone.

- Algorytmy więcej mieć zrównoleglona implementacje: is_sorted() is_sorted_until(), is_partitioned(), set_difference(), set_intersection(), is_heap(), is_heap_until().

- Ulepszenia `std::variant` się bardziej Optymalizator przyjazne, co lepiej wygenerowanego kodu. Wbudowanie kodu jest teraz znacznie lepiej korzystać z `std::visit`.

- Zastosowaliśmy clang-format do nagłówków standardowej biblioteki języka C++ w celu zapewnienia lepszej czytelności.

- Ulepszoną przepływność, gdy niektóre funkcje biblioteki standardowej są kompilowane przy użyciu `if constexpr`.

- Zoptymalizowane pod kątem fizycznego projektu biblioteki standardowej w celu uniknięcia kompilowanie części biblioteki standardowej nie # dyrektywy #include Wycinanie w wysokości równej połowie czas kompilacji pusty plik, który zawiera tylko \<wektor >.

## <a name="performancethroughput-fixes"></a>Wydajność/przepływności poprawki

- Ulepszenia przepływności, w tym sposób konsolidator obsługi We/Wy, kompilacji i połącz czas tworzenia i scalanie typu PDB.

- Dodano wsparcie podstawowe dla OpenMP SIMD wektoryzacji. Można je włączyć za pomocą nowego przełącznika CL `-openmp:experimental`. Ta opcja umożliwia oznaczony za pomocą pętli `#pragma omp simd` do potencjalnie zwektoryzowana. Nie jest gwarantowana wektoryzacji i pętli z adnotacjami, ale nie jest zwektoryzowana zostanie wyświetlone ostrzeżenie, zgłaszane. Klauzule SIMD, nie są obsługiwane, są one po prostu ignorowane zgłosił ostrzeżenie.

- Dodano nowy przełącznik wiersza polecenia wbudowanie `-Ob3`, która jest nieco bardziej agresywnego `-Ob2`. `-O2` (Optymalizuj dane binarne dla szybkości) nadal oznacza `-Ob2` domyślnie. Jeśli okaże się, kompilator wystarczająco agresywnie nie wbudowanych, należy wziąć pod uwagę przekazywanie `-O2 -Ob3`.

- Aby zapewnić obsługę wektoryzacji pętli for z wywołania do funkcji bibliotek matematycznych i niektórych innych operacji, takich jak dzielenie liczby całkowitej ręcznie, Dodaliśmy obsługę funkcji wewnętrznych krótkich wektorów matematyczne biblioteki (SVML). Te funkcje obliczeniowe odpowiedniki wektor 128-bitowego, 256-bitowego lub 512-bitowe. Aby uzyskać definicje obsługiwanych funkcji, zobacz [Intel Intrinsic Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML) (Przewodnik wewnętrzny firmy Intel).

- Nowe i ulepszone optymalizacje:

  - Składania stałej i arytmetyczne definiowaniu wyrażeń przy użyciu funkcji wewnętrznych wektora SIMD, float i liczba całkowita formularzy.

  - Bardziej zaawansowanych analiz do wyodrębniania informacji z przepływu sterowania (instrukcji if/else/switch) do usunięcia gałęzi zawsze okazał się być prawdziwe lub fałszywe.

  - Ulepszone funkcji memset odwijania do zastosowania instrukcjami wektor SSE2.

  - Ulepszone usuwania kopii bezcelowe struct/class, szczególnie w przypadku programów C++, przekazywane przez wartość.

  - Ulepszona Optymalizacja kodu za pomocą `memmove`, takich jak `std::copy` lub `std::vector` i `std::string` konstrukcji.

## <a name="c-ide"></a>Środowisko IDE języka C++

### <a name="live-share-c-support"></a>Na żywo obsługi języka C++ udziału

[Na żywo udziału](/visualstudio/liveshare/) obsługuje obecnie C++, co pozwoli deweloperom współpracować w czasie rzeczywistym za pomocą programu Visual Studio lub Visual Studio Code. Aby uzyskać więcej informacji, zobacz [ogłoszenie funkcja udostępniania na żywo dla języka C++: Współpraca i udostępnianie w czasie rzeczywistym](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>Rozszerzenie IntelliCode dla języka C++

Rozszerzenie IntelliCode to opcjonalne rozszerzenie korzystającą z własną rozbudowane szkolenia i kontekst kodu put, co to są najbardziej prawdopodobne do użycia na początku listy uzupełnianej. Często można to wyeliminować potrzebę przewiń listę w dół. Dla języka C++ IntelliCode zawiera większość pomocy w przypadku przy użyciu popularnych bibliotek, takich jak biblioteki standardowej. Aby uzyskać więcej informacji, zobacz [AI-Assisted kod zakończenia sugestie osiągnięcie C++ za pomocą IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

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

## <a name="cmake-support"></a>Obsługa CMake

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

## <a name="debugging"></a>Debugowanie

- Dla aplikacji C++ z systemem Windows pliki PDB teraz załadować w oddzielnym procesie 64-bitowych. Ta zmiana dotyczy szeroką gamę awarie spowodowane przez debuger brakować pamięci podczas debugowania aplikacji, które zawierają dużą liczbę moduły i pliki PDB.

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

## <a name="unit-testing"></a>Testowanie jednostek

Szablon zarządzanego projektu testowego w języku C++ nie jest już dostępny. Aby kontynuować, przy użyciu struktury testowej C++ zarządzane w istniejących projektów. W przypadku nowych testów jednostkowych, zastanów się nad użyciem struktur natywnych testów, dla których program Visual Studio udostępnia szablony (MSTest, platformy Google Test) lub zarządzany C# szablonu projektu testu.
