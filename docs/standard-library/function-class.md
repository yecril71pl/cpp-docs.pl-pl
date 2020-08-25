---
title: function — Klasa
ms.date: 11/04/2016
f1_keywords:
- functional/std::function
- functional/std::function::result_type
- functional/std::function::assign
- functional/std::function::swap
- functional/std::function::target
- functional/std::function::target_type
- functional/std::function::operator unspecified
- functional/std::function::operator()
helpviewer_keywords:
- std::function [C++]
- std::function [C++], result_type
- std::function [C++], assign
- std::function [C++], swap
- std::function [C++], target
- std::function [C++], target_type
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
ms.openlocfilehash: 052cbba69aa99d33de963a3e360e6951a6006bec
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831466"
---
# <a name="function-class"></a>function — Klasa

Otoka dla możliwego do oddzielenia obiektu.

## <a name="syntax"></a>Składnia

```cpp
template <class Fty>
class function  // Fty of type Ret(T1, T2, ..., TN)
    : public unary_function<T1, Ret>       // when Fty is Ret(T1)
    : public binary_function<T1, T2, Ret>  // when Fty is Ret(T1, T2)
{
public:
    typedef Ret result_type;

    function();
    function(nullptr_t);
    function(const function& right);
    template <class Fty2>
        function(Fty2 fn);
    template <class Fty2, class Alloc>
        function(reference_wrapper<Fty2>, const Alloc& Ax);

    template <class Fty2, class Alloc>
        void assign(Fty2, const Alloc& Ax);
    template <class Fty2, class Alloc>
        void assign(reference_wrapper<Fty2>, const Alloc& Ax);
    function& operator=(nullptr_t);
    function& operator=(const function&);
    template <class Fty2>
        function& operator=(Fty2);
    template <class Fty2>
        function& operator=(reference_wrapper<Fty2>);

    void swap(function&);
    explicit operator bool() const;

    result_type operator()(T1, T2, ....., TN) const;
    const std::type_info& target_type() const;
    template <class Fty2>
        Fty2 *target();

    template <class Fty2>
        const Fty2 *target() const;

    template <class Fty2>
        void operator==(const Fty2&) const = delete;
    template <class Fty2>
        void operator!=(const Fty2&) const = delete;
};
```

### <a name="parameters"></a>Parametry

*Fty*\
Typ funkcji do oblewania.

*Oś*\
Funkcja alokatora.

## <a name="remarks"></a>Uwagi

Szablon klasy jest otoką wywołania, której sygnatura wywołania to `Ret(T1, T2, ..., TN)` . Służy do umieszczania różnych wywoływanych obiektów w jednorodnej otoki.

Niektóre funkcje członkowskie przyjmują operand, który nazywa żądany obiekt docelowy. Możesz określić taki operand na kilka sposobów:

`fn` --Obiekt możliwy do `fn` wywołania; po wywołaniu `function` obiektu posiada kopię `fn`

`fnref` --możliwy do wywołania obiekt nazwany przez `fnref.get()` ; po wywołaniu `function` obiektu jest odwołanie do `fnref.get()`

`right` --Obiekt możliwy do odłożenia (jeśli istnieje), który jest przechowywany przez `function` obiekt `right`

`npc` --pusty wskaźnik; Po wywołaniu `function` obiekt jest pusty

We wszystkich przypadkach, `INVOKE(f, t1, t2, ..., tN)` gdzie `f` jest obiektem, który jest możliwy do `t1, t2, ..., tN` nalvalues `T1, T2, ..., TN` , musi być poprawnie sformułowany i, jeśli `Ret` nie jest typem void, można przekonwertować na `Ret` .

Pusty obiekt nie posiada możliwego `function` do przeprowadzenia obiektu ani odwołania do możliwego do narzutowania obiektu.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|Nazwa|Opis|
|-|-|
|[funkcyjn](#function)|Konstruuje otokę, która jest pusta lub przechowuje możliwy do przechowania obiekt dowolnego typu ze stałą sygnaturą.|

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|-|-|
|[result_type](#result_type)|Zwracany typ przechowywanego obiektu, który jest wywoływany.|

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[przypisać](#assign)|Przypisuje obiekt możliwy do oddzielenia do tego obiektu funkcji.|
|[wymiany](#swap)|Zamień dwa obiekty, które są wywoływane.|
|[obiektów](#target)|Testuje, czy przechowywany wywoływany obiekt jest wywoływany jako określony.|
|[target_type](#target_type)|Pobiera informacje o typie dla możliwego do odzyskania obiektu.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[nieokreślony operator](#op_unspecified)|Testuje, czy istnieje przechowywany możliwy do przeprowadzenia obiekt.|
|[operator ()](#op_call)|Wywołuje możliwy do wywołania obiekt.|
|[operator =](#op_eq)|Zastępuje przechowywany obiekt, który jest wywoływany.|

## <a name="assign"></a><a name="assign"></a> ponownie

Przypisuje obiekt możliwy do oddzielenia do tego obiektu funkcji.

```cpp
template <class Fx, class Alloc>
    void assign(
        Fx _Func,
        const Alloc& Ax);

template <class Fx, class Alloc>
    void assign(
        reference_wrapper<Fx> _Fnref,
        const Alloc& Ax);
```

### <a name="parameters"></a>Parametry

*_Func*\
Obiekt możliwy do narzutu.

*_Fnref*\
Otoka odwołania, która zawiera możliwy do narzutu obiekt.

*Oś*\
Obiekt alokatora.

### <a name="remarks"></a>Uwagi

Każdy element członkowski jest zastępowany `callable object` przez obiekt, który jest **`*this`** możliwy do przekazanie jako `operand` . Przydziel magazyn z obiektem alokatora *AX*.

## <a name="function"></a>Funkcja <a name="function"></a>

Konstruuje otokę, która jest pusta lub przechowuje możliwy do przechowania obiekt dowolnego typu ze stałą sygnaturą.

```cpp
function();
function(nullptr_t npc);
function(const function& right);
template <class Fx>
    function(Fx _Func);
template <class Fx>
    function(reference_wrapper<Fx> _Fnref);
template <class Fx, class Alloc>
    function(
        Fx _Func,
        const Alloc& Ax);

template <class Fx, class Alloc>
    function(
        reference_wrapper<Fx> _Fnref,
        const Alloc& Ax);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt funkcji do skopiowania.

*Niezr*\
Typ wywoływanego obiektu.

*_Func*\
Obiekt możliwy do zawinięcia.

*Alokacj*\
Typ alokatora.

*Oś*\
Program przydzielający.

*_Fnref*\
Odwołanie do możliwego do przewinięcia obiektu.

### <a name="remarks"></a>Uwagi

Pierwsze dwa konstruktory konstruują pusty `function` obiekt. Następne trzy konstruktory konstruują `function` obiekt, który przechowuje możliwy do przekazanie obiekt jako operand. Ostatnie dwa konstruktory przydzielą magazyn z obiektem alokatora systemu AX.

### <a name="example"></a>Przykład

```cpp
// std__functional__function_function.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>
#include <vector>

int square(int val)
{
    return val * val;
}

class multiply_by
{
public:
    explicit multiply_by(const int n) : m_n(n) { }

    int operator()(const int x) const
    {
        return m_n * x;
    }

private:
    int m_n;
};

int main()
{

    typedef std::vector< std::function<int (int)> > vf_t;

    vf_t v;
    v.push_back(square);
    v.push_back(std::negate<int>());
    v.push_back(multiply_by(3));

    for (vf_t::const_iterator i = v.begin(); i != v.end(); ++i)
    {
        std::cout << (*i)(10) << std::endl;
    }

    std::function<int (int)> f = v[0];
    std::function<int (int)> g;

    if (f) {
        std::cout << "f is non-empty (correct)." << std::endl;
    } else {
        std::cout << "f is empty (can't happen)." << std::endl;
    }

    if (g) {
        std::cout << "g is non-empty (can't happen)." << std::endl;
    } else {
        std::cout << "g is empty (correct)." << std::endl;
    }

    return 0;
}
```

```Output
100
-10
30
f is non-empty (correct).
g is empty (correct).
```

## <a name="operator-unspecified"></a><a name="op_unspecified"></a> nieokreślony operator

Testuje, czy istnieje przechowywany możliwy do przeprowadzenia obiekt.

```cpp
operator unspecified();
```

### <a name="remarks"></a>Uwagi

Operator zwraca wartość, która jest konwertowany na wartość **`bool`** true, tylko wtedy, gdy obiekt nie jest pusty. Służy do sprawdzania, czy obiekt jest pusty.

### <a name="example"></a>Przykład

```cpp
// std__functional__function_operator_bool.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == " << (bool)fn0 << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == " << (bool)fn1 << std::endl;

    return (0);
    }
```

```Output
not empty == false
not empty == true
```

## <a name="operator"></a><a name="op_call"></a> operator ()

Wywołuje możliwy do wywołania obiekt.

```cpp
result_type operator()(
    T1 t1,
    T2 t2, ...,
    TN tN);
```

### <a name="parameters"></a>Parametry

*TN*\
Typ argumentu n wywołania.

*tN*\
N-ty argument wywołania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `INVOKE(fn, t1, t2, ..., tN, Ret)` , gdzie `fn` jest obiektem docelowym przechowywanym w **`*this`** . Służy do wywoływania zapakowanego obiektu, który można wywołać.

### <a name="example"></a>Przykład

```cpp
// std__functional__function_operator_call.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
```

## <a name="operator"></a><a name="op_eq"></a> operator =

Zastępuje przechowywany obiekt, który jest wywoływany.

```cpp
function& operator=(null_ptr_type npc);
function& operator=(const function& right);
template <class Fty>
    function& operator=(Fty fn);
template <class Fty>
    function& operator=(reference_wrapper<Fty> fnref);
```

### <a name="parameters"></a>Parametry

*npc*\
Stała wskaźnika o wartości null.

*Kliknij*\
Obiekt funkcji do skopiowania.

*Fn*\
Obiekt możliwy do zawinięcia.

*fnref*\
Odwołanie do możliwego do przewinięcia obiektu.

### <a name="remarks"></a>Uwagi

Operatorzy każdy zastępują obiekt możliwy do przetrzymywania **`*this`** z obiektem możliwym do przekazanie jako operand.

### <a name="example"></a>Przykład

```cpp
// std__functional__function_operator_as.cpp
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
    fn1 = 0;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;

    fn1 = neg;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    fn1 = fn0;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    fn1 = std::cref(fn1);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
empty == true
empty == false
val == -3
empty == false
val == -3
empty == false
val == -3
```

## <a name="result_type"></a><a name="result_type"></a> result_type

Zwracany typ przechowywanego obiektu, który jest wywoływany.

```cpp
typedef Ret result_type;
```

### <a name="remarks"></a>Uwagi

Element typedef jest synonimem dla typu `Ret` w podpisie wywołania szablonu. Służy do określenia zwracanego typu zapakowanego obiektu, który można wywołać.

### <a name="example"></a>Przykład

```cpp
// std__functional__function_result_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;

    std::function<int (int)>::result_type val = fn1(3);
    std::cout << "val == " << val << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
```

## <a name="swap"></a><a name="swap"></a> wymiany

Zamień dwa obiekty, które są wywoływane.

```cpp
void swap(function& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt funkcyjny do zamiany.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia obiekty docelowe między **`*this`** i *po prawej*. Robi to w stałym czasie i nie zgłasza wyjątków.

### <a name="example"></a>Przykład

```cpp
// std__functional__function_swap.cpp
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

    fn0.swap(fn1);
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

## <a name="target"></a><a name="target"></a> obiektów

Testuje, czy przechowywany wywoływany obiekt jest wywoływany jako określony.

```cpp
template <class Fty2>
    Fty2 *target();
template <class Fty2>
    const Fty2 *target() const;
```

### <a name="parameters"></a>Parametry

*Fty2*\
Docelowy typ obiektu możliwy do przetestowania.

### <a name="remarks"></a>Uwagi

Typ *Fty2* musi być wywoływany dla typów argumentów `T1, T2, ..., TN` i zwracanego typu `Ret` . Jeśli `target_type() == typeid(Fty2)` , funkcja szablonu elementu członkowskiego zwraca adres obiektu docelowego; w przeciwnym razie zwraca wartość 0.

Typ *Fty2* jest wywoływany dla typów argumentów `T1, T2, ..., TN` i zwracanego typu, `Ret` Jeśli dla lvalues `fn, t1, t2, ..., tN` typów, odpowiednio, `Fty2, T1, T2, ..., TN` `INVOKE(fn, t1, t2, ..., tN)` jest poprawnie sformułowany i, jeśli `Ret` nie **`void`** , jest konwertowany na `Ret` .

### <a name="example"></a>Przykład

```cpp
// std__functional__function_target.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    typedef int (*Myfun)(int);
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "no target == " << (fn0.target<Myfun>() == 0) << std::endl;

    Myfun *fptr = fn0.target<Myfun>();
    std::cout << "val == " << (*fptr)(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "no target == " << (fn1.target<Myfun>() == 0) << std::endl;

    return (0);
    }
```

```Output
empty == false
no target == false
val == -3
empty == true
no target == true
```

## <a name="target_type"></a><a name="target_type"></a> target_type

Pobiera informacje o typie dla możliwego do odzyskania obiektu.

```cpp
const std::type_info& target_type() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `typeid(void)` wartość **`*this`** , jeśli jest pusta. w przeciwnym razie zwraca `typeid(T)` , gdzie `T` jest typem obiektu docelowego.

### <a name="example"></a>Przykład

```cpp
// std__functional__function_target_type.cpp
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
    std::cout << "type == " << fn0.target_type().name() << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "type == " << fn1.target_type().name() << std::endl;

    return (0);
    }
```

```Output
empty == false
type == int (__cdecl*)(int)
empty == true
type == void
```
