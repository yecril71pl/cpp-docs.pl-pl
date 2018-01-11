---
title: "Nowości w języku Visual C++ w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 11/15/2017
ms.technology: vs-ide-general
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f266e17e88118e41550da68e77434f52b3456261
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="whats-new-for-visual-c-in-includevsdev15mdmiscincludesvsdev15mdmd"></a>Nowości w języku Visual C++ w[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)]

[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)]udostępnia wiele aktualizacji i poprawki dla środowiska Visual C++. Wprowadzeniu stałej ponad 250 usterek i zgłoszone problemy w narzędzi i kompilatora, wiele przesyłanych przez klientów za pośrednictwem [zgłosić Problem](/visualstudio/how-to-report-a-problem-with-visual-studio-2017) i [Podaj sugestię](https://visualstudio.uservoice.com/) opcje w obszarze **Prześlij opinię** . Dziękujemy za zgłaszanie usterek! Aby uzyskać więcej informacji dotyczących nowości we wszystkich programu Visual Studio, odwiedź [nowości [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] ](https://go.microsoft.com/fwlink/p/?linkid=834481).

<!--The compiler and tools version number in [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] is 14.10.24629. -->

## <a name="c-compiler"></a>kompilator C++

### <a name="c-conformance-improvements"></a>Ulepszenia zgodność języka C++

W tej wersji zaktualizowaliśmy standardową bibliotekę i kompilator języka C++ o rozszerzoną obsługę funkcji języka C ++ 11 i C ++ 14, a także wstępną obsługę niektórych funkcji, które mają zostać uwzględnione w standardowym języku C ++ 17. Aby uzyskać szczegółowe informacje, zobacz [ulepszenia zgodność języka C++ w programie Visual Studio 2017](cpp-conformance-improvements-2017.md).

### <a name="new-compiler-options"></a>Nowe opcje kompilatora

- **/STD:c ++ 14** i **/std:c ++ najnowsze**: tych opcji kompilatora umożliwiają wyrazić zgodę na określonych wersji ISO C++ język w projekcie programowania. Aby uzyskać więcej informacji, zobacz [/std (Określ wersję Standard języka)](build/reference/std-specify-language-standard-version.md). Nowy projekt standardowych funkcji jest chroniony przez większość **/std:c ++ najnowsze** opcji.

   **Visual Studio 2017 wersji 15 ustęp 3**:

   **/Std:c ++ 17** opcji udostępnia zestaw funkcji C ++ 17 implementowane przez kompilator języka Visual C++. Ta opcja powoduje wyłączenie kompilator i biblioteki standardowej obsługi dla funkcji, które zostały zmienione lub nowego w wersji aktualizacji pracy roboczą i usterką standardu C++ po C ++ 17. Aby włączyć te funkcje, należy użyć **/std:c ++ najnowsze**.

   **Visual Studio 2017 wersji 15,5 cala**:

   Kompilator Visual C++ obsługuje około 75% funkcje, które są nowością w programie C ++ 17, strukturalnych powiązań, w tym `constexpr` wyrażeń lambda, `if constexpr`, fold wbudowane zmienne, wyrażenia i dodawanie `noexcept` do typu systemu. Są one dostępne w obszarze **/std:c ++ 17** opcji. Aby uzyskać więcej informacji, zobacz [ulepszenia zgodność języka C++ w programie Visual Studio 2017 r.](cpp-conformance-improvements-2017.md)

- [/ ograniczająca-](build/reference/permissive-standards-conformance.md): Włącz wszystkie standardy strict zgodność-opcje kompilatora i wyłączyć większości rozszerzenia kompilatora specyficzne dla firmy Microsoft (ale nie `__declspec(dllimport)`, na przykład). Ta opcja jest domyślnie wyłączona, ale będzie na domyślnie w pewnym momencie w przyszłości.

   **Visual Studio 2017 wersji 15,5 cala**:

   **/ Ograniczająca-** tryb zgodności obsługuje częściowe dwufazowego nazw wyszukiwania. Aby uzyskać więcej informacji, zobacz [ulepszenia zgodność języka C++ w programie Visual Studio 2017](cpp-conformance-improvements-2017.md).

- [/Diagnostics](build/reference/diagnostics-compiler-diagnostic-options.md): Włącz wyświetlania numer wiersza, numer wiersza i kolumny, lub numer wiersza i kolumny i karetki w wierszu kodu, w którym zostało znalezione diagnostycznych błąd lub ostrzeżenie.

- [/Debug:fastlink](build/reference/debug-generate-debug-info.md): Włącz do 30% szybciej konsolidowania przyrostowego razy (vs. Visual Studio 2015) przed kopiowaniem wszystkie informacje w pliku PDB debugowania. Zamiast tego pliku PDB wskazuje informacji debugowania dla obiekt i biblioteki plików używany do tworzenia pliku wykonywalnego. Zobacz [cykl w programie VS "15" z /Debug:fastlink kompilacji C++ szybciej](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-build-cycle-in-vs-15-with-debugfastlink/) i [zalecenia dotyczące szybkości kompilacji C++ w programie Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2016/10/26/recommendations-to-speed-c-builds-in-visual-studio/).

- [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)]Umożliwia korzystanie z [/SDL](build/reference/sdl-enable-additional-security-checks.md) z [/ await](build/reference/await-enable-coroutine-support.md). Firma Microsoft usunęła [/RTC](build/reference/rtc-run-time-error-checks.md) ograniczenia z procedury wspólnej.

### <a name="codegen-security-diagnostics-and-versioning"></a>CODEGEN, zabezpieczeń, diagnostyki i kontroli wersji

Tej wersji wprowadzono kilka ulepszeń optymalizacji, generowanie kodu, przechowywanie wersji zestawu narzędzi i diagnostyki. Do istotnych ulepszeń należą:

- Ulepszone generowanie kodu pętli: obsługa automatycznej wektoryzacji dzielenia stałych liczb całkowitych, lepsza identyfikacja wzorców funkcji memset.
- Ulepszone zabezpieczenia kodu: ulepszono emisji diagnostyki kompilatora przepełnienie buforu, i [/GUARD: CF](build/reference/guard-enable-control-flow-guard.md) teraz osłony przełącznika instrukcji, które Generowanie spisów przeskoku.
- Przechowywanie wersji: Wartość wbudowane makro preprocesora  **\_MSC\_VER** jest teraz monotonicznie aktualizowany po każdej aktualizacji narzędzi programu Visual C++. Aby uzyskać więcej informacji, zobacz [kompilatora Visual C++ w wersji](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/).
- Nowy układ zestawu narzędzi: kompilacji powiązane narzędzi i kompilatora ma nowej struktury lokalizacji i katalog na komputerze deweloperskim. Nowy układ umożliwia side-by-side instalacji wielu wersji kompilatora. Aby uzyskać więcej informacji, zobacz [układ narzędzi kompilatora Visual Studio "15"](https://blogs.msdn.microsoft.com/vcblog/2016/10/07/compiler-tools-layout-in-visual-studio-15/).
- Ulepszona diagnostyka: W oknie danych wyjściowych zawiera obecnie kolumnę gdzie występuje błąd. Aby uzyskać więcej informacji, zobacz [ulepszenia diagnostyki kompilatora C++ w programie VS "15" Preview 5](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-compiler-diagnostics-improvements-in-vs-15-rc/).
- Korzystając z procedury wspólnej, eksperymentalne — słowo kluczowe **yield** (dostępnych w ramach **/ await** opcji) została usunięta. Kod powinien zostać zaktualizowany do użycia `co_yield` zamiast tego. Więcej informacji można znaleźć na [blogu zespołu Visual C++](https://blogs.msdn.microsoft.com/vcblog/).

**Visual Studio 2017 wersji 15 ustęp 3**:

Dodatkowe ulepszenia diagnostyki kompilatora. Aby uzyskać więcej informacji, zobacz [diagnostycznych ulepszeń w programie Visual Studio 2017 15.3.0](https://blogs.msdn.microsoft.com/vcblog/2017/07/21/diagnostic-improvements-in-vs2017-15-3-0/).

**Visual Studio 2017 wersji 15,5 cala**:

Visual C++ runtime wydajności w dalszym ciągu poprawy z powodu lepszą jakość wygenerowanego kodu. Oznacza to, czy po prostu ponownie skompilować kod, a aplikacja będzie działać szybciej. Niektóre optymalizacje kompilatora są całkowicie nowe, takich jak vectorization warunkowego magazynów skalarne łączenie wywołań `sin(x)` i `cos(x)` do nowego `sincos(x)`i eliminacja nadmiarowe instrukcji Optymalizator SSA. Inne optymalizacje kompilatora są ulepszenia istniejących funkcji, takich jak Algorytm heurystyczny wektoryzowania wyrażenia warunkowego, lepszej optymalizacji pętli i codegen min/max float. Konsolidator ma nowy i szybsze **/OPT: ICF** implementacji, co może skutkować 9% połączyć speedups czasu, a istnieją inne poprawki wydajności w konsolidowania przyrostowego. Aby uzyskać więcej informacji, zobacz [od (optymalizacje)](https://docs.microsoft.com/en-us/cpp/build/reference/opt-optimizations) i [/incremental (łącze przyrostowo)](https://docs.microsoft.com/en-us/cpp/build/reference/incremental-link-incrementally).

Visual C++ obsługuje jest AVX firmy Intel-512, łącznie z instrukcjami długość wektora nowych funkcji w AVX 512 doprowadzić rejestrów szeroki 128 - i 256-bitowego.

[/Zc:noexceptTypes-](build/reference/zc-noexcepttypes.md) opcji może służyć do powrotu do języka C ++ 14 wersji `noexcept` podczas w trybie C ++ 17 ogólnie. Dzięki temu można zaktualizować kodu źródłowego z języków C ++ 17, bez konieczności ponownego zapisania wszystkie Twoje `throw()` kodu w tym samym czasie. Aby uzyskać więcej informacji, zobacz [usuwania specyfikacji wyjątków dynamicznych i noexcept](cpp-conformance-improvements-2017.md#noexcept_removal).

## <a name="c-standard-library-improvements"></a>Ulepszenia standardowa biblioteka C++

- Drobne `basic_string` `_ITERATOR_DEBUG_LEVEL != 0` ulepszenia diagnostyki. Wyzwolenie kontroli IDL w maszynie ciągu zgłasza teraz określone zachowanie, które spowodowało wyzwolenie. Na przykład zamiast komunikatu „iterator ciągu nie umożliwia wyłuskiwania” otrzymasz komunikat „nie można wyłuskać iteratora ciągu, ponieważ jest on poza zakresem (np. iterator końca)”.
- Zwiększenie wydajności: wprowadzone `basic_string::find(char)` overloads tylko wywołania `traits::find` po. Wcześniej było to wdrożone jako ogólne wyszukiwanie ciągu o długości 1.
- Zwiększenie wydajności: `basic_string::operator==` przed porównaniem ciągi są zawartości sprawdza rozmiar ciągu.
- Zwiększenie wydajności: usunięty formant sprzężenia w `basic_string`, które było trudne analizowanie Optymalizator kompilatora. Należy pamiętać, że dla wszystkich ciągów krótkich wywoływania `reserve` nadal ma niezerową koszt nic nie rób.
- Dodaliśmy \<żadnych\>, \<string_view\>, `apply()`, `make_from_tuple()`.
- `std::vector`zostały zmienić prawidłowości i wydajności: aliasów podczas wstawiania i umieszczanie poprawnie jest teraz obsługiwany jako wymagane przez standardowe, wyjątek silnej gwarancji jest teraz udostępniany na żądanie przez Standard za pośrednictwem `move_if_noexcept()` i innych logiki i wstawiania/umieszczanie wykonywać operacje na elementach mniej.
- Standardowa biblioteka C++ unika teraz dereferencji ozdobne wskaźniki o wartości null.
- Dodaje \<opcjonalne\>, \<variant\>, `shared_ptr::weak_type`, i \<cstdalign\>.
- Włączone C ++ 14 `constexpr` w `min(initializer_list)`, `max(initializer_list)`, i `minmax(initializer_list)`, i `min_element()`, `max_element()`, i `minmax_element()`.
- Ulepszone `weak_ptr::lock()` wydajności.
- Stałe `std::promise` operator przypisania przenoszenia, która może spowodować wcześniej kod, aby zablokować nieustannego.
- Błędy kompilatora przy użyciu stałej `atomic<T*>` niejawnej konwersji `T*`.
- `pointer_traits<Ptr>`teraz, prawidłowo wykrywane `Ptr::rebind<U>`.
- Stałe braku `const` kwalifikator w `move_iterator` operator odejmowania.
- Stałe ciche Generowanie nieprawidłowego kodu dla stanowych allocators zdefiniowane przez użytkownika —, żądanie `propagate_on_container_copy_assignment` i `propagate_on_container_move_assignment`.
- `atomic<T>`teraz zaakceptować przeciążony `operator&()`.
- W celu zwiększenia przepływności kompilatora, nagłówki standardowa biblioteka C++ teraz uniknąć, włączając deklaracje dla funkcje wewnętrzne kompilatora niepotrzebne.
- Nieznacznie poprawia diagnostyki kompilatora dla niepoprawne `bind()` wywołania.
- Zwiększona wydajność `std::string` i `std::wstring` przenieść konstruktorów przez więcej niż trzy razy.

Aby uzyskać pełną listę biblioteki standardowej Zobacz improvments [standardowej biblioteki poprawki w VS 2017 RTM](https://blogs.msdn.microsoft.com/vcblog/2017/02/06/stl-fixes-in-vs-2017-rtm/).

### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 wersji 15 ustęp 3

#### <a name="c17-features"></a>C ++ 17 funkcji

Zastosowano kilka dodatkowych funkcji C ++ 17. Aby uzyskać więcej informacji, zobacz [Visual zgodność języka C++](cpp-conformance-improvements-2017.md#improvements_153).

#### <a name="other-new-features"></a>Inne nowe funkcje

- Zaimplementowane P0602R0 "variant i opcjonalne powinien propagację triviality skopiowania/przeniesienia".
- Standardowa biblioteka teraz oficjalnie zaakceptować RTTI dynamiczne są wyłączone przez [czasie](build/reference/gr-enable-run-time-type-information.md) opcji. Zarówno `dynamic_pointer_cast()` i `rethrow_if_nested()` z założenia wymagają `dynamic_cast`, więc biblioteki standardowej teraz oznacza je jako `=delete` w obszarze **czasie**.
- Nawet gdy RTTI dynamicznych zostało wyłączone za pomocą **czasie**, "statyczne RTTI" (w postaci `typeid(SomeType)`) jest nadal dostępny i obsługuje kilka składników biblioteki standardowej. Standardowa biblioteka obsługuje teraz wyłączenie to, za pomocą **/D\_HAS\_STATYCZNYCH\_RTTI = 0**. Należy pamiętać, że to spowoduje wyłączenie `std::any`, `target()` i `target_type()` funkcji Członkowskich `std::function`i `get_deleter()` friend funkcji członkowskiej klasy `std::shared_ptr` i `std::weak_ptr`.

#### <a name="correctness-fixes-in-visual-studio-2017-version-153"></a>Poprawność poprawki w Visual Studio 2017 wersji 15 ustęp 3

- Standardowa biblioteka kontenery teraz ograniczenie ich `max_size()` do `numeric_limits<difference_type>::max()` zamiast `max()` z `size_type`. Gwarantuje to, że wynik `distance()` na Iteratory z tego kontenera jest można przedstawić w zwracany typ `distance()`.
- Stałe Brak specjalizacji `auto_ptr<void>`.
- `for_each_n()`, `generate_n()`, I `search_n()` algorytmy wcześniej kompilacja nie powiodła się, jeśli długość argumentu nie jest typem całkowitym; teraz podejmować przekonwertować długości niecałkowity Iteratory `difference_type`.
- `normal_distribution<float>`już nie emituje ostrzeżenia w standardowej bibliotece o zawężanie z typu double na float.
- Usunięto niektóre `basic_string` działań, które zostały porównanie z `npos` zamiast `max_size()` podczas sprawdzania dostępności maksymalny rozmiar overflow.
- `condition_variable::wait_for(lock, relative_time, predicate)`oczekiwania przez cały czas względny w przypadku wznawiania fałszywe. Teraz będzie czekać przez tylko jeden interwał względne czasu.
- `future::get()`teraz unieważnia `future`, ponieważ wymaga standardowego.
- `iterator_traits<void *>`używane jako poważny błąd, ponieważ podjęto próbę formularza `void&`; teraz prawidłowo staje się puste struktury, aby umożliwić korzystanie z `iterator_traits` w "jest iteratora" techniki SFINAE warunki.
- Ostrzeżenia zgłoszone przez Clang **- wsystem — nagłówki** zostały usunięte.
- Usunięto również "Specyfikacja wyjątku w deklaracji niezgodność z poprzednią deklaracją" zgłoszone przez Clang **- Wmicrosoft-wyjątku spec**.
- Usunięto również mem inicjator listy ostrzeżeń porządkowania zgłaszanych przez Clang i C1XX.
- Kontenery nieuporządkowaną nie wymiany ich hashers lub predykaty, gdy same kontenery zostały zamienione. Teraz je.
- Wiele operacji wymiany kontenera zostały oznaczone `noexcept` (zgodnie z naszym biblioteki standardowej nigdy nie zamierza zgłoszenia wyjątku podczas wykrywania nienależących`propagate_on_container_swap` bez przydzielania równości niezdefiniowane zachowanie warunku).
- Wiele `vector<bool>` operacje zostały oznaczone `noexcept`.
- Biblioteki standardowej teraz będzie wymuszać pasującego alokatora `value_type` (tryb C ++ 17) z kreskowania ucieczki rezygnacji z.
- Stałe niektóre warunki, w przypadku, gdy niezależne-range-insert into `basic_string` czy szyfrują zawartość ciągów. (Uwaga: niezależne-range-insert into wektory nadal jest zabronione przez standardowego.)
- `basic_string::shrink_to_fit()`nie dotyczy programu przydzielania `propagate_on_container_swap`.
- `std::decay`teraz obsługuje typy funkcji abominable (tj. Funkcja typy, które są cv kwalifikowaną lub kwalifikowaną ref).
- Zmienione dyrektyw prawidłowego uwzględniana wielkość liter i ukośniki, poprawy przenośność.
- Ostrzeżenie C4061 stałej "moduł wyliczający"*modułu wyliczającego*"w switch wyliczenia"*wyliczenie*"nie jest jawnie obsługiwany przez etykietę case". To ostrzeżenie jest wyłączone domyślnie i został rozwiązany jako wyjątek do biblioteki standardowej zasady ogólne ostrzeżenia. (Standardowa biblioteka jest **/W4** czyszczenie, ale nie jest podejmowana próba można **/ścian** czyste. Wiele poza domyślnie ostrzeżenia są bardzo dużo i nie są przeznaczone do użycia na bieżąco.)
- Ulepszone `std::list` debugowania kontroli. Lista wyboru teraz Iteratory `operator->()`, i `list::unique()` teraz oznacza Iteratory jako unieważnione.
- Stałe metaprogramowania w używa alokatora `tuple`.

#### <a name="performancethroughput-fixes"></a>Wydajność/przepływności poprawki

- Przepracowany wokół interakcji z `noexcept` który uniemożliwił ze śródwierszowaniem `std::atomic` implementacją na funkcje programu wykorzystujące strukturalnych obsługi wyjątków (SEH).
- Zmienione biblioteki standardowej obiektu wewnętrznego `_Deallocate()` funkcji w celu zoptymalizowania na mniejsze kod, dzięki któremu można wbudować w większej liczbie miejsc.
- Zmienione `std::try_lock()` umożliwia rozwinięcie pakietu zamiast rekursji.
- Ulepszone `std::lock()` algorytm unikania zakleszczenie w celu użycia `lock()` operacje zamiast Obracająca na `try_lock()` na wszystkich blokad.
- Włączono optymalizację nazwanych wartości zwracanej w `system_category::message()`.
- `conjunction`i `disjunction` teraz utworzyć wystąpienia N + 1 typów, zamiast 2N + 2 typów.
- `std::function`nie tworzy przydzielania maszyny pomocy technicznej dla każdego wymazane typu można wywołać, ulepszanie przepływności i zmniejszenie rozmiaru .obj w programach, które przekazać wiele różnych wyrażeń lambda do `std::function`.
- `allocator_traits<std::allocator>`zawiera wbudowane ręcznie `std::allocator` operacji zmniejszenia rozmiaru kodu w kodzie, który współdziała z `std::allocator` za pośrednictwem `allocator_traits` tylko (to znaczy w większość kodu).
- C ++ 11 alokatora minimalny interfejs jest teraz obsługiwany przez biblioteki standardowej wywoływania `allocator_traits` bezpośrednio, zamiast zawijania programu przydzielania w Wewnętrzna klasa `_Wrap_alloc`. To zmniejsza rozmiar kodu wygenerowany dla pomocy technicznej programu przydzielania, zwiększa możliwości Optymalizator Przyczyna o biblioteki standardowej kontenery w niektórych przypadkach i zapewnia lepsze debugowania (ponieważ spowoduje to wyświetlenie danego typu alokatora zamiast `_Wrap_alloc<your_allocator_type>` w Debuger).
- Usunięte metaprogramowania, aby uzyskać dostosowane `allocator::reference`, które allocators — faktycznie nie są dozwolone dostosować. (Allocators — ułatwia kontenery, użyj wskaźników ozdobne, ale nie ozdobne odwołań.)
- Kompilator frontonu został jednocześnie dekodowania Iteratory debugowania w opartej na zakresie dla pętle, poprawia wydajność debugowania kompilacji.
- `basic_string` Wewnętrzny zmniejszania rozmiaru ścieżki dla `shrink_to_fit()` i `reserve()` nie jest już w ścieżce ponowne przydzielanie operacji zmniejszenia rozmiaru kodu dla wszystkich członków mutating.
- `basic_string` Wewnętrzny wzrostu ścieżka nie jest już w ścieżce `shrink_to_fit()`.
- `basic_string` Mutacja operacji teraz są rozkładane na — przydzielanie szybkiej ścieżki i alokowania funkcje powolną ścieżkę, dzięki czemu częściej w typowych przypadkach realokacja nie być wbudowane w obiekty wywołujące.
- `basic_string` Mutacja operacji teraz konstrukcja przydzielić buforów w żądanym stanie zamiast zmiany rozmiaru w miejscu. Na przykład wstawianie na początku ciąg teraz przenosi zawartości po wstawieniu dokładnie raz (w dół lub w buforze nowoprzydzielonych), zamiast dwukrotnie w tym przypadku reallocating (nowoprzydzielonych buforu, a następnie w dół).
- Operacje wywoływania biblioteki standardowe C w \<ciąg\> teraz pamięci podręcznej `errno` adres do usunięcia powtarzane interakcji z protokołem TLS.
- Uproszczone `is_pointer` implementacji.
- Zakończono zmiana funkcji techniki SFINAE wyrażeń do `struct` i `void_t`— na podstawie.
- Standardowa biblioteka algorytmów uniknąć teraz postincrementing Iteratory.
- Ostrzeżenia obcięcie stałej, używając 32-bitowych allocators — w systemach 64-bitowych.
- `std::vector`przypisania przenoszenia jest teraz bardziej efektywne w przypadku innych niż alokatora równości z systemem innym niż POCMA przez ponowne użycie buforu, gdy jest to możliwe.

#### <a name="readability-and-other-improvements"></a>Zwiększyć czytelność, a inne ulepszenia

- Standardowa biblioteka korzysta z języka C ++ 14 `constexpr` bezwarunkowo, zamiast warunkowo zdefiniowane makra.
- Standardowa biblioteka używa teraz szablonów aliasów wewnętrznie.
- Standardowa biblioteka używa teraz `nullptr` wewnętrznego, zamiast z `nullptr_t{}`. (Wewnętrzny użycie wartości NULL została zlikwidowana. Użycie wewnętrznego 0 jako wartość null jest oczyszczany stopniowo.)
- Standardowa biblioteka używa teraz `std::move()` wewnętrznego, zamiast stylistically niewłaściwie korzysta z `std::forward()`.
- Zmienione `static_assert(false, "message")` do `#error message`. Zwiększa to diagnostyki kompilatora, ponieważ `#error` natychmiastowe zatrzymanie kompilacji.
- Standardowa biblioteka oznacza już nie działa jako `__declspec(dllimport)`. Nowoczesny konsolidatora technologii nie wymaga już to.
- Wyodrębnionego techniki SFINAE do domyślnych argumentów szablonu, który upraszcza w porównaniu do zwrócenia typów i typy argumentów funkcji.
- Sprawdza debugowania \<losowe\> teraz używać maszyn zwykle biblioteki standardowej, zamiast funkcji wewnętrznej `_Rng_abort()` której wywołać `fputs()` do **stderr**. Implementacja tej funkcji jest zachowywane dla zgodności plików binarnych, ale została usunięta w następnej wersji biblioteki standardowej binarnie niezgodna.

### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 wersji 15,5 cala

Kilka funkcje standardowej biblioteki zostały dodane, przestarzałe lub usunięte zgodnie z języka C ++ 17 standard. Aby uzyskać więcej informacji, zobacz [ulepszenia zgodność języka C++ w programie Visual Studio](cpp-conformance-improvements-2017.md#improvements_155).

#### <a name="new-experimental-features"></a>Nowe funkcje eksperymentalne

- Obsługa eksperymentalna następujących algorytmów równoległych:
  - `all_of`
  - `any_of`
  - `for_each`
  - `for_each_n`
  - `none_of`
  - `reduce`
  - `replace`
  - `replace_if`
  - `sort`
- Podpisy dla następujących algorytmów równoległych zostały dodane, ale nie została zrównoleglona w tej chwili; Profilowanie pokazanego żadnych korzyści parallelizing algorytmów tylko przenieść lub permute — elementy:
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

#### <a name="performance-fixes-and-improvements"></a>Ulepszenia i wydajności

- `basic_string<char16_t>`teraz angażujący takie same `memcmp`, `memcpy`i podobne optymalizację, które `basic_string<wchar_t>` angażujący.
- Ograniczenie Optymalizator, który uniemożliwił wskaźników funkcji z możliwości wbudowanego udostępnianych przez naszych "unikać kopiowania funkcji" pracy w Visual Studio 2015 Update 3 zostały działał wokół, przywracanie wydajność `lower_bound(iter, iter, function pointer)`.
- Obciążenie debugowania iteratora do weryfikacji kolejność danych wejściowych w celu `includes`, `set_difference`, `set_symmetric_difference`, i `set_union` został zmniejszony przez Odkodowywanie Iteratory przed zaewidencjonowaniem kolejności.
- `std::inplace_merge`teraz nakłada się na elementy, które już znajdują się w pozycji.
- Konstruowanie `std::random_device` już tworzy, a następnie niszczy `std::string`.
- `std::equal`i `std::partition` miał wątkowość skok przebiegu optymalizacji, która zapisuje porównania iteratora.
- Gdy `std::reverse` jest przekazywany wskaźników do trivially copyable `T`, teraz wyśle odręcznie zwektoryzowane implementacji.
- `std::fill`, `std::equal`, i `std::lexicographical_compare` zostały nauczanych sposób wysłania do `memset` i `memcmp` dla `std::byte` i `gsl::byte` (i innych wyliczeniach typu char i Wylicz klasy). Należy pamiętać, że `std::copy` wywołuje przy użyciu `is_trivially_copyable` i w związku z tym nie wymagają żadnych zmian.
- Standardowa biblioteka nie zawiera już którego tylko zachowanie było typów innych niż — trivially — które można zniszczyć destruktory puste nawiasy.

#### <a name="correctness-fixes-in-visual-studio-2017-version-155"></a>Poprawność poprawki w Visual Studio 2017 wersji 15,5 cala

- `std::partition`teraz razy predykatu N zamiast N + 1 godziny jako standard jest wymagane.
- Naprawiono prób, aby uniknąć magicznych danych statycznych w wątkach w wersji 15 ustęp 3 w wersji 15,5 cala.
- `std::atomic<T>`nie wymaga już `T` jako domyślne umożliwia konstrukcji.
- Sterty algorytmów trwać logarytmicznej już do potwierdzenia czasu liniowego, czy dane wejściowe są w rzeczywistości sterty włączenie debugowania iteratora.
- `__declspec(allocator)`jest teraz chroniony dla C1XX zapobiec ostrzeżenia Clang, którego nie rozpoznaje tego declspec.
- `basic_string::npos`jest teraz dostępna jako stałą czasu kompilacji.
- `std::allocator`w trybie C ++ 17 teraz prawidłowo alokacji uchwytów nadmiernie wyrównane typy, oznacza to, typy którego wyrównanie jest większa niż `max_align_t`, chyba że zostaną wyłączone przez **/Zc:alignedNew-**.  Na przykład wektory obiektów z wyrównaniem 16 i 32-bajtowych będzie teraz prawidłowo wyrównać instrukcje SSE i AVX.

## <a name="other-libraries"></a>Inne biblioteki

### <a name="open-source-library-support"></a>Obsługa biblioteki typu open source

**Vcpkg** to narzędzie wiersza polecenia open source, które znacząco upraszcza proces pobierania i tworzenia biblioteki statycznej typu open source C++ i bibliotek DLL w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [vcpkg: Menedżer pakietów dla języka C++](vcpkg.md).

**Visual Studio 2017 wersji 15,5 cala**:

### <a name="cpprest-sdk-290"></a>Zestaw SDK CPPRest 2.9.0

CPPRestSDK, i platform interfejsu API sieci web dla języka C++, została zaktualizowana do wersji 2.9.0. Aby uzyskać więcej informacji, zobacz [CppRestSDK 2.9.0 jest dostępna w serwisie GitHub](https://blogs.msdn.microsoft.com/vcblog/2016/10/21/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL

- Jeszcze inny zestaw poprawki zgodności wyszukiwanie nazw
- Istniejące konstruktory przenoszenia i przenieść operatory przypisania są teraz prawidłowo oznaczone jako z systemem innym niż zgłaszanie
- Pomiń UN prawidłowy ostrzeżenie C4640 o wątku init bezpieczne z lokalnych danych statycznych w wątkach w atlstr.h
- Wątek bezpiecznego inicjowania lokalnych danych statycznych w wątkach automatycznie był wyłączony w zestawie narzędzi XP podczas [za pomocą ALT i tworzenie biblioteki DLL]. Obecnie taka ewentualność nie zachodzi. Możesz dodać **/Zc:threadSafeInit-** w ustawieniach projektu, jeśli wątek wymagane jest bezpieczne inicjowanie off.

### <a name="visual-c-runtime"></a>Środowiska uruchomieniowego Visual C++

- Nowy nagłówek "cfguard.h" Ochrona przepływu sterowania symboli.

## <a name="c-ide"></a>Środowisko IDE języka C++

- Wydajność wprowadzania zmian w konfiguracji jest teraz lepsza w przypadku natywnych projektów w języku C++ i o wiele lepsza w projektach C++/CLI. W momencie pierwszej aktywacji konfiguracja rozwiązania będzie teraz szybsza, a wszystkie kolejne aktywacje konfiguracji rozwiązania będą prawie natychmiastowe.

**Visual Studio 2017 wersji 15 ustęp 3**:

- Ponownie napisano kilka kreatorów projektu i kodów w stylu okna dialogowego podpisu.
- **Dodaj klasę** teraz bezpośrednio uruchamia Kreator dodawania klasy. Wszystkie elementy, które były wcześniej w tym miejscu są teraz dostępne w obszarze **Dodaj > Nowy element**.
- Win32 projekty są teraz w obszarze **Windows Desktop** kategorii w **nowy projekt** okna dialogowego.
- **Konsoli systemu Windows** i **aplikacji pulpitu** szablony teraz tworzyć projekty bez wyświetlania kreatora. Jest dostępna nowa **kreatora pulpitu systemu Windows** w tej samej kategorii, wyświetla te same opcje jako stary **aplikacji konsoli Win32** kreatora.

**Visual Studio 2017 wersji 15,5 cala**:

Kilka operacji C++, które używają aparatu IntelliSense dla nawigacji refaktoryzacji i kod znacznie szybsze. Następujące numery są oparte na rozwiązaniu Visual Studio chromu z projektami 3500:

|||
|-|-|
|Funkcja|Zwiększenie wydajności|
|Zmień nazwę|5.3 x|
|Zmiana podpisu |4.5 x|
|Znajdź wszystkie odwołania|4,7 x|

Kliknij z wciśniętym obsługuje teraz C++ **przejdź do definicji**, dzięki łatwo myszy nawigacji do definicji. Wizualizator struktury z pakietu Narzędzia Power wydajności jest teraz również zawarta w produkcie domyślnie.

## <a name="intellisense"></a>IntelliSense

Nowy aparat bazy danych oparty na SQLite jest teraz używany domyślnie. Przyspieszy to operacje bazy danych, takie jak **przejdź do definicji** i **Znajdź wszystkie odwołania**oraz znacznie skróci czas analizy początkowej rozwiązania. Ustawienie został przeniesiony do **Narzędzia > Opcje > Edytor tekstu > C/C++ > Zaawansowane** (wcześniej znajdowało się w obszarze... C/C++ | Eksperymentalne).

- Zwiększono wydajność funkcji IntelliSense w projektach i pliki nie używa prekompilowanych nagłówków — automatyczne Prekompilowanego nagłówka, zostanie utworzona dla nagłówków w bieżącym pliku.

- Do listy błędów dodaliśmy filtrowanie błędów i pomoc dotyczącą błędów funkcji IntelliSense. Kliknięcie kolumny błędów umożliwia teraz filtrowanie. Ponadto kliknięcie konkretnego błędu lub naciśnięcie klawisza F1 uruchamia wyszukiwanie online dotyczące danego komunikatu o błędzie.

  ![Lista błędów](media/ErrorList1.png "Lista błędów")

  ![Filtrowana lista błędów](media/ErrorList2.png "Filtrowana lista błędów")

- Dodano możliwość filtrowania listy elementów członkowskich według rodzaju.

  ![Filtrowanie listy elementów członkowskich](media/mlfiltering.png "Filtrowanie listy elementów członkowskich")

- Dodano nową eksperymentalną funkcję Predictive IntelliSense, która pozwala na kontekstowe filtrowanie pozycji wyświetlanych na liście elementów członkowskich. Zobacz [ulepszenia IntelliSense dla C++ - predykcyjnej IntelliSense & filtrowania](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-intellisense-improvements-predictive-intellisense-filtering/)

- **Znajdź wszystkie odwołania** (Shift + F12) teraz codebases pomaga poruszania łatwe, nawet w przypadku złożonych. Umożliwia grupowanie zaawansowane filtrowanie, sortowanie, wyszukiwanie w wynikach i (w przypadku niektórych języków) kolorowania, dzięki czemu można uzyskać przejrzysty referencje. Dla języka C++ nowy interfejs użytkownika zawiera informacje na temat tego, czy możemy Odczyt lub zapis do zmiennej.

- Funkcja zmiany kropki na strzałkę IntelliSense została przeniesiona z doświadczalnych do zaawansowanych i teraz jest domyślnie włączona. Funkcje edycji **rozwiń zakresy** i **rozwiń pierwszeństwo** również zostały przeniesione z eksperymentalne do zaawansowane.

- Eksperymentalną refaktoryzacji **zmiany sygnatury** i **wyodrębnić funkcja** są teraz dostępne jako domyślne.

- Eksperymentalna funkcji "Projekt szybciej obciążenia" dla projektów C++. Przy następnym otwarciu projektu w języku C++ będzie on ładować się szybciej, a przy każdym następnym będzie ładować się naprawdę szybko!

Niektóre z tych funkcji są wspólne dla innych języków, a niektóre są specyficzne dla języka C++. Aby uzyskać więcej informacji na temat nowych funkcji, zobacz [Announcing programu Visual Studio "15"](https://blogs.msdn.microsoft.com/visualstudio/2016/10/05/announcing-visual-studio-15-preview-5/).

## <a name="non-msbuild-projects-with-open-folder"></a>Inne niż MSBuild projektów z otwartym folderze

Visual Studio 2017 wprowadza **Otwórz Folder** funkcji, która umożliwia kodu, kompilowanie i debugowanie w folderze zawierające kod źródłowy bez konieczności tworzenia żadnych rozwiązań lub projektów. Dzięki temu można łatwiej rozpocząć pracę z programem Visual Studio, nawet jeśli projekt nie jest częścią projektu MSBuild. Z **Otwórz Folder** uzyskać dostęp do zaawansowanych kodu, opis, edytowania, kompilowanie i debugowanie funkcji dostępnych w programie Visual Studio już dla projektów MSBuild. Aby uzyskać więcej informacji, zobacz [Otwórz Folder projekty w programie Visual C++](ide/non-msbuild-projects.md).

- Ulepszenia obsługi polecenia Otwórz folder. Środowisko użytkownika można dostosować za pomocą tych plików JSON:
  - CppProperties.json dostosowuje obsługę funkcji IntelliSense i przeglądania.
  - Tasks.json dostosowuje kroki kompilacji.
  - Launch.json dostosowuje obsługę debugowania.

**Visual Studio 2017 wersji 15 ustęp 3**:

- Ulepszona obsługa alternatywnych kompilatory i środowiska kompilacji, takie jak MinGW i programów Cygwin. Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska MinGW i programów Cygwin Visual C++ i otwórz Folder](https://blogs.msdn.microsoft.com/vcblog/2017/07/19/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Dodano obsługę do definiowania zmiennych środowiskowych globalne i specyficzne dla konfiguracji w CppProperties.json i CMakeSettings.json. Te zmienne środowiskowe mogą być używane przez zdefiniowane w launch.vs.json i zadania w tasks.vs.json konfiguracji debugowania. Aby uzyskać więcej informacji, zobacz [Dostosowywanie środowiska Visual C++ i otwórz Folder](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/customizing-your-environment-with-visual-c-and-open-folder/).
- Ulepszona obsługa generator Nindżą w CMake, łącznie z możliwością łatwego 64-bitowych platform docelowych.

## <a name="cmake-support-via-open-folder"></a>Obsługa CMake za pośrednictwem Otwórz Folder

Visual Studio 2017 wprowadzono obsługę za pomocą CMake projekty bez konwersji pliki projektu MSBuild (.vcxproj). Aby uzyskać więcej informacji, zobacz [CMake projekty w programie Visual C++](ide/cmake-tools-for-visual-cpp.md). Otwieranie CMake projektów z **Otwórz Folder** automatycznie konfiguruje środowisko dla języka C++, edytowania, kompilowania i debugowania.

- IntelliSense dla C++ działa bez konieczności tworzenia pliku CppProperties.json w folderze głównym. Wraz z tym dodaliśmy nowe listy rozwijane, aby użytkownicy mogli łatwo przełączać się między konfiguracjami dostarczonymi przez pliki CMake i CppProperties.json.

- Dalsza konfiguracja jest obsługiwana przy użyciu pliku CMakeSettings.json, który znajduje się w tym samym folderze co plik CMakeLists.txt.

  ![Cmake Otwórz folder](media/cmake_cpp.png "CMake Otwórz folder")

**Visual Studio 2017 wersji 15 ustęp 3**: generator Nindżą CMake dodać obsługę. Aby uzyskać więcej informacji, zobacz [CMake projekty w programie Visual C++](ide/cmake-tools-for-visual-cpp.md).

**Visual Studio 2017 wersji 15,5 cala**: importowanie istniejących CMake dodano obsługę przechowuje w pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [CMake projekty w programie Visual C++](ide/cmake-tools-for-visual-cpp.md).

## <a name="windows-desktop-development-with-c"></a>Programowanie aplikacji pulpitu systemu Windows za pomocą języka C++

Zapewniamy obecnie bardziej zaawansowane środowisko instalacji oryginalnego obciążenia C++. Dodaliśmy możliwe do wybrania składniki pozwalające na zainstalowanie tylko tych narzędzi, których potrzebujesz.  Należy pamiętać, że wskazane w interfejsie użytkownika instalatora rozmiary instalacji składników nie są prawidłowe i zaniżają całkowity rozmiar instalacji.

Aby pomyślnie tworzyć projekty Win32 w obciążeniu C++ dla komputerów stacjonarnych, musisz zainstalować zarówno zestaw narzędzi, jak i zestaw SDK systemu Windows. Instalowanie zalecanych składników (wybrane) **narzędzi v141 2017 VC ++ (x86, x64)** i **zestawu Windows 10 SDK (10.0.nnnnn)** zapewnia to będzie działać. Jeśli potrzebne narzędzia nie zostaną zainstalowane, projekty nie będą pomyślnie tworzone i kreator będzie się zawieszać.

**Visual Studio 2017 wersji 15,5 cala**:

Narzędzia kompilacji Visual C++ (wcześniej dostępne jako autonomiczny produkt) są teraz włączone jako obciążenie w Instalatorze programu Visual Studio. To obciążenie instaluje tylko narzędzia wymagane do tworzenia projektów C++ bez instalowania programu Visual Studio IDE. Uwzględniane są zarówno w wersji 140 i v141 procesami. Zestaw narzędzi v141 zawiera ulepszenia najnowsza w Visual Studio 2017 wersji 15,5 cala. Aby uzyskać więcej informacji, zobacz [programu Visual Studio Tools kompilacji zawierają teraz VS2017 i procesami MSVC VS2015](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Tworzenie Linux za pomocą języka C++

Popularne rozszerzenie [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) stanowi obecnie cześć programu Visual Studio. Ta instalacja zawiera wszystko, czego potrzebujesz do tworzenia i debugowania aplikacji w języku C++ działających w środowisku systemu Linux.

**Visual Studio 2017 wersji 15,2**:

Wprowadzono ulepszenia w wizualizacji udostępniania i typ kodu i platform. Aby uzyskać więcej informacji, zobacz [ulepszenia Linux C++ dla wielu platform kodu do udostępniania i typ wizualizacji](https://blogs.msdn.microsoft.com/vcblog/2017/05/10/linux-cross-platform-and-type-visualization/).

**Visual Studio 2017 wersji 15,5 cala**:

- Obciążenie systemu Linux została dodana obsługa **rsync** zamiast **sftp** synchronizowania plików do zdalnej maszyny z systemem Linux.
- Dodano obsługę wielu elementów docelowych mikrokontrolerów ARM kompilacji. Aby włączyć tę opcję w instalacji, wybierz **Linux Programowanie w języku C++** obciążenia i wybierz opcję **osadzone i rozwoju IoT**. Spowoduje to dodanie GCC ARM cross tools kompilacji i udostępnić do instalacji. Aby uzyskać więcej informacji, zobacz [GCC ARM Cross kompilacji, w programie Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/10/23/arm-gcc-cross-compilation-in-visual-studio/).
- Dodano CMake obsługę. Teraz możesz pracować na istniejący kod CMake podstawowej bez konieczności przekonwertować go do projektu programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu CMake Linux](linux/cmake-linux-project.md).
- Uruchamianie zadań zdalnego dodano obsługę. Ta funkcja umożliwia uruchamianie polecenia w systemie zdalnym, który jest zdefiniowany w Menedżerze połączeń programu Visual Studio. Zadania zdalne zapewniają również możliwość kopiowania plików do systemu zdalnego.

## <a name="game-development-with-c"></a>Tworzenie gier z C++

Pełnych możliwości języka C++ można użyć do tworzenia profesjonalnych gier obsługiwanych przy użyciu zestawu funkcji DirectX lub Cocos2d.

## <a name="mobile-development-with-c-android-and-ios"></a>Tworzenie przenośnych za pomocą języka C++ (Android i iOS)

Program Visual Studio umożliwia obecnie programowanie i debugowanie aplikacji mobilnych przeznaczonych dla systemów Android oraz iOS.

## <a name="universal-windows-apps"></a>Aplikacje uniwersalne systemu Windows

Język C++ stanowi składnik opcjonalny obciążenia Aplikacja uniwersalna systemu Windows.  Obecnie uaktualnianie projektów C++ należy wykonywać ręcznie. Po otwarciu projektu przeznaczonego dla wersji 140 platformy uniwersalnej systemu Windows (UWP) w programie Visual Studio 2017 musisz wybrać zestaw narzędzi platformy w wersji 141 na stronach właściwości projektu, jeśli nie masz zainstalowanego programu Visual Studio 2015.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nowe opcje dla języka C++ na uniwersalnych platformy systemu Windows (UWP)

Masz teraz nowe opcje zapisu i tworzenia pakietu aplikacji C++ dla platformy uniwersalnej systemu Windows i Microsoft Store. Konwerter aplikacji pulpitu umożliwia pakietu istniejącej aplikacji klasycznych dla wdrożenia za pomocą Microsoft Store. Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska uruchomieniowego Visual C++ w projekcie Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project/) i [przełączyć aplikację pulpitu do systemu Windows platformy Uniwersalnej z Mostek pulpitu](/windows/uwp/porting/desktop-to-uwp-root).

**Visual Studio 2017 wersji 15,5 cala**:

A **projekt do tworzenia pakietów aplikacji systemu Windows** zostanie dodany szablon projektu, który obsługuje pakowania aplikacje przy użyciu mostka pulpitu. Jest dostępny w obszarze **Plik > Nowy > Projekt** w obszarze **zainstalowana > Visual C++ > platformy uniwersalnej systemu Windows** po zainstalowaniu obciążenia uniwersalnej aplikacji systemu Windows.

Podczas zapisywania nowego kodu, można teraz używać C + +/ WinRT, standardowe projekcji języka C++ realizowane wyłącznie w pliki nagłówków środowiska uruchomieniowego systemu Windows. Pozwala na obu autora, a korzystanie z interfejsów API środowiska wykonawczego systemu Windows przy użyciu dowolnego ze standardami kompilator języka C++. C + +/ WinRT umożliwia deweloperom C++ z dostępem do najwyższej jakości nowoczesnych interfejsu API systemu Windows. Aby uzyskać więcej informacji, zobacz [C + +/ WinRT dostępne w witrynie GitHub](https://moderncpp.com/).

Począwszy od programu [kompilacji 17025 Windows SDK niejawnego Preview](https://blogs.windows.com/buildingapps/2017/11/01/windows-10-sdk-preview-build-17025/#ryPH3zAy6yk2cIRX.97), C + +/ WinRT znajduje się w zestawie Windows SDK. Aby uzyskać więcej informacji, zobacz [C + +/ WinRT jest teraz włączone zestaw Windows SDK](https://blogs.msdn.microsoft.com/vcblog/2017/11/01/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="clangc2-platform-toolset"></a>Zestaw narzędzi platformy clang/C2

Zestaw narzędzi Clang/C2 dostarczany z [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] obsługuje teraz **/bigobj** przełącznika, który ma kluczowe znaczenie podczas kompilowania dużych projektów. Oferuje on również kilka ważnych poprawek, zarówno we frontonie, jak i zapleczu kompilatora.

## <a name="c-code-analysis"></a>Analiza kodu C++

Podstawowe narzędzia do sprawdzania kodu C++ wymuszające stosowanie [podstawowych wytycznych dotyczących języka C++](https://github.com/isocpp/CppCoreGuidelines) są obecnie dystrybuowane z programem Visual Studio. Po prostu włącz programy w **rozszerzenia analizy kodu** stronę na stronach właściwości projektu i rozszerzenia zostanie uwzględniony podczas uruchamiania analizy kodu. Aby uzyskać więcej informacji, zobacz [przy użyciu programy C++ podstawowe wskazówki](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Strona właściwości CppCoreCheck")

**Visual Studio 2017 wersji 15 ustęp 3**:

Dodano zasady dotyczące zarządzania zasobami obsługę.

**Visual Studio 2017 wersji 15,5 cala**:

Poprawność wskaźnika inteligentnego, prawidłowe użycie globalnych inicjatory obejmują nowe funkcje sprawdzania C++ podstawowe wskazówki i flag używa konstrukcji, takich jak `goto` i zły rzutowania.

Niektóre numery ostrzeżeń, które można znaleźć w wersji 15.3, nie są już dostępne w wersji 15.5. Ostrzeżenia te zostały zastąpione bardziej szczegółowymi operacjami sprawdzania.

## <a name="unit-testing"></a>Testy jednostkowe

**Visual Studio 2017 wersji 15,5 cala**:

Adapter testowy Google i karty Boost.Test są teraz dostępne jako składniki **projektowania aplikacji w języku C++** obciążenia i są zintegrowane z **Eksploratora testów**. Obsługa CTest jest dodawany do projektów Cmake (przy użyciu Otwórz Folder), mimo że pełna integracja z **Eksploratora testów** nie jest jeszcze dostępna. Aby uzyskać więcej informacji, zobacz [dla C/C++ pozwala pisać testy jednostkowe](/visualstudio/test/writing-unit-tests-for-c-cpp).

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostyki grafiki w programie Visual Studio

Diagnostyki grafiki w programie Visual Studio jest zestaw narzędzi dla rejestrowanie i analizowanie renderowania i problemom z wydajnością w aplikacjach Direct3D. Funkcje diagnostyki grafiki można przy użyciu aplikacji uruchomionych lokalnie na komputerze z systemem Windows w emulatorze urządzenia z systemem Windows lub na zdalnym komputerze lub urządzeniu.

- **Dane wejściowe i wyjściowe dla programów do cieniowania wierzchołków i geometrii:** możliwość wyświetlania danych wejściowych i wyjściowych programów do cieniowania wierzchołków i programów do cieniowania geometrycznego był jedną z najbardziej pożądanych funkcji, a teraz jest obsługiwana w narzędziach. Po prostu zaznacz etap VS lub GS w widoku etapy potoku, aby rozpocząć sprawdzanie przychodzących i dane wyjściowe w poniższej tabeli.

  ![Wejścia/wyjścia dla programów do cieniowania](media/io-shaders.png)

- **Wyszukiwanie i filtrowanie w tabeli obiektów:** zapewnia szybki i łatwy sposób znaleźć zasoby szukasz.

  ![Wyszukaj](media/search.png)

- **Historia zasobów:** nowy widok zapewnia uproszczony sposób wyświetlenia historii całego modyfikacja zasobu, która była używana podczas renderowania przechwyconej ramce. Aby wywołać historii dla wszystkich zasobów, wystarczy kliknąć ikonę zegara obok hyperlink żadnych zasobów.

  ![Historia zasobów](media/resource-history.png)

  Spowoduje to wyświetlenie nowa **historii zasobów** okna narzędzia, wypełniane przy użyciu historii zmian zasobu.

  ![Zmiana historię zasobu](media/resource-history-change.png)

  Należy pamiętać, że jeśli Twoje przechwycenia z włączone Przechwytywanie stosu wywołania Pełna (**programu Visual Studio > Narzędzia > Opcje** w obszarze **diagnostyki grafiki**), następnie kontekście każdego zdarzenia zmiany można szybko ustalona i inspekcji w ciągu projektu programu Visual Studio.

- **Statystyka interfejsu API:** wyświetlić podsumowanie wysokiego poziomu użycia interfejsu API w sieci ramki. Może to być przydatne w odnajdywaniu wywołań mogą nie uznasz, że wprowadzasz w ogóle lub wywołań tworzonego zbyt dużej ilości. To okno jest dostępny za pośrednictwem **Widok > Statystyki interfejsu API** w analizatora grafiki programu Visual Studio.

  ![Statystyka interfejsu API](media/api-stats.png)

- **Statystyki pamięci:** wyświetlić, ile pamięci sterownik jest przydzielanie zasobów utworzyć w ramce. To okno jest dostępny za pośrednictwem **Widok > Statystyki pamięci** w **analizatora grafiki programu Visual Studio**. Dane można kopiować do pliku CSV do wyświetlenia w arkuszu kalkulacyjnym prawym przyciskiem myszy i wybierając pozycję **Kopiuj wszystko**.

  ![Statystyka pamięci](media/memory-stats.png)

- **Sprawdzanie poprawności ramki:** nową listę błędów i ostrzeżeń zapewnia prosty sposób można przejść z listy zdarzeń oparte na potencjalnych problemów wykrytych przez warstwę debugowania Direct3D. Kliknij przycisk **Widok > Ramka weryfikacji** w analizatora grafiki programu Visual Studio można otworzyć okna. Następnie kliknij przycisk **Uruchom weryfikację** można rozpocząć analizy. Może upłynąć kilka minut, w zależności od złożoności ramki.

  ![Sprawdzanie poprawności ramki](media/frame-validation.png)

- **Ramkę analizy D3D12:** analizy ramek używany do analizowania wydajności wywołania rysowania z skierowane do eksperymentów "co jeśli". Przełącz na kartę analizy ramek i uruchamiać analizę, aby wyświetlić raport. Aby uzyskać więcej informacji, obserwuj [GoingNative 25: analiza ramek grafiki programu Visual Studio](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) wideo.

  ![Analiza ramek](media/frame-analysis.png)

- **Ulepszenia użycia procesora GPU:** otwierać ślady podjęte za pomocą profilera Visual Studio dotyczących użycia procesora GPU z widoku GPU lub narzędzia Analizator wydajności systemu Windows (WPA), aby uzyskać bardziej szczegółowe analizy. Jeśli masz Toolkit wydajności systemu Windows zainstalowana na będzie dwa hiperłącza, jeden dla WPA i drugi dla widoku procesora GPU w prawym dolnym rogu omówienie sesji.

  ![Użycie procesora GPU](media/gpu-usage.png)

  Ślady otwarty w widoku procesora GPU za pośrednictwem tego łącza pomocy technicznej synchronizowane powiększanie i przesuwanie na osi czasu między VS i procesora GPU. Pole wyboru w programie VS jest używana do sterowania czy synchronizacji jest włączony, czy nie.

  ![Widok procesora GPU](media/gpu-view.png)
