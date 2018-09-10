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
ms.openlocfilehash: 5c93f32a7684d32cba0d2822571bd138f9206f46
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107416"
---
# <a name="ltfunctionalgt-functions"></a>&lt;funkcjonalności&gt; funkcji

||||
|-|-|-|
|[powiązania](#bind)|[bind1st](#bind1st)|[bind2nd](#bind2nd)|
|[bit_and](#bit_and)|[bit_not](#bit_not)|[bit_or](#bit_or)|
|[bit_xor](#bit_xor)|[cref](#cref)|[mem_fn](#mem_fn)|
|[mem_fun](#mem_fun)|[mem_fun_ref](#mem_fun_ref)|[not1](#not1)|
|[not2](#not2)|[ptr_fun](#ptr_fun)|[ref](#ref)|
|[swap](#swap)|

## <a name="bind"></a>  powiązania

Wiąże argumenty wywoływanego obiektu.

```cpp
template <class Fty, class T1, class T2, ..., class TN>
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);

template <class Ret, class Fty, class T1, class T2, ..., class TN>
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);
```

### <a name="parameters"></a>Parametry

*Fty*<br/>
Typ obiektu do wywołania.

*TN*<br/>
Typ n-tej wywołać argument.

*FN*<br/>
Obiekt do wywołania.

*TN*<br/>
Wywołanie n-ty argument.

### <a name="remarks"></a>Uwagi

Typy `Fty, T1, T2, ..., TN` musi być kopią konstrukcyjną, a `INVOKE(fn, t1, ..., tN)` musi być prawidłowym wyrażeniem dla niektórych wartości `w1, w2, ..., wN`.

Pierwsza funkcja szablonu zwraca wywołanie przekazywania otoki `g` typu wyniku słabe. Efekt `g(u1, u2, ..., uM)` jest `INVOKE(f, v1, v2, ..., vN, ` [result_of —](../standard-library/result-of-class.md)`<Fty cv (V1, V2, ..., VN)>::type)`, gdzie `cv` jest kwalifikatory cv `g` i wartości, jak i typy argumentów powiązanej `v1, v2, ..., vN` są określane jako wymienionymi poniżej. Umożliwia ona powiązanie argumenty do wywoływanego obiektu, aby wywoływanego obiektu z listą argumentów dostosowanych do potrzeb.

Druga funkcja szablonu zwraca wywołanie przekazywania otoki `g` z typem zagnieżdżonym `result_type` oznacza to synonim dla `Ret`. Efekt `g(u1, u2, ..., uM)` jest `INVOKE(f, v1, v2, ..., vN, Ret)`, gdzie `cv` jest kwalifikatory cv `g` i wartości, jak i typy argumentów powiązanej `v1, v2, ..., vN` ustala, jak określono poniżej. Umożliwia ona powiązanie argumenty do wywoływanego obiektu, aby wywoływanego obiektu, z listą argumentów dostosowanych do potrzeb i z określonym typem zwracanym.

Wartości argumentów powiązanej `v1, v2, ..., vN` oraz odpowiadające typy `V1, V2, ..., VN` zależą od typu odnośnego argumentu `ti` typu `Ti` w wywołaniu `bind` i kwalifikatory cv `cv` programu Wywołanie otoką `g` w następujący sposób:

Jeśli `ti` typu `reference_wrapper<T>` argument `vi` jest `ti.get()` i jego typ `Vi` jest `T&`;

Jeśli wartość `std::is_bind_expression<Ti>::value` jest **true** argument `vi` jest `ti(u1, u2, ..., uM)` i jego typ `Vi` jest `result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type`;

Jeśli wartość `j` z `std::is_placeholder<Ti>::value` wynosi zero nie argument `vi` jest `uj` i jego typ `Vi` jest `Uj&`;

w przeciwnym razie argument `vi` jest `ti` i jego typ `Vi` jest `Ti` `cv` `&`.

Na przykład, biorąc pod uwagę funkcji `f(int, int)` wyrażenie `bind(f, _1, 0)` zwraca przekazywania wywołania otoki `cw` tak, aby `cw(x)` wywołania `f(x, 0)`. Wyrażenie `bind(f, 0, _1)` zwraca przekazywania wywołania otoki `cw` tak, aby `cw(x)` wywołania `f(0, x)`.

Liczba argumentów w wywołaniu `bind` oprócz argument `fn` musi być równa liczbie argumentów, które mogą być przekazywane do wywoływanego obiektu `fn`. W związku z tym `bind(cos, 1.0)` jest poprawny, a oba `bind(cos)` i `bind(cos, _1, 0.0)` są nieprawidłowe.

Liczba argumentów funkcji wywołanie otoką wywołań zwracany przez `bind` musi być przynajmniej tak duże jak najwyższą wartość numerowanego `is_placeholder<PH>::value` dla wszystkich argumentów symbol zastępczy w wywołaniu `bind`. W efekcie `bind(cos, _2)(0.0, 1.0)` jest poprawny (i zwraca `cos(1.0)`), i `bind(cos, _2)(0.0)` jest niepoprawny.

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

Funkcja szablonu pomocnika, która tworzy adapter do skonwertowania obiektu binarnego funkcja do obiektu funkcyjnego jednoargumentowe przez powiązanie pierwszy argument funkcji binarnego na określoną wartość.

```cpp
template <class Operation, class Type>
binder1st <Operation> bind1st (const Operation& func, const Type& left);
```

### <a name="parameters"></a>Parametry

*FUNC*<br/>
Obiekt binarny funkcji do konwersji na obiekt funkcyjny jednoargumentowy.

*left*<br/>
Wartość, do którego ma zostać powiązany pierwszy argument obiektu binarnego funkcji.

### <a name="return-value"></a>Wartość zwracana

Obiekt funkcji Jednoelementowy, będącą wynikiem powiązanie pierwszy argument obiektu binarnego funkcji z wartością *po lewej stronie*.

### <a name="remarks"></a>Uwagi

Funkcja integratorów są pewnego rodzaju adaptera funkcji i ponieważ zwracają obiekty funkcyjne, może służyć w niektórych typach kompozycja funkcji do konstruowania bardziej skomplikowane i zaawansowanych wyrażeń.

Jeśli *func* jest obiektem typu `Operation` i `c` jest stałą, następnie `bind1st` ( `func`, `c`) jest odpowiednikiem [binder1st —](../standard-library/binder1st-class.md) konstruktora klasy `binder1st` <  `Operation`> ( `func`, `c`) i jest bardziej wygodne.

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

Funkcja szablonu pomocnika, która tworzy adapter do skonwertowania obiektu binarnego funkcja do obiektu funkcyjnego jednoargumentowe przez powiązanie drugi argument funkcji binarnego na określoną wartość.

```cpp
template <class Operation, class Type>
binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```

### <a name="parameters"></a>Parametry

*FUNC*<br/>
Obiekt binarny funkcji do konwersji na obiekt funkcyjny jednoargumentowy.

*right*<br/>
Wartość, do którego ma zostać powiązany drugi argument obiektu binarnego funkcji.

### <a name="return-value"></a>Wartość zwracana

Obiekt funkcji Jednoelementowy, będącą wynikiem powiązanie drugi argument obiektu binarnego funkcji z wartością *prawo*.

### <a name="remarks"></a>Uwagi

Funkcja integratorów są pewnego rodzaju adaptera funkcji i ponieważ zwracają obiekty funkcyjne, może służyć w niektórych typach kompozycja funkcji do konstruowania bardziej skomplikowane i zaawansowanych wyrażeń.

Jeśli *func* jest obiektem typu `Operation` i `c` jest stałą, następnie `bind2nd` ( `func`, `c` ) jest odpowiednikiem [binder2nd —](../standard-library/binder2nd-class.md) konstruktora klasy **binder2nd —\<operacji >** ( `func`, `c` ) i wygodniejsze.

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

Obiekt wstępnie zdefiniowana funkcja, która wykonuje bitową operację i (binarne `operator&`) na jego argumenty.

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

*Typ*, *T*, *U* dowolnego typu, który obsługuje `operator&` przyjmującej argumentów operacji typu określonego lub wywnioskowane uprawnienie.

*po lewej stronie*<br/>
Lewy operand operacja bitowa AND. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Wyspecjalizowane szablonu doskonała przekazywania l-wartością i argumenty odwołania rvalue wywnioskować typu *T*.

*po prawej stronie*<br/>
Prawy operand operacja bitowa AND. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Wyspecjalizowane szablonu doskonała przekazywania l-wartością i argumenty odwołania rvalue wywnioskować typu *U*.

### <a name="return-value"></a>Wartość zwracana

Wynik `Left & Right`. Szablon wyspecjalizowane doskonała przekazywania wyniku, który ma typ, który jest zwracany przez `operator&`.

### <a name="remarks"></a>Uwagi

`bit_and` Teoria jest ograniczony do typów całkowitych dla podstawowych typów danych lub do typy zdefiniowane przez użytkownika tego pliku binarnego Implementowanie `operator&`.

## <a name="bit_not"></a>  bit_not

Obiekt wstępnie zdefiniowana funkcja, który wykonuje bitowe uzupełnienie (nie) operacja (jednoargumentowy `operator~`) na jej argument.

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

*Typ*<br/>
Typ, który obsługuje jednoargumentowy `operator~`.

*po prawej stronie*<br/>
Argument operacji dopełnienia bitowego. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Szablon wyspecjalizowane doskonała przekazywania argumentu odwołanie lvalue lub rvalue typu wywnioskowanego *typu*.

### <a name="return-value"></a>Wartość zwracana

Wynik `~ Right`. Szablon wyspecjalizowane doskonała przekazywania wyniku, który ma typ, który jest zwracany przez `operator~`.

### <a name="remarks"></a>Uwagi

`bit_not` Teoria jest ograniczony do typów całkowitych dla podstawowych typów danych lub do typy zdefiniowane przez użytkownika tego pliku binarnego Implementowanie `operator~`.

## <a name="bit_or"></a>  bit_or —

Obiekt wstępnie zdefiniowana funkcja, która wykonuje bitową operację lub (`operator|`) na jego argumenty.

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

*Typ*, *T*, *U* dowolnego typu, który obsługuje `operator|` przyjmującej argumentów operacji typu określonego lub wywnioskowane uprawnienie.

*po lewej stronie*<br/>
Lewy operand operacji bitowej OR. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Wyspecjalizowane szablonu doskonała przekazywania l-wartością i argumenty odwołania rvalue wywnioskować typu *T*.

*po prawej stronie*<br/>
Prawy operand operacji bitowej OR. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Wyspecjalizowane szablonu doskonała przekazywania l-wartością i argumenty odwołania rvalue wywnioskować typu *U*.

### <a name="return-value"></a>Wartość zwracana

Wynik `Left | Right`. Szablon wyspecjalizowane doskonała przekazywania wyniku, który ma typ, który jest zwracany przez `operator|`.

### <a name="remarks"></a>Uwagi

`bit_or` Teoria jest ograniczony do typów całkowitych dla podstawowych typów danych lub do zdefiniowanych przez użytkownika typami, które implementują `operator|`.

## <a name="bit_xor"></a>  bit_xor —

Obiekt wstępnie zdefiniowana funkcja, który wykonuje bitową operację XOR (binarne `operator^`) na jego argumenty.

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

*Typ*, *T*, *U* dowolnego typu, który obsługuje `operator^` przyjmującej argumentów operacji typu określonego lub wywnioskowane uprawnienie.

*po lewej stronie*<br/>
Lewy operand operacja bitowa XOR. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Wyspecjalizowane szablonu doskonała przekazywania l-wartością i argumenty odwołania rvalue wywnioskować typu *T*.

*po prawej stronie*<br/>
Prawy operand operacja bitowa XOR. Szablon Niewyspecjalizowana przyjmuje argument odwołania l-wartości typu *typu*. Wyspecjalizowane szablonu doskonała przekazywania l-wartością i argumenty odwołania rvalue wywnioskować typu *U*.

### <a name="return-value"></a>Wartość zwracana

Wynik `Left ^ Right`. Szablon wyspecjalizowane doskonała przekazywania wyniku, który ma typ, który jest zwracany przez `operator^`.

### <a name="remarks"></a>Uwagi

`bit_xor` Teoria jest ograniczony do typów całkowitych dla podstawowych typów danych lub do typy zdefiniowane przez użytkownika tego pliku binarnego Implementowanie `operator^`.

## <a name="cref"></a>  cref

Konstruuje stałą `reference_wrapper` z argumentem.

```cpp
template <class Ty>
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ argumentu do opakowania.

*ARG*<br/>
Argument do opakowania.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja zwraca `reference_wrapper<const Ty>(arg.get())`. Umożliwia ona opakować odniesienie const. Druga funkcja zwraca `reference_wrapper<const Ty>(arg)`. Umożliwia ona zawinąć opakowana odwołanie jako odniesienie const.

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

Generuje otoki prostemu wywołaniu.

```cpp
template <class Ret, class Ty>
unspecified mem_fn(Ret Ty::*pm);
```

### <a name="parameters"></a>Parametry

*instrukcji*<br/>
Opakowana funkcja typ zwrotny.

*Ty*<br/>
Typ wskaźnika funkcji elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca otoki prostemu wywołaniu `cw`, z typem słabe wynik, taki sposób, że wyrażenie `cw(t, a2, ..., aN)` jest odpowiednikiem `INVOKE(pm, t, a2, ..., aN)`. Go nie generuje żadnych wyjątków.

Otoka wywołań zwracany jest tworzony na podstawie `std::unary_function<cv Ty*, Ret>` (dlatego Definiowanie typu zagnieżdżonego `result_type` jako synonim dla *Ret* i typu zagnieżdżonego `argument_type` jako synonim dla `cv Ty*`) tylko wtedy, gdy typ  *Ty* jest wskaźnikiem do funkcji składowej z kwalifikatorem cv `cv` która nie przyjmuje żadnych argumentów.

Otoka wywołań zwracany jest tworzony na podstawie `std::binary_function<cv Ty*, T2, Ret>` (dlatego Definiowanie typu zagnieżdżonego `result_type` jako synonim dla *Ret*, zagnieżdżony typ `first argument_type` jako synonim dla `cv Ty*`, a typ zagnieżdżony `second argument_type`jako synonim dla `T2`) tylko wtedy, gdy typ *Ty* jest wskaźnikiem do funkcji składowej z kwalifikatorem cv `cv` przyjmującą jeden argument typu `T2`.

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

Pomocnik funkcje szablonu użytego do stworzenia funkcji adapterów obiektu dla funkcji składowych po zainicjowaniu wskaźnika argumentów.

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

*pmem*<br/>
Wskaźnik do funkcji składowej klasy typu `Type` do konwersji na obiekt funkcyjny.

### <a name="return-value"></a>Wartość zwracana

A **const** lub **non_const** obiektu funkcji typu `mem_fun_t` lub `mem_fun1_t`.

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

Pomocnik funkcje szablonu użytego do stworzenia funkcji adapterów obiektu dla funkcji Członkowskich, gdy inicjowana przy użyciu argumenty odwołania.

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

*pmem*<br/>
Wskaźnik do funkcji składowej klasy typu `Type` do konwersji na obiekt funkcyjny.

### <a name="return-value"></a>Wartość zwracana

A **const** lub `non_const` obiektu funkcji typu `mem_fun_ref_t` lub `mem_fun1_ref_t`.

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

Zwraca uzupełnienie predykat.

```cpp
template <class UnaryPredicate>
unary_negate<UnaryPredicate> not1(const UnaryPredicate& pred);
```

### <a name="parameters"></a>Parametry

*P.*<br/>
Predykat jednoelementowy, aby być ujemna.

### <a name="return-value"></a>Wartość zwracana

Predykat jednoelementowy, będącego negację Predykat jednoelementowy zmodyfikowane.

### <a name="remarks"></a>Uwagi

Jeśli `unary_negate` jest zbudowany z Predykat jednoelementowy **p.**( *x*), a następnie zwraca **! P.**( *x*).

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

Zwraca uzupełnienie predykat binarny.

```cpp
template <class BinaryPredicate>
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```

### <a name="parameters"></a>Parametry

*FUNC*<br/>
Predykat binarny, aby być ujemna.

### <a name="return-value"></a>Wartość zwracana

Predykat binarny, który negację predykat binarny jest modyfikowany.

### <a name="remarks"></a>Uwagi

Jeśli `binary_negate` jest zbudowany z predykat binarny **BinPred**( *x*, *y*), a następnie zwraca! **BinPred**( *x*, *y*).

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

Szablon funkcji pomocnika używana do konwersji jednoargumentowy i wskaźników do funkcji binarne, odpowiednio do funkcji potężnej jednoargumentowy i danych binarnych.

```cpp
template <class Arg, class Result>
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```

### <a name="parameters"></a>Parametry

*pfunc*<br/>
Jednoargumentowy lub binarny wskaźnik funkcji do konwersji na funkcję dostosowywalne.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja szablonu zwraca funkcję jednoargumentową [pointer_to_unary_function —](../standard-library/pointer-to-unary-function-class.md) < `Arg`, **wynik**> (\* `pfunc`).

Druga funkcja szablonu zwraca binarny funkcja [pointer_to_binary_function —](../standard-library/pointer-to-binary-function-class.md) \< **Arg1**, **argument2**, **wynik**> (\* `pfunc`).

### <a name="remarks"></a>Uwagi

Wskaźnik funkcji jest obiektem funkcji i może być przekazywany do dowolnego algorytmu biblioteki standardowej języka C++, który oczekuje, że funkcja jako parametru, ale nie jest dostosowana. Do korzystania z adaptera, takich jak powiązania wartości do niego lub użyciu negator, należy podać zagnieżdżonych typów, które umożliwiają dostosowanie takie. Konwersja jednoargumentowy i danych binarnych wskaźników do funkcji przez `ptr_fun` dzięki funkcji pomocnika adapterów funkcji do pracy z jednoargumentowy i danych binarnych wskaźników funkcji.

### <a name="example"></a>Przykład

[!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]

## <a name="ref"></a>  REF

Konstruuje `reference_wrapper` z argumentem.

```cpp
template <class Ty>
reference_wrapper<Ty> ref(Ty& arg);

template <class Ty>
reference_wrapper<Ty> ref(reference_wrapper<Ty>& arg);
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `arg`; w szczególności `reference_wrapper<Ty>(arg)`.

### <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano dwie funkcje: jeden powiązany do zmiennej ciągu, powiązane z na odwołanie do zmiennej ciągu jest obliczana przez wywołanie `ref`. Po zmianie wartości zmiennej, pierwsza funkcja w dalszym ciągu używać starej wartości, a druga funkcja używa nowej wartości.

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

## <a name="swap"></a>  swap

Zamień dwa `function` obiektów.

```cpp
template <class Fty>
void swap(function<Fty>& f1, function<Fty>& f2);
```

### <a name="parameters"></a>Parametry

*Fty*<br/>
Typ kontrolowany przez obiekty funkcji.

*F1*<br/>
Pierwszy obiekt funkcyjny.

*F2*<br/>
Drugi obiekt funkcyjny.

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
