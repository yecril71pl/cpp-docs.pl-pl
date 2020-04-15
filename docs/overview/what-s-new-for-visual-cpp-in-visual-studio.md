---
title: Co nowego w języku C++ w programie Visual Studio
ms.date: 07/02/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
ms.openlocfilehash: 9b656d4e13fe241c22a9c555d1c597016c5353d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366817"
---
# <a name="whats-new-for-c-in-visual-studio"></a>Co nowego w języku C++ w programie Visual Studio

::: moniker range=">=vs-2019"

Visual Studio 2019 przynosi wiele aktualizacji i poprawek do środowiska Microsoft C++. Naprawiliśmy wiele błędów i problemów w kompilatorze i narzędziach. Wiele z tych problemów zostało przesłanych przez klientów za pośrednictwem [opcji Zgłoś problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019) i [Podaj sugestię](https://developercommunity.visualstudio.com/spaces/62/index.html) w obszarze **Wyślij opinię**. Dziękujemy za zgłaszanie usterek! Aby uzyskać więcej informacji na temat nowości w programie Visual Studio, odwiedź stronę [Co nowego w programie Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019). Aby uzyskać informacje na temat nowości w języku C++ w programie Visual Studio 2017, zobacz [Co nowego w języku C++ w programie Visual Studio 2017.](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017) Aby uzyskać informacje na temat nowości w języku C++ w programie Visual Studio 2015 i wcześniejszych wersjach, zobacz [Visual C++ What's New 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>kompilator C++

- Ulepszona obsługa funkcji języka C++ 17 i poprawek poprawności, a także eksperymentalna obsługa funkcji języka C++20, takich jak moduły i coroutines. Aby uzyskać szczegółowe informacje, zobacz [Ulepszenia zgodności języka C++ w programie Visual Studio 2019](cpp-conformance-improvements.md).

- Opcja `/std:c++latest` zawiera teraz funkcje C++20, które niekoniecznie są kompletne, w tym \<początkowe wsparcie dla operatora C++20 => ("statek kosmiczny") dla porównania trójdrożnego.

- Przełącznik `/Gm` kompilatora języka C++ jest teraz przestarzały. Należy rozważyć wyłączenie `/Gm` przełącznika w skryptach kompilacji, jeśli jest jawnie zdefiniowany. Można jednak bezpiecznie zignorować ostrzeżenie o `/Gm`cofnięciu dla programu , ponieważ nie jest ono traktowane jako`/WX`błąd podczas używania funkcji "Traktuj ostrzeżenia jako błędy" ( ).

- Jak MSVC rozpoczyna implementowanie funkcji ze standardowego projektu `/std:c++latest` C `/std:c++latest` ++ 20 pod flagą, jest teraz niezgodne z `/clr` (wszystkie smaki), `/ZW`i `/Gm`. W programie Visual Studio `/std:c++17` 2019 użyj lub `/clr` `/ZW` `/Gm` `/std:c++14` tryby podczas kompilowania z , lub (ale zobacz poprzedni punktor).

- Prekompilowane nagłówki nie są już generowane domyślnie dla konsoli C++ i aplikacji klasycznych.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, zabezpieczenia, diagnostyka i przechowywanie wersji

Ulepszona `/Qspectre` analiza w celu zapewnienia pomocy w łagodzeniu widmo wariant 1 (CVE-2017-5753). Aby uzyskać więcej informacji, zobacz [Spectre Mitigations w MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>Ulepszenia biblioteki standardowej języka C++

- Implementacja dodatkowych funkcji biblioteki C++ 17 i C++20 i poprawek. Aby uzyskać szczegółowe informacje, zobacz [Ulepszenia zgodności języka C++ w programie Visual Studio 2019](cpp-conformance-improvements.md).

- Clang-Format został zastosowany do standardowych nagłówków biblioteki C++ w celu zwiększenia czytelności.

- Ponieważ visual studio obsługuje teraz tylko mój kod dla języka C++, `std::function` `std::visit` standardowa biblioteka nie musi już zapewniać niestandardowe maszyny dla i osiągnąć ten sam efekt. Usunięcie tej maszyny w dużej mierze nie ma widocznych dla użytkownika efektów. Wyjątkiem jest to, że kompilator nie będzie już produkować diagnostyki, które wskazują problemy w wierszu 15732480 lub 16707566 \<type_traits> lub \<> wariantu.

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>Ulepszenia wydajności/przepływności w kompilatorze i bibliotece standardowej

- Twórz ulepszenia przepływności, w tym sposób, w jaki konsolidator obsługuje we/wy pliku, oraz czas łącza w programie PDB, łącząc i tworząc.

- Dodano podstawowe wsparcie dla wektoryzacji OpenMP SIMD. Można go włączyć za pomocą `-openmp:experimental`nowego przełącznika kompilatora . Ta opcja umożliwia pętle `#pragma omp simd` z adnotacjami, które mogą być wektoryzowane. Wektoryzacja nie jest gwarantowana, a pętle z adnotacjami, ale nie wektoryzowane otrzymają ostrzeżenie. Nie są obsługiwane żadne klauzule SIMD; są ignorowane, a ostrzeżenie jest zgłaszane.

- Dodano nowy inlining przełącznik `-Ob3`wiersza polecenia , który `-Ob2`jest bardziej agresywną wersją . `-O2`(optymalizacja binarna pod kątem `-Ob2` szybkości) nadal oznacza domyślnie. Jeśli okaże się, że kompilator nie jest wystarczająco `-O2 -Ob3`agresywny, rozważ przekazanie .

- Aby obsługiwać ręczną wektoryzację pętli za pomocą wywołań funkcji biblioteki matematycznej i niektórych innych operacji, takich jak podział liczby całkowitej, dodaliśmy obsługę wewnętrznych funkcji biblioteki matematycznej krótkich wektorów (SVML). Te funkcje obliczają 128-bitowe, 256-bitowe lub 512-bitowe odpowiedniki wektorowe. Aby uzyskać definicje obsługiwanych funkcji, zobacz [Intel Intrinsic Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML) (Przewodnik wewnętrzny firmy Intel).

- Nowe i ulepszone optymalizacje:

  - Stałe składanie i uproszczenia arytmetyczne dla wyrażeń przy użyciu wewnętrznego wektora SIMD, zarówno dla form float, jak i całkowitych.

  - Bardziej zaawansowana analiza wyodrębniania informacji z przepływu sterowania (if/else/switch instrukcji), aby usunąć gałęzie zawsze okazały się prawdziwe lub fałszywe.

  - Ulepszono rozkręcanie memsetów w celu użycia instrukcji wektorowych SSE2.

  - Ulepszone usuwanie bezużytecznych kopii struktury/klasy, szczególnie w przypadku programów W++, które przechodzą przez wartość.

  - Ulepszona optymalizacja `memmove`kodu `std::copy` przy `std::vector` `std::string` użyciu , takich jak lub i konstrukcji.

- Zoptymalizowano standardową konstrukcję fizyczną biblioteki, aby uniknąć kompilowania części standardowej biblioteki, które nie są bezpośrednio dołączone. Ta zmiana skróciła czas kompilacji pustego pliku, który zawiera tylko \<wektorowe> na pół. W związku z tym może `#include` być konieczne dodanie dyrektyw dla nagłówków, które wcześniej pośrednio zostały uwzględnione. Na przykład kod, `std::out_of_range` który używa może `#include <stdexcept>`teraz trzeba dodać . Kod, który używa operatora wstawiania `#include <ostream>`strumienia może teraz trzeba dodać . Zaletą jest to, że \<tylko jednostki tłumaczeniowe \<faktycznie używające stdexcept> lub ostream> składniki płacą koszt przepływności w celu ich skompilowania.

- `if constexpr`został zastosowany w większej liczbie miejsc w standardowej bibliotece dla lepszej przepływności i zmniejszenia rozmiaru kodu w operacjach kopiowania, w permutacjach, takich jak odwrotnie i obracaj, oraz w bibliotece algorytmów równoległych.

- Standardowa biblioteka jest `if constexpr` teraz używana wewnętrznie w celu skrócenia czasu kompilacji, nawet w trybie C++14.

- Wykrywanie dynamicznego łącza środowiska wykonawczego dla biblioteki algorytmów równoległych nie używa już całej strony do przechowywania tablicy wskaźnika funkcji. Oznaczanie tej pamięci tylko do odczytu uznano za niezamiane ze względów bezpieczeństwa.

- `std::thread`'s konstruktor nie czeka na uruchomienie wątku i nie wstawia już tak `_beginthreadex` wielu warstw wywołań funkcji między podstawową biblioteką C a dostarczonym obiektem wywoływanym. Wcześniej `std::thread` umieścić 6 `_beginthreadex` funkcji między i dostarczonym obiektem callable, który został zredukowany `std::invoke`do zaledwie 3 (z których 2 są sprawiedliwe). Ta zmiana rozwiązuje również niejasny błąd `std::thread` chronometrażu, w którym konstruktor `std::thread` zawiesiłby się, jeśli zegar systemowy zmienił się dokładnie w momencie utworzenia.

- Naprawiono regresję `std::hash` wydajności, którą `std::hash<std::filesystem::path>`wprowadziliśmy podczas wdrażania .

- Standardowa biblioteka używa teraz destruktorów zamiast bloków catch w kilku miejscach, aby osiągnąć poprawność. Ta zmiana powoduje lepszą interakcję debugera: wyjątki, które zgłaszasz za pośrednictwem standardowej biblioteki w lokalizacjach, których dotyczy problem, są teraz wyświetlane jako wyrzucane z ich oryginalnej witryny rzutowania, a nie z naszego rethrow. Nie wszystkie standardowe bloki zaczepowe biblioteki zostały wyeliminowane; oczekujemy, że liczba bloków catch zostanie zmniejszona w późniejszych wersjach MSVC.

- Suboptimal codegen `std::bitset` w spowodowane przez rzut warunkowy wewnątrz funkcji noexcept został ustalony przez faktoringu się ścieżki rzucania.

- I `std::list` `std::unordered_*` rodziny używać iteratorów bez debugowania wewnętrznie w większej liczbie miejsc.

- Kilka `std::list` elementów członkowskich zostały zmienione, aby ponownie użyć węzłów listy, gdzie to możliwe, a nie rozdzielanie i ponowne przydzielanie ich. Na przykład, `list<int>` biorąc pod uwagę, że ma już `assign(4, 1729)` rozmiar 3, wywołanie teraz zastępuje ints w pierwszych 3 węzłów listy i przydziela jeden nowy węzeł listy o wartości 1729.

- Wszystkie standardowe wywołania biblioteki `erase(begin(), end())` zostały zmienione na `clear()`.

- `std::vector`teraz inicjuje i usuwa elementy bardziej efektywnie w niektórych przypadkach.

- Ulepszenia, `std::variant` aby uczynić go bardziej optymalizatorem, co powoduje lepsze wygenerowanie kodu. Inlining kodu jest teraz `std::visit`znacznie lepiej z .

## <a name="c-ide"></a>Środowisko IDE języka C++

### <a name="live-share-c-support"></a>Pomoc techniczna aplikacji Live Share C++

[Udostępnianie na żywo](/visualstudio/liveshare/) obsługuje teraz język C++, umożliwiając deweloperom korzystającym z programu Visual Studio lub Visual Studio Code współpracę w czasie rzeczywistym. Aby uzyskać więcej informacji, zobacz [Ogłaszanie udostępniania na żywo dla języka C++: Udostępnianie i współpraca w czasie rzeczywistym](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>IntelliCode dla języka C++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16.1

IntelliCode to opcjonalne rozszerzenie, które używa własnego obszernego szkolenia i kontekstu kodu, aby umieścić to, czego najprawdopodobniej użyjesz u góry listy ukończenia. Często można wyeliminować konieczność przewijania w dół listy. W przypadku języka C++ intellicode oferuje największą pomoc podczas korzystania z popularnych bibliotek, takich jak biblioteka standardowa. Jest on dostępny jako składnik obciążenia w instalatorze. Aby uzyskać więcej informacji, zobacz [Sugestie ukończenia kodu wspomagane przez AI Przyjdź do języka C++ za pośrednictwem intellicode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

### <a name="template-intellisense"></a>Szablon IntelliSense

Pasek **szablonów** używa teraz interfejsu użytkownika **okna wglądu** zamiast okna modalnego, obsługuje szablony zagnieżdżone i wstępnie wypełnia wszystkie domyślne argumenty w **oknie wglądu**. Aby uzyskać więcej informacji, zobacz [Szablon Ulepszenia IntelliSense dla programu Visual Studio 2019 Wersja zapoznawcza 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/). A **Ostatnio używane** listy rozwijanej na **pasku szablonów** umożliwia szybkie przełączanie między poprzednimi zestawami przykładowych argumentów.

### <a name="new-start-window-experience"></a>Nowe środowisko okna Start

Podczas uruchamiania IDE pojawia się nowe okno Start z opcjami otwierania najnowszych projektów, klonowania kodu z kontroli źródła, otwierania kodu lokalnego jako rozwiązania lub folderu lub tworzenia nowego projektu. Okno dialogowe Nowy projekt zostało również przebudowane na środowisko, które można filtrować.

### <a name="new-names-for-some-project-templates"></a>Nowe nazwy niektórych szablonów projektów

Zmodyfikowaliśmy kilka nazw szablonów projektu i opisów, aby dopasować je do zaktualizowanego okna dialogowego Nowy projekt.

### <a name="various-productivity-improvements"></a>Różne ulepszenia wydajności

Visual Studio 2019 zawiera następujące funkcje, które ułatwią kodowanie i będą bardziej intuicyjne:

- Szybkie poprawki dla:
  - Dodaj brakujące #include
  - Wartość NULL do nullptr
  - Dodawanie brakującego średnika
  - Rozwiązywanie problemów z brakującym obszarem nazw lub zakresem
  - Wymień złe operandy pośrednie (do\* & \*i & do)
- Szybkie informacje o bloku, najeżdżając kursorem na nawias zamykający
- Zajrzeć do nagłówka / pliku kodu
- Przejdź do definicji na #include otwiera plik

Aby uzyskać więcej informacji, zobacz [Ulepszenia produktywności w programie Visual Studio 2019 w wersji zapoznawczej 2.](https://devblogs.microsoft.com/cppblog/c-productivity-improvements-in-visual-studio-2019-preview-2/)

### <a name="quickinfo-improvements"></a>Ulepszenia QuickInfo

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16.1

Skrócona etykietka narzędzia uwzględnia teraz kolorystykę semantyczną edytora. Posiada również nowy link **Search Online,** który będzie szukać dokumentów online, aby dowiedzieć się więcej o konstrukcji kodu aktywowanego. W przypadku czerwonego kodu, link dostarczony przez Szybkie informacje wyszuka błąd online. W ten sposób nie trzeba ponownie wpisywać wiadomości do przeglądarki. Aby uzyskać więcej informacji, zobacz [Szybkie ulepszenia w programie Visual Studio 2019: Kolorowanie i wyszukiwanie w trybie online](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/).

### <a name="intellicode-available-in-c-workload"></a>IntelliCode dostępne w środowisku C++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16.1

IntelliCode jest teraz dostarczany jako opcjonalny składnik w programie Rozwoju pulpitu z obciążeniem **języka C++.** Aby uzyskać więcej informacji, zobacz [Ulepszone C++ IntelliCode teraz dostarczane z Visual Studio 2019](https://devblogs.microsoft.com/cppblog/improved-c-intellicode-now-ships-with-visual-studio-2019/).

## <a name="cmake-support"></a>Pomoc techniczna firmy CMake

- Obsługa CMake 3.14

- Visual Studio można teraz otworzyć istniejące cMake pamięci podręcznych generowanych przez narzędzia zewnętrzne, takie jak CMakeGUI, dostosowane systemy meta-build lub tworzyć skrypty, które wywołują cmake.exe siebie.

- Poprawiono wydajność IntelliSense.

- Nowy edytor ustawień stanowi alternatywę dla ręcznej edycji pliku CMakeSettings.json i zapewnia pewne parzystości z CMakeGUI.

- Program Visual Studio ułatwia rozpoczęcie programowania w języku C++ za pomocą narzędzia CMake w systemie Linux, wykrywając, czy na komputerze z systemem Linux znajduje się zgodna wersja narzędzia CMake. W przeciwnym razie umożliwia jej zainstalowanie dla Ciebie.

- Niezgodne ustawienia w CMakeSettings, takie jak niedopasowane architektury lub niezgodne ustawienia generatora CMake, pokazują squiggles w edytorze JSON i błędy na liście błędów.

- W projektach CMake otwieranych w środowisku IDE po uruchomieniu polecenia `vcpkg integrate install` automatycznie jest wykrywany i włączany łańcuch narzędzi vcpkg. To zachowanie można wyłączyć, określając pusty plik łańcucha narzędzi w pliku CMakeSettings.

- W projektach CMake domyślnie jest teraz włączane debugowanie Tylko mój kod.

- Ostrzeżenia analizy statycznej można teraz przetwarzać w tle i wyświetlać w edytorze projektów CMake.

- Jaśniejsze kompilacji i konfigurowania "begin" i "end" wiadomości dla projektów CMake i obsługi interfejsu użytkownika postępu kompilacji programu Visual Studio. Ponadto istnieje teraz CMake ustawienie szczegółowości w **Narzędzia > Opcje,** aby dostosować poziom szczegółowości CMake kompilacji i komunikatów konfiguracyjnych w oknie wyjścia.

- Ustawienie `cmakeToolchain` jest teraz obsługiwane w CMakeSettings.json, aby określić schematy narzędzi bez ręcznego modyfikowania wiersza polecenia CMake.

- Nowy skrót menu **Zbuduj wszystko** **Ctrl+Shift+B**.

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16.1

- Zintegrowana obsługa edycji, tworzenia i debugowania projektów CMake z Clang/LLVM. Aby uzyskać więcej informacji, zobacz [Pomoc techniczna clang/LLVM w programie Visual Studio](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/).

## <a name="linux-and-the-windows-subsystem-for-linux"></a>Linux i podsystem Windows dla Linuksa

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16.1

- Obsługa [addresssanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) w linuksie i CMake projektów międzyplatformowych. Aby uzyskać więcej informacji, zobacz [AddressSanitizer (ASan) dla obciążenia systemu Linux w programie Visual Studio 2019](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/).

- Zintegrowana obsługa programu Visual Studio do korzystania z języka C++ z podsystemem windows dla systemu Linux (WSL). Aby uzyskać więcej informacji, zobacz [C++ z programem Visual Studio 2019 i Podsystem windows dla systemu Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

## <a name="incredibuild-integration"></a>Integracja IncrediBuild

IncrediBuild jest dołączony jako opcjonalny składnik w rozwoju pulpitu z obciążeniem **C++.** Monitor kompilacji IncrediBuild jest w pełni zintegrowany z ideą programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Wizualizacja kompilacji za pomocą Monitora kompilacji IncrediBuild i programu Visual Studio 2019.](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/)

## <a name="debugging"></a>Debugowanie

- W przypadku aplikacji języka C++ uruchomionych w systemie Windows pliki PDB są teraz ładowane w osobnym procesie 64-bitowym. Ta zmiana dotyczy szeregu awarii spowodowanych przez debugera wyczerpania pamięci podczas debugowania aplikacji, które zawierają dużą liczbę modułów i plików PDB.

- Wyszukiwanie jest włączone w oknach **Czujka,** **Autos**i **Locals.**

## <a name="windows-desktop-development-with-c"></a>Tworzenie pulpitu dla systemu Windows w języku C++

- Te kreatory C++ ATL/MFC nie są już dostępne:

  - Kreator składników ATL COM+ 1.0
  - Kreator składników aktywnych stron serwera ATL
  - Kreator dostawcy interfejsu OLE DB ATL
  - Kreator strony właściwości ATL
  - Kreator konsumenta OLE DB ATL
  - MFC ODBC Konsument
  - Klasa MFC z formantu ActiveX
  - Klasa MFC z typu Lib.

  Przykładowy kod dla tych technologii został zarchiwizowany w witrynie Microsoft Docs i w repozytorium GitHub VCSamples.

- Zestaw Windows 8.1 SDK nie jest już dostępny w instalatorze programu Visual Studio. Zalecamy uaktualnienie projektów języka C++ do najnowszego systemu Windows 10 SDK. Jeśli masz stałą zależność od systemu w wersji 8.1, możesz pobrać go z archiwum zestawu Windows SDK.

- Obsługa systemu Windows XP nie będzie już dostępna w najnowszym zestawie narzędzi języka C++. Kierowanie na xp z kompilatorem MSVC na poziomie VS 2017 & bibliotek jest nadal obsługiwane i można je zainstalować za pomocą "Poszczególnych składników".

- Nasza dokumentacja aktywnie zniechęca do użycia modułów scalania w przypadku wdrożenia środowiska uruchomieniowego Visual C++. Podejmujemy dodatkowy krok w tej wersji oznaczania naszych MSM jako przestarzałych. Rozważ migrację wdrożenia centralnego VCRuntime z plików MSM do pakietu redystrybucyjnego.

## <a name="mobile-development-with-c-android-and-ios"></a>Rozwój urządzeń mobilnych w języku C++ (Android i iOS)

Środowiskiem systemu Android dla języka C++ jest teraz domyślnie zestaw SDK 25 dla systemu Android i zestaw NDK 16b dla systemu Android.

## <a name="clangc2-platform-toolset"></a>Zestaw narzędzi platformy Clang/C2

Komponent eksperymentalny Clang/C2 został usunięty. Użyj zestawu narzędzi MSVC, aby uzyskać pełną `/permissive-` `/std:c++17`zgodność standardów języka C++ z i , lub z pasem narzędzi Clang/LLVM dla systemu Windows.

## <a name="code-analysis"></a>Analiza kodu

- Analiza kodu działa teraz automatycznie w tle. Ostrzeżenia są wyświetlane podczas pisania jako zielone podkreślenia w edytorze. Aby uzyskać więcej informacji, zobacz [Analiza kodu edytora w programie Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/).

- Nowe reguły eksperymentalnej kontroli współbieżności dla znanych \<typów bibliotek standardowych z nagłówka> mutex. Aby uzyskać więcej informacji, zobacz [Analiza kodu współbieżności w programie Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/).

- Zaktualizowana częściowa implementacja [narzędzia sprawdzania profilu okresu istnienia,](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/)który wykrywa zwisające wskaźniki i odwołania. Aby uzyskać więcej informacji, zobacz [Dożywotnia aktualizacja profilu w programie Visual Studio 2019 w wersji zapoznawczej 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/).

- Więcej kontroli związanych z coroutine, w tym C26138, C26810, C26811 i reguły eksperymentalnej C26800. Aby uzyskać więcej informacji, zobacz [Nowe kontrole analizy kodu w programie Visual Studio 2019: use-after-move i coroutine](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/).

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 w wersji 16.1

- Nowe szybkie poprawki dla niezainicjowanych kontroli zmiennych. Aby uzyskać więcej informacji, zobacz [Nowe szybkie poprawki analizy kodu dla pamięci niezainicjowanej (C6001) i użycie przed init (C26494) ostrzeżenia](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/).

## <a name="unit-testing"></a>Testowanie jednostek

Szablon zarządzanego projektu testowego w języku C++ nie jest już dostępny. Można kontynuować przy użyciu zarządzanej struktury testu języka C++ w istniejących projektach. W przypadku nowych testów jednostkowych należy rozważyć użycie jednej z natywnych struktur testowych, dla których program Visual Studio udostępnia szablony (MSTest, Test Google) lub szablon projektu testu zarządzanego języka C#.

::: moniker-end

::: moniker range="=vs-2017"

Visual Studio 2017 przynosi wiele aktualizacji i poprawek do środowiska C++. Naprawiliśmy ponad 250 błędów i zgłosiliśmy problemy w kompilatorze i narzędziach, wiele przesłanych przez klientów za pośrednictwem [opcji Zgłoś problem i Podaj opcję sugestii](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2017) w obszarze **Wyślij opinię**. Dziękujemy za zgłaszanie usterek! Aby uzyskać więcej informacji na temat nowości w programie Visual Studio, zobacz [Co nowego w programie Visual Studio 2017.](/visualstudio/ide/whats-new-visual-studio-2017?view=vs-2017) Aby uzyskać informacje o nowościach w języku C++ w programie Visual Studio 2019, zobacz [Co nowego w języku C++ w programie Visual Studio.](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019) Aby uzyskać informacje na temat nowości w języku C++ w programie Visual Studio 2015 i wcześniejszych wersjach, zobacz [Visual C++ What's New 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>kompilator C++

### <a name="c-conformance-improvements"></a>Ulepszenia zgodności języka C++

W tej wersji zaktualizowaliśmy standardową bibliotekę i kompilator języka C++ o rozszerzoną obsługę funkcji języka C ++ 11 i C ++ 14, a także wstępną obsługę niektórych funkcji, które mają zostać uwzględnione w standardowym języku C ++ 17. Aby uzyskać szczegółowe informacje, zobacz [Ulepszenia zgodności języka C++ w programie Visual Studio 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

Kompilator obsługuje około 75% funkcji, które są nowe w języku C++ `constexpr` 17, w tym powiązania strukturalne, lambdas, `if constexpr`, zmienne wbudowane, wyrażenia składania i dodanie `noexcept` do systemu typów. Funkcje te są dostępne w opcji **/std:c++17.** Aby uzyskać więcej informacji, zobacz [Ulepszenia zgodności języka C++ w programie Visual Studio 2017](cpp-conformance-improvements.md)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

Zestaw narzędzi kompilatora MSVC w programie Visual Studio w wersji 15.7 jest teraz zgodny ze standardem C++. Aby uzyskać więcej informacji, zobacz [Ogłaszanie: MSVC jest zgodny ze standardem C++](https://devblogs.microsoft.com/cppblog/announcing-msvc-conforms-to-the-c-standard/) i [zgodnością języka Microsoft C++.](../visual-cpp-language-conformance.md)

##### <a name="visual-studio-2017-version-158"></a>Visual Studio 2017 w wersji 15.8

Przełącznik kompilatora [/experimental:preprocesor](../build/reference/experimental-preprocessor.md) umożliwia nowy eksperymentalny preprocesor MSVC, który ostatecznie będzie zgodny ze wszystkimi obowiązującymi normami C i C++. Aby uzyskać więcej informacji, zobacz [omówienie eksperymentalnego preprocesora MSVC](../preprocessor/preprocessor-experimental-overview.md).

### <a name="new-compiler-options"></a>Nowe opcje kompilatora

- [/permissive-](../build/reference/permissive-standards-conformance.md): Włącz wszystkie opcje kompilatora zgodności ścisłych standardów i `__declspec(dllimport)`wyłącz większość rozszerzeń kompilatora specyficznych dla firmy Microsoft (ale nie , na przykład). Ta opcja jest domyślnie włączona w programie Visual Studio 2017 w wersji 15.5.  **Tryb /permissive-** konności zawiera obsługę dwufazowego wyszukiwania nazw. Aby uzyskać więcej informacji, zobacz [Ulepszenia zgodności języka C++ w programie Visual Studio](cpp-conformance-improvements.md).

- [/diagnostics](../build/reference/diagnostics-compiler-diagnostic-options.md): Włącz wyświetlanie numeru wiersza, numeru wiersza i kolumny lub numeru wiersza i kolumny oraz cieczy pod wierszem kodu, w którym znaleziono błąd diagnostyczny lub ostrzeżenie.

- [/debug:fastlink:](../build/reference/debug-generate-debug-info.md)Włącz do 30% szybsze czasy połączeń przyrostowych (w porównaniu z programem Visual Studio 2015), nie kopiując wszystkich informacji debugowania do pliku PDB. Zamiast tego plik PDB wskazuje informacje debugowania dla plików obiektu i biblioteki użytych do utworzenia pliku wykonywalnego. Zobacz [szybszy cykl kompilacji C++ w programie VS "15" z /Debug:fastlink](https://devblogs.microsoft.com/cppblog/faster-c-build-cycle-in-vs-15-with-debugfastlink/) i [zaleceniami, aby przyspieszyć kompilacje języka C++ w programie Visual Studio.](https://devblogs.microsoft.com/cppblog/recommendations-to-speed-c-builds-in-visual-studio/)

- Visual Studio 2017 umożliwia korzystanie [z /sdl](../build/reference/sdl-enable-additional-security-checks.md) z [/await](../build/reference/await-enable-coroutine-support.md). Usunęliśmy ograniczenie [/RTC](../build/reference/rtc-run-time-error-checks.md) z Coroutines.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- [/std:c++14 i /std:c++latest](../build/reference/std-specify-language-standard-version.md): Te opcje kompilatora umożliwiają wybranie określonych wersji języka programowania ISO C++ w projekcie. Większość nowych standardowych funkcji projektu jest chroniona przez opcję **/std:c++latest.**

- [/std:c++17](../build/reference/std-specify-language-standard-version.md) umożliwia zestaw funkcji C++17 zaimplementowanych przez kompilator. Ta opcja wyłącza obsługę kompilatora i biblioteki standardowej dla funkcji, które zostały zmienione lub nowe w wersjach roboczego wersji roboczej i aktualizacji wad standardu C++ po C++17. Aby włączyć te funkcje, użyj **/std:c++latest**.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, zabezpieczenia, diagnostyka i przechowywanie wersji

Ta wersja zawiera kilka ulepszeń w optymalizacji, generowania kodu, wersji zestawu narzędzi i diagnostyki. Do istotnych ulepszeń należą:

- Ulepszone generowanie kodu pętli: obsługa automatycznej wektoryzacji dzielenia stałych liczb całkowitych, lepsza identyfikacja wzorców funkcji memset.
- Ulepszone zabezpieczenia kodu: Ulepszona emisja diagnostyki kompilatora przepełnienia buforu i [/guard:cf](../build/reference/guard-enable-control-flow-guard.md) teraz chroni instrukcje przełączania, które generują tabele przesuwu.
- Przechowywanie wersji: Wartość wbudowanego makra ** \_\_** preprocesora MSC VER jest teraz jednotonicznie aktualizowana przy każdej aktualizacji zestawu narzędzi Visual C++. Aby uzyskać więcej informacji, zobacz [Visual C++ Compiler Version](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/).
- Nowy układ zestawu narzędzi: kompilator i powiązane narzędzia kompilacji mają nową strukturę lokalizacji i katalogów na komputerze deweloperskim. Nowy układ umożliwia instalacje side-by-side wielu wersji kompilatora. Aby uzyskać więcej informacji, zobacz [Układ narzędzi kompilatora w programie Visual Studio 2017](https://devblogs.microsoft.com/cppblog/compiler-tools-layout-in-visual-studio-15/).
- Ulepszona diagnostyka: Okno danych wyjściowych pokazuje teraz kolumnę, w której występuje błąd. Aby uzyskać więcej informacji, zobacz [ulepszenia diagnostyki kompilatora języka C++ w programie VS "15" Preview 5](https://devblogs.microsoft.com/cppblog/c-compiler-diagnostics-improvements-in-vs-15-rc/).
- W przypadku korzystania z procedur współrutynowych eksperymentalne słowo kluczowe **yield** (dostępne w opcji **/await)** zostało usunięte. Kod powinien zostać zaktualizowany do użycia. `co_yield` Aby uzyskać więcej informacji, zobacz [ `yield` słowo kluczowe, które ma zostać `co_yield` w programie VS 2017](https://devblogs.microsoft.com/cppblog/yield-keyword-to-become-co_yield-in-vs-2017/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

Dodatkowe ulepszenia diagnostyki w kompilatorze. Aby uzyskać więcej informacji, zobacz [Ulepszenia diagnostyczne w programie Visual Studio 2017 15.3.0](https://devblogs.microsoft.com/cppblog/diagnostic-improvements-in-vs2017-15-3-0/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

Wydajność środowiska wykonawczego języka Visual C++ nadal się poprawia ze względu na lepszą jakość kodu generowanego. Teraz możesz po prostu ponownie skompilować kod, a aplikacja działa szybciej. Niektóre optymalizacje kompilatora są zupełnie nowe, takie jak wektoryzacja magazynów `sin(x)` skalarnych warunkowych, łączenie wywołań i `cos(x)` do nowego `sincos(x)`i eliminacja zbędnych instrukcji z optymalizatora SSA. Inne optymalizacje kompilatora są ulepszenia istniejących funkcji, takich jak heurystyki wektorystycy dla wyrażeń warunkowych, lepsze optymalizacje pętli i float min/max codegen. Konsolidator ma nową i szybszą implementację **/OPT:ICF,** co może spowodować przyspieszenie do 9% czasu łącza i istnieją inne poprawki perf w łączeniu przyrostowym. Aby uzyskać więcej informacji, zobacz [/OPT (Optymalizacje)](../build/reference/opt-optimizations.md) i [/INCREMENTAL (Łącze przyrostowo)](../build/reference/incremental-link-incrementally.md).

Kompilator Microsoft C++ obsługuje avx-512 firmy Intel, w tym instrukcje Vector Length, które wprowadzają nowe funkcje w avx-512 do 128-bitowych i 256-bitowych rejestrów.

[/Zc:noexceptTypes-](../build/reference/zc-noexcepttypes.md) opcja może służyć do powrotu do wersji C ++ 14 podczas korzystania z `noexcept` trybu C ++ 17 w ogóle. Ta opcja umożliwia aktualizację kodu źródłowego, aby były zgodne z C++17 bez konieczności ponownego zapisu całego `throw()` kodu w tym samym czasie. Aby uzyskać więcej informacji, zobacz [Usuwanie specyfikacji wyjątków dynamicznych i nieobliczaj](cpp-conformance-improvements.md#noexcept_removal).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Nowy przełącznik kompilatora [/Qspectre,](../build/reference/qspectre.md) aby pomóc w łagodzeniu ataków kanału po stronie spekulacyjnego wykonywania. Aby uzyskać więcej informacji, zobacz [Środki zaradcze widmo w MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).
- Nowe ostrzeżenie diagnostyczne dotyczące łagodzenia spectre. Aby uzyskać więcej informacji, zobacz [Diagnostyka widmo w programie Visual Studio 2017 wersja 15.7 Wersja zapoznawcza 4](https://devblogs.microsoft.com/cppblog/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/).
- Nowa wartość dla /Zc, **/Zc:__cplusplus**umożliwia poprawne raportowanie standardowej obsługi języka C++. Na przykład, gdy przełącznik jest ustawiony, a kompilator jest w trybie /std:c++17, wartość rozszerza się do **201703L**. Aby uzyskać więcej informacji, zobacz [MSVC teraz poprawnie raporty __cplusplus](https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/).

## <a name="c-standard-library"></a>Standardowa biblioteka języka C++

### <a name="correctness-improvements"></a>Ulepszenia poprawności

##### <a name="visual-studio-2017-rtm-version-150"></a>Visual Studio 2017 RTM (wersja 15.0)

- Drobne `basic_string` `_ITERATOR_DEBUG_LEVEL != 0` ulepszenia diagnostyczne. Wyzwolenie kontroli IDL w maszynie ciągu zgłasza teraz określone zachowanie, które spowodowało wyzwolenie. Na przykład zamiast komunikatu „iterator ciągu nie umożliwia wyłuskiwania” otrzymasz komunikat „nie można wyłuskać iteratora ciągu, ponieważ jest on poza zakresem (np. iterator końca)”.
- Naprawiono `std::promise` operator przypisania przenoszenia, który wcześniej mógł spowodować zablokowanie kodu na zawsze.
- Naprawiono błędy kompilatora z konwersją niejawną `atomic<T*>` na `T*`.
- `pointer_traits<Ptr>`teraz poprawnie `Ptr::rebind<U>`wykrywa .
- Naprawiono `const` brak kwalifikatora w operatorze `move_iterator` odejmowania.
- Naprawiono cichy zły kodgen dla stanowych alokatorów zdefiniowanych przez użytkownika, żądających `propagate_on_container_copy_assignment` i `propagate_on_container_move_assignment`.
- `atomic<T>`toleruje przeciążone `operator&()`.
- Nieznacznie ulepszona diagnostyka `bind()` kompilatora dla niepoprawnych wywołań.

Aby uzyskać pełną listę ulepszeń biblioteki standardowej w programie Visual Studio 2017 RTM, zobacz wpis standardowej biblioteki standardu standardowy w programie C++ Team Blog [w programie VS 2017 RTM](https://devblogs.microsoft.com/cppblog/stl-fixes-in-vs-2017-rtm/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- Standardowe pojemniki biblioteczne teraz zaciskają się `max_size()` do, a nie `numeric_limits<difference_type>::max()` `max()` do . `size_type` Ta zmiana gwarantuje, że `distance()` wynik na iteratorów z tego kontenera `distance()`jest reprezentowany w typie zwracanym .
- Naprawiono brak `auto_ptr<void>`specjalizacji .
- , `for_each_n()` `generate_n()`i `search_n()` algorytmy wcześniej nie można skompilować, jeśli argument length nie był typem integralnym; teraz próbują przekonwertować niecałkowe długości na `difference_type`iteratory.
- `normal_distribution<float>`nie emituje już ostrzeżenia wewnątrz standardowej biblioteki o zwężenie od podwójnego do float.
- Naprawiono `basic_string` niektóre `npos` operacje, `max_size()` które były używane zamiast sprawdzania przepełnienia maksymalnego rozmiaru.
- `condition_variable::wait_for(lock, relative_time, predicate)`czekałby na cały względny czas w przypadku fałszywego przebudzenia. Teraz będzie czekać tylko na jeden interwał względnego czasu.
- `future::get()`teraz unieważnia `future`, zgodnie z normą wymaga.
- `iterator_traits<void *>`był twardym błędem, ponieważ próbował `void&`utworzyć ; teraz czysto staje się pustą strukturą, aby umożliwić użycie `iterator_traits` w warunkach SFINAE "czy iterator".
- Niektóre ostrzeżenia zgłoszone przez Clang **-Wsystem-headers zostały naprawione.**
- Poprawiono również "specyfikacja wyjątku w deklaracji nie pasuje do poprzedniej deklaracji" zgłoszonej przez Clang **-Wmicrosoft-exception-spec**.
- Poprawiono również mem-initializer-list zamawiania ostrzeżeń zgłoszonych przez Clang i C1XX.
- Kontenery nieurządzone nie zamieniły swoich funkcji mieszania ani predykatów, gdy same kontenery zostały zamienione. Teraz to robią.
- Wiele operacji wymiany kontenera są teraz oznaczone `noexcept` (jak nasza standardowa biblioteka nigdy nie zamierza zgłosić wyjątek podczas wykrywania non-non-equal-allocator`propagate_on_container_swap` warunek niezdefiniowanego zachowania).
- Wiele `vector<bool>` operacji jest `noexcept`teraz oznaczonych .
- Standardowa biblioteka wymusi teraz `value_type` pasujący alokator (w trybie C++17) z lukem ucieczkowym opt-out.
- Naprawiono pewne warunki, w `basic_string` których wstawianie własnego zakresu do rozszyfrowywania zawartości strun. (Uwaga: samozakres-wstawianie do wektorów jest nadal zabronione przez standard).)
- `basic_string::shrink_to_fit()`nie ma już wpływu na alokatora. `propagate_on_container_swap`
- `std::decay`teraz obsługuje obrzydliwe typy funkcji, czyli typy funkcji, które są kwalifikowane cv i/lub ref-qualified.
- Zmienione obejmują dyrektywy, aby użyć odpowiedniej czułości wielkości liter i ukośników do przodu, co poprawia przenośność.
- Poprawiono ostrzeżenie C4061 "wyliczacz '*wyliczający*' w przełączniku wyliczenia '*wyliczenia*' nie jest jawnie obsługiwane przez etykietę sprawy". To ostrzeżenie jest domyślnie i zostało ustalone jako wyjątek od ogólnych zasad biblioteki standardowej dotyczących ostrzeżeń. (Standardowa biblioteka jest **/W4** czyste, ale nie próbuje być **/Wall** czyste. Wiele ostrzeżeń domyślnie są bardzo hałaśliwe, i nie są przeznaczone do regularnego użytku.)
- Ulepszone `std::list` sprawdzanie debugowania. Iteratory listy teraz `operator->()`sprawdzić `list::unique()` , a teraz oznacza iteratory jako unieważnione.
- Poprawiono metaprogramowanie alokatora `tuple`w .

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- `std::partition`teraz wywołuje predykat N razy zamiast N + 1 razy, zgodnie z wymaganiami standardu.
- Próby uniknięcia magicznych ładunków w wersji 15.3 zostały naprawione w wersji 15.5.
- `std::atomic<T>`nie wymaga `T` już domyślnego konstruowania.
- Algorytmy sterty, które zajmują czas logarytmiczne nie zrobić liniowe twierdzenie czasu, że dane wejściowe jest w rzeczywistości sterty, gdy debugowanie iteratora jest włączona.
- `__declspec(allocator)`jest teraz strzeżony tylko dla C1XX, aby zapobiec ostrzeżeniom ze strony Clanga, który nie rozumie tej dekspekty.
- `basic_string::npos`jest teraz dostępna jako stała czasu kompilacji.
- `std::allocator`w trybie C++17 teraz poprawnie obsługuje alokację typów przerekranowanych, `max_align_t`czyli typów, których wyrównanie jest większe niż , chyba że wyłączone przez **/Zc:alignedNew-**.  Na przykład wektory obiektów z wyrównaniem 16-bajtowym lub 32-bajtowym są teraz poprawnie wyrównane dla instrukcji SSE i AVX.

### <a name="conformance-improvements"></a>Ulepszenia zgodności

- Dodaliśmy \<\>wszelkie \<, string_view\> `apply()`, `make_from_tuple()`, .
- Dodano \<\>opcjonalne\> `shared_ptr::weak_type`, \< \<wariant ,\>i cstdalign .
- Włączone C++14 `constexpr` `min(initializer_list)`w `max(initializer_list)`, `minmax(initializer_list)`i `min_element()` `max_element()`, `minmax_element()`i , i , i .

Aby uzyskać więcej informacji, zobacz [tabela zgodności języka języka Microsoft C++.](../visual-cpp-language-conformance.md)

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- Zaimplementowano kilka dodatkowych funkcji języka C++17. Aby uzyskać więcej informacji, zobacz [tabela zgodności języka języka Microsoft C++.](cpp-conformance-improvements.md#improvements_153)
- Zaimplementowano P0602R0 "wariant i opcjonalnie powinien propagować kopiowanie / przenoszenie trywialność".
- Standardowa biblioteka teraz oficjalnie toleruje dynamiczne RTTI jest wyłączona za pomocą [opcji /GR-.](../build/reference/gr-enable-run-time-type-information.md) Zarówno `dynamic_pointer_cast()` `rethrow_if_nested()` i z `dynamic_cast`natury wymagają, więc standardowa biblioteka oznacza je teraz jako `=delete` w obszarze **/GR-**.
- Nawet wtedy, gdy dynamiczne RTTI został wyłączony przez **/GR-** `typeid(SomeType)` , "statyczne RTTI" w postaci jest nadal dostępna i zasila kilka standardowych składników biblioteki. Standardowa biblioteka obsługuje teraz również wyłączenie tej funkcji, za pośrednictwem **/D\_HAS\_STATIC\_RTTI=0**. Ta flaga `std::any`wyłącza `target()` `target_type()` również , `std::function`i `get_deleter()` funkcji członkowskich `std::shared_ptr` , `std::weak_ptr`i funkcji członka znajomego i .
- Standardowa biblioteka używa teraz języka `constexpr` C++14 bezwarunkowo, zamiast zdefiniowanych warunkowo makr.
- Standardowa biblioteka używa teraz szablonów aliasów wewnętrznie.
- Standardowa biblioteka `nullptr` używa teraz wewnętrznie, `nullptr_t{}`a nie . (Wewnętrzne użycie NULL zostało wyeliminowane. Wewnętrzne użycie 0-as-null jest czyszczone stopniowo.)
- Standardowa biblioteka `std::move()` używa teraz wewnętrznie, zamiast stylowo `std::forward()`nadużywać .
- `static_assert(false, "message")` Zmieniono `#error message`na . Ta zmiana poprawia diagnostykę `#error` kompilatora, ponieważ natychmiast zatrzymuje kompilacji.
- Standardowa biblioteka nie `__declspec(dllimport)`oznacza już funkcji jako . Nowoczesna technologia linker nie wymaga już tego.
- Wyodrębnione SFINAE do domyślnych argumentów szablonu, co zmniejszyło bałagan w porównaniu do typów zwracanych i typów argumentów funkcji.
- Debuguje \<losowo\> teraz używać standardowej biblioteki zwykłych maszyn, zamiast funkcji `_Rng_abort()` wewnętrznej, która wywoływała `fputs()` do **stderr**. Implementacja tej funkcji jest zachowywana w celu zapewnienia zgodności binarnej, ale została usunięta w następnej wersji niezgodnej z binarną biblioteki standardowej.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- Dodano, przestarzało lub usunięto kilka standardowych funkcji biblioteki zgodnie ze standardem C++17. Aby uzyskać więcej informacji, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio.](cpp-conformance-improvements.md#improvements_155)
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
- Podpisy dla następujących algorytmów równoległych są dodawane, ale nie równoległe w tej chwili; profilowanie nie wykazało żadnych korzyści w równoległości algorytmów, które tylko przenieść lub permute elementów:
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
- Podstawy biblioteki V1
- Usuwanie przydziału `polymorphic_allocator`
- Poprawianie dedukcji argumentu szablonu klasy

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Obsługa algorytmów równoległych nie jest już eksperymentalna
- Nowa implementacja \<systemu plików>
- Konwersje ciągów elementarnych (częściowe)
- `std::launder()`
- `std::byte`
- `hypot(x,y,z)`
- Unikanie niepotrzebnego próchnicy
- Matematyczne funkcje specjalne
- `constexpr char_traits`
- Przewodniki po potrąceniach dla biblioteki standardowej

Aby uzyskać więcej informacji, zobacz [tabela zgodności języka języka Microsoft C++.](../visual-cpp-language-conformance.md)

### <a name="performance-and-throughput-fixes"></a>Poprawki wydajności i przepływności

- Wykonane `basic_string::find(char)` przeciążenia `traits::find` tylko raz. Wcześniej został zaimplementowany jako ogólne wyszukiwanie ciągów dla ciągu o długości 1.
- `basic_string::operator==`teraz sprawdza rozmiar ciągu przed porównaniem zawartości ciągów.
- Usunięto `basic_string`sprzężenie sterowania w , co było trudne do analizy dla optymalizatora kompilatora. Dla wszystkich krótkich `reserve` ciągów, wywołanie nadal ma koszt niezerowy, aby nic nie robić.
- `std::vector`został przebudowany pod kątem poprawności i wydajności: aliasowanie podczas operacji wstawiania i umieszczania jest teraz poprawnie obsługiwane zgodnie z wymaganiami standardu, gwarancja silnego wyjątku jest teraz dostarczana, gdy jest wymagana przez standard za pośrednictwem `move_if_noexcept()` i innych logiki, a wstawianie i umieszczanie wykonuje mniej operacji elementów.
- Standardowa biblioteka języka C++ pozwala teraz uniknąć dereferencing null fantazyjne wskaźniki.
- Zwiększona `weak_ptr::lock()` wydajność.
- Aby zwiększyć przepływność kompilatora, nagłówki biblioteki standardowej języka C++ unikają teraz dołączania deklaracji dla niepotrzebnych wewnętrznego kompilatora.
- Poprawiono wydajność `std::string` `std::wstring` konstruktorów i przenieść przez ponad trzy razy.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- Obejść interakcje, `noexcept` z którymi zapobiec inlining `std::atomic` implementacji do funkcji, które używają structured exception handling (SEH).
- Zmieniono wewnętrzną `_Deallocate()` funkcję biblioteki standardowej, aby zoptymalizować go na mniejszy kod, dzięki czemu można ją wywrzeć na więcej miejsc.
- Zmieniono `std::try_lock()` na użycie rozszerzeń pakietu zamiast rekursji.
- Ulepszono `std::lock()` algorytm unikania zakleszczenia do `lock()` `try_lock()` używania operacji zamiast obracania się na wszystkich blokadach.
- Włączono optymalizację nazwanych `system_category::message()`wartości zwracanych w pliku .
- `conjunction`i `disjunction` teraz utworzyć wystąpienie typów N + 1, zamiast typów 2N + 2.
- `std::function`nie ma już wystąpienia maszyny pomocnicze alokatora dla każdego typu usunięte wywoływane, poprawę przepustowości i zmniejszenie .obj rozmiar w programach, które przechodzą wiele różnych lambdas do `std::function`.
- `allocator_traits<std::allocator>`zawiera ręcznie inlined `std::allocator` operacji, zmniejszenie rozmiaru kodu w `std::allocator` `allocator_traits` kodzie, który współdziała z tylko za pośrednictwem (czyli w większości kodu).
- Interfejs alokatora minimalnego C++ 11 jest teraz `allocator_traits` obsługiwany przez standardową bibliotekę wywołującą bezpośrednio, zamiast zawijać alokator w klasie `_Wrap_alloc`wewnętrznej. Ta zmiana zmniejsza rozmiar kodu generowane dla obsługi alokatora, zwiększa optymalizatora zdolność do rozumowania o standardowych kontenerów biblioteki w niektórych `_Wrap_alloc<your_allocator_type>` przypadkach i zapewnia lepsze środowisko debugowania (jak teraz widzisz typu alokatora, a nie w debugerze).
- Usunięto metaprogramowanie dla niestandardowych `allocator::reference`, które alokatory nie są w rzeczywistości dozwolone do dostosowania. (Alokatorów można kontenery używać fantazyjne wskaźniki, ale nie fantazyjne odniesienia.)
- Przód kompilatora został nauczony, aby rozpakować iteratory debugowania w pętli opartych na zakresie, poprawiając wydajność kompilacji debugowania.
- Wewnętrzna `basic_string` ścieżka `shrink_to_fit()` zmniejszania dla i `reserve()` nie jest już w ścieżce ponownego przydzielania operacji, zmniejszając rozmiar kodu dla wszystkich mutujących elementów członkowskich.
- Wewnętrzna `basic_string` ścieżka wzrostu nie jest `shrink_to_fit()`już w ścieżce .
- Operacje `basic_string` mutowania są teraz uwzględniane w nieprzydzielania szybkiej ścieżki i przydzielaniu funkcji ścieżki powolnej, co czyni go bardziej prawdopodobnym dla wspólnego przypadku nie ponownego przydzielenia do wywoływania.
- Operacje `basic_string` mutatingu teraz konstruować ponownie przydzielone bufory w żądanym stanie, a nie zmiany rozmiaru w miejscu. Na przykład wstawianie na początku ciągu teraz przenosi zawartość po wstawieniu dokładnie raz (w dół lub do nowo przydzielonego buforu), zamiast dwa razy w przypadku ponownego przydzielania (do nowo przydzielonego buforu, a następnie w dół).
- Operacje wywołujące standardową \<\> bibliotekę `errno` C w ciągu teraz buforować adres, aby usunąć powtarzające się interakcje z TLS.
- Uproszczone `is_pointer` wdrażanie.
- Zakończono zmianę wyrażenia opartego na `struct` `void_t`funkcjach SFINAE na i na podstawie.
- Standardowe algorytmy biblioteki unikają teraz iteratorów postincrementing.
- Naprawiono ostrzeżenia o obcięciu podczas używania 32-bitowych alokatorów w systemach 64-bitowych.
- `std::vector`przenieść przypisanie jest teraz bardziej wydajne w przypadku non-POCMA non-equal-allocator, przez ponowneużywanie buforu, gdy jest to możliwe.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- `basic_string<char16_t>`teraz angażuje się `memcmp` `memcpy`w to samo `basic_string<wchar_t>` , i podobne optymalizacje, które zaangażuje.
- Ograniczenie optymalizatora, które uniemożliwiło inlined wskaźników funkcji, narażone przez nasze "uniknąć kopiowania funkcji" pracy w programie Visual Studio `lower_bound(iter, iter, function pointer)`2015 Update 3, został przepracowany, przywracając wydajność .
- Obciążenie iteratora debugowania weryfikacji kolejności danych `includes`wejściowych `set_symmetric_difference`do `set_union` , `set_difference`, i został zmniejszony przez rozpakowywanie iteratorów przed sprawdzeniem kolejności.
- `std::inplace_merge`teraz przeskakuje nad elementami, które są już w pozycji.
- Konstruowanie `std::random_device` nie jest już konstruowanie, `std::string`a następnie niszczy .
- `std::equal`i `std::partition` miał przejść optymalizacji wątków, który zapisuje porównanie iteratora.
- Po `std::reverse` przekazaniu wskaźników do trywialnie kopii, `T`będzie teraz wysyłać do odręcznej implementacji wektoryzowanej.
- `std::fill`, `std::equal`i `std::lexicographical_compare` uczono, jak `memset` wysyłać `std::byte` `gsl::byte` do i `memcmp` dla i (i innych char-jak wyliczenia i klasy wyliczenia). Ponieważ `std::copy` wysyłki `is_trivially_copyable`za pomocą , nie trzeba żadnych zmian.
- Standardowa biblioteka nie zawiera już destruktorów pustych nawiasów klamrowych, których jedynym zachowaniem było uczynienie typów nietrywialną.

## <a name="other-libraries"></a>Inne biblioteki

### <a name="open-source-library-support"></a>Obsługa biblioteki typu open source

**Vcpkg** to narzędzie wiersza polecenia typu open source, które znacznie upraszcza proces pozyskiwania i tworzenia statycznych libs i bibliotek DLLS typu open source w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [vcpkg: Menedżer pakietów dla języka C++](../build/vcpkg.md).

### <a name="cpprest-sdk-290"></a>CPPRest SDK 2.9.0

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

CPPRestSDK, wieloplatformowy internetowy interfejs API dla języka C++, został zaktualizowany do wersji 2.9.0. Aby uzyskać więcej informacji, zobacz [CppRestSDK 2.9.0 jest dostępny na GitHub](https://devblogs.microsoft.com/cppblog/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- Kolejny zestaw poprawek zgodności wyszukiwania nazw
- Istniejące konstruktory przenoszenia i operatory przenoszenia przydziałów są teraz poprawnie oznaczone jako nierzucające
- Unsuppress ważne ostrzeżenie C4640 o wątku bezpieczne init lokalnych statyków w atlstr.h
- Inicjowanie lokalnych statics bezpieczne wątku został automatycznie wyłączony w xp zestaw narzędzi podczas korzystania z ATL do tworzenia biblioteki DLL, ale teraz nie jest. Można dodać **/Zc:threadSafeInit-** w ustawieniach projektu, jeśli jest to możliwe za pomocą wyłączonej inicjalizacji bezpiecznej dla wątków.

### <a name="visual-c-runtime"></a>Środowisko wykonawcze języka Visual C++

- Nowy nagłówek "cfguard.h" dla symboli Control Flow Guard.

## <a name="c-ide"></a>Środowisko IDE języka C++

- Wydajność wprowadzania zmian w konfiguracji jest teraz lepsza w przypadku natywnych projektów w języku C++ i o wiele lepsza w projektach C++/CLI. Gdy konfiguracja rozwiązania jest aktywowana po raz pierwszy, będzie teraz szybsza, a wszystkie późniejsze aktywacje tej konfiguracji rozwiązania będą niemal natychmiastowe.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- Ponownie napisano kilka kreatorów projektu i kodów w stylu okna dialogowego podpisu.
- **Dodaj klasę** teraz uruchamia Kreatora dodaj klasę bezpośrednio. Wszystkie inne elementy, które były wcześniej tutaj są teraz dostępne w obszarze **Dodaj > Nowy element**.
- Projekty systemu Win32 znajdują się teraz w kategorii **Pulpit systemu Windows** w oknie dialogowym Nowy **projekt.**
- Szablony **konsoli systemu Windows** i aplikacji **klasycznych** tworzą teraz projekty bez wyświetlania kreatora. W tej samej kategorii znajduje się nowy **Kreator pulpitu systemu Windows,** który wyświetla te same opcje, co stary kreator **aplikacji konsoli Win32.**

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

Kilka operacji języka C++, które używają aparatu IntelliSense do refaktoryzacji i nawigacji kodu działają znacznie szybciej. Następujące liczby są oparte na rozwiązaniu Visual Studio Chromium z 3500 projektów:

|||
|-|-|
|Funkcja|Poprawa wydajności|
|Zmień nazwę|5,3 x|
|Zmienianie podpisu |4,5 x|
|Znajdź wszystkie odwołania|4,7x|

C++ obsługuje teraz klawisze Ctrl+Click **Go To Definition,** ułatwiając nawigację myszą w definicjach. Wizualizator struktury z pakietu Narzędzia zasilania produktywności jest teraz domyślnie również uwzględniony w produkcie.

## <a name="intellisense"></a>IntelliSense

- Nowy aparat bazy danych oparty na SQLite jest teraz używany domyślnie. Przyspieszy to operacje bazy danych, takie jak **Przejdź do definicji** i **Znajdź wszystkie odwołania,** i znacznie poprawi czas analizy początkowego rozwiązania. To ustawienie zostało przeniesione do **Tools > Options > Text Editor > C/C++ > Advanced** (dawniej pod ... C/C++ | Eksperymentalne).

- Poprawiliśmy wydajność intellisense w projektach i plikach, które nie używają wstępnie skompilowanych nagłówków — dla nagłówków w bieżącym pliku zostanie utworzony automatyczny wstępnie skompilowany nagłówek.

- Do listy błędów dodaliśmy filtrowanie błędów i pomoc dotyczącą błędów funkcji IntelliSense. Kliknięcie kolumny błędów umożliwia teraz filtrowanie. Ponadto kliknięcie konkretnego błędu lub naciśnięcie klawisza F1 uruchamia wyszukiwanie online dotyczące danego komunikatu o błędzie.

  ![Lista błędów](media/ErrorList1.png "Lista błędów")

  ![Filtrowana lista błędów](media/ErrorList2.png "Filtrowana lista błędów")

- Dodano możliwość filtrowania listy elementów członkowskich według rodzaju.

  ![Filtrowanie listy elementów członkowskich](media/mlfiltering.png "Filtrowanie listy elementów członkowskich")

- Dodano nową eksperymentalną funkcję Predictive IntelliSense, która zapewnia kontekstowe filtrowanie tego, co pojawia się na liście członków. Aby uzyskać więcej informacji, zobacz [C++ IntelliSense Ulepszenia - Predictive IntelliSense & Filtrowanie](https://devblogs.microsoft.com/cppblog/c-intellisense-improvements-predictive-intellisense-filtering/).
- **Znajdź wszystkie odwołania** (Shift + F12) teraz pomaga poruszać się łatwo, nawet w złożonych baz kodu. Zapewnia zaawansowane grupowanie, filtrowanie, sortowanie, wyszukiwanie w wynikach i (dla niektórych języków) kolorowanie, dzięki czemu można uzyskać jasne zrozumienie odwołań. W przypadku języka C++ nowy interfejs użytkownika zawiera informacje o tym, czy czytamy od zmiennej, czy piszemy do zmiennej.
- Funkcja zmiany kropki na strzałkę IntelliSense została przeniesiona z doświadczalnych do zaawansowanych i teraz jest domyślnie włączona. Funkcje edytora **Rozwiń zakresy** i **Rozwiń pierwszeństwo** również zostały przeniesione z eksperymentalnych do zaawansowanych.
- Eksperymentalne funkcje refaktoryzacji **Zmień podpis** i **Wyodrębnij funkcja** są teraz dostępne domyślnie.
- Dodano eksperymentalną funkcję "Szybsze ładowanie projektu" dla projektów w języku C++. Następnym razem, gdy otworzysz projekt C++, będzie on ładowany szybciej, a po tym czasie będzie ładować *się znacznie* szybciej!
- Niektóre z tych funkcji są wspólne dla innych języków, a niektóre są specyficzne dla języka C++. Aby uzyskać więcej informacji na temat tych nowych funkcji, zobacz [Ogłaszanie programu Visual Studio "15" Wersja zapoznawcza 5](https://devblogs.microsoft.com/visualstudio/announcing-visual-studio-15-preview-5/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Dodano wsparcie dla ClangFormat. Aby uzyskać więcej informacji, zobacz [Pomoc techniczna clangformat w programie Visual Studio 2017](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/).

## <a name="non-msbuild-projects-with-open-folder"></a>Projekty inne niż MSBuild z otwartym folderem

Visual Studio 2017 wprowadza funkcję **Otwórz folder,** która umożliwia kodowanie, tworzenie i debugowanie w folderze zawierającym kod źródłowy bez konieczności tworzenia żadnych rozwiązań lub projektów. Teraz jest znacznie prostsze, aby rozpocząć pracę z programem Visual Studio, nawet jeśli projekt nie jest projektem opartym na msbuild. Z **Open Folder**, można uzyskać dostęp do zaawansowanych możliwości zrozumienia kodu, edycji, tworzenia i debugowania, które visual studio już zapewnia dla projektów MSBuild. Aby uzyskać więcej informacji, zobacz [Otwieranie projektów folderów dla języka C++](../build/open-folder-projects-cpp.md).

- Ulepszenia obsługi polecenia Otwórz folder. Można dostosować środowisko za pomocą tych plików .json:
  - CppProperties.json dostosowuje obsługę funkcji IntelliSense i przeglądania.
  - Tasks.json dostosowuje kroki kompilacji.
  - Launch.json dostosowuje obsługę debugowania.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- Ulepszona obsługa alternatywnych kompilatorów i środowisk kompilacji, takich jak MinGW i Cygwin. Aby uzyskać więcej informacji, zobacz [Korzystanie z minGw i Cygwin z programem Visual C++ i Otwórz folder](https://devblogs.microsoft.com/cppblog/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Dodano obsługę definiowania zmiennych środowiskowych specyficznych dla globalnej i konfiguracji w plikach CppProperties.json i CMakeSettings.json. Te zmienne środowiskowe mogą być używane przez konfiguracje debugowania zdefiniowane w pliku launch.vs.json i zadania w pliku tasks.vs.json. Aby uzyskać więcej informacji, zobacz [Dostosowywanie środowiska za pomocą języka Visual C++ i Otwórz folder](https://devblogs.microsoft.com/cppblog/customizing-your-environment-with-visual-c-and-open-folder/).
- Ulepszone wsparcie dla generatora Ninja CMake, w tym możliwość łatwego targetu platform 64-bitowych.

## <a name="cmake-support-via-open-folder"></a>CZdrowa pomoc techniczna za pośrednictwem folderu Open

Visual Studio 2017 wprowadza obsługę przy użyciu projektów CMake bez konwersji do plików projektu MSBuild (.vcxproj). Aby uzyskać więcej informacji, zobacz [CMake projektów w programie Visual Studio](../build/cmake-projects-in-visual-studio.md). Otwieranie projektów CMake z **open folder** automatycznie konfiguruje środowisko do edycji C++ edycji, tworzenia i debugowania.

- C++ IntelliSense działa bez konieczności tworzenia pliku CppProperties.json w folderze głównym. Dodaliśmy również nową listy rozwijanej, aby umożliwić użytkownikom łatwe przełączanie się między konfiguracjami dostarczonymi przez pliki CMake i CppProperties.json.

- Dalsza konfiguracja jest obsługiwana przy użyciu pliku CMakeSettings.json, który znajduje się w tym samym folderze co plik CMakeLists.txt.

  ![Cmake Otwórz folder](media/cmake-cpp.png "CMake Otwórz folder")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- Dodano wsparcie dla generatora CMake Ninja.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- Dodano obsługę importowania istniejących pamięci podręcznych CMake.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- Dodano obsługę CMake 3.11, analizę kodu w projektach CMake, widok cele w Eksploratorze rozwiązań, opcje generowania pamięci podręcznej i kompilację pojedynczego pliku. Aby uzyskać więcej informacji, zobacz [CMake pomocy technicznej w programie Visual Studio](https://devblogs.microsoft.com/cppblog/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) i [CMake projektów w programie Visual Studio](../build/cmake-projects-in-visual-studio.md).

## <a name="windows-desktop-development-with-c"></a>Tworzenie pulpitu dla systemu Windows w języku C++

Zapewniamy obecnie bardziej zaawansowane środowisko instalacji oryginalnego obciążenia C++. Dodaliśmy możliwe do wybrania składniki pozwalające na zainstalowanie tylko tych narzędzi, których potrzebujesz. Wskazane rozmiary instalacji dla składników wymienionych w interfejsie użytkownika instalatora nie są dokładne i nie doceniają całkowitego rozmiaru.

Aby pomyślnie tworzyć projekty Win32 w obciążeniu C++ dla komputerów stacjonarnych, musisz zainstalować zarówno zestaw narzędzi, jak i zestaw SDK systemu Windows. Zainstaluj zalecane (wybrane) składniki **VC++ 2017 v141 toolset (x86, x64)** i **Windows 10 SDK (10.0.nnnnn),** aby upewnić się, że działa. Jeśli niezbędne narzędzia nie zostaną zainstalowane, projekty nie zostaną pomyślnie utworzone, a kreator zostanie zawiesiny.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

Narzędzia kompilacji języka Visual C++ (wcześniej dostępne jako produkt autonomiczny) są teraz uwzględniane jako obciążenie w Instalatorze programu Visual Studio. To obciążenie instaluje tylko narzędzia wymagane do tworzenia projektów języka C++ bez instalowania środowiska IDE programu Visual Studio. Zestawy narzędzi v140 i v141 są dołączone. Zestaw narzędzi w wersji 141 zawiera najnowsze ulepszenia w programie Visual Studio 2017 w wersji 15.5. Aby uzyskać więcej informacji, zobacz [Narzędzia kompilacji programu Visual Studio zawierają teraz zestawy narzędzi MSVC VS2017 i VS2015.](https://devblogs.microsoft.com/cppblog/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/)

## <a name="linux-development-with-c"></a>Programowanie dla systemu Linux w języku C++

Popularne rozszerzenie [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) stanowi obecnie cześć programu Visual Studio. Ta instalacja zawiera wszystko, czego potrzebujesz do tworzenia i debugowania aplikacji w języku C++ działających w środowisku systemu Linux.

##### <a name="visual-studio-2017-version-152"></a>Visual Studio 2017, wersja 15.2

Wprowadzono ulepszenia w udostępnianiu kodu między platformami i wizualizacji typów. Aby uzyskać więcej informacji, zobacz [Ulepszenia systemu Linux C++ dotyczące współdzielenia kodu i wizualizacji typów na wielu platformach.](https://devblogs.microsoft.com/cppblog/linux-cross-platform-and-type-visualization/)

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- Obciążenie Linuksa dodało obsługę **rsync** jako alternatywę dla **sftp** do synchronizowania plików ze zdalnymi komputerami z systemem Linux.
- Dodano obsługę kompilacji krzyżowej ukierunkowanej na mikrokontrolery ARM. Aby włączyć go w instalacji, wybierz programowanie systemu Linux z obciążeniem **C++** i wybierz opcję dla **rozwoju osadzonego i IoT**. Ta opcja dodaje narzędzia kompilacji krzyżowej ARM GCC i Make do instalacji. Aby uzyskać więcej informacji, zobacz [ARM GCC Cross Compilation w programie Visual Studio](https://devblogs.microsoft.com/cppblog/arm-gcc-cross-compilation-in-visual-studio/).
- Dodano obsługę CMake. Teraz można pracować na istniejącej bazy kodu CMake bez konieczności konwertowania go do projektu programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md).
- Dodano obsługę uruchamiania zadań zdalnych. Ta funkcja umożliwia uruchomienie dowolnego polecenia w systemie zdalnym zdefiniowanym w Menedżerze połączeń programu Visual Studio. Zadania zdalne umożliwiają również kopiowanie plików do systemu zdalnego.
Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Różne ulepszenia scenariuszy obciążenia systemu Linux. Aby uzyskać więcej informacji, zobacz [Ulepszenia obciążenia Linux C++ w systemie project system, oknie konsoli Systemu Linux, rsync i Dołącz do procesu](https://devblogs.microsoft.com/cppblog/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).
- IntelliSense dla nagłówków na zdalnych połączeniach Linuksa. Aby uzyskać więcej informacji, zobacz [IntelliSense for Remote Linux Headers](https://devblogs.microsoft.com/cppblog/intellisense-for-remote-linux-headers/) and [Configure a Linux CMake Project](../linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Programowanie gier w języku C++

Pełnych możliwości języka C++ można użyć do tworzenia profesjonalnych gier obsługiwanych przy użyciu zestawu funkcji DirectX lub Cocos2d.

## <a name="mobile-development-with-c-android-and-ios"></a>Rozwój urządzeń mobilnych w języku C++ (Android i iOS)

Program Visual Studio umożliwia obecnie programowanie i debugowanie aplikacji mobilnych przeznaczonych dla systemów Android oraz iOS.

## <a name="universal-windows-apps"></a>Aplikacje uniwersalne systemu Windows

Język C++ stanowi składnik opcjonalny obciążenia Aplikacja uniwersalna systemu Windows.  Obecnie uaktualnianie projektów C++ należy wykonywać ręcznie. Jeśli projekt uniwersalnej platformy systemu Windows przeznaczony dla wersji 140 zostanie otwarty w programie Visual Studio 2017, należy wybrać zestaw narzędzi platformy w wersji 141 na stronach właściwości projektu, jeśli nie masz zainstalowanego programu Visual Studio 2015.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nowe opcje języka C++ na uniwersalnej platformie Windows (UWP)

Dostępne są teraz nowe opcje pisania i pakowania aplikacji C++ dla platformy uniwersalnej systemu Windows i Sklepu Windows: za pomocą infrastruktury Mostek pulpitu można spakować istniejącą aplikację klasyczną lub obiekt COM do wdrożenia za pośrednictwem Sklepu Windows lub za pośrednictwem istniejących kanałów za pomocą ładowania po stronie. Nowe możliwości systemu Windows 10 umożliwiają dodawanie funkcji platformy uniwersalnej systemu Windows do aplikacji klasycznej na różne sposoby. Aby uzyskać więcej informacji, zobacz [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

Dodano szablon projektu **pakietu Windows Application Packaging Project,** co znacznie upraszcza pakowanie aplikacji klasycznych za pomocą programu Desktop Bridge. Jest on dostępny w obszarze **Plik | Nowy | Projekt | Zainstalowany | Visual C++ | Uniwersalna platforma systemu Windows**. Aby uzyskać więcej informacji, zobacz [Pakowanie aplikacji przy użyciu programu Visual Studio (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Podczas pisania nowego kodu można teraz używać języka C++/WinRT, standardowej projekcji języka C++ dla środowiska wykonawczego systemu Windows zaimplementowanego wyłącznie w plikach nagłówkowych. Umożliwia zarówno autora i używać interfejsów API środowiska wykonawczego systemu Windows przy użyciu dowolnego kompilatora C++ zgodne ze standardami. C++/WinRT został zaprojektowany, aby zapewnić deweloperom języka C++ pierwszorzędny dostęp do nowoczesnego interfejsu API systemu Windows. Aby uzyskać więcej informacji, zobacz [C++/WinRT: Modern C++ dla środowiska wykonawczego systemu Windows](https://moderncpp.com/).

Od kompilacji 17025 programu Windows SDK Insider Preview c++/winrt jest zawarty w zestawie Windows SDK. Aby uzyskać więcej informacji, zobacz [C++/WinRT jest teraz dołączony do zestawie Windows SDK](https://devblogs.microsoft.com/cppblog/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="clangc2-platform-toolset"></a>Zestaw narzędzi platformy Clang/C2

Zestaw narzędzi Clang/C2 dostarczany z programem Visual Studio 2017 obsługuje teraz przełącznik **/bigobj,** który ma kluczowe znaczenie dla tworzenia dużych projektów. Oferuje on również kilka ważnych poprawek, zarówno we frontonie, jak i zapleczu kompilatora.

## <a name="c-code-analysis"></a>Analiza kodu języka C++

Podstawowe narzędzia do sprawdzania kodu C++ wymuszające stosowanie [podstawowych wytycznych dotyczących języka C++](https://github.com/isocpp/CppCoreGuidelines) są obecnie dystrybuowane z programem Visual Studio. Wystarczy włączyć kontrolerów na stronie **Rozszerzenia analizy kodu** na stronach właściwości projektu, a rozszerzenia zostaną uwzględnione podczas uruchamiania analizy kodu. Aby uzyskać więcej informacji, zobacz [Korzystanie z kontrolerów podstawowych wytycznych języka C++](/cpp/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Strona właściwości CppCoreCheck")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017, wersja 15.3

- Dodano obsługę reguł związanych z zarządzaniem zasobami.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

- Nowe podstawowe wytyczne języka C++ sprawdza obejmują poprawność inteligentnego wskaźnika, poprawne użycie `goto` globalnych inicjatorów i oznaczanie użycia konstrukcji, takich jak i złe rzutowania.

- Niektóre numery ostrzeżeń, które można znaleźć w wersji 15.3, nie są już dostępne w wersji 15.5. Ostrzeżenia te zostały zastąpione bardziej szczegółowymi operacjami sprawdzania.

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017, wersja 15.6

- Dodano obsługę analizy pojedynczego pliku i ulepszenia w wydajności w czasie wykonywania analizy. Aby uzyskać więcej informacji, zobacz [Ulepszenia analizy statycznej języka C++ dla programu Visual Studio 2017 15.6 Preview 2](https://devblogs.microsoft.com/cppblog/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Obsługa dodana dla [/analyze:ruleset](../build/reference/analyze-code-analysis.md), która pozwala określić reguły analizy kodu do uruchomienia.
- Dodano obsługę dodatkowych reguł podstawowych wytycznych języka C++.  Aby uzyskać więcej informacji, zobacz [Korzystanie z kontrolerów podstawowych wytycznych języka C++](/cpp/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing"></a>Testowanie jednostek

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017, wersja 15.5

Karta testowa Google i adapter Boost.Test są teraz dostępne jako składniki rozwoju pulpitu z obciążeniem **C++** i są zintegrowane z **Eksploratorem testów.** Obsługa CTest jest dodawana dla projektów Cmake (przy użyciu open folder), chociaż pełna integracja z **Eksploratorem testów** nie jest jeszcze dostępna. Aby uzyskać więcej informacji, zobacz [Pisanie testów jednostkowych dla języka C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp).

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017, wersja 15.6

- Dodano obsługę dynamicznej biblioteki Boost.Test.
- Szablon elementu Boost.Test jest teraz dostępny w IDE.

Aby uzyskać więcej informacji, zobacz [Boost.Test Unit Testing: Obsługa biblioteki dynamicznej i Nowy szablon elementu](https://devblogs.microsoft.com/cppblog/boost-test-unit-testing-dynamic-library-support-and-new-item-template/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

[CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) wsparcie dodane dla projektów testów jednostkowych języka C++. Aby uzyskać więcej informacji, zobacz [Ogłaszanie funkcji CodeLens dla testowania jednostek języka C++](https://devblogs.microsoft.com/cppblog/announcing-codelens-for-c-unit-testing/).

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostyka grafiki programu Visual Studio

Diagnostyka grafiki programu Visual Studio to zestaw narzędzi do rejestrowania i analizowania problemów z renderowaniem i wydajnością w aplikacjach Direct3D. Funkcji diagnostyki grafiki można używać z aplikacjami działającymi lokalnie na komputerze z systemem Windows, w emulatorze urządzenia z systemem Windows lub na komputerze lub urządzeniu zdalnym.

- **Dane wejściowe & wyjście dla modułów cieniowania wierzchołków i geometrii:** Możliwość wyświetlania danych wejściowych i wyjściowych modułów cieniujących wierzchołków i modułów cieniujących geometrię jest jedną z najbardziej pożądanych operacji i jest teraz obsługiwana w narzędziach. Wystarczy wybrać etap VS lub GS w widoku Etapy potoku, aby rozpocząć sprawdzanie jego danych wejściowych i wyjściowych w poniższej tabeli.

  ![Wejście/wyjście dla modułów cieniującego](media/io-shaders.png)

- **Wyszukiwanie i filtrowanie w tabeli obiektów:** Zapewnia szybki i łatwy sposób na znalezienie zasobów, których szukasz.

  ![Wyszukiwanie](media/search.png)

- **Historia zasobów:** Ten nowy widok zapewnia usprawniony sposób wyświetlania całej historii modyfikacji zasobu, ponieważ był używany podczas renderowania przechwyconej ramki. Aby wywołać historię dla dowolnego zasobu, po prostu kliknij ikonę zegara obok dowolnego hiperłącza zasobu.

  ![Historia zasobów](media/resource-history.png)

  Spowoduje to wyświetlenie nowego okna narzędzia **Historia zasobów,** wypełnionego historią zmian zasobu.

  ![Zmiana historii zasobów](media/resource-history-change.png)

  Jeśli ramka została przechwycona z włączonym przechwytywaniem pełnego stosu wywołań **(Visual Studio > Tools > Options** w obszarze Diagnostyka grafiki), kontekst każdego zdarzenia zmiany można szybko **wywnioskować**i sprawdzić w projekcie programu Visual Studio.

- **Statystyki API:** Wyświetl podsumowanie wysokiego poziomu użycia interfejsu API w ramce. Jest to przydatne do odkrywania połączeń, które możesz nie zdawać sobie sprawy, że w ogóle tworzysz, lub połączeń, które robisz zbyt wiele. To okno jest dostępne za pośrednictwem **widoku > statystyki interfejsu API** w programie Visual Studio Graphics Analyzer.

  ![Statystyki API](media/api-stats.png)

- **Statystyki pamięci:** Zobacz, ile pamięci jest przydzielana przez sterownik dla zasobów utworzonych w ramce. To okno jest dostępne za pośrednictwem **view > statystyki pamięci** w programie Visual Studio Graphics **Analyzer**. Dane można kopiować do pliku CSV w celu przeglądania w arkuszu kalkulacyjnym, klikając prawym przyciskiem myszy i wybierając polecenie **Kopiuj wszystko**.

  ![Statystyki pamięci](media/memory-stats.png)

- **Sprawdzanie poprawności ramki:** Nowa lista błędów i ostrzeżeń umożliwia nawigowanie po liście zdarzeń na podstawie potencjalnych problemów wykrytych przez warstwę debugowania Direct3D. Kliknij **pozycję Wyświetl > sprawdzanie poprawności ramki** w analizatorze grafiki programu Visual Studio, aby otworzyć okno. Następnie kliknij przycisk **Uruchom sprawdzanie poprawności,** aby rozpocząć analizę. Może upłynąć kilka minut, w zależności od złożoności ramki.

  ![Sprawdzanie poprawności ramki](media/frame-validation.png)

- **Analiza ramek dla D3D12:** Analiza ramek służy do analizowania wydajności połączeń rysowania za pomocą ukierunkowanych eksperymentów "co jeśli". Przełącz się na kartę Analiza ramek i uruchom analizę, aby wyświetlić raport. Aby uzyskać więcej informacji, obejrzyj [wideo GoingNative 25: Visual Studio Graphics Frame Analysis.](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool)

  ![Analiza ramek](media/frame-analysis.png)

- **Ulepszenia użycia gpu:** Otwórz ślady można podjąć za pomocą profilera użycia procesora GPU programu Visual Studio za pomocą widoku gpu lub narzędzia WPA (Windows Performance Analyzer) w celu bardziej szczegółowej analizy. Jeśli masz zainstalowany zestaw narzędzi wydajności systemu Windows, w prawym dolnym rogu przeglądu sesji znajdują się dwa hiperłącza, jedno dla WPA, a drugie dla widoku gpu.

  ![Użycie gpu](media/gpu-usage.png)

  Ślady otwarte w widoku GPU za pośrednictwem tego łącza obsługują zsynchronizowane powiększanie i przesuwanie na osi czasu między widokem VS i GPU. Pole wyboru w programie VS służy do kontrolowania, czy synchronizacja jest włączona, czy nie.

  ![Widok gpu](media/gpu-view.png)

::: moniker-end

::: moniker range="=vs-2015"

Aby uzyskać pełną listę nowości za pośrednictwem programu Visual Studio 2015 Update 3, zobacz [Visual C++ What's New 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015). Aby uzyskać więcej informacji na temat nowości we wszystkich programach Visual Studio 2015, zobacz informacje o wersji połączone z [historii notatek wydania programu Visual Studio 2015.](/visualstudio/releasenotes/vs2015-version-history) Aby uzyskać informacje o nowościach w języku C++ w programie Visual Studio 2019, zobacz [Co nowego w języku C++ w programie Visual Studio.](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019) Aby uzyskać informacje na temat nowości w języku C++ w programie Visual Studio 2017, zobacz [Co nowego w języku C++ w programie Visual Studio 2017.](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017)

::: moniker-end
