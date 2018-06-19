---
title: '&lt;Pamięć&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- memory/std::operator!=
- memory/std::operator>
- memory/std::operator>=
- memory/std::operator<
- memory/std::operator<=
- memory/std::operator<<
- memory/std::operator==
dev_langs:
- C++
ms.assetid: 257e3ba9-c4c2-4ae8-9b11-b156ba9c28de
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01fe61112e5b36c8341e4a3209a9bec335549736
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857194"
---
# <a name="ltmemorygt-operators"></a>&lt;Pamięć&gt; operatory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|[Operator&gt;=](#op_gt_eq)|
|[Operator&lt;](#op_lt)|[Operator&lt;&lt;](#op_lt_lt)|[Operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator! =

Testy pod kątem nierówności między obiektami.

```cpp
template <class Type, class Other>
bool operator!=(
    const allocator<Type>& left,
    const allocator<Other>& right) throw();

template <class T, class Del1, class U, class Del2>
bool operator!=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator!=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parametry

`left` Jeden z obiektów pod kątem nierówności.

`right` Jeden z obiektów pod kątem nierówności.

`Ty1` Typ kontrolowane przez wskaźnik udostępnione po lewej stronie.

`Ty2` Typ kontrolowane przez prawo wskaźnika udostępnionego.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** obiekty nie są równe; **false** Jeśli obiekty są takie same.

### <a name="remarks"></a>Uwagi

Pierwszy operator szablonu zwraca wartość false. (Wszystkie domyślne allocators — są takie same).

Operatory drugi i trzeci szablon zwracać `!(left == right)`.

### <a name="example"></a>Przykład

```cpp
// memory_op_me.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<double> Alloc;
   vector <char>:: allocator_type v1Alloc;

   if ( Alloc != v1Alloc )
      cout << "The allocator objects Alloc & v1Alloc not are equal."
           << endl;
   else
      cout << "The allocator objects Alloc & v1Alloc are equal."
           << endl;
}
```

```Output
The allocator objects Alloc & v1Alloc are equal.
```

### <a name="example"></a>Przykład

```cpp
// std__memory__operator_ne.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(0));
    std::shared_ptr<int> sp1(new int(0));

    std::cout << "sp0 != sp0 == " << std::boolalpha
        << (sp0 != sp0) << std::endl;
    std::cout << "sp0 != sp1 == " << std::boolalpha
        << (sp0 != sp1) << std::endl;

    return (0);
    }

```

```Output
sp0 != sp0 == false
sp0 != sp1 == true
```

## <a name="op_eq_eq"></a>  operator ==

Testy równości między obiektami.

```cpp
template <class Type, class Other>
bool operator==(
    const allocator<Type>& left,
    const allocator<Other>& right) throw();

template <class Ty1, class Del1, class Ty2, class Del2>
bool operator==(
    const unique_ptr<Ty1, Del1>& left,
    const unique_ptr<Ty2, Del2>& right);

template <class Ty1, class Ty2>
bool operator==(
    const shared_ptr<Ty1>& left;,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parametry

`left` Jeden z obiektów pod kątem równości.

`right` Jeden z obiektów pod kątem równości.

`Ty1` Typ kontrolowane przez wskaźnik udostępnione po lewej stronie.

`Ty2` Typ kontrolowane przez prawo wskaźnika udostępnionego.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli obiekty są takie same, `false` obiekty nie są równe.

### <a name="remarks"></a>Uwagi

Pierwszy operator szablonu zwraca wartość true. (Wszystkie domyślne allocators — są takie same).

Operatory drugi i trzeci szablon zwracać ` left.get() ==  right.get()`.

### <a name="example"></a>Przykład

```cpp
// memory_op_eq.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<char> Alloc;
   vector <int>:: allocator_type v1Alloc;

   allocator<char> cAlloc(Alloc);
   allocator<int> cv1Alloc(v1Alloc);

   if ( cv1Alloc == v1Alloc )
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."
           << endl;

   if ( cAlloc == Alloc )
      cout << "The allocator objects cAlloc & Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cAlloc & Alloc are not equal."
           << endl;
}
```

```Output
The allocator objects cv1Alloc & v1Alloc are equal.
The allocator objects cAlloc & Alloc are equal.
```

### <a name="example"></a>Przykład

```cpp
// std__memory__operator_eq.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(0));
    std::shared_ptr<int> sp1(new int(0));

    std::cout << "sp0 == sp0 == " << std::boolalpha
        << (sp0 == sp0) << std::endl;
    std::cout << "sp0 == sp1 == " << std::boolalpha
        << (sp0 == sp1) << std::endl;

    return (0);
    }

```

```Output
sp0 == sp0 == true
sp0 == sp1 == false
```

## <a name="op_gt_eq"></a>  Operator&gt;=

Testy dla jednego obiektu jest większa niż lub równa drugiego obiektu.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator>=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U, Del2>& right);

template <class Ty1, class Ty2>
bool operator>=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parametry

`left` Jeden z obiektów, które ma zostać porównane.

`right` Jeden z obiektów, które ma zostać porównane.

`Ty1` Typ kontrolowane przez wskaźnik udostępnione po lewej stronie.

`Ty2` Typ kontrolowane przez prawo wskaźnika udostępnionego.

### <a name="remarks"></a>Uwagi

Operatory szablonu zwracać `left.get() >= right.get()`.

## <a name="op_lt"></a>  Operator&lt;

Testy dla jednego trwa obiektu za mniej niż drugi obiekt.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator<(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator<(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parametry

`left` Jeden z obiektów, które ma zostać porównane.

`right` Jeden z obiektów, które ma zostać porównane.

`Ty1` Typ kontrolowane przez wskaźnik po lewej stronie.

`Ty2` Typ kontrolowane przez prawo wskaźnika.

## <a name="op_lt_eq"></a>  Operator&lt;=

Testy dla jednego obiektu jest większa niż drugi obiekt.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator<=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator<=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parametry

`left` Jeden z obiektów, które ma zostać porównane.

`right` Jeden z obiektów, które ma zostać porównane.

`Ty1` Typ kontrolowane przez wskaźnik udostępnione po lewej stronie.

`Ty2` Typ kontrolowane przez prawo wskaźnika udostępnionego.

### <a name="remarks"></a>Uwagi

Zwraca operatory szablonu `left.get() <= right.get()`

## <a name="op_gt"></a>  Operator&gt;

Testy dla jednego obiektu, jest większy niż drugi obiekt.

```cpp
template <class Ty1, class Del1, class Ty2, class Del2>
bool operator>(
    const unique_ptr<Ty1, Del1>& left,
    const unique_ptr<Ty2&, Del2gt;& right);

template <class Ty1, class Ty2>
bool operator>(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parametry

`left` Jeden z obiektów, które ma zostać porównane.

`right` Jeden z obiektów, które ma zostać porównane.

`Ty1` Typ kontrolowane przez wskaźnik udostępnione po lewej stronie.

`Ty2` Typ kontrolowane przez prawo wskaźnika udostępnionego.

## <a name="op_lt_lt"></a>  Operator&lt;&lt;

Zapisuje udostępnionego wskaźnika do strumienia.

```cpp
template <class Elem, class Tr, class Ty>
std::basic_ostream<Elem, Tr>& operator<<(std::basic_ostream<Elem, Tr>& out,
    shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>Parametry

`Elem` Typ elementu strumienia.

`Tr` Typ cech elementu strumienia.

`Ty` Typ kontrolowane przez wskaźnik udostępnionego.

`out` W strumieniu wyjściowym.

`sp` Wskaźnik udostępnionego.

### <a name="remarks"></a>Uwagi

Funkcja szablonu `out << sp.get()`.

### <a name="example"></a>Przykład

```cpp
// std__memory__operator_sl.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "sp0 == " << sp0 << " (varies)" << std::endl;

    return (0);
    }

```

```Output
sp0 == 3f3040 (varies)
```

## <a name="see-also"></a>Zobacz także

[\<memory>](../standard-library/memory.md)<br/>
