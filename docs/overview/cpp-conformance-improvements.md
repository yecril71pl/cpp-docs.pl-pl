---
title: Ulepszenia zgodności języka C++
ms.date: 06/14/2019
description: Microsoft C++ w programie Visual Studio jest postępować w kierunku pełną zgodność ze standardem 20 języka C ++.
ms.technology: cpp-language
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 1652c7ab9a48de65b32123b34c3231a0b06a410a
ms.sourcegitcommit: 0ad35b26e405bbde17dc0bd0141e72f78f0a38fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67194769"
---
# <a name="c-conformance-improvements-in-visual-studio"></a>Ulepszenia zgodności języka C++ w programie Visual Studio

Microsoft C++ sprawia, że zgodność ulepszeń i poprawek błędów w każdej wersji. W tym artykule wymieniono usprawnienia w wersji głównych, następnie według wersji. Zawiera również listę głównych poprawki w wersji. Aby przejść bezpośrednio do zmiany dla określonej wersji, należy użyć **w tym artykule** listy.

::: moniker range=">=vs-2019"

## <a name="improvements_160"></a> Ulepszenia programu Visual Studio RTW 2019 r (wersja 16.0)

Visual Studio 2019 RTW zawiera następujące ulepszenia zgodności, poprawki i zmiany zachowania w programie Microsoft C++ kompilatora (MSVC).

**Uwaga:** C ++ 20 funkcje zostaną udostępnione w `/std:c++latest` tryb zakończeniem 20 implementacji języka C ++ dla kompilatora i technologii IntelliSense. W tym czasie `/std:c++20` tryb kompilatora zostaną wprowadzone.

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Moduły ulepszoną obsługę wykrywania błędów i szablony

Moduły są teraz oficjalnie w języku C ++ 20 standardowych. Ulepszona obsługa został dodany w programie Visual Studio 2017 w wersji 15.9. Aby uzyskać więcej informacji, zobacz [lepsze wykrywanie pomocy technicznej i błąd szablonu w moduły języka C++ w wersji 15.9 2017 MSVC](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/).

### <a name="modified-specification-of-aggregate-type"></a>Zmodyfikowane Specyfikacja typu agregacji

Specyfikacja typu agregacji został zmieniony w języku C ++ 20 (zobacz [ze Stanów Zjednoczonych zabraniają agregacji za pomocą zgłoszonych przez użytkownika konstruktorów](https://wg21.link/p1008r1)). W programie Visual Studio 2019 r w obszarze `/std:c++latest`, klasy za pomocą konstruktora wszystkie zgłoszone przez użytkownika (na przykład, w tym konstruktorze zadeklarowana `= default` lub `= delete`) nie jest agregacją. Wcześniej tylko dostarczone przez użytkownika konstruktorów spowoduje zdyskwalifikowany klasy miałyby agregacji. Ta zmiana powoduje umieszczenie dodatkowe ograniczenia dotyczące jak typy takie mogą być zainicjowane.

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

### <a name="partial-support-for-operator-"></a>Częściowa Obsługa `operator <=>`

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

Aby uniknąć błędów, wstawić odstęp naruszającym wierszem przed zamykającego nawiasu ostrego: `U<&S::operator<= > u;`.

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>Odwołania do typów z niezgodnymi kwalifikatory cv

Wcześniej MSVC dozwolone powiązanie bezpośrednie odwołanie z typu z niezgodnymi kwalifikatory cv poniżej najwyższego poziomu. To powiązanie umożliwia modyfikowanie funkcji rzekomo const danych określonych przez odwołanie. Kompilator jest teraz tworzy tymczasową, zgodnie z wymogami normy. W programie Visual Studio 2017 poniższy kod kompiluje się bez ostrzeżeń. W programie Visual Studio 2019 r, kompilator generuje *ostrzeżenie C4172: \<func: nr 1 "?PData@X @@QBEABQBXXZ"> zwracanie adresu lokalnej zmiennej lub tymczasowej*.

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

Argument `reinterpret_cast` nie jest jednym z kontekstów, w których adres przeciążonej funkcji jest dozwolone. Poniższy kod kompiluje się bez błędów w programie Visual Studio 2017, ale w programie Visual Studio 2019 zgłasza *C2440: nie można konwertować z "przeciążonych funkcji" do "fp"* :

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

W języku C ++ 14 typy zamknięcia lambda nie są literały. Podstawowy konsekwencji tej zasady jest wyrażenia lambda nie może być przypisany do `constexpr` zmiennej. Poniższy kod kompiluje się bez błędów w programie Visual Studio 2017, ale w programie Visual Studio 2019 zgłasza *C2127: "l": niedozwolone inicjowanie elementu entity "constexpr" with — wyrażenie niestałe*:

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

Aby uniknąć tego błędu, albo usuń `constexpr` kwalifikator; w przeciwnym razie Zmień tryb zgodności do `/std:c++17`.

### <a name="stdcreatedirectory-failure-codes"></a>`std::create_directory` Kody błędów

Zaimplementowane [P1164](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1164r1.pdf) z języka C ++ 20 bezwarunkowo. Spowoduje to zmianę `std::create_directory` do sprawdzenia, czy element docelowy został już katalog, w przypadku niepowodzenia. Wcześniej wszystkie błędy typu ERROR_ALREADY_EXISTS zostały przekształcone kody utworzone sukces — ale katalogu — nie.

### `operator<<(std::ostream, nullptr_t)`

Na [LWG 2221](https://cplusplus.github.io/LWG/issue2221)dodano `operator<<(std::ostream, nullptr_t)` do zapisywania nullptrs strumieni.

### <a name="additional-parallel-algorithms"></a>Dodatkowe algorytmy równoległe

Nowe wersje równoległe `is_sorted`, `is_sorted_until`, `is_partitioned`, `set_difference`, `set_intersection`, `is_heap`, i `is_heap_until`.

### <a name="atomic-initialization"></a>Inicjowanie Atomic

[P0883 "Ustalanie atomic inicjowania"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0883r1.pdf) zmiany `std::atomic` do inicjowania wartości zawartej T, a nie domyślnej — jego inicjowania. Poprawka jest włączona, gdy wewnątrz platformy Clang/LLVM przy użyciu biblioteki standardowej firmy Microsoft. Jest obecnie wyłączona dla programu Microsoft C++ kompilatora, jako obejście dla usterki w `constexpr` przetwarzania.

### <a name="removecvref-and-removecvreft"></a>`remove_cvref` i `remove_cvref_t`

Zaimplementowane `remove_cvref` i `remove_cvref_t` typ cechy z [P0550](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf). Stałości odwołań i stałych nietrwałych kwalifikacji je usunąć z typem bez zanikające funkcje i tablic do wskaźników (w przeciwieństwie do `std::decay` i `std::decay_t`).

### <a name="feature-test-macros"></a>Makra Feature-test

[P0941R2 — makra feature-test](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html) zostanie zakończone, z obsługą `__has_cpp_attribute`. Makra Feature-test są obsługiwane we wszystkich trybach pracy standardowych.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Stanów Zjednoczonych zabraniają agregacji za pomocą zgłoszonych przez użytkownika konstruktorów

[C ++ 20 P1008R1 - zabronienia agregacji za pomocą zgłoszonych przez użytkownika konstruktorów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf) zostało zakończone.

## <a name="improvements_161"></a> Ulepszenia programu Visual Studio 2019 wersji 16.1

### <a name="char8t"></a>char8_t

[P0482r6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html). C ++ 20 dodaje nowy typ znaku, który jest używany do reprezentowania jednostek kodu UTF-8. `u8` Literały ciągu języka C ++ 20 mają typ `const char8_t[N]` zamiast `const char[N]`, które miało miejsce wcześniej. Podobne zmiany zostały zaproponowane dla standardu C [N2231](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2231.htm). Sugestie dotyczące `char8_t` korygowania zgodności z poprzednimi wersjami znajdują się w [P1423r0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1423r0.html). Microsoft C++ kompilator dodaje obsługę `char8_t` w Visual Studio 2019 wersji 16.1 po określeniu **/Zc:char8_t** — opcja kompilatora. W przyszłości, będzie ono obsługiwane za pomocą [/STD: c ++ najnowsze](../build/reference/std-specify-language-standard-version.md), której można przywrócić C ++ 17 zachowanie za pośrednictwem **/Zc:char8_t-** . Kompilator agenci EDG, która napędza IntelliSense jeszcze go nie obsługuje, więc zobaczysz fałszywe błędy tylko do funkcji IntelliSense, które nie mają wpływ na rzeczywistych kompilacji.

#### <a name="example"></a>Przykład

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtypeidentity-metafunction-and-stdidentity-function-object"></a>Obiekt STD::type_identity metafunction i std::identity — funkcja

[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf). Przestarzała `std::identity` rozszerzenie szablonu klasy ma został usunięty i zastąpiony parametrem 20 C ++ `std::type_identity` metafunction i `std::identity` obiektu funkcyjnego. Oba są dostępne tylko w ramach [/STD: c ++ najnowsze](../build/reference/std-specify-language-standard-version.md).

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

Nowy procesor lambda Włącza tryb zgodności niektóre składni zaewidencjonuje ogólnych wyrażeń lambda, w obszarze [/STD: c ++ najnowsze](../build/reference/std-specify-language-standard-version.md) lub inny tryb języka przy użyciu **/ eksperymentalne: newLambdaProcessor**.

W programie Visual Studio 2017, ten kod kompiluje się bez ostrzeżeń, ale w programie Visual Studio 2019 generuje błąd *C2760 błąd składniowy: nieoczekiwany token "\<identyfikator expr >", oczekiwano "identyfikator wyrażenia"* :

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

### <a name="new-and-updated-standard-library-functions-c20"></a>Funkcje biblioteki standardowej nowe i zaktualizowane (C ++ 20)

- `starts_with()` i `ends_with()` dla `basic_string` i `basic_string_view`.
- `contains()` dla kontenerów asocjacyjnych.
- `remove()`, `remove_if()` i `unique()` dla obiektów `list` i `forward_list` zwracają teraz obiekt `size_type`.
- `shift_left()` i `shift_right()` dodane do \<algorytm >.

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019"></a>Poprawki i zmiany zachowania w programie Visual Studio 2019 r.

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

Błąd został wprowadzony w programie Visual Studio 2017 powodujący kompilatorowi ignorowanie błędów i wygenerować żadnego kodu dla nieprawidłowych wywołań += i-= w obszarze dyskretne `/clr` lub `/ZW`. Poniższy kod kompiluje się bez błędów w programie Visual Studio 2017, ale w Visual Studio 2019 r zgłasza poprawnie *błąd C2845: "System::String ^": arytmetyka wskaźnika nie jest dozwolona dla tego typu*:

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

Aby uniknąć tego błędu, w tym przykładzie, należy użyć operatora przy użyciu metody ToString(): `s += E::e.ToString();`.

### <a name="initializers-for-inline-static-data-members"></a>Inicjatory dla elementów członkowskich danych statycznych w tekście

Nieprawidłowy element członkowski, który uzyskuje dostęp w ramach `inline` i `static constexpr` inicjatory teraz są poprawnie wykrywane. Poniższy przykład skompiluje się bez błędów w programie Visual Studio 2017, ale w Visual Studio 2019 r, w obszarze `/std:c++17` tryb zgłasza *C2248 błąd: nie dostępu prywatnego elementu członkowskiego jest zadeklarowana w klasie "X"* .

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

MSVC używać, aby wydajności ostrzeżenie C4800 dotyczące niejawnej konwersji `bool`. Był zbyt duży hałas podczas on i nie można było pominąć, prowadzące z nami, aby usunąć go w programie Visual Studio 2017. Jednak z cyklem Visual Studio 2017 mamy mnóstwo informacji zwrotnych na przydatne w przypadkach, którego został on rozwiązywania. Możemy przywrócić w Visual Studio 2019 starannie dopasowane C4800, wraz z C4165 objaśnienia. Obu tych ostrzeżeń, które można łatwo pominąć za pomocą jawnego rzutowania, lub porównanie 0 odpowiedniego typu. C4800 jest to ostrzeżenie wyłączone domyślnie poziom 4, a C4165 jest to ostrzeżenie wyłączone domyślnie poziom 3. Oba są wykrywalni przy użyciu `/Wall` — opcja kompilatora.

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
void example()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>Funkcja treści szablonu zawierającego constexpr, jeśli instrukcji

Gdy ciało funkcji jest szablon zawierający `if constexpr` instrukcje mają też `/permissive-` włączone kontrole związane z analizy. Na przykład w programie Visual Studio 2017, poniższy kod tworzy C*7510: "Type": Użyj nazwy zależne typu musi być poprzedzona znakiem "typename"* tylko wtedy, gdy `/permissive-` opcja nie jest ustawiona. W programie Visual Studio 2019 tego samego błędy kodu w zgłasza nawet wtedy, gdy `/permissive-` ustawiono opcję:

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

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>Wbudowany kod zestawu nie jest obsługiwany w wyrażeniu lambda

Element wizualny C++ zespół był ostatnio świadomy problem zabezpieczeń, w którym stosowania asemblera wbudowanego w obrębie wyrażenia lambda może spowodować uszkodzenie z `ebp` (Zarejestruj adres zwrotny) w czasie wykonywania. Osoba atakująca może ewentualnie skorzystaj z tego scenariusza. Ze względu na charakter problem fakt, że tego asemblera wbudowanego jest tylko obsługiwana w x86 i niską interakcji między asembler wbudowany i pozostałe kompilatora, najbezpieczniejszym rozwiązaniem tego problemu było zabrania asemblera wbudowanego w wyrażeniu lambda.

Tylko stosowania asemblera wbudowanego w wyrażeniu lambda, które znaleźliśmy "w środowisku naturalnym" była możliwość przechwytywania adres zwrotny. W tym scenariuszu można przechwycić adres zwrotny na wszystkich platformach przy użyciu wewnętrzne polecenie kompilatora `_ReturnAddress()`.

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

### <a name="iterator-debugging-and-stdmoveiterator"></a>Debugowania iteratora i `std::move_iterator`

Debugowania funkcji iteratora ma zostały prowadzone do odkodowania prawidłowo `std::move_iterator`. Na przykład `std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` teraz mogą angażować `memcpy` szybkiej ścieżki.

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Poprawki dotyczące \<xkeycheck.h > wymuszania — słowo kluczowe

Standardowa biblioteka makra, zastępowanie wymuszania — słowo kluczowe \<xkeycheck.h > został naprawiony, aby emitować wykryto zamiast ogólnego komunikatu — słowo kluczowe rzeczywistego problemu. Ponadto obsługuje C ++ 20 słów kluczowych i pozwala uniknąć oszukiwanie informujący o tym, że losowe słowa kluczowe są makra funkcji IntelliSense.

### <a name="allocator-types-no-longer-deprecated"></a>Typy alokatora nie jest już przestarzałe

`std::allocator<void>`, `std::allocator::size_type`, i `std::allocator::difference_type` są już przestarzałe.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Poprawić ostrzeżenie zawężaniu zakresu konwersje, ciąg

Fałszywe `static_cast` nie zostanie wywołana dla przez standard, które przypadkowo pominięte C4244 zawężanie ostrzeżeń został usunięty z `std::string`. Próba wywołania `std::string::string(const wchar_t*, const wchar_t*)` prawidłowo teraz wyemitują *C4244 "zawężanie wchar_t do znaku".*

### <a name="various-filesystem-correctness-fixes"></a>Różne \<filesystem > poprawki do poprawności

- Naprawiono `std::filesystem::last_write_time` kończy się niepowodzeniem podczas próby zmiany katalogu użytkownika ostatni czas zapisu.
- `std::filesystem::directory_entry` Konstruktor przechowuje teraz zakończonych niepowodzeniem wyników, zamiast zgłaszać wyjątek, jeśli podano ścieżkę docelową nieistniejącej.
- `std::filesystem::create_directory` Wersji parametru 2 została zmieniona na wywołuje wersji parametr 1, jako bazowego `CreateDirectoryExW` użyje funkcji `copy_symlink` podczas `existing_p` został Link symboliczny.
- `std::filesystem::directory_iterator` nie kończy się niepowodzeniem po znalezieniu przerwany Link symboliczny.
- `std::filesystem::space` teraz akceptuje ścieżki względne.
- `std::filesystem::path::lexically_relative` nie jest już zastanawia końcowe ukośniki, zgłaszane jako [LWG 3096](https://cplusplus.github.io/LWG/issue3096).
- Pracował wokół `CreateSymbolicLinkW` odrzuca ścieżki z ukośnikami w `std::filesystem::create_symlink`.
- Pracował wokół trybie usuwania POSIX `delete` funkcji istniejące w systemie Windows 10 LTSB 1609, ale bez faktycznego możliwość usuwania plików.
- `std::boyer_moore_searcher` i `std::boyer_moore_horspool_searcher`przez konstruktory kopiujące i kopiujące operatory przypisania faktycznie kopiować dane.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Algorytmy równoległe w systemie Windows 8 lub nowszy

Biblioteka algorytmów równoległych prawidłowo używa teraz rzeczywiste `WaitOnAddress` rodziny, w systemie Windows 8 lub nowszy, zamiast zawsze przy użyciu Windows 7 i starszych wersji fałszywe.

### <a name="stdsystemcategorymessage-whitespace"></a>`std::system_category::message()` Białe znaki

`std::system_category::message()` teraz przycina końcowe białe znaki z zwracanego komunikatu.

### <a name="stdlinearcongruentialengine-divide-by-zero"></a>`std::linear_congruential_engine` dzielenie przez zero

Niektóre warunki, które mogą być przyczyną `std::linear_congruential_engine` do wyzwolenia zostały naprawione dzielenie przez 0.

### <a name="fixes-for-iterator-unwrapping"></a>Poprawki dla iteratora rozpakowanie

Iterator rozpakowanie maszyny, która najpierw została udostępniona integracji programisty niezwiązanych z użytkownikiem w Visual Studio 2017 15.8, zgodnie z opisem w C++ artykuł z bloga zespołu [funkcje i poprawki w programie VS 2017 15.8](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/), nie jest już dekoduje Iteratory pochodną iteratorów standardowej biblioteki. Na przykład użytkownik, który pochodzi od klasy `std::vector<int>::iterator` i próbuje teraz dostosować zachowanie pobiera zachowanie wskaźnika, a nie ich niestandardowe zachowanie podczas wywoływania algorytmami standardowej biblioteki.

Kontener nieuporządkowaną `reserve` działa teraz faktycznie rezerwy dla elementów N, zgodnie z opisem w [LWG 2156](https://cplusplus.github.io/LWG/issue2156).

### <a name="time-handling"></a>Czas obsługi

- Wcześniej, niektóre wartości czasu, które zostały przekazane do biblioteki współbieżności spowodowałoby przepełnienie, na przykład `condition_variable::wait_for(seconds::max())`. Po rozwiązaniu przepełnienia dostosować zachowanie pozornie losowe cyklu 29 dni (po milisekund uint32_t zaakceptowane przez podstawowych interfejsów API systemu Win32 nastąpiło przepełnienie).

- <ctime> Nagłówka teraz poprawnie deklaruje `timespec` i `timespec_get` w przestrzeni nazw `std` oprócz stwierdzenie ich w globalnej przestrzeni nazw.

### <a name="various-fixes-for-containers"></a>Różne poprawki dla kontenerów

- Wiele funkcji pojemnika wewnętrznego biblioteki standardowej wprowadzono prywatny, aby uzyskać lepsze działanie funkcji IntelliSense. W kolejnych wersjach MSVC powinny dodatkowe poprawki, aby oznaczyć elementy członkowskie jako prywatne.

- Wyjątek bezpieczeństwa poprawność problemów, na którym kontenerów opartych na węźle, takich jak `list`, `map`, i `unordered_map` może ulec uszkodzeniu zostały rozwiązane. Podczas `propagate_on_container_copy_assignment` lub `propagate_on_container_move_assignment` operację ponownego przypisania, firma Microsoft będzie kontenera wartownik węzeł za darmo dzięki usłudze stare alokatora, wykonaj przypisanie POCCA/POCMA za pośrednictwem stare alokatora, a następnie spróbuj uzyskać węzła wartownik z nowego programu przydzielania. Jeśli ten przydział nie powiodła się, kontener jest uszkodzony i jeszcze nie zostać zniszczone jako będąca właścicielem jest węzłem wartownik niezmiennej strukturze twardych danych. Ten kod został naprawiony przydzielić nowego węzła wartownik z kontenera źródłowego alokatora przed niszczenie istniejący węzeł wskaźnikowych.

- Kontenery zostały rozwiązane do buforów zawsze kopiowania/przenoszenia/wymiany zgodnie z opisem w `propagate_on_container_copy_assignment`, `propagate_on_container_move_assignment`, i `propagate_on_container_swap`, nawet w przypadku puli buforów zadeklarowana `is_always_equal`.

- Dodano przeciążenia dla kontenera, scalanie i wyodrębnić funkcji elementów członkowskich, które akceptują rvalue kontenerów na [P0083 "Łączenie map i zestawów"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)

### <a name="stdbasicistreamread-processing-of-rn--n"></a>`std::basic_istream::read` Przetwarzanie \\r\\n = > \\n

`std::basic_istream::read` Naprawiono nie zapis do części dostarczony bufor tymczasowo jako część \\r\\n = > \\n przetwarzania. Ta zmiana rezygnuje ze niektóre korzyści wynikające z wydajności, uzyskane w Visual Studio 2017 15.8 dla odczytów przekracza 4K w rozmiarze. Jednakże ulepszenia wydajności z unikanie trzech wywołaniach wirtualnych na znak są nadal dostępne.

### <a name="stdbitset-constructor"></a>`std::bitset` Konstruktor

`std::bitset` Konstruktor nie jest już odczytuje te i wyzerowania w odwrotnej kolejności dla dużych bitsets.

### <a name="stdpairoperator-regression"></a>`std::pair::operator=` Regresji

Naprawiono regresję w `std::pair`użytkownika operator przypisania wprowadzone podczas implementowania [LWG 2729 "Brak SFINAE na std::pair::operator =";](https://cplusplus.github.io/LWG/issue2729). Teraz poprawnie przyjmuje typy możliwe do przekonwertowania na `std::pair` ponownie.

### <a name="non-deduced-contexts-for-addconstt"></a>Określić inne niż konteksty dla `add_const_t`

Usunięto usterkę cech typu pomocniczych, gdzie `add_const_t` i pokrewnych funkcji powinna być-wywnioskować kontekstu. Innymi słowy `add_const_t` powinien być aliasem `typename add_const<T>::type`, a nie `const T`.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="improvements_150"></a> Ulepszenia programu Visual Studio RTW 2017 (wersja 15.0)

Dzięki obsłudze dla uogólniony `constexpr` i Inicjowanie składowej danych niestatycznych (NSDMI) dla wartości zagregowanych, Microsoft C++ kompilatora w programie Visual Studio 2017 jest teraz ukończona funkcje dodane w C ++ 14 standardowych. Jednak w kompilatorze nadal brakuje kilku funkcji ze standardowych C ++ 11 i C ++ 98 normy. Zobacz [Visual zgodność języka C++](../visual-cpp-language-conformance.md) dla tabeli, która pokazuje bieżący stan kompilatora.

### <a name="c11-expression-sfinae-support-in-more-libraries"></a>C++11: Wyrażenie SFINAE obsługi w bibliotekach więcej

Kompilator w dalszym ciągu zwiększyć jego obsługę wyrażenie SFINAE, który jest wymagany do odliczanie argumentu szablon i podstawianie gdzie `decltype` i `constexpr` wyrażenia może być wyświetlana jako parametry szablonu. Aby uzyskać więcej informacji, zobacz [wyrażenie SFINAE ulepszeń w programie Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3).

### <a name="c14-nsdmi-for-aggregates"></a>C++14: NSDMI dla wartości zagregowanych

Wartość zagregowana jest tablicą lub klasą z żaden konstruktor dostarczone przez użytkownika, nie prywatnych lub chronionych niestatycznych składowych danych, nie mają klas bazowych i żadnych funkcji wirtualnych. Począwszy od wersji programu C ++ 14 agregatów mogą zawierać inicjatorów składowych. Aby uzyskać więcej informacji, zobacz [inicjatorów składowych i agreguje](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html).

### <a name="c14-extended-constexpr"></a>C++14: rozszerzone `constexpr`

Wyrażenia zadeklarowane jako `constexpr` teraz mogą zawierać niektórych rodzajów deklaracji, jeśli i Przełącz instrukcji, instrukcje pętli i mutacji obiektów, których okres istnienia rozpoczął się w ramach oceny wyrażenia constexpr. Ponadto nie jest już wymagane, `constexpr` niestatycznej składowej musi być niejawnie `const`. Aby uzyskać więcej informacji, zobacz [złagodzić ograniczenia dotyczące funkcji constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html).

### <a name="c17-terse-staticassert"></a>C++17: Zwięzła `static_assert`

Parametr komunikat `static_assert` jest opcjonalne. Aby uzyskać więcej informacji, zobacz [rozszerzanie static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf).

### <a name="c17-fallthrough-attribute"></a>C ++ 17: `[[fallthrough]]` atrybutu

W **/STD: c ++ 17** trybie `[[fallthrough]]` atrybut może być używany w kontekście instrukcji switch jako wskazówka do kompilatora ma zachowanie należą do. Ten atrybut zapobiega wystawianie ostrzeżenia w takich przypadkach kompilator. Aby uzyskać więcej informacji, zobacz [słownictwo dla \[ \[fallthrough\] \] atrybutu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf).

### <a name="generalized-range-based-for-loops"></a>Uogólnione w zakresie pętli for opierających

Oparta na zakresie dla pętli nie jest już wymagany, który `begin()` i `end()` zwracać obiekty tego samego typu. Ta zmiana umożliwia `end()` do zwrócenia wartownik używane przez zakresów w [v3 zakresu](https://github.com/ericniebler/range-v3) i ukończone ale not-to jeszcze gotowe — opublikowanego specyfikacji technicznej zakresów. Aby uzyskać więcej informacji, zobacz [uogólnianie bazująca na zakresie pętli For](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html).

## <a name="improvements_153"></a> Ulepszenia w programie Visual Studio 2017 w wersji 15.3

### <a name="constexpr-lambdas"></a>lambdy wyrażeń constexpr

Wyrażenia lambda mogą teraz używać w wyrażeniach stałych. Aby uzyskać więcej informacji, zobacz [constexpr wyrażeń lambda w języku C++](../cpp/lambda-expressions-constexpr.md).

### <a name="if-constexpr-in-function-templates"></a>`if constexpr` w szablonach — funkcja

Szablon funkcji może zawierać `if constexpr` instrukcji, aby włączyć rozgałęzianie w czasie kompilacji. Aby uzyskać więcej informacji, zobacz [Jeśli instrukcji constexpr](../cpp/if-else-statement-cpp.md#if_constexpr).

### <a name="selection-statements-with-initializers"></a>Instrukcje wyboru z inicjatorami

`if` Instrukcji może zawierać inicjatora i wprowadza zmiennej w zakresie bloku w instrukcji, sam. Aby uzyskać więcej informacji, zobacz [Jeśli instrukcji za pomocą inicjatora](../cpp/if-else-statement-cpp.md#if_with_init).

### <a name="maybeunused-and-nodiscard-attributes"></a>`[[maybe_unused]]` i `[[nodiscard]]` atrybutów

Nowy atrybut `[[maybe_unused]]` kod ostrzeżenia, gdy jednostka nie jest używana. `[[nodiscard]]` Atrybut tworzy ostrzeżenie, jeśli wartość zwracaną przez wywołanie funkcji jest odrzucany. Aby uzyskać więcej informacji, zobacz [atrybutów w języku C++](../cpp/attributes.md).

### <a name="using-attribute-namespaces-without-repetition"></a>Używanie atrybutu przestrzeni nazw, bez powtarzania

Nową składnię, aby włączyć tylko identyfikator jednej przestrzeni nazw na liście atrybutów. Aby uzyskać więcej informacji, zobacz [atrybutów w języku C++](../cpp/attributes.md).

### <a name="structured-bindings"></a>Powiązania strukturalne

Teraz jest to możliwe w jednej deklaracji do przechowywania wartości z poszczególne nazwy dla jego składników, gdy wartość jest tablicą, `std::tuple` lub `std::pair`, lub wszystkich publicznych niestatycznych elementów członkowskich danych. Aby uzyskać więcej informacji, zobacz [powiązań strukturalnych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf) i [zwracanie wielu wartości z funkcją](../cpp/functions-cpp.md#multi_val).

### <a name="construction-rules-for-enum-class-values"></a>Konstrukcja reguł dla `enum class` wartości

Jest teraz niejawne/inne niż zawężanie konwersji z podstawowym typem wyliczenia w zakresie firmy do wyliczenia, gdy jego definicja wprowadza nie modułu wyliczającego źródła jest używana składnia inicjalizacji listy. Aby uzyskać więcej informacji, zobacz [konstruowania reguły dla wyliczenia klasy wartości](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf) i [wyliczenia](../cpp/enumerations-cpp.md#no_enumerators).

### <a name="capturing-this-by-value"></a>Przechwytywanie `*this` według wartości

`*this` w wyrażeniu lambda teraz mogą być przechwytywane przez wartość. Ta zmiana umożliwia realizację scenariuszy, w których wyrażenie lambda jest wywoływana w operacje równoległe i asynchroniczne, zwłaszcza na nowszych architektury maszyny. Aby uzyskać więcej informacji, zobacz [Przechwytywanie Lambda \*to przez wartość jako \[=\*to\]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html).

### <a name="removing-operator-for-bool"></a>Usuwanie `operator++` dla `bool`

`operator++` nie jest już obsługiwany na `bool` typów. Aby uzyskać więcej informacji, zobacz [Usuń przestarzałe operator++(bool)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html).

### <a name="removing-deprecated-register-keyword"></a>Usuwanie przestarzałe `register` — słowo kluczowe

`register` — Słowo kluczowe, wcześniej przestarzały (i ignorowane przez kompilator), zostało usunięte z języka. Aby uzyskać więcej informacji, zobacz [Usuń przestarzałe użytkowania register — słowo kluczowe](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html).

## <a name="improvements_155"></a> Ulepszenia w programie Visual Studio 2017 w wersji 15.5

Funkcje oznaczone atrybutem \[14] są dostępne w bezwarunkowo nawet w **/STD: c ++ 14** trybu.

### <a name="new-compiler-switch-for-extern-constexpr"></a>Nowy przełącznik dla `extern constexpr`

We wcześniejszych wersjach programu Visual Studio, kompilator zawsze udostępniła `constexpr` zmiennej zewnętrzne, nawet wtedy, gdy zmienna została oznaczona jako `extern`. W programie Visual Studio 2017 w wersji 15.5, nowy przełącznik kompilatora [/Zc: externconstexpr](../build/reference/zc-externconstexpr.md), umożliwia poprawne zachowanie zgodne z normami. Aby uzyskać więcej informacji, zobacz [extern constexpr powiązania](#extern_linkage).

### <a name="removing-dynamic-exception-specifications"></a>Usuwanie specyfikacji wyjątków dynamicznych

[P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html) specyfikacje wyjątków dynamicznych zostały zaniechane w C ++ 11. Ta funkcja zostanie usunięta z C ++ 17, ale przestarzałe (nadal) `throw()` specyfikacji są przechowywane wyłącznie jako aliasu dla `noexcept(true)`. Aby uzyskać więcej informacji, zobacz [usuwanie specyfikacji wyjątków dynamicznych i noexcept](#noexcept_removal).

### `not_fn()`

[P0005R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html) `not_fn` zostanie `not1` i `not2`.

### <a name="rewording-enablesharedfromthis"></a>Zmiana sformułowania elementu `enable_shared_from_this`

[P0033R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html) `enable_shared_from_this` został dodany w C ++ 11. C ++ 17 standardowych aktualizacji specyfikacji lepiej obsłużyć niektórych przypadki brzegowe. [14]

### <a name="splicing-maps-and-sets"></a>Łączenie map i zestawów

[P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) ta funkcja umożliwia wyodrębnianie węzłów z kontenerów asocjacyjnych (czyli `map`, `set`, `unordered_map`, `unordered_set`) które następnie można modyfikować i dodaje do tego samego kontenera lub inny kontener, który używa tego samego typu węzła. (Typowy przypadek użycia jest wyodrębnienie węzła z `std::map`, należy zmienić wartość klucza i ponownie włóż.)

### <a name="deprecating-vestigial-library-parts"></a>Wycofano przestarzały biblioteki części

[P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html) kilka funkcji C++ standardowej biblioteki zostały zastąpione przez nowsze funkcje w ciągu lat; w przeciwnym razie zostały znalezione nie przydatne lub problemami. Te funkcje oficjalnie zostały zaniechane w C ++ 17.

### <a name="removing-allocator-support-in-stdfunction"></a>Usuwanie obsługi alokatora w `std::function`

[P0302R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html) przed C ++ 17, szablon klasy `std::function` ma kilka konstruktorów, które miały argument alokatora. Jednak korzystanie z puli buforów w tym kontekście był kłopotliwy i semantyka były niejasne. Problem contructors został usunięty.

### <a name="fixes-for-notfn"></a>Poprawki dla `not_fn()`

[P0358R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html) nowe sformułowanie funkcji `std::not_fn` zapewnia obsługę propagacji kategorii wartości, gdy są używane w przypadku wywołania otoki.

### <a name="sharedptrt-sharedptrtn"></a>`shared_ptr<T[]>`, `shared_ptr<T[N]>`

[P0414R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html) scalanie `shared_ptr` zmieni się z dokumentu Library Fundamentals C ++ 17. [14]

### <a name="fixing-sharedptr-for-arrays"></a>Naprawianie `shared_ptr` dla tablic

[P0497R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html) poprawki do działu pomocy technicznej shared_ptr dla tablic. [14]

### <a name="clarifying-insertreturntype"></a>Wyjaśnienie `insert_return_type`

[P0508R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html) kontenery asocjacyjne z unikatowymi kluczami i kontenery nieuporządkowane z unikatowymi kluczami mają funkcję członkowską `insert` zwracającego typ zagnieżdżony `insert_return_type`. Zwracać typ jest teraz zdefiniowany jako specjalizacją typu, który jest sparametryzowane iteratora i element NodeType kontenera.

### <a name="inline-variables-for-the-standard-library"></a>Zmienne śródwierszowe standardowej biblioteki

[P0607R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)

### <a name="annex-d-features-deprecated"></a>Przestarzałe funkcje załącznik D

Załącznik D C++ standard zawiera wszystkie funkcje, które zostały wycofane, w tym `shared_ptr::unique()`, `<codecvt>`, i `namespace std::tr1`. Gdy **/STD: c ++ 17** przełącznika kompilatora jest ustawiona, prawie wszystkie funkcje biblioteki standardowej załącznik D są oznaczone jako przestarzałe. Aby uzyskać więcej informacji, zobacz [funkcje biblioteki standardowej, w załączniku D są oznaczone jako przestarzałe](#annex_d).

`std::tr2::sys` Przestrzeni nazw w `<experimental/filesystem>` teraz emituje ostrzeżenie o zakończeniu obsługi, w obszarze **/STD: c ++ 14** domyślnie, a teraz zostanie usunięta w ramach **/STD: c ++ 17** domyślnie.

Ulepszone zgodność w `<iostream>` , unikając użyto niestandardowego rozszerzenia (jawne specjalizacje w klasie).

Standardowa biblioteka korzysta z szablonów zmiennych wewnętrznie.

Standardowa biblioteka została zaktualizowana w odpowiedzi na C ++ 17 zmiany w kompilatorze, włącznie z dodaniem `noexcept` w systemie typów oraz usunięcie specyfikacje dynamic wyjątków.

## <a name="improvements_156"></a> Ulepszenia w programie Visual Studio 2017 w wersji 15.6

### <a name="c17-library-fundamentals-v1"></a>C ++ 17 biblioteki podstawy V1

[P0220R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) zawiera specyfikacji technicznej podstawowe informacje dotyczące biblioteki standardu C ++ 17 w postaci standardowych. Obejmuje aktualizacje \<eksperymentalne/krotki >, \<eksperymentalne/opcjonalne >, \<eksperymentalne/funkcjonalności >, \<eksperymentalne/any >, \<eksperymentalne/string_view >, \<eksperymentalne/pamięci >, \<eksperymentalne/memory_resource >, a \<eksperymentalne/algorytm >.

### <a name="c17-improving-class-template-argument-deduction-for-the-standard-library"></a>C++17: Usprawnienie odliczanie argumentu szablon klasy biblioteki standardowej

[P0739R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html) przenieść `adopt_lock_t` przedniej lista parametrów dla `scoped_lock` umożliwia spójne używanie `scoped_lock`. Zezwalaj na `std::variant` Konstruktor uczestniczy w przeciążeniu rozdzielczości w większości przypadków, aby umożliwić przydzielania kopii.

## <a name="improvements_157"></a> Ulepszenia w programie Visual Studio 2017 wersji 15.7

### <a name="c17-rewording-inheriting-constructors"></a>C++17: Konstruktory dziedziczące sformułować

[P0136R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html) Określa, że **przy użyciu** deklarację, że teraz nazwy konstruktora sprawia, że odpowiednie widoczne dla inicjowania klasy pochodnej Konstruktory klasy bazowej, zamiast deklarowania dodatkowe pochodne Konstruktory klasy. Ta zmiana sformułowania elementu różni się od C ++ 14. W programie Visual Studio 2017 wersji 15.7 lub nowszej, w **/STD: c ++ 17** trybu, kod, który jest prawidłowy w C ++ 14 i używa konstruktory dziedziczące jest nieprawidłowy lub mogą mieć różną semantykę.

Poniższy przykład przedstawia C ++ 14 zachowanie:

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

W poniższym przykładzie przedstawiono **/STD: c ++ 17** zachowania w programie Visual Studio 15.7:

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

### <a name="c17-extended-aggregate-initialization"></a>C++17: Rozszerzony inicjowania agregacji

[P0017R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)

Jeśli konstruktor klasy bazowej jest niepublicznych, ale dostęp do klasy pochodnej, następnie w obszarze **/STD: c ++ 17** tryb w programie Visual Studio w wersji 15.7 pustych nawiasów klamrowych nie jest już służy do inicjowania obiektu typu pochodnego.

Poniższy przykład przedstawia C ++ 14 zgodność zachowanie:

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

W języku C ++ 17 `Derived` teraz jest uznawany za typ agregacji. Oznacza to, że Inicjalizacja `Base` za pośrednictwem prywatnych domyślnego konstruktora się dzieje bezpośrednio, jako część reguły rozszerzonej inicjowania agregacji. Wcześniej `Base` Konstruktor prywatny została wywołana przy użyciu `Derived` konstruktora, a zakończyło się pomyślnie z powodu deklaracją elementu zaprzyjaźnionego.

W poniższym przykładzie pokazano C ++ 17 zachowania w programie Visual Studio w wersji 15.7 w **/STD: c ++ 17** trybu:

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

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C++17: Deklarowanie parametry szablonu bez typu dzięki funkcji autoskalowania

[P0127R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)

W **/STD: c ++ 17** tryb, kompilator może teraz wywnioskować typ argumentu szablonu bez typu, która jest zadeklarowana za pomocą **automatycznie**:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

Jeden wpływ tej nowej funkcji polega na prawidłowy C ++ 14 Kod jest nieprawidłowy lub mogą mieć różną semantykę. Na przykład niektóre przeciążenia, które były wcześniej nieprawidłowe są teraz prawidłowe. W poniższym przykładzie pokazano C ++ 14 Kod, który kompiluje się, ponieważ wywołanie `example(p)` jest powiązany z `example(void*);`. W programie Visual Studio 2017 wersji 15.7 w **/STD: c ++ 17** trybie `example` szablon funkcji jest najlepsze dopasowanie.

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*) = delete;

void example(void *);

void sample(A<0> *p)
{
    example(p); // OK in C++14
}
```

Poniższy przykład pokazuje C ++ 17 kodu w Visual Studio 15.7 w w **/STD: c ++ 17** trybu:

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*);

void example(void *);

void sample(A<0> *p)
{
    example(p); // C2280: 'int example<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C++17: podstawowe ciąg konwersje (częściowa Obsługa)

[P0067R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html) niskiego poziomu, niezależnie od ustawień regionalnych funkcje do konwersji liczb całkowitych i ciągi oraz między liczb zmiennoprzecinkowych i ciągów.

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C++20: Unikanie niepotrzebnych zanikania (częściowa)

[P0777R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf) dodaje rozróżnienie między koncepcji "zanikania" i po prostu usunąć const lub kwalifikatory odwołań.  Nowy typ cechy `remove_reference_t` zastępuje `decay_t` w niektórych kontekstach. Obsługa `remove_cvref_t` jest zaimplementowane w Visual Studio 2019 r.

### <a name="c17-parallel-algorithms"></a>C++17: Algorytmy równoległe

[P0024R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html) TS równoległości jest włączona do standard, za pomocą drobnych modyfikacji.

### <a name="c17-hypotx-y-z"></a>C ++ 17: `hypot(x, y, z)`

[P0030R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf) dodaje trzy pomocy nowych przeciążeń `std::hypot`, dla typów **float**, **double**, i **typu long double**, z których każdy ma trzy parametry wejściowe.

### <a name="c17-filesystem"></a>C ++ 17: \<filesystem >

[P0218R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html) przyjmuje usług terminalowych systemu plików w postaci standardowych za pomocą niewielkiej modyfikacji treść.

### <a name="c17-mathematical-special-functions"></a>C++17: Funkcje matematyczne specjalne

[P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) przyjmuje poprzedniego specyfikacje techniczne dla funkcji matematycznych specjalne do standardowego \<cmath > nagłówka.

### <a name="c17-deduction-guides-for-the-standard-library"></a>C++17: Wnioskowanie przewodniki dotyczące biblioteki standardowej

[P0433R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html) aktualizacje STL, aby móc korzystać z języka C ++ 17 przyjęcia [P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html), która dodaje obsługę odliczanie argumentu szablon klasy.

### <a name="c17-repairing-elementary-string-conversions"></a>C++17: Naprawianie podstawowe ciąg konwersje

[P0682R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0682r1.html) nowe funkcje konwersji ciągu podstawowe z P0067R5 przenosić do nowego nagłówka \<charconv > i innych ulepszeń, w tym zmiana obsługi błędów, aby użyć `std::errc` zamiast `std::error_code`.

### <a name="c17-constexpr-for-chartraits-partial"></a>C ++ 17: `constexpr` dla `char_traits` (częściowa)

[P0426R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html) zmieni się na `std::traits_type` elementów członkowskich `length`, `compare`, i `find` się `std::string_view` można używać w wyrażeniach stałych. (W programie Visual Studio 2017 w wersji 15.6 obsługę Clang/LLVM tylko. W wersji 15.7 w wersji zapoznawczej 2, pomocy technicznej jest niemal należy wykonać ClXX także.)

## <a name="improvements_159"></a> Ulepszenia w programie Visual Studio 2017 w wersji 15.9

### <a name="left-to-right-evaluation-order-for-operators-----and-"></a>Kolejność obliczania od lewej do prawej dla operatorów `->*`, `[]`, `>>`, i `<<`

Począwszy od C ++ 17, argumenty operacji operatory `->*`, `[]`, `>>`, i `<<` muszą być obliczane w kolejności od lewej do prawej. Istnieją dwa przypadki, w których kompilator nie może zagwarantować to zamówienie:

- gdy jedno z wyrażeń operand jest obiektem, przekazać przez wartość lub zawiera obiekt przekazywany przez wartość, lub

- gdy kompilowany przy użyciu **/CLR**, a jeden z argumentów jest pole elementu tablicy lub obiektu.

Kompilator generuje ostrzeżenie [C4866](https://docs.microsoft.com/cpp/error-messages/compiler-warnings/c4866?view=vs-2017) kiedy nie może zagwarantować oceny od lewej do prawej. Kompilator generuje ostrzeżenie tylko wtedy, gdy **/STD: c ++ 17** lub nowszej jest określony, wymaganie kolejności od lewej do prawej te operatory wprowadzono w języku C ++ 17.

Aby rozwiązać tego ostrzeżenia, najpierw należy wziąć pod uwagę czy oceny argumentów od lewej do prawej jest to konieczne, takich jak podczas oceny operandów może powodować generowanie efekty uboczne zależnych od kolejności. W wielu przypadkach kolejność, w której argumenty operacji są obliczane nie ma widocznych wpływu. Jeśli kolejność obliczania musi mieć od lewej do prawej, należy rozważyć, czy można przekazywać argumentów przez odniesienie const zamiast tego. Ta zmiana eliminuje ostrzeżenie w następującym przykładzie kodu:

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

## <a name="update_150"></a> Poprawki błędów w Visual Studio RTW 2017 (wersja 15.0)

### <a name="copy-list-initialization"></a>Copy-list-initialization

Program Visual Studio 2017 poprawnie zgłasza błędy kompilatora dotyczące tworzenia obiektów przy użyciu listy inicjatorów, które nie zostały wykryte w Visual Studio 2015 i może prowadzić do awarii lub niezdefiniowane zachowanie środowiska uruchomieniowego. Zgodnie z 13.3.1.7p1 N4594, w liście Inicjalizacja kopiowania kompilator jest wymagany do rozważenia jawny Konstruktor przypadku rozpoznawania przeciążenia, ale musi zgłosić błąd, jeśli wybrano tego określonego przeciążenia.

Dwa poniższe przykłady kompilacji w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.

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

Aby poprawić ten błąd, należy użyć inicjalizacji bezpośredniej:

```cpp
A a1{ 1 };
const A& a2{ 1 };
```

W programie Visual Studio 2015 kompilator błędnie traktowane listy Inicjalizacja kopiowania na w taki sam sposób, jak regularne Inicjowanie kopiowania; uznaje się jedynie konwertowanie konstruktory przeciążeń z późnym wiązaniem. W poniższym przykładzie Visual Studio 2015 wybiera MyInt(23), ale Visual Studio 2017 niepoprawnie zgłasza błąd.

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

Ten przykład jest podobny do poprzedniego, ale zgłasza błąd inny. Ona powiedzie się w programie Visual Studio 2015 i kończy się niepowodzeniem w programie Visual Studio 2017 z C2668.

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

Program Visual Studio 2017 teraz wydaje się prawidłowe ostrzeżenie dotyczące przestarzałe definicje typów, które są zadeklarowane w klasie lub strukturze. W poniższym przykładzie kompiluje się bez ostrzeżeń w programie Visual Studio 2015, ale generuje C4996 w programie Visual Studio 2017.

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

### `constexpr`

Program Visual Studio 2017 niepoprawnie zgłasza błąd, gdy lewostronny operand warunkowo oceny operacja jest nieprawidłowa w kontekście wyrażenia constexpr. Poniższy kod jest kompilowany w programie Visual Studio 2015, ale nie w programie Visual Studio 2017 ("f". Funkcja constexpr nie może być wyrażeniem stałym C3615):

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

Aby poprawić ten błąd, albo zadeklarować `array::size()` pełnią `constexpr` lub usuń `constexpr` kwalifikator z `f`.

### <a name="class-types-passed-to-variadic-functions"></a>Typy klas przekazywane do funkcji ze zmienną liczbą argumentów

W programie Visual Studio 2017 klasy lub struktury, które są przekazywane do funkcji ze zmienną liczbą argumentów, takich jak printf musi być kopiowania. Podczas przekazywania takie obiekty, kompilator po prostu sprawia, że kopia bitowa i nie wywołuje konstruktor lub destruktor.

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

Aby poprawić ten błąd, należy wywołać funkcji składowej, która zwraca typ trywialne,

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

w przeciwnym razie Użyj rzutowania statycznego do konwertowania obiektu przed przekazaniem go:

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

Ciągi utworzone i zarządzane przy użyciu CString podane `operator LPCTSTR()` powinien być używany do rzutowania obiektu CString wskaźnik języka C, oczekiwany przez ciąg formatu.

```cpp
CString str1;
CString str2 = _T("hello!");
str1.Format(_T("%s"), static_cast<LPCTSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>Kwalifikatory CV w konstrukcji klasy

W programie Visual Studio 2015 Kompilator ignoruje czasami niepoprawnie Kwalifikator cv podczas generowania obiektu przez wywołanie konstruktora klasy. Ten problem może teoretycznie spowodować awarię lub nieoczekiwane zachowanie. W poniższym przykładzie kompiluje w programie Visual Studio 2015, ale zgłasza błąd kompilatora w programie Visual Studio 2017:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Aby poprawić ten błąd, Zadeklaruj `operator int()` jako `const`.

### <a name="access-checking-on-qualified-names-in-templates"></a>Trwa sprawdzanie kwalifikowane nazwy w szablonach dostępu

Poprzednie wersje kompilatora nie sprawdzanie dostępu do kwalifikowane nazwy w niektórych kontekstach szablonów. Ten problem może zakłócać oczekiwane zachowanie SFINAE, gdzie podstawienia może zakończyć się niepowodzeniem z powodu inaccessibility nazwy. Go może potencjalnie spowodowały awarię lub nieoczekiwane zachowanie w czasie wykonywania ponieważ kompilator niepoprawnie wywołana niewłaściwego przeciążenia operatora. W programie Visual Studio 2017 zgłaszany jest błąd kompilatora. Ten błąd może się różnić, ale zazwyczaj jest "Nie zgodnej przeciążonej funkcji, o których odnaleźć C2672". Poniższy kod kompilowany w programie Visual Studio 2015, ale zgłasza błąd w programie Visual Studio 2017:

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

W programie Visual Studio 2015 lub starszego kompilator nie diagnozowanie brakuje listy argumentów szablonu, gdy szablon pojawiły się na liście szablonu parametrów, na przykład, jako część domyślnego argumentu szablonu lub parametru szablonu bez typu. Ten problem może spowodować nieprzewidywalne zachowanie, w tym kompilator awarie lub nieoczekiwane zachowanie. Poniższy kod kompilowany w programie Visual Studio 2015, ale generuje błąd w programie Visual Studio 2017.

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Expression-SFINAE

Aby zapewnić obsługę wyrażenie SFINAE, w którym kompilator teraz analizuje `decltype` argumentów, jeśli szablony są deklarowane, a nie uruchomiony. W związku z tym jeśli specjalizacji zależne od innych zostanie znaleziony w argumencie decltype, jest ona nie odroczone do czasu wystąpienia. Jest on przetwarzany natychmiast, a wszystkie wynikowe błędy są zdiagnozować w danym momencie.

Poniższy przykład przedstawia takich błąd kompilatora, który jest wywoływany w punkcie deklaracji:

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

### <a name="classes-declared-in-anonymous-namespaces"></a>Klasy zadeklarowane w przestrzeniach nazw anonimowe

Zgodnie z opisem w C++ posiada klasy zadeklarowanej w anonimowej przestrzeni nazw w warstwie standardowa, wewnętrzne łączenie i oznacza to, że nie można wyeksportować. W programie Visual Studio 2015 i starszych tej reguły nie została wymuszona. W programie Visual Studio 2017 reguła częściowo jest wymuszana. Poniższy przykład generuje ten błąd w programie Visual Studio 2017: "Błąd C2201: const namespace::S1::vftable anonimowe: musi mieć zewnętrzne połączenie w celu eksportu/importu."

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>Domyślne Inicjatory dla wartości elementy członkowskie klasy (C++sposób niezamierzony)

W programie Visual Studio 2015 lub starszego kompilatora dozwolone (ale ignorowane) domyślny inicjator składowej dla składowej klasy wartości. Domyślna Inicjalizacja klasy wartości zawsze zero inicjuje elementy członkowskie. Domyślny konstruktor nie jest dozwolone. W programie Visual Studio 2017 domyślny element członkowski inicjatory podnieść błąd kompilatora, jak pokazano w poniższym przykładzie:

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // isn't allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Indeksatory domyślne (C++sposób niezamierzony)

W programie Visual Studio 2015 lub starszego kompilatora w niektórych przypadkach misidentified domyślna właściwość jako indeksatora domyślne. Można obejść ten problem za pomocą identyfikatora `default` do dostępu do właściwości. Obejście się stało się problematyczne po `default` została wprowadzona jako słowo kluczowe w C ++ 11. W programie Visual Studio 2017, błędy, które wymagane obejście zostały poprawione i kompilator teraz zgłasza błąd, gdy `default` umożliwia dostęp do właściwości domyślnej klasy.

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

W Visual Studio 2017 uzyskujesz dostęp do obu wartości właściwości, według nazwy:

```cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="update_153"></a> Poprawki błędów w programie Visual Studio 2017 w wersji 15.3

### <a name="calls-to-deleted-member-templates"></a>Wywołania do szablonów usuniętego elementu członkowskiego

W poprzednich wersjach programu Visual Studio kompilatora w niektórych przypadkach zakończy się niepowodzeniem, będzie emitował błąd źle sformułowane wywołań do szablonu usuniętego elementu członkowskiego, która potencjalnie spowodowałaby awarii w czasie wykonywania. Poniższy kod generuje teraz C2280, "" int S\<int >:: f\<int > (void) ": próba odwania do usuniętej funkcji do":

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

Aby naprawić błąd, należy zadeklarować `i` jako `int`.

### <a name="pre-condition-checks-for-type-traits"></a>Sprawdza, czy warunek wstępny cech typu

Visual Studio 2017 w wersji 15.3 zwiększa cech typu w celu bardziej restrykcyjnie zgodne ze standardem sprawdza, czy warunek wstępny. Jednego takiego wyboru jest możliwy do przypisania. Poniższy kod generuje C2139 w programie Visual Studio 2017 w wersji 15.3:

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Nowe ostrzeżenie kompilatora i środowiska uruchomieniowego kontroli native zarządzane organizowanie

Wywoływanie z funkcji zarządzanej do funkcji natywnych wymaga szeregowanie. Środowisko CLR jest kierowanie, ale go nie rozpoznaje C++ semantyki. Jeśli przekażesz obiekt natywny przez wartość CLR wywołuje Konstruktor kopiujący obiektu lub używa `BitBlt`, co może spowodować niezdefiniowane zachowanie w czasie wykonywania.

Obecnie kompilator generuje ostrzeżenie, jeśli je znasz, w czasie kompilacji, obiekt natywny przy użyciu domyślnego elementu ctor kopiowania usunięto przekazywaną między granic natywnych i zarządzanych przez wartość. Dla tych przypadków, w których kompilator nie może ustalić w czasie kompilacji, jej wprowadza kontroli w czasie wykonywania, aby program wywołuje `std::terminate` natychmiast, gdy źle sformułowane marshaling wystąpi. W programie Visual Studio 2017 w wersji 15.3, poniższy kod generuje ostrzeżenie C4606 "'A': przekazywanie argumentów poprzez wartość granicę natywne i zarządzane wymaga prawidłowej kopii konstruktora. W przeciwnym razie działanie środowiska uruchomieniowego jest niezdefiniowane.

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

Aby naprawić błąd, należy usunąć `#pragma managed` dyrektywy, aby oznaczyć obiektu wywołującego jako natywną i uniknąć szeregowanie.

### <a name="experimental-api-warning-for-winrt"></a>Eksperymentalne ostrzeżenie interfejsu API dla WinRT

Interfejsy API WinRT, które są wydawane dla ozdobione eksperymentowania i opinie `Windows.Foundation.Metadata.ExperimentalAttribute`. W programie Visual Studio 2017 w wersji 15.3 kompilator generuje ostrzeżenie C4698, gdy napotkają atrybut. Kilka interfejsów API w poprzednich wersjach zestawu Windows SDK ma już został ozdobione atrybutu i wywołań do tych interfejsów API teraz wyzwolić tego ostrzeżenia kompilatora. Nowsze Windows SDK mają atrybut, który został usunięty ze wszystkich typów dostarczany, ale jeśli używasz starszy zestaw SDK, należy pominąć te ostrzeżenia dla wszystkich wywołań do wysłania typów.

Poniższy kod generuje ostrzeżenie C4698: "" Windows:: magazynu:: IApplicationDataStatics2::GetForUserAsync"jest przeznaczony wyłącznie do celów oceny i może ulec zmianie, albo usunięty w przyszłych aktualizacjach":

```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); //C4698
```

Aby wyłączyć ostrzeżenia, należy dodać #pragma:

```cpp
#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>Definicja funkcji członkowskiej szablonu końca wiersza

Visual Studio 2017 w wersji 15.3 powoduje błąd, po napotkaniu definicji poza wierszem szablonu funkcji składowej, która nie została zadeklarowana w klasie. Następujący kod teraz generuje błąd C2039: 'f': nie jest członkiem użytkownika ':

```cpp
struct S {};

template <typename T>
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

Aby naprawić błąd, Dodaj deklarację klasy:

```cpp
struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Podjęto próbę przyjąć adresu `this` wskaźnika

W C++ `this` jest prvalue typu wskaźnika do X. Nie można przyjąć adresu `this` lub powiązać go z odwołaniem lvalue. W poprzednich wersjach programu Visual Studio kompilator umożliwi obejście tego ograniczenia przy użyciu rzutowania. W programie Visual Studio 2017 w wersji 15.3 kompilator generuje błąd C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Konwersja do niedostępnej klasy bazowej

Visual Studio 2017 w wersji 15.3 powoduje błąd, gdy użytkownik spróbuje przekonwertować typ do klasy bazowej, który jest niedostępny. Kompilator zgłasza teraz "Błąd C2243:"cast typu": konwersja miał *" do "B *" istnieje, ale jest niedostępna ". Poniższy kod jest nieprawidłowo sformułowany i może powodować awarię w czasie wykonywania. Kompilator generuje C2243 teraz, po napotkaniu kodu w następujący sposób:

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-arent-allowed-on-out-of-line-definitions-of-member-functions"></a>Argumenty domyślne nie są dozwolone w poza wiersza definicje funkcji elementów członkowskich

Argumenty domyślne nie są dozwolone w definicji poza wierszem funkcji składowych w klasach szablonu. Kompilator zgłosi ostrzeżenie w obszarze **/ permissive**i poważny błąd w obszarze **/ permissive-** .

W poprzednich wersjach programu Visual Studio poniższy kod źle sformułowane potencjalnie może spowodować awarię środowiska uruchomieniowego. Visual Studio 2017 w wersji 15.3 generuje ostrzeżenie C5034: "A\<T >:: f": definicja końca wiersza składowej szablonu klasy nie może mieć argumentów domyślnych:

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

Aby naprawić błąd, należy usunąć `= false` domyślnych argumentów.

### <a name="use-of-offsetof-with-compound-member-designator"></a>Korzystanie z `offsetof` z desygnator złożonej składowej

W programie Visual Studio 2017 w wersji 15.3, przy użyciu `offsetof(T, m)` gdzie *m* jest "desygnator złożonej składowej" skutkuje ostrzeżenia podczas kompilowania z **/Wall** opcji. Poniższy kod jest nieprawidłowo sformułowany i potencjalnie może spowodować awarię w czasie wykonywania. Generuje programie Visual Studio 2017 w wersji 15.3 "ostrzeżenie C4841: użyto niestandardowego rozszerzenia: desygnator złożonej składowej w makrze offsetof":

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

Aby naprawić kod, wyłącz ostrzeżenia z pragmą lub zmień kod, aby nie używać `offsetof`:

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Za pomocą `offsetof` przy użyciu statycznej składowej danych lub funkcji składowej

W programie Visual Studio 2017 w wersji 15.3, przy użyciu `offsetof(T, m)` gdzie *m* odwołuje się do statycznej składowej danych lub element członkowski funkcji będzie skutkowało błędem. Poniższy kod generuje "Błąd C4597: niezdefiniowane zachowanie: makro offsetof zastosowano do funkcji składowej"przykładowy"" i "Błąd C4597: niezdefiniowane zachowanie: makro offsetof zastosowano do statycznej składowej danych"przykładowy"":

```cpp
#include <cstddef>

struct A {
   int ten() { return 10; }
   static constexpr int two = 2;
};

constexpr auto off = offsetof(A, ten);
constexpr auto off2 = offsetof(A, two);
```

Ten kod jest nieprawidłowo sformułowany i potencjalnie może spowodować awarię w czasie wykonywania. Aby naprawić błąd, Zmień kod, aby nie jest już wywołania niezdefiniowane zachowanie. Nieprzenośne kodu, który jest zabroniona przez C++ standardowych.

### <a name="declspec"></a> Nowe ostrzeżenie dotyczące `__declspec` atrybutów

W programie Visual Studio 2017 w wersji 15.3, kompilator nie jest już ignoruje atrybuty Jeśli `__declspec(...)` zostanie zastosowany przed `extern "C"` Specyfikacja powiązania. Wcześniej kompilator będzie ignorować atrybut, który może mieć wpływ na środowisko uruchomieniowe. Gdy **/Wall** i **/WX** opcje są ustawione, poniższy kod generuje "ostrzeżenie C4768: atrybuty __declspec przed specyfikacją konsolidacji są ignorowane":

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Aby usunąć to ostrzeżenie, należy umieścić `extern "C"` pierwszy:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

To ostrzeżenie jest wyłączone domyślnie w 15.3, ale na przez domyślne w wersji 15.5, a jedynie wpływ na kod skompilowany przy użyciu **/Wall** **/WX**.

### <a name="decltype-and-calls-to-deleted-destructors"></a>`decltype` i wywołania usunięto destruktorów

W poprzednich wersjach programu Visual Studio, kompilator nie wykryło ono po wywołaniu destruktora usunięto wystąpił w kontekście wyrażenia skojarzone z `decltype`. W programie Visual Studio 2017 w wersji 15.3, poniższy kod generuje "Błąd C2280: "A\<T >:: ~ A(void)": próba odwania do usuniętej funkcji do ":

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

Visual Studio 2017 w wersji RTW wersji miał regresji, w którym C++ kompilatora nie wystawiać diagnostycznych if `const` zmienna nie została zainicjowana. Regresja ten został rozwiązany w programie Visual Studio 2017 w wersji 15.3. Poniższy kod generuje teraz "ostrzeżenie C4132: "Value": obiekt const powinien być inicjowany jako ":

```cpp
const int Value; //C4132
```

Aby naprawić błąd, należy przypisać wartość do `Value`.

### <a name="empty-declarations"></a>Pusty deklaracji

Visual Studio 2017 w wersji 15.3 teraz wyświetli ostrzeżenie w deklaracjach puste w przypadku wszystkich typów i nie tylko wbudowane typy. Poniższy kod generuje teraz C4091 włączonego ostrzeżenia poziomu 2 dla wszystkich czterech deklaracji:

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

Aby usunąć ostrzeżenia, komentarz lub usuń puste deklaracji. W przypadkach, gdzie nienazwane obiektu jest przeznaczona do ma efekt uboczny, (na przykład RAII) powinna mieć nazwę.

To ostrzeżenie jest wyłączone na podstawie **/WV: 18** i jest włączona domyślnie w ramach ostrzeżenie W2 poziomu.

### <a name="stdisconvertible-for-array-types"></a>`std::is_convertible` dla typów macierzy

Poprzednie wersje kompilatora udostępniła niepoprawne wyniki dla [std::is_convertible](../standard-library/is-convertible-class.md) dla typów macierzy. Wymaga to autorów biblioteki, aby szczególny firmy Microsoft C++ kompilatora, korzystając z `std::is_convertible<...>` cechy typu. W poniższym przykładzie statycznej potwierdza — dostęp próbny we wcześniejszych wersjach programu Visual Studio, ale się nie powieść w programie Visual Studio 2017 w wersji 15.3:

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>` jest obliczana na podstawie sprawdzania, jeśli definicja funkcji urojone jest poprawnie sformułowany:

```cpp
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdisconstructible"></a>Destruktory prywatnych oraz `std::is_constructible`

Poprzednie wersje kompilatora ignorowane czy destruktor jest prywatny, podczas podejmowania decyzji o wyniku [std::is_constructible](../standard-library/is-constructible-class.md). Teraz traktuje je. W poniższym przykładzie statycznej potwierdza — dostęp próbny we wcześniejszych wersjach programu Visual Studio, ale się nie powieść w programie Visual Studio 2017 w wersji 15.3:

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

Destruktory prywatnej spowodować, że typ, który ma być inne niż konstrukcyjną. `std::is_constructible<T, Args...>` oblicza się tak, jakby były zapisywane następującą deklarację:

```cpp
   T obj(std::declval<Args>()...)
```

To wywołanie oznacza wywołanie destruktora.

### <a name="c2668-ambiguous-overload-resolution"></a>C2668: Rozpoznanie przeciążenia niejednoznaczne

Poprzednie wersje kompilatora czasami nie można wykryć niejednoznaczności, kiedy znalezionym wielu kandydatów za pośrednictwem zarówno za pomocą deklaracje i wyszukiwania zależnego od argumentów. Ten błąd może prowadzić do niewłaściwej przeciążenia, wybierany i nieoczekiwane zachowanie. W poniższym przykładzie Visual Studio 2017 w wersji 15.3 zgłasza poprawnie C2668 "f": niejednoznaczne wywołanie przeciążonej funkcji:

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

Aby naprawić kod, usunąć używając `N::f` instrukcji, jeśli Twoim zamiarem było wywołanie `::f()`.

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660: deklaracje funkcji lokalnej i wyszukiwania zależnego od argumentów

Deklaracje funkcji lokalnej ukrycie deklaracji funkcji w zasięgu i wyłączyć wyszukiwanie zależne od argumentów. Jednakże poprzednie wersje kompilatora wykonywane wyszukiwania zależnego od argumentów w tym przypadku prowadzącego do niewłaściwej przeciążenia wybierany i nieoczekiwane zachowanie. Zazwyczaj ten błąd jest ze względu na nieprawidłowy podpis w deklaracji funkcji lokalnej. W poniższym przykładzie Visual Studio 2017 w wersji 15.3 zgłasza poprawnie C2660 "f": funkcja nie przyjmuje dwa argumenty:

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

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038: kolejność inicjowanie w listy inicjatorów

Elementy członkowskie klasy są inicjowane w kolejności, w której są one zdeklarowane nie kolejności, w której są wyświetlane na listach inicjatora. Poprzednie wersje kompilatora nie Ostrzegaj, gdy kolejność na liście inicjatora różnił się od kolejności deklaracji. Ten problem może prowadzić do niezdefiniowanego zachowania, jeśli Inicjalizacja jednego członka zależała od innego członka na liście, który został już zainicjowany. W poniższym przykładzie Visual Studio 2017 w wersji 15.3 (przy użyciu **/Wall**) zgłasza "ostrzeżenie C5038: element członkowski danych"A::y"zostanie zainicjowany po"A::x"element członkowski danych":

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

Aby rozwiązać ten problem, należy zorganizować na liście inicjatora, aby mieć takiej samej kolejności jak deklaracji. Ostrzeżenie podobne jest wywoływane, gdy jeden lub oba inicjatory się odwoływać do członków klasy podstawowej.

To ostrzeżenie jest wyłączone domyślnie, a tylko wpływa na kod skompilowany przy użyciu **/Wall**.

## <a name="update_155"></a> Poprawki błędów i inne zmiany zachowania w programie Visual Studio 2017 w wersji 15.5

### <a name="partial-ordering-change"></a>Częściowe porządkowanie zmiany

Kompilator teraz poprawnie odrzuca następujący kod i zapewnia odpowiedni komunikat o błędzie:

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

Problem w powyższym przykładzie zakłada, że dwie różnice w typach (const a niestały i dodatkiem Service pack, a-pack). Aby wyeliminować ten błąd kompilatora, usuń jedną z różnic. Dzięki temu kompilator, aby jednoznacznie kolejność funkcji.

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

Programy obsługi, odwołania do typu tablicy lub funkcji są nigdy nie pasuje do dowolnego obiektu wyjątku. Kompilator teraz poprawnie honoruje tę regułę i generuje ostrzeżenie poziom 4. Również nie jest już zgodny program obsługi `char*` lub `wchar_t*` z ciągiem literału gdy **/Zc: strictstrings** jest używany.

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

Poniższy kod pozwala uniknąć błąd:

```cpp
catch (int (*)[1]) {}
```

### <a name="tr1"></a> `std::tr1` przestrzeń nazw jest przestarzały.

Niestandardowego typu `std::tr1` przestrzeni nazw jest teraz oznaczone jako przestarzałe w języku C ++ 14 i C ++ 17 tryby. W programie Visual Studio 2017 w wersji 15.5 poniższy kod generuje C4996:

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

### <a name="annex_d"></a> Funkcje biblioteki standardowej, w załączniku D są oznaczone jako przestarzałe

Gdy **/STD: c ++ 17** tryb przełącznika kompilatora jest ustawiona, prawie wszystkie funkcje biblioteki standardowej, w załączniku D są oznaczone jako przestarzałe.

W programie Visual Studio 2017 w wersji 15.5 poniższy kod generuje C4996:

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

Aby naprawić błąd, postępuj zgodnie z instrukcjami w tekst ostrzeżenia, jak pokazano w poniższym kodzie:

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

W programie Visual Studio 15.5 ostrzeżenie C4189 jest emitowane w większości przypadków, jak pokazano w poniższym kodzie:

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}
```

```Output
warning C4189: 's': local variable is initialized but not referenced
```

Aby naprawić błąd, Usuń nieużywaną zmienną.

### <a name="single-line-comments"></a>Komentarze jednowierszowe

W programie Visual Studio 2017 w wersji 15.5 ostrzeżenia C4001 i C4179 są już emitowane przez kompilator C. Wcześniej tylko zostały emitowane w obszarze **/Za** przełącznika kompilatora.  Ostrzeżenia są już potrzebne, ponieważ Komentarze jednowierszowe zostały częścią standardu języka C od C99.

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

Jeśli kod nie potrzeba zgodne ze starszymi wersjami, można uniknąć ostrzeżenia, usuwając pomijanie C4001/C4179. Jeśli kod musi być zgodne z poprzednimi wersjami, Pomiń C4619 tylko.

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="declspec-attributes-with-extern-c-linkage"></a>`__declspec` atrybuty atrybutem `extern "C"` powiązania

We wcześniejszych wersjach programu Visual Studio, kompilator ignorowane `__declspec(...)` atrybuty kiedy `__declspec(...)` została zastosowana przed `extern "C"` Specyfikacja powiązania. To zachowanie, które spowodowało kod, aby był generowany tak, że użytkownik przypadkowo mających wpływ na możliwości środowiska uruchomieniowego. Ostrzeżenie został dodany do programu Visual Studio w wersji 15.3, ale było domyślnie wyłączone. W programie Visual Studio 2017 w wersji 15.5 to ostrzeżenie jest domyślnie włączona.

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

Aby naprawić błąd, umieść Specyfikacja powiązania przed atrybut __declspec:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Nowe ostrzeżenie C4768 jest podany na niektóre nagłówki Windows SDK, które były dostarczane z programem Visual Studio 2017 15.3 lub starszy (na przykład: wersji 10.0.15063.0, znany także jako RS2 SDK). Jednak nowsze wersje zestawu Windows SDK nagłówki (w szczególności ShlObj.h i ShlObj_core.h) została naprawiona, aby ich nie generują ostrzeżenie. Po wyświetleniu tego ostrzeżenia, pochodzące z zestawu Windows SDK nagłówków, można wykonać następujące akcje:

1. Przełącz się do najnowszy zestaw Windows SDK, dołączony do programu Visual Studio 2017 w wersji 15.5.

1. Wyłącz ostrzeżenie wokół #include instrukcji nagłówka zestawu Windows SDK:

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern_linkage"></a>Extern constexpr powiązania

We wcześniejszych wersjach programu Visual Studio, kompilator zawsze udostępniła `constexpr` zmiennej zewnętrzne, nawet wtedy, gdy zmienna została oznaczona jako `extern`. W programie Visual Studio 2017 w wersji 15.5, nowy przełącznik ( **/Zc: externconstexpr**) umożliwia poprawne zachowanie zgodne z normami. Ostatecznie to zachowanie będzie domyślnie.

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

Jeśli nagłówek pliku zawiera zmiennej zadeklarowanej `extern constexpr`, musi być oznaczony `__declspec(selectany)` zapewnienie jego deklaracji zduplikowanych połączone prawidłowo:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>`typeid` Nie można używać w typie niekompletnej klasy

We wcześniejszych wersjach programu Visual Studio kompilator może niepoprawnie następujący kod, co potencjalnie nieprawidłowe informacje o typie. W programie Visual Studio 2017 w wersji 15.5 kompilator poprawnie zgłasza błąd:

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdisconvertible-target-type"></a>`std::is_convertible` Typ docelowy

`std::is_convertible` wymaga typu docelowego i być prawidłowym typem zwracanym. We wcześniejszych wersjach programu Visual Studio kompilator może niepoprawnie typy abstrakcyjne, które mogą prowadzić do rozwiązania przeciążenia niepoprawne i niezamierzone zachowanie.  Poniższy kod teraz zgłasza poprawnie C2338:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5
```

Aby uniknąć tego błędu, używając `is_convertible` można porównać typów wskaźnika, ponieważ porównania bez typu wskaźnika może zakończyć się niepowodzeniem, jeśli jeden typ jest abstrakcyjny:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");
```

### <a name="noexcept_removal"></a> Usuwanie specyfikacji wyjątków dynamicznych i `noexcept`

W języku C ++ 17 `throw()` jest aliasem dla `noexcept`, `throw(<type list>)` i `throw(...)` są usuwane, i mogą obejmować niektóre typy `noexcept`. Ta zmiana może spowodować problemy ze zgodnością źródła z kodem, który jest zgodny, C ++ 14 lub wcześniej. **/Zc:noexceptTypes-** przełącznik może służyć do przywrócenia do języka C ++ 14 wersji `noexcept` podczas korzystania z języka C ++ 17 trybu ogólnie rzecz biorąc. Umożliwia to aktualizację kodzie źródłowym, aby były zgodne ze C ++ 17, bez konieczności ponownego zapisania wszystkich swoje `throw()` kodu w tym samym czasie.

Kompilator jest teraz również diagnozuje więcej specyfikacje wyjątków niezgodne w deklaracjach trybem C ++ 17, lub za pomocą **/ permissive-** nowe ostrzeżenie C5043.

Poniższy kod generuje C5043 i C5040 w programie Visual Studio 2017 w wersji 15.5 podczas **/STD: c ++ 17** stosowany przełącznik:

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

Aby usunąć błędy podczas korzystania z nadal **/STD: c ++ 17**, Dodaj **/Zc:noexceptTypes-** przejdź do wiersza polecenia, w przeciwnym razie aktualizacji kodu, aby użyć `noexcept`, jak pokazano w poniższym przykładzie:

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

Elementy członkowskie danych statycznych constexpr niejawnie są teraz w tekście, co oznacza, że ich deklaracji w obrębie klasy jest teraz ich definicji. Przy użyciu definicji poza wierszem dla składowej danych statycznych constexpr jest nadmiarowy i obecnie przestarzałe. W programie Visual Studio 2017 w wersji 15.5 gdy **/STD: c ++ 17** stosowany przełącznik następujący kod teraz generuje ostrzeżenie C5041 *"size": definicji poza wierszem dla składowej danych statycznych constexpr jest niepotrzebna i jest przestarzała w języku C ++ 17*:

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-declspec-warning-c4768-now-on-by-default"></a>`extern "C" __declspec(...)` Ostrzeżenie C4768 teraz na domyślnie

Ostrzeżenie został dodany w programie Visual Studio 2017 w wersji 15.3, ale było domyślnie wyłączone. W programie Visual Studio 2017 w wersji 15.5 to ostrzeżenie jest domyślnie włączone. Aby uzyskać więcej informacji, zobacz [nowe ostrzeżenie na \_ \_atrybuty declspec](#declspec).

### <a name="defaulted-functions-and-declspecnothrow"></a>Domyślnie funkcje i `__declspec(nothrow)`

Kompilator umożliwiało funkcji domyślnych, które mają zostać zadeklarowane za pomocą `__declspec(nothrow)` po z odpowiednimi funkcjami bazowych/składowych dozwolone wyjątków. To zachowanie jest sprzeczna C++ standardowe i może spowodować niezdefiniowane zachowanie w czasie wykonywania. Standard wymaga tych funkcji jest zdefiniowany jako usunięty, jeśli wystąpi niezgodność specyfikacji wyjątku.  W obszarze **/STD: c ++ 17**, poniższy kod zgłasza C2280 *próby odwoływać się do usuniętej funkcji. Funkcja została niejawnie usunięta, ponieważ jawna Specyfikacja wyjątku jest niezgodna ze deklaracji niejawnej.*

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

Aby poprawić ten kod, Usuń __declspec(nothrow) funkcję domyślne lub usuń `= default` i zawierają definicje dla funkcji oraz wszelkie wymagane wyjątków:

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

### <a name="noexcept-and-partial-specializations"></a>`noexcept` i specjalizacjami częściowymi

Za pomocą `noexcept` w systemie typów częściowych specjalizacji dopasowanie określone typy "wywoływalnej" może zakończyć się niepowodzeniem kompilować lub Wybierz podstawowy szablon ze względu na brak częściowej specjalizacji dla wskaźników do noexcept funkcji.

W takich przypadkach użytkownik może być konieczne dodanie dodatkowych specjalizacjami częściowymi do obsługi `noexcept` wskaźniki funkcji i `noexcept` wskaźników do elementów członkowskich. Taka przeciążona funkcja sprawdza tylko są dopuszczalne w **/STD: c ++ 17** trybu. Jeśli należy zachować zgodności z poprzednimi wersjami z C ++ 14 i pisania kodu, używanie przez innych użytkowników, a następnie należy zabezpieczyć te nowe przeciążenia wewnątrz `#ifdef` dyrektywy. Jeśli pracujesz w module niezależny, a następnie zamiast `#ifdef` osłony, można po prostu kompilacji z **/Zc:noexceptTypes-** przełącznika.

Poniższy kod jest kompilowany w obszarze **/STD: c ++ 14** , ale nie powiedzie się w obszarze **/STD: c ++ 17** z "błąd C2027:use niezdefiniowanego typu" A\<T > "":

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

Poniższy kod zakończy się powodzeniem, w obszarze **/STD: c ++ 17** ponieważ kompilator wybiera nowy częściowa specjalizacja `A<void (*)() noexcept>`:

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

## <a name="update_157"></a> Poprawki błędów i inne zmiany zachowania w programie Visual Studio 2017 wersji 15.7

### <a name="c17-default-argument-in-the-primary-class-template"></a>C++17: Argument domyślny w szablonie klasy podstawowej

Ta zmiana zachowanie jest warunkiem wstępnym [Wnioskowanie argumentu szablonu dla szablonów klas - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html).

Wcześniej kompilator zignorowano argument domyślny w szablonie klasy głównej:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

W **/STD: c ++ 17** tryb w programie Visual Studio 2017 wersji 15.7, domyślnego argumentu nie jest ignorowany:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>Rozpoznawanie nazw zależnych

Ta zmiana zachowanie jest warunkiem wstępnym [Wnioskowanie argumentu szablonu dla szablonów klas - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html).

W poniższym przykładzie, kompilator w Visual Studio 15.6 i starszych rozpoznaje `D::type` do `B<T>::type` w szablonie klasy podstawowej.

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

Visual Studio 2017 w wersji 15.7, w **/STD: c ++ 17** tryb, wymaga `typename` — słowo kluczowe w `using` instrukcji w D. Bez `typename`, wywołuje kompilatora ostrzeżenie C4346: *"B < T\*>:: typu": zależna nazwa nie jest typem* i błąd C2061: *błąd składniowy: identyfikator "type"* :

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

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C ++ 17: `[[nodiscard]]` atrybut — ostrzeżenie zwiększenie poziomu

W programie Visual Studio 2017 wersji 15.7 w **/STD: c ++ 17** trybie poziom ostrzeżenia C4834 (odrzucanie zwracanej wartości funkcji z atrybutem "nodiscard" ") został podniesiony z W3 na W1. Można wyłączyć ostrzeżenia o rzutowania `void`, lub przez przekazanie **/wd:4834** w kompilatorze

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Ze zmienną liczbą argumentów szablonu konstruktora klasy bazowej inicjalizacji listy

W poprzednich wersjach programu Visual Studio ze zmienną liczbą argumentów szablonu konstruktora klasy bazowej inicjowania listę, która nie zawierał argumentów szablonu został błędnie dozwolona bez błędów. W programie Visual Studio 2017 wersji 15.7 zgłaszany jest błąd kompilatora.

Poniższy przykład kodu w programie Visual Studio 2017 w wersji 15.7 zgłasza *błąd C2614: D\<int >: niedozwolone inicjowanie składowej: "B" nie jest obiektem bazowym ani składową*

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

Aby naprawić błąd, zmień wyrażenie B() b\<T > ().

### <a name="constexpr-aggregate-initialization"></a>`constexpr` Inicjowanie agregacji

Poprzednie wersje C++ kompilatora nieprawidłowo obsługiwane `constexpr` inicjowania agregacji; it zaakceptowane nieprawidłowego kodu, w którym ma za dużo elementów listy inicjowania agregacji i generowane Generowanie nieprawidłowego kodu dla niego. Poniższy kod jest przykładem takiego kodu:

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

W programie Visual Studio 2017 w wersji 15.7 z aktualizacją 3 lub nowszym, zgłasza teraz poprzedni przykład *C2078 zbyt wiele inicjatorów*. Poniższy przykład pokazuje, jak naprawić kod. Podczas inicjowania `std::array` zagnieżdżonych nawiasów klamrowych list inicjacji, nadaj wewnętrzny tablicy w nawiasach klamrowych listę swój własny:

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

## <a name="update_158"></a> Poprawki i zmiany zachowania w programie Visual Studio 2017 wersja 15.8

Zmiany w kompilatorze w programie Visual Studio 2017 wersja 15.8 wszystkie należą do kategorii poprawki i zmiany sposobu działania i są wymienione poniżej:

### <a name="typename-on-unqualified-identifiers"></a>`typename` na niekwalifikowanej identyfikatorów

W [/ permissive-](../build/reference/permissive-standards-conformance.md) tryb fałszywe `typename` słowa kluczowe na niekwalifikowanej identyfikatorów w definicjach szablonów alias już nie są akceptowane przez kompilator. Poniższy kod generuje teraz C7511 *t ": słowo kluczowe"typename"musi następować kwalifikowana nazwa*:

```cpp
template <typename T>
using  X = typename T;
```

Aby naprawić błąd, zmień drugi wiersz do `using  X = T;`.

### <a name="declspec-on-right-side-of-alias-template-definitions"></a>`__declspec()` po prawej stronie definicji szablonu aliasu

[__declspec](../cpp/declspec.md) już nie jest dozwolona na po prawej stronie definicji szablonu aliasu. Ten kod został wcześniej zaakceptowano używanie usługi, ale ignorowane przez kompilator i nigdy nie będzie powodować ostrzeżenie o zakończeniu obsługi stosowania aliasu.

Standardowa C++ atrybut [ \[ \[przestarzałe\] \] ](../cpp/attributes.md) mogą być używane zamiast i jest zachowana w programie Visual Studio 2017 w wersji 15.6. Poniższy kod generuje teraz C2760 *błąd składniowy: nieoczekiwany token "__declspec", oczekiwano "Specyfikator typu"* :

```cpp
template <typename T>
using X = __declspec(deprecated("msg")) T;
```

Aby naprawić błąd, Zmień kod do następujących (atrybutem umieszczony przed "=" definicji aliasu):

```cpp
template <typename T>
using  X [[deprecated("msg")]] = T;
```

### <a name="two-phase-name-lookup-diagnostics"></a>Nazwa dwufazowe wyszukiwanie diagnostyki

Dwufazowe wyszukiwanie nazw wymaga, że nazwy zależne od innych niż używane w treści szablonu muszą być widoczne w szablonie w czasie definicji. Wcześniej firmy Microsoft C++ kompilatora spowoduje, że unfound nazwę, jak nie looked aż do czasu wystąpienia. Teraz wymaga to, że zależne od innych nazw są powiązane w treści szablonu.

Jeden ze sposobów osiągnięcia tego manifestu, można to za pomocą wyszukiwania do zależnego klas bazowych. Wcześniej kompilator może nazwy, które są zdefiniowane w klasach bazowych, zależnych, ponieważ będą dzielone w czasie wystąpienia, gdy wszystkie typy są rozwiązywane. Teraz, gdy kod jest traktowany jako błąd. W takich przypadkach istnieje możliwość wymuszenia zmiennej, aby wyszukiwać w momencie konkretyzacji przez kwalifikujących się on z typem klasy bazowej lub w przeciwnym razie co zależnych, na przykład dodając `this->` wskaźnika.

W **/ permissive-** tryb, poniższy kod zgłasza teraz C3861: *"base_value": nie odnaleziono identyfikatora*:

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

Aby naprawić błąd, zmień `return` instrukcję, aby `return this->base_value;`.

**Uwaga:** W bibliotece python Boost wprowadzono przez długi czas obejście MSVC specyficzne dla szablonu deklaracji do przodu w [unwind_type.hpp](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp). W obszarze [/ permissive-](../build/reference/permissive-standards-conformance.md) trybu, począwszy od programu Visual Studio 2017 w wersji 15.8 (_MSC_VER = 1915), za pomocą kompilatora MSVC jest poprawnie wyszukiwania do nazwy zależnej od argumentu (ADL) i jest spójne za pomocą innych kompilatorów, dzięki czemu ochrona tego rozwiązania niepotrzebne. Aby uniknąć błędów *C3861: "unwind_type": nie odnaleziono identyfikatora*, zobacz [229 żądania Ściągnięcia](https://github.com/boostorg/python/pull/229) w repozytorium zwiększenie wydajności, aby zaktualizować plik nagłówkowy. Firma Microsoft została już zastosować poprawki względem jakiegokolwiek [vcpkg](../build/vcpkg.md) Boost pakietu, więc jeśli pobieranie lub uaktualnienie źródła Boost z vcpkg następnie nie trzeba zastosować poprawkę oddzielnie.

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>deklaracje przechodzenia do przodu i definicje w przestrzeni nazw `std`

C++ standard nie zezwala na użytkownika do dodania do przodu deklaracji lub definicji do przestrzeni nazw `std`. Dodawanie deklaracji lub definicji do przestrzeni nazw `std` lub przestrzeni nazw w ramach przestrzeni nazw `std` teraz powoduje zachowanie niezdefiniowane.

W czasie w przyszłości Microsoft zostanie przesunięty w lokalizacji, gdzie są zdefiniowane niektórych typów biblioteki standardowej. Ta zmiana spowoduje przerwanie istniejący kod, który dodaje deklaracje przechodzenia do przodu do przestrzeni nazw `std`. Nowe ostrzeżenie C4643, pomaga w identyfikowaniu problemów takich źródła. To ostrzeżenie jest włączone w **/wartość domyślna** tryb i jest domyślnie wyłączona. Będzie miało wpływ na programy, które są kompilowane przy użyciu **/Wall** lub **/WX**.

Poniższy kod zgłasza teraz C4643: *Do przodu deklarowanie "vector" w przestrzeni nazw std nie jest dozwolona przez C++ Standard*.

```cpp
namespace std {
    template<typename T> class vector;
}
```

Aby naprawić błąd, należy użyć **obejmują** dyrektywy zamiast deklaracją do przodu:

```cpp
#include <vector>
```

### <a name="constructors-that-delegate-to-themselves"></a>Konstruktory, który deleguje do siebie

C++ Standard sugeruje, że kompilatora, powinny wysyłać Diagnostyka podczas konstruktora delegującego deleguje do samego siebie. Kompilator Microsoft C++ w [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md) i [/STD: c ++ najnowsze](../build/reference/std-specify-language-standard-version.md) tryby zgłasza teraz C7535: *"X::X": Konstruktor delegujący wywołuje sam siebie*.

Bez tego błędu poniższy program zostanie skompilowany, ale wygeneruje wejścia w nieskończoną pętlę:

```cpp
class X {
public:
    X(int, int);
    X(int v) : X(v){}
};
```

Aby uniknąć nieskończoną pętlę, delegować do innego konstruktora:

```cpp
class X {
public:

    X(int, int);
    X(int v) : X(v, 0) {}
};
```

### <a name="offsetof-with-constant-expressions"></a>`offsetof` przy użyciu wyrażeń stałych

[Makro offsetof](../c-runtime-library/reference/offsetof-macro.md) tradycyjnie została zaimplementowana za pomocą makra, która wymaga [reinterpret_cast](../cpp/reinterpret-cast-operator.md). Tego użycia jest niedozwolona w kontekstach, które wymagają wyrażeniem stałym, ale Microsoft C++ kompilatora tradycyjnie jest dozwolone. `offsetof` — Makro, który jest dostarczany jako część biblioteki standardowej poprawnie używa wewnętrzne polecenie kompilatora (**wartości __builtin_offsetof**), ale wiele osób ma lewy — makro definiować własne `offsetof`.

W programie Visual Studio 2017 w wersji 15.8 kompilator ogranicza obszarów że powyższe `reinterpret_cast` operatory mogą być wyświetlane w domyślnym trybie, aby ułatwić kodu, które są zgodne ze standardem C++ zachowanie. W obszarze [/ permissive-](../build/reference/permissive-standards-conformance.md), ograniczenia są jeszcze bardziej restrykcyjne. Za pomocą wynik `offsetof` w miejscach, które wymagają wyrażeń stałych może spowodować w kodzie, generuje ostrzeżenie C4644 *użycia wzorca na podstawie — makro offsetof w wyrażeniach stałych jest niestandardowych; użyj makra offsetof zdefiniowane w C++ Standardowa biblioteka zamiast* lub C2975 *nieprawidłowy argument szablonu, oczekiwano stałego wyrażenia czasu kompilacji*.

Poniższy kod zgłasza C4644 w **/wartość domyślna** i **/STD: c ++ 17** trybów i C2975 w **/ permissive-** trybu:

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

Aby naprawić błąd, należy użyć `offsetof` zgodnie z definicją za pośrednictwem \<cstddef — >:

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

### <a name="cv-qualifiers-on-base-classes-subject-to-pack-expansion"></a>Kwalifikatory CV na klasach bazowych, które podlegają rozwinięcia pakietu

Poprzednie wersje programu Microsoft C++ kompilatora nie wykryło ono klasą bazową miały kwalifikatory cv, jeśli została również zastrzeżeniem rozwinięcie pakietu.

W programie Visual Studio 2017 wersja 15.8 w **/ permissive-** tryb poniższy kod wywołuje C3770 *"const S": nie jest prawidłową klasę podstawową*:

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x;
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>`template` słowo kluczowe i zagnieżdżone name-specifiers

W **/ permissive-** tryb, kompilator wymaga teraz `template` — słowo kluczowe poprzedzającą nazwę szablonu, jeśli chodzi po zależnych zagnieżdżonych name-specifier.

Poniższy kod w **/ permissive-** tryb zgłasza teraz C7510: *"przykładowy": użycie szablonu zależnego nazwy musi być poprzedzona znakiem "template". Uwaga: Zobacz odwołania do wystąpienia szablonu klasy "X<T>" Trwa skompilowany*:

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

Aby naprawić błąd, należy dodać `template` słowa kluczowego `Base<T>::example<int>();` instrukcji, jak pokazano w poniższym przykładzie:

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

## <a name="update_159"></a> Poprawki i zmiany zachowania w programie Visual Studio 2017 w wersji 15.9

### <a name="identifiers-in-member-alias-templates"></a>Identyfikatory w szablonach aliasów elementu członkowskiego

Identyfikator używany w składowej aliasu definicji szablonu musi być zadeklarowana przed użyciem.

W poprzedniej wersji kompilatora mógł następujący kod:

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

W programie Visual Studio 2017 w wersji 15.9 w **/ permissive-** tryb, wywołuje kompilatora C3861: *"from_template": nie odnaleziono identyfikatora*.

Aby naprawić błąd, należy zadeklarować `from_template` przed `from_template_t`.

### <a name="modules-changes"></a>Zmiany modułów

W programie Visual Studio 2017 w wersji 15.9, kompilator generuje C5050 zawsze wtedy, gdy opcje wiersza polecenia dla modułów nie są spójne Tworzenie modułu i stronach użycie modułu. W poniższym przykładzie istnieją dwa problemy:

- Użycie po stronie (main.cpp) opcja **/ehsc** nie został określony.

- C++ Wersja jest **/STD: c ++ 17** na stronie tworzenia i **/STD: c ++ 14** stronie zużycia.

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

Kompilator generuje C5050 dla obu tych przypadkach: *ostrzeżenie C5050: Jestem możliwe niezgodne środowisko podczas importowania modułu ": niezgodność wersji języka C++.  Bieżąca wersja "201402" module "201703"* .

Kompilator wywołuje również C7536 zawsze wtedy, gdy plik .ifc zostały naruszone. Nagłówek interfejsu modułu zawiera algorytmu SHA2 skrót zawartości poniżej. Przy imporcie plik .ifc skrótu w taki sam sposób, następnie porównywany wyznaczania wartości skrótu, podany w nagłówku. Jeśli te nie są zgodne, zgłaszany jest błąd C7536: *ifc sprawdzania integralności nie powiodło się.  Oczekiwano algorytmu SHA2: '66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6'* .

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>Częściowe szeregowania obejmujące aliasów i konteksty — ustalona

Implementacje rozdzielić częściowe reguł sortowania obejmujące aliasów w kontekstach — ustalona. W poniższym przykładzie, GCC i kompilator C++ firmy Microsoft (w **/ permissive-** tryb) zgłosić błąd, podczas gdy Clang akceptuje kodu.

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

Poprzedni przykład wywołuje C2668:

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

Rozbieżności wdrożenia jest z powodu Regresja w C++ standardowa treść. Rozwiązanie do kluczową kwestię 2235 usunięte jakiś tekst, które pozwoliłoby te przeciążenia do zamówienia. Bieżący C++ standard nie udostępniają mechanizm częściowo kolejności tych funkcji, aby były uważane niejednoznaczne.

Obejść ten problem zaleca się, że użytkownik nie zależą od częściowe porządkowanie, aby rozwiązać ten problem. Zamiast tego należy użyć SFINAE można usunąć określonego przeciążenia. W poniższym przykładzie użyto klasę pomocy `IsA` do usunięcia pierwszego przeciążenia, kiedy `Alloc` jest specjalizacją `A`:

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

### <a name="illegal-expressions-and-non-literal-types-in-templated-function-definitions"></a>Niedozwolony wyrażeń i typy literału definicje funkcji oparte na szablonach

Niedozwolony wyrażeń i typy literału teraz są poprawnie zdiagnozować w definicji funkcji oparte na szablonach, które są jawnie specjalizowany. Wcześniej takie błędy nie zostały wyemitowane dla definicji funkcji. Jednak niedozwolone wyrażenie lub typem literału będzie nadal mieć rozpoznano Jeśli ocenione jako część wyrażeniem stałym.

W poprzednich wersjach programu Visual Studio poniższy kod jest kompilowany bez ostrzeżenia:

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

W programie Visual Studio 2017 w wersji 15.9 kod generuje ten błąd:

```Output
error C3615: constexpr function 'S<int>::f' cannot result in a constant expression.
note: failure was caused by call of undefined function or one not declared 'constexpr'
note: see usage of 'g'.
```

Aby uniknąć tego błędu, Usuń `constexpr` kwalifikator z jawnym utworzeniem wystąpienia funkcji `f()`.

::: moniker-end

## <a name="c-conformance-improvements-in-visual-studio-2015"></a>C++ulepszenia zgodności w programie Visual Studio 2015

Aby uzyskać pełną listę ulepszeń zgodność się za pomocą programu Visual Studio 2015 Update 3, zobacz [Visual C++ co w nowym roku 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="see-also"></a>Zobacz także

[Wizualne zgodność języka C++](../visual-cpp-language-conformance.md)
