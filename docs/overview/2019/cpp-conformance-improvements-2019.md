---
title: Ulepszenia zgodności języka C++
ms.date: 03/22/2019
description: Microsoft C++ w programie Visual Studio 2019 r jest postępować w kierunku pełną zgodność ze standardem 20 języka C ++.
ms.technology: cpp-language
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 331d8bd94076979f51adb0b3b7188a93d99623f0
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65404987"
---
# <a name="c-conformance-improvements-in-visual-studio-2019"></a>Ulepszenia zgodności języka C++ w Visual Studio 2019 r.

Visual Studio 2019 RTW zawiera następujące ulepszenia zgodności, poprawki i zmiany zachowania w kompilatorze Microsoft C++ (MSVC).

**Uwaga:** C ++ 20 funkcje zostaną udostępnione w `/std:c++latest` tryb zakończeniem 20 implementacji języka C ++ dla kompilatora i technologii IntelliSense. W tym czasie `/std:c++20` tryb kompilatora zostaną wprowadzone.

## <a name="conformance-improvements"></a>Ulepszenia zgodności

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

C ++ 20 wprowadza `<=>` operator porównania trzystopniowo, znany także jako "pojazdu kosmicznego operatora". Visual Studio 2019 r w `/std:c++latest` tryb wprowadza częściową obsługę dla operatora, tworząc błędy składni, która jest teraz niedozwolona. Na przykład, poniższy kod kompiluje bez błędów w programie Visual Studio 2017, ale zgłasza kilka błędów w Visual Studio 2019 r, w obszarze `/std:c++latest`:

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

## <a name="bug-fixes-and-behavior-changes"></a>Poprawki błędów i zmiany sposobu działania

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

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>Nieprawidłowe wywołania += i-= w ramach/CLR lub /ZW teraz są poprawnie wykrywane.

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

MSVC umożliwia wydajność ostrzeżenie C4800 dotyczące niejawnej konwersji na bool, który był zbyt hałas i insuppressible, prowadząc z nami, aby usunąć go w programie VS 2017. Jednak z cyklem programu VS 2017 mamy mnóstwo informacji zwrotnych na przydatne w przypadkach, którego został on rozwiązywania. Możemy przywrócić w Visual Studio 2019 starannie dopasowane C4800 wraz z jego C4165 towarzyszącego, które można łatwo pominąć za pomocą jawnego rzutowania lub porównanie 0 odpowiedniego typu. C4800 jest to ostrzeżenie wyłączone domyślnie poziom 4, a C4165 jest to ostrzeżenie wyłączone domyślnie poziom 3. Oba są wykrywalni przy użyciu `/Wall` — opcja kompilatora.

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

### <a name="clr-now-incompatible-with-stdclatest"></a>/ CLR jest teraz niezgodna z/STD: c ++ najnowsze

Po rozpoczęciu MSVC implementowania funkcji z języka C ++ 20 standardowy projekt w obszarze `/std:c++latest` flagi `/std:c++latest` jest teraz niezgodna z `/clr` (wszystkie odmian) `/ZW`, i `/Gm`. W programie Visual Studio 2019 r, użyj `/std:c++17` lub `/std:c++14` tryby podczas kompilowania za pomocą `/clr`, `/ZW` lub `/Gm`.

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

## <a name="see-also"></a>Zobacz także

[What's new in Visual Studio 2019 r.](../what-s-new-for-visual-cpp-in-visual-studio.md)