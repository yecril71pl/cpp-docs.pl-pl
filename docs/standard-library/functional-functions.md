---
title: '&lt;funkcjonalności&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- functional/std::bind
- xfunctional/std::bind1st
- xfunctional/std::bind2nd
- xfunctional/std::bit_and
- xfunctional/std::bit_not
- xfunctional/std::bit_or
- xfunctional/std::bit_xor
- functional/std::cref
- type_traits/std::cref
- xfunctional/std::mem_fn
- xfunctional/std::mem_fun_ref
- xfunctional/std::not1
- xfunctional/std::not2
- xfunctional/std::ptr_fun
- functional/std::ref
- functional/std::swap
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b14e656d77247984ba3306d6efff78e6cca713cb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ltfunctionalgt-functions"></a>&lt;funkcjonalności&gt; funkcji

||||
|-|-|-|
|[BIND](#bind)|[bind1st](#bind1st)|[bind2nd](#bind2nd)|
|[bit_and](#bit_and)|[bit_not](#bit_not)|[bit_or](#bit_or)|
|[bit_xor](#bit_xor)|[cref](#cref)|[mem_fn](#mem_fn)|
|[mem_fun](#mem_fun)|[mem_fun_ref](#mem_fun_ref)|[not1](#not1)|
|[not2](#not2)|[ptr_fun](#ptr_fun)|[ref](#ref)|
|[swap](#swap)|

## <a name="bind"></a>  BIND

Wiąże argumentów można wywołać obiektu.

```cpp
template <class Fty, class T1, class T2, ..., class TN>
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);

template <class Ret, class Fty, class T1, class T2, ..., class TN>
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);
```

### <a name="parameters"></a>Parametry

`Fty` Typ obiektu do wywołania.

`TN` Typ określona liczba wywołań argumentu.

`fn` Obiekt do wywołania.

`tN` Argument n-tego wywołania.

### <a name="remarks"></a>Uwagi

Typy `Fty, T1, T2, ..., TN` musi być umożliwia konstrukcji, kopiowania i `INVOKE(fn, t1, ..., tN)` musi być prawidłowym wyrażeniem dla niektórych wartości `w1, w2, ..., wN`.

Pierwszy funkcji szablonu zwraca wywołanie przekazywania otoki `g` z typem wyniku słabe. Efekt `g(u1, u2, ..., uM)` jest `INVOKE(f, v1, v2, ..., vN, ` [result_of —](../standard-library/result-of-class.md)`<Fty cv (V1, V2, ..., VN)>::type)`, gdzie `cv` jest kwalifikatorów cv z `g` oraz wartości i typy argumentów powiązania `v1, v2, ..., vN` są określane jako wymienionymi poniżej. Umożliwia ona powiązać obiektu można wywołać, aby obiekt można wywołać z listą argumentów dopasowane argumentów.

Drugi funkcji szablonu zwraca wywołanie przekazywania otoki `g` z typem zagnieżdżonym `result_type` czyli synonimem `Ret`. Efekt `g(u1, u2, ..., uM)` jest `INVOKE(f, v1, v2, ..., vN, Ret)`, gdzie `cv` jest kwalifikatorów cv z `g` oraz wartości i typy argumentów powiązania `v1, v2, ..., vN` są wymienione poniżej. Umożliwia ona powiązanie argumentów do obiektu można wywołać, aby obiekt można wywołać z listą argumentów dopasowane i z określonym typem zwracanym.

Wartości argumentów powiązania `v1, v2, ..., vN` i jako odpowiednie typy `V1, V2, ..., VN` zależą od typu odpowiadającego mu argumentu `ti` typu `Ti` w wywołaniu `bind` i kwalifikatorów cv `cv` z Wywołanie otoką `g` w następujący sposób:

Jeśli `ti` jest typu `reference_wrapper<T>` argument `vi` jest `ti.get()` i jej typie `Vi` jest `T&`;

Jeśli wartość `std::is_bind_expression<Ti>::value` jest `true` argument `vi` jest `ti(u1, u2, ..., uM)` i jej typie `Vi` jest `result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type`;

Jeśli wartość `j` z `std::is_placeholder<Ti>::value` wynosi zero nie argument `vi` jest `uj` i jej typie `Vi` jest `Uj&`;

w przeciwnym razie argument `vi` jest `ti` i jej typie `Vi` jest `Ti` `cv` `&`.

Przykładowo, podana funkcji `f(int, int)` wyrażenie `bind(f, _1, 0)` zwraca przekazywania wywołań otok `cw` tak, aby `cw(x)` wywołania `f(x, 0)`. Wyrażenie `bind(f, 0, _1)` zwraca przekazywania wywołań otok `cw` tak, aby `cw(x)` wywołania `f(0, x)`.

Liczba argumentów w wywołaniu `bind` oprócz argument `fn` musi być równa liczbie argumentów, które mogą zostać przekazane do można wywołać obiektu `fn`. W związku z tym `bind(cos, 1.0)` jest poprawna, a oba `bind(cos)` i `bind(cos, _1, 0.0)` są nieprawidłowe.

Liczba argumentów w funkcji wywołanie otoką wywołania zwrócony przez `bind` musi być przynajmniej tak duże jak najwyższą wartość numeru `is_placeholder<PH>::value` dla wszystkich argumentów symbol zastępczy w wywołaniu `bind`. W związku z tym `bind(cos, _2)(0.0, 1.0)` jest prawidłowa (i zwraca `cos(1.0)`), a `bind(cos, _2)(0.0)` jest niepoprawny.

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

## <a name="bind1st"></a>  bind1st —

Funkcja szablonu pomocnika, która tworzy adaptera, aby przekonwertować obiektu binarnego funkcja obiektem funkcji jednoargumentowy przez powiązanie pierwszy argument funkcji binarnego do określonej wartości.

```cpp
template <class Operation, class Type>
binder1st <Operation> bind1st (const Operation& func, const Type& left);
```

### <a name="parameters"></a>Parametry

`func` Obiekt binarny funkcji do przekonwertowania na obiekt funkcja jednoargumentowy.

`left` Wartość, do której ma zostać powiązany pierwszy argument obiektu binarnego funkcji.

### <a name="return-value"></a>Wartość zwracana

Obiekt funkcji jednoargumentowy będącą wynikiem powiązanie pierwszy argument obiektu, funkcja binarnej na wartość `left`.

### <a name="remarks"></a>Uwagi

Funkcja integratorów są pewnego rodzaju karty funkcji i zwracają obiekty funkcji można jej używać w niektórych typów kompozycja funkcji do utworzenia bardziej złożone i zaawansowane wyrażenia.

Jeśli `func` jest obiektem typu `Operation` i `c` jest stałą, następnie `bind1st` ( `func`, `c`) jest odpowiednikiem [binder1st —](../standard-library/binder1st-class.md) konstruktora klasy `binder1st` <  `Operation`> ( `func`, `c`) i jest wygodniejsze.

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

## <a name="bind2nd"></a>  bind2nd —

Funkcja szablonu pomocnika, która tworzy adaptera, aby przekonwertować obiektu binarnego funkcja obiektem funkcji jednoargumentowy przez powiązanie drugi argument funkcji binarnego do określonej wartości.

```cpp
template <class Operation, class Type>
binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```

### <a name="parameters"></a>Parametry

`func` Obiekt binarny funkcji do przekonwertowania na obiekt funkcja jednoargumentowy.

`right` Wartość, do której ma zostać powiązany drugi argument obiektu binarnego funkcji.

### <a name="return-value"></a>Wartość zwracana

Obiekt funkcji jednoargumentowy będącą wynikiem powiązanie drugi argument obiektu, funkcja binarnej na wartość `right`.

### <a name="remarks"></a>Uwagi

Funkcja integratorów są pewnego rodzaju karty funkcji i zwracają obiekty funkcji można jej używać w niektórych typów kompozycja funkcji do utworzenia bardziej złożone i zaawansowane wyrażenia.

Jeśli `func` jest obiektem typu **operacji** i `c` jest stałą, następnie `bind2nd` ( `func`, `c` ) jest odpowiednikiem [binder2nd —](../standard-library/binder2nd-class.md) — klasa Konstruktor **binder2nd —\<operacji >** ( `func`, `c` ) i wygodniejsze.

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

## <a name="bit_and"></a>  bit_and —

Obiekt wstępnie zdefiniowanych funkcji, który wykonuje operacji i (binarne `operator&`) na jego argumenty.

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

`Type`, `T`, `U` Dowolnego typu, który obsługuje `operator&` pobierającej argumentów operacji typu określonego lub wywnioskowany.

`Left` Lewy argument operacji i. Szablon klasy niespecjalizowanej przyjmuje argument odwołania l-wartością typu `Type`. Specjalne szablonu doskonała przekazującej lewostronnie i argumenty odwołanie do r-wartości wywnioskować typu `T`.

`Right` Prawy argument operacji i. Szablon klasy niespecjalizowanej przyjmuje argument odwołania l-wartością typu `Type`. Specjalne szablonu doskonała przekazującej lewostronnie i argumenty odwołanie do r-wartości wywnioskować typu `U`.

### <a name="return-value"></a>Wartość zwracana

Wynik `Left & Right`. Specjalne szablonu doskonała przekazywanie wynik, który ma typ zwracany przez `operator&`.

### <a name="remarks"></a>Uwagi

`bit_and` Obiekt jest ograniczony do typów całkowitych dla danych podstawowych lub do zdefiniowanych przez użytkownika typów danych binarnych tej implementacji `operator&`.

## <a name="bit_not"></a>  bit_not

Obiekt wstępnie zdefiniowanych funkcji, który wykonuje dopełnienia bitowego (nie) operacji (jednoargumentowy `operator~`) na jej argument.

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
    auto operator()(Type&& Right) const  ->  decltype(~std::forward<Type>(Right));
 };
```

### <a name="parameters"></a>Parametry

`Type` Typ, który obsługuje jednoargumentowe `operator~`.

`Right` Argument operacji dopełnienia bitowego. Szablon klasy niespecjalizowanej przyjmuje argument odwołania l-wartością typu `Type`. Specjalne szablonu doskonała przekazywanie l-wartością lub r-wartości argumentu odwołania typu wywnioskowane `Type`.

### <a name="return-value"></a>Wartość zwracana

Wynik `~ Right`. Specjalne szablonu doskonała przekazywanie wynik, który ma typ zwracany przez `operator~`.

### <a name="remarks"></a>Uwagi

`bit_not` Obiekt jest ograniczony do typów całkowitych dla danych podstawowych lub do zdefiniowanych przez użytkownika typów danych binarnych tej implementacji `operator~`.

## <a name="bit_or"></a>  bit_or —

Obiekt wstępnie zdefiniowanych funkcji, który wykonuje operację lub bitowe ( `operator|`) na jego argumenty.

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
        ->  decltype(std::forward<T>(Left) | std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parametry

`Type`, `T`, `U` Dowolnego typu, który obsługuje `operator|` pobierającej argumentów operacji typu określonego lub wywnioskowany.

`Left` Lewy argument operacji lub operacji. Szablon klasy niespecjalizowanej przyjmuje argument odwołania l-wartością typu `Type`. Specjalne szablonu doskonała przekazującej lewostronnie i argumenty odwołanie do r-wartości wywnioskować typu `T`.

`Right` Prawy argument operacji lub operacji. Szablon klasy niespecjalizowanej przyjmuje argument odwołania l-wartością typu `Type`. Specjalne szablonu doskonała przekazującej lewostronnie i argumenty odwołanie do r-wartości wywnioskować typu `U`.

### <a name="return-value"></a>Wartość zwracana

Wynik `Left | Right`. Specjalne szablonu doskonała przekazywanie wynik, który ma typ zwracany przez `operator|`.

### <a name="remarks"></a>Uwagi

`bit_or` Obiekt jest ograniczony do typów całkowitych dla danych podstawowych lub do zdefiniowanych przez użytkownika typów, które implementują `operator|`.

## <a name="bit_xor"></a>  bit_xor —

Obiekt wstępnie zdefiniowanych funkcji, który wykonuje operację bitowego XOR (binarne `operator^`) na jego argumenty.

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

`Type`, `T`, `U` Dowolnego typu, który obsługuje `operator^` pobierającej argumentów operacji typu określonego lub wywnioskowany.

`Left` Lewy operand operacji XOR. Szablon klasy niespecjalizowanej przyjmuje argument odwołania l-wartością typu `Type`. Specjalne szablonu doskonała przekazującej lewostronnie i argumenty odwołanie do r-wartości wywnioskować typu `T`.

`Right` Prawy argument operacji XOR. Szablon klasy niespecjalizowanej przyjmuje argument odwołania l-wartością typu `Type`. Specjalne szablonu doskonała przekazującej lewostronnie i argumenty odwołanie do r-wartości wywnioskować typu `U`.

### <a name="return-value"></a>Wartość zwracana

Wynik `Left ^ Right`. Specjalne szablonu doskonała przekazywanie wynik, który ma typ zwracany przez `operator^`.

### <a name="remarks"></a>Uwagi

`bit_xor` Obiekt jest ograniczony do typów całkowitych dla danych podstawowych lub do zdefiniowanych przez użytkownika typów danych binarnych tej implementacji `operator^`.

## <a name="cref"></a>  cref

Konstrukcje typu const `reference_wrapper` z argumentem.

```cpp
template <class Ty>
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```

### <a name="parameters"></a>Parametry

`Ty` Typ argumentu do zakodowania.

`arg` Argument do zakodowania.

### <a name="remarks"></a>Uwagi

Zwraca pierwszą funkcję `reference_wrapper<const Ty>(arg.get())`. Umożliwia ona zawijać const odwołania. Zwraca funkcję drugi `reference_wrapper<const Ty>(arg)`. Umożliwia ona zawinąć opakowana odwołanie jako const odwołanie.

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

## <a name="mem_fn"></a>  mem_fn —

Generuje otoki proste wywołania.

```cpp
template <class Ret, class Ty>
unspecified mem_fn(Ret Ty::*pm);
```

### <a name="parameters"></a>Parametry

`Ret` Opakowana funkcja typ zwracany.

`Ty` Typ wskaźnika funkcji Członkowskich.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca otoki proste wywołania `cw`, z typem wyniku słabe tak, aby wyrażenie `cw(t, a2, ..., aN)` jest odpowiednikiem `INVOKE(pm, t, a2, ..., aN)`. Generują żadnych wyjątków.

Otoki wywołania zwracane jest pochodną `std::unary_function<cv Ty*, Ret>` (stąd Definiowanie typu zagnieżdżonego `result_type` jako synonimem `Ret` i typu zagnieżdżonego `argument_type` jako synonimem `cv Ty*`) tylko wtedy, gdy typ `Ty` jest wskaźnik do elementu członkowskiego Funkcja z kwalifikatorem cv `cv` który nie przyjmuje żadnych argumentów.

Otoki wywołania zwracane jest pochodną `std::binary_function<cv Ty*, T2, Ret>` (stąd Definiowanie typu zagnieżdżonego `result_type` jako synonimem `Ret`, typu zagnieżdżonego `first argument_type` jako synonimem `cv Ty*`i typu zagnieżdżonego `second argument_type` jako synonimem `T2`) tylko wtedy, gdy typ `Ty` wskaźnika do funkcji członkowskiej z kwalifikatorem cv `cv` pobierającej jeden argument typu `T2`.

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

## <a name="mem_fun"></a>  mem_fun —

Funkcje pomocy szablonu, użyty do utworzenia karty obiektu funkcji dla funkcji Członkowskich po zainicjowaniu z argumentami wskaźnika.

```cpp
template <class Result, class Type>
mem_fun_t<Result, Type> mem_fun (Result(Type::* pmem)());

template <class Result, class Type, class Arg>
mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pmem)(Arg));

template <class Result, class Type>
const_mem_fun_t<Result, Type> mem_fun(Result (Type::* pmem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pmem)(Arg) const);
```

### <a name="parameters"></a>Parametry

`pmem` Wskaźnik do funkcji członkowskiej klasy **typu** do przekonwertowania na obiekt funkcji.

### <a name="return-value"></a>Wartość zwracana

A **const** lub **non_const** typu obiektu funkcja `mem_fun_t` lub `mem_fun1_t`.

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

## <a name="mem_fun_ref"></a>  mem_fun_ref —

Funkcje pomocy szablonu, użyty do utworzenia karty obiektu funkcji dla funkcji Członkowskich podczas inicjowania przy użyciu argumenty odwołania.

```cpp
template <class Result, class Type>
mem_fun_ref_t<Result, Type> mem_fun_ref(Result (Type::* pmem)());

template <class Result, class Type, class Arg>
mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (Type::* pmem)(Arg));

template <class Result, class Type>
const_mem_fun_ref_t<Result, Type> mem_fun_ref(Result Type::* pmem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (T::* pmem)(Arg) const);
```

### <a name="parameters"></a>Parametry

`pmem` Wskaźnik do funkcji członkowskiej klasy `Type` do przekonwertowania na obiekt funkcji.

### <a name="return-value"></a>Wartość zwracana

A `const` lub `non_const` typu obiektu funkcja `mem_fun_ref_t` lub `mem_fun1_ref_t`.

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

## <a name="not1"></a>  not1 —

Zwraca dopełnienia predykatu jednoargumentowy.

```cpp
template <class UnaryPredicate>
unary_negate<UnaryPredicate> not1(const UnaryPredicate& pred);
```

### <a name="parameters"></a>Parametry

`pred` Predykat jednoargumentowy do można zanegowane.

### <a name="return-value"></a>Wartość zwracana

Predykat jednoargumentowy jest negacji predykatu jednoargumentowy zmodyfikowane.

### <a name="remarks"></a>Uwagi

Jeśli `unary_negate` jest tworzony z predykatem jednoargumentowy **p.**( *x*), a następnie zwraca **! P.**( *x*).

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

## <a name="not2"></a>  not2 —

Zwraca dopełnienia predykatu binarnego.

```cpp
template <class BinaryPredicate>
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```

### <a name="parameters"></a>Parametry

`func` Predykat binarnego do można zanegowane.

### <a name="return-value"></a>Wartość zwracana

Predykat binarnego, będący negacji predykatu binarne zmodyfikowane.

### <a name="remarks"></a>Uwagi

Jeśli `binary_negate` jest tworzony z predykatem binarne **BinPred**( *x*, *y*), a następnie zwraca! **BinPred**( *x*, *y*).

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

## <a name="ptr_fun"></a>  ptr_fun —

Funkcje szablonów pomocnika służący do konwertowania jednoargumentowy i wskaźniki funkcji binarnego, odpowiednio na funkcje dostosowywalne jednoargumentowy i danych binarnych.

```cpp
template <class Arg, class Result>
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```

### <a name="parameters"></a>Parametry

`pfunc` Jednoargumentowy lub binarne wskaźnik funkcji do skonwertowania dostosowywalne funkcji.

### <a name="return-value"></a>Wartość zwracana

Funkcja jednoargumentowy zwraca pierwszej funkcji szablonu [pointer_to_unary_function —](../standard-library/pointer-to-unary-function-class.md) < `Arg`, **wynik**> (* `pfunc`).

Drugi funkcji szablonu zwraca funkcja binarnej [pointer_to_binary_function —](../standard-library/pointer-to-binary-function-class.md) \< **Arg1**, **Arg2**, **wynik**> (* `pfunc`).

### <a name="remarks"></a>Uwagi

Wskaźnik funkcji jest obiektem funkcji i mogą być przekazywane do dowolnego algorytmu standardowa biblioteka C++, która oczekuje jako parametru funkcji, ale nie jest to dostosowywalne. Aby używać go z karty, takie jak powiązania wartości do niego lub użyciu negator, musi zostać dostarczony zagnieżdżonych typów, które umożliwiają takie dostosowanie. Konwersja typu binarnego i jednoargumentowy wskaźników funkcji za `ptr_fun` dzięki funkcji pomocnika adapterów funkcji do pracy z binarnego i jednoargumentowy wskaźników funkcji.

### <a name="example"></a>Przykład

[!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]

## <a name="ref"></a>  REF

Tworzy `reference_wrapper` z argumentem.

```cpp
template <class Ty>
reference_wrapper<Ty> ref(Ty& arg);

template <class Ty>
reference_wrapper<Ty> ref(reference_wrapper<Ty>& arg);
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `arg`; w szczególności `reference_wrapper<Ty>(arg)`.

### <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano dwie funkcje: jeden powiązany ze zmienną ciągu powiązane z odwołaniem zmiennej ciągu, która jest obliczana przez wywołanie do `ref`. Po zmianie wartości zmiennej, pierwszej funkcji w dalszym ciągu używa stara wartość i funkcji second używa nowej wartości.

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

## <a name="swap"></a>  Swap

Zamienia dwa `function` obiektów.

```cpp
template <class Fty>
void swap(function<Fty>& f1, function<Fty>& f2);
```

### <a name="parameters"></a>Parametry

`Fty` Typ kontrolowane przez obiekty funkcji.

`f1` Pierwszy obiekt funkcji.

`f2` Drugi obiekt funkcji.

### <a name="remarks"></a>Uwagi

Funkcja zwraca `f1.swap(f2)`.

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

## <a name="see-also"></a>Zobacz także

[\<functional>](../standard-library/functional.md)<br/>
