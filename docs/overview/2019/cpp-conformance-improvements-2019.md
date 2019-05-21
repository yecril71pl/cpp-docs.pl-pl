---
title: Ulepszenia zgodności języka C++
ms.date: 05/16/2019
description: Microsoft C++ w programie Visual Studio 2019 r jest postępować w kierunku pełną zgodność ze standardem 20 języka C ++.
ms.technology: cpp-language
author: mikeblome
ms.author: mblome
ms.openlocfilehash: e9bc86683ec89858d0b6cb39dcc6a65cf4eb05b2
ms.sourcegitcommit: 61121faf879cc581a4d39e4baccabf7cf1f673a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934129"
---
# <a name="c-conformance-improvements-in-visual-studio-2019-rtw-and-version-161improvements161"></a>C++ulepszenia zgodności w programie Visual Studio RTW 2019 r i wersji [16.1](#improvements_161)

## <a name="improvements-in-visual-studio-2019-rtw"></a>Ulepszenia programu Visual Studio RTW 2019 r

Visual Studio 2019 RTW zawiera następujące ulepszenia zgodności, poprawki i zmiany zachowania w kompilatorze Microsoft C++ (MSVC).

**Uwaga:** C ++ 20 funkcje zostaną udostępnione w `/std:c++latest` tryb zakończeniem 20 implementacji języka C ++ dla kompilatora i technologii IntelliSense. W tym czasie `/std:c++20` tryb kompilatora zostaną wprowadzone.

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Moduły ulepszoną obsługę wykrywania błędów i szablony

Moduły są teraz oficjalnie w języku C ++ 20 standardowych. Ulepszona obsługa został dodany w programie Visual Studio 2017 w wersji 15.9. Aby uzyskać więcej informacji, zobacz [lepsze wykrywanie pomocy technicznej i błąd szablonu w moduły języka C++ w wersji 15.9 2017 MSVC](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/).

### <a name="modified-specification-of-aggregate-type"></a>Zmodyfikowane Specyfikacja typu agregacji

Specyfikacja typu agregacji został zmieniony w języku C ++ 20 (zobacz [ze Stanów Zjednoczonych zabraniają agregacji za pomocą zgłoszonych przez użytkownika konstruktorów](http://wg21.link/p1008r1)). W programie Visual Studio 2019 r w obszarze `/std:c++latest`, klasy za pomocą konstruktora wszystkie zgłoszone przez użytkownika (np. w tym konstruktorze zadeklarowana `= default` lub `= delete`) nie jest agregacją. Wcześniej tylko dostarczone przez użytkownika konstruktorów spowoduje zdyskwalifikowany klasy miałyby agregacji. Ta zmiana powoduje umieszczenie dodatkowe ograniczenia dotyczące jak typy takie mogą być zainicjowane.

Poniższy kod kompiluje bez błędów w programie Visual Studio 2017, ale zgłasza błędy C2280 i C2440 w Visual Studio 2019 r, w obszarze `/std:c++latest`:

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

### <a name="partial-support-for-operator-"></a>Częściowa Obsługa <> = — operator

[P0515R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0515r3.pdf) wprowadza C ++ 20 `<=>` operator porównania trzystopniowo, znany także jako "pojazdu kosmicznego operatora". Visual Studio 2019 r w `/std:c++latest` tryb wprowadza częściową obsługę dla operatora, tworząc błędy składni, która jest teraz niedozwolona. Na przykład, poniższy kod kompiluje bez błędów w programie Visual Studio 2017, ale zgłasza kilka błędów w Visual Studio 2019 r, w obszarze `/std:c++latest`:

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

Aby uniknąć błędów, wstawić odstęp naruszającym wierszem przed nawiasie zamykającym: `U<&S::operator<= > u;`.

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>Odwołania do typów z niezgodnymi kwalifikatory cv

MSVC umożliwiało powiązanie bezpośrednie odwołanie z typu z niezgodnymi kwalifikatory cv poniżej najwyższego poziomu. Może to zapewnić, modyfikacji danych funkcji rzekomo const określonych przez odwołanie, a kompilator utworzy teraz tymczasowy zgodnie z wymaganiami standardu. W programie Visual Studio 2017 poniższy kod kompiluje się bez ostrzeżeń. W programie Visual Studio 2019 r, kompilator generuje *ostrzeżenie C4172: \<func: nr 1 "?PData@X @@QBEABQBXXZ"> zwracanie adresu lokalnej zmiennej lub tymczasowej*.

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
### <a name="reinterpretcast-from-an-overloaded-function"></a>`reinterpret_cast` z przeciążonej funkcji

Argument `reinterpret_cast` nie jest jednym z kontekstów, w których adres przeciążonej funkcji jest dozwolone. Poniższy kod kompiluje się bez błędów w programie Visual Studio 2017, ale w programie Visual Studio 2019 zgłasza *C2440: nie można konwertować z "przeciążonych funkcji" do "fp"*:

```cpp
int f(int) { return 1; }
int f(float) { return .1f; }
using fp = int(*)(int);

int main()
{
    fp r = reinterpret_cast<fp>(&f);
}
```

Aby uniknąć tego błędu, należy użyć rzutowania dozwolone dla tego scenariusza:

```cpp
int f(int);
int f(float);
using fp = int(*)(int);

int main()
{
    fp r = static_cast<fp>(&f); // or just &f;
}
```

### <a name="lambda-closures"></a>Lambda zamknięcia

W języku C ++ 14 typy zamknięcia lambda nie są literału. Podstawowy konsekwencji tej zasady jest wyrażenia lambda nie może być przypisany do `constexpr` zmiennej. Poniższy kod kompiluje bez błędów w programie Visual Studio 2017, ale w Visual Studio 2019 go zgłasza *C2127: "l": niedozwolone inicjowanie elementu entity "constexpr" with — wyrażenie niestałe* :

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

Aby uniknąć tego błędu, albo usuń `constexpr` kwalifikator; w przeciwnym razie Zmień tryb zgodności do `/std:c++17`.

### <a name="stdcreatedirectory-failure-codes"></a>kody błędów STD::create_directory

Zaimplementowane [P1164](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1164r1.pdf) z języka C ++ 20 bezwarunkowo. Spowoduje to zmianę `std::create_directory` do sprawdzenia, czy element docelowy został już katalog, w przypadku niepowodzenia. Wcześniej wszystkie błędy typu ERROR_ALREADY_EXISTS zostały przekształcone kody utworzone sukces — ale katalogu — nie.

### <a name="operatorstdostream-nullptrt"></a>Operator < <(std::ostream, nullptr_t)

Na [LWG 2221](https://cplusplus.github.io/LWG/issue2221)dodano `operator<<(std::ostream, nullptr_t)` do zapisywania nullptrs strumieni. 

### <a name="additional-parallel-algorithms"></a>Dodatkowe algorytmy równoległe

Nowe wersje równoległe `is_sorted`, `is_sorted_until`, `is_partitioned`, `set_difference`, `set_intersection`, `is_heap`, i `is_heap_until`.

### <a name="atomic-initialization"></a>Inicjowanie Atomic

[P0883 "Ustalanie atomic inicjowania"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0883r1.pdf) zmiany `std::atomic` do inicjowania wartości zawartej T, a nie domyślnej — jego inicjowania. Poprawka jest włączona, gdy wewnątrz platformy Clang/LLVM przy użyciu biblioteki standardowej firmy Microsoft. Jest obecnie wyłączona dla programu Microsoft C++ kompilatora obejścia dla błędu podczas przetwarzania wyrażenia constexpr.

### <a name="removecvref-and-removecvreft"></a>remove_cvref i remove_cvref_t

Zaimplementowane `remove_cvref` i `remove_cvref_t` typ cechy z [P0550](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf). Stałości odwołań i stałych nietrwałych kwalifikacji je usunąć z typem bez zanikające funkcje i tablic do wskaźników (w przeciwieństwie do `std::decay` i `std::decay_t`).

### <a name="feature-test-macros"></a>Makra Feature-test

[P0941R2 — makra feature-test](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html) zostanie zakończone, z obsługą `__has_cpp_attribute`. Makra Feature-test są obsługiwane we wszystkich trybach pracy standardowych.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Stanów Zjednoczonych zabraniają agregacji za pomocą zgłoszonych przez użytkownika konstruktorów

[C ++ 20 P1008R1 - zabronienia agregacji za pomocą zgłoszonych przez użytkownika konstruktorów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf) zostało zakończone.

## <a name="improvements_161"></a> Ulepszenia programu Visual Studio 2019 wersji 16.1

### <a name="char8t"></a>char8_t

[P0482r6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html). C ++ 20 dodaje nowy typ znaku, który jest używany do reprezentowania jednostek kodu UTF-8. literał ciągu U8 w języku C ++ 20 mają typ `const char8_t[N]` zamiast `const char[N]`, które miało miejsce wcześniej. Podobne zmiany zostały zaproponowane dla przez Standard C w [N2231](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2231.htm). Sugestie dotyczące korygowania zgodności z poprzednimi wersjami char8_t są podane w [P1423r0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1423r0.html). Microsoft C++ kompilatora alokowanej char8_t w Visual Studio 2019 wersji 16.1 po określeniu **/Zc:char8_t** — opcja kompilatora. W przyszłości, będzie ono obsługiwane za pomocą [/STD: c ++ najnowsze](../../build/reference/std-specify-language-standard-version.md), której można przywrócić C ++ 17 zachowanie za pośrednictwem **/Zc:char8_t-**. Agenci EDG kompilatora, który obsługuje funkcję IntelliSense nie obsługuje jeszcze, więc zostanie wyświetlony fałszywe błędy tylko do funkcji IntelliSense, które nie wpływają one na rzeczywistych kompilacji.

#### <a name="example"></a>Przykład

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtypeidentity-metafunction-and-stdidentity-function-object"></a>Obiekt STD::type_identity metafunction i std::identity — funkcja

[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf). Przestarzała `std::identity` rozszerzenie szablonu klasy ma został usunięty i zastąpiony parametrem 20 C ++ `std::type_identity` metafunction i `std::identity` obiektu funkcyjnego. Oba są dostępne tylko w ramach [/STD: c ++ najnowsze](../../build/reference/std-specify-language-standard-version.md). 

Poniższy przykład generuje ostrzeżenie C4996 dla wycofywania `std::identity` (zdefiniowane w \<type_traits >) w programie Visual Studio 2017: 

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

Poniższy przykład pokazuje, jak korzystać z nowych `std::identity` (zdefiniowane w \<funkcjonalności >) wraz z nowym `std::type_identity`:

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>Sprawdzanie składni dla ogólnych wyrażeń lambda

Nowy procesor lambda Włącza tryb zgodności niektóre składni zaewidencjonuje ogólnych wyrażeń lambda, w obszarze [/STD: c ++ najnowsze](../../build/reference/std-specify-language-standard-version.md) lub inny tryb języka przy użyciu **/ eksperymentalne: newLambdaProcessor**. 

W programie Visual Studio 2017, ten kod kompiluje się bez ostrzeżeń, ale w programie Visual Studio 2019 generuje błąd *C2760 błąd składniowy: nieoczekiwany token "\<identyfikator expr >", oczekiwano "identyfikator wyrażenia"*:

```cpp
void f() {
    auto a = [](auto arg) {
        decltype(arg)::Type t;
    };
}
```

Poniższy przykład przedstawia poprawnej składni, teraz są wymuszane przez kompilator:

```cpp
void f() {
    auto a = [](auto arg) {
        typename decltype(arg)::Type t;
    };
}
```

### <a name="argument-dependent-lookup-for-function-calls"></a>Wyszukiwanie zależne od argumentów dla wywołania funkcji

[P0846R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0846r0.html) (C ++ 20) zwiększyć możliwości można znaleźć szablony funkcji za pomocą wyszukiwania zależnego od argumentów dla wyrażenia wywołania funkcji za pomocą jawnych argumentów szablonów. Wymaga **/STD: c ++ najnowsze**.

### <a name="designated-initialization"></a>Inicjowanie wyznaczonym

[P0329R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf) (C ++ 20) zezwala na inicjowanie wyznaczone określeni członkowie do wybrania podczas inicjowania agregacji za pomocą `Type t { .member = expr }` składni. Wymaga **/STD: c ++ najnowsze**.

### <a name="new-and-updated-standard-library-functions-c20"></a>Nowe i zaktualizowane funkcje biblioteki standardowej (C ++ 20)

- `starts_with()` i `ends_with()` dla `basic_string` i `basic_string_view`.
- `contains()` dla kontenerów asocjacyjnych.
- `remove()`, `remove_if()`, i `unique()` dla` list` i `forward_list` teraz zwracają `size_type`.
- `shift_left()` i `shift_right()` dodane do \<algorytm >.

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019-rtw"></a>Poprawki i zmiany zachowania w programie Visual Studio RTW 2019 r

### <a name="correct-diagnostics-for-basicstring-range-constructor"></a>Poprawne diagnostyki basic_string zakresu konstruktora

W programie Visual Studio 2019 r `basic_string` Konstruktor zakresu nie jest już pomija diagnostyki kompilatora przy użyciu `static_cast`. Poniższy kod kompiluje się bez ostrzeżeń w programie Visual Studio 2017, pomimo możliwej utracie danych z `wchar_t` do `char` podczas inicjowania `out`:

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

2019 usługi Visual Studio niepoprawnie zgłasza *C4244: "argument": konwersja z "wchar_t" na "const _Elem", możliwa utrata danych*. Aby uniknąć ostrzeżenia, można zainicjować std::string, jak pokazano w poniższym przykładzie:

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>Nieprawidłowe wywołania += i-= w ramach/CLR lub /ZW teraz są poprawnie wykrywane

Usterka została wprowadzona w Visual Studio 2017, który spowodował kompilatorowi ignorowanie błędów i wygenerować żadnego kodu dla nieprawidłowych wywołań += i-= w obszarze dyskretne `/clr` lub `/ZW`. Poniższy kod kompiluje się bez błędów w programie Visual Studio 2017, ale w Visual Studio 2019 r zgłasza poprawnie *błąd C2845: "System::String ^": arytmetyka wskaźnika nie jest dozwolona dla tego typu*:

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

Aby uniknąć tego błędu, w tym przykładzie, należy użyć operatora przy użyciu metody ToString(): `s += E::e.ToString();`.

### <a name="initializers-for-inline-static-data-members"></a>Inicjatory dla elementów członkowskich danych statycznych w tekście

Nieprawidłowy element członkowski, który uzyskuje dostęp w ramach `inline` i `static constexpr` inicjatory teraz są poprawnie wykrywane. Poniższy przykład skompiluje się bez błędów w programie Visual Studio 2017, ale w Visual Studio 2019 r, w obszarze `/std:c++17` tryb zgłasza *C2248 błąd: nie dostępu prywatnego elementu członkowskiego jest zadeklarowana w klasie "X"*.

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

Aby uniknąć tego błędu, należy zadeklarować element członkowski `X::c` jako chronione:

```cpp
struct X
{
    protected:
        static inline const int c = 1000;
};
```

### <a name="c4800-reinstated"></a>C4800 przywrócone

MSVC umożliwia wydajność ostrzeżenie C4800 dotyczące niejawnej konwersji na bool, który był zbyt hałas i insuppressible, prowadzące z nami, aby usunąć go w programie Visual Studio 2017. Jednak z cyklem Visual Studio 2017 mamy mnóstwo informacji zwrotnych na przydatne w przypadkach, którego został on rozwiązywania. Możemy przywrócić w Visual Studio 2019 starannie dopasowane C4800 wraz z jego C4165 towarzyszącego, które można łatwo pominąć za pomocą jawnego rzutowania lub porównanie 0 odpowiedniego typu. C4800 jest to ostrzeżenie wyłączone domyślnie poziom 4, a C4165 jest to ostrzeżenie wyłączone domyślnie poziom 3. Oba są wykrywalni przy użyciu `/Wall` — opcja kompilatora.

Poniższy przykład wywołuje C4800 i C4165 w obszarze `/Wall`:

```cpp
bool test(IUnknown* p)
{
    bool valid = p; // warning C4800: Implicit conversion from 'IUnknown*' to bool. Possible information loss
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return hr; // warning C4165: 'HRESULT' is being converted to 'bool'; are you sure this is what you want?
}
```

W celu uniknięcia ostrzeżeń w poprzednim przykładzie, można napisać kod następująco:

```cpp
bool test(IUnknown* p)
{
    bool valid = p != nullptr; // OK
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return SUCCEEDED(hr);  // OK
}
```

### <a name="local-class-member-function-doesnt-have-a-body"></a>Funkcja składowa klasy lokalnej nie ma on treści

In Visual Studio 2017, *C4822: Funkcja składowa klasy lokalnej nie ma on treści* jest wywoływane tylko wtedy, gdy — opcja kompilatora `/w14822` jest jawnie ustawiona; nie jest wyświetlana przy użyciu `/Wall`. W programie Visual Studio 2019 r, C4822 jest ostrzeżenie wyłączone domyślnie, co sprawia, że wykrywalne w obszarze `/Wall` bez konieczności ustawiania `/w14822` jawnie.

```cpp
void foo()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>Funkcja treści szablonu zawierającego constexpr, jeśli instrukcji

Gdy ciało funkcji jest szablon zawierający `if constexpr` instrukcje mają też `/permissive-` włączone kontrole związane z analizy. Na przykład w programie Visual Studio 2017, poniższy kod tworzy C*7510: "Type": Użyj nazwy zależne typu musi być poprzedzona znakiem "typename"* tylko wtedy, gdy `/permissive-` opcja nie jest ustawiona. W programie Visual Studio 2019 ten sam kod zgłasza błędy czy `/permissive-` ustawiono opcję:

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

Aby uniknąć tego błędu, należy dodać `typename` — słowo kluczowe do deklaracji `a`: `typename T::Type a;`.

### <a name="inline-assembly-code-is-not-supported-in-a-lambda-expression"></a>Wbudowany kod zestawu nie jest obsługiwana w wyrażeniu lambda

Zespołu Visual C++ niedawno został poinformowany o problem zabezpieczeń, w którym stosowania asemblera wbudowanego w obrębie wyrażenia lambda może spowodować uszkodzenie "ebp" (Zarejestruj adres zwrotny) w czasie wykonywania. Osoba atakująca może być w stanie wykorzystać ten scenariusz. Ze względu na charakter problem fakt, że asembler wbudowany jest obsługiwana tylko na x86 i niską interakcję asemblera wbudowanego z pozostałą częścią kompilatora, który został uznało, że jest najbezpieczniejszym rozwiązaniem tego problemu nie zezwalaj na asemblera wbudowanego w obrębie wyrażenia lambda wyrażenie.

Uwaga: jedynym stosowania asemblera wbudowanego w wyrażeniu lambda, które wystąpiły w symbolami był korzystanie z celem było przechwycić adres zwrotny. W tym scenariuszu można przechwycić adres zwrotny na wszystkich platformach przy użyciu wewnętrzne polecenie kompilatora `_ReturnAddress()`.

Poniższy kod generuje *C7552: wbudowany asembler nie jest obsługiwana w wyrażenia lambda* w obu 15.9 2017 usługi Visual Studio i Visual Studio 2019 r.:

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

Aby uniknąć tego błędu, Przenieś kod zestawu do funkcji o nazwie, jak pokazano w poniższym przykładzie:

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

### <a name="iterator-debugging-and-stdmoveiterator"></a>Debugowania iteratora i std::move_iterator

Debugowania funkcji iteratora ma zostały prowadzone do odkodowania prawidłowo `std::move_iterator`. Na przykład `std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` teraz mogą angażować `memcpy` szybkiej ścieżki.

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Poprawki dotyczące \<xkeycheck.h > wymuszania — słowo kluczowe

Biblioteki standardowej ized — makro — słowo kluczowe wymuszania \<xkeycheck.h > został naprawiony, aby emitować wykryto zamiast ogólnego komunikatu — słowo kluczowe rzeczywistego problemu. Ponadto obsługuje C ++ 20 słów kluczowych i pozwala uniknąć oszukiwanie informujący o tym, że losowe słowa kluczowe są makra funkcji IntelliSense.

### <a name="allocator-types-un-deprecated"></a>Typy alokatora, usuwając przestarzałe

`std::allocator<void>`, `std::allocator::size_type`, i `std::allocator::difference_type` zostały usuwając przestarzały.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Poprawić ostrzeżenie zawężaniu zakresu konwersje, ciąg

Fałszywe `static_cast` nie zostanie wywołana dla przez standard, które przypadkowo pominięte C4244 zawężanie ostrzeżeń został usunięty z std::string. Próba wywołania `std::string::string(const wchar_t*, const wchar_t*)` prawidłowo teraz wyemitują *C4244 "zawężanie wchar_t do znaku".*

### <a name="various-filesystem-correctness-fixes"></a>Różne \<filesystem > poprawki do poprawności

- Naprawiono `std::filesystem::last_write_time` kończy się niepowodzeniem podczas próby zmiany katalogu użytkownika ostatni czas zapisu.
- `std::filesystem::directory_entry` Konstruktor przechowuje teraz zakończonych niepowodzeniem wyników, zamiast zgłaszać wyjątek, jeśli podano ścieżkę docelową nieistniejącej.
- `std::filesystem::create_directory` Wersji parametru 2 została zmieniona na wywołuje wersji parametr 1, jako bazowego `CreateDirectoryExW` wykona funkcja `copy_symlink` kiedy existing_p był Link symboliczny.
- `std::filesystem::directory_iterator` nie kończy się niepowodzeniem po napotkaniu przerwany Link symboliczny.
- `std::filesystem::space` teraz akceptuje ścieżki względne.
- `std::filesystem::path::lexically_relative` nie jest już zastanawia końcowe ukośniki, zgłaszane jako [LWG 3096](https://cplusplus.github.io/LWG/issue3096).
- Pracował wokół `CreateSymbolicLinkW` odrzuca ścieżki z ukośnikami w `std::filesystem::create_symlink`.
- Pracował wokół trybie usuwania POSIX `delete` funkcji istniejące w systemie Windows 10 LTSB 1609, ale bez faktycznego zdolność usuwania plików.
- `std::boyer_moore_searcher` i `std::boyer_moore_horspool_searcher`przez konstruktory kopiujące i kopiujące operatory przypisania faktycznie kopiować dane.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Algorytmy równoległe w systemie Windows 8 lub nowszy

Biblioteka algorytmów równoległych prawidłowo używa teraz rzeczywiste `WaitOnAddress` rodziny, w systemie Windows 8 lub nowszy, zamiast zawsze przy użyciu Windows 7 i starszych wersji fałszywe.

### <a name="stdsystemcategorymessage-whitespace"></a>STD::system_category::Message() białe znaki

`std::system_category::message()` teraz przycina końcowe białe znaki z zwracanego komunikatu.

### <a name="stdlinearcongruentialengine-divide-by-zero"></a>STD::linear_congruential_engine dzielenie przez zero

Niektóre warunki, które mogą być przyczyną `std::linear_congruential_engine` do wyzwolenia zostały naprawione dzielenie przez 0.

### <a name="fixes-for-iterator-unwrapping"></a>Poprawki dla iteratora rozpakowanie

Iterator rozpakowanie maszyny najpierw została udostępniona integracji programisty niezwiązanych z użytkownikiem w Visual Studio 2017 15.8 (zgodnie z opisem w https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/ ) nie jest już dekoduje Iteratory pochodną iteratorów standardowej biblioteki. Na przykład użytkownik, który pochodzi od klasy `std::vector<int>::iterator` i próbuje teraz dostosować zachowanie pobiera zachowanie wskaźnika, a nie ich niestandardowe zachowanie podczas wywoływania algorytmami standardowej biblioteki.
Funkcja rezerwy nieuporządkowaną kontenera teraz faktycznie rezerwy dla elementów N, zgodnie z opisem w [LWG 2156](https://cplusplus.github.io/LWG/issue2156).

### <a name="time-handling"></a>Czas obsługi

- Wcześniej, niektóre wartości czasu, które zostały przekazane do biblioteki współbieżności spowodowałoby przepełnienie, na przykład `condition_variable::wait_for(seconds::max())`. Te przepełnienia rozwiązano problem, zmienić zachowanie na pozornie losowe cyklu 29 dni (po milisekund uint32_t zaakceptowane przez podstawowych interfejsów API systemu Win32 nastąpiło przepełnienie).

- <ctime> Nagłówka teraz poprawnie deklaruje timespec i timespec_get w przestrzeni nazw std oprócz stwierdzenie ich w globalnej przestrzeni nazw.

### <a name="various-fixes-for-containers"></a>Różne poprawki dla kontenerów

- Wiele funkcji pojemnika wewnętrznego biblioteki standardowej wprowadzono prywatny, aby uzyskać lepsze działanie funkcji IntelliSense. W kolejnych wersjach MSVC powinny dodatkowe poprawki, aby oznaczyć elementy członkowskie jako prywatne.

- Wyjątek bezpieczeństwa poprawność problemów, na którym kontenerów opartych na węźle, takich jak `list`, `map`, i `unordered_map` może ulec uszkodzeniu zostały rozwiązane. Podczas `propagate_on_container_copy_assignment` lub `propagate_on_container_move_assignment` operację ponownego przypisania, firma Microsoft będzie kontenera wartownik węzeł za darmo dzięki usłudze stare alokatora, wykonaj przypisanie POCCA/POCMA za pośrednictwem stare alokatora, a następnie spróbuj uzyskać węzła wartownik z nowego programu przydzielania. Jeśli ten przydział nie powiodła się, kontener jest uszkodzony i nawet nie może zostać zniszczone jako będąca właścicielem jest węzłem wartownik niezmiennej strukturze twardych danych. Ten problem został rozwiązany przydzielić nowego węzła wartownik z kontenera źródłowego alokatora przed niszczenie istniejący węzeł wskaźnikowych.

- Kontenery zostały rozwiązane do buforów zawsze kopiowania/przenoszenia/wymiany zgodnie z opisem w `propagate_on_container_copy_assignment`, `propagate_on_container_move_assignment`, i `propagate_on_container_swap`, nawet w przypadku puli buforów zadeklarowana `is_always_equal`.

- Dodano przeciążenia dla kontenera, scalanie i wyodrębnić funkcji elementów członkowskich, które akceptują rvalue kontenerów na [P0083 "Łączenie map i zestawów"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)

### <a name="stdbasicistreamread-processing-of-rn--n"></a>Przetwarzanie STD::basic_istream::Read \r\n = > \n

`std::basic_istream::read` Naprawiono nie zapis do części dostarczony bufor tymczasowo jako część \r\n = > \n przetwarzania. Dzięki temu Zwolnij trochę zaletą wydajności uzyskane w Visual Studio 2017 15.8 dla odczytów przekracza 4K rozmiar, ale ulepszenia wydajności z unikanie 3 wywołania wirtualnego w ciągu znaków są nadal dostępne.

### <a name="stdbitset-constructor"></a>Konstruktor STD::bitset

`std::bitset`jego Konstruktor nie jest już odczytuje te i wyzerowania w odwrotnej kolejności dla dużych bitsets.

### <a name="stdpairoperator-regression"></a>STD::Pair::operator = regresji

Naprawiono regresję w `std::pair`użytkownika operator przypisania wprowadzone podczas implementowania [LWG 2729 "Brak SFINAE na std::pair::operator =";](https://cplusplus.github.io/LWG/issue2729). Teraz poprawnie przyjmuje typy możliwe do przekonwertowania na `std::pair` ponownie.

### <a name="non-deduced-contexts-for-addconstt"></a>Określić inne niż konteksty dla add_const_t

Usunięto usterkę cech typu pomocniczych, gdzie `add_const_t` i pokrewnych funkcji powinna być-wywnioskować kontekstu. Innymi słowy `add_const_t` powinien być aliasem `typename add_const<T>::type`, a nie `const T`.

## <a name="see-also"></a>Zobacz także

[What's new in Visual Studio 2019 r.](../what-s-new-for-visual-cpp-in-visual-studio.md)