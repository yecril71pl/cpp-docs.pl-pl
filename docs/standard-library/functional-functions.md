---
title: '&lt;&gt;funkcje funkcjonalne'
ms.date: 02/21/2019
f1_keywords:
- functional/std::bind
- functional/std::bind1st
- functional/std::bind2nd
- functional/std::bit_and
- functional/std::bit_not
- functional/std::bit_or
- functional/std::bit_xor
- functional/std::cref
- type_traits/std::cref
- functional/std::mem_fn
- functional/std::mem_fun_ref
- functional/std::not1
- functional/std::not2
- functional/std::not_fn
- functional/std::ptr_fun
- functional/std::ref
- functional/std::swap
helpviewer_keywords:
- std::bind [C++]
- std::bind1st
- std::bind2nd
- std::bit_and [C++]
- std::bit_not [C++]
- std::bit_or [C++]
- std::bit_xor [C++]
- std::cref [C++]
ms.assetid: c34d0b45-50a7-447a-9368-2210d06339a4
ms.openlocfilehash: 5e3aa35395c8fd5a42d7127d0b6072a3edf4ace5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838090"
---
# <a name="ltfunctionalgt-functions"></a>&lt;&gt;funkcje funkcjonalne

Te funkcje są przestarzałe w języku C++ 11 i zostały usunięte w języku C++ 17:

[bind1st —](#bind1st)\
[bind2nd —](#bind2nd)\
[mem_fun](#mem_fun)\
[mem_fun_ref](#mem_fun_ref)\
[ptr_fun](#ptr_fun)

Te funkcje są przestarzałe w języku C++ 17:

[not1 —](#not1)\
[not2 —](#not2)

## <a name="bind"></a><a name="bind"></a> węglowodor

Tworzy powiązania argumentów z wywoływanym obiektem.

```cpp
template <class FT, class T1, class T2, ..., class TN>
    unspecified bind(FT fn, T1 t1, T2 t2, ..., TN tN);

template <class RTy, class FT, class T1, class T2, ..., class TN>
    unspecified bind(FT fn, T1 t1, T2 t2, ..., TN tN);
```

### <a name="parameters"></a>Parametry

*Fey*\
Typ obiektu do wywołania.

*TN*\
Typ argumentu n wywołania.

*Fn*\
Obiekt, który ma zostać wywołany.

*tN*\
N-ty argument wywołania.

### <a name="remarks"></a>Uwagi

Typy `FT, T1, T2, ..., TN` muszą mieć wartość Copy-konstrukcyjną i `INVOKE(fn, t1, ..., tN)` musi być prawidłowym wyrażeniem dla niektórych wartości `w1, w2, ..., wN` .

Pierwsza funkcja szablonu zwraca otokę wywołań przekazywania `g` z słabym typem wyniku. Efekt `g(u1, u2, ..., uM)` jest `INVOKE(f, v1, v2, ..., vN,` [invoke_result](../standard-library/invoke-result-class.md) `<FT cv (V1, V2, ..., VN)>::type)` , gdzie `cv` jest kwalifikatory CV `g` i wartości i typy powiązanych argumentów `v1, v2, ..., vN` są określone poniżej. Służy do powiązania argumentów z wywoływanym obiektem, aby wykonać wywoływany obiekt z listą argumentów, które można wywołać.

Druga funkcja szablonu zwraca otokę wywołania przekazywania `g` z zagnieżdżonym typem `result_type` , który jest synonimem dla `RTy` . Efektem `g(u1, u2, ..., uM)` jest `INVOKE(f, v1, v2, ..., vN, RTy)` , gdzie `cv` jest kwalifikatory CV `g` i wartości i typy powiązanych argumentów `v1, v2, ..., vN` są określone poniżej. Służy do powiązania argumentów z wywoływanym obiektem, aby wykonać wywoływany obiekt z listą argumentów o dopasowanej postaci i z określonym typem zwracanym.

Wartości powiązanych argumentów `v1, v2, ..., vN` i odpowiadające im typy `V1, V2, ..., VN` zależą od typu odpowiadającego argumentu `ti` typu `Ti` w wywołaniu `bind` i kwalifikatory CV `cv` otoki wywołania `g` w następujący sposób:

Jeśli `ti` jest `reference_wrapper<T>` argumentem typu, `vi` `ti.get()` a jego typ `Vi` to `T&` ;

Jeśli wartość `std::is_bind_expression<Ti>::value` jest **`true`** argumentu `vi` `ti(u1, u2, ..., uM)` i jego typ `Vi` to `result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type` ;

Jeśli wartość `j` nie jest `std::is_placeholder<Ti>::value` równa zero, argument `vi` jest `uj` i jego typ `Vi` to `Uj&` ;

w przeciwnym razie argument `vi` jest `ti` i jego typem `Vi` jest `Ti` `cv` `&` .

Na przykład w przypadku funkcji `f(int, int)` wyrażenie `bind(f, _1, 0)` zwraca otokę wywołania przekazującego `cw` , taką, która `cw(x)` wywołuje `f(x, 0)` . Wyrażenie `bind(f, 0, _1)` zwraca otokę wywołania przekazującego `cw` , taką, która `cw(x)` wywołuje `f(0, x)` .

Liczba argumentów w wywołaniu `bind` i argumencie `fn` musi być równa liczbie argumentów, które mogą być przekazane do możliwego do wywołania obiektu `fn` . Na przykład `bind(cos, 1.0)` jest poprawna, a oba `bind(cos)` i `bind(cos, _1, 0.0)` są nieprawidłowe.

Liczba argumentów w wywołaniu funkcji do otoki wywołań zwracanych przez `bind` musi być co najmniej tak duża jak najwyższa wartość numerowana `is_placeholder<PH>::value` dla wszystkich argumentów symbolu zastępczego w wywołaniu `bind` . Na przykład, `bind(cos, _2)(0.0, 1.0)` jest poprawne (i zwraca `cos(1.0)` ) i `bind(cos, _2)(0.0)` jest niepoprawne.

### <a name="example"></a>Przykład

```cpp
// std__functional__bind.cpp
// compile with: /EHsc
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std::placeholders;

void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

void product(double x, double y)
{
    std::cout << x << "*" << y << " == " << x * y << std::endl;
}

int main()
{
    double arg[] = { 1, 2, 3 };

    std::for_each(&arg[0], arg + 3, square);
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(product, _1, 2));
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(square, _1));

    return (0);
}
```

```Output
1^2 == 1
2^2 == 4
3^2 == 9

1*2 == 2
2*2 == 4
3*2 == 6

1^2 == 1
2^2 == 4
3^2 == 9
```

## <a name="bind1st"></a><a name="bind1st"></a> bind1st —

Funkcja szablonu pomocnika, która tworzy adapter do przekonwertowania obiektu funkcji binarnej na jednoargumentowy obiekt funkcji. Wiąże pierwszy argument funkcji Binary z określoną wartością. Przestarzałe w języku C++ 11, usunięte w języku C++ 17.

```cpp
template <class Operation, class Type>
    binder1st <Operation> bind1st (const Operation& func, const Type& left);
```

### <a name="parameters"></a>Parametry

*Func*\
Obiekt funkcji binarnej do przekonwertowania na jednoargumentowy obiekt funkcji.

*lewym*\
Wartość, do której należy powiązać pierwszy argument obiektu funkcji binarnej.

### <a name="return-value"></a>Wartość zwracana

Jednoargumentowy obiekt funkcji, który jest wynikiem powiązania pierwszego argumentu obiektu funkcji binarnej z wartością *pozostawioną*.

### <a name="remarks"></a>Uwagi

Powiązania funkcji są rodzajem adaptera funkcji. Ponieważ zwracają one obiekty funkcji, mogą one być używane w niektórych typach kompozycji funkcji do konstruowania bardziej złożonych i zaawansowanych wyrażeń.

Jeśli *Func* jest obiektem typu `Operation` i `c` jest stałą, `bind1st( func, c )` to jest taka sama jak Konstruktor klasy [binder1st —](../standard-library/binder1st-class.md) `binder1st<Operation>(func, c)` i jest bardziej wygodna do użycia.

### <a name="example"></a>Przykład

```cpp
// functional_bind1st.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan5: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 5);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1a;
    result1a = count_if(v1.begin(), v1.end(), bind1st(less<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1a << "." << endl;

    // Compare: counting the number of integers > 5 in the vector
    // with a user defined function object
    vector<int>::iterator::difference_type result1b;
    result1b = count_if(v1.begin(), v1.end(), greaterthan5());
    cout << "The number of elements in v1 greater than 5 is: "
         << result1b << "." << endl;

    // Count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(), bind2nd(less<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 greater than 5 is: 4.
The number of elements in v1 less than 10 is: 2.
```

## <a name="bind2nd"></a><a name="bind2nd"></a> bind2nd —

Funkcja szablonu pomocnika, która tworzy adapter do przekonwertowania obiektu funkcji binarnej na jednoargumentowy obiekt funkcji. Wiąże drugi argument funkcji Binary z określoną wartością. Przestarzałe w języku C++ 11, usunięte w języku C++ 17.

```cpp
template <class Operation, class Type>
    binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```

### <a name="parameters"></a>Parametry

*Func*\
Obiekt funkcji binarnej do przekonwertowania na jednoargumentowy obiekt funkcji.

*Kliknij*\
Wartość, do której należy powiązać drugi argument obiektu funkcji binarnej.

### <a name="return-value"></a>Wartość zwracana

Obiekt funkcji jednoargumentowej wynik powiązania drugiego argumentu obiektu funkcji binarnej z *prawą*.

### <a name="remarks"></a>Uwagi

Powiązania funkcji są rodzajem adaptera funkcji. Ponieważ zwracają one obiekty funkcji, mogą one być używane w niektórych typach kompozycji funkcji do konstruowania bardziej złożonych i zaawansowanych wyrażeń.

Jeśli *Func* jest obiektem typu `Operation` i `c` jest stałą, `bind2nd(func, c)` to jest taka sama jak Konstruktor klasy [binder2nd —](../standard-library/binder2nd-class.md) i jest `binder2nd<Operation>(func, c)` bardziej wygodna do użycia.

### <a name="example"></a>Przykład

```cpp
// functional_bind2nd.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan15: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 15);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1a;
    result1a = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1a << "." << endl;

    // Compare counting the number of integers > 15 in the vector
    // with a user-defined function object
    vector<int>::iterator::difference_type result1b;
    result1b = count_if(v1.begin(), v1.end(), greaterthan15());
    cout << "The number of elements in v1 greater than 15 is: "
         << result1b << "." << endl;

    // Count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(), bind1st(greater<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 greater than 15 is: 2.
The number of elements in v1 less than 10 is: 2.
```

## <a name="bit_and"></a><a name="bit_and"></a> bit_and

Wstępnie zdefiniowany obiekt funkcji, który wykonuje operacje bitowe i operacji (Binary `operator&` ) w argumentach.

```cpp
template <class Type = void>
struct bit_and : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator&
template <>
struct bit_and<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const  ->
        decltype(std::forward<T>(Left) & std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parametry

*Typ*, *T*, *U*\
Dowolny typ, który obsługuje element `operator&` , który pobiera operandy określonego lub wywnioskowanego typu.

*Lewym*\
Lewy operand operacji bitowej i. Niewyspecjalizowany szablon przyjmuje argument odwołania lvalue *typu.* Szablon wyspecjalizowany jest idealnym przekazywaniem argumentów odwołania lvalue i rvalue dla typu wywnioskowanego *T*.

*Kliknij*\
Prawy operand operacji koniunkcji binarnej. Niewyspecjalizowany szablon przyjmuje argument odwołania lvalue *typu.* Szablon wyspecjalizowany jest idealnym przekazywaniem argumentów odwołania lvalue i rvalue dla typu wywnioskowanego *U*.

### <a name="return-value"></a>Wartość zwracana

Wynik `Left & Right` . Wyspecjalizowany szablon robi doskonałe przekazywanie wyniku, który ma typ zwracany przez `operator&` .

### <a name="remarks"></a>Uwagi

`bit_and`Funktor jest ograniczone do typów całkowitych dla podstawowych typów danych lub do typów zdefiniowanych przez użytkownika, które implementują dane binarne `operator&` .

## <a name="bit_not"></a><a name="bit_not"></a> bit_not

Wstępnie zdefiniowany obiekt funkcji, który wykonuje operacje uzupełniania bitowego (nie) (jednoargumentowe `operator~` ) dla tego argumentu. Dodano w języku C++ 14.

```cpp
template <class Type = void>
struct bit_not : public unary_function<Type, Type>
{
    Type operator()(const Type& Right) const;
};

// specialized transparent functor for operator~
template <>
struct bit_not<void>
{
    template <class Type>
    auto operator()(Type&& Right) const -> decltype(~std::forward<Type>(Right));
};
```

### <a name="parameters"></a>Parametry

*Wprowadź*\
Typ, który obsługuje jednoargumentowy `operator~` .

*Kliknij*\
Operand operacji uzupełniania bitowego. Niewyspecjalizowany szablon przyjmuje argument odwołania lvalue *typu.* Szablon wyspecjalizowany jest idealnym przekazywaniem argumentu odwołania lvalue lub rvalue *typu*wywnioskowanego.

### <a name="return-value"></a>Wartość zwracana

Wynik `~ Right` . Wyspecjalizowany szablon robi doskonałe przekazywanie wyniku, który ma typ zwracany przez `operator~` .

### <a name="remarks"></a>Uwagi

`bit_not`Funktor jest ograniczone do typów całkowitych dla podstawowych typów danych lub do typów zdefiniowanych przez użytkownika, które implementują dane binarne `operator~` .

## <a name="bit_or"></a><a name="bit_or"></a> bit_or

Wstępnie zdefiniowany obiekt funkcji, który wykonuje operacje bitowe ( `operator|` ) w argumentach.

```cpp
template <class Type = void>
struct bit_or : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator|
template <>
struct bit_or<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) | std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parametry

*Typ*, *T*, *U*\
Dowolny typ, który obsługuje element `operator|` , który pobiera operandy określonego lub wywnioskowanego typu.

*Lewym*\
Lewy operand operacji bitowej or. Niewyspecjalizowany szablon przyjmuje argument odwołania lvalue *typu.* Szablon wyspecjalizowany jest idealnym przekazywaniem argumentów odwołania lvalue i rvalue dla typu wywnioskowanego *T*.

*Kliknij*\
Prawy operand operacji bitowej or. Niewyspecjalizowany szablon przyjmuje argument odwołania lvalue *typu.* Szablon wyspecjalizowany jest idealnym przekazywaniem argumentów odwołania lvalue i rvalue dla typu wywnioskowanego *U*.

### <a name="return-value"></a>Wartość zwracana

Wynik `Left | Right` . Wyspecjalizowany szablon robi doskonałe przekazywanie wyniku, który ma typ zwracany przez `operator|` .

### <a name="remarks"></a>Uwagi

`bit_or`Funktor jest ograniczone do typów całkowitych dla podstawowych typów danych lub do typów zdefiniowanych przez użytkownika, które implementują `operator|` .

## <a name="bit_xor"></a><a name="bit_xor"></a> bit_xor

Wstępnie zdefiniowany obiekt funkcji, który wykonuje operacje bitowe XOR (Binary `operator^` ) na jego argumentach.

```cpp
template <class Type = void>
struct bit_xor : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator^
template <>
struct bit_xor<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) ^ std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parametry

*Typ*, *T*, *U*\
Dowolny typ, który obsługuje element `operator^` , który pobiera operandy określonego lub wywnioskowanego typu.

*Lewym*\
Lewy operand operacji bitowej XOR. Niewyspecjalizowany szablon przyjmuje argument odwołania lvalue *typu.* Szablon wyspecjalizowany jest idealnym przekazywaniem argumentów odwołania lvalue i rvalue dla typu wywnioskowanego *T*.

*Kliknij*\
Prawy operand operacji bitowej XOR. Niewyspecjalizowany szablon przyjmuje argument odwołania lvalue *typu.* Szablon wyspecjalizowany jest idealnym przekazywaniem argumentów odwołania lvalue i rvalue dla typu wywnioskowanego *U*.

### <a name="return-value"></a>Wartość zwracana

Wynik `Left ^ Right` . Wyspecjalizowany szablon robi doskonałe przekazywanie wyniku, który ma typ zwracany przez `operator^` .

### <a name="remarks"></a>Uwagi

`bit_xor`Funktor jest ograniczone do typów całkowitych dla podstawowych typów danych lub do typów zdefiniowanych przez użytkownika, które implementują dane binarne `operator^` .

## <a name="cref"></a><a name="cref"></a> cref

Konstruuje stałą `reference_wrapper` z argumentu.

```cpp
template <class Ty>
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```

### <a name="parameters"></a>Parametry

*Br*\
Typ argumentu, który ma być zawijany.

*ARG*\
Argument, który ma być zawijany.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja zwraca wartość `reference_wrapper<const Ty>(arg.get())` . Służy do zawijania odwołania const. Druga funkcja zwraca `reference_wrapper<const Ty>(arg)` . Jest on używany do przepakowania opakowanego odwołania jako odwołanie stałe.

### <a name="example"></a>Przykład

```cpp
// std__functional__cref.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    int i = 1;

    std::cout << "i = " << i << std::endl;
    std::cout << "cref(i) = " << std::cref(i) << std::endl;
    std::cout << "cref(neg)(i) = "
        << std::cref(&neg)(i) << std::endl;

    return (0);
    }
```

```Output
i = 1
cref(i) = 1
cref(neg)(i) = -1
```

## <a name="invoke"></a><a name="invoke"></a> wywołuje

Wywołuje dowolny możliwy do wykonania obiekt z podanym argumentami. Dodano w języku C++ 17.

```cpp
template <class Callable, class... Args>
invoke_result_t<Callable, Args...>
    invoke(Callable&& fn, Args&&... args) noexcept(/* specification */);
```

### <a name="parameters"></a>Parametry

*Żądanie*\
Typ obiektu do wywołania.

*Argumentów*\
Typy argumentów wywołania.

*Fn*\
Obiekt, który ma zostać wywołany.

*argumentów*\
Argumenty wywołania.

*określając*\
**`noexcept`** Specyfikacja `std::is_nothrow_invocable_v<Callable, Args>)` .

### <a name="remarks"></a>Uwagi

Wywołuje możliwy do wywołujący obiekt *Fn* przy użyciu *argumentów*parametrów. Efektywnie, `INVOKE(std::forward<Callable>(fn), std::forward<Args>(args)...)` , gdzie pseudo funkcja `INVOKE(f, t1, t2, ..., tN)` oznacza jedną z następujących czynności:

- `(t1.*f)(t2, ..., tN)` gdy `f` jest wskaźnikiem do funkcji składowej klasy `T` i `t1` jest obiektem typu `T` lub odwołaniem do obiektu typu `T` lub odwołaniem do obiektu typu pochodnego od `T` . To jest, gdy `std::is_base_of<T, std::decay_t<decltype(t1)>>::value` ma wartość true.

- `(t1.get().*f)(t2, ..., tN)` gdy `f` jest wskaźnikiem do funkcji składowej klasy `T` i `std::decay_t<decltype(t1)>` jest specjalizacją `std::reference_wrapper` .

- `((*t1).*f)(t2, ..., tN)` gdy `f` jest wskaźnikiem do funkcji składowej klasy `T` i `t1` nie jest jednym z poprzednich typów.

- `t1.*f` gdy N = = 1 i `f` jest wskaźnikiem do danych elementu członkowskiego klasy `T` i `t1` jest obiektem typu `T` lub odwołaniem do obiektu typu `T` lub odwołaniem do obiektu typu pochodnego od `T` .  To jest, gdy `std::is_base_of<T, std::decay_t<decltype(t1)>>::value` ma wartość true.

- `t1.get().*f` gdy N = = 1 i `f` jest wskaźnikiem do danych składowych klasy `T` i `std::decay_t<decltype(t1)>` jest specjalizacją `std::reference_wrapper` .

- `(*t1).*f` gdy N = = 1 i `f` jest wskaźnikiem do danych składowych klasy `T` i `t1` nie jest jednym z poprzednich typów.

- `f(t1, t2, ..., tN)` we wszystkich innych przypadkach.

Aby uzyskać informacje na temat typu wyniku wywoływanego obiektu, zobacz [invoke_result](invoke-result-class.md). W przypadku predykatów o wywoływanych typach zobacz [is_invocable, is_invocable_r, is_nothrow_invocable, is_nothrow_invocable_r klasy](is-invocable-classes.md).

### <a name="example"></a>Przykład

```cpp
// functional_invoke.cpp
// compile using: cl /EHsc /std:c++17 functional_invoke.cpp
#include <functional>
#include <iostream>

struct Demo
{
    int n_;

    Demo(int const n) : n_{n} {}

    void operator()( int const i, int const j ) const
    {
        std::cout << "Demo operator( " << i << ", "
            << j << " ) is " << i * j << "\n";
    }

    void difference( int const i ) const
    {
        std::cout << "Demo.difference( " << i << " ) is "
            << n_ - i << "\n";
    }
};

void divisible_by_3(int const i)
{
    std::cout << i << ( i % 3 == 0 ? " is" : " isn't" )
        << " divisible by 3.\n";
}

int main()
{
    Demo d{ 42 };
    Demo * pd{ &d };
    auto pmf = &Demo::difference;
    auto pmd = &Demo::n_;

    // Invoke a function object, like calling d( 3, -7 )
    std::invoke( d, 3, -7 );

    // Invoke a member function, like calling
    // d.difference( 29 ) or (d.*pmf)( 29 )
    std::invoke( &Demo::difference, d, 29 );
    std::invoke( pmf, pd, 13 );

    // Invoke a data member, like access to d.n_ or d.*pmd
    std::cout << "d.n_: " << std::invoke( &Demo::n_, d ) << "\n";
    std::cout << "pd->n_: " << std::invoke( pmd, pd ) << "\n";

    // Invoke a stand-alone (free) function
    std::invoke( divisible_by_3, 42 );

    // Invoke a lambda
    auto divisible_by_7 = []( int const i ) {
        std::cout << i << ( i % 7 == 0 ? " is" : " isn't" )
            << " divisible by 7.\n";
        };
    std::invoke( divisible_by_7, 42 );
}
```

```Output
Demo operator( 3, -7 ) is -21
Demo.difference( 29 ) is 13
Demo.difference( 13 ) is 29
d.n_: 42
pd->n_: 42
42 is divisible by 3.
42 is divisible by 7.
```

## <a name="mem_fn"></a><a name="mem_fn"></a> mem_fn

Generuje prosty otokę wywołania.

```cpp
template <class RTy, class Ty>
unspecified mem_fn(RTy Ty::*pm);
```

### <a name="parameters"></a>Parametry

*RTy*\
Zwracany typ funkcji opakowanej.

*Br*\
Typ wskaźnika funkcji składowej.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca prostą otokę wywołania `cw` z słabym typem wyniku, tak że wyrażenie jest takie `cw(t, a2, ..., aN)` samo jak `INVOKE(pm, t, a2, ..., aN)` . Nie generuje żadnych wyjątków.

Zwracana otoka wywołań pochodzi od `std::unary_function<cv Ty*, RTy>` (i definiująca zagnieżdżony typ `result_type` jako synonim dla *RTy* i zagnieżdżony typ `argument_type` jako synonim `cv Ty*` ) tylko wtedy, gdy typ *ty* jest wskaźnikiem do funkcji składowej z kwalifikatorem CV `cv` , który nie przyjmuje argumentów.

Zwracana otoka wywołania pochodzi od `std::binary_function<cv Ty*, T2, RTy>` (i definiująca zagnieżdżony typ `result_type` jako synonim dla *RTy*, Typ zagnieżdżony `first argument_type` jako synonim dla `cv Ty*` i zagnieżdżony typ `second argument_type` jako synonim `T2` ), tylko wtedy, gdy typ *ty* jest wskaźnikiem do funkcji składowej z kwalifikatorem CV, `cv` który przyjmuje jeden argument typu `T2` .

### <a name="example"></a>Przykład

```cpp
// std__functional__mem_fn.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

class Funs
    {
public:
    void square(double x)
        {
        std::cout << x << "^2 == " << x * x << std::endl;
        }

    void product(double x, double y)
        {
        std::cout << x << "*" << y << " == " << x * y << std::endl;
        }
    };

int main()
    {
    Funs funs;

    std::mem_fn(&Funs::square)(funs, 3.0);
    std::mem_fn(&Funs::product)(funs, 3.0, 2.0);

    return (0);
    }
```

```Output
3^2 == 9
3*2 == 6
```

## <a name="mem_fun"></a><a name="mem_fun"></a> mem_fun

Funkcje szablonu pomocnika służące do konstruowania adapterów obiektów funkcji dla funkcji Członkowskich po zainicjowaniu z argumentami wskaźnika. Przestarzałe w języku C++ 11 dla [mem_fn](#mem_fn) i [powiązania](#bind)i usunięte w języku c++ 17.

```cpp
template <class Result, class Type>
mem_fun_t<Result, Type> mem_fun (Result(Type::* pMem)());

template <class Result, class Type, class Arg>
mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pMem)(Arg));

template <class Result, class Type>
const_mem_fun_t<Result, Type> mem_fun(Result (Type::* pMem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pMem)(Arg) const);
```

### <a name="parameters"></a>Parametry

*pMem*\
Wskaźnik do funkcji składowej klasy `Type` , która ma zostać przekonwertowana na obiekt funkcji.

### <a name="return-value"></a>Wartość zwracana

**`const`** Lub **non_const** obiekt funkcji typu `mem_fun_t` lub `mem_fun1_t` .

### <a name="example"></a>Przykład

```cpp
// functional_mem_fun.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

class StoreVals
{
    int val;
public:
    StoreVals() { val = 0; }
    StoreVals(int j) { val = j; }

    bool display() { cout << val << " "; return true; }
    int squareval() { val *= val; return val; }
    int lessconst(int k) {val -= k; return val; }
};

int main( )
{
    vector<StoreVals *> v1;

    StoreVals sv1(5);
    v1.push_back(&sv1);
    StoreVals sv2(10);
    v1.push_back(&sv2);
    StoreVals sv3(15);
    v1.push_back(&sv3);
    StoreVals sv4(20);
    v1.push_back(&sv4);
    StoreVals sv5(25);
    v1.push_back(&sv5);

    cout << "The original values stored are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;

    // Use of mem_fun calling member function through a pointer
    // square each value in the vector using squareval ()
    for_each(v1.begin(), v1.end(), mem_fun<int, StoreVals>(&StoreVals::squareval));
    cout << "The squared values are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;

    // Use of mem_fun1 calling member function through a pointer
    // subtract 5 from each value in the vector using lessconst ()
    for_each(v1.begin(), v1.end(),
        bind2nd (mem_fun1<int, StoreVals,int>(&StoreVals::lessconst), 5));
    cout << "The squared values less 5 are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;
}
```

## <a name="mem_fun_ref"></a><a name="mem_fun_ref"></a> mem_fun_ref

Funkcje szablonu pomocnika służące do konstruowania adapterów obiektów funkcji dla funkcji Członkowskich po zainicjowaniu przy użyciu argumentów odwołania. Przestarzałe w języku C++ 11, usunięte w języku C++ 17.

```cpp
template <class Result, class Type>
mem_fun_ref_t<Result, Type> mem_fun_ref(Result (Type::* pMem)());

template <class Result, class Type, class Arg>
mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (Type::* pMem)(Arg));

template <class Result, class Type>
const_mem_fun_ref_t<Result, Type> mem_fun_ref(Result Type::* pMem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (T::* pMem)(Arg) const);
```

### <a name="parameters"></a>Parametry

*pMem*\
Wskaźnik do funkcji składowej klasy `Type` , która ma zostać przekonwertowana na obiekt funkcji.

### <a name="return-value"></a>Wartość zwracana

**`const`** `non_const` Obiekt typu lub `mem_fun_ref_t` `mem_fun1_ref_t` .

### <a name="example"></a>Przykład

```cpp
// functional_mem_fun_ref.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

class NumVals
   {
   int val;
   public:
   NumVals ( ) { val = 0; }
   NumVals ( int j ) { val = j; }

   bool display ( ) { cout << val << " "; return true; }
   bool isEven ( ) { return ( bool )  !( val %2 ); }
   bool isPrime( )
   {
      if (val < 2) { return true; }
      for (int i = 2; i <= val / i; ++i)
      {
         if (val % i == 0) { return false; }
      }
      return true;
   }
};

int main( )
{
   vector <NumVals> v1 ( 13 ), v2 ( 13 );
   vector <NumVals>::iterator v1_Iter, v2_Iter;
   int i, k;

   for ( i = 0; i < 13; i++ ) v1 [ i ] = NumVals ( i+1 );
   for ( k = 0; k < 13; k++ ) v2 [ k ] = NumVals ( k+1 );

   cout << "The original values stored in v1 are: " ;
   for_each( v1.begin( ), v1.end( ),
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   // Use of mem_fun_ref calling member function through a reference
   // remove the primes in the vector using isPrime ( )
   v1_Iter = remove_if ( v1.begin( ),  v1.end( ),
      mem_fun_ref ( &NumVals::isPrime ) );
   cout << "With the primes removed, the remaining values in v1 are: " ;
   for_each( v1.begin( ), v1_Iter,
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   cout << "The original values stored in v2 are: " ;
   for_each( v2.begin( ), v2.end( ),
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   // Use of mem_fun_ref calling member function through a reference
   // remove the even numbers in the vector v2 using isEven ( )
   v2_Iter = remove_if ( v2.begin( ),  v2.end( ),
      mem_fun_ref ( &NumVals::isEven ) );
   cout << "With the even numbers removed, the remaining values are: " ;
   for_each( v2.begin( ),  v2_Iter,
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;
}
```

```Output
The original values stored in v1 are: 1 2 3 4 5 6 7 8 9 10 11 12 13
With the primes removed, the remaining values in v1 are: 4 6 8 9 10 12
The original values stored in v2 are: 1 2 3 4 5 6 7 8 9 10 11 12 13
With the even numbers removed, the remaining values are: 1 3 5 7 9 11 13
```

## <a name="not1"></a><a name="not1"></a> not1 —

Zwraca uzupełnienie predykatu jednoargumentowego. Przestarzałe dla [not_fn](#not_fn) w języku c++ 17.

```cpp
template <class UnaryPredicate>
unary_negate<UnaryPredicate> not1(const UnaryPredicate& predicate);
```

### <a name="parameters"></a>Parametry

*predykatu*\
Predykat jednoargumentowy, który ma być negacją.

### <a name="return-value"></a>Wartość zwracana

Predykat jednoargumentowy, który jest negacją predykatu jednoargumentowego zmodyfikowanego.

### <a name="remarks"></a>Uwagi

Jeśli obiekt `unary_negate` jest zbudowany z predykatu jednoargumentowego `predicate(x)` , zwraca `!predicate(x)` .

### <a name="example"></a>Przykład

```cpp
// functional_not1.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 7; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    // Count the elements greater than 10
    result1 = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    vector<int>::iterator::difference_type result2;
    // Use the negator to count the elements less than or equal to 10
    result2 = count_if(v1.begin(), v1.end(),
        not1(bind2nd(greater<int>(), 10)));

    cout << "The number of elements in v1 not greater than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 30 35 )
The number of elements in v1 greater than 10 is: 5.
The number of elements in v1 not greater than 10 is: 3.
```

## <a name="not2"></a><a name="not2"></a> not2 —

Zwraca uzupełnienie predykatu binarnego. Przestarzałe dla [not_fn](#not_fn) w języku c++ 17.

```cpp
template <class BinaryPredicate>
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```

### <a name="parameters"></a>Parametry

*Func*\
Predykat binarny, który ma być negacją.

### <a name="return-value"></a>Wartość zwracana

Predykat binarny, który jest negacją elementu binarnego predykatu.

### <a name="remarks"></a>Uwagi

Jeśli obiekt `binary_negate` jest zbudowany z predykatu binarnego `binary_predicate(x, y)` , zwraca `!binary_predicate(x, y)` .

### <a name="example"></a>Przykład

```cpp
// functional_not2.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <cstdlib>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   v1.push_back( 6262 );
   v1.push_back( 6262 );
   for ( i = 0 ; i < 5 ; i++ )
   {
      v1.push_back( rand( ) );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // use the binary_negate helper function not2
   sort( v1.begin( ), v1.end( ), not2(less<int>( ) ) );
   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 6262 6262 41 18467 6334 26500 19169 )
Sorted vector v1 = ( 41 6262 6262 6334 18467 19169 26500 )
Resorted vector v1 = ( 26500 19169 18467 6334 6262 6262 41 )
```

## <a name="not_fn"></a><a name="not_fn"></a> not_fn

`not_fn`Szablon funkcji przyjmuje możliwy do naprawnego obiektu i zwraca możliwy do naprawnego obiektu. Gdy zwracany obiekt wywołujący jest później wywoływany z niektórymi argumentami, przekazuje je do oryginalnego możliwego do wywołania obiektu i logicznie negacj wynik. Zachowuje wartość i zachowanie kategorii const dla zapakowanego obiektu, który jest wywoływany. `not_fn` jest Nowość w języku c++ 17 i zastępuje przestarzałe `std::not1` , `std::not2` , `std::unary_negate` , i `std::binary_negate` .

```cpp
template <class Callable>
/* unspecified */ not_fn(Callable&& func);
```

### <a name="parameters"></a>Parametry

*Func*\
Obiekt możliwy do wywołania, używany do konstruowania otoki wywołań przekazywania.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca otokę wywołania, taką jak `return call_wrapper(std::forward<Callable>(func))` , na podstawie tej klasy tylko do specyfikacji:

```cpp
class call_wrapper
{
   using FD = decay_t<Callable>;
   explicit call_wrapper(Callable&& func);

public:
   call_wrapper(call_wrapper&&) = default;
   call_wrapper(call_wrapper const&) = default;

   template<class... Args>
     auto operator()(Args&&...) & -> decltype(!declval<invoke_result_t<FD&(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) const& -> decltype(!declval<invoke_result_t<FD const&(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) && -> decltype(!declval<invoke_result_t<FD(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) const&& -> decltype(!declval<invoke_result_t<FD const(Args...)>>());

private:
  FD fd;
};
```

Jawny Konstruktor dla wywoływanego obiektu *Func* wymaga typu `std::decay_t<Callable>` , aby spełnić wymagania `MoveConstructible` i `is_constructible_v<FD, Callable>` musi mieć wartość true. Inicjuje zapakowany obiekt, który jest wywoływany `fd` z `std::forward<Callable>(func)` i zgłasza każdy wyjątek zgłoszony przez konstrukcję `fd` .

Otoka ujawnia operatory wywołań, które różnią się od kategorii odwołań lvalue lub rvalue i posiadają kwalifikacje stałe, jak pokazano poniżej:

```cpp
template<class... Args> auto operator()(Args&&... args) & -> decltype(!declval<invoke_result_t<FD&(Args...)>>());
template<class... Args> auto operator()(Args&&... args) const& -> decltype(!declval<invoke_result_t<FD const&(Args...)>>());
template<class... Args> auto operator()(Args&&... args) && -> decltype(!declval<invoke_result_t<FD(Args...)>>());
template<class... Args> auto operator()(Args&&... args) const&& -> decltype(!declval<invoke_result_t<FD const(Args...)>>());
```

Pierwsze dwa są takie same, jak `return !std::invoke(fd, std::forward<Args>(args)...)` . Drugie dwa są takie same, jak `return !std::invoke(std::move(fd), std::forward<Args>(args)...)` .

### <a name="example"></a>Przykład

```cpp
// functional_not_fn_.cpp
// compile with: /EHsc /std:c++17
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()
{
    std::vector<int> v1 = { 99, 6264, 41, 18467, 6334, 26500, 19169 };
    auto divisible_by_3 = [](int i){ return i % 3 == 0; };

    std::cout << "Vector v1 = ( " ;
    for (const auto& item : v1)
    {
        std::cout << item << " ";
    }
    std::cout << ")" << std::endl;

    // Count the number of vector elements divisible by 3.
    int divisible =
        std::count_if(v1.begin(), v1.end(), divisible_by_3);
    std::cout << "Elements divisible by three: "
        << divisible << std::endl;

    // Count the number of vector elements not divisible by 3.
    int not_divisible =
        std::count_if(v1.begin(), v1.end(), std::not_fn(divisible_by_3));
    std::cout << "Elements not divisible by three: "
        << not_divisible << std::endl;
}
```

```Output
Vector v1 = ( 99 6264 41 18467 6334 26500 19169 )
Elements divisible by three: 2
Elements not divisible by three: 5
```

## <a name="ptr_fun"></a><a name="ptr_fun"></a> ptr_fun

Funkcje szablonu pomocnika służące do konwersji jednoargumentowych i binarnych wskaźników funkcji, odpowiednio, do funkcji, które można dostosowywać jednoargumentowo. Przestarzałe w języku C++ 11, usunięte w języku C++ 17.

```cpp
template <class Arg, class Result>
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```

### <a name="parameters"></a>Parametry

*pfunc*\
Wskaźnik funkcji jednoargumentowej lub binarnej, który ma zostać przekonwertowany na funkcję adaptacyjną.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja szablonu zwraca jednoargumentową funkcję [pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md)  < `Arg` , **wynik**> ( \* `pfunc` ).

Druga funkcja szablonu zwraca funkcję binarną [pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md) \<**Arg1**, **Arg2**, **Result**> ( \* `pfunc` ).

### <a name="remarks"></a>Uwagi

Wskaźnik funkcji jest obiektem funkcji. Może być przekazanie do dowolnego algorytmu, który oczekuje funkcji jako parametru, ale nie można go dostosować. Informacje o jego typach zagnieżdżonych są wymagane do używania go z adapterem, na przykład w celu powiązania z nim wartości lub Negate go. Konwersja jednoargumentowych i binarnych wskaźników funkcji `ptr_fun` pomocnika umożliwia adapterom funkcji współdziałanie ze wskaźnikami funkcji jednoargumentowych i binarnych.

### <a name="example"></a>Przykład

[!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]

## <a name="ref"></a><a name="ref"></a> umieszczone

Tworzy element a `reference_wrapper` z argumentu.

```cpp
template <class Ty>
    reference_wrapper<Ty> ref(Ty& arg);

template <class Ty>
    reference_wrapper<Ty> ref(reference_wrapper<Ty>& arg);
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do; w odniesieniu do `arg` `reference_wrapper<Ty>(arg)` .

### <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano dwie funkcje: jedną powiązaną z zmienną ciągu, drugą powiązaną z odwołaniem zmiennej String obliczanej przez wywołanie `ref` . Po zmianie wartości zmiennej Pierwsza funkcja nadal używa starej wartości, a druga funkcja używa nowej wartości.

```cpp
#include <algorithm>
#include <functional>
#include <iostream>
#include <iterator>
#include <ostream>
#include <string>
#include <vector>
using namespace std;
using namespace std;
using namespace std::placeholders;

bool shorter_than(const string& l, const string& r) {
    return l.size() < r.size();
}

int main() {
    vector<string> v_original;
    v_original.push_back("tiger");
    v_original.push_back("cat");
    v_original.push_back("lion");
    v_original.push_back("cougar");

    copy(v_original.begin(), v_original.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    string s("meow");

    function<bool (const string&)> f = bind(shorter_than, _1, s);
    function<bool (const string&)> f_ref = bind(shorter_than, _1, ref(s));

    vector<string> v;

    // Remove elements that are shorter than s ("meow")

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    // Now change the value of s.
    // f_ref, which is bound to ref(s), will use the
    // new value, while f is still bound to the old value.

    s = "kitty";

    // Remove elements that are shorter than "meow" (f is bound to old value of s)

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    // Remove elements that are shorter than "kitty" (f_ref is bound to ref(s))

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f_ref), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;
}
```

```Output
tiger cat lion cougar
tiger lion cougar
tiger lion cougar
tiger cougar
```

## <a name="swap"></a><a name="swap"></a> wymiany

Zamienia dwa `function` obiekty.

```cpp
template <class FT>
    void swap(function<FT>& f1, function<FT>& f2);
```

### <a name="parameters"></a>Parametry

*STÓP*\
Typ kontrolowany przez obiekty funkcji.

*nacionięcie*\
Pierwszy obiekt funkcji.

*F2*\
Drugi obiekt funkcji.

### <a name="remarks"></a>Uwagi

Funkcja zwraca wartość `f1.swap(f2)` .

### <a name="example"></a>Przykład

```cpp
// std__functional__swap.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "val == " << fn0(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << std::endl;

    swap(fn0, fn1);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
empty == true

empty == true
empty == false
val == -3
```
