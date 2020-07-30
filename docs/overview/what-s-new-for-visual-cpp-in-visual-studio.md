---
title: Co nowego w języku C++ w programie Visual Studio
ms.date: 05/19/2020
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
ms.openlocfilehash: 28b3708c8064623a364b7a60eb63c508808b0a0b
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390003"
---
# <a name="whats-new-for-c-in-visual-studio"></a>Co nowego w języku C++ w programie Visual Studio

::: moniker range=">=vs-2019"

Program Visual Studio 2019 oferuje wiele aktualizacji i poprawek do środowiska Microsoft C++. Rozwiązano wiele usterek i problemów w kompilatorze i narzędziach. Wiele z tych problemów zostało przesłanych przez klientów w wyniku [zgłoszenia problemu](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019) i [udostępnienia opcji sugestii](https://developercommunity.visualstudio.com/spaces/62/index.html) w obszarze **Wyślij opinię**. Dziękujemy za zgłaszanie usterek! Aby uzyskać więcej informacji na temat nowości we wszystkich wersjach programu Visual Studio, zobacz [co nowego w programie Visual studio 2019](/visualstudio/ide/whats-new-visual-studio-2019). Aby uzyskać informacje na temat Nowości w języku C++ w programie Visual Studio 2017, zobacz [co nowego w języku c++ w programie Visual studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017). Aby uzyskać informacje na temat Nowości w języku C++ w programie Visual Studio 2015 i jego wcześniejszych wersjach, zobacz [Visual C++ co nowego 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>kompilator C++

- Ulepszona obsługa funkcji i poprawek w języku C++ 17 oraz Eksperymentalna obsługa funkcji języka C++ 20, takich jak moduły i współprocedury. Aby uzyskać szczegółowe informacje, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio 2019](cpp-conformance-improvements.md).

- Ta `/std:c++latest` opcja zawiera teraz funkcje języka c++ 20, które nie są gotowe, w tym wstępną obsługę operatora c++ 20 \<=> ("Spaceship") na potrzeby porównania trójwymiarowego.

- Przełącznik kompilatora języka C++ `/Gm` jest obecnie przestarzały. Rozważ wyłączenie `/Gm` przełącznika w skryptach kompilacji, jeśli jest on jawnie zdefiniowany. Można również bezpiecznie zignorować ostrzeżenia o zaniechaniu dla `/Gm` , ponieważ nie jest on traktowany jako błąd podczas używania "Traktuj ostrzeżenia jako błędy" ( `/WX` ).

- Ponieważ MSVC rozpoczyna Implementowanie funkcji ze standardowego projektu C++ 20 w ramach `/std:c++latest` flagi, `/std:c++latest` jest teraz niezgodne z `/clr` (wszystkie wersje), `/ZW` i `/Gm` . W programie Visual Studio 2019 Użyj `/std:c++17` lub `/std:c++14` trybów podczas kompilowania z `/clr` , `/ZW` lub `/Gm` (ale Zobacz poprzedni punktor).

- Prekompilowane nagłówki nie są już generowane domyślnie dla konsoli C++ i aplikacji klasycznych.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, zabezpieczenia, Diagnostyka i przechowywanie wersji

Ulepszona analiza z programem `/Qspectre` w celu zapewnienia pomocy w zakresie ograniczenia dla Spectre wariantu 1 (CVE-2017-5753). Aby uzyskać więcej informacji, zobacz [Spectree ograniczenia w MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>Ulepszenia standardowej biblioteki języka C++

- Implementacja dodatkowych funkcji i poprawek biblioteki C++ 17 i C++ 20. Aby uzyskać szczegółowe informacje, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio 2019](cpp-conformance-improvements.md).

- Clang-format został zastosowany do nagłówków standardowej biblioteki C++ w celu zwiększenia czytelności.

- Ponieważ program Visual Studio obsługuje teraz Tylko mój kod dla języka C++, standardowa biblioteka nie musi już zapewniać niestandardowych maszyn `std::function` i `std::visit` Aby osiągnąć ten sam efekt. Usuwanie maszyn w dużej mierze nie ma żadnych efektów widocznych dla użytkownika. Jedynym wyjątkiem jest to, że kompilator nie będzie już generować diagnostyki wskazującej problemy w wierszu 15732480 lub 16707566 \<type_traits> lub \<variant> .

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>Ulepszenia wydajności/przepływności w bibliotece kompilator i Standardowa

- Ulepszenia przepływności kompilacji, w tym sposób, w jaki konsolidator obsługuje operacje we/wy na plikach, oraz czas połączenia w przypadku scalania i tworzenia typu PDB.

- Dodano obsługę podstawową dla systemu OpenMP SIMD wektoryzacji. Można ją włączyć przy użyciu nowego przełącznika kompilatora **`/openmp:experimental`** . Ta opcja zezwala na używanie pętli `#pragma omp simd` do potencjalnie wektora. Wektoryzacji nie jest gwarantowany, natomiast pętle, które nie są wektorowe, zostaną wyświetlone ostrzeżenie. Nie są obsługiwane żadne klauzule SIMD; są one ignorowane i raportowane jest ostrzeżenie.

- Dodano nowy, wbudowany przełącznik wiersza polecenia **`/Ob3`** , który jest bardziej agresywną wersją programu **`/Ob2`** . **`/O2`**(Optymalizacja plików binarnych dla szybkości) nadal jest **`/Ob2`** Domyślnie implikowana. Jeśli okaże się, że kompilator nie działa w sposób agresywny, rozważ przekazanie **`/O2 -Ob3`** .

- Dodaliśmy obsługę funkcji wewnętrznych SVML (Short Vector Math Library). Te funkcje obliczają odpowiedniki wektorów 128-bitowe, 256-bitowe lub 512-bitowego. Dodaliśmy je do obsługi wektoryzacji pętli z wywołaniami funkcji biblioteki matematycznej i niektórych innych operacji, takich jak dzielenie liczby całkowitej. Aby uzyskać definicje obsługiwanych funkcji, zobacz [Intel Intrinsic Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML) (Przewodnik wewnętrzny firmy Intel).

- Nowe i ulepszone optymalizacje:

  - Uproszczone i arytmetyczne uproszczenia dla wyrażeń wykorzystujących wewnętrzne SIMD wektorowe, zarówno dla formularzy zmiennoprzecinkowych, jak i liczb całkowitych.

  - Bardziej wydajna analiza dla wyodrębniania informacji z przepływu sterowania (instrukcji if/else/Switch) w celu usunięcia gałęzi zawsze sprawdzanych pod kątem wartości true lub false.

  - Ulepszono funkcji memset odwrócenia, aby użyć instrukcji SSE2 Vector.

  - Ulepszone usuwanie bezużytecznych kopii struktury/klas, szczególnie w przypadku programów C++, które są przekazywane przez wartość.

  - Ulepszona Optymalizacja kodu przy użyciu `memmove` , takich jak `std::copy` lub `std::vector` i `std::string` konstrukcja.

- Zoptymalizowano fizyczny projekt biblioteki standardowej, aby uniknąć niebezpośredniego kompilowania części biblioteki standardowej. Ta zmiana spowoduje skrócenie czasu kompilacji pustego pliku, który zawiera tylko \<vector> połowę. W związku z tym może być konieczne dodanie `#include` dyrektyw dla nagłówków, które wcześniej zostały uwzględnione. Na przykład kod, który używa `std::out_of_range` może teraz być dodany `#include <stdexcept>` . Kod, który używa operatora wstawiania strumienia, może teraz być dodany `#include <ostream>` . Korzyść polega na tym, że tylko jednostki tłumaczenia faktycznie używające \<stdexcept> lub \<ostream> komponentów zwracają koszt przepływności w celu ich skompilowania.

- `if constexpr`został zastosowany w większej liczbie miejsc w standardowej bibliotece w celu zwiększenia przepływności i zmniejszenia rozmiaru kodu w operacjach kopiowania w permutacjach, takich jak odwracanie i obracanie, oraz w bibliotece algorytmów równoległych.

- Standardowa biblioteka jest teraz używana wewnętrznie `if constexpr` w celu skrócenia czasów kompilowania, nawet w trybie c++ 14.

- Wykrywanie dynamicznego łączenia środowiska uruchomieniowego dla biblioteki algorytmów równoległych nie używa już całej strony do przechowywania tablicy wskaźników funkcji. Oznaczenie tej pamięci jako tylko do odczytu nie jest już ważne ze względów bezpieczeństwa.

- `std::thread`Konstruktor nie czeka już na uruchomienie wątku i nie wstawia już tak wielu warstw wywołań funkcji między podstawową biblioteką C a podanym `_beginthreadex` możliwym do wywołania obiektem. Poprzednio `std::thread` umieścić sześć funkcji między `_beginthreadex` i podanym możliwym do nadania obiektowi. Ta liczba została zredukowana do trzech, z których tylko trzy `std::invoke` . Ta zmiana powoduje również rozwiązanie usterki powodującej zaciemnienie czasu, w której `std::thread` Konstruktor przestanie odpowiadać, jeśli zegar systemowy został zmieniony w chwili, gdy jest `std::thread` tworzony.

- Naprawiono regresję wydajności `std::hash` wprowadzoną podczas wdrażania `std::hash<std::filesystem::path>` .

- Biblioteka standardowa używa teraz destruktorów zamiast bloków catch w kilku miejscach, aby osiągnąć poprawność. Ta zmiana skutkuje lepszym interakcją debugera: wyjątki zgłaszane przez bibliotekę standardową w lokalizacjach, których dotyczy ta operacja, są teraz wyświetlane jako zgłoszone przez ich pierwotną witrynę throw, a nie z naszych ponownych alertów. Nie wszystkie bloki catch biblioteki standardowej zostały wyeliminowane. Oczekujemy, że liczba bloków catch zostanie zmniejszona w nowszych wersjach MSVC.

- Nieoptymalny codegen w wyniku `std::bitset` warunkowego zgłaszania wewnątrz funkcji noexcept został ustalony przez Rozstrzelenie ścieżki, która zostanie wyrzucana.

- Z `std::list` i `std::unordered_*` rodziną są używane Iteratory niebędące debugowaniem wewnętrznie w większej liczbie miejsc.

- Kilka `std::list` elementów członkowskich zostało zmienionych w celu ponownego użycia węzłów listy, tam gdzie jest to możliwe, a nie cofnięcia przydziału i ponownego przydzielenia. Na przykład w przypadku, gdy `list<int>` ma już rozmiar 3, wywołanie w celu zastąpi element `assign(4, 1729)` liczby całkowite w pierwszych trzech węzłach listy i przydzieli jeden nowy węzeł listy z wartością 1729.

- Wszystkie wywołania biblioteki standardowej `erase(begin(), end())` zostały zmienione na `clear()` .

- `std::vector`teraz inicjuje i wymazuje elementy bardziej wydajnie w niektórych przypadkach.

- Udoskonalenia w `std::variant` celu zwiększenia przyjaznego Optymalizatora, co prowadzi do lepszego wygenerowanego kodu. Tworzenie kodu w kodzie jest teraz znacznie lepszym rozwiązaniem `std::visit` .

## <a name="c-ide"></a>Środowisko IDE języka C++

### <a name="live-share-c-support"></a>Obsługa Live Share C++

[Live Share](/visualstudio/liveshare/) teraz obsługuje C++, dzięki czemu deweloperzy mogą korzystać z programu Visual Studio lub Visual Studio Code do współpracy w czasie rzeczywistym. Aby uzyskać więcej informacji, zobacz temat [ogłaszanie Live Share w języku C++: udostępnianie i współpraca w czasie rzeczywistym](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>Rozszerzenia intellicode dla języka C++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16.1

Rozszerzenia intellicode używa własnego rozbudowanego szkolenia i kontekstu kodu, aby określić, najprawdopodobniej z nich korzystasz w górnej części listy uzupełniania. Często może wyeliminować konieczność przewijania w dół listy. W przypadku języka C++ rozszerzenia intellicode oferuje największą pomoc w przypadku korzystania z popularnych bibliotek, takich jak standardowa biblioteka. Rozszerzenia intellicode jest opcjonalnym rozszerzeniem dostępnym jako składnik obciążenia w instalatorze. Aby uzyskać więcej informacji, zobacz temat [sugestie uzupełniania kodu z asystą w języku AI zostały przekazane do języka C++ za pośrednictwem rozszerzenia intellicode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

### <a name="template-intellisense"></a>IntelliSense szablonu

**Pasek szablonu** korzysta teraz z interfejsu użytkownika **okna wglądu** , a nie okna modalnego, obsługuje zagnieżdżone szablony i wstępnie wypełnia wszystkie argumenty domyślne w **oknie wgląd**. Aby uzyskać więcej informacji, zobacz artykuł [ulepszenia funkcji IntelliSense dla programu Visual Studio 2019 (wersja zapoznawcza 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/)). **Ostatnio używana** lista rozwijana na **pasku szablonu** pozwala szybko przełączać się między poprzednimi zestawami przykładowych argumentów.

### <a name="new-start-window-experience"></a>Nowe środowisko okna uruchamiania

Podczas uruchamiania środowiska IDE pojawia się nowe okno uruchamiania. Dostępne są opcje otwierania ostatnich projektów, klonowania kodu z kontroli źródła, otwierania kodu lokalnego jako rozwiązania lub folderu lub tworzenia nowego projektu. Okno dialogowe Nowy projekt zostało również przedzielone na wyszukanie, a następnie przeprowadzono filtrowanie.

### <a name="new-names-for-some-project-templates"></a>Nowe nazwy dla niektórych szablonów projektu

Zmodyfikowano kilka nazw i opisów szablonu projektu, aby dopasować je do zaktualizowanego okna dialogowego nowego projektu.

### <a name="various-productivity-improvements"></a>Różne ulepszenia produktywności

Program Visual Studio 2019 zawiera następujące funkcje, które ułatwiają tworzenie i bardziej intuicyjne kodowanie:

- Szybkie poprawki dla:
  - Dodaj brakujące #include
  - Wartość zerowa do nullptr
  - Dodaj brakujący średnik
  - Rozwiązywanie brakującej przestrzeni nazw lub zakresu
  - Zastąp złe operandy pośrednie ( \* do & i & do \* )
- Szybkie informacje dla bloku przez umieszczenie kursora w zamykającym nawiasie klamrowym
- Wgląd w plik nagłówka/kodu
- Przejdź do definicji na #include otwiera plik

Aby uzyskać więcej informacji, zobacz [ulepszenia produktywności w języku C++ w programie Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/c-productivity-improvements-in-visual-studio-2019-preview-2/).

### <a name="quickinfo-improvements"></a>Udoskonalenia sekcji szybkich informacji

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16.1

Etykietka Szybka podpowiedź teraz uwzględnia kolorowanie semantyczne edytora. Dostępne jest również nowe łącze **wyszukiwania online** , które umożliwia wyszukanie dokumentacji online w celu uzyskania dodatkowych informacji na temat aktywowanej konstrukcji kodu. Link dostarczony przez szybkie informacje dla kodu w kolorze czerwonym będzie szukać błędu w trybie online. Dzięki temu nie trzeba ponownie wpisywać komunikatu do przeglądarki. Aby uzyskać więcej informacji, zobacz [ulepszenia szybkiej informacji w programie Visual Studio 2019: kolorowanie i przeszukiwanie w trybie online](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/).

### <a name="intellicode-available-in-c-workload"></a>Rozszerzenia intellicode dostępne w obciążeniu C++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16.1

Rozszerzenia intellicode teraz dostarcza jako składnik opcjonalny do **tworzenia aplikacji klasycznych przy użyciu obciążenia C++** . Aby uzyskać więcej informacji, zobacz [udoskonalony język C++ rozszerzenia intellicode teraz dostarczany z programem Visual Studio 2019](https://devblogs.microsoft.com/cppblog/improved-c-intellicode-now-ships-with-visual-studio-2019/).

## <a name="cmake-support"></a>Obsługa CMake

- Obsługa CMake 3,14

- Program Visual Studio może teraz otwierać istniejące pamięci podręczne CMake wygenerowane przez narzędzia zewnętrzne, takie jak CMakeGUI, dostosowane systemy meta-Build lub skrypty kompilacji, które wywołują cmake.exe.

- Ulepszona wydajność funkcji IntelliSense.

- Nowy edytor ustawień oferuje alternatywę do ręcznego edytowania CMakeSettings.jsw pliku i zapewnia pewną zgodność z CMakeGUI.

- Program Visual Studio ułatwia rozpoczęcie programowania w języku C++ za pomocą narzędzia CMake w systemie Linux, wykrywając, czy na komputerze z systemem Linux znajduje się zgodna wersja narzędzia CMake. W przeciwnym razie umożliwia jej zainstalowanie dla Ciebie.

- Niezgodne ustawienia w pliku cmakesettings, takie jak niezgodne architektury lub niezgodne ustawienia generatora CMake, pokazują zygzaki w edytorze JSON i błędy na liście błędów.

- W projektach CMake otwieranych w środowisku IDE po uruchomieniu polecenia `vcpkg integrate install` automatycznie jest wykrywany i włączany łańcuch narzędzi vcpkg. To zachowanie można wyłączyć, określając pusty plik łańcucha narzędzi w pliku CMakeSettings.

- W projektach CMake domyślnie jest teraz włączane debugowanie Tylko mój kod.

- Ostrzeżenia analizy statycznej są teraz przetwarzane w tle i wyświetlane w edytorze dla projektów CMake.

- Wyraźniejsze Kompilowanie i Konfigurowanie komunikatów "BEGIN" i "End" dla projektów CMake i obsługi interfejsu użytkownika postępu kompilacji programu Visual Studio. Ponadto istnieje teraz ustawienie szczegółowości CMake w obszarze **narzędzia > opcje** umożliwiające dostosowanie poziomu szczegółowości komunikatów kompilacji CMAKE i konfiguracji w okno dane wyjściowe.

- To `cmakeToolchain` ustawienie jest teraz obsługiwane w CMakeSettings.jsna, aby określić łańcuchy narzędzi bez ręcznej modyfikacji wiersza polecenia CMAKE.

- Nowe menu **Kompiluj wszystkie** skróty **Ctrl + Shift + B**.

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16.1

- Zintegrowana obsługa edytowania, kompilowania i debugowania projektów CMake przy użyciu Clang/LLVM. Aby uzyskać więcej informacji, zobacz [Clang/LLVM Support in Visual Studio](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/).

## <a name="linux-and-the-windows-subsystem-for-linux"></a>Linux i podsystem Windows dla systemu Linux

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16.1

- Obsługa [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) w projektach dla wielu platform w systemach Linux i CMAKE. Aby uzyskać więcej informacji, zobacz [AddressSanitizer (ASan) dla obciążenia systemu Linux w programie Visual Studio 2019](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/).

- Zintegrowana obsługa programu Visual Studio na potrzeby używania języka C++ z podsystemem Windows dla systemu Linux (WSL). Aby uzyskać więcej informacji, zobacz [C++ za pomocą programu Visual Studio 2019 i podsystemu Windows dla systemu Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

## <a name="incredibuild-integration"></a>Integracja IncrediBuild

IncrediBuild jest dołączany jako składnik opcjonalny do **tworzenia aplikacji klasycznych przy użyciu obciążenia C++** . Monitor kompilacji IncrediBuild jest w pełni zintegrowany w środowisku IDE programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Wizualizacja kompilacji za pomocą monitora kompilacji IncrediBuild i programu Visual Studio 2019](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/).

## <a name="debugging"></a>Debugowanie

- W przypadku aplikacji C++ działających w systemie Windows pliki PDB są teraz ładowane w osobnym procesie 64-bitowym. Ta zmiana dotyczy zakresu awarii spowodowanych brakiem pamięci przez debuger. Na przykład podczas debugowania aplikacji zawierających dużą liczbę modułów i plików PDB.

- Wyszukiwanie jest włączone w oknach **czujka**, **autostarty**i **lokalne** .

## <a name="windows-desktop-development-with-c"></a>Programowanie aplikacji klasycznych systemu Windows przy użyciu języka C++

- Te kreatory C++ ATL/MFC nie są już dostępne:

  - Kreator składników ATL COM+ 1.0
  - Kreator składnika stron Active Server ATL
  - Kreator dostawcy interfejsu OLE DB ATL
  - Kreator strony właściwości ATL
  - Kreator konsumenta OLE DB ATL
  - Odbiorca MFC ODBC
  - Klasa MFC z kontrolki ActiveX
  - Klasa MFC z typu lib.

  Przykładowy kod dla tych technologii został zarchiwizowany w witrynie Microsoft Docs i w repozytorium GitHub VCSamples.

- Zestaw Windows 8.1 Software Development Kit (SDK) nie jest już dostępny w Instalatorze programu Visual Studio. Zalecamy uaktualnienie projektów C++ do najnowszej wersji Windows 10 SDK. Jeśli masz stałą zależność od systemu w wersji 8.1, możesz pobrać go z archiwum zestawu Windows SDK.

- Obsługa systemu Windows XP nie będzie już dostępna w najnowszym zestawie narzędzi języka C++. Program XP obsługujący biblioteki MSVC & kompilatora programu VS 2017 na poziomie jest nadal obsługiwany i można go zainstalować za pomocą "poszczególnych składników".

- Nasza dokumentacja aktywnie zniechęca do użycia modułów scalania w przypadku wdrożenia środowiska uruchomieniowego Visual C++. Zajmiemy się dodatkowymi krokami w tej wersji o oznaczaniu naszych MSMs jako przestarzałych. Rozważ migrację wdrożenia centralnego VCRuntime z plików MSM do pakietu redystrybucyjnego.

## <a name="mobile-development-with-c-android-and-ios"></a>Programowanie aplikacji mobilnych za pomocą języka C++ (Android i iOS)

Środowiskiem systemu Android dla języka C++ jest teraz domyślnie zestaw SDK 25 dla systemu Android i zestaw NDK 16b dla systemu Android.

## <a name="clangc2-platform-toolset"></a>Zestaw narzędzi platformy Clang/C2

Składnik eksperymentalny Clang/C2 został usunięty. Użyj zestawu narzędzi MSVC, aby uzyskać pełną zgodność ze standardami języka C++ z `/permissive-` `/std:c++17` systemami i lub CLANG/LLVM łańcucha narzędzi dla systemu Windows.

## <a name="code-analysis"></a>Analiza kodu

- Analiza kodu działa teraz automatycznie w tle. Ostrzeżenia są wyświetlane podczas pisania jako zielone podkreślenia w edytorze. Aby uzyskać więcej informacji, zobacz [Analiza kodu w edytorze w programie Visual Studio 2019 (wersja zapoznawcza 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/)).

- Nowe eksperymentalne reguły ConcurrencyCheck dla dobrze znanych standardowych typów bibliotek z \<mutex> nagłówka. Aby uzyskać więcej informacji, zobacz [Analiza kodu współbieżności w programie Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/).

- Zaktualizowana częściowa implementacja [Narzędzia sprawdzania profilu okresu istnienia](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/), która wykrywa zawieszonegoe wskaźniki i odwołania. Aby uzyskać więcej informacji, zobacz [Aktualizacja profilu okresu istnienia w programie Visual Studio 2019 (wersja zapoznawcza 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/)).

- Więcej kontroli związanych z innymi procedurami, w tym C26138, C26810, C26811 i doświadczalną regułę C26800. Aby uzyskać więcej informacji, zobacz [nowe sprawdzenia analizy kodu w programie Visual Studio 2019: Użyj funkcji-After-Move i wspólnej](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/).

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16.1

- Nowe szybkie poprawki dla niezainicjowanych testów zmiennych. Aby uzyskać więcej informacji, zobacz [nowe szybkie poprawki analizy kodu dla niezainicjowanej pamięci (C6001) i używane przed ostrzeżeniami init (C26494)](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/).

## <a name="unit-testing"></a>Testowanie jednostek

Szablon zarządzanego projektu testowego w języku C++ nie jest już dostępny. Można nadal używać zarządzanej platformy testów C++ w istniejących projektach. W przypadku nowych testów jednostkowych należy rozważyć użycie jednego z natywnych platform testowych, dla których program Visual Studio udostępnia szablony (MSTest, Google Test) lub szablon projektu testu zarządzanego w języku C#.

::: moniker-end

::: moniker range="=vs-2017"

Program Visual Studio 2017 udostępnia wiele aktualizacji i poprawek do środowiska języka C++. Naprawiono ponad 250 usterek i zgłoszono problemy w kompilatorze i narzędziach. Wiele przesłanych przez klientów w wyniku [zgłoszenia problemu i udostępnienia opcji sugestii](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2017) w obszarze **Wyślij opinię**. Dziękujemy za zgłaszanie usterek! Aby uzyskać więcej informacji na temat nowości we wszystkich wersjach programu Visual Studio, zobacz [co nowego w programie Visual studio 2017](/visualstudio/ide/whats-new-visual-studio-2017?view=vs-2017). Aby uzyskać informacje na temat Nowości w języku C++ w programie Visual Studio 2019, zobacz [co nowego w języku c++ w programie Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Aby uzyskać informacje na temat Nowości w języku C++ w programie Visual Studio 2015 i jego wcześniejszych wersjach, zobacz [Visual C++ co nowego 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="visual-studio-2017-c-compiler"></a>Kompilator języka Visual Studio 2017 C++

### <a name="c-conformance-improvements"></a>Ulepszenia zgodności języka C++

Zaktualizowaliśmy kompilator i standardową bibliotekę języka C++ w tej wersji z ulepszoną obsługą funkcji języka C++ 11 i C++ 14. Obejmuje to również wstępną obsługę pewnych funkcji, które powinny być w standardzie C++ 17. Aby uzyskać szczegółowe informacje, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

Kompilator obsługuje około 75% funkcji, które są nowością w języku C++ 17, w tym powiązania strukturalne, **`constexpr`** wyrażenia lambda, `if constexpr` zmienne wbudowane, zapełnianie wyrażeń i Dodawanie **`noexcept`** do systemu typu. Te funkcje są dostępne w ramach **`/std:c++17`** opcji. Aby uzyskać więcej informacji, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio 2017](cpp-conformance-improvements.md)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

Zestaw narzędzi kompilatora MSVC w programie Visual Studio w wersji 15,7 jest teraz zgodny ze standardem C++. Aby uzyskać więcej informacji, zobacz temat [ogłaszanie: MSVC jest zgodny ze standardem c++](https://devblogs.microsoft.com/cppblog/announcing-msvc-conforms-to-the-c-standard/) i [zgodnym z językiem Microsoft c++](../visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-158"></a>Visual Studio 2017 w wersji 15,8

[`/experimental:preprocessor`](../build/reference/experimental-preprocessor.md)Przełącznik kompilatora włącza nowy eksperymentalny preprocesor MSVC, który będzie ostatecznie zgodny ze wszystkimi odpowiednimi standardami C i C++. Aby uzyskać więcej informacji, zobacz [MSVC eksperymentalny preprocesora — Omówienie](../preprocessor/preprocessor-experimental-overview.md).

### <a name="new-compiler-options"></a>Nowe opcje kompilatora

- [`/permissive-`](../build/reference/permissive-standards-conformance.md): Włącz wszystkie ścisłe normy zgodne z opcjami kompilatora i Wyłącz większość rozszerzeń kompilatora specyficznych dla firmy Microsoft ( `__declspec(dllimport)` na przykład). Ta opcja jest domyślnie włączona w programie Visual Studio 2017 w wersji 15,5.  **`/permissive-`** Tryb zgodności obejmuje obsługę dwuetapowego wyszukiwania nazw. Aby uzyskać więcej informacji, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio](cpp-conformance-improvements.md).

- [`/diagnostics`](../build/reference/diagnostics-compiler-diagnostic-options.md): Umożliwia wyświetlanie błędu diagnostyki lub lokalizacji ostrzegawczej na trzy różne sposoby: tylko numer wiersza, numer wiersza i kolumny, numer wiersza i kolumnę, z karetką pod nieprawidłowym wierszem kodu.

- [`/debug:fastlink`](../build/reference/debug-generate-debug-info.md): Włącz do 30% szybszych przyrostowych czasów linków (vs. Visual Studio 2015), nie kopiując wszystkich informacji debugowania do pliku PDB. Zamiast tego plik PDB wskazuje informacje o debugowaniu dla plików obiektu i biblioteki użytych do utworzenia pliku wykonywalnego. Zobacz [szybszy cykl kompilacji c++ w programie vs "15" `/Debug:fastlink` ](https://devblogs.microsoft.com/cppblog/faster-c-build-cycle-in-vs-15-with-debugfastlink/) i [zalecenia dotyczące przyspieszenia kompilacji C++ w programie Visual Studio](https://devblogs.microsoft.com/cppblog/recommendations-to-speed-c-builds-in-visual-studio/).

- Program Visual Studio 2017 umożliwia korzystanie [`/sdl`](../build/reference/sdl-enable-additional-security-checks.md) z programu z usługą [`/await`](../build/reference/await-enable-coroutine-support.md) . Usunięto [`/RTC`](../build/reference/rtc-run-time-error-checks.md) ograniczenie przy użyciu procedur wspólnych.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- [ `/std:c++14` i `/std:c++latest` ](../build/reference/std-specify-language-standard-version.md): te opcje kompilatora umożliwiają wybór określonych wersji języka programowania ISO C++ w projekcie. Większość nowych funkcji w wersji Standard jest chronionych przez **`/std:c++latest`** opcję.

- [`/std:c++17`](../build/reference/std-specify-language-standard-version.md)Włącza zestaw funkcji języka C++ 17 wdrożonych przez kompilator. Ta opcja powoduje wyłączenie obsługi biblioteki kompilatora i standardowej dla funkcji po C++ 17: te, które są zmieniane lub nowe w nowszych wersjach roboczej wersji roboczej, oraz aktualizacje usterek w standardzie C++. Aby włączyć te funkcje, użyj programu **`/std:c++latest`** .

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, zabezpieczenia, Diagnostyka i przechowywanie wersji

W tej wersji wprowadzono kilka ulepszeń optymalizacji, generowania kodu, przechowywania wersji zestawu narzędzi i diagnostyki. Do istotnych ulepszeń należą:

- Ulepszone generowanie kodu pętli: obsługa automatycznej wektoryzacji dzielenia stałych liczb całkowitych, lepsza identyfikacja wzorców funkcji memset.
- Ulepszone zabezpieczenia kodu: Ulepszona emisja diagnostyki kompilatora przepełnienia buforu i [`/guard:cf`](../build/reference/guard-enable-control-flow-guard.md) teraz chroni instrukcje Switch, które generują tabele skoku.
- Przechowywanie wersji: wartość wbudowanego makra preprocesora monotonicznie jest teraz aktualizowana ** \_ \_ ** w każdej aktualizacji zestawu narzędzi Visual C++. Aby uzyskać więcej informacji, zobacz [Visual C++ wersja kompilatora](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/).
- Nowy układ zestawu narzędzi: kompilator i powiązane narzędzia do kompilacji mają nową lokalizację i strukturę katalogów na komputerze deweloperskim. Nowy układ umożliwia instalacje równoległe wielu wersji kompilatora. Aby uzyskać więcej informacji, zobacz [układ narzędzi kompilatora w programie Visual Studio 2017](https://devblogs.microsoft.com/cppblog/compiler-tools-layout-in-visual-studio-15/).
- Ulepszona diagnostyka: w oknie danych wyjściowych jest teraz wyświetlana kolumna, w której występuje błąd. Aby uzyskać więcej informacji, zobacz [ulepszenia diagnostyki kompilatora języka C++ w programie vs "15" (wersja zapoznawcza 5](https://devblogs.microsoft.com/cppblog/c-compiler-diagnostics-improvements-in-vs-15-rc/)).
- W przypadku korzystania ze współprocedur, wartość eksperymentalne **słowo kluczowe** (dostępne w ramach **`/await`** opcji) zostało usunięte. Kod powinien zostać zaktualizowany do użycia `co_yield` zamiast tego. Aby uzyskać więcej informacji, zobacz [ `yield` słowo kluczowe, aby przejść do `co_yield` programu vs 2017](https://devblogs.microsoft.com/cppblog/yield-keyword-to-become-co_yield-in-vs-2017/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

Dodatkowe ulepszenia diagnostyki w kompilatorze. Aby uzyskać więcej informacji, zobacz [udoskonalenia diagnostyczne w programie Visual Studio 2017 15.3.0](https://devblogs.microsoft.com/cppblog/diagnostic-improvements-in-vs2017-15-3-0/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

Wydajność środowiska uruchomieniowego Visual C++ w dalszym ciągu ulepsza jakość kodu. Teraz możesz po prostu ponownie skompilować kod i aplikacja działała szybciej. Niektóre optymalizacje kompilatora są zupełnie nowe, takie jak wektoryzacji warunkowych magazynów skalarnych, łączenie wywołań `sin(x)` i `cos(x)` nowe `sincos(x)` oraz Usuwanie nadmiarowych instrukcji z Optymalizatora ochrony zdarzeń. Inne optymalizacje kompilatora to ulepszenia istniejących funkcji, takie jak: heurystyka wektoryzator dla wyrażeń warunkowych, lepsza Optymalizacja pętli i zmiennoprzecinkowa minimalna/maksymalna codegena. Konsolidator ma nową i szybszą **`/OPT:ICF`** implementację, co może skutkować do 9% przyspieszenia czasu linku i innych poprawek wydajności w konsolidacji przyrostowej. Aby uzyskać więcej informacji, zobacz [/opt (optymalizacje)](../build/reference/opt-optimizations.md) i [/Incremental (łączenie przyrostowo)](../build/reference/incremental-link-incrementally.md).

Kompilator języka Microsoft C++ obsługuje firmę Intel AVX-512. Zawiera instrukcje długości wektora, które wprowadzają nowe funkcje w AVX-512 do 128-bitowe i 256-bit Wide.

Opcja [/Zc: noexceptTypes —](../build/reference/zc-noexcepttypes.md) umożliwia przywrócenie do wersji c++ 14 systemu, w którym jest **`noexcept`** używany tryb c++ 17. Ta opcja umożliwia zaktualizowanie kodu źródłowego tak, aby był zgodny z językiem C++ 17 bez konieczności ponownego pisania całego `throw()` kodu. Aby uzyskać więcej informacji, zobacz sekcję [usuwanie specyfikacji wyjątków dynamicznych i noexcept](cpp-conformance-improvements.md#noexcept_removal).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Nowy przełącznik kompilatora [/Qspectre](../build/reference/qspectre.md) , aby pomóc w wyeliminowaniu ataków na kanał po stronie wykonywania spekulacyjnego. Aby uzyskać więcej informacji, zobacz [Spectree ograniczenia w MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).
- Nowe ostrzeżenie diagnostyczne na potrzeby ograniczenia Spectre. Aby uzyskać więcej informacji, zobacz [Spectre Diagnostic in Visual Studio 2017 w wersji 15,7 Preview 4](https://devblogs.microsoft.com/cppblog/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/).
- Nowa wartość dla/Zc, **`/Zc:__cplusplus`** , umożliwia poprawne raportowanie standardowej obsługi języka C++. Na przykład, gdy przełącznik jest ustawiony i kompilator jest w **`/std:c++17`** trybie, wartość rozwija się do **`201703L`** . Aby uzyskać więcej informacji, zobacz [MSVC teraz prawidłowo raporty __cplusplus](https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/).

## <a name="c-standard-library"></a>Standardowa biblioteka C++

### <a name="correctness-improvements"></a>Ulepszenia poprawności

##### <a name="visual-studio-2017-rtm-version-150"></a>Visual Studio 2017 RTM (wersja 15,0)

- `basic_string` `_ITERATOR_DEBUG_LEVEL != 0` Ulepszenia diagnostyki pomocniczej. Gdy sprawdzanie IDL jest wyzwalane w maszynach ciągów, będzie teraz raportowane określone zachowanie, które spowodowało wydrukowanie. Na przykład zamiast komunikatu „iterator ciągu nie umożliwia wyłuskiwania” otrzymasz komunikat „nie można wyłuskać iteratora ciągu, ponieważ jest on poza zakresem (np. iterator końca)”.
- Naprawiono `std::promise` operator przypisania przenoszenia, który wcześniej mógłby spowodować zablokowanie kodu na zawsze.
- Naprawiono błędy kompilatora z `atomic<T*>` niejawną konwersją na `T*` .
- `pointer_traits<Ptr>`teraz poprawnie wykrywane `Ptr::rebind<U>` .
- Naprawiono brakujący **`const`** kwalifikator w `move_iterator` operatorze odejmowania.
- Rozwiązano cichą codegeną nieprawidłowym dla stanowych zdefiniowanych przez użytkownika przystawek `propagate_on_container_copy_assignment` z żądaniem i `propagate_on_container_move_assignment` .
- `atomic<T>`teraz dopuszczalne są przeciążenia `operator&()` .
- Nieco Ulepszona diagnostyka kompilatora dla nieprawidłowych `bind()` wywołań.

Program Visual Studio 2017 RTM zawiera więcej ulepszeń biblioteki standardowej. Aby zapoznać się z pełną listą, zobacz temat poprawki biblioteki standardowej wpisu w blogu dla języka C++ [w programie VS 2017 RTM](https://devblogs.microsoft.com/cppblog/stl-fixes-in-vs-2017-rtm/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- Kontenery biblioteki standardowej teraz zawężają zamiast `max_size()` `numeric_limits<difference_type>::max()` `max()` `size_type` . Ta zmiana gwarantuje, że wynik `distance()` iteratorów z tego kontenera jest reprezentowany w zwracanym typie `distance()` .
- Naprawiono brak specjalizacji `auto_ptr<void>` .
- `for_each_n()`, `generate_n()` , I `search_n()` algorytmy, które wcześniej nie zostały skompilowane, jeśli długość argumentu nie jest typem całkowitym. Teraz staramy się skonwertować długość niecałkowitą do iteratorów `difference_type` .
- `normal_distribution<float>`nie emituje już ostrzeżeń wewnątrz standardowej biblioteki o zawężaniu wartości z podwójnej do zmiennoprzecinkowej.
- Naprawiono niektóre `basic_string` operacje, które były używane `npos` zamiast `max_size()` sprawdzania maksymalnego rozmiaru przepełnienia.
- `condition_variable::wait_for(lock, relative_time, predicate)`czeka na cały relatywny czas, jeśli wystąpił fałszywe Wake. Teraz czeka tylko na pojedynczy interwał czasu względnego.
- `future::get()`teraz unieważnia `future` , zgodnie z wymaganiami standardowymi.
- `iterator_traits<void *>`używany jako twardy błąd, ponieważ próbuje go utworzyć `void&` ; teraz czyści to pustą strukturę, aby zezwolić na użycie `iterator_traits` w "ITERATOR" SFINAE warunków.
- Niektóre ostrzeżenia zgłoszone przez Clang **-wSystem-Headers** zostały naprawione.
- Ustalono również "Specyfikacja wyjątku w deklaracji jest niezgodna z poprzednią deklaracją" zgłoszoną przez Clang **-wMicrosoft-Exception-spec**.
- Również stałe pamięci podręcznej określania kolejności list raportowane przez Clang i C1XX.
- Kontenery nieuporządkowane nie zamieniają swoich funkcji skrótu ani predykatów, gdy same kontenery zostały zamienione. Teraz.
- Wiele operacji wymiany kontenera jest teraz oznaczonych **`noexcept`** (w przypadku, gdy biblioteka standardowa nigdy nie zamierza zgłosić wyjątku podczas wykrywania `propagate_on_container_swap` niezdefiniowanego warunku zachowania nierównego alokatora).
- Wiele `vector<bool>` operacji jest teraz oznaczonych **`noexcept`** .
- Biblioteka standardowa będzie teraz wymuszać pasujący Alokator `value_type` (w trybie c++ 17) z wystąpieniem ucieczki.
- Naprawiono niektóre warunki, w których funkcja samodzielnego wstawiania `basic_string` może zaszyfrować zawartość ciągów. (Uwaga: zestaw samodzielny — Wstawianie do wektorów jest nadal zabroniony przez standard).
- `basic_string::shrink_to_fit()`nie ma już wpływ na program przydzielający `propagate_on_container_swap` .
- `std::decay`obsługuje teraz typy funkcji Abominable, czyli typy funkcji, które są kwalifikowana za kwalifikatorem, lub w obu przypadkach.
- Zmieniono dyrektywy include, aby użyć poprawnej czułości wielkości liter i ukośników, co poprawia możliwości przenoszenia.
- Stałe ostrzeżenie C4061 "*Enumerator" w*przełączniku wyliczenia*wyliczeniowy "nie*jest jawnie obsługiwane przez etykietę case". To ostrzeżenie jest domyślnie wyłączone i zostało naprawione jako wyjątek od ogólnych zasad biblioteki standardowej dla ostrzeżeń. (Standardowa biblioteka jest **`/W4`** czysta, ale nie próbuje być **`/Wall`** czyste. Wiele ostrzeżeń, które są domyślnie, są niezwykle zakłóceni i nie są przeznaczone do regularnego użycia.
- Udoskonalone `std::list` testy debugowania. Iteratory list sprawdzają teraz `operator->()` , a `list::unique()` teraz oznacza Iteratory jako unieważnione.
- Stałe zastosowania-programowanie w programie w programie `tuple` .

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- `std::partition`teraz wywołuje czas predykatu `N` , a nie `N + 1` razy, zgodnie z wymaganiami standardowymi.
- Program podejmie próbę uniknięcia, że w wersji 15,3 został na15,5 prawiony Magiczna liczba statycznych.
- `std::atomic<T>`nie wymaga już `T` domyślnego konstrukcyjną.
- Algorytmy sterty, które mają czas logarytmiczny, zachowują się inaczej po włączeniu debugowania iteratora. Nie wykonują już jednoliniowej potwierdzenia czasu, że dane wejściowe są w rzeczywistości stertą.
- `__declspec(allocator)`jest teraz chronione tylko dla C1XX, aby zapobiec występowaniu ostrzeżeń z Clang, które nie rozumie tego declspec.
- `basic_string::npos`jest teraz dostępna jako stała czasu kompilacji.
- `std::allocator`w trybie C++ 17 poprawnie obsługuje alokację typów nadmiernie wyrównanych, czyli typów, których wyrównanie jest większe niż `max_align_t` , chyba że jest wyłączone przez **`/Zc:alignedNew-`** .  Na przykład wektory obiektów z wyrównaniam 16-bajtowym lub 32-bajtowym są teraz prawidłowo wyrównane do instrukcji SSE i AVX.

### <a name="conformance-improvements"></a>Ulepszenia zgodności

- Dodaliśmy \<any\> , \<string_view\> , `apply()` , `make_from_tuple()` .
- Dodano \<optional\> , \<variant\> , `shared_ptr::weak_type` , i \<cstdalign\> .
- Włączono C++ 14 **`constexpr`** w `min(initializer_list)` , `max(initializer_list)` , i `minmax(initializer_list)` ,, `min_element()` i `max_element()` `minmax_element()` .

Aby uzyskać więcej informacji, zobacz [tabela zgodność języka Microsoft C++](../visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- Wprowadzono kilka dodatkowych funkcji języka C++ 17. Aby uzyskać więcej informacji, zobacz [tabela zgodność języka Microsoft C++](cpp-conformance-improvements.md#improvements_153).
- Zaimplementowana P0602R0 "Variant i Optional powinna propagować nieuproszczoność kopiowania/przenoszenia".
- Biblioteka standardowa teraz oficjalnie dopuszcza, aby dynamiczne RTTI były wyłączone za pośrednictwem opcji [/gr-](../build/reference/gr-enable-run-time-type-information.md) . Zarówno, jak i niezależnie `dynamic_pointer_cast()` `rethrow_if_nested()` **`dynamic_cast`** , więc Biblioteka standardowa oznacza teraz je jako `=delete` poniżej **`/GR-`** .
- Nawet wtedy, gdy dynamiczny RTTI został wyłączony za pośrednictwem **`/GR-`** , "static RTTI" w formie `typeid(SomeType)` jest nadal dostępny i ma kilka składników biblioteki standardowej. Biblioteka standardowa obsługuje teraz wyłączenie tej funkcji za pośrednictwem programu **`/D_HAS_STATIC_RTTI=0`** . Ta flaga wyłącza również `std::any` `target()` `target_type()` funkcje elementów członkowskich i `std::function` `get_deleter()` zaprzyjaźnioną funkcję członkowską i `std::shared_ptr` `std::weak_ptr` .
- Biblioteka standardowa domyślnie używa języka C++ 14 **`constexpr`** zamiast wstępnie zdefiniowanych makr.
- Biblioteka standardowa używa teraz szablonów aliasów wewnętrznie.
- Biblioteka standardowa używa teraz **`nullptr`** wewnętrznie, zamiast `nullptr_t{}` . (Zostało wyeliminowane wewnętrzne użycie wartości NULL. Wewnętrzne użycie 0-jako-null jest czyszczone stopniowo.)
- Biblioteka standardowa jest teraz używana `std::move()` wewnętrznie zamiast stylistically `std::forward()` .
- Zmieniono `static_assert(false, "message")` na `#error message` . Ta zmiana poprawia diagnostykę kompilatora, ponieważ `#error` natychmiast kończy kompilację.
- Standardowa biblioteka nie oznacza już funkcji jako `__declspec(dllimport)` . Nowoczesne technologie konsolidatora nie wymagają już tego.
- Wyodrębniono SFINAE do domyślnych argumentów szablonu, które zmniejszają bałagan w porównaniu z typami zwracanymi i typami argumentów funkcji.
- Testy debugowania w \<random\> tym teraz używają zwykłych maszyn w bibliotece standardowej zamiast funkcji wewnętrznej `_Rng_abort()` , która jest wywoływana `fputs()` do **stderr**. Implementacja tej funkcji została zatrzymana na potrzeby zgodności binarnej. Usuniemy ją w następnej binarnej niezgodnej wersji biblioteki standardowej.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- Niektóre funkcje biblioteki standardowej zostały dodane, wycofane lub usunięte zgodnie ze standardem C++ 17. Aby uzyskać więcej informacji, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio](cpp-conformance-improvements.md#improvements_155).
- Eksperymentalna obsługa następujących algorytmów równoległych:
  - `all_of`
  - `any_of`
  - `for_each`
  - `for_each_n`
  - `none_of`
  - `reduce`
  - `replace`
  - `replace_if`
  - `sort`
- W tym momencie są dodawane podpisy dla następujących algorytmów równoległych. Profilowanie nie wykazało korzyści w algorytmach przekształcają, które tylko przesuwają lub Permute — elementy:
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

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017, wersja 15.6

- \<memory_resource>
- Podstawowe informacje o bibliotece v1
- Usuwanie `polymorphic_allocator` przypisania
- Ulepszanie odejmowania argumentów szablonu klasy

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Obsługa algorytmów równoległych nie jest już eksperymentalna
- Nowa implementacja programu\<filesystem>
- Konwersje elementarne ciągów (częściowa)
- `std::launder()`
- `std::byte`
- `hypot(x,y,z)`
- Uniknięcie niepotrzebnego uszkodzenia
- Specjalne funkcje matematyczne
- `constexpr char_traits`
- Wskazówki dotyczące odejmowania dla standardowej biblioteki

Aby uzyskać więcej informacji, zobacz [tabela zgodność języka Microsoft C++](../visual-cpp-language-conformance.md).

### <a name="performance-and-throughput-fixes"></a>Poprawki wydajności i przepływności

- Wykonane `basic_string::find(char)` przeciążenia tylko `traits::find` raz. Wcześniej była zaimplementowana jako ogólne wyszukiwanie ciągu dla ciągu o długości 1.
- `basic_string::operator==`teraz sprawdza rozmiar ciągu przed porównaniem zawartości ciągów.
- Usunięto sprzężenie kontrolne w `basic_string` , które było trudne do analizowania przez optymalizator kompilatora. W przypadku wszystkich krótkich ciągów wywoływanie `reserve` nadal ma koszt różny od zera.
- `std::vector`został przekroczony w celu poprawienia i wydajności: aliasowanie podczas operacji INSERT i emplace jest teraz prawidłowo obsługiwane zgodnie z wymogami standardu, silna gwarancja wyjątku jest teraz dostępna w przypadku, gdy jest to wymagane przez standard za pośrednictwem `move_if_noexcept()` i innych logiki, a następnie INSERT i emplace do mniejszej liczby operacji elementu.
- Biblioteka standardowa języka C++ pozwala teraz uniknąć usuwania odwołań do pustych wskaźników.
- Zwiększona `weak_ptr::lock()` wydajność.
- Aby zwiększyć przepływność kompilatora, nagłówki standardowej biblioteki C++ można teraz uniknąć uwzględniania deklaracji niezbędnych funkcji wewnętrznych kompilatora.
- Ulepszona wydajność `std::string` `std::wstring` konstruktorów i przenoszenie ich przez więcej niż trzy razy.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- Praca z usługą **`noexcept`** , która uniemożliwiła `std::atomic` wprowadzanie implementacji do funkcji, które korzystają z obsługi wyjątków strukturalnych (SEH).
- Zmieniono wewnętrzną funkcję biblioteki standardowej `_Deallocate()` , aby zoptymalizować do mniejszego kodu, co pozwala na przekreślenie do większej liczby miejsc.
- Zmieniono `std::try_lock()` , aby użyć rozwinięcia pakietu zamiast rekursji.
- Ulepszono `std::lock()` algorytm unikania zakleszczenia w celu używania `lock()` operacji zamiast obracania na `try_lock()` wszystkie blokady.
- Włączono optymalizację nazwanej wartości zwracanej w `system_category::message()` .
- `conjunction`i `disjunction` teraz można tworzyć wystąpienia `N + 1` typów, a nie `2N + 2` typy.
- `std::function`nie jest już tworzone Tworzenie wystąpienia maszyn obsługi programu przydzielania dla każdego typu, który został wymazany, zwiększona przepływność i zmniejszenie rozmiaru. obj w programach, które przechodzą wiele różnych wyrażeń lambda do `std::function` .
- `allocator_traits<std::allocator>`zawiera ręcznie nieliniowe `std::allocator` operacje, zmniejszając rozmiar kodu w kodzie, który współdziała z `std::allocator` `allocator_traits` , tylko (czyli w większości kodu).
- Interfejs języka C++ 11 o minimalnym przydziałaniu jest teraz obsługiwany przez standardową metodę wywoływania `allocator_traits` bezpośrednio, zamiast zawijania alokatora w klasie wewnętrznej `_Wrap_alloc` . Ta zmiana powoduje zmniejszenie rozmiaru kodu wygenerowanego na potrzeby obsługi alokatora, usprawnia w niektórych przypadkach możliwości Optymalizatora dotyczące kontenerów standardowej biblioteki, a także udostępnia lepsze środowisko debugowania (ponieważ teraz można zobaczyć typ alokatora, a nie `_Wrap_alloc<your_allocator_type>` w debugerze).
- Usunięto Programowanie dla dostosowań `allocator::reference` , które nie mogą być dostosowywane przez przydzielenie. (Przydzielenie mogą sprawić, że kontenery korzystają z ozdobnych wskaźników, ale nie są to odwołania ozdobne).
- Fronton kompilatora był sposobem na odwinięcie iteratorów debugowania w oparciu o pętle, zwiększając wydajność kompilacji debugowania.
- `basic_string`Wewnętrzna ścieżka zmniejszania dla `shrink_to_fit()` i `reserve()` nie jest już ścieżką do ponownej alokacji operacji, co zmniejsza rozmiar kodu dla wszystkich mutacji elementów członkowskich.
- `basic_string`Wewnętrzna ścieżka wzrostu nie znajduje się już w ścieżce `shrink_to_fit()` .
- `basic_string`Operacje zmieniania są teraz uwzględniane w niealokowanej szybkiej ścieżce i przydzielaniu funkcji wolnych ścieżek, co jest bardziej podobne dla wspólnych przypadków bez ponownego przydzielenia.
- `basic_string`Operacje mutacji teraz konstruują ponownie przydzieloną bufory w preferowanym stanie zamiast zmieniać rozmiar w miejscu. Na przykład Wstaw na początku ciągu teraz przenosi zawartość po wstawieniu dokładnie jeden raz. Jest on przenoszony w dół lub do nowo przydzielonych buforów. Nie jest już dwukrotnie przenoszona w przypadku ponownej alokacji, najpierw do nowo przydzielonych buforów, a następnie w dół.
- Operacje wywołujące w pamięci podręcznej standardowej biblioteki języka C w tym \<string\> momencie `errno` umożliwiają usunięcie powtórzonej interakcji z protokołem TLS.
- Uproszczona `is_pointer` implementacja.
- Zakończono zmianę wyrażenia opartego na funkcji SFINAE na **`struct`** i `void_t` -based.
- Algorytmy biblioteki standardowej teraz unikają iteratorów postincrementing.
- Stałe ostrzeżenia obcinania w przypadku korzystania z 32-bitowych przystawek w systemach 64-bitowych.
- `std::vector`przypisanie przenoszenia jest teraz bardziej wydajne w przypadku niePOCMAego przypadku alokatora, gdy jest to możliwe.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- `basic_string<char16_t>`teraz angażuje te same `memcmp` , `memcpy` i podobne optymalizacje, które są `basic_string<wchar_t>` zaangażowane.
- Ograniczenie Optymalizatora, które uniemożliwiło wbudowanie wskaźników funkcji, uwidacznianych przez nasze działania "Unikaj kopiowania funkcji" w programie Visual Studio 2015 Update 3, już pracowało, przywracając wydajność programu `lower_bound(iter, iter, function pointer)` .
- Narzuty weryfikacji kolejności debugowania iteratora danych wejściowych do `includes` , `set_difference` , `set_symmetric_difference` i `set_union` zostało zmniejszone przez odpakowanie iteratorów przed sprawdzeniem kolejności.
- `std::inplace_merge`teraz pomija elementy, które już znajdują się na pozycji.
- Konstruowanie `std::random_device` nie powoduje już konstrukcji, a następnie niszczy `std::string` .
- `std::equal`i `std::partition` miała przebieg optymalizacji obejmujących wielowątkowość, która zapisuje porównanie iteratora.
- Gdy program `std::reverse` przekazuje wskaźniki, aby można je było z nich skopiować `T` , będzie teraz wysyłany do implementacji rozpisanych ręcznie.
- `std::fill`, `std::equal` i `std::lexicographical_compare` były to metody wysyłania do `memset` i `memcmp` dla `std::byte` i `gsl::byte` (oraz innych wyliczeń i typów wyliczeniowych takich jak). Ponieważ `std::copy` są wysyłane przy użyciu `is_trivially_copyable` , nie wymaga żadnych zmian.
- Biblioteka standardowa nie zawiera już pustych nawiasów klamrowych, których jedynym zachowaniem było dokonanie, że typy nie zniszczalnych.

## <a name="other-libraries"></a>Inne biblioteki

### <a name="open-source-library-support"></a>Obsługa biblioteki Open Source

**Vcpkg** to narzędzie wiersza polecenia typu open source, które znacznie upraszcza proces pozyskiwania i tworzenia statycznych libs i bibliotek DLL typu open source w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [vcpkg: A Package Manager for C++](../build/vcpkg.md).

### <a name="cpprest-sdk-290"></a>CPPRest SDK 2.9.0

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

CPPRestSDK, Międzyplatformowy interfejs API sieci Web dla języka C++, został zaktualizowany do wersji 2.9.0. Aby uzyskać więcej informacji, zobacz [CppRestSDK 2.9.0 jest dostępny w witrynie GitHub](https://devblogs.microsoft.com/cppblog/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- Jeszcze inny zestaw poprawek zgodności z wyszukiwaniem nazw
- Istniejące konstruktory przenoszenia i operatory przypisania przenoszenia są teraz prawidłowo oznaczone jako niezgłaszane
- Nie pomijaj prawidłowego ostrzeżenia C4640 o inicjacji bezpiecznego wątku lokalnych elementów statycznych w pliku atlstr. h
- Inicjowanie bezpiecznego wątku lokalnych elementów statycznych zostało automatycznie wyłączone w zestawie narzędzi systemu XP podczas tworzenia biblioteki DLL przy użyciu biblioteki ATL. Teraz nie jest. Możesz dodać **`/Zc:threadSafeInit-`** w ustawieniach projektu, jeśli nie chcesz, aby inicjowanie nie było bezpieczne dla wątków.

### <a name="visual-c-runtime"></a>Środowisko uruchomieniowe Visual C++

- Nowy nagłówek "cfguard. h" dla symboli ochrony przepływu sterowania.

## <a name="visual-studio-2017-c-ide"></a>Środowisko IDE programu Visual Studio 2017 C++

- Wydajność wprowadzania zmian w konfiguracji jest teraz lepsza w przypadku natywnych projektów w języku C++ i o wiele lepsza w projektach C++/CLI. Gdy konfiguracja rozwiązania jest uaktywniana po raz pierwszy, będzie ona teraz szybsza i wszystkie późniejsze aktywacje konfiguracji rozwiązania będą prawie natychmiastowo.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- Ponownie napisano kilka kreatorów projektu i kodów w stylu okna dialogowego podpisu.
- **Dodaj klasę** teraz uruchamia Kreatora dodawania klasy bezpośrednio. Wszystkie inne elementy, które wcześniej znajdowały się w tym miejscu, są teraz dostępne w obszarze **dodaj > nowy element**.
- Projekty Win32 znajdują się teraz w kategorii **pulpitu systemu Windows** w oknie dialogowym **Nowy projekt** .
- Szablony **konsoli systemu Windows** i **aplikacji klasycznych** teraz tworzą projekty bez wyświetlania kreatora. W tej samej kategorii jest dostępny nowy **Kreator pulpitu systemu Windows** , w którym są wyświetlane te same opcje, co w przypadku starego kreatora **aplikacji konsolowej Win32** .

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

Kilka operacji języka C++, które używają aparatu IntelliSense do refaktoryzacji i nawigowania po kodzie przebiega znacznie szybciej. Następujące numery opierają się na rozwiązaniu Visual Studio chrom z projektami 3500:

| Cechy | Poprawa wydajności |
|--|--|
| Zmień nazwę | 5.3 x |
| Zmień sygnaturę | 4,5 x |
| Znajdź wszystkie odwołania | 4,7 x |

Język C++ obsługuje teraz kombinację klawiszy Ctrl + kliknij **Przejdź do definicji**, dzięki czemu można łatwo dołączać do definicji myszą. Wizualizator struktury z pakietu narzędzi do wydajnej wydajności jest teraz również uwzględniony w produkcie.

## <a name="intellisense"></a>IntelliSense

- Nowy aparat bazy danych oparty na SQLite jest teraz używany domyślnie. Nowy aparat przyspiesza operacje bazy danych, takie jak **Przejdź do definicji** i **Znajdź wszystkie odwołania**. Znacznie poprawia początkowy czas analizy rozwiązania. Ustawienie zostało przeniesione do **narzędzi > opcje > Edytor tekstu > C/C++ > zaawansowane**. (Dawniej była w... Język C/C++ > eksperymentalne).

- Ulepszono wydajność IntelliSense w projektach i plikach, które nie używają prekompilowanych nagłówków — automatycznie prekompilowany nagłówek zostanie utworzony dla nagłówków w bieżącym pliku.

- Do listy błędów dodaliśmy filtrowanie błędów i pomoc dotyczącą błędów funkcji IntelliSense. Kliknięcie kolumny błędów umożliwia teraz filtrowanie. Ponadto kliknięcie konkretnego błędu lub naciśnięcie klawisza F1 uruchamia wyszukiwanie online dotyczące danego komunikatu o błędzie.

  ![Lista błędów](media/ErrorList1.png "Lista błędów")

  ![Filtrowana lista błędów](media/ErrorList2.png "Filtrowana lista błędów")

- Dodano możliwość filtrowania listy elementów członkowskich według rodzaju.

  ![Filtrowanie listy elementów członkowskich](media/mlfiltering.png "Filtrowanie listy elementów członkowskich")

- Dodano nową eksperymentalną funkcję IntelliSense predykcyjną, która zapewnia kontekstowe Filtrowanie elementów wyświetlanych na liście elementów członkowskich. Aby uzyskać więcej informacji, zobacz [C++ IntelliSense — udoskonalenia — Przewidywalność & IntelliSense](https://devblogs.microsoft.com/cppblog/c-intellisense-improvements-predictive-intellisense-filtering/).
- Funkcja **Znajdź wszystkie odwołania** (Shift + F12) teraz ułatwia łatwe poruszanie się, nawet w złożonych bazach kodu. Zapewnia zaawansowane grupowanie, filtrowanie, sortowanie, wyszukiwanie w wynikach i (w przypadku niektórych języków) kolorowanie, dzięki czemu można jasno zrozumieć odwołania. W przypadku języka C++ nowy interfejs użytkownika zawiera informacje o tym, czy odczytujemy lub zapisujesz do zmiennej.
- Funkcja zmiany kropki na strzałkę IntelliSense została przeniesiona z doświadczalnych do zaawansowanych i teraz jest domyślnie włączona. Funkcje edytora **rozszerzają zakresy** i **pierwszeństwo rozwijania** są również przenoszone z eksperymentalnego do zaawansowanego.
- Eksperymentalne funkcje refaktoryzacji **Zmień podpis** i **Wyodrębnij funkcję** są teraz dostępne domyślnie.
- Dodano funkcję eksperymentalnego "szybszego ładowania projektu" dla projektów języka C++. Przy następnym otwarciu projektu w języku C++ będzie on ładować się szybciej, a po tym czasie zostanie *znacznie* szybszy.
- Niektóre z tych funkcji są wspólne dla innych języków, a niektóre z nich są specyficzne dla języka C++. Aby uzyskać więcej informacji o tych nowych funkcjach, zobacz temat [ogłaszanie programu Visual Studio "15" (wersja zapoznawcza 5](https://devblogs.microsoft.com/visualstudio/announcing-visual-studio-15-preview-5/)).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Dodano obsługę dla ClangFormat. Aby uzyskać więcej informacji, zobacz [Obsługa ClangFormat w programie Visual Studio 2017](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/).

## <a name="non-msbuild-projects-with-open-folder"></a>Projekty inne niż MSBuild z otwartym folderem

W programie Visual Studio 2017 wprowadzono funkcję **Otwórz folder** . Umożliwia to kod, kompilację i debugowanie w folderze zawierającym kod źródłowy bez konieczności tworzenia jakichkolwiek rozwiązań i projektów. Teraz znacznie prostsze jest rozpoczęcie pracy z programem Visual Studio, nawet jeśli projekt nie jest projektem opartym na programie MSBuild. Funkcja **Otwórz folder** zapewnia dostęp do zaawansowanych funkcji interpretacji kodu, edytowania, kompilowania i debugowania. Są one takie same, jak program Visual Studio udostępnia już projekty MSBuild. Aby uzyskać więcej informacji, zobacz [Otwieranie projektów folderu dla języka C++](../build/open-folder-projects-cpp.md).

- Ulepszenia obsługi polecenia Otwórz folder. Środowisko można dostosować za pomocą tych plików JSON:
  - CppProperties.json dostosowuje obsługę funkcji IntelliSense i przeglądania.
  - Tasks.json dostosowuje kroki kompilacji.
  - Launch.json dostosowuje obsługę debugowania.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- Ulepszona obsługa alternatywnych kompilatorów i środowisk kompilacji, takich jak MinGW i Cygwin. Aby uzyskać więcej informacji, zobacz [Używanie MinGW i Cygwin z Visual C++ i otwartym folderem](https://devblogs.microsoft.com/cppblog/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Dodano obsługę definiowania zmiennych środowiskowych globalnych i specyficznych dla konfiguracji w CppProperties.jsna i CMakeSettings.js. Te zmienne środowiskowe mogą być używane przez konfiguracje debugowania zdefiniowane w launch.vs.jsna i zadania w tasks.vs.jsna. Aby uzyskać więcej informacji, zobacz [Dostosowywanie środowiska przy użyciu Visual C++ i otwartych folderów](https://devblogs.microsoft.com/cppblog/customizing-your-environment-with-visual-c-and-open-folder/).
- Ulepszona obsługa generatora Ninja programu CMake, w tym możliwość łatwego kierowania platform 64-bitowych.

## <a name="cmake-support-via-open-folder"></a>Obsługa CMake za pośrednictwem otwartego folderu

Program Visual Studio 2017 wprowadza obsługę projektów CMake bez konwertowania na pliki projektu MSBuild (. vcxproj). Aby uzyskać więcej informacji, zobacz [CMAKE projects in Visual Studio](../build/cmake-projects-in-visual-studio.md). Otwieranie projektów CMake z **otwartym folderem** automatycznie konfiguruje środowisko do edytowania, kompilowania i debugowania języka C++.

- Funkcja IntelliSense języka C++ działa bez konieczności tworzenia CppProperties.jsw pliku w folderze głównym. Dodano również nową listę rozwijaną, aby umożliwić użytkownikom łatwe przełączanie się między konfiguracjami dostarczonymi przez CMake i CppProperties.jsna plikach.

- Dalsza konfiguracja jest obsługiwana przy użyciu pliku CMakeSettings.json, który znajduje się w tym samym folderze co plik CMakeLists.txt.

  ![CMake Otwórz folder](media/cmake-cpp.png "CMake Otwórz folder")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- Dodano obsługę generatora Ninja CMake.

##### <a name="visual-studio-2017-version-154"></a>Visual Studio 2017, wersja 15.4

- Dodano obsługę importowania istniejących pamięci podręcznych CMake.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- Dodano wsparcie dla CMake 3,11, analiza kodu w projektach CMake, widok obiektów docelowych w Eksplorator rozwiązań, opcje generacji pamięci podręcznej i kompilowanie pojedynczego pliku. Aby uzyskać więcej informacji, zobacz [CMAKE Support in Visual Studio](https://devblogs.microsoft.com/cppblog/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) and [CMAKE projects in Visual Studio](../build/cmake-projects-in-visual-studio.md).

## <a name="windows-desktop-development"></a>Tworzenie aplikacji klasycznych systemu Windows

Zapewniamy obecnie bardziej zaawansowane środowisko instalacji oryginalnego obciążenia C++. Dodaliśmy możliwe do wybrania składniki pozwalające na zainstalowanie tylko tych narzędzi, których potrzebujesz. Wskazane rozmiary instalacji składników wymienionych w interfejsie użytkownika Instalatora są nieprawidłowe i nieszacunkowo łączny rozmiar.

Aby pomyślnie tworzyć projekty Win32 w obciążeniu C++ dla komputerów stacjonarnych, musisz zainstalować zarówno zestaw narzędzi, jak i zestaw SDK systemu Windows. Zainstaluj zalecane (wybrane) składniki programu **VC + + 2017 najnowsze 141 zestaw narzędzi (x86, x64)** i **Windows 10 SDK (10.0. nnnnn)** , aby upewnić się, że działa. Jeśli niezbędne narzędzia nie są zainstalowane, projekty nie zostaną utworzone pomyślnie, a Kreator przestanie odpowiadać.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

Narzędzia kompilacji Visual C++ (wcześniej dostępne jako produkt autonomiczny) są teraz uwzględniane jako obciążenie w Instalator programu Visual Studio. To obciążenie powoduje zainstalowanie tylko narzędzi wymaganych do kompilowania projektów C++ bez instalowania środowiska IDE programu Visual Studio. Dostępne są zarówno zestawy narzędzi wersji 140, jak i najnowsze 141. Zestaw narzędzi najnowsze 141 zawiera najnowsze ulepszenia programu Visual Studio 2017 w wersji 15,5. Aby uzyskać więcej informacji, zobacz [Visual Studio Build Tools teraz obejmują zestawy narzędzi program VS2017 i programu VS2015 MSVC](https://devblogs.microsoft.com/cppblog/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Programowanie dla systemu Linux w języku C++

Popularne rozszerzenie [Visual C++ for Linux Development](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.VisualCforLinuxDevelopment) stanowi obecnie cześć programu Visual Studio. Ta instalacja zawiera wszystko, czego potrzebujesz do tworzenia i debugowania aplikacji w języku C++ działających w środowisku systemu Linux.

##### <a name="visual-studio-2017-version-152"></a>Program Visual Studio 2017 w wersji 15.2

Wprowadzono ulepszenia w zakresie udostępniania kodu dla wielu platform i wizualizacji typów. Aby uzyskać więcej informacji, zobacz temat [udoskonalenia systemu Linux C++ na potrzeby udostępniania kodu międzyplatformowego i wizualizacji typu](https://devblogs.microsoft.com/cppblog/linux-cross-platform-and-type-visualization/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- W obciążeniu systemu Linux dodano obsługę **rsync** jako alternatywę dla protokołu **SFTP** do synchronizowania plików na zdalnych maszynach z systemem Linux.
- Dodano obsługę dla mikrokontrolerów ARM dla kompilacji krzyżowej. Aby włączyć ją w instalacji, wybierz pozycję Programowanie dla systemu **Linux przy użyciu języka C++** i wybierz opcję **tworzenia aplikacji osadzonych i IoT**. Ta opcja umożliwia dodanie narzędzi do kompilacji krzyżowej ARM i dokonanie instalacji. Aby uzyskać więcej informacji, zobacz [kompilacja między różnymi platformami w programie Visual Studio](https://devblogs.microsoft.com/cppblog/arm-gcc-cross-compilation-in-visual-studio/).
- Dodano obsługę dla CMake. Teraz można korzystać z istniejącej bazy kodu CMake bez konieczności konwertowania jej na projekt programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu systemu Linux CMAKE](../linux/cmake-linux-project.md).
- Dodano obsługę uruchamiania zadań zdalnych. Ta funkcja umożliwia uruchamianie dowolnego polecenia w systemie zdalnym, który jest zdefiniowany w Menedżerze połączeń programu Visual Studio. Zadania zdalne zapewniają również możliwość kopiowania plików do systemu zdalnego.
Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu systemu Linux CMAKE](../linux/cmake-linux-project.md).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Różne ulepszenia scenariuszy obciążeń systemu Linux. Aby uzyskać więcej informacji, zobacz [udoskonalenia obciążeń środowiska Linux C++ w systemie projektu, oknie konsoli systemu Linux, rsync i dołączanie do procesu](https://devblogs.microsoft.com/cppblog/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).
- Funkcja IntelliSense dla nagłówków w zdalnych połączeniach systemu Linux. Aby uzyskać więcej informacji, zobacz [IntelliSense dla zdalnych nagłówków systemu Linux](https://devblogs.microsoft.com/cppblog/intellisense-for-remote-linux-headers/) i [Konfigurowanie projektu systemu Linux CMAKE](../linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Programowanie gier w języku C++

Pełnych możliwości języka C++ można użyć do tworzenia profesjonalnych gier obsługiwanych przy użyciu zestawu funkcji DirectX lub Cocos2d.

## <a name="mobile-development-with-c-for-android-and-ios"></a>Programowanie aplikacji mobilnych za pomocą języka C++ dla systemów Android i iOS

Program Visual Studio umożliwia obecnie programowanie i debugowanie aplikacji mobilnych przeznaczonych dla systemów Android oraz iOS.

## <a name="universal-windows-apps"></a>Aplikacje uniwersalne systemu Windows

Język C++ stanowi składnik opcjonalny obciążenia Aplikacja uniwersalna systemu Windows. Obecnie należy ręcznie uaktualnić projekty w języku C++. Możesz otworzyć projekt platforma uniwersalna systemu Windows przeznaczony dla wersji 140 w programie Visual Studio 2017. Należy jednak wybrać zestaw narzędzi platformy najnowsze 141 na stronach właściwości projektu, jeśli nie masz zainstalowanego programu Visual Studio 2015.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nowe opcje dla języka C++ w platforma uniwersalna systemu Windows (platformy UWP)

Dostępne są teraz nowe opcje pisania i pakowania aplikacji C++ dla platforma uniwersalna systemu Windows i sklepu Windows: infrastruktura mostka dla komputerów stacjonarnych umożliwia spakowanie istniejącej aplikacji klasycznej lub obiektu COM do wdrożenia za pomocą Sklepu Windows. Lub, w przypadku wdrażania za pośrednictwem istniejących kanałów za pośrednictwem ładowania bezpośredniego. Nowe funkcje w systemie Windows 10 umożliwiają dodawanie funkcji platformy UWP do aplikacji klasycznych na różne sposoby. Aby uzyskać więcej informacji, zobacz [mostek Desktop](/windows/uwp/porting/desktop-to-uwp-root).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

Zostanie dodany szablon projektu **pakietu aplikacji systemu Windows** , który znacznie upraszcza pakowanie aplikacji klasycznych za pomocą mostka programu Desktop. Jest on dostępny w **pliku | Nowy | Projekt | Zainstalowane | Visual C++ | Platforma uniwersalna systemu Windows**. Aby uzyskać więcej informacji, zobacz [pakowanie aplikacji za pomocą programu Visual Studio (mostek Desktop)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Podczas pisania nowego kodu można teraz używać języka C++/WinRT, czyli standardowego rzutu języka C++ dla środowisko wykonawcze systemu Windows zaimplementowane wyłącznie w plikach nagłówkowych. Umożliwia korzystanie z interfejsów API środowisko wykonawcze systemu Windows i tworzenie ich przy użyciu dowolnych zgodnych ze standardami kompilatora języka C++. Język c++/WinRT został zaprojektowany, aby zapewnić deweloperom języka C++ dostęp do nowoczesnego interfejsu API systemu Windows przy użyciu pierwszej klasy. Aby uzyskać więcej informacji, zobacz [c++/WinRT: nowoczesny c++ dla środowisko wykonawcze systemu Windows](https://moderncpp.com/).

Począwszy od kompilacji 17025 Windows SDK w wersji zapoznawczej, w Windows SDK znajduje się/WinRT C++. Aby uzyskać więcej informacji, zobacz [C++/WinRT jest teraz dołączany do Windows SDK](https://devblogs.microsoft.com/cppblog/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="the-clangc2-platform-toolset"></a>Zestaw narzędzi platformy Clang/C2

Zestaw narzędzi Clang/C2 dostarczany z programem Visual Studio 2017 obsługuje teraz **`/bigobj`** przełącznik, który jest kluczowy dla kompilowania dużych projektów. Zawiera również kilka ważnych poprawek, zarówno w frontonie, jak i zapleczu kompilatora.

## <a name="c-code-analysis"></a>Analiza kodu w języku C++

Podstawowe narzędzia do sprawdzania kodu C++ wymuszające stosowanie [podstawowych wytycznych dotyczących języka C++](https://github.com/isocpp/CppCoreGuidelines) są obecnie dystrybuowane z programem Visual Studio. Włącz kontrolki na stronie **rozszerzenia analizy kodu** na stronach właściwości projektu. Rozszerzenia są następnie dołączane podczas uruchamiania analizy kodu. Aby uzyskać więcej informacji, zobacz [using the podstawowe wytyczne dotyczące języka C++ checks](/cpp/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Strona właściwości CppCoreCheck")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- Dodano obsługę reguł związanych z zarządzaniem zasobami.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- Nowe podstawowe wytyczne dotyczące języka C++ sprawdzają poprawność wskaźnika inteligentnego, prawidłowe użycie inicjatorów globalnych i Oflagowanie użycia konstrukcji, takich jak **`goto`** i złe rzutowanie.

- Niektóre numery ostrzeżeń, które można znaleźć w wersji 15.3, nie są już dostępne w wersji 15.5. Ostrzeżenia te zostały zastąpione bardziej szczegółowymi operacjami sprawdzania.

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017, wersja 15.6

- Dodano obsługę analizy pojedynczych plików i ulepszenia wydajności w czasie wykonywania analizy. Aby uzyskać więcej informacji, zobacz [udoskonalenia analizy statycznej języka C++ dla programu Visual Studio 2017 15,6 (wersja zapoznawcza 2](https://devblogs.microsoft.com/cppblog/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/) )

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Dodano obsługę [`/analyze:ruleset`](../build/reference/analyze-code-analysis.md) , która umożliwia określenie reguł analizy kodu do uruchomienia.
- Dodano obsługę dodatkowych reguł podstawowe wytyczne dotyczące języka C++.  Aby uzyskać więcej informacji, zobacz [using the podstawowe wytyczne dotyczące języka C++ checks](/cpp/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing-in-visual-studio-2017"></a>Testy jednostkowe w programie Visual Studio 2017

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

Google Test Adapter i zwiększanie wydajności. Adapter testowy jest teraz dostępny jako składniki **programowania aplikacji klasycznych w języku C++** . Są one zintegrowane z **Eksploratorem testów**. Obsługa narzędzia ctest jest dodawana do projektów CMake (przy użyciu otwartego folderu), ale pełna integracja z **Eksploratorem testów** nie jest jeszcze dostępna. Aby uzyskać więcej informacji, zobacz [pisanie testów jednostkowych dla C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp).

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017, wersja 15.6

- Dodano obsługę dla `Boost.Test` obsługi biblioteki dynamicznej.
- `Boost.Test`Szablon elementu jest teraz dostępny w środowisku IDE.

Aby uzyskać więcej informacji, zobacz [ `Boost.Test` testowanie jednostek: obsługa biblioteki dynamicznej i szablon nowego elementu](https://devblogs.microsoft.com/cppblog/boost-test-unit-testing-dynamic-library-support-and-new-item-template/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

Dodano obsługę [CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) dla projektów testów jednostkowych w języku C++. Aby uzyskać więcej informacji, zobacz temat [ogłaszanie CodeLens dla testów jednostkowych w języku C++](https://devblogs.microsoft.com/cppblog/announcing-codelens-for-c-unit-testing/).

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostyka grafiki programu Visual Studio

Narzędzia Diagnostyka grafiki programu Visual Studio: można ich używać do rejestrowania i analizowania problemów z renderowaniem i wydajnością w aplikacjach Direct3D. Należy używać ich w aplikacjach, które są uruchamiane lokalnie na komputerze z systemem Windows, w emulatorze urządzenia z systemem Windows lub na komputerze zdalnym lub urządzeniu.

- Dane **wejściowe & danych wyjściowych dla programów do cieniowania wierzchołków i geometrii:** Możliwość wyświetlania danych wejściowych i wyjściowych programów do cieniowania wierzchołków i cieniowania geometrycznego była jedną z najbardziej żądanych funkcji. Jest ona teraz obsługiwana w narzędziach. Wybierz etap programu VS lub GS w widoku etapy potoku, aby rozpocząć inspekcję danych wejściowych i wyjściowych w poniższej tabeli.

  ![Dane wejściowe/wyjściowe dla programów do cieniowania](media/io-shaders.png)

- **Wyszukiwanie i filtrowanie w tabeli obiektów:** Zapewnia szybki i łatwy sposób znajdowania szukanych zasobów.

  ![Wyszukaj](media/search.png)

- **Historia zasobów:** Ten nowy widok zapewnia ulepszony sposób wyświetlania całej historii modyfikacji zasobu, ponieważ był używany podczas renderowania przechwyconej ramki. Aby wywoływać historię dla dowolnego zasobu, kliknij ikonę zegara obok dowolnego hiperłącza zasobu.

  ![Historia zasobów](media/resource-history.png)

  Zostanie wyświetlone nowe okno narzędzia **historia zasobów** wypełnione historią zmian zasobu.

  ![Zmiana historii zasobów](media/resource-history-change.png)

  Można przechwytywać ramki z włączonym pełnym przechwytywaniem stosu wywołań. Pozwala to szybko ustalić kontekst każdego zdarzenia zmiany i sprawdzić je w projekcie programu Visual Studio. Ustaw opcję Przechwyć pełną stos w oknie dialogowym **opcje > narzędzia** Visual Studio w obszarze **Diagnostyka grafiki**.

- **Statystyka interfejsu API:** Wyświetl podsumowanie wysokiego poziomu użycia interfejsu API w ramce. Jest to przydatne w przypadku odnajdywania wywołań, które mogą nie być w ogóle wykonywane, lub wywoływać zbyt często. To okno jest dostępne za pośrednictwem **widoku > statystyk interfejsu API** w programie Analizator grafiki programu Visual Studio.

  ![Statystyka interfejsu API](media/api-stats.png)

- **Statystyka pamięci:** Wyświetl ilość pamięci przydzielonej przez sterownik dla zasobów tworzonych w ramce. To okno jest dostępne za pośrednictwem **widoku > statystyk pamięci** w **Analizator grafiki programu Visual Studio**. Aby skopiować dane do pliku CSV w celu wyświetlenia w arkuszu kalkulacyjnym, kliknij prawym przyciskiem myszy i wybierz polecenie **Kopiuj wszystko**.

  ![Statystyki pamięci](media/memory-stats.png)

- **Sprawdzanie poprawności ramki:** Nowa lista błędów i ostrzeżeń umożliwia łatwe nawigowanie po liście zdarzeń na podstawie potencjalnych problemów wykrytych przez warstwę debugowania Direct3D. Kliknij pozycję **wyświetl > sprawdzanie poprawności ramki** w Analizator grafiki programu Visual Studio, aby otworzyć okno. Następnie kliknij pozycję **Uruchom weryfikację** , aby rozpocząć analizę. Ukończenie tej operacji może potrwać kilka minut, w zależności od złożoności ramki.

  ![Sprawdzanie poprawności ramki](media/frame-validation.png)

- **Analiza klatek dla D3D12:** Analiza klatek umożliwia analizowanie wydajności wywołań rysowania przy użyciu ukierunkowanych eksperymentów "co w przypadku". Przejdź do karty analiza klatek i Uruchom analizę, aby wyświetlić raport. Aby uzyskać więcej informacji, Obejrzyj [GoingNative 25: film wideo z programu Visual analiza klatek grafiki Studio](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) .

  ![Analiza klatek](media/frame-analysis.png)

- **Ulepszenia użycia procesora GPU:** Otwarte śledzenia można wykonać za pośrednictwem profilera użycia procesora GPU programu Visual Studio z widokiem procesora GPU lub narzędziem Windows Performance Analyzer (WPA) w celu uzyskania bardziej szczegółowej analizy. Jeśli masz zainstalowany zestaw narzędzi wydajności systemu Windows, istnieją dwa hiperlinki: jeden dla WPA i inny dla widoku GPU, w prawym dolnym rogu omówienia sesji.

  ![Użycie procesora GPU](media/gpu-usage.png)

  Ślady otwierane w widoku GPU za pośrednictwem tego linku obsługują zsynchronizowane i graficzne wyświetlanie osi czasu oraz powiększanie i panoramowanie. Pole wyboru w programie VS kontroluje, czy synchronizacja jest włączona, czy nie.

  ![Widok procesora GPU](media/gpu-view.png)

::: moniker-end

::: moniker range="=vs-2015"

Aby zapoznać się z pełną listą nowości w programie Visual Studio 2015 Update 3, zobacz [Visual C++ co nowego 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

Aby uzyskać więcej informacji na temat nowości we wszystkich wersjach programu Visual Studio 2015, zobacz informacje o wersji. Są one połączone z [historią informacji o wersji programu Visual Studio 2015](/visualstudio/releasenotes/vs2015-version-history).

Aby uzyskać informacje na temat Nowości w języku C++ w programie Visual Studio 2019, zobacz [co nowego w języku c++ w programie Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019).

Aby uzyskać informacje na temat Nowości w języku C++ w programie Visual Studio 2017, zobacz [co nowego w języku c++ w programie Visual studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017).

::: moniker-end
