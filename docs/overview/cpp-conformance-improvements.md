---
title: Ulepszenia zgodności języka C++
ms.date: 03/16/2020
description: Microsoft C++ w programie Visual Studio postępuje w kierunku pełnej zgodności ze standardem języka C++ 20.
ms.technology: cpp-language
ms.openlocfilehash: 2309e79acb4784cd2e79b4f3f6fffb29e8d5dea8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353536"
---
# <a name="c-conformance-improvements-in-visual-studio"></a>Ulepszenia zgodności języka C++ w programie Visual Studio

Microsoft C++ wprowadza ulepszenia zgodności i poprawki błędów w każdej wersji. W tym artykule wymieniono ulepszenia według wersji głównej, a następnie według wersji. Zawiera również listę głównych poprawek błędów według wersji. Aby przejść bezpośrednio do zmian dla określonej wersji, użyj **listy W tym artykule.**

::: moniker range="vs-2019"

## <a name="conformance-improvements-in-visual-studio-2019-rtw-version-160"></a><a name="improvements_160"></a>Ulepszenia zgodności w programie Visual Studio 2019 RTW (wersja 16.0)

Program Visual Studio 2019 RTW zawiera następujące ulepszenia zgodności, poprawki błędów i zmiany zachowania w kompilatorze Microsoft C++ (MSVC)

**Uwaga:** Funkcje języka C++20 `/std:c++latest` będą udostępniane w trybie do czasu ukończenia implementacji języka C++20 dla kompilatora i intellisense. W tym czasie `/std:c++20` zostanie wprowadzony tryb kompilatora.

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Ulepszone moduły obsługują szablony i wykrywanie błędów

Moduły są teraz oficjalnie w standardzie C++20. Ulepszona obsługa została dodana w programie Visual Studio 2017 w wersji 15.9. Aby uzyskać więcej informacji, zobacz [Lepsza obsługa szablonów i wykrywanie błędów w modułach C++ z MSVC 2017 w wersji 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/).

### <a name="modified-specification-of-aggregate-type"></a>Zmodyfikowana specyfikacja typu kruszywa

Specyfikacja typu agregacji uległa zmianie w języku C++20 (zobacz [Zakaz agregacje z konstruktorami zadeklarowanych przez użytkownika).](https://wg21.link/p1008r1) W programie Visual Studio 2019 w obszarze `/std:c++latest`, klasa z dowolnego konstruktora zadeklarowanego przez użytkownika (na przykład, w tym konstruktora zadeklarowane `= default` lub) `= delete`nie jest agregacji. Wcześniej tylko konstruktory dostarczone przez użytkownika dyskwalifikuje klasy z agregacji. Ta zmiana stawia dodatkowe ograniczenia dotyczące sposobu inicjowania takich typów.

Poniższy kod kompiluje bez błędów w programie Visual Studio 2017, ale zgłasza błędy C2280 `/std:c++latest`i C2440 w programie Visual Studio 2019 w obszarze:

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

### <a name="partial-support-for-operator-"></a>Częściowe wsparcie dla`operator <=>`

[P0515R3](https://wg21.link/p0515r3) C++20 wprowadza `<=>` trójdrożny operator porównania, znany również jako "operator statku kosmicznego". Visual Studio 2019 w `/std:c++latest` trybie wprowadza częściową obsługę operatora przez podnoszenie błędów dla składni, która jest teraz niedozwolona. Na przykład następujący kod kompiluje bez błędów w programie Visual Studio 2017, ale `/std:c++latest`wywołuje wiele błędów w programie Visual Studio 2019 w obszarze:

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

Aby uniknąć błędów, wstaw spację w linii naruszającej `U<&S::operator<= > u;`przed końcowym nawiasem kątowym: .

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>Odwołania do typów z niedopasowanymi kwalifikatorami cv

Wcześniej msvc dozwolone bezpośrednie powiązanie odwołania z typu z niezgodnych kwalifikatorów cv poniżej najwyższego poziomu. To powiązanie może umożliwić modyfikację rzekomo const danych, o których mowa w odwołaniu. Kompilator tworzy teraz tymczasowe, zgodnie z wymaganiami standardu. W programie Visual Studio 2017 następujący kod kompiluje się bez ostrzeżeń. W programie Visual Studio 2019 kompilator podnosi *ostrzeżenie \<C4172: func:#1 "?PData@X @@QBEABQBXXZ"> zwracany adres zmiennej lokalnej lub tymczasowej*.

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

### <a name="reinterpret_cast-from-an-overloaded-function"></a>`reinterpret_cast`z przeciążonej funkcji

Argument `reinterpret_cast` nie jest jednym z kontekstów, w których adres funkcji przeciążony jest dozwolone. Poniższy kod kompiluje się bez błędów w programie Visual Studio 2017, ale w programie Visual Studio 2019 wywołuje *C2440: nie można przekonwertować z 'overloaded-function' na 'fp':*

```cpp
int f(int) { return 1; }
int f(float) { return .1f; }
using fp = int(*)(int);

int main()
{
    fp r = reinterpret_cast<fp>(&f);
}
```

Aby uniknąć błędu, użyj dozwolonego rzutu dla tego scenariusza:

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

W języku C++14 typy zamknięcia lambda nie są literałami. Główną konsekwencją tej reguły jest to, że lambda nie może być przypisany do zmiennej **constexpr.** Poniższy kod kompiluje się bez błędów w programie Visual Studio 2017, ale w programie Visual Studio 2019 podnosi *C2127: 'l': nielegalne inicjowanie jednostki 'constexpr' z wyrażeniem nieo constant:*

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

Aby uniknąć tego błędu, usuń kwalifikator **constexpr** lub `/std:c++17`zmień tryb zgodności na .

### <a name="stdcreate_directory-failure-codes"></a>`std::create_directory`kody awarii

Zaimplementowano [P1164](https://wg21.link/p1164r1) z języka C++20 bezwarunkowo. Spowoduje `std::create_directory` to zmianę, aby sprawdzić, czy obiekt docelowy był już katalogiem awarii. Wcześniej wszystkie błędy typu ERROR_ALREADY_EXISTS zostały przekształcone w kody sukcesu, ale katalog-nietworzone.

### `operator<<(std::ostream, nullptr_t)`

Na [LWG 2221](https://cplusplus.github.io/LWG/issue2221), dodano `operator<<(std::ostream, nullptr_t)` do pisania nullptrs do strumieni.

### <a name="additional-parallel-algorithms"></a>Dodatkowe algorytmy równoległe

Nowe równoległe `is_sorted` `is_sorted_until`wersje `is_partitioned` `set_difference`, `set_intersection` `is_heap`, `is_heap_until`, , , i .

### <a name="atomic-initialization"></a>inicjalizacja atomowa

[P0883 "Naprawianie inicjowania atomowego"](https://wg21.link/p0883r1) zmienia się `std::atomic` w wartość inicjowania zawartego T, a nie inicjując go domyślnie. Poprawka jest włączona podczas korzystania z Clang/LLVM ze standardową biblioteką firmy Microsoft. Jest obecnie wyłączona dla kompilatora Microsoft C++, jako obejście problemu w **przetwarzaniu constexpr.**

### <a name="remove_cvref-and-remove_cvref_t"></a>`remove_cvref` i `remove_cvref_t`

Zaimplementowano cechy `remove_cvref` typu `remove_cvref_t` [p0550](https://wg21.link/p0550r2). Te usunąć reference-ness i cv kwalifikacji z typu bez rozkładających się `std::decay` `std::decay_t`funkcji i tablic do wskaźników (w przeciwieństwie do i ).

### <a name="feature-test-macros"></a>Makra testowe funkcji

[P0941R2 - makra testowe funkcji](https://wg21.link/p0941r2) jest `__has_cpp_attribute`kompletna, z obsługą . Makra testów funkcji są obsługiwane we wszystkich trybach standardowych.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Zabroń agregatów z konstruktorami zadeklarowanym przez użytkownika

[C++ 20 P1008R1 - zakaz agregacji z konstruktorami zadeklarowanych przez użytkownika](https://wg21.link/p1008r1) jest zakończona.

## <a name="conformance-improvements-in-161"></a><a name="improvements_161"></a>Ulepszenia zgodności w 16.1

### <a name="char8_t"></a>char8_t

[P0482r6](https://wg21.link/p0482r6). C++20 dodaje nowy typ znaku, który jest używany do reprezentowania jednostek kodu UTF-8. `u8`literały ciągów w języku C++20 mają typ `const char8_t[N]` zamiast `const char[N]`, co było wcześniej. Zaproponowano podobne zmiany dla normy C w [N2231](https://wg14.link/n2231). Sugestie `char8_t` dotyczące korygowania zgodności z powrotem podano w [P1423r3](https://wg21.link/p1423r3). Kompilator Microsoft C++ `char8_t` dodaje obsługę w programie Visual Studio 2019 w wersji 16.1 po określeniu opcji kompilatora **/Zc:char8_t.** W przyszłości będzie obsługiwany za pomocą [/std:c++latest](../build/reference/std-specify-language-standard-version.md), które można przywrócić do zachowania C++17 za pośrednictwem **/Zc:char8_t-**. Kompilator EDG, który zasila IntelliSense, jeszcze go nie obsługuje, więc zobaczysz fałszywe błędy tylko IntelliSense, które nie mają wpływu na rzeczywistą kompilację.

#### <a name="example"></a>Przykład

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtype_identity-metafunction-and-stdidentity-function-object"></a>std::type_identity metafunkcji i std::identity, obiekt funkcji

[P0887R1 type_identity](https://wg21.link/p0887r1). Przestarzałe `std::identity` rozszerzenie szablonu klasy zostało usunięte i zastąpione `std::type_identity` metafunkcji `std::identity` c++ 20 i obiekt funkcji. Oba są dostępne tylko w obszarze [/std:c++latest](../build/reference/std-specify-language-standard-version.md).

Poniższy przykład daje ostrzeżenie o wycofanie C4996 dla `std::identity` (zdefiniowane w \<type_traits>) w programie Visual Studio 2017:

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

Poniższy przykład pokazuje, jak `std::identity` używać \<nowego (zdefiniowanego w> `std::type_identity`funkcjonalnych) wraz z nowym:

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>Kontrola składni dla generycznych lambdas

Nowy procesor lambda umożliwia pewne kontrole składni w trybie zgodności w generycznych lambdas, w [obszarze /std:c++latest](../build/reference/std-specify-language-standard-version.md) lub w dowolnym innym trybie językowym z **/experimental:newLambdaProcessor**.

W programie Visual Studio 2017 ten kod kompiluje się bez ostrzeżeń, ale w programie Visual Studio 2019 generuje błąd błędu *składni C2760: nieoczekiwany token '\<id-expr>', oczekiwane "wyrażenie id":*

```cpp
void f() {
    auto a = [](auto arg) {
        decltype(arg)::Type t;
    };
}
```

Poniższy przykład przedstawia poprawną składnię, teraz wymuszane przez kompilator:

```cpp
void f() {
    auto a = [](auto arg) {
        typename decltype(arg)::Type t;
    };
}
```

### <a name="argument-dependent-lookup-for-function-calls"></a>Wyszukiwanie zależne od argumentów dla wywołań funkcji

[P0846R0](https://wg21.link/p0846r0) (C++20) Zwiększona możliwość znajdowania szablonów funkcji za pomocą wyszukiwania zależnego od argumentów dla wyrażeń wywołań funkcji z jawnymi argumentami szablonu. Wymaga **/std:c++latest**.

### <a name="designated-initialization"></a>Desygnowana inicjalizacja

[P0329R4](https://wg21.link/p0329r4) (C++20) Inicjowanie wyznaczone umożliwia wybranie określonych `Type t { .member = expr }` elementów członkowskich przy inicjacji agregacji przy użyciu składni. Wymaga **/std:c++latest**.

### <a name="new-and-updated-standard-library-functions-c20"></a>Nowe i zaktualizowane standardowe funkcje biblioteki (C++20)

- `starts_with()`oraz `ends_with()` `basic_string` dla `basic_string_view`i .
- `contains()` dla kontenerów asocjacyjnych.
- `remove()`, `remove_if()` i `unique()` dla obiektów `list` i `forward_list` zwracają teraz obiekt `size_type`.
- `shift_left()`i `shift_right()` dodane \<do> algorytmu.

## <a name="conformance-improvements-in-162"></a><a name="improvements_162"></a>Ulepszenia zgodności w 16.2

### <a name="noexcept-constexpr-functions"></a>noexcept constexpr funkcje

Funkcje Constexpr nie są już domyślnie uważane za **niez wyjątkiem,** gdy są używane w wyrażeniu stałym. Ta zmiana zachowania pochodzi z rozdzielczości [CWG 1351](https://wg21.link/cwg1351) i jest włączona w [/permissive-](../build/reference/permissive-standards-conformance.md). Poniższy przykład kompiluje w programie Visual Studio 2019 w wersji 16.1 i wcześniejszych, ale produkuje C2338 w programie Visual Studio 2019 w wersji 16.2:

```cpp
constexpr int f() { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept"); // C2338 in 16.2
}
```

Aby naprawić błąd, dodaj wyrażenie **noexcept** do deklaracji funkcji:

```cpp
constexpr int f() noexcept { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept");
}
```

### <a name="binary-expressions-with-different-enum-types"></a>Wyrażenia binarne z różnymi typami wyliczeń

Możliwość zastosowania zwykłych konwersji arytmetycznych na operandach, gdzie jeden ma typ wyliczenia, a drugi ma inny typ wyliczenia lub typ zmiennoprzecinkowy jest przestarzały w C++20 ([P1120R0](https://wg21.link/p1120r0)). W programie Visual Studio 2019 w wersji 16.2 i nowszych następujący kod generuje ostrzeżenie poziomu 4, gdy opcja [/std:c++latest](../build/reference/std-specify-language-standard-version.md) compiler jest włączona:

```cpp
enum E1 { a };
enum E2 { b };
int main() {
    int i = a | b; // warning C5054: operator '|': deprecated between enumerations of different types
}
```

Aby uniknąć ostrzeżenia, użyj [static_cast,](../cpp/static-cast-operator.md) aby przekonwertować drugi operand:

```cpp
enum E1 { a };
enum E2 { b };
int main() {
  int i = a | static_cast<int>(b);
}
```

### <a name="binary-expressions-with-enumeration-and-floating-point-types"></a>Wyrażenia binarne z wyliczeniami i typami zmiennoprzecinkowymi

Możliwość zastosowania zwykłych konwersji arytmetycznych na operandach, gdzie jeden ma typ wyliczenia, a drugi ma inny typ wyliczenia lub typ zmiennoprzecinkowy jest przestarzały w C++20 ([P1120R0](https://wg21.link/p1120r0)). Innymi słowy przy użyciu operacji binarnej między wyliczenia i typu zmiennoprzecinkowego jest teraz ostrzeżenie, gdy [/std:c++ostatni](../build/reference/std-specify-language-standard-version.md) kompilator opcja jest włączona:

```cpp
enum E1 { a };
int main() {
  double i = a * 1.1;
}
```

Aby uniknąć ostrzeżenia, użyj [static_cast,](../cpp/static-cast-operator.md) aby przekonwertować drugi operand:

```cpp
enum E1 { a };
int main() {
   double i = static_cast<int>(a) * 1.1;
}
```

### <a name="equality-and-relational-comparisons-of-arrays"></a>Równość i relacje tablic

Porównania równości i relacyjne między dwoma argumentami typu tablicy są przestarzałe w języku C++20 ([P1120R0](https://wg21.link/p1120r0)). Innymi słowy, operacja porównania między dwiema tablicami (niezależnie od podobieństw rangi i zasięgu) jest teraz ostrzeżeniem. Począwszy od programu Visual Studio 2019 w wersji 16.2, następujący kod tworzy *C5056: operator '==': przestarzałe dla typów tablic,* gdy [/std:c++ostatni](../build/reference/std-specify-language-standard-version.md) kompilator opcja jest włączona:

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (a == b) { return 1; }
}
```

Aby uniknąć ostrzeżenia, można porównać adresy pierwszych elementów:

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (&a[0] == &b[0]) { return 1; }
}
```

Aby ustalić, czy zawartość dwóch tablic jest równa, należy użyć funkcji [std::equal:](../standard-library/algorithm-functions.md#equal)

```cpp
std::equal(std::begin(a), std::end(a), std::begin(b), std::end(b));
```

### <a name="effect-of-defining-spaceship-operator-on--and-"></a>Wpływ definiowania operatora statku kosmicznego na == i !=

Sama definicja operatora statku**<=>** kosmicznego ( ) nie będzie **==** już przepisywać wyrażeń z `= default` udziałem lub **!=** chyba że operator statku kosmicznego jest oznaczony jako ([P1185R2](https://wg21.link/p1185r2)). Poniższy przykład kompiluje w programie Visual Studio 2019 RTW i wersji 16.1, ale produkuje C2678 w programie Visual Studio 2019 w wersji 16.2:

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

Aby uniknąć błędu, zdefiniuj operator== lub zadeklaruj go jako domyślnego:

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

- \<charconv> `to_chars()` ze stałą/naukową precyzją. (Ogólna precyzja jest obecnie planowana na 16.4.)
- [P0020R6](https://wg21.link/p0020r6):\<atomowy> pływakowy, atomowy\<podwójny\<>, atomowy podwójny>
- [P0463R1](https://wg21.link/p0463r1): endian
- [P0482R6](https://wg21.link/p0482r6): Obsługa bibliotek dla char8_t
- [P0600R1](https://wg21.link/p0600r1):\[[ nodiscard]] Dla STL, część 1
- [P0653R2](https://wg21.link/p0653r2): to_address()
- [P0754R2](https://wg21.link/p0754r2) \<: wersja>
- [P0771R1](https://wg21.link/p0771r1): noexcept Dla konstruktora ruchu std::function

## <a name="conformance-improvements-in-visual-studio-2019-version-163"></a><a name="improvements_163"></a>Ulepszenia zgodności w programie Visual Studio 2019 w wersji 16.3

### <a name="stream-extraction-operators-for-char-removed"></a>Operatory ekstrakcji strumienia dla znaku* usunięte

Operatory wyodrębniania strumienia dla wskaźników do znaków zostały usunięte i zastąpione przez operatory ekstrakcji dla tablicy znaków (na [P0487R1](https://wg21.link/p0487r1)). WG21 uważa usunięte przeciążenia za niebezpieczne. W trybie [/std:c++latest](../build/reference/std-specify-language-standard-version.md) poniższy przykład daje teraz *C2679: binary '>>': nie znaleziono operatora, który\*przyjmuje po prawej stronie operand typu 'char' (lub nie ma dopuszczalnej konwersji)*:

```cpp
   char x[42];
   char* p = x;
   std::cin >> std::setw(42);
   std::cin >> p;
```

Aby uniknąć błędu, należy użyć operatora ekstrakcji ze zmienną char[]:

```cpp
char x[42];
std::cin >> x;
```

### <a name="new-keywords-requires-and-concept"></a>Nowe słowa kluczowe **i** **koncepcja**

Nowe słowa kluczowe **wymaga** i **koncepcji** zostały dodane do kompilatora Microsoft C++. Jeśli spróbujesz użyć jednego z nich jako identyfikatora w trybie [/std:c++latest,](../build/reference/std-specify-language-standard-version.md) kompilator podniesie *błąd składni C2059:*.

### <a name="constructors-as-type-names-disallowed"></a>Konstruktory jako nazwy typów niedozwolone

Nazwy konstruktorów nie są już uważane za wstrzyknięte nazwy klas, gdy pojawiają się w nazwie kwalifikowanej po aliasie do specjalizacji szablonu klasy. Wcześniej zezwalało to na używanie konstruktorów jako nazwy typu do deklarowania innych jednostek. Poniższy przykład teraz tworzy *C3646: "TotalDuration": nieznany specyfikator zastępowania:*

```cpp
#include <chrono>

class Foo {
   std::chrono::milliseconds::duration TotalDuration{};
};

```

Aby uniknąć błędu, `TotalDuration` należy zadeklarować, jak pokazano poniżej:

```cpp
#include <chrono>

class Foo {
  std::chrono::milliseconds TotalDuration {};
};
```

### <a name="stricter-checking-of-extern-c-functions"></a>Bardziej rygorystyczne sprawdzanie funkcji extern "C"

Jeśli **funkcja extern "C"** została zadeklarowana w różnych przestrzeniach nazw, poprzednie wersje kompilatora Microsoft C++ nie sprawdziły, czy deklaracje były zgodne. W programie Visual Studio 2019 w wersji 16.3 kompilator wykonuje takie sprawdzanie. W [trybie /permissive-](../build/reference/permissive-standards-conformance.md) następujący kod tworzy *C2371 : redefinition; różne typy podstawowe* i *C2733 nie można przeciążyć funkcji z funkcją C:*

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

Aby uniknąć błędów w poprzednim przykładzie, należy użyć **bool** zamiast **BOOL** konsekwentnie w obu deklaracjach `f`.

### <a name="standard-library-improvements"></a>Ulepszenia biblioteki standardowej

Niestandardowe \<nagłówki stdexcpt.h> i \<typeinfo.h> zostały usunięte. Kod, który je zawiera, powinien \<zawierać odpowiednio wyjątek \<standardowych nagłówków> i> typeinfo.

## <a name="conformance-improvements-in-visual-studio-2019-version-164"></a><a name="improvements_164"></a>Ulepszenia zgodności w programie Visual Studio 2019 w wersji 16.4

### <a name="better-enforcement-of-two-phase-name-lookup-for-qualified-ids-in-permissive-"></a>Lepsze wymuszanie dwufazowego wyszukiwania nazw kwalifikowanych identyfikatorów w /permisyw-

Wyszukiwanie nazw dwufazowych wymaga, aby nazwy niesie zależne używane w treściach szablonów były widoczne dla szablonu w czasie definicji. Wcześniej takie nazwy mogły zostać znalezione podczas tworzenia wystąpienia szablonu. Ta zmiana ułatwia pisanie przenośnego kodu zgodnego w MSVC pod [/permissive-](../build/reference/permissive-standards-conformance.md) flaga.

W programie Visual Studio 2019 w wersji 16.4 z ustawioną flagą **/permissive,** poniższy przykład powoduje błąd, ponieważ `N::f` nie jest widoczny, gdy `f<T>` szablon jest zdefiniowany:

```cpp
template <class T>
int f() {
    return N::f() + T{}; // error C2039: 'f': is not a member of 'N'
}

namespace N {
    int f() { return 42; }
}
```

Zazwyczaj można to naprawić, dołączając brakujące nagłówki lub funkcje lub zmienne do przodu, jak pokazano w poniższym przykładzie:

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

### <a name="implicit-conversion-of-integral-constant-expressions-to-null-pointer"></a>Niejawna konwersja wyrażeń stałych integralnych do wskaźnika null

Kompilator MSVC implementuje teraz [CWG Issue 903](https://wg21.link/cwg903) w trybie zgodności (/permisywne-). Ta reguła nie zezwala na niejawną konwersję wyrażeń stałej (z wyjątkiem liczby całkowitej literału "0") do stałych wskaźnika null. Poniższy przykład tworzy C2440 w trybie zgodności:

```cpp
int* f(bool* p) {
    p = false; // error C2440: '=': cannot convert from 'bool' to 'bool *'
    p = 0; // OK
    return false; // error C2440: 'return': cannot convert from 'bool' to 'int *'
}
```

Aby naprawić błąd, należy użyć **nullptr** zamiast **false**. Należy pamiętać, że literał 0 jest nadal dozwolony:

```cpp
int* f(bool* p) {
    p = nullptr; // OK
    p = 0; // OK
    return nullptr; // OK
}
```

### <a name="standard-rules-for-types-of-integer-literals"></a>Standardowe reguły dla typów literałów całkowitych

W trybie zgodności (włączonym przez [/permissive-](../build/reference/permissive-standards-conformance.md)), MSVC używa standardowych reguł dla typów literałów liczby całkowitej. Wcześniej literały dziesiętne zbyt duże, aby zmieścić się w podpisanej "int" zostały podane typu "unsigned int". Teraz takie literały są podane następny największy typ liczby całkowitej podpisane, "długi długi". Ponadto literały z przyrostkiem "ll", które są zbyt duże, aby zmieścić się w typie podpisanym, są podane jako "unsigned long long".

Może to prowadzić do generowania różnych diagnostyki ostrzeżenie i różnice w zachowaniu dla operacji arytmetycznych wykonywanych na literały.

W poniższym przykładzie przedstawiono nowe zachowanie w programie Visual Studio 2019 w wersji 16.4. Zmienna `i` jest typu **unsigned int** i dlatego ostrzeżenie jest wywoływane. Bity wysokiego rzędu zmiennej `j` są ustawione na 0.

```cpp
void f(int r) {
    int i = 2964557531; // warning C4309: truncation of constant value
    long long j = 0x8000000000000000ll >> r; // literal is now unsigned, shift will fill high-order bits with 0
}
```

W poniższym przykładzie pokazano, jak zachować stare zachowanie, a tym samym uniknąć ostrzeżenia i zmiany zachowania w czasie wykonywania:

```cpp
void f(int r) {
int i = 2964557531u; // OK
long long j = (long long)0x8000000000000000ll >> r; // shift will keep high-order bits
}
```

### <a name="function-parameters-that-shadow-template-parameters"></a>Parametry funkcji, które w tle parametry szablonu

Kompilator MSVC teraz generuje błąd, gdy parametr funkcji cienie parametr szablonu:

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T(&buffer)[Size], int& Size) // error C7576: declaration of 'Size' shadows a template parameter
{
    return f(buffer, Size, Size);
}
```

Aby naprawić błąd, zmień nazwę jednego z parametrów:

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T (&buffer)[Size], int& size_read)
{
    return f(buffer, Size, size_read);
}
```

### <a name="user-provided-specializations-of-type-traits"></a>Specjalizacje typu dostarczane przez użytkownika

Zgodnie z *meta.rqmts* podklawa standardu kompilator MSVC teraz generuje błąd, gdy napotka specjalizacji `type_traits` zdefiniowane `std` przez użytkownika jednego z określonych szablonów w obszarze nazw. O ile nie określono inaczej, takie specjalizacje powodują niezdefiniowane zachowanie. Poniższy przykład ma niezdefiniowane zachowanie, ponieważ `static_assert` narusza regułę, a kończy się niepowodzeniem z błędem **C2338**.

```cpp
#include <type_traits>
struct S;

template<>
struct std::is_fundamental<S> : std::true_type {};

static_assert(std::is_fundamental<S>::value, "fail");
```

Aby uniknąć błędu, należy zdefiniować strukturę, `type_trait`która dziedziczy z preferowanego i specjalizować się, że:

```cpp
#include <type_traits>

struct S;

template<typename T>
struct my_is_fundamental : std::is_fundamental<T> {};

template<>
struct my_is_fundamental<S> : std::true_type { };

static_assert(my_is_fundamental<S>::value, "fail");
```

### <a name="changes-to-compiler-provided-comparison-operators"></a>Zmiany w operatorach porównawczych dostarczonych przez kompilator

Kompilator MSVC implementuje teraz następujące zmiany operatorów porównania na [P1630R1,](https://wg21.link/p1630r1) gdy opcja [/std:c++latest](../build/reference/std-specify-language-standard-version.md) jest włączona:

Kompilator nie przepisuje już `operator==` wyrażeń przy użyciu, jeśli dotyczą one typu zwracanego, który nie jest **bool**. Poniższy kod generuje teraz *błąd C2088: '!=': default for struct:*

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

Aby uniknąć błędu, należy jawnie zdefiniować potrzebny operator:

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

Kompilator nie definiuje już domyślnego operatora porównania, jeśli jest członkiem klasy podobnej do unii. Poniższy przykład teraz produkuje *C2120: "void" nielegalne ze wszystkimi typami:*

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

Aby uniknąć błędu, należy zdefiniować obiekt dla operatora:

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

Kompilator nie będzie już definiować domyślnego operatora porównania, jeśli klasa zawiera element członkowski odwołania. Poniższy kod generuje teraz *błąd C2120: "void" nielegalne ze wszystkimi typami:*

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

Aby uniknąć błędu, należy zdefiniować obiekt dla operatora:

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

## <a name="conformance-improvements-in-visual-studio-2019-version-165"></a><a name="improvements_165"></a>Ulepszenia zgodności w programie Visual Studio 2019 w wersji 16.5

### <a name="explicit-specialization-declaration-without-an-initializer-is-not-a-definition"></a>Jawna deklaracja specjalizacji bez inicjatora nie jest definicją

W `/permissive-`obszarze MSVC wymusza teraz standardową regułę, zgodnie z którą jawne deklaracje specjalizacji bez inicjatorów nie są definicjami. Wcześniej deklaracja będzie uważana za definicję z domyślnym inicjatorem. Efekt jest zauważalny w czasie łącza, ponieważ program w zależności od tego zachowania może teraz mieć nierozwiązane symbole. W tym przykładzie teraz powoduje błąd:

```cpp
template <typename> struct S {
    static int a;
};

// In permissive-, this declaration is not a definition and the program will not link.
template <> int S<char>::a;

int main() {
    return S<char>::a;
}
```

```Output
error LNK2019: unresolved external symbol "public: static int S<char>::a" (?a@?$S@D@@2HA) referenced in function _main
at link time.
```

Aby rozwiązać ten problem, dodaj inicjatora:

```cpp
template <typename> struct S {
    static int a;
};

// Add an initializer for the declaration to be a definition.
template <> int S<char>::a{};

int main() {
    return S<char>::a;
}
```

### <a name="preprocessor-output-preserves-newlines"></a>Wyjście preprocesora zachowuje nowe linie

Preprocesor eksperymentalny zachowuje teraz nowe linie i `/P` odstępy podczas używania lub `/E` z `/experimental:preprocessor`. Tę zmianę można wyłączyć `/d1experimental:preprocessor:oldWhitespace`za pomocą programu .

Biorąc pod uwagę przykładowe źródło,

```cpp
#define m()
line m(
) line
```

Poprzednie wyniki `/E` to:

```Output
line line
#line 2
```

Nowe wyjście `/E` jest teraz:

```Output
line
 line
```

### <a name="import-and-module-keywords-are-context-dependent"></a>Słowa kluczowe "import" i "moduł" są zależne od kontekstu

Na P1857R1, import i moduł preprocesor dyrektyw mają dodatkowe ograniczenia dotyczące ich składni. W tym przykładzie nie jest już kompilowany:

```cpp
import // Invalid
m;
```

Generuje następujący komunikat o błędzie:

```Output
error C2146: syntax error: missing ';' before identifier 'm'
```

Aby rozwiązać ten problem, należy zachować import w tym samym wierszu:

```cpp
import m; // OK
```

### <a name="removal-of-stdweak_equality-and-stdstrong_equality"></a>Usuwanie std::weak_equality i std::strong_equality

Scalanie P1959R0 wymaga kompilatora, aby usunąć `std::weak_equality` `std::strong_equality` zachowanie i odwołania do i typów.

Kod w tym przykładzie nie jest już kompilowany:

```cpp
#include <compare>

struct S {
    std::strong_equality operator<=>(const S&) const = default;
};

void f() {
    nullptr<=>nullptr;
    &f <=> &f;
    &S::operator<=> <=> &S::operator<=>;
}
```

Przykład teraz prowadzi do tych błędów:

```Output
error C2039: 'strong_equality': is not a member of 'std'
error C2143: syntax error: missing ';' before '<=>'
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C7546: binary operator '<=>': unsupported operand types 'nullptr' and 'nullptr'
error C7546: binary operator '<=>': unsupported operand types 'void (__cdecl *)(void)' and 'void (__cdecl *)(void)'
error C7546: binary operator '<=>': unsupported operand types 'int (__thiscall S::* )(const S &) const' and 'int (__thiscall S::* )(const S &) const'
```

Aby rozwiązać ten problem, zaktualizuj, aby preferować wbudowane operatory relacyjne i zastąpić usunięte typy:

```cpp
#include <compare>

struct S {
    std::strong_ordering operator<=>(const S&) const = default; // prefer 'std::strong_ordering'
};

void f() {
    nullptr != nullptr; // use pre-existing builtin operator != or ==.
    &f != &f;
    &S::operator<=> != &S::operator<=>;
}
```

### <a name="tls-guard-changes"></a>Zmiany w gwardii TLS

Wcześniej zmienne lokalne wątku w bibliotekach DLL nie zostały poprawnie zainicjowane przed ich pierwszym użyciem w wątkach, które istniały przed załadowaniem biblioteki DLL, inne niż wątek, który załadował bibliotekę DLL. Ta wada została naprawiona.
Zmienne lokalne wątku w takiej biblioteki DLL są inicjowane bezpośrednio przed ich pierwszym użyciem w takich wątkach.

To nowe zachowanie testowania inicjowania przy użyciu zmiennych lokalnych `/Zc:tlsGuards-` wątków może zostać wyłączone przy użyciu przełącznika kompilatora. Lub, dodając `[[msvc:no_tls_guard]]` atrybut do określonych zmiennych lokalnych wątku.

### <a name="better-diagnosis-of-call-to-deleted-functions"></a>Lepsza diagnoza połączenia z usuniętymi funkcjami

Nasz kompilator był bardziej dopuszczalne o wywołania usuniętych funkcji wcześniej. Na przykład jeśli wywołania miały miejsce w kontekście treści szablonu, nie zdiagnozowalibyśmy wywołania. Ponadto jeśli było wiele wystąpień wywołań usuniętych funkcji, firma We będzie tylko problem jednej diagnostyki. Teraz wydajemy diagnostykę dla każdego z nich.

Jedną z konsekwencji nowego zachowania może spowodować małą zmianę podziału: Kod, który nazywa się usuniętą funkcję nie zostanie zdiagnozowany, jeśli nigdy nie był potrzebny do generowania kodu. Teraz diagnozujemy to z góry.

W tym przykładzie pokazano kod, który teraz generuje błąd:

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s{};
};

U u{ 0 };
```

```Output
error C2280: 'S::S(void)': attempting to reference a deleted function
note: see declaration of 'S::S'
note: 'S::S(void)': function was explicitly deleted
```

Aby rozwiązać ten problem, usuń połączenia z usuniętymi funkcjami:

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s;  // Do not call the deleted ctor of 'S'.
};

U u{ 0 };
```

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019"></a><a name="update_160"></a>Poprawki błędów i zmiany w zachowaniu w programie Visual Studio 2019

### <a name="reinterpret_cast-in-a-constexpr-function"></a>Reinterpret_cast w funkcji constexpr

**Reinterpret_cast** jest niezgodny z prawem w funkcji **constexpr.** Kompilator Microsoft C++ wcześniej **odrzucał reinterpret_cast** tylko wtedy, gdy był używany w kontekście **constexpr.** W programie Visual Studio 2019 we wszystkich trybach standardów języka kompilator poprawnie diagnozuje **reinterpret_cast** w definicji funkcji **constexpr.** Poniższy kod tworzy teraz *C3615: constexpr funkcja "f" nie może spowodować wyrażenia stałego*.

```cpp
long long i = 0;
constexpr void f() {
    int* a = reinterpret_cast<int*>(i);
}
```

Aby uniknąć błędu, usuń **modyfikator constexpr** z deklaracji funkcji.

### <a name="correct-diagnostics-for-basic_string-range-constructor"></a>Prawidłowa diagnostyka konstruktora basic_string zakresu

W programie Visual Studio 2019 konstruktor `basic_string` zakresu nie `static_cast`pomija już diagnostyki kompilatora za pomocą programu . Poniższy kod kompiluje bez ostrzeżeń w programie Visual Studio 2017, pomimo możliwej utraty danych z `wchar_t` do **char** podczas inicjowania: `out`

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Visual Studio 2019 poprawnie podnosi *C4244: "argument": konwersja z 'wchar_t' na 'const _Elem', możliwa utrata danych*. Aby uniknąć ostrzeżenia, można zainicjować std::string, jak pokazano w tym przykładzie:

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>Nieprawidłowe wywołania += i -= w obszarze /clr lub /ZW są teraz poprawnie wykrywane

W programie Visual Studio 2017 wprowadzono błąd, który powodował, że kompilator dyskretnie ignorował `/clr` błędy `/ZW`i nie wygenerował kodu dla nieprawidłowych wywołań += i -= w obszarze lub . Poniższy kod kompiluje się bez błędów w programie Visual Studio 2017, ale w programie Visual Studio 2019 poprawnie wywołuje *błąd C2845: "System::String ^": wskaźnik arytmetyczny nie jest dozwolony dla tego typu:*

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

Aby uniknąć błędu w tym przykładzie, należy użyć operatora `s += E::e.ToString();`z ToString() metoda: .

### <a name="initializers-for-inline-static-data-members"></a>Inicjatory wbudowanych elementów członkowskich danych statycznych

Nieprawidłowy element członkowski uzyskuje dostęp w ramach **inline** i **statyczne constexpr** inicjatorów są teraz poprawnie wykryte. Poniższy przykład kompiluje bez błędu w programie Visual Studio 2017, ale w programie Visual Studio 2019 w `/std:c++17` trybie wywołuje błąd *C2248: nie można uzyskać dostępu do prywatnego elementu członkowskiego zadeklarowane w klasie "X"*.

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

Aby uniknąć błędu, należy `X::c` zadeklarować element członkowski jako chroniony:

```cpp
struct X
{
    protected:
        static inline const int c = 1000;
};
```

### <a name="c4800-reinstated"></a>C4800 przywrócony

MSVC używane do ostrzeżenia o wydajności C4800 o niejawnej konwersji do **bool**. Było zbyt głośno i nie można było go pominąć, co doprowadziło nas do usunięcia go w programie Visual Studio 2017. Jednak w całym cyklu życia programu Visual Studio 2017 otrzymaliśmy wiele opinii na temat przydatnych przypadków, które rozwiązywał. Przywracamy w programie Visual Studio 2019 starannie dostosowany C4800 wraz z objaśniającym C4165. Oba te ostrzeżenia można łatwo pominąć za pomocą jawnego rzutowanie lub porównania do 0 odpowiedniego typu. C4800 jest domyślnym ostrzeżeniem poziomu 4, a C4165 jest domyślnym ostrzeżeniem poziomu 3. Oba są wykrywalne `/Wall` przy użyciu opcji kompilatora.

Poniższy przykład podnosi C4800 i C4165 w: `/Wall`

```cpp
bool test(IUnknown* p)
{
    bool valid = p; // warning C4800: Implicit conversion from 'IUnknown*' to bool. Possible information loss
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return hr; // warning C4165: 'HRESULT' is being converted to 'bool'; are you sure this is what you want?
}
```

Aby uniknąć ostrzeżeń w poprzednim przykładzie, można napisać kod w ten sposób:

```cpp
bool test(IUnknown* p)
{
    bool valid = p != nullptr; // OK
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return SUCCEEDED(hr);  // OK
}
```

### <a name="local-class-member-function-doesnt-have-a-body"></a>Funkcja elementu członkowskiego klasy lokalnej nie ma treści

W programie Visual Studio 2017 *C4822: Funkcja elementu członkowskiego klasy lokalnej* nie `/w14822` ma treści jest wywoływana tylko wtedy, gdy opcja kompilatora jest jawnie ustawiona; nie jest wyświetlany `/Wall`z . W programie Visual Studio 2019 C4822 jest ostrzeżeniem domyślnym, `/Wall` które umożliwia `/w14822` wykrycie w obszarze bez konieczności jawnego ustawiania.

```cpp
void example()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>Obiekty szablonu funkcji zawierające constexpr if instrukcje

Jednostki funkcji szablonu **zawierające, jeśli constexpr** instrukcje mają pewne [/permissive-](../build/reference/permissive-standards-conformance.md) analizowanie związane z kontroli włączone. Na przykład w programie Visual Studio 2017 następujący kod tworzy *C7510: "Typ": użycie nazwy typu zależnego musi być poprzedzone "typename"* tylko wtedy, gdy opcja **/permissive-** nie jest ustawiona. W programie Visual Studio 2019 ten sam kod powoduje błędy nawet wtedy, gdy ustawiona jest opcja **/permissive-:**

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

Aby uniknąć błędu, dodaj słowo kluczowe nazwa `a`type `typename T::Type a;`**do** deklaracji : .

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>Wbudowany kod zestawu nie jest obsługiwany w wyrażeniu lambda

Zespół Microsoft C++ został niedawno poinformowany o problemie z zabezpieczeniami, w którym użycie wbudowanego asemblera w lambda może prowadzić do uszkodzenia (rejestru adresów zwrotnych) `ebp` w czasie wykonywania. Złośliwy atakujący może ewentualnie skorzystać z tego scenariusza. Biorąc pod uwagę charakter problemu, fakt, że wbudowany asembler jest obsługiwany tylko na x86, a słaba interakcja między wbudowanym asemblera i resztą kompilatora, najbezpieczniejszym rozwiązaniem tego problemu było niezezwolnienie wbudowanego asemblera w wyrażeniu lambda.

Jedynym użyciem wbudowanego asemblera w wyrażeniu lambda, które znaleźliśmy "na wolności", było uchwycenie adresu zwrotnego. W tym scenariuszu można przechwycić adres zwrotny na wszystkich `_ReturnAddress()`platformach po prostu przy użyciu kompilatora wewnętrznego .

Poniższy kod tworzy *C7552: wbudowany asemblera nie jest obsługiwany w lambda* w programie Visual Studio 2017 15.9 i visual studio 2019:

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

Aby uniknąć błędu, przenieś kod zestawu do nazwanej funkcji, jak pokazano w poniższym przykładzie:

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

### <a name="iterator-debugging-and-stdmove_iterator"></a>Debugowanie iteratora i`std::move_iterator`

Funkcja debugowania iteratora została nauczona prawidłowego `std::move_iterator`rozpakowania . Na przykład, `std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` może `memcpy` teraz zaangażować szybką ścieżkę.

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Poprawki do \<xkeycheck.h> wymuszania słów kluczowych

Makro biblioteki standardowej zastępujące \<xkeycheck.h wymuszania słów kluczowych> zostało naprawione w celu emisji wykrytego słowa kluczowego rzeczywistego problemu, a nie ogólnego komunikatu. Obsługuje również słowa kluczowe C++20 i pozwala uniknąć oszukiwania IntelliSense na mówienie, że losowe słowa kluczowe są makrami.

### <a name="allocator-types-no-longer-deprecated"></a>Typy alokatorów nie są już przestarzałe

`std::allocator<void>`, `std::allocator::size_type`i `std::allocator::difference_type` nie są już przestarzałe.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Prawidłowe ostrzeżenie dotyczące zawężania konwersji ciągów

Fałszywy `static_cast` nie wezwał przez standard, który przypadkowo tłumione C4244 `std::string`zwężenie ostrzeżenia został usunięty z . Próba wywołania `std::string::string(const wchar_t*, const wchar_t*)` będzie teraz poprawnie emitować *C4244 "zwężenie wchar_t do char."*

### <a name="various-filesystem-correctness-fixes"></a>Różne \<poprawki poprawności systemu plików>

- Naprawiono `std::filesystem::last_write_time` błąd podczas próby zmiany ostatniego czasu zapisu katalogu.
- Konstruktor `std::filesystem::directory_entry` przechowuje teraz wynik nie powiodło się, zamiast zgłaszania wyjątku, po podaniu nieistniejącej ścieżki docelowej.
- Wersja `std::filesystem::create_directory` 2-parametr została zmieniona, aby wywołać wersję `CreateDirectoryExW` 1-parametr, jak podstawowa funkcja będzie używać, `copy_symlink` gdy `existing_p` był dowiązanie symboliczne.
- `std::filesystem::directory_iterator`nie kończy się niepowodzeniem po znalezieniu uszkodzonego dowiązania symbolicznego.
- `std::filesystem::space`teraz akceptuje ścieżki względne.
- `std::filesystem::path::lexically_relative`nie jest już mylony przez końcowe ukośniki, zgłoszone jako [LWG 3096](https://cplusplus.github.io/LWG/issue3096).
- Obejść `CreateSymbolicLinkW` odrzucanie ścieżek z ukośnikami do przodu w `std::filesystem::create_symlink`.
- Obejść posix funkcja trybu `delete` usuwania istniejących w systemie Windows 10 LTSB 1609, ale w rzeczywistości nie jest w stanie usunąć pliki.
- `std::boyer_moore_searcher`i `std::boyer_moore_horspool_searcher`'s konstruktorów kopii i operatorów przypisania kopii teraz rzeczywiście skopiować rzeczy.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Algorytmy równoległe w systemie Windows 8 i nowszych

Biblioteka algorytmów równoległych teraz poprawnie `WaitOnAddress` używa prawdziwej rodziny w systemie Windows 8 i nowszych, zamiast zawsze używać systemu Windows 7 i wcześniejszych fałszywych wersji.

### <a name="stdsystem_categorymessage-whitespace"></a>`std::system_category::message()`Odstępu

`std::system_category::message()`teraz przycina końcowe odstępy z zwróconej wiadomości.

### <a name="stdlinear_congruential_engine-divide-by-zero"></a>`std::linear_congruential_engine`dzielenie przez zero

Niektóre warunki, `std::linear_congruential_engine` które mogłyby spowodować wywołanie podziału przez 0 zostały ustalone.

### <a name="fixes-for-iterator-unwrapping"></a>Poprawki dotyczące rozpakowywania iteratora

Iterator rozpakowywania maszyn, który został po raz pierwszy narażony na integrację programista-użytkownik w programie Visual Studio 2017 15.8, zgodnie z opisem w języku C++ Team Blog artykułu [Funkcje i poprawki STL w vs 2017 15.8](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/), nie odwija iteratory pochodzące ze standardowych iteratorów biblioteki. Na przykład użytkownik, który `std::vector<int>::iterator` wywodzi się z i próbuje dostosować zachowanie teraz pobiera ich niestandardowe zachowanie podczas wywoływania standardowych algorytmów biblioteki, a nie zachowanie wskaźnika.

Funkcja nieurządzony `reserve` kontener teraz faktycznie rezerwuje dla elementów N, jak opisano w [LWG 2156](https://cplusplus.github.io/LWG/issue2156).

### <a name="time-handling"></a>Obsługa czasu

- Wcześniej niektóre wartości czasu, które zostały przekazane do biblioteki współbieżności `condition_variable::wait_for(seconds::max())`przepełnienia, na przykład . Teraz naprawione, przepełnienia zmienił zachowanie w cyklu pozornie losowe 29-dniowy (gdy uint32_t milisekundy akceptowane przez podstawowych interfejsów API Win32 przepełnione).

- Nagłówek \<> ctime teraz poprawnie deklaruje `timespec` `timespec_get` i w `std` obszarze nazw oprócz deklarowania ich w globalnej przestrzeni nazw.

### <a name="various-fixes-for-containers"></a>Różne poprawki dla kontenerów

- Wiele standardowych funkcji kontenera wewnętrznego biblioteki zostało prywatnych dla lepszego środowiska IntelliSense. Dodatkowe poprawki do oznaczania elementów członkowskich jako prywatnych są oczekiwane w późniejszych wersjach MSVC.

- Problemy z poprawnością bezpieczeństwa wyjątków, `map`w `unordered_map` których kontenery oparte na węzłach, takie jak `list`, i zostaną uszkodzone, zostały naprawione. Podczas `propagate_on_container_copy_assignment` operacji `propagate_on_container_move_assignment` zmiany przypisania lub ponownego przypisania, możemy zwolnić węzła wartownika kontenera ze starym alokatora, wykonaj przypisanie POCCA/POCMA za pomocą starego alokatora, a następnie spróbuj uzyskać węzeł wartownika z nowego alokatora. Jeśli ta alokacja nie powiodła się, kontener został uszkodzony i nie można nawet zniszczyć, ponieważ posiadanie węzła wartownika jest niezmienną strukturą danych twardych. Ten kod został ustalony, aby przydzielić nowy węzeł wartownika z alokatora kontenera źródłowego przed zniszczeniem istniejącego węzła wartownika.

- Kontenery zostały ustalone, aby `propagate_on_container_copy_assignment`zawsze kopiować/przenosić/wymieniać alokatory zgodnie z , `propagate_on_container_move_assignment`i `propagate_on_container_swap`, nawet dla zadeklarowanych `is_always_equal`alokatorów.

- Dodano przeciążenia dla funkcji scalania i wyodrębniania kontenerów, które akceptują kontenery rvalue na [P0083 "Splicing Mapy i zestawy"](https://wg21.link/p0083r3)

### <a name="stdbasic_istreamread-processing-of-rn--n"></a>`std::basic_istream::read`przetwarzanie \\r\\n = \\> n

`std::basic_istream::read`nie zapisuj tymczasowo w części dostarczonego buforu jako część \\przetwarzania r\\n => \\n. Ta zmiana rezygnuje z niektórych korzyści wydajności, który został uzyskany w programie Visual Studio 2017 15.8 dla odczytów większych niż 4K w rozmiarze. Jednak ulepszenia wydajności z unikania trzech wywołań wirtualnych na znak są nadal obecne.

### <a name="stdbitset-constructor"></a>`std::bitset`Konstruktor

Konstruktor `std::bitset` nie odczytuje już jedynek i zer w odwrotnej kolejności dla dużych bitsetów.

### <a name="stdpairoperator-regression"></a>`std::pair::operator=`Regresji

Naprawiono regresję w `std::pair`'s operatora przypisania wprowadzone podczas wdrażania [LWG 2729 "Brak SFINAE na std::pair::operator=";](https://cplusplus.github.io/LWG/issue2729). Teraz poprawnie akceptuje typy `std::pair` convertible ponownie.

### <a name="non-deduced-contexts-for-add_const_t"></a>Nie wydedukowane konteksty dla`add_const_t`

Naprawiono błąd cech typu pomocniczego, w którym `add_const_t` i powiązane funkcje mają być kontekstem niewyuczionym. Innymi słowy, `add_const_t` powinien być aliasem dla `typename add_const<T>::type`, nie `const T`.

## <a name="bug-fixes-and-behavior-changes-in-162"></a><a name="update_162"></a>Poprawki błędów i zmiany zachowania w 16.2

### <a name="const-comparators-for-associative-containers"></a>Komparatory konspiracyjne do pojemników zespolonych

Kod wyszukiwania i wstawiania w [zestawie,](../standard-library/set-class.md) [mapa](../standard-library/map-class.md), [multiset](../standard-library/multiset-class.md)i [multimap](../standard-library/multimap-class.md) został scalony dla zmniejszonego rozmiaru kodu. Operacje wstawiania teraz wywołać mniej niż porównania na **const** porównania functor, w taki sam sposób, że operacje wyszukiwania zostały wykonane wcześniej. Poniższy kod kompiluje się w programie Visual Studio 2019 w wersji 16.1 i wcześniejszych, ale wywołuje C3848 w programie Visual Studio 2019 w wersji 16.2:

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

Aby uniknąć błędu, należy wykonać **const**operatora porównania:

```cpp
struct Comparer  {
   bool operator() (K a, K b) const {
      return a.a < b.a;
   }
};

```

::: moniker-end

::: moniker range="vs-2017"

## <a name="conformance-improvements-in-visual-studio-2017-rtw-version-150"></a><a name="improvements_150"></a>Ulepszenia zgodności w programie Visual Studio 2017 RTW (wersja 15.0)

Dzięki obsłudze uogólnionych **constexpr** i inicjowania elementu członkowskiego danych niestatycznych (NSDMI) dla agregatów kompilator Microsoft C++ w programie Visual Studio 2017 został ukończony dla funkcji dodanych w standardzie C++14. Jednak kompilator nadal brakuje kilku funkcji ze standardów C++11 i C++98. Zobacz [tabelę zgodności języka Języka Microsoft C++](../visual-cpp-language-conformance.md) dla tabeli, która pokazuje bieżący stan kompilatora.

### <a name="c11-expression-sfinae-support-in-more-libraries"></a>C++11: Obsługa wyrażenia SFINAE w większej liczbie bibliotek

Kompilator w dalszym ciągu poprawić swoją obsługę wyrażenia SFINAE, który jest wymagany do dedukcji argument szablonu i podstawienia, gdzie **wyrażenia decltype** i **constexpr** mogą być wyświetlane jako parametry szablonu. Aby uzyskać więcej informacji, zobacz [ulepszenia wyrażenia SFINAE w programie Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3).

### <a name="c14-nsdmi-for-aggregates"></a>C++14: NSDMI dla agregatów

Agregacja jest tablicą lub klasą bez konstruktora dostarczonego przez użytkownika, bez prywatnych lub chronionych elementów członkowskich danych niestatycznych, bez klas podstawowych i bez funkcji wirtualnych. Począwszy od C+ + 14 agregatów może zawierać inicjatorów elementu członkowskiego. Aby uzyskać więcej informacji, zobacz [inicjatory i agregaty członkowskie](https://wg21.link/n3605).

### <a name="c14-extended-constexpr"></a>C++14: **Rozszerzone constexpr**

Wyrażenia zadeklarowane jako **constexpr** mogą teraz zawierać pewne rodzaje deklaracji, if i switch instrukcji, instrukcji pętli i mutacji obiektów, których okres istnienia rozpoczął się w ramach oceny wyrażenia constexpr. Ponadto nie ma już wymogu, że **constexpr** niestatyczne funkcji elementu członkowskiego musi być niejawnie **const**. Aby uzyskać więcej informacji, zobacz [Rozluźnianie ograniczeń funkcji constexpr](https://wg21.link/n3652).

### <a name="c17-terse-static_assert"></a>C++17: Terse`static_assert`

parametr message `static_assert` for jest opcjonalny. Aby uzyskać więcej informacji, zobacz [Rozszerzanie static_assert, wersja 2](https://wg21.link/n3928).

### <a name="c17-fallthrough-attribute"></a>C++17: `[[fallthrough]]` atrybut

W **trybie /std:c++17** `[[fallthrough]]` atrybut może być używany w kontekście instrukcji switch jako wskazówka do kompilatora, że zachowanie fall-through jest przeznaczony. Ten atrybut uniemożliwia kompilatorowi wydawanie ostrzeżeń w takich przypadkach. Aby uzyskać więcej informacji, zobacz [Sformułowanie dla \[ \[atrybutu fallthrough\] \] ](https://wg21.link/p0188r0).

### <a name="generalized-range-based-for-loops"></a>Uogólnione pętle oparte na zakresie

Oparte na zakresie dla pętli `begin()` nie `end()` wymagają już tego i zwracają obiekty tego samego typu. Ta zmiana `end()` umożliwia zwrócenie wartownika używanego przez zakresy w [zakresie v3](https://github.com/ericniebler/range-v3) i ukończoną specyfikację techniczną zakresów, ale nie do końca opublikowaną. Aby uzyskać więcej informacji, zobacz [Generalizacja pętli dla pętli opartej na zakresie](https://wg21.link/p0184r0).

## <a name="conformance-improvements-in-153"></a><a name="improvements_153"></a>Ulepszenia zgodności w 15.3

### <a name="constexpr-lambdas"></a>constexpr lambdas

Wyrażenia Lambda mogą być teraz używane w wyrażeniach stałych. Aby uzyskać więcej informacji, zobacz [wyrażenia lambda constexpr w języku C++](../cpp/lambda-expressions-constexpr.md).

### <a name="if-constexpr-in-function-templates"></a>**jeśli constexpr** w szablonach funkcji

Szablon funkcji może **zawierać, jeśli constexpr** instrukcji, aby włączyć rozgałęzienia w czasie kompilacji. Aby uzyskać więcej informacji, [zobacz, czy constexpr instrukcji](../cpp/if-else-statement-cpp.md#if_constexpr).

### <a name="selection-statements-with-initializers"></a>Instrukcje wyboru z inicjatorami

If **if** Instrukcja może zawierać inicjatora, który wprowadza zmienną w zakresie bloku w samej instrukcji. Aby uzyskać więcej informacji, [zobacz, czy instrukcje z inicjatorem](../cpp/if-else-statement-cpp.md#if_with_init).

### <a name="maybe_unused-and-nodiscard-attributes"></a>`[[maybe_unused]]`i `[[nodiscard]]` atrybuty

Nowy atrybut `[[maybe_unused]]` wycisza ostrzeżenia, gdy jednostka nie jest używana. Atrybut `[[nodiscard]]` tworzy ostrzeżenie, jeśli zwracana wartość wywołania funkcji zostanie odrzucona. Aby uzyskać więcej informacji, zobacz [Atrybuty w języku C++](../cpp/attributes.md).

### <a name="using-attribute-namespaces-without-repetition"></a>Używanie obszarów nazw atrybutów bez powtarzania

Nowa składnia umożliwiająca włączenie tylko jednego identyfikatora obszaru nazw na liście atrybutów. Aby uzyskać więcej informacji, zobacz [Atrybuty w języku C++](../cpp/attributes.md).

### <a name="structured-bindings"></a>Wiązania strukturalne

Teraz jest możliwe w pojedynczej deklaracji do przechowywania wartości z poszczególnych nazw dla `std::tuple` jego `std::pair`składników, gdy wartość jest tablica, lub , lub ma wszystkie publiczne niestatyczne elementy członkowskie danych. Aby uzyskać więcej informacji, zobacz [Powiązania strukturalne](https://wg21.link/p0144r0) i [Zwracanie wielu wartości z funkcji](../cpp/functions-cpp.md#multi_val).

### <a name="construction-rules-for-enum-class-values"></a>Zasady budowy wartości **klas wyliczenia**

Istnieje teraz niejawna/niewężająca się konwersja z typu źródłowego wyliczenia o określonym zakresie do samego wyliczenia, gdy jego definicja nie wprowadza żadnego wylicznika, a źródło używa składni inicjowania listy. Aby uzyskać więcej informacji, zobacz [Reguły konstrukcyjne dla wartości klasy wyliczenia](https://wg21.link/p0138r2) [i wyliczenia](../cpp/enumerations-cpp.md#no_enumerators).

### <a name="capturing-this-by-value"></a>Przechwytywanie `*this` według wartości

Obiekt `*this` w wyrażeniu lambda może być teraz przechwycony przez wartość. Ta zmiana umożliwia scenariusze, w których lambda jest wywoływana równolegle i asynchronicznych operacji, szczególnie na nowszych architektur komputera. Aby uzyskać więcej informacji, zobacz [Lambda \[Capture\*\]this \*by Value as =, this](https://wg21.link/p0018r3).

### <a name="removing-operator-for-bool"></a>Usuwanie `operator++` **bool**

`operator++`nie jest już obsługiwana w typach **bool.** Aby uzyskać więcej informacji, zobacz [Usuwanie przestarzałego operatora++(bool)](https://wg21.link/p0002r1).

### <a name="removing-deprecated-register-keyword"></a>Usuwanie przestarzałego słowa kluczowego **rejestru**

Register **register** słowo kluczowe, wcześniej przestarzałe (i ignorowane przez kompilator), jest teraz usuwany z języka. Aby uzyskać więcej informacji, zobacz [Usuwanie przestarzałego używania słowa kluczowego rejestru](https://wg21.link/p0001r1).

## <a name="conformance-improvements-in-155"></a><a name="improvements_155"></a>Ulepszenia zgodności w 15.5

Funkcje \[oznaczone 14] są dostępne bezwarunkowo nawet w trybie **/std:c++14.**

### <a name="new-compiler-switch-for-extern-constexpr"></a>Nowy przełącznik kompilatora dla **extern constexpr**

We wcześniejszych wersjach programu Visual Studio kompilator zawsze dawał wewnętrzne powiązanie zmiennej **constexpr** nawet wtedy, gdy zmienna była oznaczona **jako extern**. W programie Visual Studio 2017 w wersji 15.5 nowy przełącznik kompilatora [/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)umożliwia poprawne zachowanie zgodne ze standardami. Aby uzyskać więcej informacji, zobacz [extern constexpr powiązania](#extern_linkage).

### <a name="removing-dynamic-exception-specifications"></a>Usuwanie dynamicznych specyfikacji wyjątków

[P0003R5](https://wg21.link/p0003r5) Specyfikacje wyjątków dynamicznych zostały przestarzałe w języku C++11. funkcja jest usuwana z języka C++17, ale `throw()` (nadal) przestarzała `noexcept(true)`specyfikacja jest ściśle zachowywana jako alias dla . Aby uzyskać więcej informacji, zobacz [Usuwanie specyfikacji wyjątków dynamicznych i nieobliczaj](#noexcept_removal).

### `not_fn()`

[P0005R4](https://wg21.link/p0005r4) `not_fn` zastępuje `not1` i `not2`.

### <a name="rewording-enable_shared_from_this"></a>Przeredagowanie`enable_shared_from_this`

[P0033R1](https://wg21.link/p0033r1) `enable_shared_from_this` został dodany w języku C++11. Standard C++17 aktualizuje specyfikację, aby lepiej obsługiwać niektóre przypadki narożników. [14]

### <a name="splicing-maps-and-sets"></a>Łączenie map i zestawów

[P0083R3](https://wg21.link/p0083r3) Ta funkcja umożliwia wyodrębnianie węzłów z kontenerów `set` `unordered_map`zespolonych (czyli `unordered_set` `map`, , ), które następnie można zmodyfikować i wstawić z powrotem do tego samego kontenera lub innego kontenera, który używa tego samego typu węzła. (Typowym przypadkiem użycia jest wyodrębnienie węzła z `std::map`, zmień klucz i wstawić ponownie).)

### <a name="deprecating-vestigial-library-parts"></a>Przestarzałe części biblioteki przedsionkowej

[P0174R2](https://wg21.link/p0174r2) Kilka funkcji standardowej biblioteki Języka C++ zostało zastąpionych przez nowsze funkcje na przestrzeni lat, w przeciwnym razie zostały uznane za nieprzydatne lub problematyczne. Te funkcje są oficjalnie przestarzałe w języku C++17.

### <a name="removing-allocator-support-in-stdfunction"></a>Usuwanie obsługi alokatora w`std::function`

[P0302R1](https://wg21.link/p0302r1) Przed C++ 17 szablon `std::function` klasy miał kilka konstruktorów, które miały argument alokatora. Jednak użycie alokatorów w tym kontekście było problematyczne, a semantyka była niejasna. Usunięto problemowe contructory.

### <a name="fixes-for-not_fn"></a>Poprawki dla`not_fn()`

[P0358R1](https://wg21.link/p0358r1) Nowe sformułowanie `std::not_fn` zapewnia obsługę propagacji kategorii wartości, gdy jest używana w wywołaniu otoki.

### <a name="shared_ptrt-shared_ptrtn"></a>`shared_ptr<T[]>`, `shared_ptr<T[N]>`

[P0414R2](https://wg21.link/p0414r2) Scalanie `shared_ptr` zmian z podstaw biblioteki na C++17. [14]

### <a name="fixing-shared_ptr-for-arrays"></a>Mocowanie `shared_ptr` dla tablic

[P0497R0](https://wg21.link/p0497r0) Poprawki do shared_ptr obsługi tablic. [14]

### <a name="clarifying-insert_return_type"></a>Wyjaśnienie`insert_return_type`

[P0508R0](https://wg21.link/p0508r0) Kontenery zespolone z unikatowymi kluczami i nieuporządkowane kontenery z unikatowymi kluczami mają funkcję `insert` elementu członkowskiego, która zwraca typ `insert_return_type`zagnieżdżony. Ten typ zwracany jest teraz zdefiniowany jako specjalizacja typu, który jest sparametryzowany na iteratora i nodetype kontenera.

### <a name="inline-variables-for-the-standard-library"></a>Zmienne wbudowane dla biblioteki standardowej

[P0607R0](https://wg21.link/p0607r0)

### <a name="annex-d-features-deprecated"></a>Cechy załącznika D przestarzałe

Załącznik D do standardu C++ zawiera wszystkie funkcje, `shared_ptr::unique()` `<codecvt>`które `namespace std::tr1`zostały przestarzałe, w tym , i . Po ustawieniu przełącznika kompilatora **/std:c++17** prawie wszystkie standardowe funkcje biblioteki w załączniku D są oznaczone jako przestarzałe. Aby uzyskać więcej informacji, zobacz [Standardowe funkcje biblioteki w załączniku D są oznaczone jako przestarzałe](#annex_d).

Obszar `std::tr2::sys` nazw `<experimental/filesystem>` w teraz emituje ostrzeżenie o deprecation w **/std:c++14** domyślnie i jest teraz usuwany w **obszarze /std:c++17** domyślnie.

Poprawiono `<iostream>` zgodność, unikając niestandardowego rozszerzenia (specjalizacje jawne w klasie).

Standardowa biblioteka używa teraz szablonów zmiennych wewnętrznie.

Standardowa biblioteka została zaktualizowana w odpowiedzi na zmiany kompilatora C++17, w tym dodanie **noexcept** w systemie typu i usunięcie specyfikacji wyjątków dynamicznych.

## <a name="conformance-improvements-in-156"></a><a name="improvements_156"></a>Ulepszenia zgodności w 15.6

### <a name="c17-library-fundamentals-v1"></a>Podstawy biblioteki C++17 V1

[P0220R1](https://wg21.link/p0220r1) zawiera specyfikację techniczną podstawy biblioteki dla C ++17 do standardu. Obejmuje aktualizacje> \<doświadczalnej/krotki, \<> eksperymentalnych/opcjonalnych, \<> eksperymentalnych/funkcjonalnych, \<> \<eksperymentalnych/string_view, \<>> doświadczalne/pamięciowe, \<> doświadczalne/memory_resource oraz \<> doświadczalne/algorytmowe.

### <a name="c17-improving-class-template-argument-deduction-for-the-standard-library"></a>C++17: Poprawa potrącenia argumentu szablonu klasy dla biblioteki standardowej

[P0739R0](https://wg21.link/p0739r0) Przejdź `adopt_lock_t` do przodu listy `scoped_lock` parametrów, `scoped_lock`aby umożliwić spójne korzystanie z programu . Zezwalaj `std::variant` konstruktorowi na uczestnictwo w rozpoznawaniu przeciążenia w większej liczbie przypadków, aby włączyć przypisywanie kopii.

## <a name="conformance-improvements-in-157"></a><a name="improvements_157"></a>Ulepszenia zgodności w 15.7

### <a name="c17-rewording-inheriting-constructors"></a>C++17: Przeredagowanie konstruktorów dziedziczących

[P0136R1](https://wg21.link/p0136r1) określa, że **using** deklaracji, która nazywa konstruktora teraz sprawia, że odpowiednie konstruktory klasy podstawowej widoczne inicjowania klasy pochodnej, zamiast deklarowania dodatkowych konstruktorów klas pochodnych. To przeredagowanie jest zmianą z Języka C++14. W programie Visual Studio 2017 w wersji 15.7 i nowszej w trybie **/std:c++17** kod, który jest prawidłowy w języku C++14 i używa konstruktorów dziedziczenia może być nieprawidłowy lub może mieć inną semantycę.

W poniższym przykładzie przedstawiono zachowanie języka C++14:

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

Poniższy przykład pokazuje **/std:c++17** zachowanie w programie Visual Studio 15.7:

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

Aby uzyskać więcej informacji, zobacz [Konstruktory](../cpp/constructors-cpp.md#inheriting_constructors).

### <a name="c17-extended-aggregate-initialization"></a>C++17: Rozszerzona inicjalizacja agregacji

[P0017R1](https://wg21.link/p0017r1)

Jeśli konstruktor klasy podstawowej jest niepubliczny, ale dostępny dla klasy pochodnej, w trybie **/std:c++17** w programie Visual Studio 2017 w wersji 15.7 nie można już używać pustych nawiasów klamrowych do zainicjowania obiektu typu pochodnego.
Poniższy przykład przedstawia zachowanie konformanta języka C++14:

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

W języku C++ `Derived` 17 jest teraz uważany za typ agregacji. Oznacza to, że `Base` inicjowanie za pośrednictwem prywatnego konstruktora domyślnego odbywa się bezpośrednio, jako część rozszerzonej reguły inicjowania agregacji. Wcześniej `Base` konstruktor prywatny został wywołany za pośrednictwem `Derived` konstruktora i zakończyło się pomyślnie z powodu deklaracji znajomego.
Poniższy przykład pokazuje zachowanie języka C++ 17 w programie Visual Studio w wersji 15.7 w **trybie /std:c++17:**

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

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C++17: Deklarowanie parametrów szablonu nienapowego za pomocą auto

[P0127R2](https://wg21.link/p0127r2)

W trybie **/std:c++17** kompilator może teraz wywnić typ argumentu **auto**szablonu nienap.

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

Jednym z wpływów tej nowej funkcji jest to, że prawidłowy kod C++ 14 może być nieprawidłowy lub może mieć inną semantycę. Na przykład niektóre przeciążenia, które wcześniej były nieprawidłowe, są teraz prawidłowe. W poniższym przykładzie pokazano kod C++ 14, który kompiluje, ponieważ wywołanie `example(p)` jest powiązane `example(void*);`z . W programie Visual Studio 2017 w wersji 15.7 w trybie `example` **/std:c++17** szablon funkcji jest najlepszym dopasowaniem.

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*) = delete;

void example(void *);

void sample(A<0> *p)
{
    example(p); // OK in C++14
}
```

Poniższy przykład pokazuje kod C++ 17 w programie Visual Studio 15.7 w **trybie /std:c++17:**

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*);

void example(void *);

void sample(A<0> *p)
{
    example(p); // C2280: 'int example<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C++17: Konwersje ciągów elementarnych (częściowe)

[P0067R5](https://wg21.link/p0067r5) Funkcje niezależne od niskiego poziomu, niezależnie od ustawień regionalnych dla konwersji między liczbami całkowitymi i ciągami oraz między liczbami zmiennoprzecinkowami i ciągami.

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C++20: Unikanie niepotrzebnego rozkładu (częściowe)

[P0777R1](https://wg21.link/p0777r1) Dodaje rozróżnienie między pojęciem "rozpadu" i po prostu usunięcie const lub kwalifikatorów odwołania.  Nowa cecha `remove_reference_t` typu `decay_t` zastępuje w niektórych kontekstach. Obsługa `remove_cvref_t` jest implementowana w programie Visual Studio 2019.

### <a name="c17-parallel-algorithms"></a>C++17: Algorytmy równoległe

[P0024R2](https://wg21.link/p0024r2) Model Parallelism TS jest włączony do standardu, z niewielkimi modyfikacjami.

### <a name="c17-hypotx-y-z"></a>C++17:`hypot(x, y, z)`

[P0030R1](https://wg21.link/p0030r1) `std::hypot`Dodaje trzy nowe przeciążenia do , dla typów **float,** **double**i long **double**, z których każdy ma trzy parametry wejściowe.

### <a name="c17-filesystem"></a>C++17: \<> systemu plików

[P0218R1](https://wg21.link/p0218r1) Przyjmuje system plików TS do standardu z kilkoma modyfikacjami brzmienia.

### <a name="c17-mathematical-special-functions"></a>C++17: Matematyczne funkcje specjalne

[P0226R1](https://wg21.link/p0220r1) Przyjmuje poprzednie specyfikacje techniczne dla matematycznych \<funkcji specjalnych do standardowego nagłówka cmath>.

### <a name="c17-deduction-guides-for-the-standard-library"></a>C++17: Przewodniki po potrąceniach dla standardowej biblioteki

[P0433R2](https://wg21.link/p0433r2) Aktualizacje STL, aby skorzystać z C ++ 17 przyjęcia [P0091R3](https://wg21.link/p0091r3), który dodaje obsługę dedukcji argumentu szablonu klasy.

### <a name="c17-repairing-elementary-string-conversions"></a>C++17: Naprawa konwersji ciągów elementarnych

[P0682R1](https://wg21.link/p0682r1) Przenieś nowe funkcje konwersji ciągów elementarnych z \<P0067R5 do nowego charconv nagłówka `std::errc`> `std::error_code`i dokonać innych ulepszeń, w tym zmiany obsługi błędów do użycia zamiast .

### <a name="c17-constexpr-for-char_traits-partial"></a>C++17: **constexpr** dla `char_traits` (częściowe)

[P0426R1](https://wg21.link/p0426r1) Zmiany `std::traits_type` w `length`funkcjach `find` członkowskich `std::string_view` , `compare`i aby użyteczne w wyrażeniach stałych. (W programie Visual Studio 2017 w wersji 15.6 obsługiwane tylko dla Clang/LLVM. W wersji 15.7 Preview 2 wsparcie jest prawie kompletne również dla ClXX.)

## <a name="conformance-improvements-in-159"></a><a name="improvements_159"></a>Ulepszenia zgodności w 15.9

### <a name="left-to-right-evaluation-order-for-operators-----and-"></a>Kolejność oceny od lewej do `->*` `[]`prawej `>>`dla operatorów , , i`<<`

Począwszy od C ++ 17, argumenty `->*` `[]`operatorów , `>>`i `<<` muszą być oceniane w kolejności od lewej do prawej. Istnieją dwa przypadki, w których kompilator nie może zagwarantować tej kolejności:

- gdy jedno z wyrażeń operandowych jest obiektem przekazywanym przez wartość lub zawiera obiekt przekazywany przez wartość, lub

- podczas kompilowania przy użyciu **/clr**, a jeden z argumentów jest polem obiektu lub elementu tablicy.

Kompilator emituje ostrzeżenie [C4866,](https://docs.microsoft.com/cpp/error-messages/compiler-warnings/c4866?view=vs-2017) gdy nie może zagwarantować oceny od lewej do prawej. Kompilator generuje to ostrzeżenie tylko wtedy, **gdy /std:c++17** lub nowsze jest określony, jak wymagania kolejności od lewej do prawej tych operatorów został wprowadzony w języku C++17.

Aby rozwiązać to ostrzeżenie, należy najpierw rozważyć, czy ocena od lewej do prawej argumentów jest konieczna, na przykład gdy ocena argumentów może powodować efekty uboczne zależne od zamówienia. W wielu przypadkach kolejność, w jakiej są oceniane argumenty, nie ma zauważalnego efektu. Jeśli kolejność oceny musi być od lewej do prawej, należy rozważyć, czy można przekazać argumenty przez const odwołania zamiast. Ta zmiana eliminuje ostrzeżenie w poniższym przykładzie kodu:

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

## <a name="bug-fixes-in-visual-studio-2017-rtw-version-150"></a><a name="update_150"></a>Poprawki błędów w programie Visual Studio 2017 RTW (wersja 15.0)

### <a name="copy-list-initialization"></a>Inicjowanie listy kopiowania

Visual Studio 2017 poprawnie wywołuje błędy kompilatora związane z tworzeniem obiektów przy użyciu list inicjatora, które nie zostały przechwycone w programie Visual Studio 2015 i może prowadzić do awarii lub niezdefiniowanego zachowania środowiska uruchomieniowego. Zgodnie z N4594 13.3.1.7p1, w copy-list-inicjowania kompilator jest zobowiązany do rozważenia jawnego konstruktora dla rozpoznawania przeciążenia, ale musi podnieść błąd, jeśli zostanie wybrany ten szczególny przeciążenie.

Poniższe dwa przykłady skompilować w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.

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

Aby rozwiązać ten błąd, należy użyć zainicjowania bezpośredniego:

```cpp
A a1{ 1 };
const A& a2{ 1 };
```

W programie Visual Studio 2015 kompilator błędnie potraktował inicjowanie listy kopii w taki sam sposób, jak zwykła inicjowanie kopiowania; za konwersję konstruktorów dla rozdzielczości przeciążenia. W poniższym przykładzie Visual Studio 2015 wybiera MyInt(23), ale Visual Studio 2017 poprawnie zgłasza błąd.

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

Ten przykład jest podobny do poprzedniego, ale wywołuje inny błąd. To powiedzie się w programie Visual Studio 2015 i kończy się niepowodzeniem w programie Visual Studio 2017 z C2668.

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

Visual Studio 2017 teraz wystawia poprawne ostrzeżenie dla przestarzałych typedefs, które są zadeklarowane w klasie lub struktury. Poniższy przykład kompiluje bez ostrzeżeń w programie Visual Studio 2015, ale produkuje C4996 w programie Visual Studio 2017.

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

Visual Studio 2017 poprawnie podnosi błąd, gdy po lewej stronie operand warunkowo oceny operacji nie jest prawidłowy w kontekście constexpr. Poniższy kod kompiluje się w programie Visual Studio 2015, ale nie w programie Visual Studio 2017 (funkcja konsekpr C3615 'f' nie może spowodować wyrażenia stałego):

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

Aby rozwiązać ten błąd, `array::size()` zadeklaruj funkcję jako **constexpr** lub usuń kwalifikator **constexpr** z `f`.

### <a name="class-types-passed-to-variadic-functions"></a>Typy klas przekazywane do funkcji zmiennorozmiasnych

W programie Visual Studio 2017 klasy lub struktury, które są przekazywane do funkcji zmiennej, takich jak printf musi być trywialnie do kopiowania. Podczas przekazywania takich obiektów kompilator po prostu wykonuje kopię bitową i nie wywołuje konstruktora lub destruktora.

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

Aby poprawić błąd, można wywołać funkcję elementu członkowskiego, która zwraca trywialnie skopiowany typ,

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

lub użyć rzutowania statycznego do konwersji obiektu przed przekazaniem go:

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

Dla ciągów zbudowanych i zarządzanych `operator LPCTSTR()` przy użyciu CString, dostarczone powinny być używane do rzutowania CString obiektu do wskaźnika C oczekiwane przez ciąg formatu.

```cpp
CString str1;
CString str2 = _T("hello!");
str1.Format(_T("%s"), static_cast<LPCTSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>Kwalifikacje cv w budowie klas

W programie Visual Studio 2015 kompilator czasami niepoprawnie ignoruje kwalifikator cv podczas generowania obiektu klasy za pośrednictwem wywołania konstruktora. Ten problem może potencjalnie spowodować awarię lub nieoczekiwane zachowanie środowiska uruchomieniowego. Poniższy przykład kompiluje w programie Visual Studio 2015, ale wywołuje błąd kompilatora w programie Visual Studio 2017:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Aby poprawić błąd, `operator int()` zadeklarować jako **const**.

### <a name="access-checking-on-qualified-names-in-templates"></a>Sprawdzanie dostępu do kwalifikowanych nazw w szablonach

Poprzednie wersje kompilatora nie sprawdzały dostępu do nazw kwalifikowanych w niektórych kontekstach szablonu. Ten problem może kolidować z oczekiwanym zachowaniem SFINAE, gdzie zastąpienie oczekuje się nie powiódł się z powodu niedostępności nazwy. Może to potencjalnie spowodować awarię lub nieoczekiwane zachowanie w czasie wykonywania, ponieważ kompilator niepoprawnie wywołane nieprawidłowe przeciążenie operatora. W programie Visual Studio 2017 wywoływany jest błąd kompilatora. Konkretny błąd może się różnić, ale zazwyczaj jest to "C2672 nie pasujące przeciążone funkcji znaleziono". Następujący kod kompiluje się w programie Visual Studio 2015, ale wywołuje błąd w programie Visual Studio 2017:

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

### <a name="missing-template-argument-lists"></a>Brakujące listy argumentów szablonu

W programie Visual Studio 2015 i wcześniejszych kompilator nie zdiagnozował brakujących list argumentów szablonu, gdy szablon pojawił się na liście parametrów szablonu, na przykład jako część domyślnego argumentu szablonu lub parametru szablonu innego typu. Ten problem może spowodować nieprzewidywalne zachowanie, w tym awarii kompilatora lub nieoczekiwane zachowanie środowiska uruchomieniowego. Poniższy kod kompiluje się w programie Visual Studio 2015, ale generuje błąd w programie Visual Studio 2017.

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Wyrażenie-SFINAE

Do obsługi expression-SFINAE kompilator teraz analizuje argumenty **decltype,** gdy szablony są zadeklarowane, a nie wystąpienia. W związku z tym jeśli specjalizacja nieoleżna znajduje się w decltype argument, nie jest odroczone do czasu wystąpienia. Jest przetwarzany natychmiast, a wszelkie wynikające z tego błędy są diagnozowane w tym czasie.

Poniższy przykład pokazuje taki błąd kompilatora, który jest wywoływany w punkcie deklaracji:

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

Zgodnie ze standardem C++ klasa zadeklarowana wewnątrz anonimowego obszaru nazw ma wewnętrzne powiązanie, a to oznacza, że nie można jej wyeksportować. W programie Visual Studio 2015 i wcześniejszych tej reguły nie było wymuszane. W programie Visual Studio 2017 reguła jest częściowo wymuszana. Poniższy przykład wywołuje ten błąd w programie Visual Studio 2017: "błąd C2201: const anonimowy obszar nazw::S1::vftable: musi mieć zewnętrzne powiązanie, aby można było wyeksportować/zaimportować."

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>Domyślne inicjatory elementów członkowskich klasy wartości (C++/CLI)

W programie Visual Studio 2015 i wcześniejszych kompilator dozwolone (ale ignorowane) domyślny inicjatora elementu członkowskiego dla członka klasy wartości. Domyślna inicjowanie klasy wartości zawsze inicjuje zero elementów członkowskich. Domyślny konstruktor nie jest dozwolony. W programie Visual Studio 2017 domyślne inicjatory elementu członkowskiego podnoszą błąd kompilatora, jak pokazano w tym przykładzie:

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // isn't allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Domyślne indeksatory (C++/CLI)

W programie Visual Studio 2015 i wcześniejszych kompilator w niektórych przypadkach błędnie zidentyfikowano właściwość domyślną jako domyślny indeksator. Można było obejść ten problem przy użyciu **domyślnego** identyfikatora, aby uzyskać dostęp do właściwości. Samo obejście stało się problematyczne po wprowadzeniu **domyślnego** słowa kluczowego w języku C++11. W programie Visual Studio 2017 usunięcie błędów, które wymagały obejścia, a kompilator generuje teraz błąd, gdy **domyślnie** jest używany do uzyskiwania dostępu do domyślnej właściwości dla klasy.

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

W programie Visual Studio 2017 można uzyskać dostęp do obu właściwości Value według ich nazwy:

```cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="bug-fixes-in-153"></a><a name="update_153"></a>Poprawki błędów w 15.3

### <a name="calls-to-deleted-member-templates"></a>Wywołania usuniętych szablonów członków

W poprzednich wersjach programu Visual Studio kompilator w niektórych przypadkach nie może emitować błąd dla źle sformułowanych wywołań do usuniętego szablonu elementu członkowskiego, który mógłby potencjalnie spowodować awarie w czasie wykonywania. Poniższy kod tworzy teraz C2280, "'int S\<int\<>::f int>(void)': próba odwołania się do usuniętej funkcji":

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

Aby naprawić błąd, `i` zadeklarować jako **int**.

### <a name="pre-condition-checks-for-type-traits"></a>Wstępne sprawdzanie stanu pod kątem cech typu

Visual Studio 2017 w wersji 15.3 poprawia wstępne sprawdzanie stanu cech typu bardziej rygorystycznie przestrzegać standardu. Jednym z takich kontroli jest możliwość przypisania. Poniższy kod tworzy C2139 w programie Visual Studio 2017 w wersji 15.3:

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Nowe ostrzeżenie kompilatora i sprawdzanie środowiska uruchomieniowego na natywnej do zarządzanej

Wywołanie z funkcji zarządzanych do funkcji natywnych wymaga organizowania. CLR nie marshaling, ale nie rozumie semantyki języka C++. Jeśli przekażesz obiekt macierzysty według wartości, program CLR wywołuje konstruktora kopii obiektu lub używa `BitBlt`, co może powodować niezdefiniowane zachowanie w czasie wykonywania.

Teraz kompilator emituje ostrzeżenie, jeśli może wiedzieć w czasie kompilacji, że obiekt macierzysty z usuniętym ctor kopii jest przekazywana między natywną i zarządzaną granicą przez wartość. W tych przypadkach, w których kompilator nie wie w czasie kompilacji, wstrzykuje sprawdzanie środowiska uruchomieniowego, tak aby program wywołuje `std::terminate` natychmiast, gdy występuje źle sformułowane kierowanie. W programie Visual Studio 2017 w wersji 15.3 następujący kod generuje ostrzeżenie C4606 "'A': przekazywanie argumentu przez wartość przez natywną i zarządzaną granicę wymaga prawidłowego konstruktora kopiowania. W przeciwnym razie zachowanie środowiska wykonawczego jest niezdefiniowane.

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

Aby naprawić błąd, `#pragma managed` usuń dyrektywę, aby oznaczyć wywołującego jako natywnego i uniknąć organizowania.

### <a name="experimental-api-warning-for-winrt"></a>Eksperymentalne ostrzeżenie API dla winrt

Interfejsy API winrt, które są wydawane do `Windows.Foundation.Metadata.ExperimentalAttribute`eksperymentowania i opinii są ozdobione . W programie Visual Studio 2017 w wersji 15.3 kompilator generuje ostrzeżenie C4698, gdy napotka atrybut. Kilka interfejsów API w poprzednich wersjach zestawie Windows SDK zostały już ozdobione atrybutem i wywołania tych interfejsów API teraz wyzwolić to ostrzeżenie kompilatora. Nowsze sdk systemu Windows mają atrybut usunięte ze wszystkich wysłanych typów, ale jeśli używasz starszego SDK, należy pominąć te ostrzeżenia dla wszystkich wywołań do wysłanych typów.

Poniższy kod generuje ostrzeżenie C4698: "'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' służy wyłącznie do celów ewaluacyjnych i może ulec zmianie lub usunięciu w przyszłych aktualizacjach":

```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); //C4698
```

Aby wyłączyć ostrzeżenie, dodaj #pragma:

```cpp
#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>Definicja elementu członkowskiego szablonu poza wierszem

Visual Studio 2017 w wersji 15.3 generuje błąd, gdy napotka poza wierszem definicji funkcji elementu członkowskiego szablonu, który nie został zadeklarowany w klasie. Poniższy kod generuje teraz błąd C2039: 'f': nie jest członkiem 'S':

```cpp
struct S {};

template <typename T>
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

Aby naprawić błąd, dodaj deklarację do klasy:

```cpp
struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Próba podjęcia adresu **tego** wskaźnika

W języku C++ jest **to** wartość prvalue wskaźnika typu do X. Nie można wziąć adres **tego** lub powiązać go z lvalue odwołania. W poprzednich wersjach programu Visual Studio kompilator pozwoli obejść to ograniczenie przy użyciu rzutowania. W programie Visual Studio 2017 w wersji 15.3 kompilator generuje błąd C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Konwersja do niedostępnej klasy podstawowej

Visual Studio 2017 w wersji 15.3 generuje błąd podczas próby przekonwertowania typu na klasę podstawową, która jest niedostępna. Kompilator teraz podnosi "błąd C2243: 'type cast': konwersja z 'D *' do 'B *' istnieje, ale jest niedostępna". Poniższy kod jest źle sformułowany i może potencjalnie spowodować awarię w czasie wykonywania. Kompilator teraz produkuje C2243, gdy napotka kod tak:

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-arent-allowed-on-out-of-line-definitions-of-member-functions"></a>Domyślne argumenty nie są dozwolone w definicjach poza wierszem funkcji członkowskich

Domyślne argumenty nie są dozwolone w pozawierszowych definicjach funkcji członkowskich w klasach szablonów. Kompilator wyda ostrzeżenie w **obszarze /permissive**i twardy błąd w [/permissive-](../build/reference/permissive-standards-conformance.md).

W poprzednich wersjach programu Visual Studio następujący źle sformułowany kod może potencjalnie spowodować awarię środowiska wykonawczego. Visual Studio 2017 w wersji 15.3 generuje ostrzeżenie\<C5034: "T>::f": definicja poza wierszem elementu członkowskiego szablonu klasy nie może mieć domyślnych argumentów:

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

Aby naprawić błąd, `= false` usuń domyślny argument.

### <a name="use-of-offsetof-with-compound-member-designator"></a>Zastosowanie `offsetof` z elementem konstrukcyjnym złożonym

W programie Visual Studio 2017 w wersji `offsetof(T, m)` 15.3, przy użyciu *m* jest "element członkowski projektator złożony" powoduje ostrzeżenie podczas kompilacji z **/Wall** opcji. Poniższy kod jest źle sformułowany i może potencjalnie spowodować awarię w czasie wykonywania. Visual Studio 2017 w wersji 15.3 produkuje "ostrzeżenie C4841: niestandardowe rozszerzenie używane: złożony projekt elementu członkowskiego w offsetof":

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

Aby naprawić kod, wyłącz ostrzeżenie za pomocą pragmy lub zmień `offsetof`kod, aby nie używać:

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Używanie `offsetof` z statycznym elementem członkowskim lub funkcją elementu członkowskiego danych

W programie Visual Studio 2017 w wersji `offsetof(T, m)` 15.3, przy użyciu *m* odwołuje się do elementu członkowskiego danych statycznych lub funkcji elementu członkowskiego powoduje błąd. Poniższy kod tworzy "error C4597: undefined behavior: offsetof applied to member function 'example'" i "error C4597: undefined behavior: offsetof applied to static data member 'sample'"

```cpp
#include <cstddef>

struct A {
   int ten() { return 10; }
   static constexpr int two = 2;
};

constexpr auto off = offsetof(A, ten);
constexpr auto off2 = offsetof(A, two);
```

Ten kod jest źle sformułowany i może potencjalnie spowodować awarię w czasie wykonywania. Aby naprawić błąd, zmień kod, aby nie wywoływał już niezdefiniowanego zachowania. Jest to nieprzenośny kod, który jest niedozwolony przez standard C++.

### <a name="new-warning-on-__declspec-attributes"></a><a name="declspec"></a>Nowe ostrzeżenie `__declspec` o atrybutach

W programie Visual Studio 2017 w wersji 15.3 `__declspec(...)` kompilator `extern "C"` nie ignoruje już atrybutów, jeśli jest stosowany przed specyfikacją powiązania. Wcześniej kompilator będzie ignorować atrybut, który może mieć wpływ na środowisko uruchomieniowe. Po ustawieniu opcji **/Wall** i **/WX** następujący kod generuje "ostrzeżenie C4768: __declspec atrybuty przed specyfikacją powiązania są ignorowane":

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Aby naprawić ostrzeżenie, `extern "C"` połóż najpierw:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

To ostrzeżenie jest domyślnie wyłączone w 15.3, ale domyślnie włączone w 15.5 i wpływa tylko na kod skompilowany z **/Wall** **/WX**.

### <a name="decltype-and-calls-to-deleted-destructors"></a>**decltype** i wywołania usuniętych destruktorów

W poprzednich wersjach programu Visual Studio kompilator nie wykrył, kiedy wywołanie usuniętego destruktora wystąpiło w kontekście wyrażenia skojarzonego z **decltypem**. W programie Visual Studio 2017 w wersji 15.3 następujący kod generuje\<"błąd C2280: 'T>::~A(void)': próba odwołania się do usuniętej funkcji":

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

Wydanie RTW programu Visual Studio 2017 miało regresję, w której kompilator języka C++ nie wystawiłby diagnostyki, jeśli nie została zainicjowana zmienna **const.** Ta regresja została naprawiona w programie Visual Studio 2017 w wersji 15.3. Poniższy kod generuje teraz "ostrzeżenie C4132: 'Value': const object should be initialized":

```cpp
const int Value; //C4132
```

Aby naprawić błąd, przypisz `Value`wartość do pliku .

### <a name="empty-declarations"></a>Puste deklaracje

Visual Studio 2017 w wersji 15.3 ostrzega teraz o pustych deklaracjach dla wszystkich typów, a nie tylko typów wbudowanych. Poniższy kod generuje teraz ostrzeżenie poziomu 2 C4091 dla wszystkich czterech deklaracji:

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

Aby usunąć ostrzeżenia, skomentuj lub usuń puste deklaracje. W przypadkach, gdy obiekt bez nazwy ma mieć efekt uboczny (na przykład RAII), należy nadać mu nazwę.

Ostrzeżenie jest wykluczone w **obszarze /Wv:18** i jest domyślnie włączone na poziomie ostrzeżenia W2.

### <a name="stdis_convertible-for-array-types"></a>`std::is_convertible`dla typów tablic

Poprzednie wersje kompilatora dał niepoprawne wyniki dla [std::is_convertible](../standard-library/is-convertible-class.md) dla typów tablic. To wymagane moduły zapisu biblioteki do specjalnego przypadku `std::is_convertible<...>` kompilatora Microsoft C++ podczas korzystania z cechy typu. W poniższym przykładzie statyczne potwierdzenia przekazać we wcześniejszych wersjach programu Visual Studio, ale nie w programie Visual Studio 2017 w wersji 15.3:

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>`jest obliczana przez sprawdzenie, czy definicja funkcji wyimaginowanej jest dobrze sformułowana:

```cpp
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdis_constructible"></a>Prywatne destruktory i`std::is_constructible`

Poprzednie wersje kompilatora ignorowane, czy destruktor był prywatny przy podejmowaniu decyzji o wyniku [std::is_constructible](../standard-library/is-constructible-class.md). Teraz je rozpatruje. W poniższym przykładzie statyczne potwierdzenia przekazać we wcześniejszych wersjach programu Visual Studio, ale nie w programie Visual Studio 2017 w wersji 15.3:

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

Prywatne destruktory powodują, że typ jest niekonstruowalny. `std::is_constructible<T, Args...>`jest obliczana tak, jakby sporządzono następującą deklarację:

```cpp
   T obj(std::declval<Args>()...)
```

To wywołanie implikuje wywołanie destruktora.

### <a name="c2668-ambiguous-overload-resolution"></a>C2668: Niejednoznaczna rozdzielczość przeciążenia

Poprzednie wersje kompilatora czasami nie można wykryć niejednoznaczności, gdy znaleziono wielu kandydatów za pomocą deklaracji i wyszukiwania zależne od argumentów. Ten błąd może prowadzić do wybranego nieprawidłowego przeciążenia i nieoczekiwanego zachowania środowiska uruchomieniowego. W poniższym przykładzie Visual Studio 2017 w wersji 15.3 poprawnie podnosi C2668 'f': niejednoznaczne wywołanie funkcji przeciążonej:

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

Aby naprawić kod, usuń `N::f` instrukcję using, `::f()`jeśli zamierzasz wywołać program .

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660: lokalne deklaracje funkcji i wyszukiwanie zależne od argumentów

Lokalne deklaracje funkcji ukrywają deklarację funkcji w otaczającym zakresie i wyłączają wyszukiwanie zależne od argumentów. Jednak poprzednie wersje kompilatora wykonywane wyszukiwania zależne od argumentów w tym przypadku, potencjalnie prowadzi do niewłaściwego przeciążenia są wybierane i nieoczekiwane zachowanie środowiska uruchomieniowego. Zazwyczaj błąd jest z powodu niepoprawnego podpisu deklaracji funkcji lokalnej. W poniższym przykładzie Visual Studio 2017 w wersji 15.3 poprawnie podnosi C2660 'f': funkcja nie przyjmuje dwóch argumentów:

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

Aby rozwiązać ten problem, `f(S)` zmień podpis lub usuń go.

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038: kolejność inicjowania na listach inicjatorów

Elementy członkowskie klasy są inicjowane w kolejności, w jakiej są deklarowane, a nie w kolejności, w jakiej pojawiają się na listach inicjatorów. Poprzednie wersje kompilatora nie ostrzegały, gdy kolejność listy inicjatorów różniła się od kolejności deklaracji. Ten problem może prowadzić do niezdefiniowanego zachowania środowiska uruchomieniowego, jeśli inicjowanie jednego elementu członkowskiego zależało od innego elementu członkowskiego na liście, który został już zainicjowany. W poniższym przykładzie visual studio 2017 w wersji 15.3 (z **/Wall**) podnosi "ostrzeżenie C5038: element członkowski danych "A::y" zostanie zainicjowany po element członkowski danych 'A::x'":

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

Aby rozwiązać ten problem, rozmieść listę inicjatora, aby mieć taką samą kolejność jak deklaracje. Podobne ostrzeżenie jest wywoływane, gdy jeden lub oba inicjatory odnoszą się do elementów członkowskich klasy podstawowej.

To ostrzeżenie jest domyślnie wyłączone i dotyczy tylko kodu skompilowanego z **/Wall**.

## <a name="bug-fixes-and-other-behavior-changes-in-155"></a><a name="update_155"></a>Poprawki błędów i inne zmiany zachowania w 15.5

### <a name="partial-ordering-change"></a>Częściowa zmiana kolejności

Kompilator teraz poprawnie odrzuca następujący kod i daje poprawny komunikat o błędzie:

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

Problem w powyższym przykładzie polega na tym, że istnieją dwie różnice w typach (const vs. non-const i pack vs. non-pack). Aby wyeliminować błąd kompilatora, usuń jedną z różnic. Dzięki temu kompilator jednoznacznie uporządkować funkcje.

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

Programy obsługi odwołania do tablicy lub typu funkcji nigdy nie są zgodne dla dowolnego obiektu wyjątku. Kompilator teraz poprawnie honoruje tę regułę i podnosi ostrzeżenie poziomu 4. Nie pasuje już do `char*` obsługi `wchar_t*` lub do literału ciągu, gdy **/Zc:strictStrings** jest używany.

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

### <a name="stdtr1-namespace-is-deprecated"></a><a name="tr1"></a>`std::tr1` obszar nazw jest przestarzały

Niestandardowy obszar `std::tr1` nazw jest teraz oznaczony jako przestarzały w trybach C++14 i C++17. W programie Visual Studio 2017 w wersji 15.5 następujący kod wywołuje C4996:

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

Aby naprawić błąd, usuń odwołanie `tr1` do obszaru nazw:

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

### <a name="standard-library-features-in-annex-d-are-marked-as-deprecated"></a><a name="annex_d"></a>Standardowe elementy biblioteki w załączniku D są oznaczone jako przestarzałe

Po ustawieniu przełącznika kompilatora trybu **/std:c++17** prawie wszystkie standardowe funkcje biblioteki w załączniku D są oznaczone jako przestarzałe.

W programie Visual Studio 2017 w wersji 15.5 następujący kod wywołuje C4996:

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

Aby naprawić błąd, postępuj zgodnie z instrukcjami w tekście ostrzeżenia, jak pokazano w poniższym kodzie:

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

### <a name="unreferenced-local-variables"></a>Zmienne lokalne bez odwołań

W programie Visual Studio 15.5 ostrzeżenie C4189 jest emitowane w większej liczbie przypadków, jak pokazano w poniższym kodzie:

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}
```

```Output
warning C4189: 's': local variable is initialized but not referenced
```

Aby naprawić błąd, usuń nieużyną zmienną.

### <a name="single-line-comments"></a>Komentarze jednowierszowe

W programie Visual Studio 2017 w wersji 15.5 ostrzeżenia C4001 i C4179 nie są już emitowane przez kompilator C. Wcześniej były one emitowane tylko w przełączniku kompilatora **/Za.**  Ostrzeżenia nie są już potrzebne, ponieważ komentarze jednowierszowe są częścią normy C od C99.

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

Jeśli kod nie musi być zgodny z powrotem, można uniknąć ostrzeżenia, usuwając c4001/C4179 tłumienia. Jeśli kod musi być zgodny z powrotem, należy pominąć tylko C4619.

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="__declspec-attributes-with-extern-c-linkage"></a>`__declspec`atrybuty `extern "C"` z powiązaniem

We wcześniejszych wersjach programu Visual Studio `__declspec(...)` kompilator zignorował atrybuty, gdy `__declspec(...)` został zastosowany przed specyfikacją `extern "C"` powiązania. To zachowanie spowodowało, że kod ma być generowany, że użytkownik nie zamierza, z możliwych implikacji środowiska uruchomieniowego. Ostrzeżenie zostało dodane w programie Visual Studio w wersji 15.3, ale było domyślnie wyłączone. W programie Visual Studio 2017 w wersji 15.5 ostrzeżenie jest domyślnie włączone.

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

Aby naprawić błąd, umieść specyfikację powiązania przed atrybutem __declspec:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

To nowe ostrzeżenie C4768 jest podane w niektórych nagłówkach SDK systemu Windows, które zostały dostarczone z programem Visual Studio 2017 15.3 lub starszym (na przykład: wersja 10.0.15063.0, znany również jako RS2 SDK). Jednak nowsze wersje nagłówków SDK systemu Windows (w szczególności ShlObj.h i ShlObj_core.h) zostały naprawione, aby nie wygenerowały ostrzeżenia. Gdy zobaczysz to ostrzeżenie pochodzące z nagłówków SDK systemu Windows, możesz podjąć następujące akcje:

1. Przełącz się do najnowszego sdk systemu Windows, który został doszła do wersji 15.5 programu Visual Studio 2017.

1. Wyłącz ostrzeżenie wokół #include instrukcji nagłówka zestawie Windows SDK:

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern-constexpr-linkage"></a><a name="extern_linkage"></a>Połączenie Extern constexpr

We wcześniejszych wersjach programu Visual Studio kompilator zawsze dawał wewnętrzne powiązanie zmiennej **constexpr** nawet wtedy, gdy zmienna była oznaczona **jako extern**. W programie Visual Studio 2017 w wersji 15.5 nowy przełącznik kompilatora (**/Zc:externConstexpr**) umożliwia poprawne zachowanie zgodne ze standardami. Ostatecznie to zachowanie stanie się ustawieniem domyślnym.

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

Jeśli plik nagłówka zawiera zmienną zadeklarowaną **extern constexpr,** musi być oznaczony `__declspec(selectany)` tak, aby jego zduplikowane deklaracje zostały poprawnie połączone:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>**typeid** nie może być używany w przypadku typu klasy niekompletnej

We wcześniejszych wersjach programu Visual Studio kompilator niepoprawnie dozwolone następujący kod, co powoduje potencjalnie niepoprawne informacje o typie. W programie Visual Studio 2017 w wersji 15.5 kompilator poprawnie zgłasza błąd:

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdis_convertible-target-type"></a>`std::is_convertible`typ docelowy

`std::is_convertible`wymaga, aby typ docelowy był prawidłowym typem zwracanym. We wcześniejszych wersjach programu Visual Studio kompilator niepoprawnie dozwolone typy abstrakcyjne, co może prowadzić do niepoprawne przeciążenie rozpoznawania i niezamierzone zachowanie środowiska uruchomieniowego.  Następujący kod teraz poprawnie podnosi C2338:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5
```

Aby uniknąć błędu, `is_convertible` podczas korzystania należy porównać typy wskaźników, ponieważ porównanie typu niebędącego wskaźnikiem może zakończyć się niepowodzeniem, jeśli jeden typ jest abstrakcyjny:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");
```

### <a name="dynamic-exception-specification-removal-and-noexcept"></a><a name="noexcept_removal"></a>Dynamiczne usuwanie specyfikacji wyjątków i **brak zmekceptu**

W `throw()` języku C++17 jest aliasem dla **noexcept** `throw(<type list>)` i `throw(...)` są usuwane, a niektóre typy mogą zawierać **noexcept**. Ta zmiana może powodować problemy ze zgodnością źródła z kodem, który jest zgodny z C++ 14 lub wcześniej. Przełącznik **/Zc:noexceptTypes-** może służyć do powrotu do wersji C++ 14 **noexcept** podczas korzystania z trybu C++17 w ogóle. Umożliwia aktualizację kodu źródłowego, aby były zgodne z C++17 bez konieczności ponownego zapisu całego `throw()` kodu w tym samym czasie.

Kompilator diagnozuje teraz bardziej niezgodne specyfikacje wyjątków w deklaracjach w trybie C++17 lub [z /permissive-](../build/reference/permissive-standards-conformance.md) z nowym ostrzeżeniem C5043.

Następujący kod generuje C5043 i C5040 w programie Visual Studio 2017 w wersji 15.5, gdy zostanie zastosowany przełącznik **/std:c++17:**

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

Aby usunąć błędy podczas korzystania z **/std:c++17**, dodaj przełącznik **/Zc:noexceptTypes-** do wiersza polecenia lub zaktualizuj kod, aby użyć **noexcept**, jak pokazano w poniższym przykładzie:

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

Statyczne constexpr elementy członkowskie danych są teraz niejawnie wbudowane, co oznacza, że ich deklaracja w klasie jest teraz ich definicja. Za pomocą definicji out-of-line dla statycznego elementu członkowskiego danych constexpr jest nadmiarowy, a teraz przestarzałe. W programie Visual Studio 2017 w wersji 15.5 po zastosowaniu przełącznika **/std:c++17** następujący kod generuje teraz ostrzeżenie C5041 *"size": definicja pozawierszowa dla elementu członkowskiego danych statycznych constexpr nie jest potrzebna i jest przestarzała w języku C++17:*

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-__declspec-warning-c4768-now-on-by-default"></a>`extern "C" __declspec(...)`ostrzeżenie C4768 jest domyślnie włączone

Ostrzeżenie zostało dodane w programie Visual Studio 2017 w wersji 15.3, ale było domyślnie wyłączone. W programie Visual Studio 2017 w wersji 15.5 ostrzeżenie jest domyślnie włączone. Aby uzyskać więcej informacji, zobacz [Nowe ostrzeżenie dotyczące \_ \_atrybutów declspec](#declspec).

### <a name="defaulted-functions-and-__declspecnothrow"></a>Domyślne funkcje i`__declspec(nothrow)`

Kompilator wcześniej dozwolone domyślne funkcje `__declspec(nothrow)` mają być zadeklarowane, gdy odpowiednie funkcje podstawowe/członkowskie dozwolone wyjątki. To zachowanie jest sprzeczne ze standardem C++ i może powodować niezdefiniowane zachowanie w czasie wykonywania. Standard wymaga, aby takie funkcje były definiowane jako usunięte, jeśli istnieje niezgodność specyfikacji wyjątku.  W **obszarze /std:c++17**poniższy kod wywołuje C2280 *próbując odwoływać się do usuniętej funkcji. Funkcja została niejawnie usunięta, ponieważ specyfikacja jawnego wyjątku jest niezgodna z specyfikacją niejawnej deklaracji.*

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

Aby poprawić ten kod, usuń __declspec(nothrow) z domyślnej funkcji `= default` lub usuń i podaj definicję funkcji wraz z wymaganą obsługą wyjątków:

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

### <a name="noexcept-and-partial-specializations"></a>**specjalizacje niez wyjątkiem** i częściowe

Z **noexcept** w systemie typu, częściowe specjalizacje do dopasowania określonych typów "wywoływane" może nie skompilować lub wybrać szablon podstawowy z powodu braku częściowej specjalizacji dla wskaźników do-noexcept-functions.

W takich przypadkach może być konieczne dodanie dodatkowych specjalizacji częściowych do obsługi wskaźników funkcji **noexcept** i **wskaźników bezwydatkowych** do funkcji członkowskich. Te przeciążenia są legalne tylko w trybie **/std:c++17.** Jeśli zgodność z powrotem z C++ 14 musi być utrzymywana, a piszesz kod, który inni `#ifdef` zużywają, następnie należy chronić te nowe przeciążenia wewnątrz dyrektyw. Jeśli pracujesz w samodzielnym module, zamiast używać `#ifdef` osłon możesz po prostu skompilować za pomocą przełącznika **/Zc:noexceptTypes-.**

Poniższy kod kompiluje się w **obszarze /std:c++14,** ale kończy się niepowodzeniem w **obszarze /std:c++17** z "error C2027:use of undefined type 'A\<T>'":

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

Następujący kod powiedzie się w **obszarze /std:c++17,** ponieważ `A<void (*)() noexcept>`kompilator wybiera nową specjalizację częściową:

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

## <a name="bug-fixes-and-other-behavior-changes-in-157"></a><a name="update_157"></a>Poprawki błędów i inne zmiany zachowania w 15.7

### <a name="c17-default-argument-in-the-primary-class-template"></a>C++17: Domyślny argument w szablonie klasy podstawowej

Ta zmiana zachowania jest warunkiem wstępnym [dedukcji argumentu szablonu dla szablonów klas - P0091R3](https://wg21.link/p0091r3).

Wcześniej kompilator zignorował domyślny argument w szablonie klasy podstawowej:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

W trybie **/std:c++17** w programie Visual Studio 2017 w wersji 15.7 domyślny argument nie jest ignorowany:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>Rozpoznawanie nazw zależnych

Ta zmiana zachowania jest warunkiem wstępnym [dedukcji argumentu szablonu dla szablonów klas - P0091R3](https://wg21.link/p0091r3).

W poniższym przykładzie kompilator w programie Visual Studio 15.6 i wcześniejszych jest rozpoznawany `D::type` `B<T>::type` w szablonie klasy podstawowej.

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

Visual Studio 2017 w wersji 15.7, w **trybie /std:c++17,** wymaga słowa**kluczowego nazwy typu** w **using** instrukcji w D. Bez**nazwy typu**kompilator podnosi ostrzeżenie C4346: *'B\*<T>::type': nazwa zależna nie jest typem,* a błąd C2061: *błąd składniowy: identyfikator 'type':*

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

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C++17: `[[nodiscard]]` atrybut - wzrost poziomu ostrzeżenia

W programie Visual Studio 2017 w wersji 15.7 w trybie **/std:c++17** poziom ostrzeżenia C4834 ("odrzucająca wartość zwracania funkcji z atrybutem 'nodiscard'") jest zwiększany z W3 do W1. Ostrzeżenie można wyłączyć z rzutem na **pustkę**lub przekazując **/wd:4834** do kompilatora

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Lista inicjowania klasy podstawowej konstruktora szablonu variadic

W poprzednich wersjach programu Visual Studio lista inicjowania klasy podstawowej konstruktora szablonu variadic, na których brakowało argumentów szablonu, została błędnie dozwolona bez błędu. W programie Visual Studio 2017 w wersji 15.7 zgłaszany jest błąd kompilatora.

Poniższy przykład kodu w programie Visual Studio 2017 w wersji 15.7 wywołuje *błąd C2614: D\<int>: nielegalne inicjowanie elementu członkowskiego: 'B' nie jest podstawową ani członkową*

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

Aby naprawić błąd, zmień wyrażenie B() na B\<T>().

### <a name="constexpr-aggregate-initialization"></a>**inicjowanie** agregacji constexpr

Poprzednie wersje kompilatora C++ niepoprawnie obsługiwane **constexpr** ingregacji; zaakceptował nieprawidłowy kod, w którym lista agregacji init miała zbyt wiele elementów i wyprodukowała dla niego zły kodgen. Poniższy kod jest przykładem takiego kodu:

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

W programie Visual Studio 2017 w wersji 15.7 aktualizacja 3 i nowszych, poprzedni przykład teraz podnosi *C2078 zbyt wiele inicjatorów*. W poniższym przykładzie pokazano, jak naprawić kod. Podczas inicjowania `std::array` z zagnieżdżonych list nawiasów klamrowych, dać tablicy wewnętrznej usztywnionej listy własnych:

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

## <a name="bug-fixes-and-behavior-changes-in-158"></a><a name="update_158"></a>Poprawki błędów i zmiany zachowania w 15.8

Zmiany kompilatora w programie Visual Studio 2017 w wersji 15.8 należą do kategorii poprawek błędów i zmian zachowania i są wymienione poniżej:

### <a name="typename-on-unqualified-identifiers"></a>**nazwa typu** w identyfikatorach bez kwalifikacji

W [trybie /permissive-](../build/reference/permissive-standards-conformance.md) fałszywe słowa kluczowe**nazwy typu** na niekwalifikowanych identyfikatorach w definicjach szablonów aliasów nie są już akceptowane przez kompilator. Poniższy kod tworzy teraz C7511 *"T": po "typename" musi następować kwalifikowana nazwa:*

```cpp
template <typename T>
using  X = typename T;
```

Aby naprawić błąd, zmień drugi `using  X = T;`wiersz na .

### <a name="__declspec-on-right-side-of-alias-template-definitions"></a>`__declspec()`po prawej stronie definicji szablonów aliasów

[__declspec](../cpp/declspec.md) nie jest już dozwolone po prawej stronie definicji szablonu aliasu. Ten kod został wcześniej zaakceptowany, ale zignorowany przez kompilator i nigdy nie spowoduje ostrzeżenia o usunięciu, gdy alias był używany.

Standardowy atrybut [ \[ \[\] ](../cpp/attributes.md) C++ przestarzały może być używany zamiast tego i jest przestrzegany w programie Visual Studio 2017 w wersji 15.6. Poniższy kod generuje teraz błąd *składniowy C2760: nieoczekiwany token "__declspec", oczekiwany "specyfikator typu":*

```cpp
template <typename T>
using X = __declspec(deprecated("msg")) T;
```

Aby naprawić błąd, zmień na kod na następujący (z atrybutem umieszczonym przed '=' definicji aliasu):

```cpp
template <typename T>
using  X [[deprecated("msg")]] = T;
```

### <a name="two-phase-name-lookup-diagnostics"></a>Dwufazowa diagnostyka wyszukiwania nazw

Wyszukiwanie nazw dwufazowych wymaga, aby nazwy niesie zależne używane w treściach szablonów były widoczne dla szablonu w czasie definicji. Wcześniej kompilator Microsoft C++ pozostawiał nieoznakowaną nazwę, która nie była odkryta do czasu wystąpienia. Teraz wymaga, aby nazwy niesie zależne są powiązane w treści szablonu.

Jednym ze sposobów, w jaki to może się objawiać, jest wyszukiwanie w zależnych klasach podstawowych. Wcześniej kompilator zezwalał na używanie nazw, które są zdefiniowane w zależnych klasach podstawowych, ponieważ będą one wyszukane w czasie wystąpienia, gdy wszystkie typy są rozpoznawane. Teraz ten kod jest traktowany jako błąd. W takich przypadkach można wymusić zmienną, która ma być wyszukany w czasie wystąpienia, kwalifikując ją do `this->` typu klasy podstawowej lub w inny sposób uzależniając ją, na przykład przez dodanie wskaźnika.

W [trybie /permissive-](../build/reference/permissive-standards-conformance.md) następujący kod podnosi teraz C3861: *"base_value": nie znaleziono identyfikatora:*

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

Aby naprawić błąd, `return` zmień `return this->base_value;`instrukcję na .

**Uwaga:** W bibliotece Boost python przez długi czas istniało obejście specyficzne dla msvc dla deklaracji przesyłania dalej szablonu w [unwind_type.hpp](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp). W [trybie /permissive-](../build/reference/permissive-standards-conformance.md) począwszy od programu Visual Studio 2017 w wersji 15.8 (_MSC_VER=1915) kompilator MSVC poprawnie odnośnik nazwy zależnej od argumentów (ADL) i jest zgodny z innymi kompilatorami, co powoduje niepotrzebne obejście tego obejścia. Aby uniknąć błędu *C3861: "unwind_type": nie znaleziono identyfikatora*, zobacz [PR 229](https://github.com/boostorg/python/pull/229) w repozytorium Boost, aby zaktualizować plik nagłówka. Mamy już poprawione [vcpkg](../build/vcpkg.md) Boost pakiet, więc jeśli masz lub uaktualnić źródła Boost z vcpkg to nie trzeba stosować poprawkę oddzielnie.

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>przekazywanie deklaracji i definicji w przestrzeni nazw`std`

Standard C++ nie zezwala użytkownikowi na dodawanie deklaracji lub definicji `std`do przodu do obszaru nazw. Dodawanie deklaracji lub definicji `std` do obszaru nazw lub `std` do obszaru nazw w obszarze nazw powoduje teraz niezdefiniowane zachowanie.

W pewnym momencie w przyszłości firma Microsoft przeniesie lokalizację, w której zdefiniowano niektóre standardowe typy bibliotek. Ta zmiana spowoduje przerwanie istniejącego kodu, `std`który dodaje deklaracje do przodu do obszaru nazw . Nowe ostrzeżenie, C4643, pomaga zidentyfikować takie problemy ze źródłem. Ostrzeżenie jest włączone w **trybie /default** i jest domyślnie wyłączone. Będzie to miało wpływ na programy, które są kompilowane z **/Wall** lub **/WX**.

Poniższy kod teraz podnosi C4643: *Forward deklarując "wektor" w obszarze nazw std nie jest dozwolone przez C++ Standard*.

```cpp
namespace std {
    template<typename T> class vector;
}
```

Aby naprawić błąd, należy użyć **include** dyrektywy, a nie forward deklaracji:

```cpp
#include <vector>
```

### <a name="constructors-that-delegate-to-themselves"></a>Konstruktorzy, którzy delegują sobie

Standard C++ sugeruje, że kompilator powinien emitować diagnostykę, gdy konstruktor delegujący deleguje do siebie. Kompilator Microsoft C++ w [trybach /std:c++17](../build/reference/std-specify-language-standard-version.md) i [/std:c++najnowsze](../build/reference/std-specify-language-standard-version.md) tworzy teraz C7535: *'X::X': delegowanie konstruktora wywołuje się*.

Bez tego błędu następujący program skompiluje, ale wygeneruje nieskończoną pętlę:

```cpp
class X {
public:
    X(int, int);
    X(int v) : X(v){}
};
```

Aby uniknąć nieskończonej pętli, należy przekazać do innego konstruktora:

```cpp
class X {
public:

    X(int, int);
    X(int v) : X(v, 0) {}
};
```

### <a name="offsetof-with-constant-expressions"></a>`offsetof`ze stałymi wyrażeniami

[offsetof](../c-runtime-library/reference/offsetof-macro.md) został tradycyjnie zaimplementowany przy użyciu makra, które wymaga [reinterpret_cast](../cpp/reinterpret-cast-operator.md). To użycie jest niezgodne z prawem w kontekstach, które wymagają wyrażenia stałego, ale kompilator Microsoft C++ tradycyjnie zezwolił na to. Makro, `offsetof` które jest dostarczane jako część standardowej biblioteki poprawnie używa kompilatora wewnętrznego **(__builtin_offsetof),** ale wiele osób `offsetof`użyło sztuczki makro do zdefiniowania własnego .

W programie Visual Studio 2017 w wersji 15.8 `reinterpret_cast` kompilator ogranicza obszary, które te operatory mogą być wyświetlane w trybie domyślnym, aby pomóc kodowi dostosować się do standardowego zachowania języka C++. W [obszarze /permissive-](../build/reference/permissive-standards-conformance.md)ograniczenia są jeszcze bardziej rygorystyczne. Korzystanie z wyniku `offsetof` w miejscach, które wymagają wyrażeń stałych może spowodować kod, który wydaje ostrzeżenie C4644 *użycie wzorca offsetof oparte na makrach w wyrażeniach stałych jest niestandardowe; użyj offsetof zdefiniowane w bibliotece standardowej C++ zamiast* lub C2975 *nieprawidłowy argument szablonu, oczekiwane wyrażenie stałe w czasie kompilacji*.

Poniższy kod podnosi C4644 w **trybie /default** i **/std:c++17** i C2975 w trybie [/permissive-](../build/reference/permissive-standards-conformance.md)

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

Aby naprawić błąd, `offsetof` użyj \<zdefiniowanego przez cstddef>:

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

### <a name="cv-qualifiers-on-base-classes-subject-to-pack-expansion"></a>cv-kwalifikacje na zajęciach podstawowych z zastrzeżeniem rozszerzenia pakietu

Poprzednie wersje kompilatora Microsoft C++ nie wykryły, że klasa podstawowa miała kwalifikacje cv, jeśli również podlegała rozszerzeniu pakietu.

W programie Visual Studio 2017 w wersji 15.8 w trybie [/permissive-](../build/reference/permissive-standards-conformance.md) następujący kod podnosi C3770 *'const S': nie jest prawidłową klasą podstawową:*

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

W [trybie /permissive-](../build/reference/permissive-standards-conformance.md) kompilator wymaga teraz słowa kluczowego **szablonu,** aby poprzedzać nazwę szablonu, jeśli chodzi o zależny specyfikator zagnieżdżonej nazwy.

Następujący kod w [/permissive-](../build/reference/permissive-standards-conformance.md) mode teraz podnosi C7510: *"przykład": użycie nazwy szablonu zależnego musi być poprzedzone "szablon". uwaga: zobacz odwołanie do wystąpienia szablonu klasy "X\<T>" jest kompilowany:*

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

Aby naprawić błąd, dodaj słowo `Base<T>::example<int>();` kluczowe **szablonu** do instrukcji, jak pokazano w poniższym przykładzie:

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

## <a name="bug-fixes-and-behavior-changes-in-159"></a><a name="update_159"></a>Poprawki błędów i zmiany zachowania w 15.9

### <a name="identifiers-in-member-alias-templates"></a>Identyfikatory w szablonach aliasów członkowskich

Identyfikator używany w definicji szablonu aliasu elementu członkowskiego musi być zadeklarowany przed użyciem.

W poprzednich wersjach kompilatora dozwolony był następujący kod:

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

W programie Visual Studio 2017 w wersji 15.9 w trybie [/permissive-](../build/reference/permissive-standards-conformance.md) kompilator podnosi C3861: *"from_template": nie znaleziono identyfikatora*.

Aby naprawić błąd, `from_template` `from_template_t`zadeklaruj przed .

### <a name="modules-changes"></a>Zmiany modułów

W programie Visual Studio 2017 w wersji 15.9 kompilator podnosi C5050, gdy opcje wiersza polecenia dla modułów nie są spójne między strony tworzenia modułu i użycia modułu. W poniższym przykładzie istnieją dwa problemy:

- Po stronie zużycia (main.cpp) opcja **/EHsc** nie jest określona.

- Wersja C++ jest **/std:c++17** po stronie tworzenia i **/std:c++14** po stronie zużycia.

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

Kompilator podnosi C5050 dla obu tych przypadkach: *ostrzeżenie C5050: Możliwe niezgodne środowisko podczas importowania modułu "m": niedopasowane wersje C++.  Aktualna wersja modułu "201402" "201703"*.

Kompilator również podnosi C7536 za każdym razem, gdy plik .ifc został zmodyfikowany. Nagłówek interfejsu modułu zawiera skrót SHA2 zawartości poniżej. Podczas importowania plik .ifc jest mieszany w ten sam sposób, a następnie sprawdzany względem skrótu podanego w nagłówku. Jeśli te nie są zgodne, błąd C7536 jest wywoływany: *ifc nie powiodło się sprawdzanie integralności.  Oczekiwany SHA2: '66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6'*.

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>Częściowe zamawianie obejmujące aliasy i konteksty niewydedukowane

Implementacje różnią się w regułach częściowego zamawiania obejmujących aliasy w kontekstach niewydedukowanych. W poniższym przykładzie GCC i kompilator Microsoft C++ (w [trybie /permissive)](../build/reference/permissive-standards-conformance.md) zgłaszają błąd, podczas gdy Clang akceptuje kod.

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

W poprzednim przykładzie pojawia się C2668:

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

Rozbieżność implementacji wynika z regresji w standardowym brzmieniu języka C++. W rozwiązaniu do podstawowego wydania 2235 usunięto tekst, który pozwoliłby na zamówienie tych przeciążeń. Bieżący standard C++ nie zapewnia mechanizmu, aby częściowo uporządkować te funkcje, więc są one uważane za niejednoznaczne.

Aby obejść ten problem, zaleca się, aby nie polegać na częściowym zamawianiu w celu rozwiązania tego problemu. Zamiast tego należy użyć SFINAE, aby usunąć określone przeciążenia. W poniższym przykładzie używamy klasy `IsA` pomocnika, aby usunąć `Alloc` pierwsze przeciążenie, gdy jest `A`specjalizacja:

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

### <a name="illegal-expressions-and-non-literal-types-in-templated-function-definitions"></a>Nielegalne wyrażenia i typy inne niż literalne w definicjach funkcji szablonów

Niedozwolone wyrażenia i typy niesalnopłatne są teraz poprawnie diagnozowane w definicjach funkcji szablonów, które są jawnie wyspecjalizowane. Wcześniej takie błędy nie były emitowane dla definicji funkcji. Jednak nielegalne wyrażenie lub nie-dosłowny typ nadal zostałyby zdiagnozowane, jeśli są oceniane jako część wyrażenia stałego.

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

W programie Visual Studio 2017 w wersji 15.9 kod wywołuje ten błąd:

```Output
error C3615: constexpr function 'S<int>::f' cannot result in a constant expression.
note: failure was caused by call of undefined function or one not declared 'constexpr'
note: see usage of 'g'.
```

Aby uniknąć błędu, usuń kwalifikator **constexpr** z `f()`jawnego wystąpienia funkcji .

::: moniker-end

::: moniker range="vs-2015"

## <a name="c-conformance-improvements-in-visual-studio-2015"></a>Ulepszenia zgodności języka C++ w programie Visual Studio 2015

Aby uzyskać pełną listę ulepszeń zgodności w górę za pośrednictwem programu Visual Studio 2015 Update 3, zobacz [Visual C++ What's New 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Tabela zgodności języka języka Microsoft C++](../visual-cpp-language-conformance.md)
