---
title: Funkcja klasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- functional/std::function
- functional/std::function::result_type
- functional/std::function::assign
- functional/std::function::swap
- functional/std::function::target
- functional/std::function::target_type
- functional/std::function::operator unspecified
- functional/std::function::operator()
dev_langs:
- C++
helpviewer_keywords:
- std::function [C++]
- std::function [C++], result_type
- std::function [C++], assign
- std::function [C++], swap
- std::function [C++], target
- std::function [C++], target_type
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ca8621067c851b5a1e107eb16800d546562fbb6
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959937"
---
# <a name="function-class"></a>function — Klasa

Otoka dla wywoływanego obiektu.

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

*Fty* typu funkcji do opakowania.

*AX* funkcja alokatora.

## <a name="remarks"></a>Uwagi

Klasa szablonu to wywołanie otoką ma podpis wywołania `Ret(T1, T2, ..., TN)`. Umożliwia ona ująć wielu obiektów wywoływane w jednolity otoki.

Niektóre funkcje Członkowskie przyjmują operand, że nazwy obiektu docelowego żądanej. Argument operacji można określić na kilka sposobów:

`fn` --wywoływanego obiektu `fn`; po wywołaniu `function` obiekt przechowuje kopię `fn`

`fnref` — obiekt o nazwie określonej przez `fnref.get()`; po wywołaniu `function` obiektu zawiera odwołanie do `fnref.get()`

`right` --wywoływanego obiektu, jeśli w posiadaniu `function` obiektu `right`

`npc` --wskaźnika o wartości null; Po wywołaniu `function` obiekt jest pusty

We wszystkich przypadkach `INVOKE(f, t1, t2, ..., tN)`, gdzie `f` jest wywoływanego obiektu i `t1, t2, ..., tN` są l-wartością typów `T1, T2, ..., TN` odpowiednio, musi być poprawnie sformułowany i, jeśli `Ret` nie jest void, możliwa do przekonwertowania na `Ret`.

Pusta `function` obiektu nie przechowuje wywoływanego obiektu lub odwołanie do wywoływanego obiektu.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[— Funkcja](#function)|Tworzy otokę, która jest pusta lub przechowuje obiekt możliwy do wywołania dowolnego typu z ustaloną sygnaturę.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[result_type](#result_type)|Zwracany typ przechowywany obiekt możliwy do wywołania.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Przypisz](#assign)|Przypisuje wywoływanego obiektu, do tego obiektu funkcji.|
|[swap](#swap)|Zamień dwa obiekty możliwy do wywołania.|
|[Docelowy](#target)|Sprawdza, czy przechowywany obiekt jest możliwy do wywołania określonych.|
|[target_type](#target_type)|Pobiera typ informacji na obiekt.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[nie określono tego parametru Function::operator](#op_unspecified)|Sprawdza, czy istnieje przechowywany obiekt możliwy do wywołania.|
|[Funkcja:: operator()](#op_call)|Wywołuje wywoływanego obiektu.|
|[Function::operator =](#op_eq)|Zastępuje przechowywany obiekt możliwy do wywołania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** standardowe

## <a name="assign"></a>  funkcji

Przypisuje wywoływanego obiektu, do tego obiektu funkcji.

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

*_Func* wywoływanego obiektu.

*_Fnref* otok odwołania, który zawiera obiekt możliwy do wywołania.

*AX* obiekt programu przydzielania.

### <a name="remarks"></a>Uwagi

Element członkowski funkcji każdego Zastąp `callable object` posiadaniu `*this` z obiekt przekazany jako `operand`. Zarówno przydzielanie magazynu za pomocą obiektu programu przydzielania *Ax*.

## <a name="function"></a>  Function::Function

Tworzy otokę, która jest pusta lub przechowuje obiekt możliwy do wywołania dowolnego typu z ustaloną sygnaturę.

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

*prawy* obiekt funkcji do skopiowania.

*FX* Typ wywoływanego obiektu.

*_Func* obiekt do opakowania.

*ALLOC* typ programu przydzielania.

*AX* alokator.

*_Fnref* odwołania obiekt do opakowania.

### <a name="remarks"></a>Uwagi

Dwa pierwsze konstruktory utworzyć pustą `function` obiektu. Następne trzy konstruktory konstruowania `function` obiekt, który zawiera obiekt jest przekazywany jako argument. Ostatnie dwa konstruktory przydzielanie magazynu za pomocą obiektu programu przydzielania Ax.

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

## <a name="op_unspecified"></a>  nie określono tego parametru Function::operator

Sprawdza, czy istnieje przechowywany obiekt możliwy do wywołania.

```cpp
operator unspecified();
```

### <a name="remarks"></a>Uwagi

Operator zwraca wartość, która jest konwertowany na **bool** z wartością true tylko wtedy, gdy obiekt nie jest pusty. Możesz użyć do sprawdzenia, czy obiekt jest pusty.

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

## <a name="op_call"></a>  Funkcja:: operator()

Wywołuje wywoływanego obiektu.

```cpp
result_type operator()(
    T1 t1,
    T2 t2, ...,
    TN tN);
```

### <a name="parameters"></a>Parametry

*TN* typ argumentu n-tego wywołania.

*tN* n-ty argument wywołania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `INVOKE(fn, t1, t2, ..., tN, Ret)`, gdzie `fn` jest obiektem docelowym przechowywane w `*this`. Możesz użyć go do wywołania opakowana wywoływanego obiektu.

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

## <a name="op_eq"></a>  Function::operator =

Zastępuje przechowywany obiekt możliwy do wywołania.

```cpp
function& operator=(null_ptr_type npc);
function& operator=(const function& right);
template <class Fty>
    function& operator=(Fty fn);
template <class Fty>
    function& operator=(reference_wrapper<Fty> fnref);
```

### <a name="parameters"></a>Parametry

*npc* stałą pustego wskaźnika.

*prawy* obiekt funkcji do skopiowania.

*FN* obiekt do opakowania.

*fnref* odwołania obiekt do opakowania.

### <a name="remarks"></a>Uwagi

Operatory każdego Zamień posiadane przez obiekt `*this` przy użyciu wywoływanego obiektu przekazywany jako argument.

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

## <a name="result_type"></a>  Function::result_type

Zwracany typ przechowywany obiekt możliwy do wywołania.

```cpp
typedef Ret result_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem typu `Ret` w sygnatury wywołania z tego szablonu. Możesz użyć do określenia zwracany typ opakowany wywoływanego obiektu.

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

## <a name="swap"></a>  Function::swap

Zamień dwa obiekty możliwy do wywołania.

```cpp
void swap(function& right);
```

### <a name="parameters"></a>Parametry

*prawy* obiekt funkcji, która ma być Zamień.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia obiektów docelowych między `*this` i *prawo*. Ją w stałym czasie i zgłasza żadnych wyjątków.

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

## <a name="target"></a>  Function::target

Sprawdza, czy przechowywany obiekt jest możliwy do wywołania określonych.

```cpp
template <class Fty2>
    Fty2 *target();
template <class Fty2>
    const Fty2 *target() const;
```

### <a name="parameters"></a>Parametry

*Fty2* Typ wywoływanego obiektu docelowego do przetestowania.

### <a name="remarks"></a>Uwagi

Typ *Fty2* musi być możliwy do wywołania dla typów argumentu `T1, T2, ..., TN` oraz zwracany typ `Ret`. Jeśli `target_type() == typeid(Fty2)`, funkcja szablonu elementu członkowskiego zwraca adresu docelowego obiektu; w przeciwnym razie zwraca wartość 0.

Typ *Fty2* jest wywoływane dla typów argumentu `T1, T2, ..., TN` oraz zwracany typ `Ret` if dla l-wartością `fn, t1, t2, ..., tN` typów `Fty2, T1, T2, ..., TN`odpowiednio `INVOKE(fn, t1, t2, ..., tN)` jest dobrze sformułowany i, jeśli `Ret`nie **void**, jest konwertowany na `Ret`.

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

## <a name="target_type"></a>  Function::target_type

Pobiera typ informacji na obiekt.

```cpp
const std::type_info& target_type() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `typeid(void)` Jeśli `*this` jest pusta, w przeciwnym razie zwraca `typeid(T)`, gdzie `T` jest typem obiektu docelowego.

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

## <a name="see-also"></a>Zobacz także

[mem_fn](../standard-library/functional-functions.md#mem_fn)<br/>
[reference_wrapper, klasa](../standard-library/reference-wrapper-class.md)<br/>
