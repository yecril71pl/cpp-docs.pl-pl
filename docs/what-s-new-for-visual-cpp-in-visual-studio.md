---
title: "Nowości w języku Visual C++ w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9927726585572f69bdf121c4ed71e8b034fc1ed3
ms.sourcegitcommit: 1b480aa74886930b3bd0435d71cfcc3ccda36424
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="whats-new-for-visual-c-in-includevsdev15mdmiscincludesvsdev15mdmd"></a>Nowości w języku Visual C++ w[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)]

[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)]udostępnia wiele aktualizacji i poprawki dla środowiska Visual C++. Firma Microsoft usunęła ponad 250 usterek i zgłoszonych problemów w kompilatorze i narzędziach — wiele z nich było zgłoszonych przez klientów za pośrednictwem witryny [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect"). Dziękujemy za zgłaszanie usterek!  Aby uzyskać więcej informacji dotyczących nowości we wszystkich programu Visual Studio, odwiedź [nowości [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] ](https://go.microsoft.com/fwlink/?linkid=834481).

<!--The compiler and tools version number in [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] is 14.10.24629. -->


## <a name="c-compiler"></a>kompilator C++

### <a name="c-conformance-improvements"></a>Ulepszenia zgodność języka C++
W tej wersji zaktualizowaliśmy standardową bibliotekę i kompilator języka C++ o rozszerzoną obsługę funkcji języka C ++ 11 i C ++ 14, a także wstępną obsługę niektórych funkcji, które mają zostać uwzględnione w standardowym języku C ++ 17. Aby uzyskać szczegółowe informacje, zobacz [ulepszenia zgodność języka C++ w programie Visual Studio 2017](cpp-conformance-improvements-2017.md).

### <a name="new-compiler-switches"></a>Nowe przełączniki kompilatora  

 -**/STD:c ++ 14** i **/std:c ++ najnowsze**: te przełączniki kompilatora umożliwiają wyrazić zgodę na określonych wersji ISO C++ język w projekcie programowania. Aby uzyskać więcej informacji, zobacz [-std (Określ wersję Standard języka)](build/reference/std-specify-language-standard-version.md). Większość nowych wersji roboczej standardowych funkcji jest chroniony przez /std:c ++ najnowsze przełącznika. 

**Visual Studio 2017 wersji 15 ustęp 3**: **/std:c ++ 17** opcji udostępnia zestaw funkcji C ++ 17 implementowane przez kompilator języka Visual C++. Ta opcja powoduje wyłączenie kompilator i biblioteki standardowej obsługi funkcji, które zostały zmienione lub nowych w nowszych wersjach aktualizacji pracy roboczą i usterką standardu C++.

-[/ ograniczająca-](build/reference/permissive-standards-conformance.md): Włącz wszystkie standardy strict zgodność-opcje kompilatora i wyłączyć najbardziej rozszerzenia kompilatora specyficzne dla firmy Microsoft (ale nie __declspec(dllimport), na przykład). (Funkcja domyślnie wyłączona, ale będzie na domyślnie w pewnym momencie w przyszłości).

-[/Diagnostics](build/reference/diagnostics-compiler-diagnostic-options.md): Włącz wyświetlania numer wiersza, numer wiersza i kolumny, lub numer wiersza i kolumny i karetki w wierszu kodu, w którym zostało znalezione diagnostycznych błąd lub ostrzeżenie.

-[/Debug:fastlink](build/reference/debug-generate-debug-info.md):  
Włącz do 30% szybciej konsolidowania przyrostowego razy (vs. Visual Studio 2015) przed kopiowaniem wszystkie informacje w pliku PDB debugowania. Zamiast tego pliku PDB wskazuje informacji debugowania dla obiekt i biblioteki plików używany do tworzenia pliku wykonywalnego. Zobacz [cykl w programie VS "15" z /Debug:fastlink kompilacji C++ szybciej](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-build-cycle-in-vs-15-with-debugfastlink/) i [zalecenia dotyczące szybkości kompilacji C++ w programie Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2016/10/26/recommendations-to-speed-c-builds-in-visual-studio/).

[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)]Umożliwia przy użyciu/SDL z / await. Firma Microsoft usunęła ograniczenie/RTC z procedury wspólnej. 

**Visual Studio 2017 wersji 15,5 cala**: kompilatora Visual C++ obsługuje około 75% C ++ 17 funkcje, takie jak powiązania strukturalnych `constexpr` wyrażeń lambda, `if constexpr`, wbudowane zmienne, fold wyrażeń i dodawanie `noexcept` do typu System. Są one dostępne w obszarze /std:c ++ 17 przełącznika. Tryb /permissive-conformance obsługuje częściowe dwufazowego nazw wyszukiwania. Aby uzyskać więcej informacji, zobacz [ulepszenia zgodność języka C++ w programie Visual Studio 2017](cpp-conformance-improvements-2017.md). 

### <a name="codegen-security-diagnostics-and-versioning"></a>CODEGEN, zabezpieczeń, diagnostyki i kontroli wersji
Tej wersji wprowadzono kilka ulepszeń optymalizacji, generowanie kodu, przechowywanie wersji zestawu narzędzi i diagnostyki. Do istotnych ulepszeń należą:  

- Ulepszone generowanie kodu pętli: obsługa automatycznej wektoryzacji dzielenia stałych liczb całkowitych, lepsza identyfikacja wzorców funkcji memset.
- Ulepszone zabezpieczenia kodu: ulepszona emisja diagnostyki kompilatora w zakresie przepełnienia buforu, a funkcja /guard:cf chroni teraz instrukcje switch, które generują tabele przeskoków.
- Przechowywanie wersji: Wartość elemencie _MSC_VER wbudowane makro preprocesora jest teraz monotonicznie aktualizowany po każdej aktualizacji narzędzi programu Visual C++. Aby uzyskać więcej informacji, zobacz [kompilatora Visual C++ w wersji](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/).
- Nowy układ zestawu narzędzi: kompilacji powiązane narzędzi i kompilatora ma nowej struktury lokalizacji i katalog na komputerze deweloperskim. Nowy układ umożliwia side-by-side instalacji wielu wersji kompilatora. Aby uzyskać więcej informacji, zobacz [układ narzędzi kompilatora Visual Studio "15"](https://blogs.msdn.microsoft.com/vcblog/2016/10/07/compiler-tools-layout-in-visual-studio-15/).
- Ulepszona diagnostyka: W oknie danych wyjściowych zawiera obecnie kolumnę gdzie występuje błąd. Aby uzyskać więcej informacji, zobacz [ulepszenia diagnostyki kompilatora C++ w programie VS "15" Preview 5](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-compiler-diagnostics-improvements-in-vs-15-rc/).
- Korzystając z procedury wspólnej, eksperymentalne — słowo kluczowe "yield" (dostępny w obszarze / await przełącznika) została usunięta. Kod powinien zostać zaktualizowany do użycia `co_yield` zamiast tego. Więcej informacji można znaleźć na [blogu zespołu Visual C++](https://blogs.msdn.microsoft.com/vcblog/). 

**Visual Studio 2017 wersji 15 ustęp 3**: dodatkowe ulepszenia diagnostyki kompilatora. Aby uzyskać więcej informacji, zobacz [diagnostycznych ulepszeń w programie Visual Studio 2017 15.3.0](https://blogs.msdn.microsoft.com/vcblog/2017/07/21/diagnostic-improvements-in-vs2017-15-3-0/).

**Visual Studio 2017 wersji 15,5 cala**: wydajność środowiska uruchomieniowego Visual C++ w dalszym ciągu poprawy z powodu jakości lepiej wygenerowanego kodu. Oznacza to, czy po prostu ponownie skompilować kod i aplikacji po prostu działa szybciej. Niektóre optymalizacje kompilatora są całkowicie nowe, takich jak vectorization warunkowego magazynów skalarne, łączenie sin(x) wywołania i cos(x) do nowego sincos(x) i eliminacja nadmiarowe instrukcji Optymalizator SSA. Inne optymalizacje kompilatora są ulepszenia istniejących funkcji, takich jak Algorytm heurystyczny wektoryzowania wyrażenia warunkowego, lepszej optymalizacji pętli i codegen min/max float. Konsolidator ma implementacji nowego i szybsze/OPT: ICF, co może skutkować do 9 speedups czas łącza %, a istnieją inne poprawki wydajności w "konsolidowania przyrostowego". Aby uzyskać więcej informacji, zobacz [od (optymalizacje)](https://docs.microsoft.com/en-us/cpp/build/reference/opt-optimizations) i [/incremental (łącze przyrostowo)](https://docs.microsoft.com/en-us/cpp/build/reference/incremental-link-incrementally).

Visual C++ obsługuje jest AVX firmy Intel-512, łącznie z instrukcjami długość wektora nowych funkcji w AVX 512 doprowadzić rejestrów szeroki 128 - i 256-bitowego.

**/Zc:noexceptTypes-** przełącznika może służyć do przywrócenia C ++ 14 wersja `noexcept` podczas w trybie C ++ 17 ogólnie. Dzięki temu można zaktualizować kodu źródłowego z języków C ++ 17, bez konieczności ponownego zapisania wszystkie Twoje `throw()` kodu w tym samym czasie. Aby uzyskać więcej informacji, zobacz [usuwania specyfikacji wyjątków dynamicznych i noexcept](cpp-conformance-improvements-2017.md#noexcept_removal).


## <a name="c-standard-library-improvements"></a>Ulepszenia standardowa biblioteka C++

* Nieznaczne usprawnienia diagnostyki basic_string _ITERATOR_DEBUG_LEVEL != 0. Wyzwolenie kontroli IDL w maszynie ciągu zgłasza teraz określone zachowanie, które spowodowało wyzwolenie. Na przykład zamiast komunikatu „iterator ciągu nie umożliwia wyłuskiwania” otrzymasz komunikat „nie można wyłuskać iteratora ciągu, ponieważ jest on poza zakresem (np. iterator końca)”.
* Ulepszenie wydajności: wykonanie instrukcji basic_string::find(char) przeciąża tylko raz wywołanie traits::find. Wcześniej było to wdrożone jako ogólne wyszukiwanie ciągu o długości 1.
* Ulepszenie wydajności: instrukcja basic_string::operator== sprawdza teraz rozmiar ciągu przed porównaniem zawartości ciągów.
* Ulepszenie wydajności: usunięto formant sprzężenia w ciągu basic_string, który był trudny do analizy przez optymalizator kompilatora. Usuwa VSO # 262848 "\<ciąg\>: reserve() zbyt dużo działa". Należy pamiętać, że dla wszystkich krótkich ciągów wywoływanie rezerwy nadal ma niezerowy koszt bezczynności.
* Dodaliśmy obiekty \<any\>, \<string_view\>, apply() i make_from_tuple().
* Instrukcja std::vector została przejrzana pod kątem prawidłowości i wydajności: tworzenie aliasów podczas wstawiania/umieszczania jest teraz poprawnie obsługiwane zgodnie z wymaganiami standardu. Zapewniana jest teraz gwarancja silnego wyjątku, gdy jest to wymagane przez Standard, za pośrednictwem funkcji move_if_noexcept() i innej logiki, a wstawianie/umieszczanie wykonuje mniej operacji na elementach.
* Standardowa biblioteka C++ unika teraz dereferencji ozdobne wskaźniki o wartości null.
* Dodano obiekty \<optional\>, \<variant\>, shared_ptr::weak_type oraz \<cstdalign\>.
* Włączono słowo kluczowe constexpr języka C++14 w wyrażeniach min/max/minmax(initializer_list) oraz min_element/max_element/minmax_element().
* Zwiększona wydajność funkcji weak_ptr::lock().
* Naprawiono operator przypisania przeniesienia obiektu std::promise, który mógł wcześniej spowodować zablokowanie kodu na stałe.
* Naprawiono błędy kompilatora dotyczące niejawnej konwersji struktury atomic\<T \*\> do T \*.
* Obiekt pointer_traits\<Ptr\> wykrywa teraz prawidłowo Ptr::rebind\<U\>.
* Naprawiono brakujący kwalifikator const w operatorze odejmowania obiektu move_iterator.
* Naprawiono ciche, nieprawidłowe generowanie kodu dla stanowych programów przydzielających definiowanych przez użytkownika żądających obiektów propagate_on_container_copy_assignment oraz propagate_on_container_move_assignment.
* atomic\<T\> toleruje obecnie przeciążony operator&().
* W celu zwiększenia przepływności kompilatora, nagłówki standardowa biblioteka C++ teraz uniknąć, włączając deklaracje dla funkcje wewnętrzne kompilatora niepotrzebne.
* Nieco ulepszona diagnostyka kompilatora dla nieprawidłowych wywołań bind().
* Zwiększono wydajność std::string / std::wstring przez przeniesienie konstruktorów za więcej niż 3 x
* Aby uzyskać pełną listę biblioteki standardowej Zobacz improvments [standardowej biblioteki poprawki w VS 2017 RTM](https://blogs.msdn.microsoft.com/vcblog/2017/02/06/stl-fixes-in-vs-2017-rtm/).

### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 wersji 15 ustęp 3

#### <a name="c17-features"></a>C ++ 17 funkcji 
Zastosowano kilka dodatkowych funkcji C ++ 17. Aby uzyskać więcej informacji, zobacz [Visual zgodność języka C++](cpp-conformance-improvements-2017.md#improvements_153).

#### <a name="other-new-features"></a>Inne nowe funkcje
* Zaimplementowane P0602R0 "variant i opcjonalne powinien propagację triviality skopiowania/przeniesienia".
* Standardowa biblioteka teraz oficjalnie zaakceptować RTTI dynamiczne są wyłączone przez czasie. dynamic_pointer_cast() i rethrow_if_nested() z założenia wymaga dynamic_cast, dzięki czemu można biblioteki standardowej teraz oznacza je jako = delete w czasie.
* Nawet po RTTI dynamicznej została wyłączona za pomocą czasie, "statyczne RTTI" (w postaci typeid(SomeType)) jest nadal dostępny i obsługuje kilka składników biblioteki standardowej. Standardowa biblioteka obsługuje teraz wyłączenie to, za pośrednictwem /D_HAS_STATIC_RTTI = 0. *Należy pamiętać, wyłączenia std::any, target() std::function w i target_type() oraz get_deleter() shared_ptr firmy.*

#### <a name="correctness-fixes"></a>Poprawność poprawki
* Standardowa biblioteka kontenery teraz clamp ich max_size() do numeric_limits\<difference_type\>:: max() zamiast size_type do maksymalnej. To zapewnia, że wynik distance() na Iteratory z tego kontenera jest można przedstawić w distance() typ zwracany.
* Stałe Brak auto_ptr specjalizacji\<void\>.
* Algorytmy meow_n() wcześniej kompilacja nie powiodła się, jeśli długość argumentu nie jest typem całkowitym; teraz mogła przekonwertować długości niecałkowity difference_type Iteratory.
* normal_distribution —\<float\> już emituje ostrzeżenia w standardowej bibliotece o zawężanie z typu double na float.
* Usunięto niektóre operacje basic_string —, które zostały porównanie z npos zamiast max_size(), gdy sprawdzanie przepełnienia maksymalny rozmiar.
* condition_variable::wait_for (blokady, relative_time predykatu) oczekiwania przez cały czas względny w przypadku wznawiania fałszywe. Teraz będzie czekać przez tylko jeden interwał względne czasu.
* przyszłe:: get() teraz unieważnia przyszłości jako standard wymaga.
* iterator_traits\<void \* \> się poważny błąd, ponieważ podjęto próbę utworzenia void&; teraz prawidłowo staje się puste struktury umożliwia użycie iterator_traits w "jest iteratora" techniki SFINAE warunki.
* Zgłoszone przez Clang - wsystem —-headers ostrzeżenia zostały usunięte.
* Usunięto również "Specyfikacja wyjątku w deklaracji niezgodność z poprzednią deklaracją" zgłoszone przez Clang - Wmicrosoft-wyjątku spec.
* Usunięto również mem inicjator listy ostrzeżeń porządkowania zgłaszanych przez Clang i C1XX.
* Kontenery nieuporządkowaną nie wymiany ich hashers lub predykaty, gdy same kontenery zostały zamienione. Teraz je.
* Wiele operacji wymiany kontenera zostały oznaczone noexcept (zgodnie z naszym biblioteki standardowej zamierza nigdy nie zgłoszenia wyjątku podczas wykrywania stanu bez przydzielania równości niezdefiniowane zachowanie propagate_on_container_swap z systemem innym niż).
* Wektor wiele\<bool\> operacje zostały oznaczone noexcept.
* Standardowa biblioteka będzie wymuszać teraz dopasowywania value_types alokatora (tryb C ++ 17) z kreskowania ucieczki rezygnacji z.
* Usunięto niektóre warunki gdzie niezależne-range-insert into basic_strings czy szyfrują zawartość ciągi są. (Uwaga: niezależne-range-insert into wektory nadal jest zabronione przez standardowego.)
* basic_string::shrink_to_fit() nie ma wpływu na propagate_on_container_swap programu przydzielania.
* STD::decay obsługuje teraz typy funkcji abominable (tj. Funkcja typy, które są cv kwalifikowaną lub kwalifikowaną ref).
* Zmienione dyrektyw prawidłowego uwzględniana wielkość liter i ukośniki, poprawy przenośność.
* Stałe ostrzeżenie C4061 "moduł wyliczający"Meow"przełącznika wyliczenia, które"Kitten"nie jest jawnie obsługiwany przez etykietę case". To ostrzeżenie jest wyłączone domyślnie i został rozwiązany jako wyjątek do biblioteki standardowej zasady ogólne ostrzeżenia. (Standardowa biblioteka jest/W4 czystą, ale nie jest podejmowana próba można/Wall czyste. Wiele poza domyślnie ostrzeżenia są bardzo dużo i nie są przeznaczone do użycia na bieżąco.)
* Sprawdza, czy ulepszona kontener std::list debugowania. Iteratory listy Sprawdź teraz operator -> () oraz listy:: unique() teraz oznacza Iteratory jako unieważnione.
* Stałe używa alokatora metaprogramowania w spójnej kolekcji.

#### <a name="performancethroughput-fixes"></a>Wydajność/przepływności poprawki
* Przepracowany wokół interakcji z noexcept, który uniemożliwił ze śródwierszowaniem std:: atomic do implementacji w funkcje programu wykorzystujące strukturalnych obsługi wyjątków (SEH).
* Zmienić standardowa biblioteka _Deallocate() wewnętrznej funkcji w celu zoptymalizowania na mniejsze kod, dzięki któremu można wbudować w większej liczbie miejsc.
* Zmienić std::try_lock() umożliwia rozwinięcie pakietu zamiast rekursji.
* (Ulepszone std::lock) zakleszczenie unikania algorytm używany operacji lock() zamiast Obracająca na wszystkich blokad try_lock () s.
* Włączono optymalizację nazwanych wartości zwracanej w system_category::message().
* połączeniu i rozłączenia teraz wystąpienia N + 1 typów, zamiast 2N + 2 typów.
* STD::Function tworzy już przydzielania maszyny pomocy technicznej dla każdego wymazane typu można wywołać, ulepszanie przepływności i zmniejszenie rozmiaru .obj w programach, które przekazać wiele różnych wyrażeń lambda do std::function.
* allocator_traits —\<std::allocator\> zawiera operacje std::allocator ręcznie śródwierszowych, zmniejszyć rozmiar kodu w kodzie, który współdziała z std::allocator za pośrednictwem allocator_traits — w tylko (tj. większość kodu).
* C ++ 11 alokatora minimalnego interfejsu jest teraz obsługiwany przez biblioteki standardowej wywoływania allocator_traits — bezpośrednio, zamiast zawijania programu przydzielania w _Wrap_alloc Wewnętrzna klasa. To zmniejsza rozmiar kodu wygenerowany dla pomocy technicznej programu przydzielania, zwiększa możliwości Optymalizator Przyczyna o biblioteki standardowej kontenery w niektórych przypadkach i zapewnia lepsze debugowania (jak widoczny z alokatora typu, a nie _Wrap_alloc\<danego typu alokatora\> w debugerze).
* Usunięte metaprogramowania dla allocator::reference niestandardowych, które allocators — faktycznie nie są dozwolone dostosować. (Allocators — ułatwia kontenery, użyj wskaźników ozdobne, ale nie ozdobne odwołań.)
* Kompilator frontonu został jednocześnie dekodowania Iteratory debugowania w opartej na zakresie dla pętle, poprawia wydajność debugowania kompilacji.
* basic_string — w wewnętrznej zmniejszania ścieżka shrink_to_fit() i reserve() nie jest już w ścieżce ponowne przydzielanie operacji zmniejszenia rozmiaru kodu dla wszystkich członków mutating.
* basic_string — obiektu wewnętrznego wzrostu ścieżka nie jest już w ścieżce shrink_to_fit().
* operacje mutacja w basic_string — teraz są rozkładane na — przydzielanie szybkiej ścieżki i alokowania funkcje powolną ścieżkę, dzięki czemu częściej w typowych przypadkach realokacja nie być wbudowane w obiekty wywołujące.
* konstrukcja teraz operacje mutacja w basic_string — przydzielić buforów żądaną stanu zamiast zmiany rozmiaru w miejscu. Na przykład wstawianie na początku ciąg teraz przenosi zawartości po wstawieniu dokładnie raz (w dół lub w buforze nowoprzydzielonych), zamiast dwukrotnie w tym przypadku reallocating (nowoprzydzielonych buforu, a następnie w dół).
* Operacje wywoływania biblioteki standardowe C w \<ciąg\> teraz pamięci podręcznej adres errno firmy do usunięcia powtarzane interakcji z protokołem TLS.
* Uproszczony is_pointer — implementacji.
* Zakończono zmiana opartą na strukturze/void_t na podstawie funkcja techniki SFINAE wyrażeń.
* Standardowa biblioteka algorytmów uniknąć teraz postincrementing Iteratory.
* Ostrzeżenia obcięcie stałej, używając 32-bitowych allocators — w systemach 64-bitowych.
* STD::Vector przypisania przenoszenia jest teraz bardziej efektywne w przypadku innych niż alokatora równości z systemem innym niż POCMA przez ponowne użycie buforu, gdy jest to możliwe.

#### <a name="readability-and-other-improvements"></a>Zwiększyć czytelność, a inne ulepszenia
* Standardowa biblioteka teraz używa języka C ++ 14 constexpr bezwarunkowo, zamiast warunkowo zdefiniowane makra.
* Standardowa biblioteka używa teraz szablonów aliasów wewnętrznie.
* Standardowa biblioteka korzysta teraz nullptr wewnętrznego, zamiast nullptr_t {}. (Wewnętrzny użycie wartości NULL została zlikwidowana. Użycie wewnętrznego 0 jako wartość null jest oczyszczany stopniowo.)
* Standardowa biblioteka korzysta teraz std::move() wewnętrznego, zamiast stylistically niewłaściwie korzysta z std::forward().
* Zmienione static_assert (wartość false, "komunikat") do #error wiadomości. Zwiększa to diagnostyki kompilatora, ponieważ #error natychmiastowe zatrzymanie kompilacji.
* Standardowa biblioteka już oznacza funkcji jako __declspec(dllimport). Nowoczesny konsolidatora technologii nie wymaga już to.
* Wyodrębnionego techniki SFINAE do domyślnych argumentów szablonu, który upraszcza w porównaniu do zwrócenia typów i typy argumentów funkcji.
* Sprawdza debugowania \<losowe\> teraz używać maszyn zwykle biblioteki standardowej, zamiast _Rng_abort() wewnętrznej funkcji, która wywołuje fputs() stderr. Implementacja tej funkcji jest zachowywane dla zgodności plików binarnych, ale została usunięta w następnej wersji biblioteki standardowej binarnie niezgodna. 

### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 wersji 15,5 cala
Kilka funkcje standardowej biblioteki zostały dodane, przestarzałe lub usunięte zgodnie z języka C ++ 17 standard. Aby uzyskać więcej informacji, zobacz [ulepszenia zgodność języka C++ w programie Visual Studio](cpp-conformance-improvements-2017.md#improvements_155).

#### <a name="new-experimental-features"></a>Nowe funkcje eksperymentalne
* Obsługa eksperymentalna następujących algorytmów równoległych:
  * all_of
  * any_of
  * for_each
  * for_each_n
  * none_of
  * Zmniejsz
  * replace
  * replace_if
  * sort
* Podpisy dla następujących algorytmów równoległych zostały dodane, ale nie została zrównoleglona w tej chwili; Profilowanie pokazanego żadnych korzyści parallelizing algorytmów tylko przenieść lub permute — elementy:
  * copy
  * copy_n
  * fill
  * fill_n
  * move
  * reverse
  * reverse_copy
  * rotate
  * rotate_copy
  * swap_ranges

#### <a name="performance-fixes-and-improvements"></a>Ulepszenia i wydajności
* basic_string —\<char16_t > teraz angażujący optymalizacje funkcji memcmp/memcpy/itp. tego basic_string —\<wchar_t > angażujący.
* Ograniczenie Optymalizator, który uniemożliwił wskaźników funkcji z możliwości wbudowanego udostępnianych przez naszych "unikać kopiowania funkcji" pracy w Visual Studio 2015 Update 3 zostały działał wokół, przywracanie wydajności lower_bound (iter, iter, wskaźnik funkcji).
* Set_union — został zmniejszony przez Odkodowywanie Iteratory przed zaewidencjonowaniem kolejności i obciążenie debugowania iteratora matki kolejności weryfikacji danych wejściowych w celu obejmuje, set_difference —, set_symmetric_difference —.
* STD::inplace_merge teraz nakłada się na elementy, które już znajdują się w pozycji.
* Konstruowanie std::random_device już tworzy i następnie niszczy std::string.
* STD::Equal i std::partition miały wątkowość skok przebiegu optymalizacji, która zapisuje porównania iteratora.
* Gdy std::reverse przesunie się wskaźniki do typu T trivially copyable, będzie teraz wysyłania odręcznie zwektoryzowane implementacji.
* STD::Fill, std::equal i std::lexicographical_compare zostały nauczanych sposobu wysyłania do funkcji memset / funkcji memcmp std::byte gsl::byte (i innych wyliczeniach char-ish i Wylicz klasy). Należy pamiętać, że std::copy wywołuje przy użyciu is_trivially_copyable i w związku z tym nie wymagają zmiany.
* STL nie zawiera już którego tylko zachowanie było typów innych niż — trivially — które można zniszczyć destruktory puste nawiasy.

#### <a name="correctness-fixes"></a>Poprawność poprawki
* STD::partition teraz wywołuje razy predykatu N zamiast N + 1 godziny jako standard wymaga.
* Naprawiono prób, aby uniknąć magicznych danych statycznych w wątkach w 15 ustęp 3 w 15,5 cala.
* STD::Atomic\<T > nie wymaga już T, aby być domyślnie umożliwia konstrukcji.
* Sterty algorytmów trwać logarytmicznej już do potwierdzenia czasu liniowego, czy dane wejściowe są w rzeczywistości sterty włączenie debugowania iteratora.
* funkcji __declspec(Allocator) jest teraz chroniony dla C1XX zapobiec ostrzeżenia Clang, którego nie rozpoznaje tego declspec.
* basic_string::npos jest teraz dostępna jako stałą czasu kompilacji.
* STD::Allocator teraz poprawnie obsługuje alokacji nadmiernie wyrównane typy — typy, których wyrównania jest większy niż max_align_t — w trybie C ++ 17 (chyba że są wyłączone przez /Zc:alignedNew-).  Na przykład wektory obiektów z wyrównaniem 16 i 32-bajtowych będzie teraz prawidłowo wyrównać dla SSE / instrukcji AVX.


## <a name="other-libraries"></a>Inne biblioteki

### <a name="open-source-library-support"></a>Obsługa biblioteki typu open source  
Vcpkg to narzędzie wiersza polecenia open source, które znacząco upraszcza proces pobierania i tworzenia biblioteki statycznej typu open source C++ i bibliotek DLL w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [vcpkg: Menedżer pakietów dla języka C++](vcpkg.md).

**Visual Studio 2017 wersji 15,5 cala** 

### <a name="cpprest-sdk-290"></a>Zestaw SDK CPPRest 2.9.0  
CPPRestSDK, i platform interfejsu API sieci web dla języka C++, została zaktualizowana do wersji 2.9.0. Aby uzyskać więcej informacji, zobacz [CppRestSDK 2.9.0 jest dostępna w serwisie GitHub](https://blogs.msdn.microsoft.com/vcblog/2016/10/21/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL
* Jeszcze inny zestaw poprawki zgodności wyszukiwanie nazw
* Istniejące konstruktory przenoszenia i przenieść operatory przypisania są teraz prawidłowo oznaczone jako z systemem innym niż zgłaszanie
* Pomiń UN prawidłowy ostrzeżenie C4640 o wątku init bezpieczne z lokalnych danych statycznych w wątkach w atlstr.h
* Wątek bezpiecznego inicjowania lokalnych danych statycznych w wątkach automatycznie był wyłączony w zestawie narzędzi XP podczas [za pomocą ALT i tworzenie biblioteki DLL]. Obecnie taka ewentualność nie zachodzi. W ustawieniach projektu można dodać parametr /Zc:threadSafeInit, jeśli wymagane jest wyłączenie bezpiecznego wątkowo inicjowania. 

### <a name="visual-c-runtime"></a>Środowiska uruchomieniowego Visual C++
* Nowy nagłówek "cfguard.h" Ochrona przepływu sterowania symboli. 

## <a name="c-ide"></a>Środowisko IDE języka C++

* Wydajność wprowadzania zmian w konfiguracji jest teraz lepsza w przypadku natywnych projektów w języku C++ i o wiele lepsza w projektach C++/CLI. W momencie pierwszej aktywacji konfiguracja rozwiązania będzie teraz szybsza, a wszystkie kolejne aktywacje konfiguracji rozwiązania będą prawie natychmiastowe.

**Visual Studio 2017 wersji 15 ustęp 3**:
* Ponownie napisano kilka kreatorów projektu i kodów w stylu okna dialogowego podpisu.
* **Dodaj klasę** teraz bezpośrednio uruchamia Kreator dodawania klasy. Wszystkie elementy, które były wcześniej w tym miejscu są teraz dostępne w obszarze **Dodaj > Nowy element**.
* Win32 projekty są teraz kategorii pulpitu systemu Windows w **nowy projekt** okna dialogowego.
* Szablony konsoli systemu Windows i aplikacji klasycznych umożliwiają teraz tworzenie projektów bez wyświetlania kreatora. W tej samej kategorii jest teraz dostępny Kreator aplikacji klasycznej systemu Windows, który oferuje te same opcje, co poprzednio.

**Visual Studio 2017 wersji 15,5 cala**: operacje kilka C++, które używają aparatu IntelliSense dla nawigacji refaktoryzacji i kod uruchamiane znacznie szybciej. Następujące numery są oparte na rozwiązaniu Visual Studio chromu z projektami 3500: 
|||
|-|-|
|Funkcja|Zwiększenie wydajności| 
|Zmień nazwę|5.3 x| 
|Zmiana podpisu |4.5 x| 
|Znajdź wszystkie odwołania|4,7 x| 

 
 
C++ obsługuje teraz Ctrl + kliknięcie, przejdź do definicji, dzięki łatwo myszy nawigacji do definicji. Wizualizator struktury z pakietu Narzędzia Power wydajności jest teraz również zawarta w produkcie domyślnie.

## <a name="intellisense"></a>IntelliSense  
Nowy aparat bazy danych oparty na SQLite jest teraz używany domyślnie. Przyspieszy to wykonywanie operacji bazy danych, takich jak przechodzenie do definicji i wyszukiwanie wszystkich odwołań, oraz znacznie skróci czas analizy początkowej rozwiązania. Ustawienie został przeniesiony do **narzędzia | Opcje | Edytor tekstu | C/C++ | Zaawansowane** (wcześniej znajdowało się w obszarze... C/C++ | Eksperymentalne).

* Zwiększono wydajność funkcji IntelliSense w projektach i pliki nie używa prekompilowanych nagłówków — automatyczne Prekompilowanego nagłówka, zostanie utworzona dla nagłówków w bieżącym pliku.

* Do listy błędów dodaliśmy filtrowanie błędów i pomoc dotyczącą błędów funkcji IntelliSense. Kliknięcie kolumny błędów umożliwia teraz filtrowanie. Ponadto kliknięcie konkretnego błędu lub naciśnięcie klawisza F1 uruchamia wyszukiwanie online dotyczące danego komunikatu o błędzie.

  ![Lista błędów](media/ErrorList1.png "Lista błędów")

  ![Filtrowana lista błędów](media/ErrorList2.png "Filtrowana lista błędów")

* Dodano możliwość filtrowania listy elementów członkowskich według rodzaju.

  ![Filtrowanie listy elementów członkowskich](media/mlfiltering.png "Filtrowanie listy elementów członkowskich")

* Dodano nową eksperymentalną funkcję Predictive IntelliSense, która pozwala na kontekstowe filtrowanie pozycji wyświetlanych na liście elementów członkowskich. Zobacz [ulepszenia IntelliSense dla C++ - predykcyjnej IntelliSense & filtrowania](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-intellisense-improvements-predictive-intellisense-filtering/)

* Znajdź wszystkie odwołania (Shift + F12), teraz codebases pomaga poruszania łatwe, nawet w przypadku złożonych. Umożliwia grupowanie zaawansowane filtrowanie, sortowanie, wyszukiwanie w wynikach i (w przypadku niektórych języków) kolorowania, dzięki czemu można uzyskać przejrzysty referencje. Dla języka C++ nowy interfejs użytkownika zawiera informacje na temat tego, czy możemy Odczyt lub zapis do zmiennej.

* Funkcja zmiany kropki na strzałkę IntelliSense została przeniesiona z doświadczalnych do zaawansowanych i teraz jest domyślnie włączona. Funkcje edytora Rozwiń zakresy i Rozwiń pierwszeństwo również zostały przeniesione z doświadczalnych do zaawansowanych.

* Eksperymentalne funkcje refaktoryzacji Zmień podpis i Wyodrębnij funkcję są teraz dostępne domyślnie.

* Funkcja eksperymentalna dla języka C++ projektów "Szybsze ładowania projektu". Przy następnym otwarciu projektu w języku C++ będzie on ładować się szybciej, a przy każdym następnym będzie ładować się naprawdę szybko!

Niektóre z tych funkcji są wspólne dla innych języków, a niektóre są specyficzne dla języka C++. Aby uzyskać więcej informacji na temat nowych funkcji, zobacz [Announcing programu Visual Studio "15"](https://blogs.msdn.microsoft.com/visualstudio/2016/10/05/announcing-visual-studio-15-preview-5/). 


## <a name="non-msbuild-projects-with-open-folder"></a>Inne niż MSBuild projektów z otwartym folderze
Visual Studio 2017 wprowadza funkcji "Otwórz Folder", która umożliwia kodu, kompilowanie i debugowanie folderu zawierającego kod źródłowy bez konieczności tworzenia żadnych rozwiązań lub projektów. Dzięki temu można łatwiej rozpocząć pracę z programem Visual Studio, nawet jeśli projekt nie jest częścią projektu MSBuild. Z "Otwórz Folder" można uzyskać dostęp do zaawansowanych kodu, opis, edytowania, kompilowanie i debugowanie funkcji dostępnych w programie Visual Studio już dla projektów MSBuild. Aby uzyskać więcej informacji, zobacz [Otwórz Folder projekty w programie Visual C++](ide/non-msbuild-projects.md).

* Ulepszenia obsługi polecenia Otwórz folder. Środowisko można dostosować za pomocą tych plików json:
  - CppProperties.json dostosowuje obsługę funkcji IntelliSense i przeglądania.
  - Tasks.json dostosowuje kroki kompilacji. 
  - Launch.json dostosowuje obsługę debugowania.

**Visual Studio 2017 wersji 15 ustęp 3**: 
* Ulepszona obsługa alternatywnych kompilatory i środowiska kompilacji, takie jak MinGW i programów Cygwin. Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska MinGW i programów Cygwin Visual C++ i otwórz Folder](https://blogs.msdn.microsoft.com/vcblog/2017/07/19/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
* Dodano obsługę do definiowania globalne i zmienne konfiguracji w danym środowisku "CppProperties.json" i "CMakeSettings.json". Te zmienne środowiskowe mogą być używane przez konfiguracje debugowania definiowane w pliku „launch.vs.json” i zadania w pliku „tasks.vs.json”. Aby uzyskać więcej informacji, zobacz [Dostosowywanie środowiska Visual C++ i otwórz Folder](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/customizing-your-environment-with-visual-c-and-open-folder/).
* Ulepszona obsługa generator Nindżą w CMake, łącznie z możliwością łatwego 64-bitowych platform docelowych.

## <a name="cmake-support-via-open-folder"></a>Obsługa CMake za pośrednictwem Otwórz Folder
Visual Studio 2017 wprowadzono obsługę za pomocą CMake projekty bez konwersji pliki projektu MSBuild (.vcxproj). Aby uzyskać więcej informacji, zobacz [CMake projekty w programie Visual C++](ide/cmake-tools-for-visual-cpp.md). Otwieranie CMake projekty z "Otwórz Folder" zostanie automatycznie skonfigurować środowisko dla języka C++, edytowania, kompilowania i debugowania.

* Funkcja IntelliSense w języku C++ będzie działać bez konieczności tworzenia pliku CppProperties.json w folderze głównym. Wraz z tym dodaliśmy nowe listy rozwijane, aby użytkownicy mogli łatwo przełączać się między konfiguracjami dostarczonymi przez pliki CMake i CppProperties.json.

* Dalsza konfiguracja jest obsługiwana przy użyciu pliku CMakeSettings.json, który znajduje się w tym samym folderze co plik CMakeLists.txt.

  ![Cmake Otwórz folder](media/cmake_cpp.png "CMake Otwórz folder")

**Visual Studio 2017 wersji 15 ustęp 3**: generator Nindżą CMake dodać obsługę. Aby uzyskać więcej informacji, zobacz [CMake projekty w programie Visual C++](ide/cmake-tools-for-visual-cpp.md).  

**Visual Studio 2017 wersji 15,5 cala**: importowanie istniejących CMake dodano obsługę przechowuje w pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [CMake projekty w programie Visual C++](ide/cmake-tools-for-visual-cpp.md).  

## <a name="windows-desktop-development-with-c"></a>Programowanie aplikacji pulpitu systemu Windows za pomocą języka C++  
Zapewniamy obecnie bardziej zaawansowane środowisko instalacji oryginalnego obciążenia C++. Dodaliśmy możliwe do wybrania składniki pozwalające na zainstalowanie tylko tych narzędzi, których potrzebujesz.  Należy pamiętać, że wskazane w interfejsie użytkownika instalatora rozmiary instalacji składników nie są prawidłowe i zaniżają całkowity rozmiar instalacji.

Aby pomyślnie tworzyć projekty Win32 w obciążeniu C++ dla komputerów stacjonarnych, musisz zainstalować zarówno zestaw narzędzi, jak i zestaw SDK systemu Windows. Zainstalowanie zalecanych (zaznaczonych) składników „Zestaw narzędzi „VC++ 2017 w wersji 141 (x86, x64)” oraz „Zestaw SDK systemu Windows 10 (10.0.14393)” da pewność, że będzie to możliwe. Jeśli potrzebne narzędzia nie zostaną zainstalowane, projekty nie będą pomyślnie tworzone i kreator będzie się zawieszać.

**Visual Studio 2017 wersji 15,5 cala**: narzędzia Visual C++ kompilacji (wcześniej dostępne jako autonomiczny produkt) są teraz włączone jako obciążenie w Instalatorze programu Visual Studio. To obciążenie instaluje tylko narzędzia wymagane do tworzenia projektów C++ bez instalowania programu Visual Studio IDE. Uwzględniane są zarówno w wersji 140 i v141 procesami. Zestaw narzędzi v141 zawiera ulepszenia najnowsza w programie Visual Studio 2015 wersji 15,5 cala. Aby uzyskać więcej informacji, zobacz [programu Visual Studio Tools kompilacji zawierają teraz VS2017 i procesami MSVC VS2015](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Tworzenie Linux za pomocą języka C++  
Popularne rozszerzenie [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) stanowi obecnie cześć programu Visual Studio. Ta instalacja zawiera wszystko, czego potrzebujesz do tworzenia i debugowania aplikacji w języku C++ działających w środowisku systemu Linux.  

**Visual Studio 2017 wersji 15,2**: ulepszenia dla wielu platform kodu do udostępniania i typ wizualizacji. Aby uzyskać więcej informacji, zobacz [ulepszenia Linux C++ dla wielu platform kodu do udostępniania i typ wizualizacji](https://blogs.msdn.microsoft.com/vcblog/2017/05/10/linux-cross-platform-and-type-visualization/).

**Visual Studio 2017 wersji 15,5 cala**:
1. Obciążenie systemu Linux została dodana obsługa rsync zamiast protokołu sftp podczas synchronizowania plików do zdalnej maszyny z systemem Linux.  
2. Dodano obsługę wielu elementów docelowych mikrokontrolerów ARM kompilacji. Aby włączyć to w instalacji wybierz programowanie Linux za pomocą obciążenia C++ i wybierz opcję dla osadzonych i rozwoju IoT. Spowoduje to dodanie GCC ARM cross tools kompilacji i udostępnić do instalacji. Aby uzyskać więcej informacji, zobacz [GCC ARM Cross kompilacji, w programie Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/10/23/arm-gcc-cross-compilation-in-visual-studio/).
3. Dodano CMake obsługę. Teraz możesz pracować na istniejący kod CMake podstawowej bez konieczności przekonwertować go do projektu programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu CMake Linux](linux/cmake-linux-project.md).
4. Uruchamianie zadań zdalnego dodano obsługę. Ta funkcja umożliwia uruchamianie polecenia w systemie zdalnym, który jest zdefiniowany w Menedżerze połączeń programu Visual Studio. Zadania zdalne zapewniają również możliwość kopiowania plików do systemu zdalnego. 


## <a name="game-development-with-c"></a>Tworzenie gier z C++  
Pełnych możliwości języka C++ można użyć do tworzenia profesjonalnych gier obsługiwanych przy użyciu zestawu funkcji DirectX lub Cocos2d.  

## <a name="mobile-development-with-c-android-and-ios"></a>Tworzenie przenośnych za pomocą języka C++ (Android i iOS)  
Program Visual Studio umożliwia obecnie programowanie i debugowanie aplikacji mobilnych przeznaczonych dla systemów Android oraz iOS.  

## <a name="universal-windows-apps"></a>Aplikacje uniwersalne systemu Windows  
Język C++ stanowi składnik opcjonalny obciążenia Aplikacja uniwersalna systemu Windows.  Obecnie uaktualnianie projektów C++ należy wykonywać ręcznie. Po otwarciu projektu przeznaczonego dla wersji 140 platformy uniwersalnej systemu Windows (UWP) w programie Visual Studio 2017 musisz wybrać zestaw narzędzi platformy w wersji 141 na stronach właściwości projektu, jeśli nie masz zainstalowanego programu Visual Studio 2015.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nowe opcje dla języka C++ na uniwersalnych platformy systemu Windows (UWP)
Masz teraz nowe opcje zapisu i tworzenia pakietu aplikacji C++ dla platformy uniwersalnej systemu Windows i Sklepu Windows: konwerter aplikacji pulpitu umożliwia pakietu istniejącej aplikacji klasycznych dla wdrożenia za pomocą portalu Sklepu Windows. Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska uruchomieniowego Visual C++ w projekcie Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project/) i [przełączyć aplikację pulpitu do systemu Windows platformy Uniwersalnej z Mostek pulpitu](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root).

**Visual Studio 2017 wersji 15,5 cala**  
A **projekt do tworzenia pakietów aplikacji systemu Windows** zostanie dodany szablon projektu, który obsługuje pakowania aplikacje przy użyciu mostka pulpitu. Jest on dostępny w obszarze **pliku | Nowy | Projekt | Zainstalowane | Visual C++ | Platforma uniwersalna systemu Windows**.

Podczas zapisywania nowego kodu, można teraz używać C + +/ WinRT, standardowe projekcji języka C++ realizowane wyłącznie w pliki nagłówków środowiska uruchomieniowego systemu Windows. Pozwala na obu autora, a korzystanie z interfejsów API środowiska wykonawczego systemu Windows przy użyciu dowolnego ze standardami kompilator języka C++. C + +/ WinRT umożliwia deweloperom C++ z dostępem do najwyższej jakości nowoczesnych interfejsu API systemu Windows. Aby uzyskać więcej informacji, zobacz [C + +/ WinRT dostępne w witrynie GitHub](https://moderncpp.com/). 

Począwszy od programu [kompilacji 17025 Windows SDK niejawnego Preview](https://blogs.windows.com/buildingapps/2017/11/01/windows-10-sdk-preview-build-17025/#ryPH3zAy6yk2cIRX.97), C + +/ WinRT znajduje się w zestawie Windows SDK. Aby uzyskać więcej informacji, zobacz [C + +/ WinRT jest teraz włączone zestaw Windows SDK](https://blogs.msdn.microsoft.com/vcblog/2017/11/01/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="clangc2-platform-toolset"></a>Zestaw narzędzi platformy clang/C2
Zestaw narzędzi Clang/C2 dostarczany z [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] obsługuje teraz przełącznik/bigobj, który ma kluczowe znaczenie podczas kompilowania dużych projektów. Oferuje on również kilka ważnych poprawek, zarówno we frontonie, jak i zapleczu kompilatora.

## <a name="c-code-analysis"></a>Analiza kodu C++

Podstawowe narzędzia do sprawdzania kodu C++ wymuszające stosowanie [podstawowych wytycznych dotyczących języka C++](https://github.com/isocpp/CppCoreGuidelines) są obecnie dystrybuowane z programem Visual Studio. Po prostu włącz narzędzia do sprawdzania w oknie dialogowym Rozszerzenia analizy kodu na stronach właściwości projektu, a rozszerzenia zostaną uwzględnione podczas uruchamiania analizy kodu. Aby uzyskać więcej informacji, zobacz [przy użyciu programy C++ podstawowe wskazówki](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Strona właściwości CppCoreCheck") 

**Visual Studio 2017 wersji 15 ustęp 3**: dodać obsługę zasady dotyczące zarządzania zasobami. 

**Visual Studio 2017 wersji 15,5 cala**: sprawdza nowe C++ podstawowe wskazówki obejmują poprawności wskaźnika inteligentnego, prawidłowe użycie globalnych inicjatory i używa flagowania konstrukcji, takich jak `goto` i zły rzutowania.  
Niektóre numerów ostrzeżeń, które mogą być w 15 ustęp 3 nie będą dostępne w 15,5 cala. Ostrzeżenia zostały zastąpione kontroli bardziej szczegółowe.

## <a name="unit-testing"></a>Testy jednostkowe

**Visual Studio 2017 wersji 15,5 cala**: Adapter testowy Google i karty Boost.Test są teraz dostępne jako składniki **projektowania aplikacji w języku C++** i są zintegrowane z usługą **Eksploratora testów**. Obsługa CTest jest dodawany do projektów Cmake (przy użyciu Otwórz Folder), mimo że pełna integracja z **Eksploratora testów** nie jest jeszcze dostępna. Aby uzyskać więcej informacji, zobacz [dla C/C++ pozwala pisać testy jednostkowe](/visualstudio/test/writing-unit-tests-for-c-cpp).

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostyki grafiki w programie Visual Studio

Diagnostyki grafiki w programie Visual Studio jest zestaw narzędzi dla rejestrowanie i analizowanie renderowania i problemom z wydajnością w aplikacjach Direct3D. Funkcje diagnostyki grafiki można przy użyciu aplikacji uruchomionych lokalnie na komputerze z systemem Windows w emulatorze urządzenia z systemem Windows lub na zdalnym komputerze lub urządzeniu.

* **Dane wejściowe i wyjściowe dla programów do cieniowania wierzchołków i geometrii:** możliwość wyświetlania danych wejściowych i wyjściowych programów do cieniowania wierzchołków i programów do cieniowania geometrycznego był jedną z najbardziej pożądanych funkcji, a teraz jest obsługiwana w narzędziach. Po prostu zaznacz etap VS lub GS w widoku etapy potoku, aby rozpocząć sprawdzanie przychodzących i dane wyjściowe w poniższej tabeli.

  ![Wejścia/wyjścia dla programów do cieniowania](media/io-shaders.png)

* **Wyszukiwanie i filtrowanie w tabeli obiektów:** zapewnia szybki i łatwy sposób znaleźć zasoby szukasz.

  ![Wyszukaj](media/search.png)
   
* **Historia zasobów:** nowy widok zapewnia uproszczony sposób wyświetlenia historii całego modyfikacja zasobu, która była używana podczas renderowania przechwyconej ramce. Aby wywołać historii dla wszystkich zasobów, wystarczy kliknąć ikonę zegara obok hyperlink żadnych zasobów.

  ![Historia zasobów](media/resource-history.png)

  Zostanie wyświetlone nowe okno narzędzi historii zasobów wypełniane przy użyciu historii zmian zasobu.

  ![Zmiana historię zasobu](media/resource-history-change.png)

  Należy pamiętać, że jeśli Twoje przechwycenia z włączone Przechwytywanie stosu wywołania Pełna (**programu Visual Studio | Narzędzia | Opcje | Diagnostyka grafiki**), a następnie kontekście każdego zdarzenia zmiany można szybko ustalona i inspekcji w ciągu projektu programu Visual Studio.  

* **Statystyka interfejsu API:** wyświetlić podsumowanie wysokiego poziomu użycia interfejsu API w sieci ramki. Może to być przydatne w odnajdywaniu wywołań mogą nie uznasz, że wprowadzasz w ogóle lub wywołań tworzonego zbyt dużej ilości. To okno jest dostępny za pośrednictwem **widok | Statystyki interfejsu API** w analizatorze grafiki programu Visual Studio.

  ![Statystyka interfejsu API](media/api-stats.png)

* **Statystyki pamięci:** wyświetlić, ile pamięci sterownik jest przydzielanie zasobów utworzyć w ramce. To okno jest dostępny za pośrednictwem **widok | Statystyki pamięci** w **analizator grafiki programu Visual Studio**. Dane mogą być kopiowane do pliku CSV do wyświetlenia w arkuszu kalkulacyjnym, klikając prawym przyciskiem myszy i wybierając polecenie **Kopiuj wszystko**.

  ![Statystyka pamięci](media/memory-stats.png)
 
* **Sprawdzanie poprawności ramki:** nową listę błędów i ostrzeżeń zapewnia prosty sposób można przejść z listy zdarzeń oparte na potencjalnych problemów wykrytych przez warstwę debugowania Direct3D. Kliknij przycisk **widok | Ramka weryfikacji** w analizatora grafiki programu Visual Studio można otworzyć okna. Następnie kliknij przycisk **Uruchom weryfikację** można rozpocząć analizy. Może upłynąć kilka minut, w zależności od złożoności ramki.

  ![Sprawdzanie poprawności ramki](media/frame-validation.png)
 
* **Ramkę analizy D3D12:** analizy ramek używany do analizowania wydajności wywołania rysowania z skierowane do eksperymentów "co jeśli". Przełącz na kartę analizy ramek i uruchamiać analizę, aby wyświetlić raport. Aby uzyskać więcej informacji, obserwuj [GoingNative 25: analiza ramek grafiki programu Visual Studio](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) wideo.

  ![Analiza ramek](media/frame-analysis.png)

* **Ulepszenia użycia procesora GPU:** otwierać ślady podjęte za pomocą profilera Visual Studio dotyczących użycia procesora GPU z widoku GPU lub narzędzia Analizator wydajności systemu Windows (WPA), aby uzyskać bardziej szczegółowe analizy. Jeśli masz Toolkit wydajności systemu Windows zainstalowana na będzie dwa hiperłącza, jeden dla WPA i drugi dla widoku procesora GPU w prawym dolnym rogu omówienie sesji.

  ![Użycie procesora GPU](media/gpu-usage.png)
 
  Ślady otwarty w widoku procesora GPU za pośrednictwem tego łącza pomocy technicznej synchronizowane powiększanie i przesuwanie na osi czasu między VS i procesora GPU. Pole wyboru w programie VS jest używana do sterowania czy synchronizacji jest włączony, czy nie. 

  ![Widok procesora GPU](media/gpu-view.png) 


