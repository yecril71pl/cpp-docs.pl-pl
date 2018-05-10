---
title: Ulepszenia zgodność C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/11/2018
ms.technology:
- cpp-language
ms.topic: conceptual
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1fd640b838c10e010cf2ea028d5f693cd2e5ba14
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="c-conformance-improvements-in-visual-studio-2017-versions-150-153improvements153-155improvements155-156improvements156-and-157improvements157"></a>Ulepszenia zgodność języka C++ w wersji Visual Studio 2017 15.0, [15 ustęp 3](#improvements_153), [15,5 cala](#improvements_155), [15,6](#improvements_156), i [15.7](#improvements_157)

Obsługę uogólniony constexpr i NSDMI dla wartości zagregowanych kompilator Microsoft Visual C++ jest teraz gotowy do funkcje dodane w standardzie 14 C ++. Należy zauważyć, że w kompilatorze nadal brakuje kilku funkcji ze standardowych języków C++11 i C++98. Zobacz [Visual zgodność języka C++](visual-cpp-language-conformance.md) dla tabeli, która przedstawia bieżący stan kompilatora.

## <a name="c11"></a>C++11

### <a name="expression-sfinae-support-in-more-libraries"></a>Obsługi techniki SFINAE wyrażeń w więcej bibliotek

Kompilator w dalszym ciągu zwiększyć jego obsługę wyrażenie techniki SFINAE, co jest niezbędne do Wnioskowanie argumentu szablonu i podstawienia, której wyrażenia decltype i constexpr mogą być wyświetlane jako parametry szablonu. Aby uzyskać więcej informacji, zobacz [ulepszenia techniki SFINAE wyrażeń w programie Visual Studio RC 2017](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3).

## <a name="c-14"></a>C++ 14

### <a name="nsdmi-for-aggregates"></a>NSDMI dla wartości zagregowanych

Wartość zagregowana jest tablicą lub klasą z żaden konstruktor dostarczane przez użytkownika, żadnych członków prywatnych lub chronionych danych niestatycznych nie klasy podstawowe i żadnych funkcji wirtualnych. Począwszy od wersji programu C ++ 14 agregacji może zawierać inicjatorów elementów członkowskich. Aby uzyskać więcej informacji, zobacz [inicjatorów elementów członkowskich i agreguje](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html).

### <a name="extended-constexpr"></a>Rozszerzone constexpr

Wyrażenia deklarowane jako constexpr teraz mogą zawierać niektóre rodzaje deklaracje, jeśli i przełączyć instrukcje, instrukcje pętli i mutacji obiektów, którego okres istnienia rozpoczął się w obrębie Szacowanie wyrażeń constexpr. Ponadto nie ma wymagań, że funkcja constexpr niestatycznego elementu członkowskiego jest niejawnie const. Aby uzyskać więcej informacji, zobacz [złagodzić ograniczenia w funkcji constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html).

## <a name="c17"></a>C++17

### <a name="terse-staticassert"></a>Wartości Terse static_assert

Parametr komunikatu dla static_assert jest opcjonalny. Aby uzyskać więcej informacji, zobacz [static_assert rozszerzanie, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf).

### <a name="fallthrough-attribute"></a>atrybut [[przepuszczająca]]

W **/std:c ++ 17** trybie atrybutu [[przepuszczająca]] można można używać w kontekście instrukcji switch jako wskazówkę kompilatora ma zachowanie fall-through. Zapobiega to wystawianie ostrzeżenia w takich przypadkach kompilatora. Aby uzyskać więcej informacji, zobacz [słownictwo dla atrybutu [[przepuszczająca]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf).

### <a name="generalized-range-based-for-loops"></a>Uogólniony na podstawie zakresu dla pętli

Oparta na zakresie dla pętli nie wymagają już czy begin() i end() zwracać obiekty tego samego typu. Dzięki temu end() do zwrócenia wartownik jako używane przez zakresów w [v3 zakresu](https://github.com/ericniebler/range-v3) i specyfikacja techniczna zakresy ukończone — ale — nie całkiem — opublikowane. Aby uzyskać więcej informacji, zobacz [uogólnianie opartej na zakresie pętli For](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html).

## <a name="improvements_153"></a> Ulepszenia w programie Visual Studio 2017 wersji 15 ustęp 3

### <a name="constexpr-lambdas"></a>wyrażenia lambda constexpr

Wyrażenia lambda teraz mogą być używane w wyrażeniach stałej. Aby uzyskać więcej informacji, zobacz [Constexpr Lambda](http://open-std.org/JTC1/SC22/WG21/docs/papers/2015/n4487.pdf).

### <a name="if-constexpr-in-function-templates"></a>Jeśli constexpr w szablonach — funkcja

Szablon funkcji może zawierać `if constexpr` instrukcje, aby włączyć rozgałęzianie kompilacji. Aby uzyskać więcej informacji, zobacz [Jeśli constexpr](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0128r1.html).

### <a name="selection-statements-with-initializers"></a>Instrukcje wyboru z inicjatorami

`if` Instrukcji może zawierać inicjatora wprowadza zmiennej w zakresie bloku w instrukcji, do samej siebie. Aby uzyskać więcej informacji, zobacz [instrukcje wyboru za pomocą inicjatora](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0305r1.html).

### <a name="maybeunused-and-nodiscard-attributes"></a>[[maybe_unused]] i [[nodiscard]] atrybutów

Nowe atrybuty o wyłączeniu ostrzeżenia, gdy jednostka nie jest używany, lub utworzyć ostrzeżenie, jeśli wartość zwracana wywołania funkcji są usuwane. Aby uzyskać więcej informacji, zobacz [słownictwo dla atrybutu maybe_unused](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0212r0.pdf) i [propozycji nieużywane atrybutów nodiscard i przepuszczająca](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0068r0.pdf).

### <a name="using-attribute-namespaces-without-repetition"></a>Używanie przestrzeni nazw atrybutu bez powtarzania

Nowej składni, aby włączyć tylko identyfikator jedna przestrzeń nazw na liście atrybutów. Aby uzyskać więcej informacji, zobacz [atrybutów w języku C++](cpp/attributes.md).

### <a name="structured-bindings"></a>Strukturalne powiązania

Teraz jest możliwe w jednej deklaracji do przechowywania wartości z nazwami poszczególnych składników, gdy wartość jest tablicą, std::tuple lub std::pair lub ma wszystkich publicznych niestatyczna elementów członkowskich danych. Aby uzyskać więcej informacji, zobacz [powiązań strukturalnych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf).

### <a name="construction-rules-for-enum-class-values"></a>Zasady konstrukcji wartości wyliczenia — klasa

Brak teraz niejawne/z systemem innym niż — zawężanie konwersji z typ podstawowy dla wyliczenia w zakresie do wyliczenia, gdy jego definicji wprowadza nie modułu wyliczającego i źródło używa składni Inicjalizacja listy. Aby uzyskać więcej informacji, zobacz [reguły konstrukcji dla wyliczenia klasy wartości](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf).

### <a name="capturing-this-by-value"></a>Przechwytywanie * to przez wartość

`*this` w wyrażeniu lambda teraz mogą być przechwytywane przez wartość. Dzięki temu scenariusze, w których wyrażenie lambda jest wywoływana podczas operacji równoległych i asynchroniczne, szczególnie w nowszej architektury maszyny. Aby uzyskać więcej informacji, zobacz [przechwytywania Lambda z \*to przez wartość jako [=,\*to]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html).

### <a name="removing-operator-for-bool"></a>Usuwanie operatora ++ na bool

`operator++` nie jest już obsługiwany na `bool` typów. Aby uzyskać więcej informacji, zobacz [Usuń przestarzałe operator++(bool)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html).

### <a name="removing-deprecated-register-keyword"></a>Usuwanie przestarzałe słowo kluczowe "register"

`register` — Słowo kluczowe, wcześniej przestarzałe i ignorowane przez kompilator, teraz zostanie usunięta z języka. Aby uzyskać więcej informacji, zobacz [Usuń przestarzałe korzystanie z rejestru — słowo kluczowe](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html).

Aby uzyskać pełną listę ulepszenia zgodność się za pomocą programu Visual Studio 2015 Update 3, zobacz [Visual C++ co przez nowy 2003 za pośrednictwem 2015](https://msdn.microsoft.com/en-us/library/mt723604.aspx).

## <a name="improvements_155"></a>  Ulepszenia w programie Visual Studio 2017 wersji 15,5 cala

Funkcje oznaczonej jako [14] dostępnych bezwarunkowo nawet w **/std:c ++ 14** tryb.

### <a name="new-compiler-switch-for-extern-constexpr"></a>Nowy kompilator przełączać extern constexpr

We wcześniejszych wersjach programu Visual Studio, zawsze nadać kompilator `constexpr` zmiennej zewnętrzne nawet wtedy, gdy zmienna została oznaczona jako `extern`. W Visual Studio 2017 wersji 15,5 cala, nowy przełącznik, [/Zc:externConstexpr](build/reference/zc-externconstexpr.md), umożliwia poprawne zachowanie zgodnych standardów. Aby uzyskać więcej informacji, zobacz [połączenie constexpr extern](#extern_linkage).

### <a name="removing-dynamic-exception-specifications"></a>Usuwanie specyfikacje wyjątków dynamicznych

[P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html) specyfikacje wyjątków dynamicznych są przestarzałe w języku C ++ 11. funkcja zostanie usunięta z języka C ++ 17, ale przestarzałe (nadal) `throw()` specyfikacji są przechowywane wyłącznie jako alias `noexcept(true)`. Aby uzyskać więcej informacji, zobacz [usuwania specyfikacji wyjątków dynamicznych i noexcept](#noexcept_removal).

### <a name="notfn"></a>not_fn()

[P0005R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html) `not_fn` zostanie `not1` i `not2`.

### <a name="rewording-enablesharedfromthis"></a>Enable_shared_from_this — sformułować

[P0033R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html) `enable_shared_from_this` został dodany w języku C ++ 11. C ++ 17 Standard aktualizuje specyfikację, aby lepiej obsługiwać niektórych sytuacjach wyjątkowych. [14]

### <a name="splicing-maps-and-sets"></a>Zestawy i łączenia mapy

[P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) ta funkcja umożliwia wyodrębnianie węzłów z kontenerów asocjacyjnej (np. mapy, ustawianie, nieuporządkowane\_mapy nieuporządkowane\_ustawić) której następnie można modyfikować i wstawiać do tego samego kontenera lub innej kontener, który używa tego samego typu węzła. (Typowe przypadek użycia jest używane do wyodrębniania węzeł z `std::map`, należy zmienić wartość klucza i ponownie.)

### <a name="deprecating-vestigial-library-parts"></a>Wycofano części Vestigial biblioteki

[P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html) kilka funkcji standardowej bibliotece C++ zostały zastąpione przez nowsze funkcje całościowo, w przeciwnym razie stwierdzono nie może być bardzo przydatne lub problemów. Te funkcje są przestarzałe oficjalnie w języku C ++ 17.

### <a name="removing-allocator-support-in-stdfunction"></a>Usuwanie std::function alokatora do obsługi

[P0302R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html) przed C ++ 17 szablonu klasy `std::function` ma kilka konstruktorów, które miały argumentu przydzielania. Jednak użycie allocators — w tym kontekście był kłopotliwy i semantykę zostały jasne. Dlatego te contructors zostały usunięte.

### <a name="fixes-for-notfn"></a>Poprawki dla not_fn()

[P0358R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html) nowe treść `std::not_fn` zapewnia obsługę propagacji wartości kategorii w przypadku wywołania otoki.

### <a name="sharedptrt-sharedptrtn"></a>shared_ptr —\<T [] >, shared_ptr\<T [N] >

[P0414R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html) scalanie `shared_ptr` zmienia się z biblioteki podstawy języka C ++ 17. [14]

### <a name="fixing-sharedptr-for-arrays"></a>Ustalania shared_ptr dla tablic

[P0497R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html) rozwiązanie do obsługi shared_ptr dla tablic. [14]

### <a name="clarifying-insertreturntype"></a>Wyjaśnienie insert_return_type

[P0508R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html) asocjacyjnej kontenery z kluczy unikatowych i kontenery Nieuporządkowana z unikatowy kluczy mają funkcji członkowskiej `insert` zwracającą typu zagnieżdżonego `insert_return_type`. Zwracać typ jest teraz zdefiniowany jako specjalizacji typu, który jest sparametryzowana iteratora i NodeType kontenera.

### <a name="inline-variables-for-the-stl"></a>Wbudowane zmienne STL

[P0607R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)

### <a name="annex-d-features-deprecated"></a>Przestarzałe funkcje załącznik D

Załącznik D C++ standard zawiera wszystkie funkcje, które zostały wycofane, łącznie z `shared_ptr::unique()`, `<codecvt>`, i `namespace std::tr1`. Gdy **/std:c ++ 17** jest ustawiona przełącznik kompilatora, prawie wszystkie funkcje standardowej biblioteki w załączniku D są oznaczone jako przestarzałe. Aby uzyskać więcej informacji, zobacz [funkcje standardowej biblioteki w załączniku D są oznaczone jako przestarzałe](#annex_d).

`std::tr2::sys` Przestrzeni nazw w `<experimental/filesystem>` teraz emituje ostrzeżenia dotyczące zaniechania w obszarze **/std:c ++ 14** domyślnie, a teraz zostanie usunięta w obszarze **/std:c ++ 17** domyślnie.

Ulepszone zgodność w iostream, unikając rozszerzenia niestandardowych (w klasie jawne specjalizacje).

Standardowa biblioteka używa teraz zmiennej szablonów wewnętrznie.

Standardowa biblioteka została zaktualizowana w odpowiedzi na C ++ 17 kompilatora zmiany, w tym dodawanie noexcept system typów i usuwania specyfikacje dynamicznie wyjątków.

## <a name="improvements_156"></a>  Ulepszenia w Visual Studio 2017 wersji 15,6

### <a name="c17-library-fundamentals-v1"></a>C ++ 17 biblioteki podstawy V1

[P0220R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) zawiera specyfikacji technicznej podstawowe informacje na temat biblioteki dla języków C ++ 17 do standardowego. Obejmuje aktualizacje \<eksperymentalne tuple/>, \<eksperymentalne/opcjonalnych >, \<eksperymentalne/funkcjonalności >, \<eksperymentalne/any >, \<eksperymentalne/string_view >, \<eksperymentalne/pamięci >, \<eksperymentalne/memory_resource >, a \<eksperymentalne/algorytm >.

### <a name="c17-improving-class-template-argument-deduction-for-the-stl"></a>C ++ 17 poprawy klasy Wnioskowanie argumentu szablonu dla STL

[P0739R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html) Przenieś `adopt_lock_t` początku listy parametrów dla `scoped_lock` umożliwiające spójne używanie `scoped_lock`. Zezwalaj na `std::variant` konstruktora, aby uczestniczyć w Rozpoznanie przeciążenia przypadków więcej, aby włączyć przypisania kopiowania.

## <a name="improvements_157"></a> Ulepszenia w Visual Studio 2017 wersji 15.7

### <a name="c17-rewording-inheriting-constructors"></a>C ++ 17 Rewording konstruktory dziedziczące

[P0136R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html) Określa, że **przy użyciu** deklaracji, która teraz nazwy konstruktora sprawia, że odpowiednie podstawowa konstruktorów klasy widoczne dla operacji inicjowania klasy pochodnej, zamiast deklarowanie dodatkowe pochodnych konstruktory klas. Jest to zmiana z C ++ 14. W Visual Studio 2017 wersji 15.7 i nowszym w **/std:c ++ 17** trybu, kod, który jest prawidłowy w języku C ++ 14 i używa konstruktory dziedziczące może być nieprawidłowy lub mogą mieć różne semantyki.

W poniższym przykładzie przedstawiono C ++ 14 zachowanie:

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n) = delete; // Error C2280
};

B b(42L); // Calls B<long>(long), which calls A(int)
          //  due to substitution failure in A<long>(long).
```

W poniższym przykładzie przedstawiono **/std:c ++ 17** zachowania w programie Visual Studio 15.7:

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n)
    {
        //do something
    }
};

B b(42L); // now calls B(int)
```

### <a name="c17-extended-aggregate-initialization"></a>C ++ 17 rozszerzone inicjowania agregacji

[P0017R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)

Jeśli jest konstruktor klasy podstawowej niepubliczne, ale dostępna dla klasy pochodnej, następnie w obszarze **/std:c ++ 17** tryb w programie Visual Studio wersja 15.7 pustymi nawiasami klamrowymi już służy do zainicjowania obiektu typu pochodnego.

W poniższym przykładzie przedstawiono C ++ 14 zgodność zachowanie:

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};

Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

W języku C ++ 17 `Derived` została uznana za agregacji typu; w związku z tym inicjowanie `Base` za pośrednictwem prywatnego domyślnego konstruktora sytuacji bezpośrednio jako część reguły rozszerzonej inicjalizacji agregacji. Wcześniej `Base` Konstruktor prywatny została wywołana za pomocą `Derived` Konstruktor i zakończyło się pomyślnie z powodu deklaracja friend.

W poniższym przykładzie przedstawiono C ++ 17 zachowanie w wersji Visual Studio 15.7 w **/std:c ++ 17** tryb:

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};

Derived d1; // OK. No aggregate init involved.

Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C ++ 17 deklarowanie bez typu parametrów szablonu z funkcją automatycznego

[P0127R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)

W **/std:c ++ 17** trybie kompilator teraz można wywnioskować typu argumentu szablonu bez typu, który jest zadeklarowana z **automatycznie**:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

Jeden wpływ ta nowa funkcja nie może być nieprawidłowy prawidłowy kodu C ++ 14 lub może być semantykę różną. Na przykład niektóre przeciążenia, które były wcześniej nieprawidłowe są teraz prawidłowe. W poniższym przykładzie przedstawiono kodu C ++ 14 kompilowany, ponieważ wywołanie `foo(p)` jest powiązany z `foo(void*);`. W programie Visual Studio 2017 wersji 15.7 w **/std:c ++ 17** trybie `foo` szablonu funkcji jest najlepsze dopasowanie.

```cpp
template <int N> struct A;
template <typename T, T N> int foo(A<N>*) = delete;

void foo(void *);

void bar(A<0> *p)
{
    foo(p); // OK in C++14
}
```

W poniższym przykładzie przedstawiono C ++ 17 kodu w programie Visual Studio 15.7 w **/std:c ++ 17** tryb:

```cpp
template <int N> struct A;
template <typename T, T N> int foo(A<N>*);

void foo(void *);

void bar(A<0> *p)
{
    foo(p); // C2280: 'int foo<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C ++ 17 podstawowe konwersji ciągów (częściowe)

[P0067R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html) funkcje niskiego poziomu, niezależne od ustawień regionalnych dla konwersji między liczbami całkowitymi i ciągi oraz między liczb zmiennoprzecinkowych i ciągów. (Począwszy od programu Visual Studio 15.7 Preview 2, obsługiwane tylko liczb całkowitych.)

### <a name="c20-avoiding-unnecessary-decay-partial"></a>Unikanie niepotrzebnych 20 c ++ decay — (częściowe)

[P0777R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf) dodaje rozróżnianie między pojęcie "decay" oraz czy po prostu usunięcia const lub kwalifikatory odwołania.  Nowy typ cechy `remove_reference_t` zastępuje `decay_t` w niektórych kontekstach. Obsługa `remove_cvref_t` nie jest jeszcze zaimplementowany począwszy od wersji programu Visual Studio 2017 15.7 Preview 2.

### <a name="c17-parallel-algorithms"></a>C ++ 17 algorytmy równoległe

[P0024R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html) równoległości usług terminalowych została włączona do standard, z drobne zmiany.

### <a name="c17-hypotx-y-z"></a>C ++ 17 hypot — (x, y, z)

[P0030R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf) dodaje trzech przeciążeń nowe do `std::hypot`, dla typów **float**, **podwójne**, i **podwójnej długości**, z których każda ma trzy parametry wejściowe.

### <a name="c17-filesystem"></a>C ++ 17 \<filesystem >

[P0218R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html) przyjmuje usług terminalowych systemu plików do standard z kilku modyfikacje treść.

### <a name="c17-mathematical-special-functions"></a>C ++ 17 specjalne funkcje matematyczne

[P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) przyjmuje poprzedniej techniczne dla specjalnych funkcji matematycznych w standardowej \<cmath > nagłówka.

### <a name="c17-deduction-guides-for-the-stl"></a>C ++ 17 wnioskowanie przewodników dotyczących STL

[P0433R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html) aktualizacje STL, aby móc korzystać z języka C ++ 17 przyjęcia [P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html), która dodaje obsługę Wnioskowanie argumentu szablonu klasy.

### <a name="c17-repairing-elementary-string-conversions"></a>Konwersje ciągu języka c ++ 17 naprawianie podstawowe

[P0682R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0682r1.html) nowych funkcji konwersji ciągu podstawowe z P0067R5 przenosić do nowego nagłówka \<charconv > i innych poprawiają, łącznie ze zmianą obsługi błędów można wykorzystać `std::errc` zamiast `std::error_code`.

### <a name="c17-constexpr-for-chartraits-partial"></a>C ++ 17 constexpr dla char_traits (częściowe)

[P0426R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html) zmienia się na `std::traits_type` funkcje Członkowskie `length`, `compare`, i `find` Aby wprowadzić `std::string_view` można używać w wyrażeniach stałej. (W programie Visual Studio 2017 wersji 15,6, obsługuje Clang/LLVM tylko. W wersji 15.7 Preview 2, pomocy technicznej jest niemal ukończyć w celu ClXX również.)

## <a name="bug-fixes-in-visual-studio-versions-150-153update153-155update155-and-157update157"></a>Poprawki błędów w wersji programu Visual Studio 15.0, [15 ustęp 3](#update_153), [15,5 cala](#update_155), i [15.7](#update_157)

### <a name="copy-list-initialization"></a>Copy-list-initialization

Visual Studio 2017 poprawnie zgłasza błędy kompilatora dotyczące tworzenia obiektów przy użyciu listy inicjatorów, które nie zostały przechwycono w programie Visual Studio 2015 i może prowadzić do awarii lub niezdefiniowane zachowanie środowiska wykonawczego. Zgodnie z harmonogramem 13.3.1.7p1 N4594, w kopiowania listy Inicjalizacja kompilator należy wziąć pod uwagę jawny Konstruktor Rozpoznanie przeciążenia, ale musi Zgłoś błąd, jeśli faktycznie jest wybierany tego przeciążenia.

Dwa poniższe przykłady kompilacji w programie Visual Studio 2015, ale nie w programie Visual Studio 2017 r.

```cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 }; // error C3445: copy-list-initialization of 'A' cannot use an explicit constructor
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot convert from 'int' to 'const A &'

}
```

Aby naprawić błąd, użyj bezpośredniego inicjowania:

```cpp
A a1{ 1 };
const A& a2{ 1 };
```

W programie Visual Studio 2015 kompilator błędnego traktowane Inicjalizacja listy kopii na w taki sam sposób jak regularne inicjacja kopii; uważa się jedynie konwertowanie konstruktorów Rozpoznanie przeciążenia. W poniższym przykładzie programu Visual Studio 2015 wybiera MyInt(23), ale 2017 usługi Visual Studio niepoprawnie zgłasza błąd.

```cpp
// From http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html#1228
struct MyStore {
    explicit MyStore(int initialCapacity);
};

struct MyInt {
    MyInt(int i);
};

struct Printer {
    void operator()(MyStore const& s);
    void operator()(MyInt const& i);
};

void f() {
    Printer p;
    p({ 23 }); // C3066: there are multiple ways that an object of this type can be called with these arguments
}
```

W tym przykładzie jest podobna do poprzedniego, ale wywołuje inny błąd. Powiedzie się w programie Visual Studio 2015, a nie powiedzie się w programie Visual Studio 2017 z C2668.

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```

### <a name="deprecated-typedefs"></a>Przestarzałe elementy TypeDef

Visual Studio 2017 wystawia teraz poprawne ostrzeżenie dotyczące przestarzałe definicje typów, które są zadeklarowane w klasie lub strukturze. W poniższym przykładzie kompiluje bez ostrzeżeń w Visual Studio 2015, ale tworzy C4996 w programie Visual Studio 2017 r.

```cpp
struct A
{
    // also for __declspec(deprecated)
    [[deprecated]] typedef int inttype;
};

int main()
{
    A::inttype a = 0; // C4996 'A::inttype': was declared deprecated
}
```

### <a name="constexpr"></a>constexpr

2017 usługi Visual Studio niepoprawnie zgłasza błąd, gdy lewostronny operand warunkowo oszacowania operacja jest nieprawidłowa w kontekście constexpr. Poniższy kod kompiluje w programie Visual Studio 2015, ale nie w programie Visual Studio 2017 (C3615 funkcji constexpr "f" nie może być wyrażeniem stałym):

```cpp
template<int N>
struct array
{
    int size() const { return N; }
};

constexpr bool f(const array<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615
}
```

Aby naprawić błąd, albo zadeklarować `array::size()` działać jako `constexpr` lub usuń `constexpr` kwalifikator z `f`.

### <a name="class-types-passed-to-variadic-functions"></a>Typy klas przekazany do funkcji ze zmienną liczbą argumentów

W programie Visual Studio 2017 r klasy lub struktury, które są przekazywane do funkcji ze zmienną liczbą argumentów printf musi być trivially copyable. Podczas przekazywania takie obiekty, kompilator po prostu tworzy kopię bitowe i nie mogą wywoływać konstruktora lub destruktora.

```cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function.
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```

Aby naprawić błąd, można wywołać funkcji członkowskiej zwracającej typu trivially copyable

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

Możesz też wykonać rzutowania statycznego, aby przekonwertować obiekt przed przekazaniem go:

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

Ciągi wbudowane i zarządzane przy użyciu CStringW dostępnego `operator LPCWSTR()` powinien być używany do rzutowania obiektu CStringW na wskaźnik C oczekiwany przez ciąg formatu.

```cpp
CStringW str1;
CStringW str2;
str1.Format(L"%s", static_cast<LPCWSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>kwalifikatorów CV konstrukcji klasy

W programie Visual Studio 2015 Kompilator ignoruje czasami niepoprawnie kwalifikatorów cv podczas generowania obiektu klasy za pośrednictwem wywołania konstruktora. To może potencjalnie spowodować awarię lub nieoczekiwane zachowanie. W poniższym przykładzie kompiluje w programie Visual Studio 2015, ale zgłasza błąd kompilatora w Visual Studio 2017:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Aby naprawić błąd, należy zadeklarować `operator int()` jako `const`.

### <a name="access-checking-on-qualified-names-in-templates"></a>Sprawdzanie nazwy kwalifikowane w szablonach dostępu

Poprzednie wersje kompilatora nie wykonał dostępu sprawdzanie na nazwy kwalifikowane w niektórych kontekstach szablonu. Może to utrudniać oczekiwane zachowanie techniki SFINAE, których można oczekiwać podstawienie się niepowodzeniem z powodu inaccessibility nazwy. To może potencjalnie spowodował awarię lub nieoczekiwanego zachowania w czasie wykonywania z powodu kompilatora niepoprawnie wywoływania niewłaściwy przeciążenia operatora. W programie Visual Studio 2017 r wystąpi błąd kompilatora jest wywoływane. Ten błąd może się różnić, ale zazwyczaj jest "Nie zgodnej przeciążonej funkcji znaleziono C2672". Poniższy kod kompiluje w programie Visual Studio 2015, ale zgłasza błąd w programie Visual Studio 2017:

```cpp
#include <type_traits>

template <class T> class S {
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x);

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```

### <a name="missing-template-argument-lists"></a>Brak listy argumentów szablonu

W programie Visual Studio 2015 i starszych kompilator nie diagnozowanie brakuje listy argumentów szablonu podczas szablonu znajdowały się na liście parametrów szablonu (na przykład jako część domyślnego argumentu szablonu lub parametr szablonu bez typu). Może to spowodować nieprzewidywalne zachowanie, w tym kompilatora awarii (Crash) lub nieoczekiwane zachowanie. Poniższy kod kompiluje w programie Visual Studio 2015, ale powoduje błąd w programie Visual Studio 2017 r.

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Techniki SFINAE wyrażeń

Do obsługi techniki SFINAE wyrażeń, kompilator teraz analizuje decltype argumenty podczas szablony są zadeklarowane zamiast wystąpienia. W związku z tym jeśli specjalizacji zależny od innych niż zostanie znaleziony w argumencie decltype, nie została odroczona do czasu wystąpienia i jest przetwarzany natychmiast i wyniki są zdiagnozowany w tym czasie.

W poniższym przykładzie przedstawiono takie wystąpi błąd kompilatora, która jest zgłaszane w punkcie deklaracji:

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT>
class IsCallable
{
public:
    struct BadType {};

    template <class U>
    static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>

    template <class U>
    static BadType Test(...);

    static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

### <a name="classes-declared-in-anonymous-namespaces"></a>Klasy zadeklarowany w anonimowej przestrzeni nazw

Zgodnie z C++ standard klasy zadeklarowanej w anonimowej przestrzeni nazw ma połączenie zewnętrzne i nie można wyeksportować. W programie Visual Studio 2015 i starszych wersji ta reguła nie była wymuszana. W programie Visual Studio 2017 reguła częściowo jest wymuszana. Poniższy przykład wywołuje ten błąd wystąpił w Visual Studio 2017: "Błąd C2201: const namespace::S1::vftable anonimowe: musi mieć zewnętrzne połączenie w celu eksportu/importu."

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>Domyślne Inicjatory dla wartości klasy elementów członkowskich (C + +/ CLI)

W programie Visual Studio 2015 i starszych kompilator dozwolone, ale ignorowane inicjator elementu członkowskiego domyślnej dla elementu członkowskiego klasy wartości. Inicjowanie domyślnych klasy wartości zawsze zero inicjuje członków; domyślny konstruktor nie jest dozwolone. W programie Visual Studio 2017 r domyślny element członkowski inicjatory podnieść wystąpi błąd kompilatora w poniższym przykładzie:

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // is not allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Indeksatory domyślne (C + +/ CLI)

W programie Visual Studio 2015 i starszych kompilatora w niektórych przypadkach misidentified właściwości domyślnej jako indeksatora domyślne. Było możliwe obejść ten problem, korzystając z identyfikatora `default` do dostępu do właściwości. Obejście sam stały się problemem po `default` wprowadzono słowo kluczowe języka C ++ 11. W związku z tym w programie Visual Studio 2017 usterki, które wymagane obejście zostały usunięte, a kompilator teraz zgłasza błąd, gdy `default` umożliwia dostęp do właściwości domyślnej klasy.

```cpp
//class1.cs

using System.Reflection;
using System.Runtime.InteropServices;

namespace ClassLibrary1
{
    [DefaultMember("Value")]
    public class Class1
    {
        public int Value
        {
            // using attribute on the return type triggers the compiler bug
            [return: MarshalAs(UnmanagedType.I4)]
            get;
        }
    }
    [DefaultMember("Value")]
    public class Class2
    {
        public int Value
        {
            get;
        }
    }
}

// code.cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value; // error
       r1->default;
       r2->Value;
       r2->default; // error
}
```

W programie Visual Studio 2017 r aby dostęp do obu wartości właściwości według nazwy:

```cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="update_153"></a> Wprowadzono poprawki błędów w programie Visual Studio 2017 wersji 15 ustęp 3

### <a name="calls-to-deleted-member-templates"></a>Wywołania szablonów usuniętego elementu członkowskiego

W poprzednich wersjach programu Visual Studio kompilatora w niektórych przypadkach może nie Emituj błędu dla wywołań źle sformułowany szablon usuniętego elementu członkowskiego, który może potencjalnie został spowodowany awarii w czasie wykonywania. Poniższy kod tworzy teraz C2280, "" int S\<int >:: f\<int > (void) ": próba odwania usunięta funkcja do":

```cpp
template<typename T>
struct S {
   template<typename U> static int f() = delete;
};

void g()
{
   decltype(S<int>::f<int>()) i; // this should fail
}
```

Aby naprawić błąd, należy zadeklarować i jako `int`.

### <a name="pre-condition-checks-for-type-traits"></a>Sprawdza, czy warunek wstępny cech typu w kompilatorze

Visual Studio 2017 wersji 15 ustęp 3 poprawia cech typu do bardziej ściśle zgodne ze standardem sprawdza, czy warunek wstępny. Dotyczy jednego takiego wyboru można przypisać. Poniższy kod tworzy C2139 w programie Visual Studio 2017 wersji 15 ustęp 3:

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Nowe ostrzeżenie kompilatora i środowiska uruchomieniowego kontroli organizowanie native zarządzane

Wywołania z funkcji zarządzanego do natywnej funkcji wymaga kierowania. Środowisko CLR wykonuje przekazywanie, ale nie rozpoznaje semantykę języka C++. Jeśli obiekt natywny przekazanie przez wartość, CLR wywołuje Konstruktor kopiujący obiektu lub używa BitBlt, co może spowodować niezdefiniowane zachowanie w czasie wykonywania.

Teraz kompilator emituje ostrzeżenie, jeśli może znać w czasie kompilacji, obiekt natywny z elementu ctor kopiowania usunięto przekazywane między granic natywnych i zarządzanych przez wartość. Dla tych przypadków, w których kompilator nie może ustalić w czasie kompilacji go injects Sprawdzanie czasu wykonywania, aby program wywołuje `std::terminate` natychmiast, gdy źle sformułowane kierowania występuje. W programie Visual Studio 2017 wersji 15 ustęp 3, poniższy kod tworzy ostrzeżenie C4606 ""A": przekazywanie argumentów poprzez wartość granicy natywnych i zarządzanych wymaga prawidłowej kopii konstruktora. W przeciwnym razie zachowania w czasie wykonywania jest niezdefiniowana".

```cpp
class A
{
public:
   A() : p_(new int) {}
   ~A() { delete p_; }

   A(A const &) = delete;
   A(A &&rhs) {
   p_ = rhs.p_;
}

private:
   int *p_;
};

#pragma unmanaged

void f(A a)
{
}

#pragma managed

int main()
{
    f(A()); // This call from managed to native requires marshalling. The CLR doesn't understand C++ and uses BitBlt, which results in a double-free later.
}
```

Aby naprawić błąd, należy usunąć `#pragma managed` dyrektywy oznaczyć wywołującego jako natywną i uniknąć kierowania.

### <a name="experimental-api-warning-for-winrt"></a>Eksperymentalne ostrzeżenie interfejsu API dla WinRT

Interfejsy API WinRT, które są wydawane dla ozdobione eksperymenty i opinie `Windows.Foundation.Metadata.ExperimentalAttribute`. W programie Visual Studio 2017 wersji 15 ustęp 3 kompilator generuje ostrzeżenie C4698 po napotkaniu atrybutu. Kilka interfejsów API w poprzednich wersjach zestawu Windows SDK ma już zostały oznaczone atrybutu i wywołań do tych interfejsów API teraz wyzwalać to ostrzeżenie kompilatora. Nowsze zestawy Windows SDK ma atrybut usunięte ze wszystkich typów wysłane, ale jeśli używasz starszej zestawu SDK, należy pominąć te ostrzeżenia dla wszystkich wywołań dostarczana typów.

Poniższy kod tworzy ostrzeżenie C4698: "" Windows:: magazynu:: IApplicationDataStatics2::GetForUserAsync"jest ocena tylko celów i mogą ulec zmianie lub usuwania w przyszłych aktualizacji":

```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); //C4698
```

Aby wyłączyć ostrzeżenia, Dodaj #pragma:

```cpp
#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>Wiersza definicji funkcji członkowskiej szablonu

Visual Studio 2017 wersji 15 ustęp 3 generuje błąd po napotkaniu-wiersza definicji funkcji członkowskiej szablon, który nie został zadeklarowany w klasie. Poniższy kod tworzy teraz błąd C2039: "f": nie jest członkiem elementu ":

```cpp
struct S {};

template <typename T>
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

Aby naprawić błąd, Dodaj oświadczenie do klasy:

```cpp
struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Podjęto próbę przyjąć adresu wskaźnika "this"

W języku C++ `this` jest prvalue bez typu wskaźnika do X. Nie można przyjąć adresu `this` lub powiązać odwołania do wartości. W poprzednich wersjach programu Visual Studio kompilator umożliwi obejść to ograniczenie, wykonując rzutowanie. W programie Visual Studio 2017 wersji 15 ustęp 3 kompilator generuje błąd C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Konwersja do niedostępnej klasy podstawowej

Visual Studio 2017 wersji 15 ustęp 3 tworzy wystąpił błąd podczas próby konwersji typu do klasy podstawowej, która jest niedostępna. Kompilator teraz zgłasza "Błąd C2243:"rzutowanie typu": konwersja z miał *" do "B *" istnieje, ale jest niedostępna ". Poniższy kod jest źle sformułowany i może powodować awarie w czasie wykonywania. Kompilator generuje teraz C2243 po napotkaniu kodu w następujący sposób:

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-are-not-allowed-on-out-of-line-definitions-of-member-functions"></a>Argumenty domyślne są niedozwolone w poza wiersza definicje funkcji Członkowskich

Argumenty domyślne są niedozwolone w definicji wiersza funkcji Członkowskich w klasach szablonu kompilator wyświetli ostrzeżenie w obszarze **/ ograniczająca**i poważny błąd w obszarze **/ ograniczająca-**.

W poprzednich wersjach programu Visual Studio poniższy kod źle sformułowane może powodować awarię środowiska wykonawczego. Visual Studio 2017 wersji 15 ustęp 3 generuje ostrzeżenie C5034: "A\<T >:: f": definicja wiersza elementu członkowskiego szablonu klasy nie może mieć argumentów domyślnych:

```cpp
template <typename T>
struct A {
    T f(T t, bool b = false);
};

template <typename T>
T A<T>::f(T t, bool b = false) // C5034
{
    // ...
}
```

Aby naprawić błąd, należy usunąć `= false` domyślny argument.

### <a name="use-of-offsetof-with-compound-member-designator"></a>Użycie makra offsetof z określeniem złożony element członkowski

W programie Visual Studio 2017 r wersji 15 ustęp 3, za pomocą `offsetof(T, m)` gdzie *m* jest "desygnator złożony element członkowski" powoduje ostrzeżenie podczas kompilowania z **/ścian** opcji. Poniższy kod jest źle sformułowany i może powodować awarie w czasie wykonywania. Visual Studio 2017 wersji 15 ustęp 3 tworzy "ostrzeżenie C4841: użyte rozszerzenie niestandardowe: oznaczeniem złożony element członkowski w makra offsetof":

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

Aby naprawić kod, wyłącz ostrzeżenia o pragma lub zmień kod, aby nie używać `offsetof`:

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Za pomocą makra offsetof statycznego elementu członkowskiego danych lub funkcji członkowskiej

W programie Visual Studio 2017 r wersji 15 ustęp 3, za pomocą `offsetof(T, m)` gdzie *m* odwołuje się do elementu członkowskiego danych statycznych lub element członkowski funkcji powoduje błąd. Poniższy kod tworzy "Błąd C4597: niezdefiniowane zachowanie: makro offsetof zastosowane do funkcji członkowskiej"foo"" i "Błąd C4597: niezdefiniowane zachowanie: makro offsetof zastosowane do elementu członkowskiego danych statycznych"bar"":

```cpp
#include <cstddef>

struct A {
   int foo() { return 10; }
   static constexpr int bar = 0;
};

constexpr auto off = offsetof(A, foo);
constexpr auto off2 = offsetof(A, bar);
```

Ten kod jest źle sformułowany i może powodować awarie w czasie wykonywania. Aby naprawić błąd, zmianę kodu można już wywołać niezdefiniowane zachowanie. To jest kod nieprzenośne jest zabronione przez C++ standard.

### <a name="declspec"></a> Nowe ostrzeżenie o atrybutach declspec

W programie Visual Studio 2017 wersji 15 ustęp 3, kompilator nie jest już ignoruje atrybuty Jeśli `__declspec(...)` zostanie zastosowany przed `extern "C"` Specyfikacja powiązania. Wcześniej kompilator będzie ignorować atrybut, który może mieć wpływ na środowisko uruchomieniowe. Gdy **/ścian** i **wx** opcje są ustawione, poniższy kod tworzy "ostrzeżenie C4768: atrybuty __declspec przed Specyfikacja powiązania są ignorowane":

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Aby usunąć to ostrzeżenie, najpierw należy umieścić zewnętrzne "C":

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

To ostrzeżenie jest wyłączone domyślnie w 15 ustęp 3, ale na przez domyślne 15,5 cala i tylko na środowisko kodu skompilowanego z **/ścian** **wx**.

### <a name="decltype-and-calls-to-deleted-destructors"></a>decltype i wywołania usunięte destruktorów

W poprzednich wersjach programu Visual Studio kompilator nie wykrył wywołanie destruktora usuniętego problemu w kontekście wyrażenia skojarzonego z "decltype". W programie Visual Studio 2017 wersji 15 ustęp 3, poniższy kod tworzy "Błąd C2280:" A\<T >:: ~ A(void) ": próba odwania usunięta funkcja do":

```cpp
template<typename T>
struct A
{
   ~A() = delete;
};

template<typename T>
auto f() -> A<T>;

template<typename T>
auto g(T) -> decltype((f<T>()));

void h()
{
   g(42);
}
```

### <a name="uninitialized-const-variables"></a>Niezainicjowanych zmiennych const

Visual Studio 2017 RTW wersji miał regresji, w którym kompilator języka C++ może nie wystawiać Diagnostyka Jeśli zmienna "const" nie został zainicjowany. Regresja ten został rozwiązany w programie Visual Studio 2017 wersji 15 ustęp 3. Poniższy kod tworzy teraz "ostrzeżenie C4132:"Wartość": obiekt const powinien być inicjowany jako":

```cpp
const int Value; //C4132
```

Aby naprawić błąd, można przypisać wartości do `Value`.

### <a name="empty-declarations"></a>Deklaracje pusty

Visual Studio 2017 wersji 15 ustęp 3 teraz ostrzega w deklaracjach puste dla wszystkich typów, nie tylko wbudowane typy. Poniższy kod tworzy teraz ostrzeżenie C4091 poziom 2 do wszystkie deklaracje cztery:

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

Aby usunąć ostrzeżenia, po prostu komentarz lub usuń puste deklaracji. W przypadkach, gdy nie nazwany obiektu ma obowiązywać po stronie (np. RAII) powinien mieć nazwę.

To ostrzeżenie jest wyłączone na podstawie **/WV: 18** i jest domyślnie w obszarze ostrzeżenie W2 poziomu.

### <a name="stdisconvertible-for-array-types"></a>STD::is_convertible dla tablic

Poprzednie wersje kompilatora nadać niepoprawne wyniki dla [std::is_convertible](standard-library/is-convertible-class.md) dla tablic. To wymagane autorów biblioteki, aby specjalny przypadek kompilator Microsoft Visual C++ przy użyciu `std::is_convertible<...>` typu cechy. W poniższym przykładzie statycznych potwierdzeń przebiegu we wcześniejszych wersjach programu Visual Studio, ale się nie powieść w Visual Studio 2017 wersji 15 ustęp 3:

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>` jest obliczana na podstawie sprawdzania, jeśli definicja funkcji urojony jest poprawnie sformułowany:

```cpp
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdisconstructible"></a>Destruktory prywatnych i std::is_constructible

Poprzednie wersje kompilatora ignorowane czy destruktora jest prywatny, podczas podejmowania decyzji o wynik [std::is_constructible](standard-library/is-constructible-class.md). Teraz uzna je. W poniższym przykładzie statycznych potwierdzeń przebiegu we wcześniejszych wersjach programu Visual Studio, ale się nie powieść w Visual Studio 2017 wersji 15 ustęp 3:

```cpp
#include <type_traits>

class PrivateDtor {
   PrivateDtor(int) { }
private:
   ~PrivateDtor() { }
};

// This assertion used to succeed. It now correctly fails.
static_assert(std::is_constructible<PrivateDtor, int>::value);
```

Destruktory prywatnej spowodować, że typ nie umożliwia konstrukcji. `std::is_constructible<T, Args...>` jest obliczana tak, jakby zostały zapisane następujące oświadczenie:

```cpp
   T obj(std::declval<Args>()...)
```

To wywołanie wymaga wywołania destruktora.

### <a name="c2668-ambiguous-overload-resolution"></a>C2668: Rozpoznanie przeciążenia niejednoznaczne

Poprzednie wersje kompilatora czasami nie można wykryć niejednoznaczności znalezione wielu kandydatów za pośrednictwem zarówno przy użyciu deklaracje i argument odnośników zależnych. Może to prowadzić do niewłaściwej przeciążenia wybierana i nieoczekiwane zachowanie. W poniższym przykładzie programu Visual Studio 2017 wersji 15 ustęp 3 poprawnie wywołuje C2668 "f": niejednoznaczne wywołanie przeciążonej funkcji:

```cpp
namespace N {
   template<class T>
   void f(T&, T&);

   template<class T>
   void f();
}

template<class T>
void f(T&, T&);

struct S {};
void f()
{
   using N::f;

   S s1, s2;
   f(s1, s2); // C2668
}
```

Aby naprawić kod, należy usunąć przy użyciu `N::f` instrukcję, jeśli zamierzasz wywołać `::f()`.

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660: deklaracje funkcji lokalnej i odnośników zależnych argument

Deklaracje funkcji lokalnej ukrywa deklaracji funkcji w otaczającym zakresie i Wyłącz odnośników zależnych argumentu. Jednakże poprzednie wersje kompilatora wykonywane argument odnośników zależnych w takim przypadku prowadzącego do nieprawidłowego przeciążenia wybierana i nieoczekiwane zachowanie. Zazwyczaj przyczyną błędu jest nieprawidłowy podpis deklaracji funkcji lokalnej. W poniższym przykładzie programu Visual Studio 2017 wersji 15 ustęp 3 poprawnie wywołuje C2660 "f": funkcja nie przyjmuje argumentów 2:

```cpp
struct S {};
void f(S, int);

void g()
{
   void f(S); // C2660 'f': function does not take 2 arguments:
   // or void f(S, int);
   S s;
   f(s, 0);
}
```

Aby rozwiązać ten problem, zmień `f(S)` podpisu lub usuń go.

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038: Wyświetla listę kolejności inicjowania w inicjatorze

Elementy członkowskie klasy są inicjowane w kolejności, które zostały zgłoszone, nie pojawiają się one w listy inicjatorów kolejności. Poprzednie wersje kompilatora nie Ostrzegaj, gdy kolejność na liście inicjatora różnił się od kolejność deklaracji. Może to spowodować niezdefiniowane zachowanie, jeśli inicjowania jednego członka była uzależniona od innego elementu członkowskiego na liście, który został już zainicjowany. W poniższym przykładzie, Visual Studio 2017 wersji 15 ustęp 3 (z **/ścian**) zgłasza "ostrzeżenie C5038:"A::y"zostanie zainicjowana po elemencie członkowskim danych"A::x"elementu członkowskiego danych":

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

Aby rozwiązać ten problem, Rozmieść na liście inicjatora, poproś go o takiej samej kolejności jak deklaracji. Ostrzeżenie podobne jest wywoływane, gdy jeden lub oba inicjatory odwoływać się do elementów członkowskich klasy podstawowej.

Warto zauważyć, że ostrzeżenia jest poza domyślnie wpływa tylko na kodu skompilowanego za pomocą **/ścian**.

## <a name="update_155"></a> Poprawki błędów i inne zmiany zachowania w programie Visual Studio 2017 wersji 15,5 cala

### <a name="partial-ordering-change"></a>Częściowe porządkowanie zmiany

Kompilator teraz prawidłowo odrzuca następujący kod i zapewnia odpowiedni komunikat o błędzie:

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(const T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);    // C2668
}
```

```Output
t161.cpp
t161.cpp(16): error C2668: 'f': ambiguous call to overloaded function
t161.cpp(8): note: could be 'int f<int*>(const T &)'
        with
        [
            T=int*
        ]
t161.cpp(2): note: or       'int f<int>(int*)'
t161.cpp(16): note: while trying to match the argument list '(int*)'
```

Problem w powyższym przykładzie zakłada, że różnice dwa typy (const w porównaniu z systemem innym niż stała i dodatkiem Service pack, a-pack). Aby wyeliminować błąd kompilatora, usuń jedną z różnic. Dzięki temu kompilatora jednoznacznie kolejność funkcji.

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);
}
```

### <a name="exception-handlers"></a>Programy obsługi wyjątków

Programy obsługi odwołania do typu tablicy lub funkcja nigdy nie są dopasowania dla dowolnego obiektu wyjątku. Kompilator teraz poprawnie honoruje tej zasady i zgłasza ostrzeżenie poziom 4. Również nie jest już zgodny program obsługi `char*` lub `wchar_t*` z ciągiem literału po wybraniu **/Zc: strictstrings** jest używany.

```cpp
int main()
{
    try {
        throw "";
    }
    catch (int (&)[1]) {} // C4843 (This should always be dead code.)
    catch (void (&)()) {} // C4843 (This should always be dead code.)
    catch (char*) {} // This should not be a match under /Zc:strictStrings
}
```

```Output
warning C4843: 'int (&)[1]': An exception handler of reference to array or function type is unreachable, use 'int*' instead
warning C4843: 'void (__cdecl &)(void)': An exception handler of reference to array or function type is unreachable, use 'void (__cdecl*)(void)' instead
```

Unika się następujący kod błędu:

```cpp
catch (int (*)[1]) {}
```

### <a name="tr1"></a>przestrzeń nazw STD::tr1 jest przestarzała

Niestandardowe `std::tr1` przestrzeni nazw jest teraz oznaczony jako przestarzały w C ++ 17 trybach i C ++ 14. W programie Visual Studio 2017 wersji 15,5 cala poniższy kod wywołuje C4996:

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::tr1::function<int (int, int)> f = std::plus<int>(); //C4996
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

```Output
warning C4996: 'std::tr1': warning STL4002: The non-Standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
```

Aby naprawić błąd, Usuń odwołanie do `tr1` przestrzeni nazw:

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::function<int (int, int)> f = std::plus<int>();
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

### <a name="annex_d"></a>Standardowe funkcje biblioteki w załączniku D są oznaczone jako przestarzałe

Gdy **/std:c ++ 17** ustawiono tryb przełącznika kompilatora, prawie wszystkie funkcje standardowej biblioteki w załączniku D są oznaczone jako przestarzałe.

W programie Visual Studio 2017 wersji 15,5 cala poniższy kod wywołuje C4996:

```cpp
#include <iterator>

class MyIter : public std::iterator<std::random_access_iterator_tag, int> {
public:
    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

```Output
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ Standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
```

Aby naprawić błąd, postępuj zgodnie z instrukcjami tekst ostrzeżenia, jak pokazano w poniższym kodzie:

```cpp
#include <iterator>

class MyIter {
public:
    typedef std::random_access_iterator_tag iterator_category;
    typedef int value_type;
    typedef ptrdiff_t difference_type;
    typedef int* pointer;
    typedef int& reference;

    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

### <a name="unreferenced-local-variables"></a>Nieużywane zmienne lokalne

W programie Visual Studio 15,5 cala ostrzeżenie C4189 jest emitowany przypadków więcej, jak pokazano w poniższym kodzie:

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}
```

```Output
warning C4189: 's': local variable is initialized but not referenced
```

Aby naprawić błąd, Usuń nieużywane zmiennej.

### <a name="single-line-comments"></a>Komentarze w jednym wierszu

W programie Visual Studio 2017 wersji 15,5 cala ostrzeżenia C4001 i C4179 są już emitowane przez kompilator C. Wcześniej tylko zostały wyemitowane w obszarze **/Za** przełącznika kompilatora.  Ostrzeżenia są już potrzebne, ponieważ pojedynczy wiersz komentarze zostały częścią standardowej od C99 C.

```cpp
/* C only */
#pragma warning(disable:4001) //C4619
#pragma warning(disable:4179)
// single line comment
//* single line comment */
```

```Output
warning C4619: #pragma warning: there is no warning number '4001'
```

Jeśli kod nie trzeba zgodne ze starszymi wersjami, usuwając pomijania C4001/C4179 można uniknąć ostrzeżenia. Jeśli kod muszą być zgodne z poprzednimi wersjami, Pomiń C4619 tylko.

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="declspec-attributes-with-extern-c-linkage"></a>atrybuty __declspec powiązania "C" extern

We wcześniejszych wersjach programu Visual Studio, kompilator ignorowane `__declspec(...)` atrybutów, kiedy `__declspec(...)` została zastosowana przed `extern "C"` Specyfikacja powiązania. To zachowanie spowodował kod jest generowany użytkownik przypadkowo o skutki możliwe środowiska wykonawczego. Ostrzeżenie został dodany w programie Visual Studio w wersji 15 ustęp 3, ale było domyślnie wyłączone. W programie Visual Studio 2017 wersji 15,5 cala ostrzeżenie jest domyślnie włączona.

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

Aby naprawić błąd, umieść Specyfikacja powiązania przed atrybutem __declspec:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Jest to nowe ostrzeżenie C4768 znajdująca się na niektórych nagłówków zestaw Windows SDK, które zostały dostarczone z 15 ustęp 3 programu Visual Studio 2017 lub starsze (na przykład: wersja 10.0.15063.0, znanej także jako RS2 SDK). Jednak nowsze wersje zestawu Windows SDK nagłówków (w szczególności ShlObj.h i ShlObj_core.h) zostały ustalone tak, aby nie produkuj to ostrzeżenie. Gdy pojawi się to ostrzeżenie pochodzące z zestawu Windows SDK nagłówków, można wykonać następujące akcje:

1. Przełącz na najnowszy zestaw Windows SDK, dołączony do programu Visual Studio 2017 wersji 15,5 cala wydania.
2. Wyłącz ostrzeżenia wokół #include instrukcji nagłówka zestawu Windows SDK:

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern_linkage"></a>Zewnętrzne połączenie constexpr

We wcześniejszych wersjach programu Visual Studio, zawsze nadać kompilator `constexpr` zmiennej zewnętrzne nawet wtedy, gdy zmienna została oznaczona jako `extern`. W Visual Studio 2017 wersji 15,5 cala, nowy przełącznik (**/Zc:externConstexpr**) umożliwia poprawne zachowanie zgodnych standardów. Po pewnym czasie będzie to wartość domyślna.

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

Jeśli plik nagłówka zawiera Zmienna zadeklarowana `extern constexpr`, musi być oznaczony `__declspec(selectany)` Aby poprawnie zawierać jego deklaracji zduplikowanych połączone:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>Nie można użyć TypeID niekompletny typ klasy

We wcześniejszych wersjach programu Visual Studio kompilator może nieprawidłowo następujący kod, co powoduje potencjalnie nieprawidłowe informacje o typie. W programie Visual Studio 2017 wersji 15,5 cala kompilator niepoprawnie zgłasza błąd:

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdisconvertible-target-type"></a>Typ docelowy STD::is_convertible

`std::is_convertible` wymaga na nieprawidłowy typ zwracany typ docelowy. We wcześniejszych wersjach programu Visual Studio kompilator może nieprawidłowo typach abstrakcyjnych, które mogą spowodować niepoprawne wiązaniem i niezamierzone zachowanie.  Poniższy kod teraz poprawnie wywołuje C2338:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5
```

Aby uniknąć tego błędu, używając `is_convertible` należy porównać typów wskaźnika, ponieważ w porównaniu z systemem innym niż typ wskaźnika może zakończyć się niepowodzeniem, jeśli jeden typ jest abstrakcyjny:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");
```

### <a name="noexcept_removal"></a> Usunięcie specyfikacji wyjątków dynamicznych i noexcept

W języku C ++ 17 `throw()` jest aliasem `noexcept`, `throw(<type list>)` i `throw(...)` są usuwane i mogą obejmować niektórych typów `noexcept`. Może to spowodować problemy ze zgodnością źródła z kodem, który odpowiada C ++ 14 lub wcześniej. **/Zc:noexceptTypes-** przełącznika może służyć do przywrócenia C ++ 14 wersja `noexcept` podczas w trybie C ++ 17 ogólnie. Dzięki temu można zaktualizować kodu źródłowego z języków C ++ 17, bez konieczności ponownego zapisania wszystkie Twoje `throw()` kodu w tym samym czasie.

Kompilator teraz również diagnozuje więcej specyfikacje wyjątków niedopasowanych w deklaracjach trybu C ++ 17 lub za pomocą **/ ograniczająca-** nowe ostrzeżenie C5043.

Poniższy kod generuje C5043 i C5040 w Visual Studio 2017 wersji 15,5 cala podczas **/std:c ++ 17** zastosowano przełącznika:

```cpp
void f() throw(); // equivalent to void f() noexcept;
void f() {} // warning C5043
void g() throw(); // warning C5040

struct A {
    virtual void f() throw();
};

struct B : A {
    virtual void f() { } // error C2694
};
```

Aby usunąć błędy podczas korzystania z nadal **/std:c ++ 17**, albo Dodaj **/Zc:noexceptTypes-** przełącznik w wierszu polecenia, w przeciwnym razie zaktualizuj kod, aby używał `noexcept`, jak pokazano w poniższym przykładzie:

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A {
    virtual void f() noexcept;
};

struct B : A {
    virtual void f() noexcept { }
};
```

### <a name="inline-variables"></a>Wbudowane zmienne

Elementy członkowskie danych statycznych constexpr niejawnie są obecnie wbudowane, co oznacza jego deklarację w obrębie klasy jest teraz ich definicji. Przy użyciu definicji wiersza dla elementu członkowskiego danych statycznych constexpr jest nadmiarowy i teraz przestarzałe. W programie Visual Studio 2017 wersji 15,5 cala podczas **/std:c ++ 17** przełącznika zostaną zastosowane, poniższy kod tworzy teraz ostrzeżenie C5041 *"rozmiar": definicja wiersza dla elementu członkowskiego danych statycznych constexpr nie jest wymagana i jest przestarzały w języku C ++ 17*:

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-declspec-warning-c4768-now-on-by-default"></a>Ostrzeżenie C4768 teraz na domyślnie __declspec(...) "C" extern

Ostrzeżenie został dodany w programie Visual Studio 2017 wersji 15 ustęp 3, ale było domyślnie wyłączone. W programie Visual Studio 2017 wersji 15,5 cala jest on domyślnie. Zobacz [nowe ostrzeżenie o atrybutach declspec](#declspec) Aby uzyskać więcej informacji.

### <a name="defaulted-functions-and-declspecnothrow"></a>Funkcje domyślne i deklaracje __declspec(nothrow)

Kompilator dozwolone wcześniej funkcje domyślne za pomocą `__declspec(nothrow)` po odpowiednie funkcje podstawowych/elementów członkowskich dozwolone wyjątków. To zachowanie jest to sprzeczne C++ Standard i może spowodować niezdefiniowane zachowanie w czasie wykonywania. Standard wymaga tych funkcji jest zdefiniowany jako usunięty, jeśli występuje niezgodność specyfikacji wyjątku.  W obszarze **/std:c ++ 17**, poniższy kod wywołuje C2280 *próby odwołania usunięta funkcja. Funkcja niejawnie została usunięta, ponieważ specyfikacji jawnych wyjątku jest niezgodna ze specyfikacją niejawne deklaracji.* :

```cpp
struct A {
    A& operator=(const A& other) { // No exception specification; this function may throw.
        ...
    }
};

struct B : public A {
    __declspec(nothrow) B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1; // error C2280
}
```

Aby rozwiązać ten kod, Usuń __declspec(nothrow) z domyślnym funkcji, lub usuń `= default` i zdefiniowanie funkcji oraz wszelkie wymagane wyjątków:

```cpp
struct A {
    A& operator=(const A& other) {
        // ...
    }
};

struct B : public A {
    B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1;
}
```

### <a name="noexcept-and-partial-specializations"></a>noexcept i częściowej specjalizacji

Z noexcept w systemie typów częściowe specjalizacje dopasowania "można wywołać" przyszłe może się nie powieść skompilować lub wybierz szablon podstawowy z powodu brakujących z częściowa specjalizacja dla wskaźników do noexcept funkcji.

W takich przypadkach może być konieczne dodanie dodatkowych częściowe specjalizacje obsługi wskaźników funkcji noexcept i noexcept wskaźniki do funkcji Członkowskich. Te przeciążenia tylko są niedozwolone w **/std:c ++ 17** tryb. Jeśli zgodności z poprzednimi wersjami z C ++ 14 muszą zostać zachowane i są pisanie kodu, który korzystać z innych użytkowników, a następnie należy zabezpieczyć te nowe przeciążenia wewnątrz `#ifdef` dyrektywy. Podczas pracy w module niezależne, a następnie zamiast `#ifdef` osłony mogą być tylko kompilacji z **/Zc:noexceptTypes-** przełącznika.

Kompiluje następujący kod pod **/std:c ++ 14** , ale nie powiedzie się w obszarze **/std:c ++ 17** z "błąd C2027:use niezdefiniowanego typu" A\<T > "":

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // C2027
}
```

Poniższy kod zakończy się powodzeniem, w obszarze **/std:c ++ 17** ponieważ nowej częściowej specjalizacji wybierze kompilator `A<void (*)() noexcept>`:

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <>
struct A<void(*)() noexcept>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // OK
}
```

## <a name="update_157"></a> Poprawki błędów i inne zmiany zachowania w Visual Studio 2017 wersji 15.7

### <a name="c17-default-argument-in-the-primary-class-template"></a>C ++ 17 domyślny argument szablonu klasy podstawowej

Warunkiem wstępnym jest to zmiana zachowania [Wnioskowanie argumentu szablonu dla szablonów klas - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html), który jest planowane, aby w pełni obsługiwane w nowszej wersji zapoznawczej programu Visual Studio 2017 wersji 15.7.

Wcześniej kompilator ignorowane domyślnego argumentu szablonu klasy podstawowej.

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

W **/std:c ++ 17** trybu w Visual Studio 2017 wersji 15.7, argument domyślny nie jest ignorowana:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>Rozpoznawanie nazw zależne

Warunkiem wstępnym jest to zmiana zachowania [Wnioskowanie argumentu szablonu dla szablonów klas - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html), który jest planowane, aby w pełni obsługiwane w nowszej wersji zapoznawczej programu Visual Studio 2017 wersji 15.7.

W poniższym przykładzie jest rozpoznawany jako kompilatora w Visual Studio 15,6 i starszych wersji `D::type` do `B<T>::type` w szablonie klasy podstawowej.

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = B<T*>::type;
};
```

Visual Studio 2017 wersji 15.7, w **/std:c ++ 17** tryb, wymaga `typename` — słowo kluczowe w `using` instrukcji w D. Bez `typename` kompilator zgłasza ostrzeżenie C4346: *' B < T\*>:: typu ": zależna nazwa nie jest typem* i błąd C2061: *błąd składniowy: identyfikator"type"*:

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = typename B<T*>::type;
};
```

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C ++ 17 [[nodiscard]] atrybutu - ostrzeżenie zwiększenia poziomu

W wersji Visual Studio 2017 15.7 w **/std:c ++ 17** trybie poziom ostrzeżeń C4834 ("odrzucanie wartości zwracanej przez funkcję z atrybutem"nodiscard"") jest zwiększona z W3 do W1. Możesz wyłączyć ostrzeżenia o Rzutowanie na `void`, lub przez przekazanie **/wd:4834** w kompilatorze

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Listy inicjowania ze zmienną liczbą argumentów szablonu konstruktora klasy podstawowej

W poprzednich wersjach programu Visual Studio ze zmienną liczbą argumentów szablonu konstruktora klasy podstawowej inicjowania listę, która nie ma argumentów szablonu jest dozwolone przez pomyłkę bez błędów. W programie Visual Studio 2017 wersji 15.7 wystąpi błąd kompilatora jest wywoływane.

Poniższy przykład kodu w zgłasza 15.7 wersji programu Visual Studio 2017 *błąd C2614: D\<int >: niedozwolona Inicjalizacja elementu członkowskiego: "B" nie jest podstawowym lub elementu członkowskiego*

```cpp
template<typename T>
struct B {};

template<typename T>
struct D : B<T>
{

    template<typename ...C>
    D() : B() {} // C2614. Missing template arguments to B.
};

D<int> d;
```

Aby naprawić błąd, należy zmienić wyrażenie B() b\<T > ().

## <a name="see-also"></a>Zobacz także

[Zgodność języka Visual C++](visual-cpp-language-conformance.md)
