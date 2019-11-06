---
title: Co nowego w języku C++ w programie Visual Studio
ms.date: 07/02/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 4b9f393f133fea41e1fbffa88abe225f9b05a9ec
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626489"
---
# <a name="whats-new-for-c-in-visual-studio"></a>Co nowego w języku C++ w programie Visual Studio

::: moniker range=">=vs-2019"

Program Visual Studio 2019 oferuje wiele aktualizacji i poprawek do środowiska C++ firmy Microsoft. Rozwiązano wiele usterek i problemów w kompilatorze i narzędziach. Wiele z tych problemów zostało przesłanych przez klientów w wyniku [zgłoszenia problemu](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019) i [udostępnienia opcji sugestii](https://developercommunity.visualstudio.com/spaces/62/index.html) w obszarze **Wyślij opinię**. Dziękujemy za zgłaszanie usterek! Aby uzyskać więcej informacji na temat nowości we wszystkich wersjach programu Visual Studio, zobacz [co nowego w programie Visual studio 2019](/visualstudio/ide/whats-new-visual-studio-2019). Aby uzyskać informacje na temat Nowości C++ w programie visual Studio 2017, zobacz [co nowego C++ w programie Visual Studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017). Aby uzyskać informacje na temat Nowości C++ w programie visual Studio 2015 i starszych wersjach, zobacz Wizualizacja nowości w programie [visual C++ 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>kompilator C++

- Ulepszona obsługa funkcji i poprawek w języku C++ 17 oraz Eksperymentalna obsługa funkcji języka C++ 20, takich jak moduły i współprocedury. Aby uzyskać szczegółowe informacje, zobacz [ C++ ulepszenia zgodności w programie Visual Studio 2019](cpp-conformance-improvements.md).

- Opcja `/std:c++latest` obejmuje teraz funkcje języka C++ 20, które nie są gotowe, w tym wstępne wsparcie dla operatora C++ 20 \<= > ("Spaceship") na potrzeby porównania trzykrotnie.

- Przełącznik C++ kompilatora `/Gm` jest obecnie przestarzały. Rozważ wyłączenie przełącznika `/Gm` w skryptach kompilacji, jeśli jest on jawnie zdefiniowany. Można również bezpiecznie zignorować ostrzeżenia o zaniechaniu `/Gm`, ponieważ nie jest on traktowany jako błąd podczas korzystania z "Traktuj ostrzeżenia jako błędy" (`/WX`).

- Ponieważ MSVC rozpoczyna Implementowanie funkcji ze standardowego projektu C++ 20 pod flagą `/std:c++latest`, `/std:c++latest` jest teraz niezgodne z `/clr` (wszystkie wersje), `/ZW`i `/Gm`. W programie Visual Studio 2019 Użyj trybów `/std:c++17` lub `/std:c++14` podczas kompilowania z `/clr`, `/ZW`lub `/Gm` (zobacz poprzedni punktor).

- Prekompilowane nagłówki nie są już generowane domyślnie dla konsoli C++ i aplikacji klasycznych.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, zabezpieczenia, Diagnostyka i przechowywanie wersji

Ulepszona analiza z `/Qspectre` w celu zapewnienia pomocy dotyczącej ograniczenia dla Spectre wariantu 1 (CVE-2017-5753). Aby uzyskać więcej informacji, zobacz [Spectree ograniczenia w MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>C++ulepszenia biblioteki standardowej

- Implementacja dodatkowych funkcji i poprawek biblioteki C++ 17 i C++ 20. Aby uzyskać szczegółowe informacje, zobacz [ C++ ulepszenia zgodności w programie Visual Studio 2019](cpp-conformance-improvements.md).

- Clang-format został zastosowany do nagłówków C++ biblioteki standardowej w celu zwiększenia czytelności.

- Ponieważ program Visual Studio obsługuje teraz Tylko mój kod C++for, standardowa biblioteka nie musi już udostępniać niestandardowych maszyn dla `std::function` i `std::visit`, aby osiągnąć ten sam efekt. Usuwanie maszyn w dużej mierze nie ma żadnych efektów widocznych dla użytkownika. Jedynym wyjątkiem jest to, że kompilator nie będzie już generować diagnostyki wskazującej problemy w wierszu 15732480 lub 16707566 \<type_traits > lub \<wariantów >.

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>Ulepszenia wydajności/przepływności w bibliotece kompilator i Standardowa

- Ulepszenia przepływności kompilacji, w tym sposób, w jaki konsolidator obsługuje operacje we/wy na plikach, oraz czas połączenia w przypadku scalania i tworzenia typu PDB.

- Dodano obsługę podstawową dla systemu OpenMP SIMD wektoryzacji. Można ją włączyć przy użyciu nowego przełącznika kompilatora `-openmp:experimental`. Ta opcja umożliwia pętlę z `#pragma omp simd`, aby mogła być wektorowa. Wektoryzacji nie jest gwarantowany, natomiast pętle, które nie są wektorowe, zostaną wyświetlone ostrzeżenie. Nie są obsługiwane żadne klauzule SIMD; są one ignorowane i raportowane jest ostrzeżenie.

- Dodano nowy, niepodkreślający przełącznik wiersza polecenia `-Ob3`, który jest bardziej agresywną wersją `-Ob2`. `-O2` (Optymalizacja plików binarnych dla szybkości) nadal oznacza `-Ob2` domyślnie. Jeśli okaże się, że kompilator nie działa w sposób agresywny, rozważ przekazanie `-O2 -Ob3`.

- Aby zapewnić obsługę wektoryzacji pętli z wywołaniami funkcji biblioteki matematycznej i niektórych innych operacji, takich jak dzielenie liczby całkowitej, dodaliśmy obsługę krótkich funkcji wektorowych biblioteki matematycznej (SVML). Te funkcje obliczają odpowiedniki wektorów 128-bitowe, 256-bitowe lub 512-bitowego. Aby uzyskać definicje obsługiwanych funkcji, zobacz [Intel Intrinsic Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML) (Przewodnik wewnętrzny firmy Intel).

- Nowe i ulepszone optymalizacje:

  - Uproszczone i arytmetyczne uproszczenia dla wyrażeń wykorzystujących wewnętrzne SIMD wektorowe, zarówno dla formularzy zmiennoprzecinkowych, jak i liczb całkowitych.

  - Bardziej wydajna analiza dla wyodrębniania informacji z przepływu sterowania (instrukcji if/else/Switch) w celu usunięcia gałęzi zawsze sprawdzanych pod kątem wartości true lub false.

  - Ulepszono funkcji memset odwrócenia, aby użyć instrukcji SSE2 Vector.

  - Ulepszone usuwanie bezużytecznych kopii struktury/klas, szczególnie C++ w przypadku programów, które przechodzą przez wartość.

  - Ulepszona Optymalizacja kodu przy użyciu `memmove`, takich jak `std::copy` lub `std::vector` i `std::string` konstrukcja.

- Zoptymalizowano fizyczny projekt biblioteki standardowej, aby uniknąć niebezpośredniego kompilowania części biblioteki standardowej. Ta zmiana obcina czas kompilacji pustego pliku, który zawiera tylko \<> wektora. W związku z tym może być konieczne dodanie `#include` dyrektyw dla nagłówków, które wcześniej zostały uwzględnione. Na przykład kod, który używa `std::out_of_range` może teraz dodawać `#include <stdexcept>`. Kod korzystający z operatora wstawiania strumienia może teraz potrzebować dodać `#include <ostream>`. Korzyść polega na tym, że tylko jednostki tłumaczenia faktycznie używające \<stdexcept > lub \<e składniki > będą obciążane kosztem przepływności w celu ich skompilowania.

- `if constexpr` został zastosowany w większej liczbie miejsc w standardowej bibliotece w celu zwiększenia przepływności i zmniejszenia rozmiaru kodu w operacjach kopiowania w permutacjach, takich jak odwracanie i obracanie, oraz w bibliotece algorytmów równoległych.

- Biblioteka standardowa teraz używa `if constexpr`, aby skrócić czas kompilowania, nawet w trybie C++ 14.

- Wykrywanie dynamicznego łączenia środowiska uruchomieniowego dla biblioteki algorytmów równoległych nie używa już całej strony do przechowywania tablicy wskaźników funkcji. Oznaczenie tej pamięci jako tylko do odczytu nie jest już ważne ze względów bezpieczeństwa.

- Konstruktor `std::thread`nie czeka już na uruchomienie wątku i nie wstawia już tak wielu warstw wywołań funkcji między podstawową biblioteką C `_beginthreadex` i dostarczonego obiektu, który można wywołać. Wcześniej `std::thread` umieścić 6 funkcji między `_beginthreadex` i podanym możliwym do nadania obiektu, który został zredukowany do tylko 3 (2, które są po prostu `std::invoke`). Ta zmiana powoduje również rozwiązanie usterki powodującej zaciemnienie czasu, w której Konstruktor `std::thread` zawiesza się po zmianie zegara systemowego w chwili, gdy `std::thread` był tworzony.

- Naprawiono regresję wydajności w `std::hash`, która została wprowadzona podczas implementowania `std::hash<std::filesystem::path>`.

- Biblioteka standardowa używa teraz destruktorów zamiast bloków catch w kilku miejscach, aby osiągnąć poprawność. Ta zmiana skutkuje lepszym interakcją debugera: wyjątki zgłaszane przez bibliotekę standardową w lokalizacjach, których dotyczy ta operacja, są teraz wyświetlane jako zgłoszone przez ich pierwotną witrynę throw, a nie z naszych ponownych alertów. Nie wszystkie bloki catch biblioteki standardowej zostały wyeliminowane; Oczekujemy, że liczba bloków catch zostanie zmniejszona w nowszych wersjach MSVC.

- Nieoptymalny codegen w `std::bitset` spowodowany rzutem warunkowym w ramach funkcji noexcept został rozwiązany przez wygenerowanie wyrzucanej ścieżki.

- Rodzina `std::list` i `std::unordered_*` używają iteratorów niezwiązanych z debugowaniem wewnętrznie w większej liczbie miejsc.

- Kilka elementów członkowskich `std::list` zostało zmienionych w celu ponownego użycia węzłów listy, jeśli jest to możliwe, a nie cofnięcia przydziału i ich ponowne przypisanie. Na przykład, mając `list<int>` o rozmiarze 3, wywołanie do `assign(4, 1729)` teraz zastępuje liczby całkowite w pierwszych 3 węzłach listy i przydziela jeden nowy węzeł listy z wartością 1729.

- Wszystkie wywołania biblioteki standardowej do `erase(begin(), end())` zostały zmienione na `clear()`.

- `std::vector` teraz inicjuje i wymazuje elementy bardziej wydajnie w niektórych przypadkach.

- Udoskonalenia `std::variant` w celu zapewnienia bardziej przyjaznego Optymalizatora, co prowadzi do lepszego wygenerowanego kodu. Tworzenie kodu w kodzie jest teraz znacznie lepsze dzięki `std::visit`.

## <a name="c-ide"></a>Środowisko IDE języka C++

### <a name="live-share-c-support"></a>Obsługa C++ Live Share

[Live Share](/visualstudio/liveshare/) teraz obsługuje C++, umożliwiając deweloperom korzystanie z programu Visual Studio lub Visual Studio Code do współpracy w czasie rzeczywistym. Aby uzyskać więcej informacji, zobacz temat [ogłaszanie C++Live Share: udostępnianie w czasie rzeczywistym i współpraca](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>Rozszerzenia intellicode dlaC++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16,1

Rozszerzenia intellicode jest opcjonalnym rozszerzeniem, które korzysta z własnego rozbudowanego szkolenia i kontekstu kodu, aby określić, co najprawdopodobniej będzie używane w górnej części listy uzupełniania. Często może wyeliminować konieczność przewijania w dół listy. W C++programie rozszerzenia intellicode oferuje największą pomoc w przypadku korzystania z popularnych bibliotek, takich jak standardowa biblioteka. Jest ona dostępna jako składnik obciążenia w instalatorze. Aby uzyskać więcej informacji, zobacz [sugestie dotyczące uzupełniania C++ kodu z obsługą AI są dostępne za pośrednictwem rozszerzenia intellicode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

### <a name="template-intellisense"></a>IntelliSense szablonu

**Pasek szablonu** korzysta teraz z interfejsu użytkownika **okna wglądu** , a nie okna modalnego, obsługuje zagnieżdżone szablony i wstępnie wypełnia wszystkie argumenty domyślne w **oknie wgląd**. Aby uzyskać więcej informacji, zobacz artykuł [ulepszenia funkcji IntelliSense dla programu Visual Studio 2019 (wersja zapoznawcza 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/)). **Ostatnio używana** lista rozwijana na **pasku szablonu** pozwala szybko przełączać się między poprzednimi zestawami przykładowych argumentów.

### <a name="new-start-window-experience"></a>Nowe środowisko okna uruchamiania

Podczas uruchamiania środowiska IDE pojawia się nowe okno uruchamiania z opcjami otwierania ostatnich projektów, klonowania kodu z kontroli źródła, otwierania kodu lokalnego jako rozwiązania lub folderu lub tworzenia nowego projektu. Okno dialogowe Nowy projekt zostało również przedzielone na wyszukanie, a następnie przeprowadzono filtrowanie.

### <a name="new-names-for-some-project-templates"></a>Nowe nazwy dla niektórych szablonów projektu

Zmodyfikowano kilka nazw i opisów szablonu projektu, aby dopasować je do zaktualizowanego okna dialogowego nowego projektu.

### <a name="various-productivity-improvements"></a>Różne ulepszenia produktywności

Program Visual Studio 2019 zawiera następujące funkcje, które ułatwiają tworzenie i bardziej intuicyjne kodowanie:

- Szybkie poprawki dla:
  - Dodaj brakujące #include
  - Wartość zerowa do nullptr
  - Dodaj brakujący średnik
  - Rozwiązywanie brakującej przestrzeni nazw lub zakresu
  - Zastąp złe operandy pośrednie (\* do & i & do \*)
- Szybkie informacje dla bloku przez umieszczenie kursora w zamykającym nawiasie klamrowym
- Wgląd w plik nagłówka/kodu
- Przejdź do definicji na #include otwiera plik

Aby uzyskać więcej informacji, zobacz [ C++ ulepszenia produktywności w programie Visual Studio 2019 (wersja zapoznawcza 2](https://devblogs.microsoft.com/cppblog/c-productivity-improvements-in-visual-studio-2019-preview-2/)).

### <a name="quickinfo-improvements"></a>Udoskonalenia sekcji szybkich informacji

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16,1

Etykietka Szybka podpowiedź teraz uwzględnia kolorowanie semantyczne edytora. Dostępne jest również nowe łącze **wyszukiwania online** , które umożliwia wyszukanie dokumentacji online w celu uzyskania dodatkowych informacji na temat aktywowanej konstrukcji kodu. W przypadku kodu z czerwonym obramowaniem link zapewniany przez szybkie informacje szuka błędu w trybie online. W ten sposób nie trzeba ponownie wpisywać komunikatu do przeglądarki. Aby uzyskać więcej informacji, zobacz [ulepszenia szybkiej informacji w programie Visual Studio 2019: kolorowanie i przeszukiwanie w trybie online](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/).

### <a name="intellicode-available-in-c-workload"></a>Rozszerzenia intellicode dostępne w C++ obciążeniu

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16,1

Rozszerzenia intellicode teraz dostarcza jako składnik opcjonalny do **tworzenia aplikacji klasycznych z C++**  obciążeniem. Aby uzyskać więcej informacji, [Zobacz C++ udoskonalony rozszerzenia intellicode teraz dostarczany z programem Visual Studio 2019](https://devblogs.microsoft.com/cppblog/improved-c-intellicode-now-ships-with-visual-studio-2019/).

## <a name="cmake-support"></a>Obsługa CMake

- Obsługa CMake 3,14

- Program Visual Studio może teraz otwierać istniejące pamięci podręczne CMake wygenerowane przez narzędzia zewnętrzne, takie jak CMakeGUI, dostosowane systemy meta-Build lub skrypty kompilacji, które wywołują program CMAKE. exe.

- Ulepszona wydajność funkcji IntelliSense.

- Nowy edytor ustawień oferuje alternatywę do ręcznego edytowania pliku pliku cmakesettings. JSON i zapewnia pewną parzystość z CMakeGUI.

- Program Visual Studio ułatwia rozpoczęcie programowania w języku C++ za pomocą narzędzia CMake w systemie Linux, wykrywając, czy na komputerze z systemem Linux znajduje się zgodna wersja narzędzia CMake. W przeciwnym razie umożliwia jej zainstalowanie dla Ciebie.

- Niezgodne ustawienia w pliku cmakesettings, takie jak niezgodne architektury lub niezgodne ustawienia generatora CMake, pokazują zygzaki w edytorze JSON i błędy na liście błędów.

- W projektach CMake otwieranych w środowisku IDE po uruchomieniu polecenia `vcpkg integrate install` automatycznie jest wykrywany i włączany łańcuch narzędzi vcpkg. To zachowanie można wyłączyć, określając pusty plik łańcucha narzędzi w pliku CMakeSettings.

- W projektach CMake domyślnie jest teraz włączane debugowanie Tylko mój kod.

- Ostrzeżenia analizy statycznej można teraz przetwarzać w tle i wyświetlać w edytorze projektów CMake.

- Wyraźniejsze Kompilowanie i Konfigurowanie komunikatów "BEGIN" i "End" dla projektów CMake i obsługi interfejsu użytkownika postępu kompilacji programu Visual Studio. Ponadto istnieje teraz ustawienie szczegółowości CMake w obszarze **narzędzia > opcje** umożliwiające dostosowanie poziomu szczegółowości komunikatów kompilacji CMAKE i konfiguracji w okno dane wyjściowe.

- Ustawienie `cmakeToolchain` jest teraz obsługiwane w pliku pliku cmakesettings. JSON w celu określenia łańcuchy narzędzi bez ręcznej modyfikacji wiersza polecenia CMake.

- Nowe menu **Kompiluj wszystkie** skróty **Ctrl + Shift + B**.

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16,1

- Zintegrowana obsługa edytowania, kompilowania i debugowania projektów CMake przy użyciu Clang/LLVM. Aby uzyskać więcej informacji, zobacz [Clang/LLVM Support in Visual Studio](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/).

## <a name="linux-and-the-windows-subsystem-for-linux"></a>Linux i podsystem Windows dla systemu Linux

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16,1

- Obsługa [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) w projektach dla wielu platform w systemach Linux i CMAKE. Aby uzyskać więcej informacji, zobacz [AddressSanitizer (ASan) dla obciążenia systemu Linux w programie Visual Studio 2019](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/).

- Zintegrowana obsługa programu Visual Studio C++ do używania z podsystemem Windows dla systemu Linux (WSL). Aby uzyskać więcej informacji, zobacz temat [ C++ z programem Visual Studio 2019 i podsystemem Windows dla systemu Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

## <a name="incredibuild-integration"></a>Integracja IncrediBuild

IncrediBuild jest dołączany jako składnik opcjonalny do **tworzenia aplikacji klasycznych z C++**  obciążeniem. Monitor kompilacji IncrediBuild jest w pełni zintegrowany w środowisku IDE programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Wizualizacja kompilacji za pomocą monitora kompilacji IncrediBuild i programu Visual Studio 2019](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/).

## <a name="debugging"></a>Debugowanie

- W C++ przypadku aplikacji uruchamianych w systemie Windows pliki PDB są teraz ładowane w osobnym procesie 64-bitowym. Ta zmiana dotyczy zakresu awarii spowodowanych przez debuger z uruchomioną pamięcią w przypadku debugowania aplikacji zawierających dużą liczbę modułów i plików PDB.

- Wyszukiwanie jest włączone w oknach **czujka**, **autostarty**i **lokalne** .

## <a name="windows-desktop-development-with-c"></a>Programowanie aplikacji klasycznych systemu WindowsC++

- Te C++ kreatory ATL/MFC nie są już dostępne:

  - Kreator składników ATL COM+ 1.0
  - Kreator składnika stron Active Server ATL
  - Kreator dostawcy OLE DB ATL
  - Kreator strony właściwości ATL
  - Kreator OLE DB klienta ATL
  - Odbiorca MFC ODBC
  - Klasa MFC z kontrolki ActiveX
  - Klasa MFC z typu lib.

  Przykładowy kod dla tych technologii jest archiwizowany w Microsoft Docs i repozytorium GitHub VCSamples.

- Zestaw Windows 8.1 SDK nie jest już dostępny w instalatorze programu Visual Studio. Zalecamy uaktualnienie C++ projektów do najnowszej wersji systemu Windows 10 SDK. Jeśli masz twardą zależność od 8,1, możesz pobrać ją z archiwum Windows SDK.

- Obsługa systemu Windows XP nie będzie już dostępna w najnowszym zestawie narzędzi języka C++. Program XP obsługujący biblioteki MSVC & kompilatora programu VS 2017 na poziomie jest nadal obsługiwany i można go zainstalować za pomocą "poszczególnych składników".

- Nasza dokumentacja aktywnie zniechęca do użycia modułów scalania w przypadku wdrożenia środowiska uruchomieniowego Visual C++. Zajmiemy się dodatkowymi krokami w tej wersji o oznaczaniu naszych MSMs jako przestarzałych. Rozważ migrację wdrożenia centralnego VCRuntime z plików MSM do pakietu redystrybucyjnego.

## <a name="mobile-development-with-c-android-and-ios"></a>Programowanie aplikacji mobilnych C++ za pomocą systemu (Android i iOS)

Środowiskiem systemu Android dla języka C++ jest teraz domyślnie zestaw SDK 25 dla systemu Android i zestaw NDK 16b dla systemu Android.

## <a name="clangc2-platform-toolset"></a>Zestaw narzędzi platformy Clang/C2

Składnik eksperymentalny Clang/C2 został usunięty. Użyj zestawu narzędzi MSVC, aby C++ uzyskać pełną zgodność ze standardami `/permissive-` i `/std:c++17`lub łańcucha narzędzi CLANG/LLVM dla systemu Windows.

## <a name="code-analysis"></a>Analiza kodu

- Analiza kodu działa teraz automatycznie w tle. Ostrzeżenia są wyświetlane podczas pisania jako zielone podkreślenia w edytorze. Aby uzyskać więcej informacji, zobacz [Analiza kodu w edytorze w programie Visual Studio 2019 (wersja zapoznawcza 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/)).

- Nowe eksperymentalne reguły ConcurrencyCheck dla dobrze znanych standardowych typów bibliotek z nagłówka > mutex \<. Aby uzyskać więcej informacji, zobacz [Analiza kodu współbieżności w programie Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/).

- Zaktualizowana częściowa implementacja [Narzędzia sprawdzania profilu okresu istnienia](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/), która wykrywa zawieszonegoe wskaźniki i odwołania. Aby uzyskać więcej informacji, zobacz [Aktualizacja profilu okresu istnienia w programie Visual Studio 2019 (wersja zapoznawcza 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/)).

- Więcej kontroli związanych z innymi procedurami, w tym C26138, C26810, C26811 i doświadczalną regułę C26800. Aby uzyskać więcej informacji, zobacz [nowe sprawdzenia analizy kodu w programie Visual Studio 2019: Użyj funkcji-After-Move i wspólnej](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/).

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16,1

- Nowe szybkie poprawki dla niezainicjowanych testów zmiennych. Aby uzyskać więcej informacji, zobacz [nowe szybkie poprawki analizy kodu dla niezainicjowanej pamięci (C6001) i używane przed ostrzeżeniami init (C26494)](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/).

## <a name="unit-testing"></a>Testowanie jednostek

Szablon zarządzanego projektu testowego w języku C++ nie jest już dostępny. Można nadal używać zarządzanego C++ środowiska testowego w istniejących projektach. W przypadku nowych testów jednostkowych należy rozważyć użycie jednego z natywnych platform testowych, dla których program Visual Studio udostępnia szablony (MSTest, Google Test) lub C# szablon zarządzanego projektu testowego.

::: moniker-end

::: moniker range="=vs-2017"

Program Visual Studio 2017 oferuje wiele aktualizacji i poprawek do C++ środowiska. Naprawiono ponad 250 usterek i zgłoszonych problemów w kompilatorze i narzędziach, wiele przesłanych przez klientów w wyniku [zgłoszenia problemu i udostępnienia opcji sugestii](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2017) w obszarze **Wyślij opinię**. Dziękujemy za zgłaszanie usterek! Aby uzyskać więcej informacji na temat nowości we wszystkich wersjach programu Visual Studio, zobacz [co nowego w programie Visual studio 2017](/visualstudio/ide/whats-new-visual-studio-2017?view=vs-2017). Aby uzyskać informacje na temat Nowości C++ w programie visual Studio 2019, zobacz [co nowego w C++ programie Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Aby uzyskać informacje na temat Nowości C++ w programie visual Studio 2015 i starszych wersjach, zobacz Wizualizacja nowości w programie [visual C++ 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>kompilator C++

### <a name="c-conformance-improvements"></a>C++ulepszenia zgodności

W tej wersji zaktualizowaliśmy standardową bibliotekę i kompilator języka C++ o rozszerzoną obsługę funkcji języka C ++ 11 i C ++ 14, a także wstępną obsługę niektórych funkcji, które mają zostać uwzględnione w standardowym języku C ++ 17. Aby uzyskać szczegółowe informacje, zobacz [ C++ ulepszenia zgodności w programie Visual Studio 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

Kompilator obsługuje około 75% funkcji, które są nowe w języku C++ 17, w tym powiązania strukturalne, `constexpr` wyrażeń lambda, `if constexpr`, zmiennych wbudowanych, składania wyrażeń i dodawania `noexcept` do systemu typów. Te funkcje są dostępne w opcji **/std: c++ 17** . Aby uzyskać więcej informacji, zobacz [ C++ ulepszenia zgodności w programie Visual Studio 2017](cpp-conformance-improvements.md)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15,7

Zestaw narzędzi kompilatora MSVC w programie Visual Studio w wersji 15,7 jest teraz zgodny ze C++ standardem. Aby uzyskać więcej informacji, zobacz temat [ogłaszanie: MSVC jest C++ zgodny z normą](https://devblogs.microsoft.com/cppblog/announcing-msvc-conforms-to-the-c-standard/) i [zgodnością języka firmy Microsoft C++ ](../visual-cpp-language-conformance.md).

### <a name="new-compiler-options"></a>Nowe opcje kompilatora

- [/permissive-](../build/reference/permissive-standards-conformance.md): Włącz wszystkie ścisłe standardy zgodne z opcjami kompilatora i Wyłącz większość rozszerzeń kompilatora specyficznych dla firmy Microsoft (na przykład nie `__declspec(dllimport)`). Ta opcja jest domyślnie włączona w programie Visual Studio 2017 w wersji 15,5.  Tryb zgodności **/permissive-** obejmuje obsługę dwuetapowego wyszukiwania nazw. Aby uzyskać więcej informacji, zobacz [ C++ ulepszenia zgodności w programie Visual Studio](cpp-conformance-improvements.md).

- [/Diagnostics](../build/reference/diagnostics-compiler-diagnostic-options.md): Włącz wyświetlanie numeru wiersza, numeru wiersza i kolumny, a także numeru wiersza i kolumny oraz karetki w wierszu kodu, w którym znaleziono błąd lub ostrzeżenie diagnostyki.

- [/Debug: Fastlink](../build/reference/debug-generate-debug-info.md): Włącz do 30% szybszych przyrostowych czasów linków (vs. Visual Studio 2015), nie kopiując wszystkich informacji debugowania do pliku PDB. Zamiast tego plik PDB wskazuje informacje o debugowaniu dla plików obiektu i biblioteki użytych do utworzenia pliku wykonywalnego. Zobacz [szybszy C++ cykl kompilacji w programie vs "15" z opcją/Debug: Fastlink](https://devblogs.microsoft.com/cppblog/faster-c-build-cycle-in-vs-15-with-debugfastlink/) i [zalecenia C++ dotyczące szybkości kompilacji w programie Visual Studio](https://devblogs.microsoft.com/cppblog/recommendations-to-speed-c-builds-in-visual-studio/).

- Program Visual Studio 2017 umożliwia korzystanie z [/SDL](../build/reference/sdl-enable-additional-security-checks.md) z [/await](../build/reference/await-enable-coroutine-support.md). Firma Microsoft usunęła ograniczenie [/RTC](../build/reference/rtc-run-time-error-checks.md) z procedurami.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15,3

- [/std: c++ 14 i/std: c + + Najnowsza](../build/reference/std-specify-language-standard-version.md): te opcje kompilatora umożliwiają wybór określonych wersji języka programowania ISO C++ w projekcie. Większość nowych funkcji w wersji Standard jest chronionych przez **/std: c + + Najnowsza** opcja.

- [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) włącza zestaw funkcji języka c++ 17 wdrożonych przez kompilator. Ta opcja powoduje wyłączenie obsługi biblioteki kompilatora i standardowej dla funkcji, które są zmieniane lub nowe w wersjach roboczych roboczej i aktualizacji wad C++ standard po c++ 17. Aby włączyć te funkcje, użyj **/std: c + + Najnowsza**.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, zabezpieczenia, Diagnostyka i przechowywanie wersji

W tej wersji wprowadzono kilka ulepszeń optymalizacji, generowania kodu, przechowywania wersji zestawu narzędzi i diagnostyki. Do istotnych ulepszeń należą:

- Ulepszone generowanie kodu pętli: obsługa automatycznej wektoryzacji dzielenia stałych liczb całkowitych, lepsza identyfikacja wzorców funkcji memset.
- Ulepszone zabezpieczenia kodu: Ulepszona emisja diagnostyki kompilatora przepełnienia buforu i [/Guard: CF](../build/reference/guard-enable-control-flow-guard.md) teraz zabezpiecza instrukcje Switch, które generują tabele skoku.
- Przechowywanie wersji: wartość wbudowanego makra preprocesora **\_MSC\_Ver** jest teraz monotonicznie aktualizowana w każdej aktualizacji zestawu narzędzi wizualnych C++ . Aby uzyskać więcej informacji, [Zobacz C++ Visual kompilator Version](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/).
- Nowy układ zestawu narzędzi: kompilator i powiązane narzędzia do kompilacji mają nową lokalizację i strukturę katalogów na komputerze deweloperskim. Nowy układ umożliwia instalacje równoległe wielu wersji kompilatora. Aby uzyskać więcej informacji, zobacz [układ narzędzi kompilatora w programie Visual Studio 2017](https://devblogs.microsoft.com/cppblog/compiler-tools-layout-in-visual-studio-15/).
- Ulepszona diagnostyka: w oknie danych wyjściowych jest teraz wyświetlana kolumna, w której występuje błąd. Aby uzyskać więcej informacji, zobacz [ C++ ulepszenia diagnostyki kompilatora w programie vs "15" (wersja zapoznawcza 5](https://devblogs.microsoft.com/cppblog/c-compiler-diagnostics-improvements-in-vs-15-rc/)).
- W przypadku korzystania z procedur współpracujących, wartość **eksperymentalnego słowa** kluczowego (dostępnego w opcji **/await** ) została usunięta. Kod powinien zostać zaktualizowany tak, aby używał `co_yield`. Aby uzyskać więcej informacji, zobacz [`yield` słowo kluczowe do `co_yield` w programie VS 2017](https://devblogs.microsoft.com/cppblog/yield-keyword-to-become-co_yield-in-vs-2017/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15,3

Dodatkowe ulepszenia diagnostyki w kompilatorze. Aby uzyskać więcej informacji, zobacz [udoskonalenia diagnostyczne w programie Visual Studio 2017 15.3.0](https://devblogs.microsoft.com/cppblog/diagnostic-improvements-in-vs2017-15-3-0/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

Wydajność C++ środowiska uruchomieniowego Visual w dalszym ciągu ulepsza się z powodu lepszej wygenerowanej jakości kodu. Teraz możesz po prostu ponownie skompilować kod i aplikacja działała szybciej. Niektóre optymalizacje kompilatora są zupełnie nowe, takie jak wektoryzacji warunkowych magazynów skalarnych, łączenie wywołań `sin(x)` i `cos(x)` do nowego `sincos(x)`oraz Usuwanie nadmiarowych instrukcji z Optymalizatora usługi SSA. Inne optymalizacje kompilatora to ulepszenia istniejących funkcji, takie jak heurystyka wektoryzator dla wyrażeń warunkowych, lepsza Optymalizacja pętli i zmiennoprzecinkowa minimalna/maksymalna codegena. Konsolidator ma nową i szybszą **/OPT: implementację zapory ICF** , co może skutkować do 9% czasu konsolidacji przyspieszenia i innych poprawek wydajności w konsolidacji przyrostowej. Aby uzyskać więcej informacji, zobacz [/opt (optymalizacje)](../build/reference/opt-optimizations.md) i [/Incremental (łączenie przyrostowo)](../build/reference/incremental-link-incrementally.md).

Kompilator firmy C++ Microsoft obsługuje AVX-512, w tym instrukcje długości wektora, które wprowadzają nowe funkcje w AVX-512 do 128-bit i 256-bit Wide.

Opcja [/Zc: noexceptTypes-](../build/reference/zc-noexcepttypes.md) umożliwia przywrócenie do wersji c++ 14 `noexcept` w przypadku ogólnego użycia trybu c++ 17. Ta opcja umożliwia zaktualizowanie kodu źródłowego tak, aby był zgodny z językiem C++ 17 bez konieczności ponownego zapisywania całego kodu `throw()`. Aby uzyskać więcej informacji, zobacz sekcję [usuwanie specyfikacji wyjątków dynamicznych i noexcept](cpp-conformance-improvements.md#noexcept_removal).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15,7

- Nowy przełącznik kompilatora [/Qspectre](../build/reference/qspectre.md) , aby pomóc w wyeliminowaniu ataków na kanał po stronie wykonywania spekulacyjnego. Aby uzyskać więcej informacji, zobacz [Spectree ograniczenia w MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).
- Nowe ostrzeżenie diagnostyczne na potrzeby ograniczenia Spectre. Aby uzyskać więcej informacji, zobacz [Spectre Diagnostic in Visual Studio 2017 w wersji 15,7 Preview 4](https://devblogs.microsoft.com/cppblog/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/).
- Nowa wartość dla/Zc, **/Zc: __cplusplus**, umożliwia poprawne raportowanie pomocy technicznej C++ Standard. Na przykład, gdy przełącznik jest ustawiony i kompilator jest w/std: c++ 17 tryb, wartość zostanie rozwinięta do **201703L**. Aby uzyskać więcej informacji, zobacz [MSVC teraz prawidłowo raporty __cplusplus](https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/).

## <a name="c-standard-library"></a>C++Biblioteka standardowa

### <a name="correctness-improvements"></a>Ulepszenia poprawności

##### <a name="visual-studio-2017-rtm-version-150"></a>Visual Studio 2017 RTM (wersja 15,0)

- Ulepszenia diagnostyki `_ITERATOR_DEBUG_LEVEL != 0` `basic_string`. Wyzwolenie kontroli IDL w maszynie ciągu zgłasza teraz określone zachowanie, które spowodowało wyzwolenie. Na przykład zamiast komunikatu „iterator ciągu nie umożliwia wyłuskiwania” otrzymasz komunikat „nie można wyłuskać iteratora ciągu, ponieważ jest on poza zakresem (np. iterator końca)”.
- Naprawiono operator przypisania przenoszenia `std::promise`, który wcześniej mógłby spowodować zablokowanie kodu na zawsze.
- Naprawiono błędy kompilatora z `atomic<T*>` niejawną konwersję na `T*`.
- `pointer_traits<Ptr>` teraz prawidłowo wykrywa `Ptr::rebind<U>`.
- Naprawiono brak kwalifikatora `const` w operatorze odejmowania `move_iterator`.
- Rozwiązano cichą codegeną nieprawidłowych dla stanowych zdefiniowanych przez użytkownika przystawek żądających `propagate_on_container_copy_assignment` i `propagate_on_container_move_assignment`.
- `atomic<T>` teraz tolerowane `operator&()`przeciążone.
- Nieco Ulepszona diagnostyka kompilatora dla nieprawidłowych wywołań `bind()`.

Aby zapoznać się z pełną listą ulepszeń biblioteki standardowej w programie Visual Studio 2017 RTM C++ , zobacz sekcję [poprawki w blogu zespołu standard w programie vs 2017 RTM](https://devblogs.microsoft.com/cppblog/stl-fixes-in-vs-2017-rtm/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15,3

- Kontenery biblioteki standardowej teraz zawężają `max_size()` do `numeric_limits<difference_type>::max()`, a nie `max()` `size_type`. Ta zmiana gwarantuje, że wynik `distance()` na iteratorach z tego kontenera zostanie zaprezentowany w typie zwracanym `distance()`.
- Naprawiono brak `auto_ptr<void>`specjalizacji.
- Nie można skompilować wcześniej algorytmów `for_each_n()`, `generate_n()`i `search_n()`, jeśli długość argumentu nie jest typem całkowitym; teraz podejmują próbę przekonwertowania długości niecałkowitych na Iteratory `difference_type`.
- `normal_distribution<float>` nie emituje już ostrzeżeń wewnątrz standardowej biblioteki o zawężaniu wartości z podwójnej do zmiennoprzecinkowej.
- Naprawiono niektóre operacje `basic_string`, które były używane `npos` zamiast `max_size()` podczas sprawdzania maksymalnego rozmiaru przepełnienia.
- `condition_variable::wait_for(lock, relative_time, predicate)` będzie oczekiwać na cały względny czas w przypadku fałszywe Wake. Teraz będzie oczekiwać tylko jednego interwału czasu względnego.
- `future::get()` teraz unieważnia `future`, zgodnie z wymaganiami standardowymi.
- `iterator_traits<void *>` używany jako twardy błąd, ponieważ próbuje utworzyć `void&`; teraz czyści ona pustą strukturę, aby zezwolić na używanie `iterator_traits` w warunkach SFINAE ".
- Niektóre ostrzeżenia zgłoszone przez Clang **-wSystem-Headers** zostały naprawione.
- Ustalono również "Specyfikacja wyjątku w deklaracji jest niezgodna z poprzednią deklaracją" zgłoszoną przez Clang **-wMicrosoft-Exception-spec**.
- Również stałe pamięci podręcznej określania kolejności list raportowane przez Clang i C1XX.
- Kontenery nieuporządkowane nie zamieniają swoich funkcji skrótu ani predykatów, gdy same kontenery zostały zamienione. Teraz.
- Wiele operacji wymiany kontenerów jest teraz oznaczonych `noexcept` (ponieważ nasza Biblioteka standardowa nigdy nie zaproponuje wygenerowania wyjątku podczas wykrywania nie`propagate_on_container_swap` niezdefiniowanego warunku zachowania nierównego alokatora).
- Wiele operacji `vector<bool>` jest teraz oznaczonych `noexcept`.
- Biblioteka standardowa będzie teraz wymuszać pasujące `value_type` alokatora (w trybie C++ 17) z wylęgowych ucieczki.
- Rozwiązano pewne warunki, w których funkcja samodzielnego wstawiania do `basic_string` może zaszyfrować zawartość ciągów. (Uwaga: zestaw samodzielny — Wstawianie do wektorów jest nadal zabroniony przez standard).
- `propagate_on_container_swap`alokatora nie ma już na `basic_string::shrink_to_fit()`.
- `std::decay` teraz obsługuje typy funkcji Abominable, czyli typy funkcji, które są kwalifikowane i/lub ref z kwalifikatorem.
- Zmieniono dyrektywy include, aby użyć poprawnej czułości wielkości liter i ukośników, co poprawia możliwości przenoszenia.
- Stałe ostrzeżenie C4061 "*Enumerator" w*przełączniku wyliczenia*wyliczeniowy "nie*jest jawnie obsługiwane przez etykietę case". To ostrzeżenie jest domyślnie wyłączone i zostało naprawione jako wyjątek od ogólnych zasad biblioteki standardowej dla ostrzeżeń. (Standardowa biblioteka to **/W4** Clean, ale nie próbuje być **/Wall** Clean. Wiele ostrzeżeń, które są domyślnie, są niezwykle zakłóceni i nie są przeznaczone do regularnego użycia.
- Udoskonalone testy debugowania `std::list`. Iteratory list sprawdzają teraz `operator->()`i `list::unique()` teraz oznacza Iteratory jako unieważnione.
- Stałe zastosowania-Programowanie dla programu przydzielające w `tuple`.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

- `std::partition` teraz wywołuje predykat N razy zamiast N + 1 razy, zgodnie z wymaganiami standardowymi.
- Program podejmie próbę uniknięcia, że w wersji 15,3 został na15,5 prawiony Magiczna liczba statycznych.
- `std::atomic<T>` nie muszą już `T` być domyślne konstrukcyjną.
- Algorytmy sterty, które pobierają czas logarytmiczny, nie wykonują już jednoliniowej potwierdzenia, że dane wejściowe są w rzeczywistości stertą, gdy jest włączone debugowanie iteratora.
- `__declspec(allocator)` jest teraz chroniona tylko dla C1XX, aby zapobiec występowaniu ostrzeżeń z Clang, które nie rozumie tego declspec.
- `basic_string::npos` jest teraz dostępna jako stała czasu kompilacji.
- `std::allocator` w trybie C++ 17 prawidłowo obsługuje alokację typów nadmiernie wyrównanych, czyli typów, których wyrównanie jest większe niż `max_align_t`, chyba że są wyłączone przez **/Zc: alignedNew-** .  Na przykład wektory obiektów z wyrównaniam 16-bajtowym lub 32-bajtowym są teraz prawidłowo wyrównane do instrukcji SSE i AVX.

### <a name="conformance-improvements"></a>Ulepszenia zgodności

- Dodaliśmy \<dowolnych\>, \<string_view\>, `apply()``make_from_tuple()`.
- Dodano \<opcjonalne\>, \<wariantów\>, `shared_ptr::weak_type`i \<cstdalign\>.
- Włączono `constexpr` języka C++ 14 w `min(initializer_list)`, `max(initializer_list)`i `minmax(initializer_list)`, a `min_element()`, `max_element()`i `minmax_element()`.

Aby uzyskać więcej informacji, [Zobacz C++ tabela zgodność z językiem Microsoft](../visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15,3

- Wprowadzono kilka dodatkowych funkcji języka C++ 17. Aby uzyskać więcej informacji, [Zobacz C++ tabela zgodność z językiem Microsoft](cpp-conformance-improvements.md#improvements_153).
- Zaimplementowana P0602R0 "Variant i Optional powinna propagować nieuproszczoność kopiowania/przenoszenia".
- Biblioteka standardowa teraz oficjalnie dopuszcza, aby dynamiczne RTTI były wyłączone za pośrednictwem opcji [/gr-](../build/reference/gr-enable-run-time-type-information.md) . Zarówno `dynamic_pointer_cast()`, jak i `rethrow_if_nested()` niezależnie wymagają `dynamic_cast`, więc Biblioteka standardowa teraz oznacza je jako `=delete` w **/gr-** .
- Nawet jeśli dynamiczny RTTI został wyłączony za pośrednictwem **/gr-** , "static RTTI" w formie `typeid(SomeType)` jest nadal dostępny i ma kilka składników biblioteki standardowej. Biblioteka standardowa obsługuje teraz wyłączenie tej funkcji za pośrednictwem **/d\_ma\_STATIC\_RTTI = 0**. Ta flaga wyłącza również `std::any`, `target()` i `target_type()` funkcje składowe `std::function`i `get_deleter()`e zaprzyjaźnionej funkcji składowej `std::shared_ptr` i `std::weak_ptr`.
- Biblioteka standardowa domyślnie używa języka C++ 14 `constexpr` bezwarunkowo, zamiast wstępnie zdefiniowanych makr.
- Biblioteka standardowa używa teraz szablonów aliasów wewnętrznie.
- Biblioteka standardowa używa teraz `nullptr` wewnętrznie, a nie `nullptr_t{}`. (Zostało wyeliminowane wewnętrzne użycie wartości NULL. Wewnętrzne użycie 0-jako-null jest czyszczone stopniowo.)
- Biblioteka standardowa używa teraz `std::move()` wewnętrznie, zamiast stylistically się niew `std::forward()`.
- Zmieniono `static_assert(false, "message")` na `#error message`. Ta zmiana poprawia diagnostykę kompilatora, ponieważ `#error` natychmiast zatrzymać kompilację.
- Biblioteka standardowa nie oznacza już funkcji jako `__declspec(dllimport)`. Nowoczesne technologie konsolidatora nie wymagają już tego.
- Wyodrębniono SFINAE do domyślnych argumentów szablonu, które zmniejszają bałagan w porównaniu z typami zwracanymi i typami argumentów funkcji.
- Testy debugowania w \<losowo\> teraz używają zwykłych maszyn w standardowej bibliotece zamiast wewnętrznej funkcji `_Rng_abort()`, która nazywa `fputs()` do **stderr**. Implementacja tej funkcji jest zachowywana na potrzeby zgodności binarnej, ale została usunięta w następnej binarnej niezgodnej wersji biblioteki standardowej.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

- Kilka standardowych funkcji biblioteki zostało dodanych, przestarzałe lub usunięte zgodnie ze standardem C++ 17. Aby uzyskać więcej informacji, zobacz [ C++ ulepszenia zgodności w programie Visual Studio](cpp-conformance-improvements.md#improvements_155).
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
- Sygnatury następujących algorytmów równoległych są dodawane, ale w tej chwili nie są równoległe; Profilowanie nie wykazało korzyści w algorytmach przekształcają, które tylko przesuwają lub Permute — elementy:
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

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 w wersji 15,6

- \<memory_resource >
- Podstawowe informacje o bibliotece v1
- Usuwanie przypisania `polymorphic_allocator`
- Ulepszanie odejmowania argumentów szablonu klasy

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15,7

- Obsługa algorytmów równoległych nie jest już eksperymentalna
- Nowa implementacja systemu \<FileSystem >
- Konwersje elementarne ciągów (częściowa)
- `std::launder()`
- `std::byte`
- `hypot(x,y,z)`
- Uniknięcie niepotrzebnego uszkodzenia
- Specjalne funkcje matematyczne
- `constexpr char_traits`
- Wskazówki dotyczące odejmowania dla standardowej biblioteki

Aby uzyskać więcej informacji, [Zobacz C++ tabela zgodność z językiem Microsoft](../visual-cpp-language-conformance.md).

### <a name="performance-and-throughput-fixes"></a>Poprawki wydajności i przepływności

- `basic_string::find(char)` przeciążenia `traits::find` tylko raz. Wcześniej była zaimplementowana jako ogólne wyszukiwanie ciągu dla ciągu o długości 1.
- `basic_string::operator==` teraz sprawdza rozmiar ciągu przed porównaniem zawartości ciągów znaków.
- Usunięto sprzężenie kontrolne w `basic_string`, które było trudne do analizowania przez optymalizator kompilatora. W przypadku wszystkich krótkich ciągów wywołanie `reserve` nadal ma koszt różny od zera.
- `std::vector` został przekroczony w celu poprawienia i wydajności: aliasowanie podczas operacji INSERT i emplace jest teraz prawidłowo obsługiwane zgodnie z wymaganiami Standard, silna gwarancja wyjątku jest teraz dostępna, gdy jest to wymagane przez standard za pośrednictwem `move_if_noexcept()` i innych logika i Insert i emplace wykonują mniejszą liczbę operacji elementu.
- Biblioteka C++ standardowa pozwala teraz uniknąć odwołujących się do pustych wskaźników ozdobnych.
- Ulepszona wydajność `weak_ptr::lock()`.
- Aby zwiększyć przepływność kompilatora C++ , nagłówki biblioteki standardowej można teraz uniknąć, włączając deklaracje dla zbędnych funkcji wewnętrznych kompilatora.
- Ulepszona wydajność `std::string` i `std::wstring` konstruktorów przenoszenia przez więcej niż trzy razy.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15,3

- Obejść interakcje z `noexcept`, które uniemożliwiają wprowadzanie implementacji `std::atomic` do funkcji, które korzystają z obsługi wyjątków strukturalnych (SEH).
- Zmieniono funkcję wewnętrznej `_Deallocate()` biblioteki standardowej, aby zoptymalizować do mniejszego kodu, co pozwala na przekreślenie do większej liczby miejsc.
- Zmieniono `std::try_lock()`, aby użyć rozwinięcia pakietu zamiast rekursji.
- Ulepszono algorytm unikania zakleszczenia `std::lock()` w celu używania operacji `lock()` zamiast nawirowania `try_lock()` na wszystkich blokadach.
- Włączono optymalizację nazwanej wartości zwracanej w `system_category::message()`.
- `conjunction` i `disjunction` teraz tworzy wystąpienia N + 1 typów, a nie typy 2N + 2.
- nie `std::function` już tworzy wystąpienia maszyn obsługi programu przydzielania dla każdego typu, który został wymazany, zwiększając przepływność i zmniejszając rozmiar. obj w programach, które przechodzą wiele różnych wyrażeń lambda do `std::function`.
- `allocator_traits<std::allocator>` zawiera ręcznie wbudowane operacje `std::allocator`, skracając rozmiar kodu w kodzie, który współdziała z `std::allocator` przez `allocator_traits` (to jest w większości kodu).
- Interfejs języka C++ 11 minimalnego alokatora jest teraz obsługiwany przez standardową bibliotekę wywołującą `allocator_traits` bezpośrednio, zamiast pakowania alokatora w wewnętrznej klasie `_Wrap_alloc`. Ta zmiana zmniejsza rozmiar kodu wygenerowanego na potrzeby obsługi alokatora, usprawnia w niektórych przypadkach możliwość optymalizacji w przypadku kontenerów biblioteki standardowej, a także udostępnia lepsze środowisko debugowania (ponieważ teraz można zobaczyć typ alokatora, a nie `_Wrap_alloc<your_allocator_type>` w Debuger).
- Usunięto Programowanie dla dostosowanych `allocator::reference`, które nie są faktycznie dozwolone do dostosowania. (Przydzielenie mogą sprawić, że kontenery korzystają z ozdobnych wskaźników, ale nie są to odwołania ozdobne).
- Fronton kompilatora był sposobem na odwinięcie iteratorów debugowania w oparciu o pętle, zwiększając wydajność kompilacji debugowania.
- `basic_string` wewnętrzna ścieżka zmniejszania dla `shrink_to_fit()` i `reserve()` nie znajduje się już w ścieżce ponownych alokacji operacji, co zmniejsza rozmiar kodu dla wszystkich elementów członkowskich.
- Ścieżka wewnętrznego wzrostu `basic_string` nie znajduje się już w ścieżce `shrink_to_fit()`.
- `basic_string` modyfikowanie operacji jest teraz uwzględniane w przypadku przydzielenia szybkiej ścieżki i przydzielania funkcji powolnych ścieżek, co jest bardziej podobne dla przypadków, w których nie można ponownie przydzielić, aby nie były one wbudowane w obiekty wywołujące.
- `basic_string` mutacje operacji teraz konstruują ponownie przydzieloną bufory w żądanym stanie zamiast zmieniać rozmiar w miejscu. Na przykład wstawianie na początku ciągu teraz przenosi zawartość po wstawieniu dokładnie raz (w dół lub do nowo przydzielonych buforów), zamiast dwukrotnie w przypadku ponownej alokacji (do nowo przydzielonych buforów, a następnie w dół).
- Operacje wywołujące bibliotekę języka C w \<ciągu\> teraz buforują adres `errno`, aby usunąć powtórzoną interakcję z protokołem TLS.
- Uproszczona implementacja `is_pointer`.
- Zakończono zmianę SFINAE wyrażeń opartych na funkcjach na `struct` i `void_t`.
- Algorytmy biblioteki standardowej teraz unikają iteratorów postincrementing.
- Stałe ostrzeżenia obcinania w przypadku korzystania z 32-bitowych przystawek w systemach 64-bitowych.
- `std::vector` przenoszenie przydziału jest teraz bardziej wydajne w przypadku niePOCMAego przypadku alokatora, gdy jest to możliwe.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

- `basic_string<char16_t>` teraz korzysta z tych samych `memcmp`, `memcpy`i podobnych optymalizacji, które `basic_string<wchar_t>` zaangażują się.
- Ograniczenie Optymalizatora, które uniemożliwiło wbudowanie wskaźników funkcji, uwidocznionych przez nasze działania "Unikaj kopiowania funkcji" w programie Visual Studio 2015 Update 3, obejść, przywracając wydajność `lower_bound(iter, iter, function pointer)`.
- Narzuty weryfikacji kolejności debugowania iteratora danych wejściowych do `includes`, `set_difference`, `set_symmetric_difference`i `set_union` zostało zredukowane przez odpakowanie iteratorów przed sprawdzeniem kolejności.
- `std::inplace_merge` teraz pomija elementy, które już znajdują się na pozycji.
- Konstruowanie `std::random_device` nie jest już konstrukcje, a następnie niszczy `std::string`.
- `std::equal` i `std::partition` miały przebieg optymalizacji wielowątkowości z przeskokiem, który zapisuje porównanie iteratora.
- Gdy `std::reverse` są przenoszone wskaźniki do `T`owo kopiującego, będzie teraz wysyłany do rozpisanej ręcznie implementacji.
- `std::fill`, `std::equal`i `std::lexicographical_compare` zostały rozłożenia, jak wysyłać do `memset` i `memcmp` dla `std::byte` i `gsl::byte` (oraz innych wyliczeniowych, takich jak wyliczenia i klasy enum). Ponieważ `std::copy` są wysyłane przy użyciu `is_trivially_copyable`, nie wymagały żadnych zmian.
- Biblioteka standardowa nie zawiera już pustych nawiasów klamrowych, których jedynym zachowaniem było dokonanie, że typy nie zniszczalnych.

## <a name="other-libraries"></a>Inne biblioteki

### <a name="open-source-library-support"></a>Obsługa biblioteki Open Source

**Vcpkg** to narzędzie wiersza polecenia typu open source, które znacznie upraszcza proces pozyskiwania i tworzenia statycznych libs i bibliotek DLL typu Open C++ Source w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [vcpkg: A Package Manager C++for ](../build/vcpkg.md).

### <a name="cpprest-sdk-290"></a>CPPRest SDK 2.9.0

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

CPPRestSDK, Międzyplatformowy interfejs API sieci Web dla C++programu, został zaktualizowany do wersji 2.9.0. Aby uzyskać więcej informacji, zobacz [CppRestSDK 2.9.0 jest dostępny w witrynie GitHub](https://devblogs.microsoft.com/cppblog/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

- Jeszcze inny zestaw poprawek zgodności z wyszukiwaniem nazw
- Istniejące konstruktory przenoszenia i operatory przypisania przenoszenia są teraz prawidłowo oznaczone jako niezgłaszane
- Nie pomijaj prawidłowego ostrzeżenia C4640 o inicjacji bezpiecznego wątku lokalnych elementów statycznych w pliku atlstr. h
- Inicjowanie bezpiecznego wątku lokalnych elementów statycznych zostało automatycznie wyłączone w zestawie narzędzi systemu XP podczas tworzenia biblioteki DLL przy użyciu biblioteki ATL, ale teraz nie jest to możliwe. Można dodać **/Zc: threadSafeInit-** w ustawieniach projektu, jeśli pożądane jest zainicjowanie bezpiecznego wątkowo.

### <a name="visual-c-runtime"></a>Środowisko C++ uruchomieniowe języka Visual

- Nowy nagłówek "cfguard. h" dla symboli ochrony przepływu sterowania.

## <a name="c-ide"></a>Środowisko IDE języka C++

- Wydajność wprowadzania zmian w konfiguracji jest teraz lepsza w przypadku natywnych projektów w języku C++ i o wiele lepsza w projektach C++/CLI. Gdy konfiguracja rozwiązania jest uaktywniana po raz pierwszy, będzie ona teraz szybsza i wszystkie późniejsze aktywacje konfiguracji rozwiązania będą prawie natychmiastowo.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15,3

- Ponownie napisano kilka kreatorów projektu i kodów w stylu okna dialogowego podpisu.
- **Dodaj klasę** teraz uruchamia Kreatora dodawania klasy bezpośrednio. Wszystkie inne elementy, które wcześniej znajdowały się w tym miejscu, są teraz dostępne w obszarze **dodaj > nowy element**.
- Projekty Win32 znajdują się teraz w kategorii **pulpitu systemu Windows** w oknie dialogowym **Nowy projekt** .
- Szablony **konsoli systemu Windows** i **aplikacji klasycznych** teraz tworzą projekty bez wyświetlania kreatora. W tej samej kategorii jest dostępny nowy **Kreator pulpitu systemu Windows** , w którym są wyświetlane te same opcje, co w przypadku starego kreatora **aplikacji konsolowej Win32** .

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

Kilka C++ operacji, które używają aparatu IntelliSense do refaktoryzacji i nawigowania po kodzie działa znacznie szybciej. Następujące numery opierają się na rozwiązaniu Visual Studio chrom z projektami 3500:

|||
|-|-|
|Funkcja|Poprawa wydajności|
|Zmień nazwę|5.3 x|
|Zmień sygnaturę |4,5 x|
|Znajdź wszystkie odwołania|4,7 x|

C++Program obsługuje teraz kombinację klawiszy Ctrl + kliknij **Przejdź do definicji**, dzięki czemu Nawigacja myszą jest prosta. Wizualizator struktury z pakietu narzędzi do wydajnej wydajności jest teraz również uwzględniony w produkcie.

## <a name="intellisense"></a>IntelliSense

- Nowy aparat bazy danych oparty na SQLite jest teraz używany domyślnie. Przyspieszy to wykonywanie operacji bazy danych, takich jak **Przejdź do definicji** i **Znajdź wszystkie odwołania**, a znacznie zwiększy czas wstępnej analizy rozwiązania. To ustawienie zostało przeniesione do **narzędzi > opcje > edytora tekstów > CC++ /> Advanced** (wcześniej było w... C/C++ | Eksperymentalne).

- Ulepszono wydajność IntelliSense w projektach i plikach, które nie używają prekompilowanych nagłówków — automatycznie prekompilowany nagłówek zostanie utworzony dla nagłówków w bieżącym pliku.

- Do listy błędów dodaliśmy filtrowanie błędów i pomoc dotyczącą błędów funkcji IntelliSense. Kliknięcie kolumny błędów umożliwia teraz filtrowanie. Ponadto kliknięcie konkretnego błędu lub naciśnięcie klawisza F1 uruchamia wyszukiwanie online dotyczące danego komunikatu o błędzie.

  ![Lista błędów](media/ErrorList1.png "Lista błędów")

  ![Lista błędów filtrowane](media/ErrorList2.png "Filtrowana lista błędów")

- Dodano możliwość filtrowania listy elementów członkowskich według rodzaju.

  ![Filtrowanie listy elementów członkowskich](media/mlfiltering.png "Filtrowanie listy elementów członkowskich")

- Dodano nową eksperymentalną funkcję IntelliSense predykcyjną, która zapewnia kontekstowe Filtrowanie elementów wyświetlanych na liście elementów członkowskich. Aby uzyskać więcej informacji, zobacz [ C++ udoskonalenia IntelliSense — przewidywalna funkcja IntelliSense & filtrowanie](https://devblogs.microsoft.com/cppblog/c-intellisense-improvements-predictive-intellisense-filtering/).
- Funkcja **Znajdź wszystkie odwołania** (Shift + F12) teraz ułatwia łatwe poruszanie się, nawet w złożonych bazach kodu. Zapewnia zaawansowane grupowanie, filtrowanie, sortowanie, wyszukiwanie w wynikach i (w przypadku niektórych języków) kolorowanie, dzięki czemu można jasno zrozumieć odwołania. W C++przypadku programu nowy interfejs użytkownika zawiera informacje o tym, czy odczytujemy lub zapisujesz do zmiennej.
- Funkcja zmiany kropki na strzałkę IntelliSense została przeniesiona z doświadczalnych do zaawansowanych i teraz jest domyślnie włączona. Funkcje edytora **rozszerzają zakresy** i **pierwszeństwo rozwijania** są również przenoszone z eksperymentalnego do zaawansowanego.
- Eksperymentalne funkcje refaktoryzacji **Zmień podpis** i **Wyodrębnij funkcję** są teraz dostępne domyślnie.
- Dodano funkcję eksperymentalnego "szybszego ładowania projektu" C++ dla projektów. Przy następnym otwarciu C++ projektu zostanie on załadowany szybciej i zostanie załadowana *znacznie* szybciej.
- Niektóre z tych funkcji są wspólne dla innych języków, a niektóre z nich są C++specyficzne dla programu. Aby uzyskać więcej informacji o tych nowych funkcjach, zobacz temat [ogłaszanie programu Visual Studio "15" (wersja zapoznawcza 5](https://devblogs.microsoft.com/visualstudio/announcing-visual-studio-15-preview-5/)).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15,7

- Dodano obsługę dla ClangFormat. Aby uzyskać więcej informacji, zobacz [Obsługa ClangFormat w programie Visual Studio 2017](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/).

## <a name="non-msbuild-projects-with-open-folder"></a>Projekty inne niż MSBuild z otwartym folderem

W programie Visual Studio 2017 wprowadzono funkcję **Otwórz folder** , która umożliwia wykonywanie kodu, kompilowanie i debugowanie w folderze zawierającym kod źródłowy bez konieczności tworzenia żadnych rozwiązań i projektów. Teraz znacznie prostsze jest rozpoczęcie pracy z programem Visual Studio, nawet jeśli projekt nie jest projektem opartym na programie MSBuild. Za pomocą **folderu Open folder**uzyskasz dostęp do zaawansowanych funkcji opisujących kod, edytowania, kompilowania i debugowania, które program Visual Studio udostępnia już dla projektów MSBuild. Aby uzyskać więcej informacji, zobacz temat [Otwieranie projektów C++folderu dla ](../build/open-folder-projects-cpp.md).

- Ulepszenia obsługi polecenia Otwórz folder. Środowisko można dostosować za pomocą tych plików JSON:
  - CppProperties.json dostosowuje obsługę funkcji IntelliSense i przeglądania.
  - Tasks.json dostosowuje kroki kompilacji.
  - Launch.json dostosowuje obsługę debugowania.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15,3

- Ulepszona obsługa alternatywnych kompilatorów i środowisk kompilacji, takich jak MinGW i Cygwin. Aby uzyskać więcej informacji, zobacz [Używanie MinGW i Cygwin z C++ wizualizacją i otwartym folderem](https://devblogs.microsoft.com/cppblog/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Dodano obsługę definiowania zmiennych środowiskowych globalnych i specyficznych dla konfiguracji w pliku cppproperties. JSON i pliku cmakesettings. JSON. Te zmienne środowiskowe mogą być używane przez konfiguracje debugowania zdefiniowane w pliku Launch. vs. JSON i zadania w pliku Tasks. vs. JSON. Aby uzyskać więcej informacji, zobacz [Dostosowywanie środowiska za pomocą C++ wizualizacji i Otwieranie folderu](https://devblogs.microsoft.com/cppblog/customizing-your-environment-with-visual-c-and-open-folder/).
- Ulepszona obsługa generatora Ninja programu CMake, w tym możliwość łatwego kierowania platform 64-bitowych.

## <a name="cmake-support-via-open-folder"></a>Obsługa CMake za pośrednictwem otwartego folderu

Program Visual Studio 2017 wprowadza obsługę projektów CMake bez konwertowania na pliki projektu MSBuild (. vcxproj). Aby uzyskać więcej informacji, zobacz [CMAKE projects in Visual Studio](../build/cmake-projects-in-visual-studio.md). Otwieranie projektów CMake z **otwartym folderem** powoduje automatyczne skonfigurowanie C++ środowiska do edycji, kompilowania i debugowania.

- C++Technologia IntelliSense działa bez konieczności tworzenia pliku pliku cppproperties. JSON w folderze głównym. Dodano również nową listę rozwijaną, aby umożliwić użytkownikom łatwe przełączanie się między konfiguracjami dostarczonymi przez pliki CMake i pliku cppproperties. JSON.

- Dalsza konfiguracja jest obsługiwana przy użyciu pliku CMakeSettings.json, który znajduje się w tym samym folderze co plik CMakeLists.txt.

  ![CMAKE Otwórz folder](media/cmake-cpp.png "CMake Otwórz folder")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15,3

- Dodano obsługę generatora Ninja CMake.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

- Dodano obsługę importowania istniejących pamięci podręcznych CMake.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

- Dodano wsparcie dla CMake 3,11, analiza kodu w projektach CMake, widok obiektów docelowych w Eksplorator rozwiązań, opcje generacji pamięci podręcznej i kompilowanie pojedynczego pliku. Aby uzyskać więcej informacji, zobacz [CMAKE Support in Visual Studio](https://devblogs.microsoft.com/cppblog/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) and [CMAKE projects in Visual Studio](../build/cmake-projects-in-visual-studio.md).

## <a name="windows-desktop-development-with-c"></a>Programowanie aplikacji klasycznych systemu WindowsC++

Zapewniamy obecnie bardziej zaawansowane środowisko instalacji oryginalnego obciążenia C++. Dodaliśmy możliwe do wybrania składniki pozwalające na zainstalowanie tylko tych narzędzi, których potrzebujesz. Wskazane rozmiary instalacji składników wymienionych w interfejsie użytkownika Instalatora nie są dokładne i nie stanowią oszacowania łącznego rozmiaru.

Aby pomyślnie tworzyć projekty Win32 w obciążeniu C++ dla komputerów stacjonarnych, musisz zainstalować zarówno zestaw narzędzi, jak i zestaw SDK systemu Windows. Zainstaluj zalecane (wybrane) składniki programu **VC + + 2017 najnowsze 141 zestaw narzędzi (x86, x64)** i **Windows 10 SDK (10.0. nnnnn)** , aby upewnić się, że działa. Jeśli niezbędne narzędzia nie są zainstalowane, projekty nie zostaną utworzone pomyślnie, a Kreator przestanie działać.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

Narzędzia do C++ kompilacji wizualizacji (wcześniej dostępne jako produkt autonomiczny) są teraz uwzględniane jako obciążenie w Instalator programu Visual Studio. To obciążenie powoduje zainstalowanie tylko tych narzędzi, które C++ są wymagane do kompilowania projektów bez instalowania środowiska IDE programu Visual Studio. Dostępne są zarówno zestawy narzędzi wersji 140, jak i najnowsze 141. Zestaw narzędzi najnowsze 141 zawiera najnowsze ulepszenia programu Visual Studio 2017 w wersji 15,5. Aby uzyskać więcej informacji, zobacz [Visual Studio Build Tools teraz obejmują zestawy narzędzi program VS2017 i programu VS2015 MSVC](https://devblogs.microsoft.com/cppblog/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Programowanie dla systemu Linux za pomocąC++

Popularne rozszerzenie [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) stanowi obecnie cześć programu Visual Studio. Ta instalacja zawiera wszystko, czego potrzebujesz do tworzenia i debugowania aplikacji w języku C++ działających w środowisku systemu Linux.

##### <a name="visual-studio-2017-version-152"></a>Visual Studio 2017 w wersji 15,2

Wprowadzono ulepszenia w zakresie udostępniania kodu dla wielu platform i wizualizacji typów. Aby uzyskać więcej informacji, [Zobacz C++ udoskonalenia systemu Linux dla międzyplatformowego udostępniania kodu i wizualizacji typów](https://devblogs.microsoft.com/cppblog/linux-cross-platform-and-type-visualization/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

- W obciążeniu systemu Linux dodano obsługę **rsync** jako alternatywę dla protokołu **SFTP** do synchronizowania plików na zdalnych maszynach z systemem Linux.
- Dodano obsługę dla mikrokontrolerów ARM dla kompilacji krzyżowej. Aby włączyć ją w instalacji, wybierz pozycję Programowanie dla systemu **Linux C++ przy użyciu** obciążenia i wybierz opcję **Programowanie dla urządzeń osadzonych i IoT**. Ta opcja umożliwia dodanie narzędzi do kompilacji krzyżowej ARM i dokonanie instalacji. Aby uzyskać więcej informacji, zobacz [kompilacja między różnymi platformami w programie Visual Studio](https://devblogs.microsoft.com/cppblog/arm-gcc-cross-compilation-in-visual-studio/).
- Dodano obsługę dla CMake. Teraz można korzystać z istniejącej bazy kodu CMake bez konieczności konwertowania jej na projekt programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu systemu Linux CMAKE](../linux/cmake-linux-project.md).
- Dodano obsługę uruchamiania zadań zdalnych. Ta funkcja umożliwia uruchamianie dowolnego polecenia w systemie zdalnym, który jest zdefiniowany w Menedżerze połączeń programu Visual Studio. Zadania zdalne zapewniają również możliwość kopiowania plików do systemu zdalnego.
Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu systemu Linux CMAKE](../linux/cmake-linux-project.md).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15,7

- Różne ulepszenia scenariuszy obciążeń systemu Linux. Aby uzyskać więcej informacji, [Zobacz C++ udoskonalenia obciążeń systemu Linux w systemie projektu, oknie konsoli Linux, rsync i dołączanie do procesu](https://devblogs.microsoft.com/cppblog/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).
- Funkcja IntelliSense dla nagłówków w zdalnych połączeniach systemu Linux. Aby uzyskać więcej informacji, zobacz [IntelliSense dla zdalnych nagłówków systemu Linux](https://devblogs.microsoft.com/cppblog/intellisense-for-remote-linux-headers/) i [Konfigurowanie projektu systemu Linux CMAKE](../linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Programowanie gier za pomocąC++

Pełnych możliwości języka C++ można użyć do tworzenia profesjonalnych gier obsługiwanych przy użyciu zestawu funkcji DirectX lub Cocos2d.

## <a name="mobile-development-with-c-android-and-ios"></a>Programowanie aplikacji mobilnych C++ za pomocą systemu (Android i iOS)

Program Visual Studio umożliwia obecnie programowanie i debugowanie aplikacji mobilnych przeznaczonych dla systemów Android oraz iOS.

## <a name="universal-windows-apps"></a>Aplikacje uniwersalne systemu Windows

Język C++ stanowi składnik opcjonalny obciążenia Aplikacja uniwersalna systemu Windows.  Obecnie uaktualnianie projektów C++ należy wykonywać ręcznie. Jeśli otworzysz projekt platforma uniwersalna systemu Windows przeznaczony dla wersji 140 w programie Visual Studio 2017, musisz wybrać zestaw narzędzi platformy najnowsze 141 na stronach właściwości projektu, jeśli nie masz zainstalowanego programu Visual Studio 2015.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nowe opcje dla C++ platforma uniwersalna systemu Windows (platformy UWP)

Dostępne są teraz nowe opcje zapisywania i pakowania C++ aplikacji dla platforma uniwersalna systemu Windows i sklepu Windows: można użyć infrastruktury mostka programu Desktop do spakowania istniejącej aplikacji klasycznej lub obiektu com na potrzeby wdrożenia za pomocą Sklep Windows lub za pośrednictwem istniejących kanałów za pośrednictwem ładowania bezpośredniego. Nowe funkcje w systemie Windows 10 umożliwiają dodawanie funkcji platformy UWP do aplikacji klasycznych na różne sposoby. Aby uzyskać więcej informacji, zobacz [mostek Desktop](/windows/uwp/porting/desktop-to-uwp-root).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

Zostanie dodany szablon projektu **pakietu aplikacji systemu Windows** , który znacznie upraszcza pakowanie aplikacji klasycznych za pomocą mostka programu Desktop. Jest on dostępny w **pliku | Nowy | Projekt | Zainstalowane | Wizualizacja C++ | Platforma uniwersalna systemu Windows**. Aby uzyskać więcej informacji, zobacz [pakowanie aplikacji za pomocą programu Visual Studio (mostek Desktop)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Podczas pisania nowego kodu można teraz używać C++/WinRT, które jest rzutowane C++ w standardowym języku dla środowisko wykonawcze systemu Windows zaimplementowane wyłącznie w plikach nagłówkowych. Umożliwia ona zarówno tworzenie, jak i korzystanie z środowisko wykonawcze systemu Windows interfejsów API przy użyciu dowolnego C++ kompilatora zgodnego ze standardami. C++/WinRT zaprojektowano w C++ celu udostępnienia deweloperom pierwszej klasy dostępu do nowoczesnego interfejsu API systemu Windows. Aby uzyskać więcej informacji, zobacz [ C++/WinRT: C++ Modern dla środowisko wykonawcze systemu Windows](https://moderncpp.com/).

Począwszy od kompilacji 17025 Windows SDK w wersji zapoznawczej, C++/WinRT znajduje się w Windows SDK. Aby uzyskać więcej informacji, zobacz [ C++/WinRT jest teraz dołączany do Windows SDK](https://devblogs.microsoft.com/cppblog/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="clangc2-platform-toolset"></a>Zestaw narzędzi platformy Clang/C2

Zestaw narzędzi Clang/C2 dostarczany z programem Visual Studio 2017 obsługuje teraz przełącznik **/bigobj** , który jest kluczowy dla kompilowania dużych projektów. Oferuje on również kilka ważnych poprawek, zarówno we frontonie, jak i zapleczu kompilatora.

## <a name="c-code-analysis"></a>C++Analiza kodu

Podstawowe narzędzia do sprawdzania kodu C++ wymuszające stosowanie [podstawowych wytycznych dotyczących języka C++](https://github.com/isocpp/CppCoreGuidelines) są obecnie dystrybuowane z programem Visual Studio. Po prostu Włącz kontrolki na stronie **rozszerzenia analizy kodu** na stronach właściwości projektu, a rozszerzenia zostaną uwzględnione podczas uruchamiania analizy kodu. Aby uzyskać więcej informacji, zobacz [Korzystanie C++ z funkcji sprawdzania podstawowych wytycznych](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Strona właściwości CppCoreCheck")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15,3

- Dodano obsługę reguł związanych z zarządzaniem zasobami.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

- Nowe C++ wskazówki podstawowe sprawdzają poprawność wskaźnika inteligentnego, poprawnego zastosowania inicjatorów globalnych i oflagowania użycia konstrukcji, takich jak `goto` i złe rzutowanie.

- Niektóre numery ostrzeżeń, które można znaleźć w wersji 15.3, nie są już dostępne w wersji 15.5. Ostrzeżenia te zostały zastąpione bardziej szczegółowymi operacjami sprawdzania.

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 w wersji 15,6

- Dodano obsługę analizy pojedynczych plików i ulepszenia wydajności w czasie wykonywania analizy. Aby uzyskać więcej informacji, zobacz [ C++ udoskonalenia analizy statycznej dla programu Visual Studio 2017 15,6 (wersja zapoznawcza 2)](https://devblogs.microsoft.com/cppblog/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15,7

- Dodano obsługę dla [/analyze: zestaw](../build/reference/analyze-code-analysis.md)reguł, który pozwala określić reguły analizy kodu do uruchomienia.
- Dodano obsługę dodatkowych C++ reguł podstawowych zasad.  Aby uzyskać więcej informacji, zobacz [Korzystanie C++ z funkcji sprawdzania podstawowych wytycznych](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing"></a>Testowanie jednostek

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15,5

Google test adapter i zwiększanie wydajności. Adapter testowy jest teraz dostępny jako składniki **rozwoju pulpitu z C++**  obciążeniem i są zintegrowane z **Eksploratorem testów**. Obsługa narzędzia ctest jest dodawana do projektów CMAKE (przy użyciu otwartego folderu), ale pełna integracja z **Eksploratorem testów** nie jest jeszcze dostępna. Aby uzyskać więcej informacji, zobacz [pisanie testów jednostkowych dlaC++języka C/](/visualstudio/test/writing-unit-tests-for-c-cpp).

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 w wersji 15,6

- Dodano obsługę w celu zwiększenia wydajności. Przetestuj obsługę bibliotek dynamicznych.
- Szablon elementu zwiększania wydajności. test jest teraz dostępny w środowisku IDE.

Aby uzyskać więcej informacji, zobacz temat ulepszanie [. Testowanie jednostkowe: obsługa biblioteki dynamicznej i szablon nowego elementu](https://devblogs.microsoft.com/cppblog/boost-test-unit-testing-dynamic-library-support-and-new-item-template/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15,7

Dodano obsługę [CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) dla C++ projektów testów jednostkowych. Aby uzyskać więcej informacji, zobacz temat [ogłaszanie C++ CodeLens na potrzeby testowania jednostkowego](https://devblogs.microsoft.com/cppblog/announcing-codelens-for-c-unit-testing/).

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostyka grafiki programu Visual Studio

Visual Studio Diagnostyka grafiki to zestaw narzędzi do rejestrowania i analizowania problemów z renderowaniem i wydajnością w aplikacjach Direct3D. Funkcji Diagnostyka grafiki można używać z aplikacjami, które działają lokalnie na komputerze z systemem Windows, w emulatorze urządzenia z systemem Windows lub na komputerze zdalnym lub urządzeniu.

- Dane **wejściowe & danych wyjściowych dla programów do cieniowania wierzchołków i geometrii:** Możliwość wyświetlania danych wejściowych i wyjściowych programów do cieniowania wierzchołków i programów do cieniowania geometrii była jedną z najbardziej żądanych funkcji i jest teraz obsługiwana w narzędziach. Po prostu wybierz etap programu VS lub GS w widoku etapy potoku, aby rozpocząć inspekcję danych wejściowych i wyjściowych w poniższej tabeli.

  ![Dane wejściowe/wyjściowe dla programów do cieniowania](media/io-shaders.png)

- **Wyszukiwanie i filtrowanie w tabeli obiektów:** Zapewnia szybki i łatwy sposób znajdowania szukanych zasobów.

  ![Wyszukaj](media/search.png)

- **Historia zasobów:** Ten nowy widok zapewnia ulepszony sposób wyświetlania całej historii modyfikacji zasobu, ponieważ był używany podczas renderowania przechwyconej ramki. Aby wywoływać historię dowolnego zasobu, wystarczy kliknąć ikonę zegara obok dowolnego hiperłącza zasobu.

  ![Historia zasobów](media/resource-history.png)

  Spowoduje to wyświetlenie nowego okna narzędzia **historia zasobów** wypełnionego historią zmian zasobu.

  ![Zmiana historii zasobów](media/resource-history-change.png)

  Jeśli ramka została przechwycona przy użyciu pełnego włączonego przechwytywania stosu wywołań (**narzędzia > Visual Studio > opcje** w obszarze **Diagnostyka grafiki**), kontekst każdego zdarzenia zmiany można szybko określić i sprawdzić w projekcie programu Visual Studio.

- **Statystyka interfejsu API:** Wyświetl podsumowanie wysokiego poziomu użycia interfejsu API w ramce. Jest to przydatne w przypadku odnajdywania wywołań, które mogą nie być w ogóle gotowe lub wywoływać zbyt wiele. To okno jest dostępne za pośrednictwem **widoku > statystyk interfejsu API** w programie Analizator grafiki programu Visual Studio.

  ![Statystyka interfejsu API](media/api-stats.png)

- **Statystyka pamięci:** Wyświetl ilość pamięci przydzielanej przez sterownik dla zasobów tworzonych w ramce. To okno jest dostępne za pośrednictwem **widoku > statystyk pamięci** w **Analizator grafiki programu Visual Studio**. Dane można skopiować do pliku CSV w celu wyświetlenia w arkuszu kalkulacyjnym, klikając prawym przyciskiem myszy i wybierając polecenie **Kopiuj wszystko**.

  ![Statystyka pamięci](media/memory-stats.png)

- **Sprawdzanie poprawności ramki:** Nowa lista błędów i ostrzeżeń umożliwia łatwe nawigowanie po liście zdarzeń na podstawie potencjalnych problemów wykrytych przez warstwę debugowania Direct3D. Kliknij pozycję **wyświetl > sprawdzanie poprawności ramki** w Analizator grafiki programu Visual Studio, aby otworzyć okno. Następnie kliknij pozycję **Uruchom weryfikację** , aby rozpocząć analizę. Ukończenie tej operacji może potrwać kilka minut, w zależności od złożoności ramki.

  ![Sprawdzanie poprawności ramki](media/frame-validation.png)

- **Analiza klatek dla D3D12:** Analiza klatek umożliwia analizowanie wydajności wywołań rysowania przy użyciu ukierunkowanych eksperymentów "co w przypadku". Przejdź do karty analiza klatek i Uruchom analizę, aby wyświetlić raport. Aby uzyskać więcej informacji, Obejrzyj [GoingNative 25: film wideo z programu Visual analiza klatek grafiki Studio](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) .

  ![Analiza klatek](media/frame-analysis.png)

- **Ulepszenia użycia procesora GPU:** Otwarte śledzenia można wykonać za pośrednictwem profilera użycia procesora GPU programu Visual Studio z widokiem procesora GPU lub narzędziem Windows Performance Analyzer (WPA) w celu uzyskania bardziej szczegółowej analizy. Jeśli masz zainstalowany zestaw narzędzi wydajności systemu Windows, istnieją dwa hiperłącza, jedno dla WPA i inne dla widoku GPU, w prawym dolnym rogu omówienia sesji.

  ![Użycie procesora GPU](media/gpu-usage.png)

  Ślady otwierane w widoku GPU za pośrednictwem tego łącza obsługują zsynchronizowane powiększanie i panoramowanie na osi czasu między widokiem a i procesorem GPU. Pole wyboru w programie VS służy do kontrolowania, czy synchronizacja jest włączona, czy nie.

  ![Widok procesora GPU](media/gpu-view.png)

::: moniker-end

::: moniker range="=vs-2015"

Aby zapoznać się z pełną listą nowości w programie Visual Studio 2015 Update 3, zobacz artykuł [ C++ co to jest nowość 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015). Aby uzyskać więcej informacji na temat nowości we wszystkich wersjach programu Visual Studio 2015, zobacz informacje o wersji połączone z [historią informacji o wersji programu Visual studio 2015](/visualstudio/releasenotes/vs2015-version-history). Aby uzyskać informacje na temat Nowości C++ w programie visual Studio 2019, zobacz [co nowego w C++ programie Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Aby uzyskać informacje na temat Nowości C++ w programie visual Studio 2017, zobacz [co nowego C++ w programie Visual Studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017).

::: moniker-end
