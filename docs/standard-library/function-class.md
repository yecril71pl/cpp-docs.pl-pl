---
title: Funkcja klasy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- functional/std::function
- functional/std::function::result_type
- functional/std::function::assign
- functional/std::function::swap
- functional/std::function::target
- functional/std::function::target_type
- functional/std::function::operator unspecified
- functional/std::function::operator()
dev_langs: C++
helpviewer_keywords:
- std::function [C++]
- std::function [C++], result_type
- std::function [C++], assign
- std::function [C++], swap
- std::function [C++], target
- std::function [C++], target_type
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: da4c8dd6a3141b16b9960720c6bb1789cd06f317
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="function-class"></a>function — Klasa
Otoka dla obiekt można wywołać.  
  
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
 `Fty`  
 Typ funkcji do zakodowania.  
  
 `Ax`  
 Funkcja przydzielania.  
  
## <a name="remarks"></a>Uwagi  
 Klasy szablonów jest otoką wywołanie jest których sygnatury wywołania `Ret(T1, T2, ..., TN)`. Umożliwia ona ujmij wielu obiektów, który można wywołać w uniform otoki.  
  
 Niektóre funkcje Członkowskie zająć argument, który określa obiekt docelowy. Argument operacji można określić na kilka sposobów:  
  
 `fn`— można wywołać obiektu `fn`; po wywołaniu metody `function` obiektu przechowuje kopię`fn`  
  
 `fnref`— można wywołać obiektu o nazwie `fnref.get()`; po wywołaniu metody `function` obiektu zawiera odwołanie do`fnref.get()`  
  
 `right`— można wywołać obiektu, jeśli taki występuje, posiadaniu `function` obiektu`right`  
  
 `npc`--wskaźnika o wartości null; Po wywołaniu metody `function` obiektu jest pusty  
  
 We wszystkich przypadkach `INVOKE(f, t1, t2, ..., tN)`, gdzie `f` można wywołać obiektu i `t1, t2, ..., tN` są lvalues typów `T1, T2, ..., TN` odpowiednio, musi być poprawnie sformułowany i, jeżeli `Ret` nie jest void, można przekonwertować na typ `Ret`.  
  
 Pusta `function` obiekt nie zawiera obiektu można wywołać lub odwołanie do obiektu można wywołać.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[Funkcja](#function)|Tworzy otoki, która jest pusta lub przechowuje dowolnego typu za pomocą stałych podpisu można wywołać obiektu.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[result_type](#result_type)|Typ zwracany przechowywanej można wywołać obiektu.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Przypisz](#assign)|Przypisuje można wywołać obiektu do obiektu tej funkcji.|  
|[swap](#swap)|Zamień dwa obiekty można wywołać.|  
|[docelowy](#target)|Testy, jeśli można wywołać obiektu przechowywana jest można wywołać określone.|  
|[target_type](#target_type)|Pobiera informacji o typie można wywołać obiektu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[Function::operator nieokreślone](#op_unspecified)|Testy, jeśli istnieje przechowywanej można wywołać obiektu.|  
|[Funkcja:: operator()](#op_call)|Wywołuje można wywołać obiektu.|  
|[Function::operator =](#op_eq)|Zastępuje przechowywanej można wywołać obiektu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<funkcjonalności >  
  
 **Namespace:** Standard  
  
##  <a name="assign"></a>Function::ASSIGN  
 Przypisuje można wywołać obiektu do obiektu tej funkcji.  
  
```  
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
 `_Func`  
 Można wywołać obiektu.  
  
 `_Fnref`  
 Otoka odwołanie, zawiera obiekt, który można wywołać.  
  
 `Ax`  
 Obiekt programu przydzielania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcje Członkowskie każdego Zamień `callable object` posiadaniu `*this` można wywołać obiektu przekazany jako `operand`. Oba przydzielić magazyn z obiektem alokatora `Ax`.  
  
##  <a name="function"></a>Function::Function  
 Tworzy otoki, która jest pusta lub przechowuje dowolnego typu za pomocą stałych podpisu można wywołać obiektu.  
  
```  
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
 `right`  
 Obiekt funkcji do skopiowania.  
  
 `Fx`  
 Typ obiektu, który można wywołać.  
  
 `_Func`  
 Można wywołać obiekt do zakodowania.  
  
 `Alloc`  
 Typ przydzielania.  
  
 `Ax`  
 Program przydzielania.  
  
 `_Fnref`  
 Odwołanie do obiektu można wywołać do zakodowania.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsze dwa konstruktory utworzyć pustą `function` obiektu. Tworzenia trzech kolejnych konstruktorów `function` obiekt przechowujący można wywołać obiektu przekazany jako argument. Ostatnie dwa konstruktory przydzielić magazyn z obiektem alokatora Ax.  
  
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
  
##  <a name="op_unspecified"></a>Function::operator nieokreślone  
 Testy, jeśli istnieje przechowywanej można wywołać obiektu.  
  
```  
operator unspecified();
```   
  
### <a name="remarks"></a>Uwagi  
 Zwraca wartość do przekonwertowania na `bool` o wartości true tylko wtedy, gdy obiekt nie jest pusty. Można użyć do sprawdzenia, czy obiekt jest pusty.  
  
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
  
##  <a name="op_call"></a>Funkcja:: operator()  
 Wywołuje można wywołać obiektu.  
  
```  
result_type operator()(
    T1 t1,
    T2 t2, ...,
    TN tN);
```  
  
### <a name="parameters"></a>Parametry  
 `TN`  
 Typ określona liczba wywołań argumentu.  
  
 `tN`  
 Argument n-tego wywołania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca `INVOKE(fn, t1, t2, ..., tN, Ret)`, gdzie `fn` jest obiektem docelowym przechowywane w `*this`. Umożliwia ona wywołać opakowana można wywołać obiektu.  
  
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
  
##  <a name="op_eq"></a>Function::operator =  
 Zastępuje przechowywanej można wywołać obiektu.  
  
```  
function& operator=(null_ptr_type npc);
function& operator=(const function& right);
template <class Fty>  
    function& operator=(Fty fn);
template <class Fty>  
    function& operator=(reference_wrapper<Fty> fnref);
```  
  
### <a name="parameters"></a>Parametry  
 `npc`  
 Stała wskaźnika o wartości null.  
  
 `right`  
 Obiekt funkcji do skopiowania.  
  
 `fn`  
 Można wywołać obiekt do zakodowania.  
  
 `fnref`  
 Odwołanie do obiektu można wywołać do zakodowania.  
  
### <a name="remarks"></a>Uwagi  
 Operatory każdego zastąpić można wywołać obiekt posiadaniu `*this` można wywołać obiektu przekazany jako argument.  
  
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
  
##  <a name="result_type"></a>Function::result_type  
 Typ zwracany przechowywanej można wywołać obiektu.  
  
```  
typedef Ret result_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Element typedef jest synonimem typu `Ret` w sygnatury wywołania szablonu. Można użyć do określenia zwracany typ opakowana można wywołać obiektu.  
  
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
  
##  <a name="swap"></a>Function::swap  
 Zamień dwa obiekty można wywołać.  
  
```  
void swap(function& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Obiekt funkcji wymiany.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zamienia obiektów docelowych między `*this` i `right`. Nie, w czasie stałej i zgłasza żadnych wyjątków.  
  
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
  
##  <a name="target"></a>Function::target  
 Testy, jeśli można wywołać obiektu przechowywana jest można wywołać określone.  
  
```  
template <class Fty2>  
    Fty2 *target();
template <class Fty2>  
    const Fty2 *target() const;
```  
  
### <a name="parameters"></a>Parametry  
 `Fty2`  
 Typ można wywołać obiektu docelowego do testowania.  
  
### <a name="remarks"></a>Uwagi  
 Typ `Fty2` musi zostać wywołane dla typów argumentu `T1, T2, ..., TN` , a zwracanym typem `Ret`. Jeśli `target_type() == typeid(Fty2)`, funkcja szablonu elementu członkowskiego zwraca adres obiektu docelowego; w przeciwnym razie zwraca wartość 0.  
  
 Typ `Fty2` można wywołać dla typów argumentu `T1, T2, ..., TN` , a zwracanym typem `Ret` przypadku lvalues `fn, t1, t2, ..., tN` typów `Fty2, T1, T2, ..., TN`odpowiednio `INVOKE(fn, t1, t2, ..., tN)` jest poprawnie sformułowany i, jeśli `Ret` nie jest `void`, można przekonwertować na typ `Ret`.  
  
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
  
##  <a name="target_type"></a>Function::target_type  
 Pobiera informacji o typie można wywołać obiektu.  
  
```  
const std::type_info& target_type() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca `typeid(void)` Jeśli `*this` jest pusta, w przeciwnym razie zwraca `typeid(T)`, gdzie `T` jest typem obiektu docelowego.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [mem_fn —](../standard-library/functional-functions.md#mem_fn)   
 [reference_wrapper — klasa](../standard-library/reference-wrapper-class.md)
