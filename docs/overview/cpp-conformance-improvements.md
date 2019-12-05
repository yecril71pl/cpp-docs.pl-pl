---
title: C++ulepszenia zgodności
ms.date: 12/04/2019
description: Firma C++ Microsoft w programie Visual Studio postępuje w kierunku pełnej zgodności ze standardem języka c++ 20.
ms.technology: cpp-language
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 06fa060b674e51a3352a9a928bccdbfa6c63aae4
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858038"
---
# <a name="c-conformance-improvements-in-visual-studio"></a>Ulepszenia zgodności języka C++ w programie Visual Studio

Firma C++ Microsoft dokonuje ulepszeń zgodności i poprawek błędów w każdej wersji. W tym artykule przedstawiono ulepszenia w wersji głównej, a następnie według wersji. Zawiera również listę najważniejszych poprawek błędów według wersji. Aby przejść bezpośrednio do zmian w określonej wersji, użyj na liście **w tym artykule** .

::: moniker range="vs-2019"

## <a name="improvements_160"></a>Udoskonalenia zgodności w programie Visual Studio 2019 RTW (wersja 16,0)

Program Visual Studio 2019 RTW zawiera następujące ulepszenia zgodności, poprawki błędów i zmiany zachowań w kompilatorze Microsoft C++ (MSVC)

**Uwaga:** Funkcje języka c++ 20 zostaną udostępnione w trybie `/std:c++latest` do momentu ukończenia implementacji języka C++ 20 dla kompilatora i IntelliSense. W tym czasie zostanie wprowadzony tryb kompilatora `/std:c++20`.

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Ulepszono obsługę modułów dla szablonów i wykrywania błędów

Moduły są teraz oficjalnie w standardzie C++ 20. Ulepszona obsługa została dodana w programie Visual Studio 2017 w wersji 15,9. Aby uzyskać więcej informacji, zobacz [lepsza obsługa szablonów i wykrywanie błędów C++ w modułach z MSVC 2017 w wersji 15,9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/).

### <a name="modified-specification-of-aggregate-type"></a>Zmodyfikowano specyfikację typu agregacji

Specyfikacja typu agregacji została zmieniona w języku C++ 20 (zobacz [Zabroń agregowania w konstruktorach zadeklarowanych przez użytkownika](https://wg21.link/p1008r1)). W programie Visual Studio 2019, w obszarze `/std:c++latest`, Klasa z dowolnym konstruktorem zadeklarowanym przez użytkownika (na przykład, w tym konstruktorem zadeklarowanym `= default` lub `= delete`) nie jest agregacją. Wcześniej tylko konstruktory dostarczone przez użytkownika nie kwalifikują klasy jako agregacji. Ta zmiana powoduje dodatkowe ograniczenia dotyczące sposobu inicjowania takich typów.

Poniższy kod kompiluje się bez błędów w programie Visual Studio 2017, ale zgłasza błędy C2280 i C2440 w programie Visual Studio 2019 w `/std:c++latest`:

```cpp
struct A
{
    A() = delete; // user-declared ctor
};

struct B
{
    B() = default; // user-declared ctor
    int i = 0;
};

A a{}; // ill-formed in C++20, previously well-formed
B b = { 1 }; // ill-formed in C++20, previously well-formed
```

### <a name="partial-support-for-operator-"></a>Częściowa obsługa `operator <=>`

[P0515R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0515r3.pdf) W języku c++ 20 wprowadzono `<=>` operatora porównania, znanego również jako "operator Spaceship". Program Visual Studio 2019 w trybie `/std:c++latest` wprowadza częściową obsługę operatora przez podnoszenie błędów dla składni, która jest obecnie niedozwolona. Na przykład poniższy kod kompiluje się bez błędów w programie Visual Studio 2017, ale wywołuje wiele błędów w programie Visual Studio 2019 w `/std:c++latest`:

```cpp
struct S
{
    bool operator<=(const S&) const { return true; }
};

template <bool (S::*)(const S&) const>
struct U { };

int main(int argc, char** argv)
{
    U<&S::operator<=> u; // In Visual Studio 2019 raises C2039, 2065, 2146.
}
```

Aby uniknąć błędów, Wstaw spację w wierszu powodującym problemy przed końcowym nawiasem ostrym: `U<&S::operator<= > u;`.

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>Odwołania do typów z niezgodnymi kwalifikatorami CV

Wcześniej MSVC dozwolone bezpośrednie powiązanie odwołania z typu z niezgodnymi kwalifikatorami CV poniżej najwyższego poziomu. To powiązanie może umożliwić modyfikację danych supposedly const, do których odwołuje się odwołanie. Kompilator tworzy teraz tymczasowy, zgodnie z wymaganiami Standard. W programie Visual Studio 2017 następujący kod kompiluje się bez ostrzeżeń. W programie Visual Studio 2019 kompilator zgłasza *Ostrzeżenie C4172: \<Func: #1 "?PData@X@@QBEABQBXXZ"> zwracanie adresu zmiennej lokalnej lub tymczasowej*.

```cpp
struct X
{
    const void* const& PData() const
    {
        return _pv;
    }

    void* _pv;
};

int main()
{
    X x;
    auto p = x.PData(); // C4172
}
```

### <a name="reinterpret_cast-from-an-overloaded-function"></a>`reinterpret_cast` ze przeciążonej funkcji

Argument `reinterpret_cast` nie jest jednym z kontekstów, w których dozwolony jest adres przeciążonej funkcji. Poniższy kod kompiluje się bez błędów w programie Visual Studio 2017, ale w Visual Studio 2019 wywołuje *C2440: nie można skonwertować z "przeciążonej funkcji" na "FP"* :

```cpp
int f(int) { return 1; }
int f(float) { return .1f; }
using fp = int(*)(int);

int main()
{
    fp r = reinterpret_cast<fp>(&f);
}
```

Aby uniknąć tego błędu, użyj dozwolonego rzutowania w tym scenariuszu:

```cpp
int f(int);
int f(float);
using fp = int(*)(int);

int main()
{
    fp r = static_cast<fp>(&f); // or just &f;
}
```

### <a name="lambda-closures"></a>Zamknięcia lambda

W języku C++ 14 typy zamknięć lambda nie są literałami. Podstawową konsekwencją tej reguły jest to, że wyrażenie lambda nie może być przypisane do zmiennej **constexpr** . Poniższy kod kompiluje się bez błędów w programie Visual Studio 2017, ale w programie Visual Studio 2019 wywołuje *C2127: ' l ': niedozwolone inicjowanie jednostki "constexpr" przy użyciu wyrażenia niestałego*:

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

Aby uniknąć tego błędu, Usuń kwalifikator **constexpr** lub zmień tryb zgodności na `/std:c++17`.

### <a name="stdcreate_directory-failure-codes"></a>Kody błędów `std::create_directory`

Implementacja [P1164](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1164r1.pdf) z c++ 20 bezwarunkowo. Ta zmiana `std::create_directory`, aby sprawdzić, czy element docelowy był już katalogiem w przypadku niepowodzenia. Poprzednio wszystkie błędy typu ERROR_ALREADY_EXISTS były przełączane do kodów, które nie zostały utworzone.

### `operator<<(std::ostream, nullptr_t)`

Na [LWG 2221](https://cplusplus.github.io/LWG/issue2221)dodano `operator<<(std::ostream, nullptr_t)` do zapisywania nullptrs do strumieni.

### <a name="additional-parallel-algorithms"></a>Dodatkowe algorytmy równoległe

Nowe równoległe wersje `is_sorted`, `is_sorted_until`, `is_partitioned`, `set_difference`, `set_intersection`, `is_heap`i `is_heap_until`.

### <a name="atomic-initialization"></a>Inicjalizacja niepodzielna

[P0883 "Usuwanie niepodzielnych inicjacji"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0883r1.pdf) zmienia `std::atomic` na wartość — zainicjuj zawartą w niej element t zamiast default-Initialized. Poprawka jest włączona w przypadku używania Clang/LLVM z biblioteką standard firmy Microsoft. Jest on obecnie wyłączony dla kompilatora Microsoft C++ , ponieważ obejście błędu w przetwarzaniu **constexpr** .

### <a name="remove_cvref-and-remove_cvref_t"></a>`remove_cvref` i `remove_cvref_t`

Zaimplementowano cechy typu `remove_cvref` i `remove_cvref_t` z [P0550](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf). Te Remove Reference-stałość i CV-kwalifikacje z typu bez obsłużenia funkcji i tablic do wskaźników (w przeciwieństwie do `std::decay` i `std::decay_t`).

### <a name="feature-test-macros"></a>Testowanie funkcji — makra

[Makra P0941R2-Feature-test](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html) są kompletne i obsługują `__has_cpp_attribute`. Makra funkcji-test są obsługiwane we wszystkich trybach standardowych.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Zabroń agregowania dla konstruktorów zadeklarowanych przez użytkownika

[C++ 20 P1008R1 — Zabroń agregacji z konstruktorami zadeklarowanymi przez użytkownika](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf) .

## <a name="improvements_161"></a>Ulepszenia zgodności w 16,1

### <a name="char8_t"></a>char8_t

[P0482r6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html). C++ 20 dodaje nowy typ znaku, który jest używany do reprezentowania jednostek kodu UTF-8. Literały ciągu `u8` w języku C++ 20 mają typ `const char8_t[N]` zamiast `const char[N]`, który był wcześniej w przypadku. Podobne zmiany zostały zaproponowane dla standardu C w [N2231](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2231.htm). Sugestie dotyczące `char8_t` korygowania zgodności z poprzednimi wersjami są podano w [P1423r0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1423r0.html). Kompilator firmy C++ Microsoft dodaje obsługę `char8_t` w programie Visual Studio 2019 w wersji 16,1 w przypadku określenia opcji kompilatora **/Zc: char8_t** . W przyszłości będzie obsługiwana z [/std: c + + Najnowsza](../build/reference/std-specify-language-standard-version.md), które można przywrócić do zachowania języka c++ 17 za pośrednictwem **/Zc: char8_t-** . Kompilator EDG, który nie obsługuje jeszcze technologii IntelliSense, więc zobaczysz, że fałszywe błędy tylko IntelliSense, które nie mają wpływu na rzeczywistą kompilację.

#### <a name="example"></a>Przykład

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtype_identity-metafunction-and-stdidentity-function-object"></a>std:: type_identitybinding i obiekt funkcji std:: Identity

[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf). Przestarzałe rozszerzenie szablonu klasy `std::identity` zostało usunięte i zastąpione obiektem funkcji SqlFunctions języka C++ 20 `std::type_identity` i `std::identity`. Oba są dostępne tylko w [/std: c + + Najnowsza](../build/reference/std-specify-language-standard-version.md).

Poniższy przykład generuje C4996 z ostrzeżeniem o zaniechaniu dla `std::identity` (zdefiniowane w \<type_traits >) w programie Visual Studio 2017:

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

Poniższy przykład pokazuje, jak używać nowego `std::identity` (zdefiniowanego w \<funkcjonalne >) wraz z nowym `std::type_identity`:

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>Sprawdzanie składni dla rodzajowych wyrażeń lambda

Nowy procesor lambda umożliwia pewną składnię w trybie zgodności, która sprawdza w ogólnym wyrażeniu lambda, w obszarze [/std: c + + Najnowsza](../build/reference/std-specify-language-standard-version.md) lub w dowolnym innym trybie języka z **/Experimental: newLambdaProcessor**.

W programie Visual Studio 2017 ten kod kompiluje się bez ostrzeżeń, ale w programie Visual Studio 2019 generuje błąd *składniowy błędu C2760: Nieoczekiwany token "\<identyfikator-expr >", oczekiwano "ID-Expression"* :

```cpp
void f() {
    auto a = [](auto arg) {
        decltype(arg)::Type t;
    };
}
```

Poniższy przykład pokazuje poprawną składnię, która jest teraz wymuszana przez kompilator:

```cpp
void f() {
    auto a = [](auto arg) {
        typename decltype(arg)::Type t;
    };
}
```

### <a name="argument-dependent-lookup-for-function-calls"></a>Wyszukiwanie wywołań funkcji zależnych od argumentów

[P0846R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0846r0.html) (c++ 20) zwiększona możliwość znajdowania szablonów funkcji przez wyszukiwanie zależne od argumentów dla wyrażeń wywołania funkcji z jawnymi argumentami szablonu. Wymaga **/std: c + + Najnowsza**.

### <a name="designated-initialization"></a>Wyznaczono inicjalizację

[P0329R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf) (c++ 20) wyznaczoną inicjalizację umożliwia wybranie określonych elementów członkowskich w ramach inicjalizacji agregacji przy użyciu składni `Type t { .member = expr }`. Wymaga **/std: c + + Najnowsza**.

### <a name="new-and-updated-standard-library-functions-c20"></a>Nowe i zaktualizowane funkcje biblioteki standardowej (C++ 20)

- `starts_with()` i `ends_with()` `basic_string` i `basic_string_view`.
- `contains()` dla kontenerów asocjacyjnych.
- `remove()`, `remove_if()` i `unique()` dla obiektów `list` i `forward_list` zwracają teraz obiekt `size_type`.
- `shift_left()` i `shift_right()` dodane do > algorytmu \<.


## <a name="improvements_162"></a>Ulepszenia zgodności w 16,2

### <a name="noexcept-constexpr-functions"></a>noexcept funkcje constexpr

Funkcje constexpr nie są już traktowane jako **noexcept** , jeśli są używane w wyrażeniu stałym. Ta zmiana zachowania pochodzi z rozwiązania [CWG 1351](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html#1351) i jest włączona w [/permissive-](../build/reference/permissive-standards-conformance.md). Poniższy przykład kompiluje w programie Visual Studio 2019 w wersji 16,1 i starszej, ale tworzy C2338 w programie Visual Studio 2019 w wersji 16,2:

```cpp
constexpr int f() { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept"); // C2338 in 16.2
}
```

Aby naprawić ten błąd, Dodaj wyrażenie **noexcept** do deklaracji funkcji:

```cpp
constexpr int f() noexcept { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept");
}
```

### <a name="binary-expressions-with-different-enum-types"></a>Wyrażenia binarne z różnymi typami wyliczeniowymi

Możliwość zastosowania zwykłych konwersji arytmetycznych na operandach, gdzie jeden jest typu wyliczenia, a drugi jest innym typem wyliczenia lub typ zmiennoprzecinkowy jest przestarzały w języku C++ 20 ([P1120R0](https://wg21.link/p1120r0)). W programie Visual Studio 2019 w wersji 16,2 lub nowszej Poniższy kod generuje ostrzeżenie poziomu 4, gdy opcja kompilatora [/std: c + +](../build/reference/std-specify-language-standard-version.md) jest włączona:

```cpp
enum E1 { a };
enum E2 { b };
int main() {
    int i = a | b; // warning C5054: operator '|': deprecated between enumerations of different types
}
```

Aby uniknąć tego ostrzeżenia, należy użyć [static_cast](../cpp/static-cast-operator.md) do przekonwertowania drugiego operandu:

```cpp
enum E1 { a };
enum E2 { b };
int main() {
  int i = a | static_cast<int>(b);
}
```

### <a name="binary-expressions-with-enumeration-and-floating-point-types"></a>Wyrażenia binarne z wyliczeniem i typami zmiennoprzecinkowymi

Możliwość zastosowania zwykłych konwersji arytmetycznych na operandach, gdzie jeden jest typu wyliczenia, a drugi jest innym typem wyliczenia lub typ zmiennoprzecinkowy jest przestarzały w języku C++ 20 ([P1120R0](https://wg21.link/p1120r0)). Innymi słowy, przy użyciu operacji binarnej między wyliczeniem a typem zmiennoprzecinkowym jest teraz ostrzeżenie, gdy opcja kompilatora [/std: c + +](../build/reference/std-specify-language-standard-version.md) jest włączona:

```cpp
enum E1 { a };
int main() {
  double i = a * 1.1;
}
```

Aby uniknąć tego ostrzeżenia, należy użyć [static_cast](../cpp/static-cast-operator.md) do przekonwertowania drugiego operandu:

```cpp
enum E1 { a };
int main() {
   double i = static_cast<int>(a) * 1.1;
}
```

### <a name="equality-and-relational-comparisons-of-arrays"></a>Porównanie równości i relacyjnych tablic

Porównania równości i relacyjnych między dwoma operandami typu Array są przestarzałe w języku C++ 20 ([P1120R0](https://wg21.link/p1120r0)). Innymi słowy, operacja porównania między dwiema tablicami (niezależnie od rangi i zakresu podobieństw) jest teraz ostrzeżeniem. Począwszy od programu Visual Studio 2019 w wersji 16,2, poniższy kod generuje *C5056: operator "= =": przestarzały dla typów tablicowych* , gdy jest włączona opcja kompilatora [/std: c + +](../build/reference/std-specify-language-standard-version.md) :

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (a == b) { return 1; }
}
```

Aby uniknąć ostrzeżenia, można porównać adresy pierwszego elementu:

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (&a[0] == &b[0]) { return 1; }
}
```

Aby określić, czy zawartość dwóch tablic jest równa, użyj funkcji [std:: EQUAL](../standard-library/algorithm-functions.md#equal) :

```cpp
std::equal(std::begin(a), std::end(a), std::begin(b), std::end(b));
```

### <a name="effect-of-defining-spaceship-operator-on--and-"></a>Efekt definiowania operatora Spaceship na = = i! =

Definicja spaceshipego operatora ( **<=>** ) nie będzie już ponownie pisać wyrażeń obejmujących **==** lub **! =** , chyba że operator Spaceship jest oznaczony jako `= default` ([P1185R2](https://wg21.link/p1185r2)). Poniższy przykład kompiluje się w programie Visual Studio 2019 RTW i w wersji 16,1, ale produkuje C2678 w programie Visual Studio 2019 w wersji 16,2:

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

Aby uniknąć tego błędu, zdefiniuj operator = = lub Zadeklaruj go jako domyślny:

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
  bool operator==(const S&) const = default;
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

### <a name="standard-library-improvements"></a>Ulepszenia biblioteki standardowej

- \<charconv > `to_chars()` z dokładnością stałą/naukową. (Ogólna precyzja jest obecnie planowana dla 16,4).
- [P0020R6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0020r6.html): niepodzielna\<zmiennoprzecinkowa >, niepodzielna\<podwójna >, niepodzielna\<długa podwójna >
- [P0463R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html): endian
- [P0482R6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html): obsługa biblioteki dla char8_t
- [P0600R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r1.pdf): [\[nodiscard]] dla STL, część 1
- [P0653R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html): to_address ()
- [P0754R2](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0754r2.pdf): > wersja \<
- [P0771R1](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0771r1.pdf): noexcept for std:: Function — Konstruktor

## <a name="improvements_163"></a>Ulepszenia zgodności w programie Visual Studio 2019 w wersji 16,3

### <a name="stream-extraction-operators-for-char-removed"></a>Operatory wyodrębniania strumienia dla char * usunięte

Operatory wyodrębniania strumienia dla wskaźników do znaków zostały usunięte i zastąpione przez operatory wyodrębniania tablic-znaków (na [P0487R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0487r1.html)). WG21 traktuje usunięte przeciążenia jako niebezpieczne. W [/std: c + + najnowszy](../build/reference/std-specify-language-standard-version.md) tryb, Poniższy przykład generuje *C2679: binary "> >": nie odnaleziono operatora, który pobiera operand z prawej strony typu "char\*" (lub nie istnieje akceptowalna konwersja)* :

```cpp
   char x[42];
   char* p = x;
   std::cin >> std::setw(42);
   std::cin >> p;
```

Aby uniknąć tego błędu, należy użyć operatora wyodrębniania z zmienną Char []:

```cpp
char x[42];
std::cin >> x;
```

### <a name="new-keywords-requires-and-concept"></a>Nowe słowa kluczowe **wymagają** i **koncepcji**

Nowe słowa kluczowe **wymagają** dodania **koncepcji** do kompilatora firmy Microsoft C++ . Jeśli spróbujesz użyć jednego jako identyfikatora w [/std: c + + najnowszy](../build/reference/std-specify-language-standard-version.md) tryb, kompilator zgłosi *C2059: błąd składni*.

### <a name="constructors-as-type-names-disallowed"></a>Konstruktory jako nazwy typów są niedozwolone

Nazwy konstruktorów nie są już traktowane jako iniekcje nazw klas, gdy pojawiają się w kwalifikowanej nazwie po aliasie dla specjalizacji szablonu klasy. To wcześniej pozwoliło użyć konstruktorów jako nazwy typu w celu zadeklarować innych jednostek. Poniższy przykład generuje teraz *C3646: "TotalDuration": nieznany specyfikator przesłonięcia*:

```cpp
#include <chrono>

class Foo {
   std::chrono::milliseconds::duration TotalDuration{};
};

```

Aby uniknąć tego błędu, zadeklaruj `TotalDuration` jak pokazano poniżej:

```cpp
#include <chrono>

class Foo {
  std::chrono::milliseconds TotalDuration {};
};
```

### <a name="stricter-checking-of-extern-c-functions"></a>Dokładniejsze sprawdzanie zewnętrznych funkcji "C"

Jeśli funkcja **extern "C"** została zadeklarowana w różnych obszarach nazw, poprzednie wersje kompilatora firmy C++ Microsoft nie sprawdzają, czy deklaracje były zgodne. W programie Visual Studio 2019 w wersji 16,3 kompilator wykonuje takie sprawdzenie. W trybie [/permissive-](../build/reference/permissive-standards-conformance.md) Poniższy kod generuje *C2371: redefinition; różne typy podstawowe* i *C2733 nie można przeciążyć funkcji z powiązaniem C*:

```cpp
using BOOL = int;

namespace N
{
   extern "C" void f(int, int, int, bool);
}

void g()
{
   N::f(0, 1, 2, false);
}

extern "C" void f(int, int, int, BOOL){}
```

Aby uniknąć błędów w poprzednim przykładzie, użyj **bool** zamiast **bool** spójnie w obu deklaracjach `f`.

### <a name="standard-library-improvements"></a>Ulepszenia biblioteki standardowej

Nagłówki niestandardowe \<stdexcpt. h > i \<. h > zostały usunięte. Kod, który zawiera te elementy, powinien zamiast tego zawierać nagłówki standardowe \<> wyjątków i > \<.

## <a name="improvements_164"></a>Ulepszenia zgodności w programie Visual Studio 2019 w wersji 16,4

### <a name="better-enforcement-of-two-phase-name-lookup-for-qualified-ids-in-permissive-"></a>Lepsze wymuszanie dwufazowego wyszukiwania nazw dla kwalifikujących się identyfikatorów w/permissive-

Dwufazowe wyszukiwanie nazw wymaga, aby nazwy niezależne używane w treści szablonu musiały być widoczne dla szablonu w czasie definicji. Wcześniej takie nazwy mogły zostać znalezione podczas tworzenia wystąpienia szablonu. Ta zmiana ułatwia pisanie przenośnego, zgodnego kodu w MSVC pod flagą [/permissive-](../build/reference/permissive-standards-conformance.md) .

W programie Visual Studio 2019 w wersji 16,4 z ustawioną flagą **/permissive-** Poniższy przykład generuje błąd, ponieważ `N::f` nie jest widoczny podczas definiowania szablonu `f<T>`:

```cpp
template <class T>
int f() {
    return N::f() + T{}; // error C2039: 'f': is not a member of 'N'
}

namespace N {
    int f() { return 42; }
}
```

Zazwyczaj można to naprawić, dołączając brakujące nagłówki lub funkcje lub zmienne deklarujące przekazywanie dalej, jak pokazano w następującym przykładzie:

```cpp
namespace N {
    int f();
}

template <class T>
int f() {
    return N::f() + T{};
}

namespace N {
    int f() { return 42; }
}
```

### <a name="implicit-conversion-of-integral-constant-expressions-to-null-pointer"></a>Niejawna konwersja wyrażeń stałych całkowitej na wskaźnik o wartości null

Kompilator MSVC implementuje teraz [CWG problem 903](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html#903) w trybie zgodności (/permissive-). Ta reguła nie zezwala na niejawną konwersję wyrażeń stałych całkowitych (z wyjątkiem literału liczby całkowitej "0") na stałe wskaźnika o wartości null. Poniższy przykład generuje C2440 w trybie zgodności:

```cpp
int* f(bool* p) {
    p = false; // error C2440: '=': cannot convert from 'bool' to 'bool *'
    p = 0; // OK
    return false; // error C2440: 'return': cannot convert from 'bool' to 'int *'
}
```

Aby naprawić ten błąd, użyj **nullptr** zamiast **false**. Należy zauważyć, że literał 0 jest nadal dozwolony:

```cpp
int* f(bool* p) {
    p = nullptr; // OK
    p = 0; // OK
    return nullptr; // OK
}
```

### <a name="standard-rules-for-types-of-integer-literals"></a>Standardowe reguły dla typów literałów liczb całkowitych

W trybie zgodności (włączony przez [/permissive-](../build/reference/permissive-standards-conformance.md)) MSVC używa standardowych reguł dla typów literałów liczb całkowitych. Wcześniej literały dziesiętne zbyt duże, aby mieściły się w podpisanym znaku "int", były typem "unsigned int". Teraz takie literały mają największy typ z liczbą całkowitą ze znakiem "long long". Ponadto literały z sufiksem "for", które są zbyt duże, aby mieściły się w podpisanym typie, mają typ "unsigned long long".

Może to prowadzić do wygenerowania różnych diagnostyki ostrzeżeń i różnic zachowania operacji arytmetycznych wykonywanych na literałach.

W poniższym przykładzie przedstawiono nowe zachowanie programu Visual Studio 2019, wersja 16,4. Zmienna `i` jest typu **unsigned int** i w związku z tym ostrzeżenie jest zgłaszane. Bity o dużej kolejności dla zmiennej `j` są ustawione na 0.

```cpp
void f(int r) {
    int i = 2964557531; // warning C4309: truncation of constant value
    long long j = 0x8000000000000000ll >> r; // literal is now unsigned, shift will fill high-order bits with 0
}
```

W poniższym przykładzie pokazano, jak zachować stare zachowanie i w ten sposób uniknąć ostrzeżeń i zmian w czasie wykonywania:

```cpp
void f(int r) {
int i = 2964557531u; // OK
long long j = (long long)0x8000000000000000ll >> r; // shift will keep high-order bits
}
```

### <a name="function-parameters-that-shadow-template-parameters"></a>Parametry funkcji, które są parametrami szablonu w tle

Kompilator MSVC teraz zgłasza błąd, gdy parametr funkcji zasłania parametr szablonu:

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T(&buffer)[Size], int& Size) // error C7576: declaration of 'Size' shadows a template parameter
{
    return f(buffer, Size, Size);
}
```

Aby naprawić ten błąd, Zmień nazwę jednego z parametrów:

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T (&buffer)[Size], int& size_read)
{
    return f(buffer, Size, size_read);
}
```

### <a name="user-provided-specializations-of-type-traits"></a>Specjalizacje podane przez użytkownika dla cech typu

Zgodnie z podklauzulą *meta. rqmts* w warstwie Standardowa kompilator MSVC wywołuje teraz błąd w przypadku napotkania specjalizacji zdefiniowanej przez użytkownika jednego z określonych szablonów type_traits w przestrzeni nazw `std`. O ile nie określono inaczej, takie specjalizacje powodują niezdefiniowane zachowanie. Poniższy przykład ma niezdefiniowane zachowanie, ponieważ narusza regułę, a `static_assert` nie powiodła się z powodu błędu **C2338**.

```cpp
#include <type_traits>
struct S;

template<>
struct std::is_fundamental<S> : std::true_type {};

static_assert(std::is_fundamental<S>::value, "fail");
```

Aby uniknąć tego błędu, Zdefiniuj strukturę, która dziedziczy po żądanym type_trait i specialize:

```cpp
#include <type_traits>

struct S;

template<typename T>
struct my_is_fundamental : std::is_fundamental<T> {};

template<>
struct my_is_fundamental<S> : std::true_type { };

static_assert(my_is_fundamental<S>::value, "fail");
```

### <a name="changes-to-compiler-provided-comparison-operators"></a>Zmiany w operatorach porównania dostarczonych przez kompilator

Kompilator MSVC implementuje teraz następujące zmiany w operatorach porównania na [P1630R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1630r1.html) , gdy opcja [/std: c + + Najnowsza](../build/reference/std-specify-language-standard-version.md) jest włączona:

Kompilator nie będzie już ponownie pisać wyrażeń z `operator==`, jeśli będą dotyczyć zwracanego typu, który nie jest typem **bool**. Poniższy kod generuje teraz *błąd C2088: '! = ': niedozwolony dla struktury*:

```cpp
struct U {
  operator bool() const;
};

struct S {
  U operator==(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
  return lhs != rhs;
}
```

Aby uniknąć tego błędu, należy jawnie zdefiniować wymaganego operatora:

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
    U operator!=(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

Kompilator nie będzie już definiować domyślnego operatora porównania, jeśli jest elementem członkowskim klasy podobnej do Union. Poniższy przykład tworzy teraz *C2120: "void" jest niedozwolony dla wszystkich typów*:

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const = default;
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

Aby uniknąć tego błędu, zdefiniuj treść dla operatora:

```cpp
#include <compare>

union S {
  int a;
  char b;
  auto operator<=>(const S&) const { ... }
}; 

bool lt(const S& lhs, const S& rhs) {
  return lhs < rhs;
}
```

Kompilator nie będzie już definiować domyślnego operatora porównywania, jeśli Klasa zawiera element członkowski odwołania. Poniższy kod generuje teraz *błąd C2120: element "void" jest niedozwolony dla wszystkich typów*:

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const = default;
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

Aby uniknąć tego błędu, zdefiniuj treść dla operatora:

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const { ... };
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

## <a name="update_160"></a>Poprawki błędów i zmiany zachowań w programie Visual Studio 2019

### <a name="reinterpret_cast-in-a-constexpr-function"></a>Reinterpret_cast w funkcji constexpr

**Reinterpret_cast** jest niedozwolona w funkcji **constexpr** . Kompilator firmy C++ Microsoft wcześniej odrzuci **reinterpret_cast** tylko wtedy, gdy był używany w kontekście **constexpr** . W programie Visual Studio 2019 we wszystkich trybach standardów języka kompilator prawidłowo diagnozuje **reinterpret_cast** w definicji funkcji **constexpr** . Poniższy kod generuje teraz *C3615: funkcja constexpr "f" nie może skutkować wyrażeniem stałym*.

```cpp
long long i = 0;
constexpr void f() {
    int* a = reinterpret_cast<int*>(i);
}
```

Aby uniknąć tego błędu, Usuń modyfikator **constexpr** z deklaracji funkcji.

### <a name="correct-diagnostics-for-basic_string-range-constructor"></a>Poprawna Diagnostyka dla konstruktora zakresu basic_string

W programie Visual Studio 2019 Konstruktor zakresu `basic_string` nie pomija już diagnostyki kompilatora z `static_cast`. Poniższy kod kompiluje bez ostrzeżeń w programie Visual Studio 2017, pomimo możliwej utraty danych z `wchar_t` do **char** podczas inicjowania `out`:

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Program Visual Studio 2019 poprawnie podnosi *C4244: "argument": konwersja z "wchar_t" na "const _Elem", możliwa utrata danych*. Aby uniknąć ostrzeżenia, można zainicjować std:: String, jak pokazano w poniższym przykładzie:

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>Nieprawidłowe wywołania wartości + = i-= w obszarze/CLR lub/ZW są teraz prawidłowo wykryte

W programie Visual Studio 2017 wprowadzono usterkę, która spowodowała, że kompilator ignoruje błędy i nie generuje kodu dla nieprawidłowych wywołań do + = i-= w obszarze `/clr` lub `/ZW`. Poniższy kod kompiluje się bez błędów w programie Visual Studio 2017, ale w programie Visual Studio 2019 poprawnie zgłasza *błąd C2845: "system:: String ^": arytmetyka wskaźnika nie jest dozwolona dla tego typu*:

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

Aby uniknąć błędu w tym przykładzie, użyj operatora z metodą ToString (): `s += E::e.ToString();`.

### <a name="initializers-for-inline-static-data-members"></a>Inicjatory dla wbudowanych statycznych elementów członkowskich danych

Nieprawidłowe prawa dostępu do elementów członkowskich wewnątrz **wbudowanych** i statycznych inicjatorów **constexpr** są teraz prawidłowo wykrywane. Poniższy przykład kompiluje się bez błędu w programie Visual Studio 2017, ale w programie Visual Studio 2019 w trybie `/std:c++17` *Wystąpił błąd C2248: nie można uzyskać dostępu do prywatnej składowej zadeklarowanej w klasie "X"* .

```cpp
struct X
{
    private:
        static inline const int c = 1000;
};

struct Y : X
{
    static inline int d = c; // C2248 in Visual Studio 2019
};
```

Aby uniknąć tego błędu, należy zadeklarować element członkowski `X::c` jako chroniony:

```cpp
struct X
{
    protected:
        static inline const int c = 1000;
};
```

### <a name="c4800-reinstated"></a>C4800 przywrócono

MSVC używany do uzyskania ostrzeżenia wydajności C4800 o niejawnej konwersji na **bool**. Był zbyt mało szumu i nie można go pominąć, co prowadzi do usunięcia go w programie Visual Studio 2017. Jednak przed cyklem życia programu Visual Studio 2017 mamy wiele opinii na temat przydatnych przypadków, w których rozwiązanie było rozwiązywane. Wracamy do programu Visual Studio 2019 a dokładnie dopasowane C4800 oraz wyjaśniając C4165. Oba te ostrzeżenia można łatwo pominąć za pomocą jawnego rzutowania lub w porównaniu do wartości 0 odpowiedniego typu. C4800 jest ostrzeżeniem na poziomie niestandardowym 4, a C4165 jest ostrzeżeniem o poziomie niestandardowym 3. Obie są wykrywalne przy użyciu opcji kompilatora `/Wall`.

Poniższy przykład podnosi C4800 i C4165 w `/Wall`:

```cpp
bool test(IUnknown* p)
{
    bool valid = p; // warning C4800: Implicit conversion from 'IUnknown*' to bool. Possible information loss
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return hr; // warning C4165: 'HRESULT' is being converted to 'bool'; are you sure this is what you want?
}
```

Aby uniknąć ostrzeżeń w poprzednim przykładzie, można napisać kod podobny do tego:

```cpp
bool test(IUnknown* p)
{
    bool valid = p != nullptr; // OK
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return SUCCEEDED(hr);  // OK
}
```

### <a name="local-class-member-function-doesnt-have-a-body"></a>Funkcja składowa klasy lokalnej nie ma treści

W programie Visual Studio 2017, *C4822: Funkcja składowa klasy lokalnej nie ma treści,* tylko gdy opcja kompilatora `/w14822` jest jawnie ustawiona; nie jest on pokazywany z `/Wall`. W programie Visual Studio 2019 C4822 jest ostrzeżeniem niezależnym od domyślnego, dzięki czemu można go odnaleźć w `/Wall` bez konieczności jawnego ustawiania `/w14822`.

```cpp
void example()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>Treści szablonu funkcji zawierających wyrażenie constexpr if

Jednostki funkcji szablonu zawierające instrukcje **if constexpr** mają włączone sprawdzanie związane z analizą [/permissive-](../build/reference/permissive-standards-conformance.md) . Na przykład w programie Visual Studio 2017 Poniższy kod generuje *C7510: "Type": użycie nazwy typu zależnego musi być poprzedzone prefiksem "typename"* tylko wtedy, gdy opcja **/permissive-** nie jest ustawiona. W programie Visual Studio 2019 ten sam kod zgłasza błędy nawet po ustawieniu opcji **/permissive-** :

```cpp
template <typename T>

int f()
{
    T::Type a; // error C7510

    if constexpr (T::val)
    {
        return 1;
    }
    else
    {
        return 2;
    }
}

struct X
{
    using Type = X;
    constexpr static int val = 1;
};

int main()
{
    return f<X>();
}
```

Aby uniknąć tego błędu, Dodaj słowo kluczowe**TypeName** do deklaracji `a`: `typename T::Type a;`.

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>Kod asemblera wbudowanego nie jest obsługiwany w wyrażeniu lambda

Zespół firmy C++ Microsoft był niedawno świadomy problemu zabezpieczeń, w którym użycie wbudowanego asemblera w ramach wyrażenia lambda może prowadzić do uszkodzenia `ebp` (rejestr adresów zwrotnych) w czasie wykonywania. Złośliwy atakujący może wykorzystać ten scenariusz. Mając na względzie charakter problemu, oznacza to, że wbudowany asembler jest obsługiwany tylko w architekturze x86, a słaba interakcja między asemblerem wbudowanym i resztą kompilatora, Najbezpieczniejsze rozwiązanie tego problemu było niedozwolone w wyrażeniu lambda.

Jedynym zastosowaniem asemblera wbudowanego w wyrażeniu lambda, którego znaleziono "w symbolu wieloznacznego, było przechwycenie adresu zwrotnego. W tym scenariuszu można przechwycić adres zwrotny na wszystkich platformach po prostu przy użyciu wewnętrznego `_ReturnAddress()`kompilatora.

Poniższy kod generuje *C7552: wbudowany asembler nie jest obsługiwany w wyrażeniach lambda* zarówno w programie visual studio 2017 15,9, jak i w programie visual Studio 2019:

```cpp
#include <cstdio>

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;

    auto lambda = [&]
    {
        __asm {

            mov eax, x
            mov y, eax
        }
    };

    lambda();
    return y;
}
```

Aby uniknąć tego błędu, Przenieś kod zestawu do funkcji nazwanej, jak pokazano w następującym przykładzie:

```cpp
#include <cstdio>

void g(int& x, int& y)
{
    __asm {
        mov eax, x
        mov y, eax
    }
}

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;
    auto lambda = [&]
    {
        g(x, y);
    };
    lambda();
    return y;
}

int main()
{
    std::printf("%d\n", f());
}
```

### <a name="iterator-debugging-and-stdmove_iterator"></a>Debugowanie iteratora i `std::move_iterator`

Funkcja debugowania iteratora została przeprowadzona w celu poprawnego odwinięcia `std::move_iterator`. Na przykład `std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` może teraz współdziałać z `memcpy` szybką ścieżką.

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Poprawki \<xkeycheck. h > wymuszanie słowa kluczowego

Makro biblioteki standardowej zastępujące słowo kluczowe wymuszania \<xkeycheck. h > zostało naprawione w celu wykrycia rzeczywistego słowa kluczowego problemu wykrytego zamiast komunikatu ogólnego. Obsługuje ona również słowa kluczowe języka C++ 20 i pozwala uniknąć używania funkcji IntelliSense do wymawiających losowo słów kluczowych.

### <a name="allocator-types-no-longer-deprecated"></a>Typy alokatorów nie są już przestarzałe

`std::allocator<void>`, `std::allocator::size_type`i `std::allocator::difference_type` nie są już przestarzałe.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Poprawne ostrzeżenie dotyczące zawężania konwersji ciągów

Fałszywe `static_cast` nie został wywołany przez standard, który przypadkowo pominięte ostrzeżenia C4244, które zostały usunięte z `std::string`. Próba wywołania `std::string::string(const wchar_t*, const wchar_t*)` będzie teraz prawidłowo emitować *C4244 "zawężanie wchar_t do znaku".*

### <a name="various-filesystem-correctness-fixes"></a>Różne \<systemu plików > poprawek poprawności

- Naprawiono niepowodzenie `std::filesystem::last_write_time` podczas próby zmiany czasu ostatniego zapisu katalogu.
- Konstruktor `std::filesystem::directory_entry` przechowuje teraz wynik niepowodzenia, zamiast zgłaszać wyjątek, gdy podano nieistniejącą ścieżkę docelową.
- `std::filesystem::create_directory` 2-parametrowa wersja została zmieniona w taki sposób, aby wywołała wersję 1-parametru, ponieważ podstawowa funkcja `CreateDirectoryExW` użyje `copy_symlink`, gdy `existing_p` była link symboliczny.
- `std::filesystem::directory_iterator` przestanie działać, gdy zostanie znaleziony uszkodzony link symboliczny.
- `std::filesystem::space` teraz akceptuje ścieżki względne.
- `std::filesystem::path::lexically_relative` nie jest już pomylony przez końcowe ukośniki, zgłoszone jako [LWG 3096](https://cplusplus.github.io/LWG/issue3096).
- Obejść `CreateSymbolicLinkW` odrzucanie ścieżek z ukośnikami w `std::filesystem::create_symlink`.
- Praca z trybem usuwania POSIX `delete` funkcję istniejącą w systemie Windows 10 LTSB 1609, ale w rzeczywistości nie można usunąć plików.
- Konstruktory kopiujące `std::boyer_moore_searcher` i `std::boyer_moore_horspool_searcher`i kopiujące operatory przypisania teraz rzeczywiście kopiują elementy.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Algorytmy równoległe w systemie Windows 8 i nowszych

Biblioteka algorytmów równoległych teraz prawidłowo używa rzeczywistej rodziny `WaitOnAddress` w systemie Windows 8 i nowszych wersjach, a nie zawsze z systemami Windows 7 i wcześniejszymi wersjami.

### <a name="stdsystem_categorymessage-whitespace"></a>`std::system_category::message()` białe znaki

`std::system_category::message()` teraz przycina końcowe odstępy od zwróconej wiadomości.

### <a name="stdlinear_congruential_engine-divide-by-zero"></a>`std::linear_congruential_engine` dzielenie przez zero

Niektóre warunki, które spowodują, że `std::linear_congruential_engine` wyzwolenia przez 0 zostało rozwiązane.

### <a name="fixes-for-iterator-unwrapping"></a>Poprawki dotyczące rozpakowywania iteratora

Iterator rozpakowywania, który był początkowo narażony na integrację użytkownika programisty w programie Visual Studio 2017 15,8, zgodnie C++ z opisem w artykule Blog zespołu [Funkcja STL i poprawki w programie vs 2017 15,8](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/), nie powoduje już odpakowania iteratorów pochodzących od iteratorów biblioteki standardowej. Na przykład użytkownik, który pochodzi z `std::vector<int>::iterator` i próbuje dostosować zachowanie, otrzymuje teraz dostosowane zachowanie podczas wywoływania standardowych algorytmów biblioteki zamiast zachowania wskaźnika.

Kontener nieuporządkowany `reserve` funkcja teraz faktycznie rezerwuje dla N elementów, zgodnie z opisem w [LWG 2156](https://cplusplus.github.io/LWG/issue2156).

### <a name="time-handling"></a>Obsługa czasu

- Wcześniej niektóre wartości czasu, które zostały przesłane do biblioteki współbieżności, zostałyby przepełnione, na przykład `condition_variable::wait_for(seconds::max())`. Naprawiono napływy zmieniono zachowanie na pozornie losowych cyklach 29-dniowych (w przypadku uint32_t milisekund zaakceptowanych przez bazowe interfejsy API Win32).

- Nagłówek \<CTime > teraz prawidłowo deklaruje `timespec` i `timespec_get` w przestrzeni nazw `std` oprócz deklarowania ich w globalnej przestrzeni nazw.

### <a name="various-fixes-for-containers"></a>Różne poprawki dla kontenerów

- Wiele wewnętrznych funkcji kontenera biblioteki standardowej została udostępniona jako prywatna dla udoskonalonego środowiska IntelliSense. Dodatkowe poprawki do oznaczania elementów członkowskich jako prywatne są oczekiwane w nowszych wersjach MSVC.

- Problemy z korekcją bezpieczeństwa wyjątków, w przypadku których kontenery oparte na węzłach, takie jak `list`, `map`i `unordered_map` zostałyby uszkodzone. Podczas operacji ponownego przypisywania `propagate_on_container_copy_assignment` lub `propagate_on_container_move_assignment`, firma Microsoft zwolni węzeł wskaźnikowego kontenera przy użyciu starego alokatora, wykona przypisanie POCCA/POCMA za pośrednictwem starego alokatora, a następnie spróbuje uzyskać węzeł wskaźnikowy z nowego alokatora. Jeśli ta alokacja nie powiodła się, kontener został uszkodzony i nie można go nawet zniszczyć, ponieważ właścicielem węzła wskaźnikowego jest niezmienna struktury danych. Ten kod został naprawiony, aby przydzielić nowy węzeł wskaźnikowy z programu przydzielania kontenera źródłowego przed zniszczeniem istniejącego węzła wskaźnikowego.

- Kontenery zostały naprawione tak, aby zawsze były kopiowane/przenoszone/zamieniane, w zależności od `propagate_on_container_copy_assignment`, `propagate_on_container_move_assignment`i `propagate_on_container_swap`, nawet w przypadku przyłożonych `is_always_equal`.

- Dodano przeciążenia dla operacji scalania kontenerów i Wyodrębnij funkcje członkowskie, które akceptują kontenery rvalue na [P0083 "łączenie map i zestawów"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)

### <a name="stdbasic_istreamread-processing-of-rn--n"></a>`std::basic_istream::read` przetwarzania \\r\\n = > \\n

`std::basic_istream::read` Naprawiono, aby nie zapisywać do części podanego buforu tymczasowo w ramach \\r\\n = > \\n przetwarzanie. Ta zmiana stanowi część zalet wydajności, która została uzyskana w programie Visual Studio 2017 15,8 dla odczytów o rozmiarze większym niż 4 KB. Jednak w dalszym ciągu istnieją ulepszenia wydajności przed uniknięciem trzech wywołań wirtualnych na znak.

### <a name="stdbitset-constructor"></a>Konstruktor `std::bitset`

Konstruktor `std::bitset` nie odczytuje już tych elementów i zero w kolejności odwrotnej dla dużych bitsets.

### <a name="stdpairoperator-regression"></a>regresja `std::pair::operator=`

Naprawiono regresję operatora przypisania `std::pair`wprowadzonego podczas implementowania [LWG 2729 "Brak SFINAE w std::p powietrze:: operator =";](https://cplusplus.github.io/LWG/issue2729). Teraz prawidłowo akceptuje typy umożliwiające konwersję na `std::pair`.

### <a name="non-deduced-contexts-for-add_const_t"></a>Konteksty niewnioskowane dla `add_const_t`

Naprawiono usterkę typu pomocniczego, gdzie `add_const_t` i powiązane funkcje powinny być kontekstem nieokreślonym. Innymi słowy `add_const_t` powinna być aliasem dla `typename add_const<T>::type`, a nie `const T`.

## <a name="update_162"></a>Poprawki błędów i zmiany zachowań w 16,2

### <a name="const-comparators-for-associative-containers"></a>Const komparatorów dla kontenerów asocjacyjnych

Kod dla wyszukiwania i wstawiania w [zestawie](../standard-library/set-class.md), [mapie](../standard-library/map-class.md), wielu [zestawów](../standard-library/multiset-class.md)i [multimap](../standard-library/multimap-class.md) został scalony pod kątem zmniejszonego rozmiaru kodu. Operacje wstawiania teraz wywołują mniej niż porównanie na Funktor porównania **const** w taki sam sposób, w jaki operacje wyszukiwania zostały wykonane wcześniej. Poniższy kod kompiluje się w programie Visual Studio 2019 w wersji 16,1 i starszej, ale wywołuje C3848 w programie Visual Studio 2019 w wersji 16,2:

```cpp
#include <iostream>
#include <map>

using namespace std;

struct K
{
   int a;
   string b = "label";
};

struct Comparer  {
   bool operator() (K a, K b) {
      return a.a < b.a;
   }
};

map<K, double, Comparer> m;

K const s1{1};
K const s2{2};
K const s3{3};

int main() {

   m.emplace(s1, 1.08);
   m.emplace(s2, 3.14);
   m.emplace(s3, 5.21);

}
```

Aby uniknąć tego błędu, należy uczynić operator porównania **stałą**:

```cpp
struct Comparer  {
   bool operator() (K a, K b) const {
      return a.a < b.a;
   }
};

```

::: moniker-end

::: moniker range="vs-2017"

## <a name="improvements_150"></a>Udoskonalenia zgodności w programie Visual Studio 2017 RTW (wersja 15,0)

Dzięki obsłudze uogólnionego elementu **constexpr** i inicjalizacji niestatycznej składowej danych (NSDMI) dla agregacji C++ , kompilator firmy Microsoft w programie Visual Studio 2017 jest teraz gotowy do obsługi funkcji dodanych w standardzie c++ 14. Jednak kompilator nadal nie ma kilku funkcji ze standardów C++ 11 i C++ 98. Zobacz [tabelę C++ zgodności języka firmy Microsoft](../visual-cpp-language-conformance.md) dla tabeli, która pokazuje bieżący stan kompilatora.

### <a name="c11-expression-sfinae-support-in-more-libraries"></a>C++ 11: obsługa wyrażenia SFINAE w większej liczbie bibliotek

Kompilator kontynuuje ulepszanie obsługi wyrażenia SFINAE, które jest wymagane do odejmowania argumentu szablonu i podstawienia, gdzie wyrażenia **decltype** i **constexpr** mogą być wyświetlane jako parametry szablonu. Aby uzyskać więcej informacji, zobacz temat [Expression SFINAE ulepszeń w programie Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3).

### <a name="c14-nsdmi-for-aggregates"></a>C++ 14: NSDMI dla agregacji

Agregacja jest tablicą lub klasą bez konstruktora dostarczonego przez użytkownika, bez prywatnych lub chronionych niestatycznych składowych danych, nie klas podstawowych ani żadnych funkcji wirtualnych. Od wartości zagregowanych w języku C++ 14 mogą znajdować się inicjatory elementów członkowskich. Aby uzyskać więcej informacji, zobacz [inicjatory i agregacje członków](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html).

### <a name="c14-extended-constexpr"></a>C++ 14: rozszerzone wyrażenie **constexpr**

Wyrażenia zadeklarowane jako **constexpr** mogą teraz zawierać pewne rodzaje deklaracji, instrukcje if i Switch, instrukcje Loop i mutację obiektów, których okres istnienia został rozpoczęty w wyniku obliczania wyrażenia constexpr. Ponadto nie istnieje już wymóg, że niestatyczna funkcja członkowska **constexpr** musi być niejawnie **stałą**. Aby uzyskać więcej informacji, zobacz [złagodzeniu wymagań dotyczących ograniczenia dotyczące funkcji constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html).

### <a name="c17-terse-static_assert"></a>C++ 17: zwięzła `static_assert`

parametr komunikatu dla `static_assert` jest opcjonalny. Aby uzyskać więcej informacji, zobacz [rozszerzanie static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf).

### <a name="c17-fallthrough-attribute"></a>C++ 17: atrybut `[[fallthrough]]`

W trybie **/std: c++ 17** , atrybut `[[fallthrough]]` może być używany w kontekście instrukcji switch jako wskazówkę dla kompilatora, że zachowanie "spadek liczby" jest zamierzone. Ten atrybut uniemożliwia kompilatorowi wygenerowanie ostrzeżeń w takich przypadkach. Aby uzyskać więcej informacji, zobacz [Wording for \[\[fallthrough\]\] Attribute](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf).

### <a name="generalized-range-based-for-loops"></a>Uogólniony zakres na podstawie pętli

Pętle oparte na zakresie dla pętli nie wymagają już `begin()` i `end()` zwracać obiektów tego samego typu. Ta zmiana umożliwia `end()` zwrócenia wskaźnikiem, który jest używany przez zakresy z [zakresu od 3](https://github.com/ericniebler/range-v3) do i gotowe, ale niecałkowicie opublikowane zakresy Specyfikacja techniczna. Aby uzyskać więcej informacji, zobacz [uogólnianie pętli for opartej na zakresie](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html).

## <a name="improvements_153"></a>Ulepszenia zgodności w 15,3

### <a name="constexpr-lambdas"></a>wyrażenie lambda wyrażeń constexpr

Wyrażenia lambda mogą być teraz używane w wyrażeniach stałych. Aby uzyskać więcej informacji, zobacz [constexpr wyrażeń lambda C++w ](../cpp/lambda-expressions-constexpr.md).

### <a name="if-constexpr-in-function-templates"></a>**Jeśli constexpr** w szablonach funkcji

Szablon funkcji może zawierać instrukcje **constexpr** , aby włączyć rozgałęzianie w czasie kompilacji. Aby uzyskać więcej informacji, zobacz [if constexpr instrukcji](../cpp/if-else-statement-cpp.md#if_constexpr).

### <a name="selection-statements-with-initializers"></a>Instrukcje wyboru z inicjatorami

Instrukcja **if** może zawierać inicjator, który wprowadza zmienną w zakresie bloku w samej instrukcji. Aby uzyskać więcej informacji, zobacz [instrukcje if z inicjatorem](../cpp/if-else-statement-cpp.md#if_with_init).

### <a name="maybe_unused-and-nodiscard-attributes"></a>atrybuty `[[maybe_unused]]` i `[[nodiscard]]`

Nowy atrybut `[[maybe_unused]]` powoduje wyciszenie ostrzeżeń, gdy jednostka nie jest używana. Atrybut `[[nodiscard]]` tworzy ostrzeżenie, jeśli wartość zwracana wywołania funkcji jest odrzucana. Aby uzyskać więcej informacji, zobacz [atrybuty C++w ](../cpp/attributes.md).

### <a name="using-attribute-namespaces-without-repetition"></a>Używanie przestrzeni nazw atrybutów bez powtarzania

Nowa składnia umożliwiająca włączenie tylko jednego identyfikatora przestrzeni nazw na liście atrybutów. Aby uzyskać więcej informacji, zobacz [atrybuty C++w ](../cpp/attributes.md).

### <a name="structured-bindings"></a>Powiązania strukturalne

Teraz można w jednej deklaracji przechowywać wartość przy użyciu pojedynczych nazw składników, gdy wartość jest tablicą, `std::tuple` lub `std::pair`, lub ma wszystkie publiczne niestatyczne elementy członkowskie danych. Aby uzyskać więcej informacji, zobacz [strukturalne powiązania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf) i [zwracają wiele wartości z funkcji](../cpp/functions-cpp.md#multi_val).

### <a name="construction-rules-for-enum-class-values"></a>Reguły konstrukcji dla wartości **klasy wyliczeniowej**

Teraz istnieje niejawna/zawężana konwersja z typu podstawowego wyliczenia z zakresem do samego wyliczenia, gdy jego definicja nie wprowadza modułu wyliczającego, a źródło używa składni inicjowania listy. Aby uzyskać więcej informacji, zobacz [reguły tworzenia dla wartości klasy enum](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf) i [wyliczeń](../cpp/enumerations-cpp.md#no_enumerators).

### <a name="capturing-this-by-value"></a>Przechwytywanie `*this` przez wartość

Obiekt `*this` w wyrażeniu lambda może teraz być przechwytywany przez wartość. Ta zmiana umożliwia scenariusze, w których wyrażenie lambda jest wywoływane w operacjach równoległych i asynchronicznych, szczególnie w przypadku nowszych architektur maszyn. Aby uzyskać więcej informacji, zobacz [przechwytywanie Lambda \*tego przez wartość jako \[=,\*tym\]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html).

### <a name="removing-operator-for-bool"></a>Usuwanie `operator++` dla elementu **bool**

`operator++` nie jest już obsługiwana w typach **bool** . Aby uzyskać więcej informacji, zobacz [usuwanie przestarzałego operatora + + (bool)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html).

### <a name="removing-deprecated-register-keyword"></a>Usuwanie przestarzałego słowa kluczowego **register**

Słowo kluczowe **register** , wcześniej przestarzałe (i zignorowane przez kompilator), jest teraz usuwane z języka. Aby uzyskać więcej informacji, zobacz [Usuń przestarzałe użycie słowa kluczowego Register](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html).

## <a name="improvements_155"></a>Ulepszenia zgodności w 15,5

Funkcje oznaczone \[14] są dostępne bezwarunkowo nawet w trybie **/std: c++ 14** .

### <a name="new-compiler-switch-for-extern-constexpr"></a>Nowy przełącznik kompilatora dla zewnętrznego elementu **constexpr**

We wcześniejszych wersjach programu Visual Studio kompilator zawsze otrzymał zmienną **constexpr** , która jest połączeniem wewnętrznym, nawet gdy zmienna została oznaczona jako **extern**. W programie Visual Studio 2017 w wersji 15,5 nowy przełącznik kompilatora, [/Zc: externConstexpr](../build/reference/zc-externconstexpr.md), włącza poprawne standardy — zgodność z zachowaniem. Aby uzyskać więcej informacji, zobacz [zewnętrzny związek constexpr](#extern_linkage).

### <a name="removing-dynamic-exception-specifications"></a>Usuwanie specyfikacji wyjątków dynamicznych

[P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html) Specyfikacje wyjątków dynamicznych są przestarzałe w języku C++ 11. Funkcja jest usuwana z C++ 17, ale (nadal) przestarzała Specyfikacja `throw()` jest przechowywana wyłącznie jako alias `noexcept(true)`. Aby uzyskać więcej informacji, zobacz sekcję [usuwanie specyfikacji wyjątków dynamicznych i noexcept](#noexcept_removal).

### `not_fn()`

[P0005R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html) `not_fn` to zastąpienie `not1` i `not2`.

### <a name="rewording-enable_shared_from_this"></a>Resformułowanie `enable_shared_from_this`

[P0033R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html) `enable_shared_from_this` został dodany w języku c++ 11. Standard C++ 17 aktualizuje specyfikację, aby lepiej obsługiwać niektóre przypadki narożne. [14]

### <a name="splicing-maps-and-sets"></a>Łączenie map i zestawów

[P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) Ta funkcja umożliwia wyodrębnienie węzłów z kontenerów asocjacyjnych (czyli `map`, `set`, `unordered_map``unordered_set`), które można następnie zmodyfikować i wstawić z powrotem do tego samego kontenera lub innego kontenera, który używa tego samego typu węzła. (Typowy przypadek użycia polega na wyodrębnieniu węzła z `std::map`, zmodyfikowaniu klucza i ponownie wstawieniu).

### <a name="deprecating-vestigial-library-parts"></a>Przestarzałe części biblioteki szczątkowe

[P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html) Niektóre funkcje biblioteki C++ standardowej zostały zastąpione przez nowsze funkcje w ciągu lat, a inne nie są przydatne ani problematyczne. Te funkcje są oficjalnie przestarzałe w języku C++ 17.

### <a name="removing-allocator-support-in-stdfunction"></a>Usuwanie obsługi alokatora w `std::function`

[P0302R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html) Wcześniej niż C++ 17, szablon klasy `std::function` miał kilka konstruktorów, którzy wykonali argument alokatora. Jednak użycie przystawek w tym kontekście było problematyczne, a semantyka była niejasne. Problem dla rodziny został usunięty.

### <a name="fixes-for-not_fn"></a>Poprawki dla `not_fn()`

[P0358R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html) Nowe słownictwo dla `std::not_fn` zapewnia obsługę propagacji kategorii wartości w przypadku użycia w wywołaniu otoki.

### <a name="shared_ptrt-shared_ptrtn"></a>`shared_ptr<T[]>`, `shared_ptr<T[N]>`

[P0414R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html) Scalanie `shared_ptr` zmian z bibliotek podstawowych do C++ 17. [14]

### <a name="fixing-shared_ptr-for-arrays"></a>Naprawianie `shared_ptr` dla tablic

[P0497R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html) Poprawki do shared_ptr obsługi tablic. [14]

### <a name="clarifying-insert_return_type"></a>Wyjaśnienie `insert_return_type`

[P0508R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html) Kontenery asocjacyjne z unikatowymi kluczami i kontenery nieuporządkowane z unikatowymi kluczami mają funkcję członkowską `insert`, która zwraca `insert_return_type`typu zagnieżdżonego. Ten typ zwracany jest teraz zdefiniowany jako specjalizacja typu, który jest sparametryzowane dla iteratora i NodeType kontenera.

### <a name="inline-variables-for-the-standard-library"></a>Wbudowane zmienne biblioteki standardowej

[P0607R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)

### <a name="annex-d-features-deprecated"></a>Załączniki D funkcji przestarzałe

Załącznik D w C++ standardzie zawiera wszystkie funkcje, które zostały wycofane, w tym `shared_ptr::unique()`, `<codecvt>`i `namespace std::tr1`. Gdy przełącznik kompilatora **/std: c++ 17** jest ustawiony, prawie wszystkie standardowe funkcje biblioteki w załączniku D są oznaczone jako przestarzałe. Aby uzyskać więcej informacji, zobacz [standardowe funkcje biblioteki w załączniku D są oznaczone jako przestarzałe](#annex_d).

Przestrzeń nazw `std::tr2::sys` w `<experimental/filesystem>` teraz emituje ostrzeżenie o zaniechaniu w obszarze **/std: c++ 14** domyślnie i jest teraz domyślnie usuwana w obszarze **/std: c++ 17** .

Ulepszona zgodność w `<iostream>` poprzez uniknięcie niestandardowym rozszerzeniem (jawne specjalizacje w klasie).

Biblioteka standardowa używa teraz szablonów zmiennych wewnętrznie.

Standardowa biblioteka została zaktualizowana w odpowiedzi na zmiany kompilatora C++ 17, w tym dodanie **noexcept** w systemie typów i usunięcie specyfikacji Dynamic-Exception-Specification.

## <a name="improvements_156"></a>Ulepszenia zgodności w 15,6

### <a name="c17-library-fundamentals-v1"></a>Biblioteka c++ 17 — podstawowe informacje o wersji 1

Biblioteka [P0220R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) zawiera podstawowe specyfikacje techniczne dla języka c++ 17 w standardzie. Obejmuje aktualizacje \<eksperymentalnych/spójnych >, \<eksperymentalnych/opcjonalnych >, \<eksperymentalnych/funkcjonalnych >, \<eksperymentalnych/dowolnych >, \<eksperymentalnych/string_view >, \<eksperymentalne/> \<, memory_resource eksperymentalne

### <a name="c17-improving-class-template-argument-deduction-for-the-standard-library"></a>C++ 17: ulepszanie odejmowania argumentów szablonu klasy dla standardowej biblioteki

[P0739R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html) Przenieś `adopt_lock_t` przed listą parametrów, aby `scoped_lock`, aby włączyć spójne korzystanie z `scoped_lock`. Zezwól konstruktorowi `std::variant`emu na uczestnictwo w rozpoznawaniu przeciążenia w większej liczbie przypadków, aby włączyć przypisanie kopiowania.

## <a name="improvements_157"></a>Ulepszenia zgodności w 15,7

### <a name="c17-rewording-inheriting-constructors"></a>C++ 17: odsformułowanie konstruktorów dziedziczenia

[P0136R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html) określa, że deklaracja **using** , która nazywa konstruktora, teraz sprawia, że odpowiadające konstruktory klasy bazowej widoczne są dla inicjalizacji klasy pochodnej, zamiast deklarowania dodatkowych konstruktorów klasy pochodnej. Jest to zmiana w języku C++ 14. W programie Visual Studio 2017 w wersji 15,7 lub nowszej w trybie **/std: c++ 17** kod, który jest prawidłowy w języku c++ 14 i używa konstruktorów dziedziczenia, może być nieprawidłowy lub mieć inną semantykę.

W poniższym przykładzie przedstawiono zachowanie języka C++ 14:

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

W poniższym przykładzie przedstawiono zachowanie **/std: c++ 17** w programie Visual Studio 15,7:

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

Aby uzyskać więcej informacji, zobacz [konstruktory](../cpp/constructors-cpp.md#inheriting_constructors).

### <a name="c17-extended-aggregate-initialization"></a>C++ 17: rozszerzona Inicjalizacja agregacji

[P0017R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)

Jeśli Konstruktor klasy bazowej jest niepubliczny, ale jest dostępny dla klasy pochodnej, wówczas w obszarze **/std: tryb c++ 17** w programie Visual Studio w wersji 15,7 nie można już używać pustych nawiasów klamrowych w celu zainicjowania obiektu typu pochodnego.

W poniższym przykładzie przedstawiono zachowanie zgodne z językiem C++ 14:

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

W języku C++ 17 `Derived` jest teraz uznawany za typ zagregowany. Oznacza to, że inicjalizacja `Base` za pośrednictwem prywatnego konstruktora domyślnego odbywa się bezpośrednio w ramach rozszerzonej reguły inicjowania agregacji. Wcześniej Konstruktor prywatny `Base` został wywołany za pośrednictwem konstruktora `Derived` i pomyślnie powiódł się z powodu deklaracji zaprzyjaźnionej.

W poniższym przykładzie przedstawiono zachowanie języka C++ 17 w programie Visual Studio w wersji 15,7 w **/std: c++ 17** :

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

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C++ 17: deklarowanie parametrów szablonu bez typu za pomocą

[P0127R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)

W trybie **/std: c++ 17** , kompilator może teraz ustalić typ argumentu szablonu bez typu, który jest zadeklarowany **za pomocą**Auto:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

Jednym wpływem tej nowej funkcji jest to, że prawidłowy kod języka C++ 14 może być nieprawidłowy lub może mieć inną semantykę. Na przykład niektóre przeciążenia, które były wcześniej nieprawidłowe, są teraz prawidłowe. Poniższy przykład przedstawia kod języka C++ 14, który kompiluje, ponieważ wywołanie `example(p)` jest powiązane z `example(void*);`. W programie Visual Studio 2017 w wersji 15,7, w trybie **/std: c++ 17** , szablon funkcji `example` jest najlepszym dopasowaniem.

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*) = delete;

void example(void *);

void sample(A<0> *p)
{
    example(p); // OK in C++14
}
```

W poniższym przykładzie przedstawiono kod C++ 17 w programie Visual Studio 15,7 w **/std: c++ 17** Mode:

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*);

void example(void *);

void sample(A<0> *p)
{
    example(p); // C2280: 'int example<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C++ 17: podstawowe konwersje ciągów (częściowa)

[P0067R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html) Funkcje niezależne od ustawień regionalnych dotyczące konwersji między liczbami całkowitymi i ciągami oraz między liczbami zmiennoprzecinkowymi i ciągami.

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C++ 20: uniknięcie niepotrzebnego uszkodzenia (częściowa)

[P0777R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf) Dodaje rozróżnienie między pojęciem "zanikania" i po prostu usuwa kwalifikatory const lub Reference.  Nowa cecha typu `remove_reference_t` zastępuje `decay_t` w niektórych kontekstach. Obsługa `remove_cvref_t` jest zaimplementowana w programie Visual Studio 2019.

### <a name="c17-parallel-algorithms"></a>C++ 17: algorytmy równoległe

[P0024R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html) Równoległość TS jest wbudowana w standard przy użyciu drobnych modyfikacji.

### <a name="c17-hypotx-y-z"></a>C++ 17: `hypot(x, y, z)`

[P0030R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf) Dodaje trzy nowe przeciążenia do `std::hypot`, dla typów **zmiennoprzecinkowych**, **Double**i **Long Double**, z których każdy ma trzy parametry wejściowe.

### <a name="c17-filesystem"></a>C++ 17: \<system plików >

[P0218R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html) Przyjmuje system plików TS w standardzie z kilkoma modyfikacjami wyrazów.

### <a name="c17-mathematical-special-functions"></a>C++ 17: specjalne funkcje matematyczne

[P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) Przyjmuje poprzednie specyfikacje techniczne dla funkcji matematycznych specjalnych w standardowym nagłówku \<cmath >.

### <a name="c17-deduction-guides-for-the-standard-library"></a>C++ 17: przewodniki odejmowania dla standardowej biblioteki

[P0433R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html) Aktualizacje biblioteki STL, aby skorzystać z wdrażania [P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)w języku c++ 17, które dodaje obsługę odliczania argumentów szablonu klasy.

### <a name="c17-repairing-elementary-string-conversions"></a>C++ 17: Naprawa podstawowych konwersji ciągów

[P0682R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0682r1.html) Przenieś nowe funkcje konwersji ciągów podstawowych z P0067R5 do nowego nagłówka \<charconv > i wprowadź inne udoskonalenia, w tym zmianę obsługi błędów, aby użyć `std::errc` zamiast `std::error_code`.

### <a name="c17-constexpr-for-char_traits-partial"></a>C++ 17: **constexpr** dla `char_traits` (częściowa)

[P0426R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html) Zmiany `std::traits_type` funkcji Członkowskich `length`, `compare`i `find`, aby `std::string_view` można używać w wyrażeniach stałych. (W programie Visual Studio 2017 w wersji 15,6 obsługiwane tylko dla Clang/LLVM. W wersji 15,7 Preview 2 Pomoc techniczna została również niemal zakończona dla ClXX.)

## <a name="improvements_159"></a>Ulepszenia zgodności w 15,9

### <a name="left-to-right-evaluation-order-for-operators-----and-"></a>Kolejność oceny od lewej do prawej dla operatorów `->*`, `[]`, `>>`i `<<`

Począwszy od języka C++ 17, operandy operatorów `->*`, `[]`, `>>`i `<<` muszą być oceniane w kolejności od lewej do prawej. Istnieją dwa przypadki, w których kompilator nie może zagwarantowania tej kolejności:

- gdy jedno z wyrażeń operandów jest obiektem przesłanym przez wartość lub zawiera obiekt przekazaną przez wartość lub

- po skompilowaniu przy użyciu **/CLR**, a jeden z operandów jest polem obiektu lub tablicy elementu.

Kompilator emituje ostrzeżenie [C4866](https://docs.microsoft.com/cpp/error-messages/compiler-warnings/c4866?view=vs-2017) , gdy nie może zagwarantować oceny od lewej do prawej. Kompilator generuje to ostrzeżenie tylko wtedy, gdy jest określony **/std: c++ 17** lub nowszy, zgodnie z wymaganiami w kolejności od lewej do prawej tego operatora w języku c++ 17.

Aby rozwiązać ten problem, należy najpierw rozważyć, czy nie ma potrzeby oceny operandów od lewej do prawej, na przykład gdy Ocena operandów może spowodować efekty uboczne zależne od kolejności. W wielu przypadkach kolejność, w której są oceniane operandy, nie ma zauważalnego efektu. Jeśli kolejność obliczeń musi być od lewej do prawej, należy rozważyć, czy można przekazać operandy przez odwołanie const. Ta zmiana eliminuje ostrzeżenie w następującym przykładzie kodu:

```cpp
// C4866.cpp
// compile with: /w14866 /std:c++17

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x) : x(x) {}
    HasCopyConstructor(const HasCopyConstructor& h) : x(h.x) { }
};

int operator>>(HasCopyConstructor a, HasCopyConstructor b) { return a.x >> b.x; }

// This version of operator>> does not trigger the warning:
// int operator>>(const HasCopyConstructor& a, const HasCopyConstructor& b) { return a.x >> b.x; }

int main()
{
    HasCopyConstructor a{ 1 };
    HasCopyConstructor b{ 2 };

    a>>b;        // C4866 for call to operator>>
};
```

## <a name="update_150"></a>Poprawki błędów w programie Visual Studio 2017 RTW (wersja 15,0)

### <a name="copy-list-initialization"></a>Copy-list-initialization

Program Visual Studio 2017 poprawnie wywołuje błędy kompilatora związane z tworzeniem obiektów przy użyciu list inicjatorów, które nie zostały przechwycone w programie Visual Studio 2015 i mogą prowadzić do awarii lub niezdefiniowanego zachowania środowiska uruchomieniowego. Zgodnie z N4594 13.3.1.7 P1, w ramach inicjalizacji listy kopii, kompilator jest wymagany do rozważania jawnego konstruktora do rozpoznawania przeciążenia, ale musi zgłosić błąd w przypadku wybrania określonego przeciążenia.

Poniższe dwa przykłady kompilują w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.

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

Aby poprawić błąd, użyj bezpośredniej inicjalizacji:

```cpp
A a1{ 1 };
const A& a2{ 1 };
```

W programie Visual Studio 2015 kompilator błędnie traktował inicjalizację listy kopiowania w taki sam sposób jak regularne inicjowanie kopiowania; jest on uważany tylko za konwersję konstruktorów w celu rozpoznania przeciążenia. W poniższym przykładzie program Visual Studio 2015 wybiera MyInt (23), ale program Visual Studio 2017 poprawnie zgłosi błąd.

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

Ten przykład jest podobny do poprzedniego, ale zgłasza inny błąd. To się powiedzie w programie Visual Studio 2015 i kończy się niepowodzeniem w programie Visual Studio 2017 z C2668.

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

### <a name="deprecated-typedefs"></a>Przestarzałe definicje typów

Program Visual Studio 2017 teraz wydaje poprawne Ostrzeżenie dla przestarzałych elementów typedef, które są zadeklarowane w klasie lub strukturze. Poniższy przykład kompiluje bez ostrzeżeń w programie Visual Studio 2015, ale tworzy C4996 w programie Visual Studio 2017.

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

### <a name="constexpr"></a>**constexpr**

Program Visual Studio 2017 poprawnie zgłasza błąd, gdy operand po lewej stronie operacji oceniania warunkowo nie jest prawidłowy w kontekście constexpr. Poniższy kod kompiluje w programie Visual Studio 2015, ale nie w programie Visual Studio 2017 (funkcja C3615 constexpr "f" nie może spowodować wyrażenia stałego):

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

Aby poprawić błąd, należy zadeklarować funkcję `array::size()` jako **constexpr** lub usunąć kwalifikator **constexpr** z `f`.

### <a name="class-types-passed-to-variadic-functions"></a>Typy klas przenoszone do funkcji wariadyczne

W programie Visual Studio 2017 klasy lub struktury, które są przenoszone do funkcji wariadyczne, takie jak printf, muszą być proste do skopiowania. Podczas przekazywania takich obiektów kompilator po prostu wykonuje kopię bitową i nie wywołuje konstruktora ani destruktora.

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

Aby poprawić błąd, można wywołać funkcję członkowską, która zwraca typ z możliwością kopiowania,

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

lub można użyć rzutowania statycznego, aby przekonwertować obiekt przed jego przekazaniem:

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

W przypadku ciągów skompilowanych i zarządzanych przy użyciu CString, podane `operator LPCTSTR()` powinny być używane do rzutowania obiektu CString na wskaźnik C oczekiwany przez ciąg formatu.

```cpp
CString str1;
CString str2 = _T("hello!");
str1.Format(_T("%s"), static_cast<LPCTSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>Kwalifikatory CV w konstrukcji klasy

W programie Visual Studio 2015 kompilator czasami niepoprawnie ignoruje kwalifikator CV podczas generowania obiektu klasy za pośrednictwem wywołania konstruktora. Przyczyną tego problemu może być awaria lub nieoczekiwane zachowanie środowiska uruchomieniowego. Poniższy przykład kompiluje w programie Visual Studio 2015, ale wywołuje błąd kompilatora w programie Visual Studio 2017:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Aby poprawić błąd, zadeklaruj `operator int()` jako **const**.

### <a name="access-checking-on-qualified-names-in-templates"></a>Sprawdzanie dostępu do nazw kwalifikowanych w szablonach

Poprzednie wersje kompilatora nie sprawdzają dostępu do nazw kwalifikowanych w niektórych kontekstach szablonów. Ten problem może zakłócać oczekiwane zachowanie SFINAE, w którym zastępowanie oczekuje się niepowodzeniem z powodu niedostępności nazwy. Przyczyną może być awaria lub nieoczekiwane zachowanie w czasie wykonywania, ponieważ kompilator nieprawidłowo wywołuje nieprawidłowe Przeciążenie operatora. W programie Visual Studio 2017 został zgłoszony błąd kompilatora. Konkretny błąd może się różnić, ale zazwyczaj jest "C2672 nie znaleziono zgodnej przeciążonej funkcji". Poniższy kod kompiluje się w programie Visual Studio 2015, ale zgłasza błąd w programie Visual Studio 2017:

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

### <a name="missing-template-argument-lists"></a>Brak list argumentów szablonu

W programie Visual Studio 2015 i starszych kompilator nie zdiagnozowanł brakujących list argumentów szablonu, gdy szablon pojawił się na liście parametrów szablonu, na przykład jako część argumentu szablonu domyślnego lub parametru szablonu bez typu. Przyczyną tego problemu może być nieprzewidywalne zachowanie, w tym awarie kompilatora lub nieoczekiwane zachowanie środowiska uruchomieniowego. Poniższy kod kompiluje się w programie Visual Studio 2015, ale generuje błąd w programie Visual Studio 2017.

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Expression-SFINAE

Aby można było obsługiwać polecenie Expression-SFINAE, kompilator analizuje teraz argumenty **decltype** , gdy są one deklarowane zamiast tworzenia wystąpienia. W związku z tym, jeśli w argumencie decltype zostanie znaleziony niezależna specjalizacja, nie zostanie ona odroczona do utworzenia wystąpienia. Jest on przetwarzany natychmiast i wszystkie wynikłe błędy są zdiagnozowane w tym czasie.

Poniższy przykład pokazuje błąd kompilatora, który jest wywoływany w punkcie deklaracji:

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

### <a name="classes-declared-in-anonymous-namespaces"></a>Klasy zadeklarowane w anonimowych przestrzeniach nazw

Zgodnie ze C++ standardem Klasa zadeklarowana wewnątrz anonimowej przestrzeni nazw ma połączenie wewnętrzne i oznacza, że nie można jej wyeksportować. W programie Visual Studio 2015 i starszych ta reguła nie została wymuszona. W programie Visual Studio 2017 reguła jest wymuszana częściowo. Poniższy przykład wywołuje ten błąd w programie Visual Studio 2017: "Error C2201: const Anonymous Namespace:: S1:: vftable: musi mieć zewnętrzne połączenie, aby można było je wyeksportować/zaimportować".

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>Domyślne inicjatory dla elementów członkowskich klasy wartościC++(/CLI)

W programie Visual Studio 2015 i starszych kompilator dozwolony (ale ignorowany) domyślny inicjator elementu członkowskiego dla elementu członkowskiego klasy wartości. Domyślna Inicjalizacja klasy wartości zawsze zero — inicjuje członków. Konstruktor domyślny jest niedozwolony. W programie Visual Studio 2017 domyślne inicjatory elementów członkowskich zgłaszają błąd kompilatora, jak pokazano w tym przykładzie:

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // isn't allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Indeksatory domyślne (C++/CLI)

W programie Visual Studio 2015 i starszych kompilator w niektórych przypadkach nie określił domyślnej właściwości jako domyślnego indeksatora. Można obejść ten problem, używając **domyślnego** identyfikatora, aby uzyskać dostęp do właściwości. Samo obejście stało się problematyczne po wprowadzeniu **domyślnego** jako słowa kluczowego w języku c++ 11. W programie Visual Studio 2017 błędy, które wymagały obejścia, zostały naprawione, a kompilator zgłasza błąd, gdy **wartość domyślna** jest używana do uzyskiwania dostępu do domyślnej właściwości klasy.

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

W programie Visual Studio 2017 można uzyskać dostęp do obu właściwości wartości według ich nazwy:

```cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="update_153"></a>Poprawki błędów w 15,3

### <a name="calls-to-deleted-member-templates"></a>Wywołania usuniętych szablonów elementów członkowskich

W poprzednich wersjach programu Visual Studio kompilator w niektórych przypadkach nie wyemituje błędu dla niepoprawnie sformułowanych wywołań do usuniętego szablonu elementu członkowskiego, który mógłby spowodować awarię w czasie wykonywania. Poniższy kod generuje teraz C2280 "" int S\<int >:: f\<int > (void) ': próba odwołująca się do usuniętej funkcji ":

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

Aby naprawić ten błąd, zadeklaruj `i` jako **int**.

### <a name="pre-condition-checks-for-type-traits"></a>Sprawdzanie warunków wstępnych dla cech typu

Program Visual Studio 2017 w wersji 15,3 poprawia warunki wstępne dla cech typu, aby dokładniej przestrzegać standardu. Takie sprawdzenie jest przeznaczone do przypisania. Poniższy kod generuje C2139 w programie Visual Studio 2017 w wersji 15,3:

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Nowe ostrzeżenie kompilatora i testy środowiska uruchomieniowego na potrzeby organizowania w trybie macierzystym

Wywołanie z funkcji zarządzanych do funkcji natywnych wymaga organizowania. Środowisko CLR wykonuje kierowanie, ale nie rozpoznaje C++ semantyki. W przypadku przekazania obiektu macierzystego przez wartość środowisko CLR wywołuje Konstruktor kopiujący obiektu lub używa `BitBlt`, co może spowodować niezdefiniowane zachowanie w czasie wykonywania.

Teraz kompilator emituje ostrzeżenie, jeśli może wiedzieć w czasie kompilacji, że obiekt macierzysty z usuniętym elementem Copy ctor jest przenoszona między natywną i zarządzaną granicą przez wartość. Dla tych przypadków, w których kompilator nie wie w czasie kompilacji, wprowadza sprawdzanie środowiska uruchomieniowego, aby program wykonywał `std::terminate` natychmiast po niepoprawnym kierowaniu. W programie Visual Studio 2017 w wersji 15,3 Poniższy kod generuje ostrzeżenie C4606 "A": przekazywanie argumentu przez wartość w obrębie natywnej i zarządzanej granicy wymaga prawidłowego konstruktora kopiującego. W przeciwnym razie zachowanie środowiska uruchomieniowego jest niezdefiniowane.

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
    f(A()); // This call from managed to native requires marshaling. The CLR doesn't understand C++ and uses BitBlt, which results in a double-free later.
}
```

Aby naprawić ten błąd, Usuń dyrektywę `#pragma managed`, aby oznaczyć obiekt wywołujący jako natywny i uniknąć organizowania.

### <a name="experimental-api-warning-for-winrt"></a>Ostrzeżenie eksperymentalnego interfejsu API dla środowiska WinRT

Interfejsy API środowiska WinRT, które są udostępniane na potrzeby eksperymentowania i przesyłania opinii, są dekoracyjne `Windows.Foundation.Metadata.ExperimentalAttribute`. W programie Visual Studio 2017 w wersji 15,3 kompilator generuje ostrzeżenie C4698 podczas napotkania atrybutu. Kilka interfejsów API we wcześniejszych wersjach Windows SDK zostało już uzupełnione atrybutem, a wywołania tych interfejsów API teraz wyzwalają to ostrzeżenie kompilatora. Nowsze zestawy SDK systemu Windows mają atrybut usunięty ze wszystkich typów wysłanych, ale jeśli używasz starszego zestawu SDK, musisz pominąć te ostrzeżenia dla wszystkich wywołań typów wysłanych.

Poniższy kod generuje ostrzeżenie C4698: "" system Windows:: Storage:: IApplicationDataStatics2:: GetForUserAsync "jest przeznaczony wyłącznie do celów ewaluacyjnych i może zostać zmieniony lub usunięty w przyszłych aktualizacjach":

```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); //C4698
```

Aby wyłączyć ostrzeżenie, Dodaj #pragma:

```cpp
#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>Definicja poza wierszem funkcji składowej szablonu

Program Visual Studio 2017 w wersji 15,3 generuje błąd podczas napotkania nieprawidłowej definicji funkcji składowej szablonu, która nie została zadeklarowana w klasie. Poniższy kod generuje teraz błąd C2039: ' f ': nie jest składową ':

```cpp
struct S {};

template <typename T>
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

Aby naprawić ten błąd, Dodaj deklarację do klasy:

```cpp
struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Podjęto próbę uzyskania adresu **tego** wskaźnika

C++ Jest **to** wartością prvalue bez typu wskaźnika do X. Nie można pobrać adresu **tego** elementu lub powiązać go z odwołaniem do lvalue. W poprzednich wersjach programu Visual Studio kompilator zezwolił na obejście tego ograniczenia przez użycie rzutowania. W programie Visual Studio 2017 w wersji 15,3 kompilator tworzy błąd C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Konwersja do niedostępnej klasy bazowej

Program Visual Studio 2017 w wersji 15,3 generuje błąd podczas próby przekonwertowania typu na klasę bazową, która jest niedostępna. Kompilator podnosi teraz "Error C2243:" Type CAST ": konwersja z" 'D * "na" B * "istnieje, ale jest niedostępna. Następujący kod jest źle sformułowany i może spowodować awarię w czasie wykonywania. Kompilator tworzy teraz C2243, gdy napotka następujący kod:

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-arent-allowed-on-out-of-line-definitions-of-member-functions"></a>Argumenty domyślne nie są dozwolone dla definicji poza wierszem funkcji Członkowskich

Argumenty domyślne nie są dozwolone w definicjach wbudowanych funkcji Członkowskich w klasach szablonów. Kompilator wyda ostrzeżenie w obszarze **/permissive**i twardy błąd w obszarze [/permissive-](../build/reference/permissive-standards-conformance.md).

W poprzednich wersjach programu Visual Studio następujący źle skonstruowany kod może potencjalnie spowodować awarię środowiska uruchomieniowego. Program Visual Studio 2017 w wersji 15,3 generuje ostrzeżenie C5034: "A\<T >:: f": Definicja poza wierszem składowej szablonu klasy nie może mieć argumentów domyślnych:

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

Aby naprawić ten błąd, Usuń domyślny argument `= false`.

### <a name="use-of-offsetof-with-compound-member-designator"></a>Użycie `offsetof` ze wskaźnikiem złożonego elementu członkowskiego

W programie Visual Studio 2017 w wersji 15,3 przy użyciu `offsetof(T, m)` gdzie *m* jest "wskaźnikiem złożonego elementu członkowskiego" powoduje wyświetlenie ostrzeżenia podczas kompilowania z użyciem opcji **/Wall** . Następujący kod jest źle sformułowany i może spowodować awarię w czasie wykonywania. Program Visual Studio 2017 w wersji 15,3 tworzy "ostrzeżenie C4841: użyto niestandardowego rozszerzenia: wyznaczania składowej złożonego w makro OffsetOf":

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

Aby naprawić kod, Wyłącz ostrzeżenie przy użyciu dyrektywy pragma lub Zmień kod, aby nie używał `offsetof`:

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Używanie `offsetof` ze statycznym elementem członkowskim danych lub funkcją członkowską

W programie Visual Studio 2017 w wersji 15,3 przy użyciu `offsetof(T, m)` gdzie *m* odwołuje się do statycznej składowej danych lub funkcji składowej w wyniku błędu. Poniższy kod generuje wartość "Error C4597: undefineed Behavior: makro OffsetOf zastosowana do funkcji składowej" example "" i "Error C4597: undefined Behavior: makro OffsetOf zastosowana do statycznej składowej danych" sample "":

```cpp
#include <cstddef>

struct A {
   int ten() { return 10; }
   static constexpr int two = 2;
};

constexpr auto off = offsetof(A, ten);
constexpr auto off2 = offsetof(A, two);
```

Ten kod jest źle sformułowany i może spowodować awarię w czasie wykonywania. Aby naprawić ten błąd, Zmień kod, aby nie wywoływać niezdefiniowanego zachowania. Nie jest to kod przenośny, który jest niedozwolony przez C++ Standard.

### <a name="declspec"></a>Nowe ostrzeżenie dotyczące atrybutów `__declspec`

W programie Visual Studio 2017 w wersji 15,3 kompilator nie ignoruje atrybutów, jeśli `__declspec(...)` jest stosowany przed specyfikacją powiązania `extern "C"`. Wcześniej kompilator zignoruje atrybut, który może mieć konsekwencje dla środowiska uruchomieniowego. Po ustawieniu opcji **/Wall** i **/WX** , poniższy kod generuje wartość "Warning C4768: __declspec Attributes zanim Specyfikacja powiązania zostanie zignorowana":

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Aby usunąć ostrzeżenie, najpierw umieść `extern "C"`:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

To ostrzeżenie jest domyślnie wyłączone w 15,3, ale domyślnie włączone w 15,5 i ma wpływ tylko na kod skompilowany przy użyciu **/Wall** **/WX**.

### <a name="decltype-and-calls-to-deleted-destructors"></a>**decltype** i wywołania usuniętych destruktorów

W poprzednich wersjach programu Visual Studio kompilator nie wykrył, kiedy wywołanie usuniętego destruktora wystąpi w kontekście wyrażenia skojarzonego z **decltype**. W programie Visual Studio 2017 w wersji 15,3 następujący kod generuje komunikat "Error C2280:" A\<T >:: ~ A (void) ': próba odwołująca się do usuniętej funkcji ":

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

### <a name="uninitialized-const-variables"></a>Niezainicjowane zmienne const

Wersja programu Visual Studio 2017 RTW ma regresję, w C++ której kompilator nie wystawia diagnostyki, jeśli zmienna **const** nie została zainicjowana. Ta regresja została naprawiona w programie Visual Studio 2017 w wersji 15,3. Poniższy kod generuje teraz "ostrzeżenie C4132:" value ": obiekt const powinien zostać zainicjowany":

```cpp
const int Value; //C4132
```

Aby naprawić ten błąd, przypisz wartość do `Value`.

### <a name="empty-declarations"></a>Puste deklaracje

Program Visual Studio 2017 w wersji 15,3 wyświetla teraz ostrzeżenie dotyczące pustych deklaracji dla wszystkich typów, a nie tylko typów wbudowanych. Poniższy kod tworzy teraz ostrzeżenie C4091 poziomu 2 dla wszystkich czterech deklaracji:

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

Aby usunąć ostrzeżenia, skomentować lub usunąć puste deklaracje. W przypadkach, gdy obiekt bez nazwy ma wpływ na efekt uboczny (na przykład RAII), powinien mieć nazwę.

Ostrzeżenie jest wyłączone w obszarze **/WV: 18** i jest domyślnie włączone w obszarze ostrzegawczy poziom W2.

### <a name="stdis_convertible-for-array-types"></a>`std::is_convertible` typów tablic

Poprzednie wersje kompilatora udzieliły nieprawidłowych wyników dla typów tablicowych [std:: is_convertible](../standard-library/is-convertible-class.md) . Te wymagane przez bibliotekę moduły zapisujące mają specjalne użycie C++ w kompilatorze firmy Microsoft w przypadku używania cech typu `std::is_convertible<...>`. W poniższym przykładzie, statyczne potwierdzenia są przekazywane we wcześniejszych wersjach programu Visual Studio, ale kończą się niepowodzeniem w programie Visual Studio 2017 w wersji 15,3:

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>` jest obliczana przez sprawdzenie, czy definicja funkcji urojonej jest poprawnie sformułowana:

```cpp
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdis_constructible"></a>Prywatne destruktory i `std::is_constructible`

Poprzednie wersje kompilatora zostały zignorowane, niezależnie od tego, czy destruktor był prywatny podczas decydowania o wyniku [std:: is_constructible](../standard-library/is-constructible-class.md). Teraz traktuje je. W poniższym przykładzie, statyczne potwierdzenia są przekazywane we wcześniejszych wersjach programu Visual Studio, ale kończą się niepowodzeniem w programie Visual Studio 2017 w wersji 15,3:

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

Prywatne destruktory powodują, że typ nie jest konstrukcyjną. `std::is_constructible<T, Args...>` jest obliczana tak, jakby została zapisywana następująca deklaracja:

```cpp
   T obj(std::declval<Args>()...)
```

To wywołanie implikuje wywołanie destruktora.

### <a name="c2668-ambiguous-overload-resolution"></a>C2668: niejednoznaczne Rozpoznanie przeciążenia

W poprzednich wersjach kompilatora czasami nie można wykryć niejednoznaczności, gdy znaleziono wiele kandydatów za pośrednictwem deklaracji using i wyszukiwania zależnego od argumentów. Ten błąd może prowadzić do wybranego błędnego przeciążenia i do nieoczekiwanego zachowania w czasie wykonywania. W poniższym przykładzie program Visual Studio 2017 w wersji 15,3 poprawnie podnosi C2668 "f": niejednoznaczne wywołanie przeciążonej funkcji:

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

Aby naprawić kod, Usuń instrukcję using `N::f`, jeśli zamierzasz wywołać `::f()`.

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660: lokalne deklaracje funkcji i wyszukiwanie zależne od argumentów

Deklaracje funkcji lokalnych — ukrywanie deklaracji funkcji w otaczającym zakresie i wyłączanie wyszukiwania zależnego od argumentów. Jednak poprzednie wersje kompilatora wykonali wyszukiwanie zależne od argumentów w tym przypadku, które mogą spowodować błędne Przeciążenie i nieoczekiwane zachowanie w czasie wykonywania. Zazwyczaj błąd jest spowodowany niepoprawną sygnaturą deklaracji funkcji lokalnej. W poniższym przykładzie program Visual Studio 2017 w wersji 15,3 poprawnie podnosi C2660 "f": funkcja nie przyjmuje dwóch argumentów:

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

Aby rozwiązać ten problem, Zmień podpis `f(S)` lub usuń go.

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038: kolejność inicjowania na listach inicjatorów

Elementy członkowskie klasy są inicjowane w kolejności, w jakiej zostały zadeklarowane, a nie kolejności, w której występują listy inicjatorów. Poprzednie wersje kompilatora nie ostrzegają, gdy porządek listy inicjatora różni się od kolejności deklaracji. Ten problem może prowadzić do niezdefiniowanego zachowania środowiska uruchomieniowego, jeśli Inicjalizacja jednego elementu członkowskiego zależała od innego elementu członkowskiego na liście, który jest już zainicjowany. W poniższym przykładzie program Visual Studio 2017 w wersji 15,3 (with **/Wall**) podnosi wartość "Warning C5038: składowa danych" a:: y "zostanie zainicjowana po elemencie członkowskim danych" a:: x "":

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

Aby rozwiązać ten problem, Rozmieść listę inicjatorów tak samo jak w przypadku deklaracji. Podobne ostrzeżenie jest zgłaszane, gdy jeden lub oba inicjatory odnoszą się do składowych klasy bazowej.

To ostrzeżenie jest domyślnie wyłączone i ma wpływ tylko na kod skompilowany przy użyciu **/Wall**.

## <a name="update_155"></a>Poprawki błędów i inne zmiany zachowań w 15,5

### <a name="partial-ordering-change"></a>Zmiana kolejności częściowej

Kompilator prawidłowo odrzuca Poniższy kod i wyświetla prawidłowy komunikat o błędzie:

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

Problem opisany w powyższym przykładzie polega na tym, że istnieją dwie różnice w typach (const a non-const i Pack a pakiet poza pakietem). Aby wyeliminować błąd kompilatora, Usuń jedną z różnic. Dzięki temu kompilator jednoznacznie porządkuje funkcje.

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

### <a name="exception-handlers"></a>Mechanizmy obsługi wyjątków

Procedury obsługi odwołania do typu tablicy lub funkcji nigdy nie są zgodne z żadnym obiektem wyjątku. Kompilator prawidłowo przestrzega tej reguły i wywołuje ostrzeżenie poziomu 4. Nie dopasowuje już również procedury obsługi `char*` lub `wchar_t*` do literału ciągu, gdy jest używany **/Zc: strictStrings** .

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

Poniższy kod pozwala uniknąć błędu:

```cpp
catch (int (*)[1]) {}
```

### <a name="tr1"></a>Przestrzeń nazw `std::tr1` jest przestarzała

Niestandardowa przestrzeń nazw `std::tr1` jest teraz oznaczona jako przestarzała w trybach C++ 14 i C++ 17. W programie Visual Studio 2017 w wersji 15,5 następujący kod wywołuje C4996:

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
warning C4996: 'std::tr1': warning STL4002: The non-standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
```

Aby naprawić ten błąd, usuń odwołanie do przestrzeni nazw `tr1`:

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

Gdy przełącznik kompilatora **/std: c++ 17** jest ustawiony, prawie wszystkie standardowe funkcje biblioteki w załączniku D są oznaczone jako przestarzałe.

W programie Visual Studio 2017 w wersji 15,5 następujący kod wywołuje C4996:

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
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
```

Aby naprawić ten błąd, postępuj zgodnie z instrukcjami wyświetlanymi w tekście ostrzegawczym, jak pokazano w poniższym kodzie:

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

### <a name="unreferenced-local-variables"></a>Zmienne lokalne, do których nie istnieją odwołania

W programie Visual Studio 15,5 ostrzeżenie C4189 jest emitowane w więcej przypadków, jak pokazano w poniższym kodzie:

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}
```

```Output
warning C4189: 's': local variable is initialized but not referenced
```

Aby naprawić ten błąd, Usuń nieużywaną zmienną.

### <a name="single-line-comments"></a>Komentarze jednowierszowe

W programie Visual Studio 2017 w wersji 15,5 ostrzeżenia C4001 i C4179 nie są już emitowane przez kompilator języka C. Wcześniej były emitowane tylko przy użyciu przełącznika kompilatora **/za** .  Ostrzeżenia nie są już potrzebne, ponieważ Komentarze jednowierszowe były częścią standardu C od C99.

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

Jeśli kod nie musi być zgodny z poprzednimi wersjami, można uniknąć ostrzeżenia przez usunięcie pomijania C4001/C4179. Jeśli kod musi być zgodny z poprzednimi wersjami, Pomiń tylko C4619.

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="__declspec-attributes-with-extern-c-linkage"></a>`__declspec` atrybutów z powiązaniem `extern "C"`

We wcześniejszych wersjach programu Visual Studio kompilator zignorował `__declspec(...)` atrybuty, gdy `__declspec(...)` został zastosowany przed specyfikacją powiązania `extern "C"`. To zachowanie spowodowało wygenerowanie kodu, który nie jest przeznaczony dla użytkownika, z możliwymi implikacjami środowiska uruchomieniowego. Ostrzeżenie zostało dodane w programie Visual Studio w wersji 15,3, ale było domyślnie wyłączone. W programie Visual Studio 2017 w wersji 15,5 ostrzeżenie jest domyślnie włączone.

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

Aby naprawić ten błąd, należy umieścić specyfikację powiązania przed atrybutem __declspec:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Ten nowy C4768 ostrzegawczy jest określony w niektórych nagłówkach Windows SDK, które zostały dostarczone z programem Visual Studio 2017 15,3 lub starszym (na przykład: Version 10.0.15063.0, znanym również jako RS2 SDK). Jednak późniejsze wersje nagłówków Windows SDK (w tym ShlObj. h i ShlObj_core. h) zostały naprawione, aby nie wygenerowały ostrzeżenia. Po wyświetleniu tego ostrzeżenia pochodzącego z nagłówków Windows SDK można wykonać następujące czynności:

1. Przejdź do najnowszego Windows SDK dołączonego do wersji 15,5 programu Visual Studio 2017.

1. Wyłącz ostrzeżenie wokół #include instrukcji Windows SDK nagłówka:

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern_linkage"></a>Zewnętrzny związek constexpr

We wcześniejszych wersjach programu Visual Studio kompilator zawsze otrzymał zmienną **constexpr** , która jest połączeniem wewnętrznym, nawet gdy zmienna została oznaczona jako **extern**. W programie Visual Studio 2017 w wersji 15,5 nowy przełącznik kompilatora ( **/Zc: externConstexpr**) włącza poprawne standardy — zgodność z zachowaniem. Ostatecznie to zachowanie stanie się wartością domyślną.

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

Jeśli plik nagłówkowy zawiera zmienną zadeklarowaną jako **extern constexpr**, należy ją oznaczyć `__declspec(selectany)`, aby pozostały prawidłowo połączone deklaracje:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>nie można użyć elementu **typeid** dla niekompletnego typu klasy

We wcześniejszych wersjach programu Visual Studio kompilator niepoprawnie zezwolił na następujący kod, co spowodowało nieprawidłowe informacje o typie. W programie Visual Studio 2017 w wersji 15,5 kompilator prawidłowo zgłasza błąd:

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdis_convertible-target-type"></a>Typ elementu docelowego `std::is_convertible`

`std::is_convertible` wymaga, aby typ docelowy był prawidłowym typem zwracanym. We wcześniejszych wersjach programu Visual Studio kompilator nieprawidłowo zezwolił typy abstrakcyjne, co może prowadzić do niepoprawnego rozpoznawania przeciążenia i niezamierzonego zachowania w czasie wykonywania.  Następujący kod teraz prawidłowo podnosi C2338:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5
```

Aby uniknąć błędu, podczas korzystania z `is_convertible` należy porównać typy wskaźnika, ponieważ porównanie typu niebędącego wskaźnikiem może zakończyć się niepowodzeniem, jeśli jeden typ jest abstrakcyjny:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");
```

### <a name="noexcept_removal"></a>Usuwanie specyfikacji wyjątku dynamicznego i **noexcept**

W języku C++ 17 `throw()` jest aliasem dla **noexcept**, `throw(<type list>)` i `throw(...)` są usuwane, a niektóre typy mogą zawierać **noexcept**. Ta zmiana może powodować problemy ze zgodnością źródła z kodem, który jest zgodny z językiem C++ 14 lub wcześniejszym. **/Zc: noexceptTypes-** Switch może służyć do przywracania wersji języka c++ 14 o wartości **noexcept** w trybie ogólnym, w którym jest używany tryb c++ 17. Umożliwia zaktualizowanie kodu źródłowego tak, aby był zgodny z językiem C++ 17 bez konieczności ponownego zapisywania całego kodu `throw()`.

Kompilator również diagnozuje teraz bardziej niezgodne specyfikacje wyjątków w deklaracjach w trybie C++ 17 lub z [/permissive-](../build/reference/permissive-standards-conformance.md) z nowym ostrzeżeniem C5043.

Poniższy kod generuje C5043 i C5040 w programie Visual Studio 2017 w wersji 15,5 w przypadku zastosowania przełącznika **/std: c++ 17** :

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

Aby usunąć błędy nadal przy użyciu **/std: c++ 17**, Dodaj **/Zc: noexceptTypes-** Switch do wiersza polecenia lub w przeciwnym razie zaktualizuj kod, aby użyć **noexcept**, jak pokazano w następującym przykładzie:

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

### <a name="inline-variables"></a>Zmienne wbudowane

Statyczne elementy członkowskie danych constexpr są teraz niejawnie wbudowane, co oznacza, że ich deklaracja w klasie jest teraz definicją. Użycie definicji poza wierszem statycznego elementu członkowskiego danych constexpr jest nadmiarowe i obecnie przestarzałe. W programie Visual Studio 2017 w wersji 15,5, gdy zostanie zastosowany przełącznik **/std: c++ 17** , w poniższym kodzie zostanie wygenerowane ostrzeżenie C5041 *"size": Definicja poza wierszem elementu członkowskiego danych statycznych constexpr nie jest wymagana i jest przestarzała w języku c++ 17*:

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-__declspec-warning-c4768-now-on-by-default"></a>Domyślnie `extern "C" __declspec(...)` ostrzeżenie C4768 teraz

Ostrzeżenie zostało dodane w programie Visual Studio 2017 w wersji 15,3, ale było domyślnie wyłączone. W programie Visual Studio 2017 w wersji 15,5 ostrzeżenie jest domyślnie włączone. Aby uzyskać więcej informacji, zobacz [nowe ostrzeżenie na \_\_atrybutów declspec](#declspec).

### <a name="defaulted-functions-and-__declspecnothrow"></a>Funkcje domyślne i `__declspec(nothrow)`

Kompilator wcześniej zezwolił na zadeklarowanie domyślnych funkcji, które mają być deklarowane przy użyciu `__declspec(nothrow)`, gdy odpowiadające im funkcje podstawowe/składowe dopuszczają wyjątki. To zachowanie jest sprzeczne ze C++ standardem i może spowodować niezdefiniowane zachowanie w czasie wykonywania. Standard wymaga, aby te funkcje były zdefiniowane jako usunięte, jeśli występuje niezgodność specyfikacji wyjątków.  W obszarze **/std: c++ 17**, poniższy kod wywołuje C2280 *próby odwołania do usuniętej funkcji. Funkcja została niejawnie usunięta, ponieważ jawna Specyfikacja wyjątku jest niezgodna z klauzulą deklaracji niejawnej.*

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

Aby poprawić ten kod, Usuń __declspec (nothrow) z funkcji Default lub Usuń `= default` i podaj definicję dla funkcji wraz z wymaganą obsługą wyjątków:

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

### <a name="noexcept-and-partial-specializations"></a>**noexcept** i częściowe specjalizacje

W przypadku opcji **noexcept** w systemie typów częściowe specjalizacje w celu dopasowania określonych typów "możliwy do przełączenia" mogą się nie powieść lub wybrać szablon podstawowy z powodu braku częściowej specjalizacji dla wskaźników do-noexcept-Functions.

W takich przypadkach może być konieczne dodanie kolejnych częściowych specjalizacji do obsługi wskaźników funkcji **noexcept** i wskaźników **noexcept** do funkcji składowych. Te przeciążenia są dozwolone tylko w trybie **/std: c++ 17** . Jeśli należy zachować zgodność z poprzednimi wersjami przy użyciu języka C++ 14 i napisać kod, który są używane przez inne osoby, należy chronić te nowe przeciążenia w ramach dyrektyw `#ifdef`. Jeśli pracujesz w module samodzielnym, a nie korzystasz z funkcji `#ifdef` Guard, możesz ją skompilować bezpośrednio przy użyciu przełącznika **/Zc: noexceptTypes** .

Poniższy kod kompiluje się pod **/std: c++ 14** , ale nie działa w **/std: c++ 17** z "Error C2027: use undefined Type" A\<t > "":

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

Następujący kod powiódł się pod **/std: c++ 17** , ponieważ kompilator wybiera nową `A<void (*)() noexcept>`specjalizacji:

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

## <a name="update_157"></a>Poprawki błędów i inne zmiany zachowań w 15,7

### <a name="c17-default-argument-in-the-primary-class-template"></a>C++ 17: domyślny argument w szablonie klasy podstawowej

Ta zmiana zachowania jest warunkiem wstępnym [odejmowania argumentu szablonu dla szablonów klas — P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html).

Wcześniej kompilator zignorował domyślny argument w szablonie klasy podstawowej:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

W **/std: tryb c++ 17** w programie Visual Studio 2017 w wersji 15,7, domyślny argument nie jest ignorowany:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>Rozpoznawanie nazw zależnych

Ta zmiana zachowania jest warunkiem wstępnym [odejmowania argumentu szablonu dla szablonów klas — P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html).

W poniższym przykładzie kompilator w programie Visual Studio 15,6 i starszych rozpoznaje `D::type` do `B<T>::type` w szablonie klasy podstawowej.

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

Program Visual Studio 2017 w wersji 15,7, w trybie **/std: c++ 17** , wymaga słowa kluczowego**TypeName** w instrukcji **using** w D. Bez**atrybutu TypeName**kompilator wywołuje ostrzeżenie C4346: *"B < T\*>:: Type": Nazwa zależna nie jest typem* i błędem C2061: *błąd składniowy: Identyfikator "Type*":

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

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C++ 17: atrybut `[[nodiscard]]` — zwiększenie poziomu ostrzeżenia

W programie Visual Studio 2017 w wersji 15,7 w trybie **/std: c++ 17** tryb ostrzegawczy C4834 ("odrzucanie zwracanej wartości funkcji z atrybutem" nodiscard ") został zwiększony z platformy W3 do W1. Można wyłączyć ostrzeżenie z rzutowaniem na wartość **void**lub przekazując **/WD: 4834** do kompilatora

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Lista inicjowania klasy bazowej konstruktora szablonów wariadyczne

W poprzednich wersjach programu Visual Studio Lista inicjowania klasy bazowej konstruktora szablonów wariadyczne, w której brakuje argumentów szablonu, została błędnie dozwolona bez błędu. W programie Visual Studio 2017 w wersji 15,7 występuje błąd kompilatora.

Poniższy przykład kodu w programie Visual Studio 2017 w wersji 15,7 zgłasza *błąd C2614: D\<int >: niedozwolona Inicjalizacja elementu członkowskiego: "B" nie jest elementem bazowym ani składową*

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

Aby naprawić ten błąd, zmień wyrażenie B () na B\<T > ().

### <a name="constexpr-aggregate-initialization"></a>Inicjalizacja agregacji **constexpr**

Poprzednie wersje C++ kompilatora niepoprawnie obsługiwały inicjalizację agregacji **constexpr** ; Zaakceptowano nieprawidłowy kod, w którym element agregujący init-list ma zbyt wiele elementów i wygenerował złą codegen dla niego. Poniższy kod jest przykładem takiego kodu:

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {
        { 1, 2 },
        { 3, 4 }
    };
    return 0;
}
```

W programie Visual Studio 2017 w wersji 15,7 Update 3 i nowszych, poprzedni przykład teraz podnosi *C2078 zbyt wiele inicjatorów*. Poniższy przykład pokazuje, jak naprawić kod. Podczas inicjowania `std::array` z zagnieżdżonymi nawiasami klamrowymi-init-list, nadaj wewnętrznej tablicy listę własnych:

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {{ // note double braces
        { 1, 2 },
        { 3, 4 }
    }}; // note double braces
    return 0;
}
```

## <a name="update_158"></a>Poprawki błędów i zmiany zachowań w 15,8

Zmiany w kompilatorze w programie Visual Studio 2017 w wersji 15,8 wszystkie są objęte kategorią poprawek i zmian w zachowaniu błędów i są wymienione poniżej:

###<a name="typename-on-unqualified-identifiers"></a>wartość **TypeName** dla niekwalifikowanych identyfikatorów

W trybie [/permissive-](../build/reference/permissive-standards-conformance.md) słowa kluczowe**TypeName** fałszywe w niekwalifikowanych identyfikatorach w definicjach szablonów aliasów nie są już akceptowane przez kompilator. Poniższy kod tworzy teraz *słowo kluczowe C7511 ":" typename "musi następować kwalifikowana nazwa*:

```cpp
template <typename T>
using  X = typename T;
```

Aby naprawić ten błąd, Zmień drugi wiersz na `using  X = T;`.

### <a name="__declspec-on-right-side-of-alias-template-definitions"></a>`__declspec()` po prawej stronie definicji szablonu aliasu

[__declspec](../cpp/declspec.md) nie jest już dozwolony po prawej stronie definicji szablonu aliasu. Ten kod został poprzednio zaakceptowany, ale ignorowany przez kompilator i nigdy nie spowoduje ostrzeżenia o zaniechaniu w przypadku użycia aliasu.

W zamian C++\[atrybutu standardowego [\[przestarzałe\]\]](../cpp/attributes.md) można użyć w programie Visual Studio 2017 w wersji 15,6. Poniższy kod generuje teraz *błąd składniowy C2760: Nieoczekiwany token "__declspec", oczekiwano "specyfikatora typu*":

```cpp
template <typename T>
using X = __declspec(deprecated("msg")) T;
```

Aby naprawić ten błąd, Zmień kod na następujący (z atrybutem umieszczonym przed znakiem "=" definicji aliasu):

```cpp
template <typename T>
using  X [[deprecated("msg")]] = T;
```

### <a name="two-phase-name-lookup-diagnostics"></a>Dwufazowe Diagnostyka wyszukiwania nazw

Dwufazowe wyszukiwanie nazw wymaga, aby nazwy niezależne używane w treści szablonu musiały być widoczne dla szablonu w czasie definicji. Wcześniej kompilator firmy Microsoft C++ pozostawi nieznalezioną nazwę jako niesprawdzoną do czasu utworzenia wystąpienia. Teraz wymaga, aby nazwy niezależne były powiązane z treścią szablonu.

Jeden ze sposobów to manifest jest z wyszukiwaniem w zależnych klasach bazowych. Wcześniej kompilator zezwolił na używanie nazw, które są zdefiniowane w zależnych klasach bazowych, ponieważ będą one wyszukiwane podczas tworzenia wystąpienia po rozwiązaniu wszystkich typów. Teraz kod jest traktowany jako błąd. W takich przypadkach można wymusić wyszukanie zmiennej w czasie tworzenia wystąpienia, kwalifikując ją z typem klasy bazowej lub w inny sposób, na przykład poprzez dodanie wskaźnika `this->`.

W trybie [/permissive-](../build/reference/permissive-standards-conformance.md) następujący kod wywołuje teraz C3861: *"base_value": nie znaleziono identyfikatora*:

```cpp
template <class T>
struct Base {
    int base_value = 42;
};

template <class T>
struct S : Base<T> {
    int f() {
        return base_value;
    }
};
```

Aby naprawić ten błąd, Zmień instrukcję `return` na `return this->base_value;`.

**Uwaga:** W bibliotece ulepszania języka Python wystąpiło długotrwałe obejście MSVC dla deklaracji do przesyłania dalej szablonu w [unwind_type. HPP](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp). W trybie [/permissive-](../build/reference/permissive-standards-conformance.md) , rozpoczynając od programu Visual Studio 2017 w wersji 15,8 (_MSC_VER = 1915), kompilator MSVC wykonuje poprawną metodę wyszukiwania nazw zależnych od ARGUMENTÓW (ADL) i jest zgodna z innymi kompilatorami, co sprawia, że ta ochrona nie jest zbędna. Aby uniknąć błędu *C3861: "unwind_type": nie znaleziono identyfikatora*, zobacz [PR 229](https://github.com/boostorg/python/pull/229) w obszarze zwiększenie poziomu repozytorium, aby zaktualizować plik nagłówkowy. Pakiet [vcpkg](../build/vcpkg.md) został już poprawiony, więc jeśli uzyskasz lub uaktualnisz swoje źródła wzrostu od vcpkg, nie musisz oddzielnie stosować poprawki.

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>przekazywanie deklaracji i definicji w przestrzeni nazw `std`

C++ Standard nie zezwala użytkownikowi na dodawanie deklaracji lub definicji do przodu do przestrzeni nazw `std`. Dodawanie deklaracji lub definicji do przestrzeni nazw `std` lub do przestrzeni nazw w przestrzeni nazw `std` teraz powoduje niezdefiniowane zachowanie.

W przyszłości firma Microsoft przeniesie lokalizację, w której są zdefiniowane niektóre standardowe typy bibliotek. Ta zmiana spowoduje przerwanie istniejącego kodu, który dodaje deklaracje przesyłania dalej do przestrzeni nazw `std`. Nowe ostrzeżenie, C4643, ułatwia identyfikowanie takich problemów źródłowych. Ostrzeżenie jest włączone w trybie **/default** i jest domyślnie wyłączone. Będzie to miało wpływ na programy skompilowane za pomocą **/Wall** lub **/WX**.

Poniższy kod teraz podnosi C4643: *przekazywanie deklaracji "Vector" w przestrzeni nazw std nie jest dozwolone przez C++ Standard*.

```cpp
namespace std {
    template<typename T> class vector;
}
```

Aby naprawić ten błąd, użyj dyrektywy **include** zamiast deklaracji do przodu:

```cpp
#include <vector>
```

### <a name="constructors-that-delegate-to-themselves"></a>Konstruktory, które są delegatem do siebie

C++ Standard sugeruje, że kompilator powinien emitować diagnostykę, gdy delegat delegowany do samego siebie. Kompilator firmy C++ Microsoft w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) i [/std: c + + najnowsze](../build/reference/std-specify-language-standard-version.md) tryby teraz wywołuje C7535: *"X:: X": delegowanie wywoływanych konstruktorów*.

Bez tego błędu następujący program zostanie skompilowany, ale wygeneruje nieskończoną pętlę:

```cpp
class X {
public:
    X(int, int);
    X(int v) : X(v){}
};
```

Aby uniknąć nieskończonej pętli, delegat do innego konstruktora:

```cpp
class X {
public:

    X(int, int);
    X(int v) : X(v, 0) {}
};
```

### <a name="offsetof-with-constant-expressions"></a>`offsetof` ze stałymi wyrażeniami

[makro OffsetOf](../c-runtime-library/reference/offsetof-macro.md) tradycyjnie zaimplementowano przy użyciu makra, które wymaga [reinterpret_cast](../cpp/reinterpret-cast-operator.md). To użycie jest niedozwolone w kontekstach, które wymagają wyrażenia stałego, ale C++ kompilator firmy Microsoft jest tradycyjnie dozwolony. Makro `offsetof`, które jest dostarczane jako część biblioteki standardowej, prawidłowo używa wewnętrznego kompilatora ( **__builtin_offsetof**), ale wiele osób użyło lew makro do definiowania własnych `offsetof`.

W programie Visual Studio 2017 w wersji 15,8 kompilator ogranicza obszary, w których te operatory `reinterpret_cast` mogą być wyświetlane w trybie domyślnym, aby pomóc w kodzie zgodnym ze C++ standardowym zachowaniem. W obszarze [/permissive-](../build/reference/permissive-standards-conformance.md)ograniczenia są jeszcze bardziej rygorystyczne. Użycie wyniku `offsetof` w miejscach, w których wymagane jest wyrażenie stałe może spowodować, że wystąpiły problemy z ostrzeżeniem C4644 *użycie wzorca makro OffsetOf opartego na makrach w wyrażeniach stałych jest niestandardowa; C++ zamiast tego użyj makro OffsetOf zdefiniowanego w bibliotece standardowej* lub C2975 *nieprawidłowy argument, oczekiwano wyrażenia stałej czasu kompilacji*.

Poniższy kod wywołuje C4644 w postaci **/default** i **/std: tryby c++ 17** , a C2975 w trybie [/permissive-](../build/reference/permissive-standards-conformance.md) :

```cpp
struct Data {
    int x;
};

// Common pattern of user-defined offsetof
#define MY_OFFSET(T, m) (unsigned long long)(&(((T*)nullptr)->m))

int main()

{
    switch (0) {
    case MY_OFFSET(Data, x): return 0;
    default: return 1;
    }
}
```

Aby naprawić ten błąd, użyj `offsetof` zgodnie z definicją \<cstddef >:

```cpp
#include <cstddef>

struct Data {
    int x;
};

int main()
{
    switch (0) {
    case offsetof(Data, x): return 0;
    default: return 1;
    }
}
```

### <a name="cv-qualifiers-on-base-classes-subject-to-pack-expansion"></a>kwalifikatory OKS w klasach bazowych, które podlegają rozwinięciu pakietu

Poprzednie wersje kompilatora Microsoft C++ nie wykryły, że klasa bazowa miała kwalifikatory OKS, jeśli była również poddana rozwinięcia.

W programie Visual Studio 2017 w wersji 15,8 w trybie [/permissive-](../build/reference/permissive-standards-conformance.md) następujący kod wywołuje C3770 *"const S": nie jest prawidłową klasą bazową*:

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x;
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>słowo kluczowe **szablonu** i specyfikatory nazwy zagnieżdżonej

W trybie [/permissive-](../build/reference/permissive-standards-conformance.md) kompilator wymaga, aby słowo kluczowe **szablonu** poprzedzać nazwę szablonu, gdy jest on dostępny Po specyfikatorze zagnieżdżonej nazwy.

Następujący kod w trybie [/permissive-](../build/reference/permissive-standards-conformance.md) wywołuje teraz C7510: *"example": użycie nazwy szablonu zależnego musi być poprzedzone prefiksem "template". Uwaga: Zobacz odwołanie do skompilowanej instancji szablonu klasy "X<T>"* :

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        Base<T>::example<int>();
    }
};
```

Aby naprawić ten błąd, Dodaj słowo kluczowe **szablonu** do instrukcji `Base<T>::example<int>();`, jak pokazano w następującym przykładzie:

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        // Add template keyword here:
        Base<T>::template example<int>();
    }
};
```

## <a name="update_159"></a>Poprawki błędów i zmiany zachowań w 15,9

### <a name="identifiers-in-member-alias-templates"></a>Identyfikatory w szablonach aliasów elementów członkowskich

Identyfikator używany w definicji szablonu aliasu składowej musi być zadeklarowany przed użyciem.

W poprzednich wersjach kompilatora można było użyć następującego kodu:

```cpp
template <typename... Ts>
struct A
{
  public:
    template <typename U>
    using from_template_t = decltype(from_template(A<U>{}));

  private:
    template <template <typename...> typename Type, typename... Args>
    static constexpr A<Args...> from_template(A<Type<Args...>>);
};

A<>::from_template_t<A<int>> a;
```

W programie Visual Studio 2017 w wersji 15,9 w trybie [/permissive-](../build/reference/permissive-standards-conformance.md) kompilator podnosi wartość C3861: *' from_template ': nie znaleziono identyfikatora*.

Aby naprawić ten błąd, zadeklaruj `from_template` przed `from_template_t`.

### <a name="modules-changes"></a>Zmiany modułów

W programie Visual Studio 2017 w wersji 15,9 kompilator podnosi C5050 za każdym razem, gdy opcje wiersza polecenia modułów nie są spójne między elementami tworzenia modułu i zużycia modułu. W poniższym przykładzie występują dwa problemy:

- Na stronie użycie (Main. cpp) nie określono opcji **/EHsc** .

- C++ Wersja to **/std: c++ 17** po stronie tworzenia i **/std: c++ 14** po stronie użycie.

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

Kompilator podnosi C5050 dla obu tych przypadków: *Warning C5050: możliwe niezgodne środowisko podczas importowania modułu 'm ': niezgodne C++ wersje.  Bieżąca wersja "201402" modułu "201703"* .

Kompilator podnosi także C7536 za każdym razem, gdy plik. IFC został naruszony. Nagłówek interfejsu modułu zawiera skrót algorytmu SHA2 zawartości poniżej. Podczas importowania plik. IFC jest tworzony w taki sam sposób, a następnie sprawdzany pod kątem skrótu podanego w nagłówku. Jeśli te nie są zgodne, zgłaszany jest błąd C7536: *nie powiodło się sprawdzenie integralności przez IFC.  Oczekiwano algorytmu SHA2: "66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6"* .

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>Kolejność częściowa obejmująca aliasy i niewnioskowane konteksty

Implementacje różnią się w regułach kolejności częściowej obejmujących aliasy w kontekstach niebędących wnioskami. W poniższym przykładzie, w trakcie działania w ramach C++ programu, w programie Microsoft kompilator (w trybie [/permissive-](../build/reference/permissive-standards-conformance.md) ) wystąpi błąd, podczas gdy Clang akceptuje kod.

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <class T, class Alloc>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

Poprzedni przykład podnosi C2668:

```Output
partial_alias.cpp(32): error C2668: 'f': ambiguous call to overloaded function
partial_alias.cpp(18): note: could be 'int f<Alloc,void>(A<void> &,const AlignedBuffer<10,4> &)'
partial_alias.cpp(12): note: or       'int f<Alloc,A<void>>(Alloc &,const AlignedBuffer<10,4> &)'
        with
        [
            Alloc=A<void>
        ]
partial_alias.cpp(32): note: while trying to match the argument list '(A<void>, AlignedBuffer<10,4>)'
```

Rozbieżność implementacji jest spowodowana regresją w C++ standardowym wyrazie. Problem z rozwiązaniem Core 2235 usunął jakiś tekst, który zezwoli na porządkowanie tych przeciążeń. Bieżący C++ Standard nie zapewnia mechanizmu do częściowo uporządkowania tych funkcji, więc są uważane za niejednoznaczne.

Aby obejść ten problem, zaleca się, aby nie polegać na częściowej kolejności tego problemu. Zamiast tego należy użyć SFINAE do usunięcia konkretnych przeciążeń. W poniższym przykładzie używamy klasy pomocnika `IsA` do usuwania pierwszego przeciążenia, gdy `Alloc` jest specjalizacją `A`:

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <typename T> struct IsA : std::false_type {};
template <typename T> struct IsA<A<T>> : std::true_type {};

template <class T, class Alloc, typename = std::enable_if_t<!IsA<Alloc>::value>>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

### <a name="illegal-expressions-and-non-literal-types-in-templated-function-definitions"></a>Niedozwolone wyrażenia i typy niebędące literałami w definicjach funkcji z szablonami

Niedozwolone wyrażenia i typy niebędące literałami są teraz prawidłowo zdiagnozowane w definicjach funkcji opartych na szablonach, które są jawnie wyspecjalizowane. Wcześniej takie błędy nie były emitowane dla definicji funkcji. Jednak niedozwolone wyrażenie lub typ niebędący literałem nadal będą zdiagnozowane, jeśli zostanie obliczony jako część wyrażenia stałej.

W poprzednich wersjach programu Visual Studio następujący kod kompiluje się bez ostrzeżenia:

```cpp
void g();

template<typename T>
struct S
{
    constexpr void f();
};

template<>
constexpr void S<int>::f()
{
    g(); // C3615 in 15.9
}
```

W programie Visual Studio 2017 w wersji 15,9 kod zgłasza ten błąd:

```Output
error C3615: constexpr function 'S<int>::f' cannot result in a constant expression.
note: failure was caused by call of undefined function or one not declared 'constexpr'
note: see usage of 'g'.
```

Aby uniknąć tego błędu, Usuń kwalifikator **constexpr** z jawnego tworzenia wystąpienia funkcji `f()`.

::: moniker-end

::: moniker range="vs-2015"

## <a name="c-conformance-improvements-in-visual-studio-2015"></a>C++ulepszenia zgodności w programie Visual Studio 2015

Aby zapoznać się z pełną listą ulepszeń w programie Visual Studio 2015 Update 3, zobacz artykuł [ C++ co nowego 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Tabela C++ zgodności języka firmy Microsoft](../visual-cpp-language-conformance.md)
