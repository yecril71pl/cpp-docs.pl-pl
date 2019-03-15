---
title: Co nowego w języku Visual C++ w programie Visual Studio
ms.date: 11/15/2017
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: b75a1903b3e0767f8aa009134a2b37a7d1a8e0d0
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810474"
---
# <a name="whats-new-for-visual-c-in-visual-studio-2017"></a>Co nowego w języku Visual C++ w programie Visual Studio 2017

Program Visual Studio 2017 obejmuje wiele aktualizacji i poprawek dotyczących środowiska Visual C++. Już firma Microsoft usunęła ponad 250 usterek i zgłoszonych problemów w kompilatorze i narzędziach, wiele przesłanych przez klientów za pośrednictwem [Zgłoś Problem](/visualstudio/how-to-report-a-problem-with-visual-studio-2017) i [sugestię](https://visualstudio.uservoice.com/) opcji w obszarze **Prześlij opinię** . Dziękujemy za zgłaszanie usterek! Aby uzyskać więcej informacji na temat what's new in całego programu Visual Studio, odwiedź [What's new in Visual Studio 2017](/visualstudio/ide/whats-new-in-visual-studio).

<!--The compiler and tools version number in Visual Studio 2017 is 14.10.24629. -->

## <a name="c-compiler"></a>kompilator C++

### <a name="c-conformance-improvements"></a>Ulepszenia zgodności języka C++

W tej wersji zaktualizowaliśmy standardową bibliotekę i kompilator języka C++ o rozszerzoną obsługę funkcji języka C ++ 11 i C ++ 14, a także wstępną obsługę niektórych funkcji, które mają zostać uwzględnione w standardowym języku C ++ 17. Aby uzyskać szczegółowe informacje, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio 2017](cpp-conformance-improvements-2017.md).

**Visual Studio 2017 w wersji 15.5**: Kompilator obsługuje około 75% funkcji, które są nowością w programie C ++ 17, w tym wiązania strukturyzowane, `constexpr` lambdy, `if constexpr`, zmienne wbudowane, złożyć wyrażenia i dodawanie `noexcept` do systemu typów. Są one dostępne w obszarze **/STD: c ++ 17** opcji. Aby uzyskać więcej informacji, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio 2017](cpp-conformance-improvements-2017.md)

**Visual Studio 2017 w wersji 15.7**: Zestaw narzędzi kompilatora MSVC w wersji 15.7 programu Visual Studio jest teraz zgodny ze standardem C++. Aby uzyskać więcej informacji, zobacz [Announcing: MSVC jest zgodny ze standardem C++](https://blogs.msdn.microsoft.com/vcblog/2018/05/07/announcing-msvc-conforms-to-the-c-standard/) i [zgodność języka Visual C++](visual-cpp-language-conformance.md).

### <a name="new-compiler-options"></a>Nowe opcje kompilatora

- [/ permissive-](build/reference/permissive-standards-conformance.md): Włącz wszystkie rygorystyczne standardy zgodność-opcje kompilatora i Wyłącz większość rozszerzeń kompilatora specyficzne dla firmy Microsoft (ale nie `__declspec(dllimport)`, na przykład). Ta opcja jest włączona domyślnie w programie Visual Studio 2017 w wersji 15.5.  **/ Permissive-** tryb zgodności obejmuje obsługę dwufazowe wyszukiwanie nazw. Aby uzyskać więcej informacji, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio 2017](cpp-conformance-improvements-2017.md).

- [/ Diagnostics](build/reference/diagnostics-compiler-diagnostic-options.md): Włącz wyświetlanie numer wiersza, numer wiersza i kolumny, lub numer wiersza i kolumny i karetki w ramach linii kodu, gdzie znaleziono diagnostycznych błąd lub ostrzeżenie.

- [/debug:fastlink](build/reference/debug-generate-debug-info.md): Włącz do 30% szybciej konsolidowania przyrostowego czasu (w porównaniu. Visual Studio 2015), kopiując nie wszystkie informacje w pliku PDB debugowania. Plik PDB wskazuje zamiast tego informacje debugowania dla plików obiektów i biblioteki, użyty do utworzenia pliku wykonywalnego. Zobacz [C++ szybciej tworzyć cyklu w programie VS "15" z fastlink](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-build-cycle-in-vs-15-with-debugfastlink/) i [zalecenia dotyczące szybkości C++ kompilacje w programie Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2016/10/26/recommendations-to-speed-c-builds-in-visual-studio/).

- Program Visual Studio 2017 umożliwia używanie [/SDL](build/reference/sdl-enable-additional-security-checks.md) z [/ await](build/reference/await-enable-coroutine-support.md). Firma Microsoft usunęła [usunęliśmy](build/reference/rtc-run-time-error-checks.md) ograniczenie koprocedur.

   **Visual Studio 2017 w wersji 15.3**:

- [/ STD: c ++ 14 i/STD: c ++ najnowsze](build/reference/std-specify-language-standard-version.md): Te opcje kompilatora umożliwiają wyrazić zgodę na określonych wersji języka programowania ISO C++ w projekcie. Nowy projekt funkcje warstwy standardowa jest chroniony przez większość **/STD: c ++ najnowsze** opcji.

- [/ STD: c ++ 17](build/reference/std-specify-language-standard-version.md) udostępnia zestaw funkcji C ++ 17 implementowane przez kompilator. Ta opcja powoduje wyłączenie kompilatora i biblioteki standardowej obsługi funkcji, które zostały zmienione lub nowych wersjach pracy roboczą i wad aktualizacje C++ Standard po C ++ 17. Aby włączyć te funkcje, użyj **/STD: c ++ najnowsze**.

### <a name="codegen-security-diagnostics-and-versioning"></a>Generowanie kodu zabezpieczeń, diagnostyki i przechowywanie wersji

Ta wersja oferuje kilka ulepszeń w optymalizacji, generowania kodu, przechowywanie wersji zestawu narzędzi i diagnostyki. Do istotnych ulepszeń należą:

- Generowanie ulepszone kodu pętli: Obsługa automatycznej wektoryzacji dzielenia stałych liczb całkowitych, Lepsza identyfikacja wzorców funkcji memset.
- Ulepszone kodu zabezpieczeń: Ulepszona emisja diagnostyki kompilatora przepełnienia buforu, a [/GUARD: CF](build/reference/guard-enable-control-flow-guard.md) teraz osłony instrukcje switch, które generują tabele przeskoków.
- Przechowywanie wersji: Wartość wbudowane makro preprocesora  **\_MSC\_VER** jest teraz monotonicznie aktualizowana przy każdej aktualizacji zestawu narzędzi Visual C++. Aby uzyskać więcej informacji, zobacz [Visual C++ w wersji kompilatora](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/).
- Nowy układ narzędzi: Kompilator i narzędzia powiązanych kompilacji ma nową strukturę lokalizacji i katalog na komputerze deweloperskim. Nowy układ umożliwia instalacje side-by-side wielu wersji kompilatora. Aby uzyskać więcej informacji, zobacz [układ narzędzia kompilatora w programie Visual Studio "15"](https://blogs.msdn.microsoft.com/vcblog/2016/10/07/compiler-tools-layout-in-visual-studio-15/).
- Ulepszona diagnostyka: W oknie danych wyjściowych zawiera obecnie kolumnę gdzie występuje błąd. Aby uzyskać więcej informacji, zobacz [ulepszenia diagnostyki kompilatora języka C++ w programie VS "15" Preview 5](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-compiler-diagnostics-improvements-in-vs-15-rc/).
- Korzystając z procedur wspólnych eksperymentalne słowo kluczowe **uzyskanie** (dostępne w obszarze **/ await** opcja) została usunięta. Zaktualizować swój kod w celu zastosowania `co_yield` zamiast tego. Więcej informacji można znaleźć na [blogu zespołu Visual C++](https://blogs.msdn.microsoft.com/vcblog/).

**Visual Studio 2017 w wersji 15.3**:

Dodatkowe ulepszenia diagnostyki w kompilatorze. Aby uzyskać więcej informacji, zobacz [ulepszenia diagnostyki w programie Visual Studio 2017 15.3.0](https://blogs.msdn.microsoft.com/vcblog/2017/07/21/diagnostic-improvements-in-vs2017-15-3-0/).

**Visual Studio 2017 w wersji 15.5**:

Visual C++ runtime wydajności w dalszym ciągu poprawić ze względu na lepszą jakość wygenerowanego kodu. Oznacza to, że można po prostu kompilację kodu, a aplikacja działa szybciej. Niektóre optymalizacje kompilatora są całkiem nowe, takich jak wektoryzację magazynów warunkowych wartości skalarnych, łączenie wywołań `sin(x)` i `cos(x)` w nowym `sincos(x)`i eliminowania nadmiarowe instrukcji od optymalizatora architektury SSA. Inne optymalizacje kompilatora są ulepszeniami istniejących funkcji, takich jak heurystyki Diagnostyka wektoryzowania automatycznego wyrażeń warunkowych, lepszej optymalizacji pętli i generowanie kodu minimalnej/maksymalnej float. Konsolidator ma nowy i szybsze **/OPT: ICF** wdrożenia, co może skutkować 9% link szybsze czasu, a inne poprawki wydajności w łączenie przyrostowe. Aby uzyskać więcej informacji, zobacz [od (optymalizacje)](build/reference/opt-optimizations.md) i [/incremental (Link przyrostowo)](build/reference/incremental-link-incrementally.md).

Visual C++ obsługuje rozszerzenia AVX-512 firmy Intel, w tym instrukcje dotyczące długości wektora, które udostępniają nowe funkcje w AVX-512 do rejestrach 128 - i 256-bitowy.

[/Zc:noexceptTypes-](build/reference/zc-noexcepttypes.md) opcji może służyć do przywrócenia do języka C ++ 14 wersji `noexcept` podczas korzystania z języka C ++ 17 trybu ogólnie rzecz biorąc. Dzięki temu można zaktualizować kodu źródłowego są zgodne z C ++ 17, bez konieczności ponownego zapisania wszystkie swoje `throw()` kodu w tym samym czasie. Aby uzyskać więcej informacji, zobacz [usuwanie specyfikacji wyjątków dynamicznych i noexcept](cpp-conformance-improvements-2017.md#noexcept_removal).

**Visual Studio 2017 w wersji 15.7**:

- Nowy przełącznik [/qspectre ](build/reference/qspectre.md) aby ułatwić uniknięcie przed atakami kanału po stronie wykonywania spekulacyjnego. Zobacz [krokami zaradczymi dla luki spectre w MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc/) Aby uzyskać więcej informacji.
- Nowe ostrzeżenie diagnostycznych migitation luki Spectre. Zobacz [diagnostyczne w Visual Studio 2017 w wersji 15.7 w wersji zapoznawczej 4 krokami zaradczymi dla luki](https://blogs.msdn.microsoft.com/vcblog/2018/04/20/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/) Aby uzyskać więcej informacji.
- Nową wartość dla /Zc, **użyciem**, pozwala rozwiązać raportowanie pomocy technicznej standard C++. Na przykład, gdy przełącznik jest ustawiona i kompilator jest w/STD: c ++ 17 tryb rozwija wartość **201703 L**. Zobacz [MSVC teraz poprawnie raporty __cplusplus](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/msvc-now-correctly-reports-__cplusplus/) Aby uzyskać więcej informacji.

## <a name="c-standard-library-improvements"></a>Ulepszenia standardowej biblioteki języka C++

- Drobne `basic_string` `_ITERATOR_DEBUG_LEVEL != 0` ulepszenia diagnostyki. Wyzwolenie kontroli IDL w maszynie ciągu zgłasza teraz określone zachowanie, które spowodowało wyzwolenie. Na przykład zamiast komunikatu „iterator ciągu nie umożliwia wyłuskiwania” otrzymasz komunikat „nie można wyłuskać iteratora ciągu, ponieważ jest on poza zakresem (np. iterator końca)”.
- Ulepszenie wydajności: wprowadzone `basic_string::find(char)` przeciąża wywołanie tylko `traits::find` po. Wcześniej było to wdrożone jako ogólne wyszukiwanie ciągu o długości 1.
- Ulepszenie wydajności: `basic_string::operator==` sprawdza rozmiar ciągu przed porównaniem zawartości ciągów.
- Ulepszenie wydajności: Usunięto formant sprzężenia w `basic_string`, który był trudny Optymalizator kompilatora do analizy. Należy pamiętać, że dla wszystkich krótkich ciągów wywoływanie `reserve` nadal ma niezerowy koszt bezczynności.
- Dodaliśmy \<wszelkie\>, \<string_view\>, `apply()`, `make_from_tuple()`.
- `std::vector` został sprawdzony pod kątem prawidłowości i wydajności: Tworzenie aliasów podczas wstawiania i umieszczanie jest teraz poprawnie obsługiwane jako wymagane przez Standard, gwarancja silnego wyjątku jest teraz udostępniany gdy jest to wymagane przez Standard za pomocą `move_if_noexcept()` oraz innych logik a Wstawianie/umieszczanie wykonuje mniej operacji na elementach.
- Standardowa biblioteka C++ unika obecnie wyłuskiwania swobodnych pustych wskaźników.
- Dodano \<opcjonalne\>, \<wariant\>, `shared_ptr::weak_type`, i \<cstdalign\>.
- Włączone C ++ 14 `constexpr` w `min(initializer_list)`, `max(initializer_list)`, i `minmax(initializer_list)`, i `min_element()`, `max_element()`, i `minmax_element()`.
- Ulepszone `weak_ptr::lock()` wydajności.
- Naprawiono `std::promise` operator przypisania przenoszenia, który mógł wcześniej spowodować zablokowanie kodu.
- Naprawiono błędy kompilatora przy użyciu `atomic<T*>` niejawnej konwersji `T*`.
- `pointer_traits<Ptr>` wykrywa teraz prawidłowo `Ptr::rebind<U>`.
- Naprawiono Brak `const` kwalifikator w `move_iterator` operator odejmowania.
- Naprawiono ciche Generowanie nieprawidłowego kodu dla stanowych przydzielających definiowanych przez użytkownika żądających `propagate_on_container_copy_assignment` i `propagate_on_container_move_assignment`.
- `atomic<T>` Toleruje obecnie przeciążony `operator&()`.
- Aby zwiększyć przepływność kompilatora, nagłówki standardowej biblioteki języka C++ unikają teraz, włączania deklaracji dla zbędnych funkcji wewnętrznych kompilatora.
- Nieco Ulepszona diagnostyka kompilatora dla niepoprawne `bind()` wywołania.
- Zwiększona wydajność `std::string` i `std::wstring` konstruktorów przenoszenia więcej niż trzy razy.

Aby uzyskać pełną listę biblioteki standardowej Zobacz improvments [standardowe biblioteki poprawki w programie VS 2017 RTM](https://blogs.msdn.microsoft.com/vcblog/2017/02/06/stl-fixes-in-vs-2017-rtm/).

### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 w wersji 15.3

#### <a name="c17-features"></a>Funkcji c ++ 17

Kilka dodatkowych funkcji C ++ 17 zostały zaimplementowane. Aby uzyskać więcej informacji, zobacz [Visual zgodność języka C++](cpp-conformance-improvements-2017.md#improvements_153).

#### <a name="other-new-features"></a>Inne nowe funkcje

- Zaimplementowane P0602R0 "variant i opcjonalne powinien Propagacja triviality kopiowania/przenoszenia".
- Standardowa biblioteka oficjalnie Toleruje obecnie dynamiczne RTTI wyłączone za pomocą [trakcie](build/reference/gr-enable-run-time-type-information.md) opcji. Zarówno `dynamic_pointer_cast()` i `rethrow_if_nested()` natury wymagają `dynamic_cast`, więc biblioteka standardowa teraz oznacza je jako `=delete` w obszarze **trakcie**.
- Nawet gdy RTTI dynamicznych została wyłączona za pomocą **trakcie**, "statyczne RTTI" (w formie `typeid(SomeType)`) są nadal dostępne i obsługuje kilka składników biblioteki standardowej. Biblioteka standardowa obsługuje teraz, wyłączenie to zbyt, za pośrednictwem **/D\_HAS, Health\_STATYCZNE\_RTTI = 0**. Należy zauważyć, że spowoduje to wyłączenie `std::any`, `target()` i `target_type()` funkcje elementów członkowskich `std::function`i `get_deleter()` funkcji elementu członkowskiego friend `std::shared_ptr` i `std::weak_ptr`.

#### <a name="correctness-fixes-in-visual-studio-2017-version-153"></a>Poprawność poprawki w programie Visual Studio 2017 w wersji 15.3

- Standardowa clamp teraz kontenery biblioteki ich `max_size()` do `numeric_limits<difference_type>::max()` zamiast `max()` z `size_type`. Gwarantuje to, że wynik `distance()` na iteratorach z tego kontenera jest stałego w typie zwracanym `distance()`.
- Naprawiono Brak specjalizacji `auto_ptr<void>`.
- `for_each_n()`, `generate_n()`, I `search_n()` algorytmy poprzednio kompilacja nie powiodła się Jeśli długość argumentu nie jest typem całkowitym; teraz próba przekonwertować długości niecałkowitoliczbowego Iteratory `difference_type`.
- `normal_distribution<float>` już nie emituje ostrzeżenia w standardowej bibliotece o zawężanie z podwójnej precyzji do liczb zmiennoprzecinkowych.
- Rozwiązano niektóre `basic_string` działań, które zostały porównanie z `npos` zamiast `max_size()` podczas sprawdzania, czy przekroczono maksymalny rozmiar.
- `condition_variable::wait_for(lock, relative_time, predicate)` oczekiwania przez cały czas względne w przypadku wznawiania fałszywe. Teraz po upływie jednego interwał względne czasu.
- `future::get()` teraz unieważnia `future`, ponieważ wymaga standard.
- `iterator_traits<void *>` kiedyś poważny błąd, ponieważ próbowała ona formularza `void&`; teraz prawidłowo staje się pustą strukturę, zezwalając na używanie `iterator_traits` w "jest iteratorem" SFINAE warunków.
- Kilka ostrzeżeń zgłaszanych przez Clang **- wsystem — nagłówki** zostały rozwiązane.
- Również stała "Specyfikacja wyjątku w deklaracji niezgodna poprzedniej deklaracji" zgłoszony przez Clang **- Wmicrosoft — wyjątek specyfikacja**.
- Także Naprawiono mem inicjatora listy szeregowania ostrzeżęnia zgłoszone przez Clang i C1XX.
- Nieuporządkowane kontenery nie zamienić ich hashers lub predykatów, gdy same kontenery zostały zamienione. Teraz im.
- Wiele operacji wymiany kontenera są teraz oznaczone `noexcept` (jak nasze biblioteki standardowej nigdy nie zamierza wyjątku podczas wykrywania non -`propagate_on_container_swap` alokatora niż równe niezdefiniowane zachowanie warunku).
- Wiele `vector<bool>` operacje, zostały oznaczone `noexcept`.
- Biblioteka standardowa teraz będzie wymuszać pasującego alokatora `value_type` (trybem C ++ 17) o rezygnacji z wyjście.
- Rozwiązano niektóre warunki, w przypadku, gdy samoobsługowego-range-insert into `basic_string` będzie szyfrują zawartości ciągów. (Uwaga: samoobsługowego-range-insert into wektorów nadal jest zabronione przez standardowe.)
- `basic_string::shrink_to_fit()` nie jest już jest zależna od alokatora `propagate_on_container_swap`.
- `std::decay` teraz obsługuje typy abominable funkcji (czyli funkcja typy, które są kwalifikowaną stałych nietrwałych i/lub kwalifikowana ref).
- Zmienione dyrektyw rozróżnianie wielkości liter dla prawidłowego i ukośników poprawy przenoszenia.
- Naprawiono ostrzeżenie C4061 "moduł wyliczający"*modułu wyliczającego*'w przełączniku Enum'*wyliczenie*"nie jest jawnie obsługiwany przez etykietę case". To ostrzeżenie jest wyłączone domyślnie i została ustalona jako wyjątek do biblioteki standardowej zasady ogólne ostrzeżenia. (Standardowa biblioteka **/W4** czyszczenie, ale nie jest podejmowana próba się **/Wall** czyste. Wiele ostrzeżeń wyłączone domyślnie są bardzo hałas i nie są przeznaczone do użycia w regularnych odstępach czasu.)
- Ulepszone `std::list` Debuguj testy. Listy wyboru teraz tworzyć Iteratory `operator->()`, i `list::unique()` teraz oznacza Iteratory, jako unieważnione.
- Naprawiono metaprogramowanie w używa alokatora `tuple`.

#### <a name="performancethroughput-fixes"></a>Wydajność/przepływności poprawki

- Pracował wokół interakcji z `noexcept` który uniemożliwił wbudowanie `std::atomic` implementacją na funkcje korzystające ze strukturą obsługi wyjątków (SEH).
- Zmienione, biblioteka standardowa przez wewnętrzny `_Deallocate()` funkcję, aby zoptymalizować do mniejszego kodu, dzięki któremu można wbudowana w większej liczbie miejsc.
- Zmienione `std::try_lock()` do użycia rozwinięcie pakietu zamiast rekursji.
- Ulepszone `std::lock()` algorytm uniknięcia zakleszczenia `lock()` operacji zamiast rotowania na `try_lock()` na wszystkich blokad.
- Włączono optymalizacji nazwanej zwracanej wartości w `system_category::message()`.
- `conjunction` i `disjunction` teraz wystąpienia N + 1 typów, zamiast 2N + 2 typy.
- `std::function` już nie tworzy wystąpienie programu przydzielania maszyn pomocy technicznej dla każdego typu wymazanego możliwy do wywołania, usprawnienie przepływności i zmniejszenie rozmiaru .obj w programach, które wiele odrębnych wyrażenia lambda można przekazać `std::function`.
- `allocator_traits<std::allocator>` zawiera ręcznie śródwierszowych `std::allocator` operacji, zmniejszyć rozmiar kodu w kodzie, który wchodzi w interakcję z `std::allocator` za pośrednictwem `allocator_traits` tylko (czyli w większość kodu).
- C ++ 11 interfejs minimalnych jest teraz obsługiwany przez standardową bibliotekę wywoływania `allocator_traits` bezpośrednio, zamiast zawijania alokator w Wewnętrzna klasa `_Wrap_alloc`. To zmniejsza rozmiar kod generowany dla obsługi alokatora, zwiększa możliwości optymalizatorowi przeglądanie informacji o kontenery standardowej biblioteki w niektórych przypadkach i zapewnia to lepszy proces debugowania (ponieważ spowoduje to wyświetlenie danego typu alokatora zamiast `_Wrap_alloc<your_allocator_type>` w Debuger).
- Usunięte metaprogramowanie, aby dostosować `allocator::reference`, buforów, które faktycznie nie są dozwolone do dostosowywania. (Buforów ułatwia kontenery, użyj swobodnych pustych wskaźników, ale nie ozdobnych odwołania.)
- Fronton kompilatora został prowadzone do odkodowania Iteratory debugowania w opartej na zakresie pętle, poprawę wydajności w przypadku kompilacji do debugowania.
- `basic_string` Ścieżki wewnętrznego zmniejszania dla `shrink_to_fit()` i `reserve()` nie jest już w ścieżce relokacja operacji, zmniejszyć rozmiar kodu dla wszystkich członków mutujące.
- `basic_string` Wewnętrzny rozwój ścieżka nie jest już w ścieżce `shrink_to_fit()`.
- `basic_string` Mutujące operacje teraz są rozkładane na — przydzielanie szybkiej ścieżki i alokowania funkcje powolną ścieżkę, dzięki czemu jest bardziej prawdopodobne w przypadku często spotykana Ponowna alokacja nie był śródwierszowy do obiektów wywołujących.
- `basic_string` Mutacja operacje po konstrukcji ponownie przydzielane buforów w żądanym stanie, a nie zmiany rozmiaru w miejscu. Na przykład wstawiania na początku ciągu teraz przenosi zawartości po wstawieniu dokładnie jeden raz (szczegółów lub do nowo przydzielonego buforu), zamiast dwa razy w przypadku reallocating (do nowo przydzielonego buforu, a następnie w dół).
- Operacje w przypadku wywoływania biblioteki standardowej C \<ciąg\> teraz w pamięci podręcznej `errno` adres do usunięcia powtarzanych interakcji z protokołem TLS.
- Uproszczony `is_pointer` implementacji.
- Zmianie na podstawie funkcji wyrażenie SFINAE do `struct` i `void_t`— na podstawie.
- Standardowa biblioteka algorytmów unikają teraz postincrementing Iteratory.
- Obcięcie stałej ostrzeżenia podczas korzystania z puli buforów 32-bitowych w 64-bitowych systemach.
- `std::vector` Dzięki ponownemu wykorzystaniu buforu, gdy jest to możliwe jest teraz bardziej efektywne w przypadku innych alokatora równe POCMA bez przeniesienia przypisania.

#### <a name="readability-and-other-improvements"></a>Czytelność i inne ulepszenia

- Standardowa biblioteka używa teraz C ++ 14 `constexpr` bezwarunkowo, zamiast warunkowo zdefiniowane makra.
- Standardowa biblioteka używa teraz szablony aliasów wewnętrznie.
- Korzysta teraz z biblioteki standardowej `nullptr` wewnętrznie, zamiast z `nullptr_t{}`. (Wewnętrznego użycia wartości NULL została zlikwidowana. Użycie wewnętrznego 0 jako wartość null jest oczyszczany stopniowo.)
- Korzysta teraz z biblioteki standardowej `std::move()` wewnętrznie, zamiast stylistically niewłaściwie `std::forward()`.
- Zmienione `static_assert(false, "message")` do `#error message`. Zwiększa to diagnostyki kompilatora, ponieważ `#error` natychmiast zatrzymuje kompilację.
- Standardowa biblioteka nie jest już oznacza funkcji jako `__declspec(dllimport)`. Konsolidator nowoczesnych technologii nie wymaga już to.
- Wyodrębnione SFINAE na domyślne argumenty szablonu, która upraszcza w porównaniu do typy zwracane i typy argumentów funkcji.
- Debugowania ewidencjonuje \<losowych\> teraz używać zwykle maszyny biblioteki standardowej, zamiast funkcji wewnętrznej `_Rng_abort()` której wywołać `fputs()` do **stderr**. Implementacja tej funkcji jest są zachowywane dla zgodność binarną, ale została usunięta w przyszłych wersjach niezgodne dane binarne w standardowej biblioteki.

### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 w wersji 15.5

Kilka funkcji standardowej biblioteki zostały dodane, przestarzałe lub usunięte zgodnie z standard C ++ 17. Aby uzyskać więcej informacji, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio](cpp-conformance-improvements-2017.md#improvements_155).

#### <a name="new-experimental-features"></a>Nowe funkcje eksperymentalne

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

#### <a name="performance-fixes-and-improvements"></a>Ulepszenia i poprawki wydajności

- `basic_string<char16_t>` teraz angażuje takie same `memcmp`, `memcpy`i podobnie optymalizacje, `basic_string<wchar_t>` angażuje.
- Ograniczenie Optymalizator, który uniemożliwił wskaźników funkcji miałyby śródwierszowych udostępnianych przez naszych "unikać kopiowania funkcji" Praca w Visual Studio 2015 Update 3 pracował zostały wokół, przywracanie wydajność `lower_bound(iter, iter, function pointer)`.
- Obciążenie debugowania iteratora w kolejności weryfikacji danych wejściowych `includes`, `set_difference`, `set_symmetric_difference`, i `set_union` został skrócony przez Odkodowywanie Iteratory przed zaewidencjonowaniem, order.
- `std::inplace_merge` teraz nakłada się na elementy, które znajdują się już w miejscu.
- Konstruowanie `std::random_device` już nie tworzy, a następnie niszczy `std::string`.
- `std::equal` i `std::partition` miał wątkowości Szybkie przebieg optymalizacji, co pozwoli zaoszczędzić porównanie iteratora.
- Gdy `std::reverse` jest przekazywany wskaźników do kopiowania `T`, teraz spowoduje wysłanie pisma odręcznego implementacji zwektoryzowane.
- `std::fill`, `std::equal`, i `std::lexicographical_compare` zostały prowadzone jak zostać wysłane żądanie `memset` i `memcmp` dla `std::byte` i `gsl::byte` (i inne typy wyliczeniowe przypominające znak i Wylicz klasy). Należy pamiętać, że `std::copy` wywołuje przy użyciu `is_trivially_copyable` i w związku z tym nie potrzebuję wszelkie zmiany.
- Standardowa biblioteka nie zawiera już destruktory nawiasów klamrowych pusty, którego jedynym zachowanie było typów innych niż przypadku zniszczalnych.

#### <a name="correctness-fixes-in-visual-studio-2017-version-155"></a>Poprawność poprawki w programie Visual Studio 2017 w wersji 15.5

- `std::partition` teraz wywołania razy predykatu N zamiast N + 1 godziny jako standard wymaga.
- Próbuje uniknąć Magiczna statyka w wersji 15.3 zostały naprawione w wersji 15.5.
- `std::atomic<T>` nie wymaga już `T` być konstrukcyjną domyślny.
- Algorytmy sterty trwać logarytmiczna nie jest już do potwierdzenia liniowo, że dane wejściowe są w rzeczywistości sterty po włączeniu debugowania iteratora.
- `__declspec(allocator)` teraz jest chroniony dla C1XX tylko zapobiec ostrzeżenia z Clang, który nie rozpoznaje tego declspec.
- `basic_string::npos` jest teraz dostępny jako stałą czasu kompilacji.
- `std::allocator` w trybie C ++ 17 teraz poprawnie obsługuje alokację typów nadmiernie wyrównanych, oznacza to, typów wyrównanie, w których jest większa niż `max_align_t`, chyba że wyłączone przez **/Zc:alignedNew-**.  Na przykład wektorami typów obiektów z 16 lub 32-bajtowego wyrównania będzie teraz prawidłowo wyrównany dla instrukcji SSE i AVX.

### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 wersja 15.6

- \<memory_resource>
- Podstawowe informacje dotyczące biblioteki w wersji 1
- Usuwanie przypisania polymorphic_allocator
- Usprawnienie Wnioskowanie argumentu szablonu klasy

### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 w wersji 15.7

- Obsługa równoległych algorytmów nie jest już experiemental
- nową metodę implementacji \<filesystem >
- podstawowe ciąg konwersje (częściowa Obsługa)
- std::launder()
- std::byte
- hypot(x,y,z)
- unikanie niepotrzebnych zanikania
- Funkcje matematyczne specjalne
- constexpr char_traits
- Przewodniki po odjęciu STL

Zobacz [zgodność języka Visual C++](visual-cpp-language-conformance.md) Aby uzyskać więcej informacji.

## <a name="other-libraries"></a>Inne biblioteki

### <a name="open-source-library-support"></a>Obsługa bibliotek typu open source

**Vcpkg** to narzędzie wiersza polecenia typu open source, które znacząco upraszcza proces pobierania i tworzenia biblioteki statycznej "open source" C++ i bibliotek DLL w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [vcpkg: Menedżer pakietów dla języka C++](vcpkg.md).

**Visual Studio 2017 w wersji 15.5**:

### <a name="cpprest-sdk-290"></a>Zestaw SDK CPPRest 2.9.0

CPPRestSDK, internetowy interfejs API dla wielu platform w języku C++, został zaktualizowany do wersji 2.9.0. Aby uzyskać więcej informacji, zobacz [CppRestSDK 2.9.0 jest dostępna w witrynie GitHub](https://blogs.msdn.microsoft.com/vcblog/2016/10/21/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL

- Jeszcze inny zbiór poprawek zgodności wyszukiwania nazw
- Istniejące konstruktory przenoszenia i Przenieś operatory przypisania są teraz prawidłowo oznaczone jako niezgłaszające
- Niewyłączone prawidłowe ostrzeżenie C4640 o bezpiecznym wątkowo programu w pliku atlstr.h
- Bezpiecznego wątkowo inicjowania lokalnych danych statycznych było automatycznie wyłączone w zestawie narzędzi XP podczas [używania biblioteki ATL i tworzenia biblioteki DLL]. Obecnie taka ewentualność nie zachodzi. Możesz dodać **threadsafeinit** w ustawieniach projektu, jeśli występują w wątku wymagane jest bezpieczne wątkowo inicjowanie wyłączone.

### <a name="visual-c-runtime"></a>Środowisko uruchomieniowe Visual C++

- Nowy nagłówek "cfguard.h" dla symboli ochrony przepływu sterowania.

## <a name="c-ide"></a>Środowisko IDE języka C++

- Wydajność wprowadzania zmian w konfiguracji jest teraz lepsza w przypadku natywnych projektów w języku C++ i o wiele lepsza w projektach C++/CLI. W momencie pierwszej aktywacji konfiguracja rozwiązania będzie teraz szybsza, a wszystkie kolejne aktywacje konfiguracji rozwiązania będą prawie natychmiastowe.

**Visual Studio 2017 w wersji 15.3**:

- Ponownie napisano kilka kreatorów projektu i kodów w stylu okna dialogowego podpisu.
- **Dodaj klasę** teraz powoduje bezpośrednie uruchomienie Kreatora dodawania klasy. Wszystkie inne elementy, które zostały wcześniej w tym miejscu są teraz dostępne w obszarze **Dodaj > Nowy element**.
- Projekty Win32 należą teraz w ramach **pulpitu Windows** kategorii **nowy projekt** okna dialogowego.
- **Konsoli Windows** i **aplikacja komputerowa** szablony teraz tworzenie projektów bez wyświetlania kreatora. Jest dostępny nowy **kreatora pulpitu Windows** w tej samej kategorii, który wyświetla te same opcje co stary **Aplikacja konsoli Win32** kreatora.

**Visual Studio 2017 w wersji 15.5**:

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

- Dodano nową eksperymentalną funkcję Predictive IntelliSense, która pozwala na kontekstowe filtrowanie pozycji wyświetlanych na liście elementów członkowskich. Zobacz [ulepszeń funkcji IntelliSense w języku C++ - Predictive IntelliSense i filtrowanie](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-intellisense-improvements-predictive-intellisense-filtering/)
- **Znajdź wszystkie odwołania** (Shift + F12) teraz pomaga obejść, nawet w przypadku złożonych bazach kodu. Umożliwia zaawansowane grupowanie, filtrowanie, sortowanie, wyszukiwanie w ramach wyników i (w przypadku niektórych języków) kolorowanie, dzięki czemu można uzyskać świadomość odwołaniami. Dla języka C++ nowy interfejs użytkownika zawiera informacje dotyczące tego, czy możemy odczytujemy ze zmiennej czy zapisujemy do zmiennej.
- Funkcja zmiany kropki na strzałkę IntelliSense została przeniesiona z doświadczalnych do zaawansowanych i teraz jest domyślnie włączona. Funkcje edytora **rozwiń zakresy** i **rozwiń pierwszeństwo** również zostały przeniesione z doświadczalnych do zaawansowanych.
- Eksperymentalne funkcje refaktoryzacji **Zmień podpis** i **Wyodrębnij funkcję** są teraz dostępne domyślnie.
- Eksperymentalną funkcję "Szybsze ładowanie projektu" dla projektów C++. Przy następnym otwarciu projektu w języku C++ będzie on ładować się szybciej, a przy każdym następnym będzie ładować się naprawdę szybko!
- Niektóre z tych funkcji są wspólne dla innych języków, a niektóre są specyficzne dla języka C++. Aby uzyskać więcej informacji o tych nowych funkcjach, zobacz [Announcing Visual Studio "15"](https://blogs.msdn.microsoft.com/visualstudio/2016/10/05/announcing-visual-studio-15-preview-5/).

**Visual Studio 1027 wersji 15.7**: Obsługa dodane do narzędzia ClangFormat. Aby uzyskać więcej informacji, zobacz [obsługę formatu ClangFormat w programie Visual Studio 2017](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/clangformat-support-in-visual-studio-2017-15-7-preview-1/).

## <a name="non-msbuild-projects-with-open-folder"></a>Projekty inne niż MSBuild z Otwórz Folder

Program Visual Studio 2017 wprowadzono **Otwórz Folder** funkcji, która umożliwia kodu, kompilacji i debugowania w folderze zawierające kod źródłowy, bez konieczności tworzenia żadnych rozwiązań lub projektów. Dzięki temu można łatwiej rozpocząć pracę z programem Visual Studio, nawet jeśli projekt nie jest projektem opartych na platformie MSBuild. Za pomocą **Otwórz Folder** uzyskasz dostęp do zaawansowanych kod, zrozumienie, edytowania, kompilowania i debugowania możliwości udostępnianych przez program Visual Studio już dla projektów programu MSBuild. Aby uzyskać więcej informacji, zobacz [Otwórz Folder projektów w języku C++](build/open-folder-projects-cpp.md).

- Ulepszenia obsługi polecenia Otwórz folder. Środowisko można dostosować za pomocą tych plików JSON:
  - CppProperties.json dostosowuje obsługę funkcji IntelliSense i przeglądania.
  - Tasks.json dostosowuje kroki kompilacji.
  - Launch.json dostosowuje obsługę debugowania.

**Visual Studio 2017 w wersji 15.3**:

- Ulepszona obsługa środowiska kompilacji, takie jak rozwiązań MinGW i Cygwin i Kompilatory języka alternatywne. Aby uzyskać więcej informacji, zobacz [przy użyciu rozwiązań MinGW i Cygwin przy użyciu języka Visual C++ i otwórz Folder](https://blogs.msdn.microsoft.com/vcblog/2017/07/19/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Dodano obsługę definiowania zmiennych środowiskowych globalnych i specyficznych dla konfiguracji w plikach CppProperties.json i pliku CMakeSettings.json. Te zmienne środowiskowe mogą być używane przez konfiguracje debugowania definiowane w pliku launch.vs.json i zadań podrzędnych w pliku tasks.vs.json. Aby uzyskać więcej informacji, zobacz [Dostosowywanie środowiska Visual C++ i otwórz Folder](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/customizing-your-environment-with-visual-c-and-open-folder/).
- Ulepszona obsługa generatora Ninja CMake, w tym możliwość platformami 64-bitowych.

## <a name="cmake-support-via-open-folder"></a>Obsługa CMake za pośrednictwem otwartego folderu

Program Visual Studio 2017 wprowadzono obsługę za pomocą projektów CMake, bez konwersji do MSBuild pliki projektu (.vcxproj). Aby uzyskać więcej informacji, zobacz [projektów CMake w programie Visual C++](build/cmake-projects-in-visual-studio.md). Otwarcie projektu CMake za pomocą **Otwórz Folder** automatycznie skonfiguruje środowisko dla języka C++, edytowania, kompilowania i debugowania.

- Funkcji C++ IntelliSense działa bez konieczności tworzenia pliku CppProperties.json w folderze głównym. Wraz z tym dodaliśmy nowe listy rozwijane, aby użytkownicy mogli łatwo przełączać się między konfiguracjami dostarczonymi przez pliki CMake i CppProperties.json.

- Dalsza konfiguracja jest obsługiwana przy użyciu pliku CMakeSettings.json, który znajduje się w tym samym folderze co plik CMakeLists.txt.

  ![Cmake Otwórz folder](media/cmake_cpp.png "CMake Otwórz folder")

**Visual Studio 2017 w wersji 15.3**: Obsługa dodane dla generatora Ninja narzędzia CMake.

**Visual Studio 2017 w wersji 15.5**: Obsługa dodane do importowania dostępnych pamięci podręcznych narzędzia CMake.

**Visual Studio 2017 w wersji 15.7**: Dodano obsługę narzędzia CMake 3.11, analizy kodu w projektach CMake, widok elementów docelowych w Eksploratorze rozwiązań, Opcje generowania pamięci podręcznej i kompilacja pojedynczego pliku. Aby uzyskać więcej informacji, zobacz [Obsługa CMake w programie Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) i [projektów CMake w programie Visual C++](build/cmake-projects-in-visual-studio.md).

## <a name="windows-desktop-development-with-c"></a>Programowanie aplikacji klasycznych Windows w języku C++

Zapewniamy obecnie bardziej zaawansowane środowisko instalacji oryginalnego obciążenia C++. Dodaliśmy możliwe do wybrania składniki pozwalające na zainstalowanie tylko tych narzędzi, których potrzebujesz.  Należy pamiętać, że wskazane w interfejsie użytkownika instalatora rozmiary instalacji składników nie są prawidłowe i zaniżają całkowity rozmiar instalacji.

Aby pomyślnie tworzyć projekty Win32 w obciążeniu C++ dla komputerów stacjonarnych, musisz zainstalować zarówno zestaw narzędzi, jak i zestaw SDK systemu Windows. Zainstalowanie zalecanych (zaznaczonych) składników **VC ++ 2017 narzędzi w wersji 141 (x86, x64)** i **zestawu Windows 10 SDK (10.0.nnnnn)** zapewnia, będzie to możliwe. Jeśli potrzebne narzędzia nie zostaną zainstalowane, projekty nie będą pomyślnie tworzone i kreator będzie się zawieszać.

**Visual Studio 2017 w wersji 15.5**:

(Wcześniej dostępny jako autonomiczny produkt) Visual C++ Build tools są teraz uwzględnione jako obciążenie w Instalatorze programu Visual Studio. To obciążenie instaluje tylko narzędzia wymagane do kompilowania projektów języka C++, bez konieczności instalowania programu Visual Studio IDE. Uwzględniane są zarówno w wersji 140, jak i w wersji 141 zestawy narzędzi. Narzędzi w wersji 141 zawiera najnowsze ulepszenia w programie Visual Studio 2017 w wersji 15.5. Aby uzyskać więcej informacji, zobacz [Visual Studio Build Tools zawierają teraz programu VS 2017 i zestawy narzędzi MSVC VS2015](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Programowanie dla systemu Linux przy użyciu języka C++

Popularne rozszerzenie [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) stanowi obecnie cześć programu Visual Studio. Ta instalacja zawiera wszystko, czego potrzebujesz do tworzenia i debugowania aplikacji w języku C++ działających w środowisku systemu Linux.

**Visual Studio 2017 wersja 15.2**:

Wprowadzono ulepszenia w wizualizacji do udostępniania i typ kodu między platformami. Aby uzyskać więcej informacji, zobacz [ulepszenia języka Linux C++ dla wielu platform kod, udostępnianie i typ wizualizacji](https://blogs.msdn.microsoft.com/vcblog/2017/05/10/linux-cross-platform-and-type-visualization/).

**Visual Studio 2017 w wersji 15.5**:

- Obciążenie systemu Linux została dodana obsługa **rsync** jako alternatywę dla **sftp** synchronizowania plików do zdalnej maszyny z systemem Linux.
- Dodano obsługę wielu kompilacji przeznaczonych dla mikrokontrolerów ARM. Aby włączyć tę opcję w instalacji, wybierz **programowanie dla systemu Linux przy użyciu języka C++** obciążenia i wybierz opcję dla **osadzonych i IoT rozwoju**. Spowoduje to dodanie marki i kompilatora GCC ARM cross tools kompilacji do instalacji. Aby uzyskać więcej informacji, zobacz [kompilatorów GCC dla procesorów ARM Cross kompilacji, w programie Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/10/23/arm-gcc-cross-compilation-in-visual-studio/).
- Obsługa dodane do narzędzia CMake. Teraz możesz pracować na istniejącej bazy kodu CMake bez konieczności konwertowania go do projektu programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu CMake systemu Linux](linux/cmake-linux-project.md).
- Obsługa dodane do uruchamiania zadania zdalne. Ta funkcja umożliwia uruchamianie dowolnego polecenia w systemie zdalnym, który jest zdefiniowany w Menedżerze połączeń programu Visual Studio. Zadania zdalne udostępniają również możliwość kopiowania plików do systemu zdalnego.
Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu CMake systemu Linux](linux/cmake-linux-project.md).

**Visual Studio 2017 w wersji 15.7**:

- Różne ulepszenia scenariusze obciążeń systemu Linux. Aby uzyskać więcej informacji, zobacz [ulepszenia obciążeniu C++ dla systemu Linux w systemie projektu, w oknie konsoli systemu Linux, polecenia rsync i Dołącz do procesu](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).
- Funkcja IntelliSense dla nagłówków w zdalnych połączeń z systemem Linux. Aby uzyskać więcej informacji, zobacz [technologii IntelliSense dla zdalnych nagłówków Linux](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/intellisense-for-remote-linux-headers/) i [Konfigurowanie projektu CMake systemu Linux](linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Programowanie gier w języku C++

Pełnych możliwości języka C++ można użyć do tworzenia profesjonalnych gier obsługiwanych przy użyciu zestawu funkcji DirectX lub Cocos2d.

## <a name="mobile-development-with-c-android-and-ios"></a>Tworzenie aplikacji mobilnych przy użyciu języka C++ (systemy Android i iOS)

Program Visual Studio umożliwia obecnie programowanie i debugowanie aplikacji mobilnych przeznaczonych dla systemów Android oraz iOS.

## <a name="universal-windows-apps"></a>Aplikacje uniwersalne systemu Windows

Język C++ stanowi składnik opcjonalny obciążenia Aplikacja uniwersalna systemu Windows.  Obecnie uaktualnianie projektów C++ należy wykonywać ręcznie. Po otwarciu projektu przeznaczonego dla wersji 140 platformy uniwersalnej systemu Windows (UWP) w programie Visual Studio 2017 musisz wybrać zestaw narzędzi platformy w wersji 141 na stronach właściwości projektu, jeśli nie masz zainstalowanego programu Visual Studio 2015.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nowe opcje dla języka C++ na uniwersalnej platformy Windows (UWP)
Masz teraz nowe opcje zapisywania i pakowania aplikacji w języku C++ platformy uniwersalnej Windows i Windows Store: Infrastrukturę Desktop Bridge pakietu istniejących aplikacji pulpitu lub obiektu COM dla wdrożenia za pośrednictwem Store Windows lub za pośrednictwem istniejących kanałów za pośrednictwem ładowania bezpośredniego. Nowe funkcje w systemie Windows 10 umożliwiają dodawanie funkcji platformy uniwersalnej systemu Windows do swojej aplikacji klasycznej na różne sposoby. Aby uzyskać więcej informacji, zobacz [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

**Visual Studio 2017 w wersji 15.5**: A **projekt pakietu aplikacji Windows** szablonu projektu zostanie dodany, które znacznie upraszczają pracę pakowania aplikacji klasycznych przy użyciu Desktop Bridge. Jest on dostępny w obszarze **pliku | Nowe | Projekt | Zainstalowane | Visual C++ | Platforma Universal Windows**. Aby uzyskać więcej informacji, zobacz [pakietu aplikacji przy użyciu programu Visual Studio (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Jeśli piszesz nowy kod, możesz teraz używać języka C + +/ WinRT, standardowe rzutowania języka C++ dla Windows implementowanej wyłącznie w plikach nagłówkowych. Ona umożliwia zarówno tworzenie i używanie interfejsów API środowiska wykonawczego Windows przy użyciu dowolnej zgodnych ze standardami kompilator języka C++. C + +/ WinRT ma na celu zapewnienie programistów C++ przy użyciu najwyższej klasy dostępu do nowoczesnego interfejsu Windows API. Aby uzyskać więcej informacji, zobacz [C + +/ WinRT dostępne w serwisie GitHub](https://moderncpp.com/).

Począwszy od tworzenia 17025 Windows SDK Insider Preview, C + +/ WinRT znajduje się w zestawie Windows SDK. Aby uzyskać więcej informacji, zobacz [C + +/ WinRT jest teraz dołączone do zestawu Windows SDK](https://blogs.msdn.microsoft.com/vcblog/2017/11/01/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="clangc2-platform-toolset"></a>Zestaw narzędzi platformy clang/C2

Zestaw narzędzi Clang/C2 dostarczany z programem Visual Studio 2017 obsługuje teraz **/bigobj** przełącznika, który jest kluczowy podczas kompilowania dużych projektów. Oferuje on również kilka ważnych poprawek, zarówno we frontonie, jak i zapleczu kompilatora.

## <a name="c-code-analysis"></a>Analiza kodu C++

Podstawowe narzędzia do sprawdzania kodu C++ wymuszające stosowanie [podstawowych wytycznych dotyczących języka C++](https://github.com/isocpp/CppCoreGuidelines) są obecnie dystrybuowane z programem Visual Studio. Po prostu włącz narzędzia do sprawdzania w **rozszerzenia analizy kodu** strony, strony właściwości projektu i rozszerzenia zostaną uwzględnione podczas uruchamiania analizy kodu. Aby uzyskać więcej informacji, zobacz [przy użyciu narzędzia do sprawdzania podstawowych wytycznych dotyczących języka C++](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Strona właściwości CppCoreCheck")

**Visual Studio 2017 w wersji 15.3**: Obsługa dodane do reguł związanych z zarządzaniem zasobami.

**Visual Studio 2017 w wersji 15.5**: Nowe funkcje sprawdzania podstawowych wytycznych dotyczących języka C++ obejmuje poprawności wskaźnika inteligentnego, poprawnego użycia inicjatorów globalnych i użycia flag konstrukcji, takich jak `goto` i zły rzutowania.

Niektóre numery ostrzeżeń, które można znaleźć w wersji 15.3, nie są już dostępne w wersji 15.5. Ostrzeżenia te zostały zastąpione bardziej szczegółowymi operacjami sprawdzania.

**Visual Studio 2017 w wersji 15.6**:

- Obsługa dodane do pojedynczego pliku analiz i poprawę wydajności analizy w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [statycznej analizy ulepszenia dla języka C++ dla Visual Studio 2017 15.6 w wersji zapoznawczej 2](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/)

**Visual Studio 2017 w wersji 15.7**:

- Dodane do pomocy technicznej [/ analyze: ruleset](build/reference/analyze-code-analysis.md) umożliwia określenie reguł analizy kodu, które można uruchomić.
- Dodano dodatkowe reguły z podstawowych wytycznych dotyczących języka C++ obsługę.  Aby uzyskać więcej informacji, zobacz [przy użyciu narzędzia do sprawdzania podstawowych wytycznych dotyczących języka C++](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing"></a>Testowanie jednostek

**Visual Studio 2017 w wersji 15.5**:

Adapter testowy Google i Boost.Test karty są teraz dostępne jako składniki **programowanie aplikacji klasycznych w języku C++** obciążenia i są zintegrowane z **Eksplorator testów**. Obsługa narzędzia CTest jest dodawany do projektów Cmake (za pomocą otwartego folderu), mimo że pełna integracja z **Eksplorator testów** nie jest jeszcze dostępna. Aby uzyskać więcej informacji, zobacz [pisanie testów jednostkowych dla języka C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp).

**Visual Studio 2017 w wersji 15.6**:

- Dodano obsługę dynamicznej biblioteki Boost.Test pomocy technicznej.
- Szablon elementu Boost.Test jest teraz dostępna w środowisku IDE.

Aby uzyskać więcej informacji, zobacz [Boost.Test Unit Testing: Dynamiczna obsługa bibliotek i nowego szablonu elementu](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/boost-test-unit-testing-dynamic-library-support-and-new-item-template/).

**Visual Studio 2017 w wersji 15.7**:

[Funkcja CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) obsługiwane dodane dla projektów testów jednostkowych C++. Aby uzyskać więcej informacji, zobacz [ogłoszenie CodeLens dla testów jednostkowych C++](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/announcing-codelens-for-c-unit-testing/).

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

  Należy pamiętać, że jeśli Twoje przechwycenia za pomocą wywołania pełny stos przechwytywania włączone (**programu Visual Studio > Narzędzia > Opcje** w obszarze **Graphics Diagnostics**), kontekst każdego zdarzenia zmiany może być szybko ustalona i inspekcji w obrębie projektu programu Visual Studio.

- **Statystyka interfejsu API:** Wyświetl podsumowanie wysokiego poziomu użycia interfejsu API w sieci ramki. Może to być przydatne w odnajdywania wywołań, mogą nie okazuje się, że wprowadzasz w ogóle lub wywołania, które wykonujesz zbyt dużej ilości. W tym oknie jest dostępna za pośrednictwem **Widok > Statystyka interfejsu API** w analizatora grafiki programu Visual Studio.

  ![Statystyka interfejsu API](media/api-stats.png)

- **Statystyki pamięci:** Wyświetl, ile pamięci sterownik jest przydzielanie zasobów tworzenie w ramce. W tym oknie jest dostępna za pośrednictwem **Widok > Statystyki pamięci** w **analizatora grafiki programu Visual Studio**. Dane mogą być kopiowane do pliku CSV do wyświetlenia w arkuszu kalkulacyjnym, klikając prawym przyciskiem myszy i wybierając pozycję **Kopiuj wszystko**.

  ![Statystyka pamięci](media/memory-stats.png)

- **Weryfikacja ramki:** Nowa lista błędów i ostrzeżeń pozwala łatwo można przejść do listy zdarzeń oparte na potencjalnych problemów wykrytych przez warstwę debugowania Direct3D. Kliknij przycisk **Widok > Weryfikacja ramki** w analizatora grafiki programu Visual Studio, aby otworzyć okno. Następnie kliknij przycisk **Uruchom weryfikację** można rozpocząć analizy. Może upłynąć kilka minut, w zależności od złożoności ramki.

  ![Weryfikacja ramki](media/frame-validation.png)

- **Analiza klatek D3D12:** Użyj analizy klatek do analizowania wydajności wywołań rysowania kierowanych eksperymentami "co jeśli". Przejdź na kartę analizy klatek i przeprowadzać analizę, aby wyświetlić raport. Aby uzyskać więcej informacji, obejrzyj [GoingNative 25: Analiza klatek grafiki programu Visual Studio](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) wideo.

  ![Analiza klatek](media/frame-analysis.png)

- **Ulepszenia użycia procesora GPU:** Otwórz ślady za pośrednictwem programu profilującego użycie procesora GPU w usłudze Visual Studio przy użyciu widoku GPU lub narzędziu Analizator wydajności Windows (WPA) dla bardziej szczegółowej analizy. Jeśli masz zestaw narzędzi wydajności Windows, które zostały zainstalowane będzie dwa hiperłącza, jeden dla WPA i innych widoku procesora GPU w prawym dolnym rogu omówienie sesji.

  ![Użycie procesora GPU](media/gpu-usage.png)

  Ślady otwierane w widoku GPU za pośrednictwem tego łącza pomocy technicznej synchronizowane powiększanie i przesuwanie na osi czasu między VS i wyświetlanie procesora GPU. Pole wyboru w programie VS jest używana do kontroli, czy włączona jest synchronizacja, czy nie.

  ![Wyświetl procesora GPU](media/gpu-view.png)
