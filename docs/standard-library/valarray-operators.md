---
title: '&lt;&gt;Operatory valarray'
ms.date: 03/27/2019
f1_keywords:
- valarray/std::operator!=
- valarray/std::operator%
- valarray/std::operator&amp;
- valarray/std::operator&amp;&amp;
- valarray/std::operator&gt;
- valarray/std::operator&gt;&gt;
- valarray/std::operator&gt;=
- valarray/std::operator&lt;
- valarray/std::operator&lt;&lt;
- valarray/std::operator&lt;=
- valarray/std::operator*
- valarray/std::operator+
- valarray/std::operator-
- valarray/std::operator/
- valarray/std::operator==
- valarray/std::operator^
- valarray/std::operator|
- valarray/std::operator||
ms.assetid: 8a53562c-90ab-4eb3-85d3-ada5259d90b0
helpviewer_keywords:
- std::operator!= (valarray), std::operator&amp; (valarray)
- std::operator&amp;&amp; (valarray)
- std::operator&gt; (valarray)
- std::operator&gt;&gt; (valarray)
- std::operator&gt;= (valarray)
- std::operator&lt; (valarray)
- std::operator&lt;&lt; (valarray)
- std::operator&lt;= (valarray), std::operator== (valarray)
ms.openlocfilehash: 76eb3553090cd88cf0798b2b17bbd49906852e40
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212012"
---
# <a name="ltvalarraygt-operators"></a>&lt;&gt;Operatory valarray

## <a name="operator"></a><a name="op_neq"></a>operator! =

Testuje, czy odpowiadające elementy dwóch valarrays o równym rozmiarze są nierówne lub czy wszystkie elementy valarray są nierówne określonej wartości.

```cpp
template <class Type>
valarray<bool>
operator!=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator!=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator!=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Pierwszy z dwóch valarrays, których elementy mają być testowane pod kątem nierówności.

*Kliknij*\
Drugi z dwóch valarrays, których elementy mają być testowane pod kątem nierówności.

### <a name="return-value"></a>Wartość zwracana

Valarray wartości logicznych, z których każdy jest:

- **`true`** Jeśli odpowiadające elementy są różne.

- **`false`** Jeśli odpowiadające elementy nie są równe.

### <a name="remarks"></a>Uwagi

Pierwszy operator szablonu zwraca obiekt klasy [valarray \<bool> ](../standard-library/valarray-bool-class.md), z których każdy `I` zawiera elementy `left[I] != right[I]` .

Drugi operator szablonu jest przechowywany w elemencie `I` `left[I] != right` .

Trzeci operator szablonu jest przechowywany w elemencie `I` `left != right[I]` .

### <a name="example"></a>Przykład

```cpp
// valarray_op_ne.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL != vaR );
   cout << "The element-by-element result of "
        << "the not equal comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the not equal comparison test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="operator"></a><a name="op_mod"></a>zakład

Uzyskuje resztę dzielącą odpowiadające elementy o dwóch równych rozmiarach valarrays lub dzielących valarray przez określoną wartość lub dzielącą określoną wartość przez valarray.

```cpp
template <class Type>
valarray<Type>
operator%(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator%(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator%(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Wartość lub valarray, która służy jako dywidenda, do której należy podzielić inną wartość lub valarray.

*Kliknij*\
Wartość lub valarray, która służy jako dzielnik i dzieli inną wartość lub valarray.

### <a name="return-value"></a>Wartość zwracana

Element valarray, którego elementy stanowią reszty z *lewej strony* podzielone przez *prawo*.

### <a name="example"></a>Przykład

```cpp
// valarray_op_rem.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 6 ), vaR ( 6 );
   valarray<int> vaREM ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  53;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -67;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  3*i+1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaREM = ( vaL % vaR );
   cout << "The remainders from the element-by-element "
        << "division is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaREM [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 53 -67 53 -67 53 -67 ).
The initial Right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
valarray: ( 0 -3 4 -7 1 -3 ).
```

## <a name="operatoramp"></a><a name="op_amp"></a>zakład&amp;

Uzyskuje bitowe **i** między odpowiednimi elementami o dwóch rozmiarach o rozmiarze valarrays lub między valarray a określoną wartością typu elementu.

```cpp
template <class Type>
valarray<Type>
operator&(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator&(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator&(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Pierwszy z dwóch valarrays, których odpowiednie elementy mają być połączone z bitową `AND` lub określoną wartością typu elementu, który ma być połączony bitowy z każdym elementem valarray.

*Kliknij*\
Drugi z dwóch valarrays, których odpowiednie elementy mają być połączone z bitową `AND` lub określoną wartością typu elementu, który ma być połączony bitowy z każdym elementem valarray.

### <a name="return-value"></a>Wartość zwracana

Element valarray, którego elementy są kombinacją elementów koniunkcji bitowej i operacji *lewej* i *prawej*.

### <a name="remarks"></a>Uwagi

Operacji bitowej można używać tylko w celu manipulowania bitami **`char`** w **`int`** typach danych i wariantami, a nie w **`float`** , **`double`** , **longdouble**, **`void`** **`bool`** lub innych, bardziej złożonych typów danych.

Wartość bitowa `AND` ma taką samą tabelę prawdy jak wartość logiczna, `AND` ale ma zastosowanie do typu danych na poziomie poszczególnych bitów. [Operator&&](#op_amp_amp) ma zastosowanie na poziomie elementu, licząc wszystkie wartości niezerowe jako prawdziwe, a wynikiem jest valarray wartości logicznych. Operator bitowy `AND` [&](#op_amp), z kolei, może spowodować valarray wartości innych niż 0 lub 1, w zależności od wyniku operacji bitowej.

### <a name="example"></a>Przykład

```cpp
// valarray_op_bitand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaBWA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i+1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaBWA = ( vaL & vaR );
   cout << "The element-by-element result of "
        << "the bitwise operator & is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaBWA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 2 0 4 0 6 0 8 0 10 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the bitwise operator & is the
valarray: ( 0 0 0 0 0 4 0 0 0 8 ).
```

## <a name="operatorampamp"></a><a name="op_amp_amp"></a>zakład&amp;&amp;

Uzyskuje koniunkcję logiczną **i** między odpowiednimi elementami o dwóch równych rozmiarach valarrays lub między valarray a określoną wartością typu elementu valarray.

```cpp
template <class Type>
valarray<bool>
operator&&(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator&&(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator&&(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Pierwszy z dwóch valarrays, których odpowiednie elementy mają być połączone z logiczną `AND` lub określoną wartością typu elementu, który ma być połączony z każdym elementem valarray.

*Kliknij*\
Drugi z dwóch valarrays, których odpowiednie elementy mają być połączone z logiczną `AND` lub określoną wartością typu elementu, który ma być połączony z każdym elementem valarray.

### <a name="return-value"></a>Wartość zwracana

Element valarray, którego elementy są typu bool i są kombinacją elementów dla logicznej `AND` operacji *lewej* i *prawej*.

### <a name="remarks"></a>Uwagi

Wartość logiczna `ANDoperator&&` jest stosowana na poziomie elementu, licząc wszystkie wartości niezerowe jako prawdziwe, a wynikiem jest valarray wartości logicznych. Bitowa wersja `AND` , [operator&,](#op_amp), z kolei, może spowodować valarray wartości innych niż 0 lub 1, w zależności od wyniku operacji bitowej.

### <a name="example"></a>Przykład

```cpp
// valarray_op_logand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL && vaR );
   cout << "The element-by-element result of "
        << "the logical AND operator&& is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&& is the
valarray: ( 0 0 0 1 0 1 0 1 0 1 ).
```

## <a name="operatorgt"></a><a name="op_gt"></a>zakład&gt;

Testuje, czy elementy jednego valarray są większe niż elementy o równym rozmiarze valarray lub czy wszystkie elementy valarray są większe lub mniejsze niż określona wartość.

```cpp
template <class Type>
valarray<bool>
operator>(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator>(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator>(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Pierwszy z dwóch valarrays, których elementy mają być porównane, lub określoną wartość do porównania z każdym elementem valarray.

*Kliknij*\
Drugi z dwóch valarrays, których elementy mają być porównane, lub określoną wartość do porównania z każdym elementem valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray wartości logicznych, z których każdy jest:

- **`true`** Jeśli *lewy* element lub wartość są większe niż odpowiadający mu *prawy* element lub wartość.

- **`false`** Jeśli *lewy* element lub wartość nie jest większy niż odpowiadający mu *prawy* element lub wartość.

### <a name="remarks"></a>Uwagi

Jeśli liczba elementów w dwóch valarrays nie jest równa, wynik jest niezdefiniowany.

### <a name="example"></a>Przykład

```cpp
// valarray_op_gt.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL > vaR );
   cout << "The element-by-element result of "
        << "the greater than comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than comparison test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>zakład&gt;=

Testuje, czy elementy jednego valarray są większe niż lub równe elementom o równym rozmiarze valarray lub czy wszystkie elementy valarray są większe niż lub równe określonej wartości.

```cpp
template <class Type>
valarray<bool>
operator>=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator>=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator>=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Pierwszy z dwóch valarrays, których elementy mają być porównane, lub określoną wartość do porównania z każdym elementem valarray.

*Kliknij*\
Drugi z dwóch valarrays, których elementy mają być porównane, lub określoną wartość do porównania z każdym elementem valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray wartości logicznych, z których każdy jest:

- **`true`** Jeśli *lewy* element lub wartość jest większa lub równa odpowiadającemu *prawemu* elementowi lub wartości.

- **`false`** Jeśli *lewy* element lub wartość jest mniejszy niż odpowiadający mu *prawy* element lub wartość.

### <a name="remarks"></a>Uwagi

Jeśli liczba elementów w dwóch valarrays nie jest równa, wynik jest niezdefiniowany.

### <a name="example"></a>Przykład

```cpp
// valarray_op_ge.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL >= vaR );
   cout << "The element-by-element result of "
        << "the greater than or equal test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than or equal test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="operatorgtgt"></a><a name="op_gt_gt"></a>zakład&gt;&gt;

Prawy przesuwa bity dla każdego elementu valarray określoną liczbę pozycji lub przez liczbę elementów określoną przez drugi valarray.

```cpp
template <class Type>
valarray<Type>
operator>>(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator>>(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator>>(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Wartość, która ma zostać przesunięta, lub valarray, której elementy mają zostać przesunięte.

*Kliknij*\
Wartość wskazująca ilość prawego przesunięcia lub valarray, której elementy wskazują ilość elementów po prawej stronie.

### <a name="return-value"></a>Wartość zwracana

Element valarray, którego elementy zostały przesunięte w prawo o określoną liczbę.

### <a name="remarks"></a>Uwagi

Cyfry podpisane mają zachowane znaki.

### <a name="example"></a>Przykład

```cpp
// valarray_op_rs.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  64;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -64;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL >> vaR );
   cout << "The element-by-element result of "
        << "the right shift is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
```

## <a name="operatorlt"></a><a name="op_lt"></a>zakład&lt;

Testuje, czy elementy jednego valarray są mniejsze niż elementy o równym rozmiarze valarray lub czy wszystkie elementy valarray są większe lub mniejsze niż określona wartość.

```cpp
template <class Type>
valarray<bool>
operator<(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator<(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator<(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Pierwszy z dwóch valarrays, których elementy mają być porównane, lub określoną wartość do porównania z każdym elementem valarray.

*Kliknij*\
Drugi z dwóch valarrays, których elementy mają być porównane, lub określoną wartość do porównania z każdym elementem valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray wartości logicznych, z których każdy jest:

- **`true`** Jeśli *lewy* element lub wartość jest mniejszy niż odpowiadający mu *prawy* element lub wartość.

- **`false`** Jeśli *lewy* element lub wartość nie jest mniejszy niż odpowiadający mu *prawy* element lub wartość.

### <a name="remarks"></a>Uwagi

Jeśli liczba elementów dwóch valarrays nie jest równa, wynik jest niezdefiniowany.

### <a name="example"></a>Przykład

```cpp
// valarray_op_lt.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL < vaR );
   cout << "The element-by-element result of "
        << "the less-than comparson test is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the less-than comparson test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>zakład&lt;=

Testuje, czy elementy jednego valarray są mniejsze niż lub równe elementom o równym rozmiarze valarray lub czy wszystkie elementy valarray są większe lub równe lub mniejsze lub równe określonej wartości.

```cpp
template <class Type>
valarray<bool>
operator<=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator<=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator<=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Pierwszy z dwóch valarrays, których elementy mają być porównane, lub określoną wartość do porównania z każdym elementem valarray.

*Kliknij*\
Drugi z dwóch valarrays, których elementy mają być porównane, lub określoną wartość do porównania z każdym elementem valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray wartości logicznych, z których każdy jest:

- **`true`** Jeśli *lewy* element lub wartość jest mniejsza lub równa odpowiadającemu *prawemu* elementowi lub wartości.

- **`false`** Jeśli *lewy* element lub wartość są większe niż odpowiadający mu *prawy* element lub wartość.

### <a name="remarks"></a>Uwagi

Jeśli liczba elementów dwóch valarrays nie jest równa, wynik jest niezdefiniowany.

### <a name="example"></a>Przykład

```cpp
// valarray_op_le.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL <= vaR );
   cout << "The element-by-element result of "
        << "the less than or equal test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the less than or equal test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>zakład&lt;&lt;

Lewy przenosi bity dla każdego elementu valarray określoną liczbę pozycji lub przez liczbę elementów określoną przez drugi valarray.

```cpp
template <class Type>
valarray<Type>
operator<<(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator<<(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator<<(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Wartość, która ma zostać przesunięta, lub valarray, której elementy mają zostać przesunięte.

*Kliknij*\
Wartość wskazująca ilość przesunięcia w lewo lub valarray, której elementy wskazują liczbę elementów przesunięcia w lewo.

### <a name="return-value"></a>Wartość zwracana

Element valarray, którego elementy zostały przesunięte w lewo o określoną liczbę.

### <a name="remarks"></a>Uwagi

Cyfry podpisane mają zachowane znaki.

### <a name="example"></a>Przykład

```cpp
// valarray_op_ls.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL << vaR );
   cout << "The element-by-element result of "
        << "the left shift is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift is the
valarray: ( 1 -2 4 -8 16 -32 64 -128 ).
```

## <a name="operator"></a><a name="op_star"></a>zakład

Uzyskuje iloczyn elementów, między odpowiednimi elementami o rozmiarze dwóch valarrays lub między valarray a określoną wartością.

```cpp
template <class Type>
valarray<Type>
operator*(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator*(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator*(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Pierwszy z dwóch valarrays, których elementy mają zostać pomnożone lub określona wartość zostanie pomnożona przez każdy element valarray.

*Kliknij*\
Drugi z dwóch valarrays, których elementy mają być pomnożone lub określonej wartości, która ma zostać pomnożona przez każdy element valarray.

### <a name="return-value"></a>Wartość zwracana

Element valarray, którego elementy stanowią iloczyn elementów z *lewej* i *prawej*strony.

### <a name="example"></a>Przykład

```cpp
// valarray_op_eprod.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL * vaR );
   cout << "The element-by-element result of "
        << "the multiplication is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
```

## <a name="operator"></a><a name="op_add"></a>operator +

Uzyskuje sumę elementów między odpowiadającymi im elementami o rozmiarze dwóch valarrays lub między valarray a określoną wartością.

```cpp
template <class Type>
valarray<Type>
operator+(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator+(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator+(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Pierwszy z dwóch valarrays, których elementy mają być dodane lub określonej wartości, która ma zostać dodana do każdego elementu valarray.

*Kliknij*\
Drugi z dwóch valarrays, których elementy mają być dodane lub określonej wartości, która ma zostać dodana do każdego elementu valarray.

### <a name="return-value"></a>Wartość zwracana

Element valarray, którego elementy są sumą rzeczy od *lewej* i *prawej*strony.

### <a name="example"></a>Przykład

```cpp
// valarray_op_esum.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL + vaR );
   cout << "The element-by-element result of "
        << "the sum is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
valarray: ( 2 0 4 2 6 4 8 6 ).
```

## <a name="operator-"></a><a name="operator-"></a>zakład

Uzyskuje różnicę elementów między odpowiednimi elementami o rozmiarze dwóch valarrays lub między valarray a określoną wartością.

```cpp
template <class Type>
valarray<Type>
operator-(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator-(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator-(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Wartość lub valarray, która służy jako odjemna, z którego inne wartości lub valarrays mają być odejmowane podczas tworzenia różnicy.

*Kliknij*\
Wartość lub valarray, która służy jako odjemnik, który ma zostać odjęty od innych wartości lub valarrays w celu utworzenia różnicy.

### <a name="return-value"></a>Wartość zwracana

Valarray, których elementy są różnicą dla elementów z *lewej* i *prawej*strony.

### <a name="remarks"></a>Uwagi

Terminologia arytmetyczna użyta podczas opisywania odejmowania:

różnica = odjemna-odjemnik

### <a name="example"></a>Przykład

```cpp
// valarray_op_ediff.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  10;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL - vaR );
   cout << "The element-by-element result of "
        << "the difference is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
```

## <a name="operator"></a><a name="op_div"></a>zakład

Uzyskuje iloraz elementów między odpowiednimi elementami o rozmiarze dwóch valarrays lub między valarray a określoną wartością.

```cpp
template <class Type>
valarray<Type>
operator/(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator/(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator/(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Wartość lub valarray, która służy jako stawka, do której należy podzielić inną wartość lub valarray w celu utworzenia ilorazu.

*Kliknij*\
Wartość lub valarray, która służy jako dzielnik i dzielący inną wartość lub valarray w tworzeniu ilorazu.

### <a name="return-value"></a>Wartość zwracana

Element valarray, którego elementy są elementem ilorazu *po lewej stronie* podzielonym po *prawej stronie*.

### <a name="remarks"></a>Uwagi

Terminologia arytmetyczna użyta podczas opisywania podziału:

iloraz = dzielna/dzielnik

### <a name="example"></a>Przykład

```cpp
// valarray_op_equo.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<double> vaL ( 6 ), vaR ( 6 );
   valarray<double> vaNE ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  100;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -100;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  2*i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL / vaR );
   cout << "The element-by-element result of "
        << "the quotient is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
valarray: ( inf -50 25 -16.6667 12.5 -10 ).
```

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

Testuje, czy odpowiadające elementy o dwóch równych rozmiarach valarrays są równe lub czy wszystkie elementy valarray są równe określonej wartości.

```cpp
template <class Type>
valarray<bool>
operator==(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator==(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator==(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Pierwszy z dwóch valarrays, których elementy mają być testowane pod kątem równości.

*Kliknij*\
Drugi z dwóch valarrays, których elementy mają być testowane pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

Valarray wartości logicznych, z których każdy jest:

- **`true`** Jeśli odpowiadające elementy są równe.

- **`false`** Jeśli odpowiadające elementy nie są równe.

### <a name="remarks"></a>Uwagi

Pierwszy operator szablonu zwraca obiekt klasy [valarray \<bool> ](../standard-library/valarray-bool-class.md), z których każdy `I` zawiera elementy `left[I] == right[I]` . Drugi operator szablonu jest przechowywany w elemencie `I` `left[I] == right` . Trzeci operator szablonu jest przechowywany w elemencie `I` `left == right[I]` .

### <a name="example"></a>Przykład

```cpp
// valarray_op_eq.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL == vaR );
   cout << "The element-by-element result of "
        << "the equality comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the equality comparison test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="operator"></a><a name="op_xor"></a>operator ^

Uzyskuje wartość bitową wykluczającą `OR` ( **XOR**) między odpowiednimi elementami o dwóch równych rozmiarach valarrays lub między valarray a określoną wartością typu elementu.

```cpp
template <class Type>
valarray<Type>
operator^(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator^(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator^(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Pierwszy z dwóch valarrays, których odpowiednie elementy mają być połączone z bitową **XOR** lub określoną wartością typu elementu, który ma być połączony bitowy z każdym elementem valarray.

*Kliknij*\
Drugi z dwóch valarrays, których odpowiednie elementy mają być połączone z bitową **XOR** lub określoną wartością typu elementu, który ma być połączony bitowy z każdym elementem valarray.

### <a name="return-value"></a>Wartość zwracana

Element valarray, którego elementy są kombinacją elementów dla bitowej operacji **XOR** z *lewej* i *prawej*strony.

### <a name="remarks"></a>Uwagi

Operacji bitowej można używać tylko w celu manipulowania bitami **`char`** w **`int`** typach danych i Variant, a nie w,,, i **`float`** **`double`** **`long double`** **`void`** **`bool`** innych, bardziej złożonych typach danych.

Bitowe wykluczające `OR` ( **XOR**) ma następującą semantykę: dane bity *b*1 i *b*2, *b*1 **XOR** *b*2 to **`true`** , jeśli dokładnie jeden z bitów ma wartość true; w **`false`** przypadku obu bitów ma wartość false lub jeśli obie bity mają wartość true.

### <a name="example"></a>Przykład

```cpp
// valarray_op_xor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL ^ vaR );
   cout << "The element-by-element result of "
        << "the bitwise XOR operator^ is the\n"
        << "valarray: ( ";
           for ( i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^ is the
valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
```

## <a name="operator124"></a><a name="op_or"></a>&#124; operatora

Uzyskuje wartość bitową `OR` między odpowiednimi elementami o dwóch rozmiarach valarrays lub między valarray a określoną wartością typu elementu.

```cpp
template <class Type>
valarray<Type>
operator|(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator|(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator|(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Pierwszy z dwóch valarrays, których odpowiednie elementy mają być połączone z bitową `OR` lub określoną wartością typu elementu, który ma być połączony bitowy z każdym elementem valarray.

*Kliknij*\
Drugi z dwóch valarrays, których odpowiednie elementy mają być połączone z bitową `OR` lub określoną wartością typu elementu, który ma być połączony bitowy z każdym elementem valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, których elementy są kombinacją elementów dla operacji bitowej z `OR` lewej i prawej *strony* . *right*

### <a name="remarks"></a>Uwagi

Operacji bitowej można używać tylko w celu manipulowania bitami **`char`** w **`int`** typach danych i wariantami, a nie w **`float`** , **`double`** , **longdouble**, **`void`** **`bool`** lub innych, bardziej złożonych typów danych.

Wartość bitowa lub ma taką samą tabelę prawdy co wartość logiczna `OR` , ale ma zastosowanie do typu danych na poziomie poszczególnych bitów. Dane bity *b*1 i *b*2, *b*1 `OR` *b*2 to **`true`** Jeśli co najmniej jeden z bitów ma wartość true lub **`false`** obie bity mają wartość false. Operator logiczny `OR` [&#124;&#124;](../standard-library/valarray-operators.md#op_lor) ma zastosowanie na poziomie elementu, licząc wszystkie niezerowe wartości jako **`true`** , a wynik jest valarray wartości logicznych. Wartość bitowa lub `operator|` , z kontrastem, może spowodować valarray wartości inne niż 0 lub 1, w zależności od wyniku operacji bitowej.

### <a name="example"></a>Przykład

```cpp
// valarray_op_bitor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;

   cout << "The initial Left valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL | vaR );
   cout << "The element-by-element result of "
        << "the bitwise OR operator| is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise OR operator| is the
valarray: ( 1 0 1 3 3 4 7 6 7 9 ).
```

## <a name="operator124124"></a><a name="op_lor"></a>&#124;&#124; operatora

Uzyskuje wartość logiczną `OR` między odpowiednimi elementami o dwóch rozmiarach valarrays lub między valarray a określoną wartością typu elementu valarray.

```cpp
template <class Type>
valarray<bool>
operator||(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator||(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator||(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Pierwszy z dwóch valarrays, których odpowiednie elementy mają być połączone z logiczną `OR` lub określoną wartością typu elementu, który ma być połączony z każdym elementem valarray.

*Kliknij*\
Drugi z dwóch valarrays, których odpowiednie elementy mają być połączone z logiczną `OR` lub określoną wartością typu elementu, który ma być połączony z każdym elementem valarray.

### <a name="return-value"></a>Wartość zwracana

Element valarray, którego elementy są typu **`bool`** i są połączeniem elementów logicznych lub operacji *lewej* i *prawej*.

### <a name="remarks"></a>Uwagi

Wartość logiczna `OR` `operator||` jest stosowana na poziomie elementu, licząc wszystkie wartości niezerowe jako **`true`** , a wynik jest valarray wartości logicznych. Bitowa wersja `OR` , [operator&#124;](../standard-library/valarray-operators.md#op_or) przez kontrast, może spowodować valarray wartości inne niż 0 lub 1, w zależności od wyniku operacji bitowej.

### <a name="example"></a>Przykład

```cpp
// valarray_op_logor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaLOR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  0;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  0;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLOR = ( vaL || vaR );
   cout << "The element-by-element result of "
        << "the logical OR operator|| is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaLOR [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 0 0 3 0 0 6 0 0 9 ).
The element-by-element result of the logical OR operator|| is the
valarray: ( 0 0 0 1 0 1 1 1 0 1 ).
```
