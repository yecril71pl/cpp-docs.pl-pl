---
title: '&lt;valarray —&gt; operatorów'
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
ms.openlocfilehash: 6de4b4ad75f9240fb86ff5e363f4a7d9062925d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365491"
---
# <a name="ltvalarraygt-operators"></a>&lt;valarray —&gt; operatorów

||||
|-|-|-|
|[operator!=](#op_neq)|[operator%](#op_mod)|[Operator&amp;](#op_amp)|
|[Operator&amp;&amp;](#op_amp_amp)|[Operator&gt;](#op_gt)|[Operator&gt;&gt;](#op_gt_gt)|
|[Operator&gt;=](#op_gt_eq)|[Operator&lt;](#op_lt)|[Operator&lt;&lt;](#op_lt_lt)|
|[Operator&lt;=](#op_lt_eq)|[operator*](#op_star)|[operator +](#op_add)|
|[operator-](#operator-)|[operator/](#op_div)|[operator==](#op_eq_eq)|
|[operator^](#op_xor)|[operator&#124;](#op_or)|[operator&#124;&#124;](#op_lor)|

## <a name="op_neq"></a>  operator! =

Sprawdza, czy odpowiadające elementy dwóch valarrays równej wielkości są różne lub tego, czy wszystkie elementy tablicy valarray są nierówne określoną wartość.

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

*left*<br/>
Pierwsza z dwóch valarrays, którego elementy mają być sprawdzane pod kątem nierówności.

*right*<br/>
Drugi dwóch valarrays, którego elementy mają być sprawdzane pod kątem nierówności.

### <a name="return-value"></a>Wartość zwracana

Valarray wartości logiczne, z których każdy jest:

- **wartość true,** Jeśli odpowiednie elementy nie są równe.

- **FALSE** Jeśli odpowiednie elementy są nierówne.

### <a name="remarks"></a>Uwagi

Pierwszy operator szablonu zwraca obiekt klasy [valarray\<bool >](../standard-library/valarray-bool-class.md), każdy z elementów, których `I` jest `left[I] != right[I]`.

Drugi operator szablonu są przechowywane w elemencie `I` `left[I] != right`.

Trzeci operator szablonu są przechowywane w elemencie `I` `left != right[I]`.

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
/* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the not equal comparison test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
*/
```

## <a name="op_mod"></a>  operator %

Uzyskuje resztę z dzielenia odpowiadające elementy dwóch valarrays równej wielkości lub podzielenie tablicę valarray przez określoną wartość lub dzielenia określonej wartości w tablicy valarray.

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

*left*<br/>
Wartość lub tablicy valarray, która służy jako dzielna na inną wartość, która lub tablicy valarray jest podzielona.

*right*<br/>
Wartość lub tablicy valarray, który służy jako dzielnik i który dzieli inną wartość lub tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są element-wise reszty z *po lewej stronie* podzielona przez *prawo*.

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
/* Output:
The initial Left valarray is: ( 53 -67 53 -67 53 -67 ).
The initial Right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
valarray: ( 0 -3 4 -7 1 -3 ).
*/
```

## <a name="op_amp"></a>  Operator&amp;

Uzyskuje bitowe **i** między odpowiadające elementy dwóch valarrays równej wielkości lub tablicę valarray i określoną wartość typu elementu.

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

*left*<br/>
Pierwsza z dwóch valarrays, w której odpowiednie elementy, które mają być łączone za pomocą operatora testu koniunkcji `AND` lub określoną wartość typu elementu, który ma być wyłączny sumy bitowej połączona z każdego elementu tablicy valarray.

*right*<br/>
Drugi dwóch valarrays, w której odpowiednie elementy, które mają być łączone za pomocą operatora testu koniunkcji `AND` lub określoną wartość typu elementu, który ma być wyłączny sumy bitowej połączona z każdego elementu tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są element-wise kombinacji operacja bitowa i z *po lewej stronie* i *prawo*.

### <a name="remarks"></a>Uwagi

Operacja bitowa należy używać tylko do manipulowania bitów **char** i **int** typów danych i wariantów a nie w systemie **float**, **double**, **longdouble**, **void**, **bool** lub innych, bardziej złożone typy danych.

Operatora testu koniunkcji `AND` ma tej samej tabeli prawdziwych danych jako logiczny `AND` , ale ma zastosowanie do typu danych na poziomie pojedynczych bitów. [Operator & &](#op_amp_amp) ma zastosowanie na poziomie elementu inwentaryzacji wszystkich wartości niezerowych jako PRAWDA, a wynik jest valarray wartościami logicznymi. Operatora testu koniunkcji `AND` [operator &](#op_amp), z kolei może doprowadzić do tablicy valarray, o wartości innej niż 0 lub 1, w zależności od wyniku operacji na poziomie bitowym.

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
/* Output:
The initial Left valarray is:  ( 0 2 0 4 0 6 0 8 0 10 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the bitwise operator & is the
valarray: ( 0 0 0 0 0 4 0 0 0 8 ).
*/
```

## <a name="op_amp_amp"></a>  Operator&amp;&amp;

Uzyskuje logicznej **i** między odpowiadające elementy dwóch valarrays równej wielkości lub tablicę valarray i określoną wartość typ elementu tablicy valarray.

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

*left*<br/>
Pierwsza z dwóch valarrays, którego odpowiednie elementy, które mają być łączone z logicznym `AND` lub określoną wartość typu elementu, który ma być połączona z każdego elementu tablicy valarray.

*right*<br/>
Drugi dwóch valarrays, którego odpowiednie elementy, które mają być łączone z logicznym `AND` lub określoną wartość typu elementu, który ma być połączona z każdego elementu tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są typu wartość logiczna i element-wise kombinacja logicznej `AND` operacji *po lewej stronie* i *prawo*.

### <a name="remarks"></a>Uwagi

Logiczny `ANDoperator&&` ma zastosowanie na poziomie elementu inwentaryzacji wszystkich wartości niezerowych jako PRAWDA, a wynik jest valarray wartościami logicznymi. Bitowe wersję `AND`, [operatora &,](#op_amp), z kolei może doprowadzić do tablicy valarray, o wartości innej niż 0 lub 1, w zależności od wyniku operacji na poziomie bitowym.

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
/* Output:
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&& is the
valarray: ( 0 0 0 1 0 1 0 1 0 1 ).
*/
```

## <a name="op_gt"></a>  Operator&gt;

Sprawdza, czy elementów tworzonej tablicy valarray jednego są większe niż elementów tworzonej tablicy valarray równej wielkości lub tego, czy wszystkie elementy tablicy valarray jest większa lub mniejsza niż określona wartość.

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

*left*<br/>
Pierwsza z dwóch valarrays, którego elementy mają być porównane lub określoną wartość ma zostać porównane z każdego elementu tablicy valarray.

*right*<br/>
Drugi dwóch valarrays, którego elementy mają być porównane lub określoną wartość do porównania z każdego elementu tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray wartości logiczne, z których każdy jest:

- **wartość true,** Jeśli *po lewej stronie* element lub wartość jest większa niż odpowiadające *prawo* element lub wartość.

- **FALSE** Jeśli *po lewej stronie* element lub wartość nie jest większa niż odpowiadające *prawo* element lub wartość.

### <a name="remarks"></a>Uwagi

Jeśli liczba elementów w dwóch valarrays nie jest taki sam, wynik jest niezdefiniowany.

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
/* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than comparison test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
*/
```

## <a name="op_gt_eq"></a>  Operator&gt;=

Sprawdza, czy elementów tworzonej tablicy valarray jednego są większe niż lub równa elementy równej wielkości tablicy valarray lub tego, czy wszystkie elementy tablicy valarray są większe niż lub równe lub mniejsze niż lub równa określonej wartości.

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

*left*<br/>
Pierwsza z dwóch valarrays, którego elementy mają być porównane lub określoną wartość ma zostać porównane z każdego elementu tablicy valarray.

*right*<br/>
Drugi dwóch valarrays, którego elementy mają być porównane lub określoną wartość do porównania z każdego elementu tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray wartości logiczne, z których każdy jest:

- **wartość true,** Jeśli *po lewej stronie* element lub wartość jest większa niż lub równa odpowiednich *prawo* element lub wartość.

- **FALSE** Jeśli *po lewej stronie* element lub wartość jest mniejsza niż odpowiadające *prawo* element lub wartość.

### <a name="remarks"></a>Uwagi

Jeśli liczba elementów w dwóch valarrays nie jest taki sam, wynik jest niezdefiniowany.

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
/* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than or equal test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
*/
```

## <a name="op_gt_gt"></a>  Operator&gt;&gt;

Po prawej stronie przesunięcia bitów dla każdego elementu tablicy valarray określoną liczbę pozycji i według określonej ilości element-wise określony przez drugi tablicy valarray.

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

*left*<br/>
Wartość jest przesuwany lub tablicy valarray, którego elementy mają zostać przesunięte.

*right*<br/>
Wartość wskazująca, wielkość przesunięcia bitowego w prawo lub wskazać element-wise ilość przesunięcia bitowego w prawo, której elementy w tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy mają prawo przesunięte według określonej ilości.

### <a name="remarks"></a>Uwagi

Oznaczone liczby ma znak zachowane.

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
/* Output:
The initial Left valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
*/
```

## <a name="op_lt"></a>  Operator&lt;

Sprawdza, czy elementów tworzonej tablicy valarray jednego są mniejsze niż elementów równej wielkości tablicy valarray lub tego, czy wszystkie elementy tablicy valarray jest większa lub mniejsza niż określona wartość.

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

*left*<br/>
Pierwsza z dwóch valarrays, którego elementy mają być porównane lub określoną wartość ma zostać porównane z każdego elementu tablicy valarray.

*right*<br/>
Drugi dwóch valarrays, którego elementy mają być porównane lub określoną wartość do porównania z każdego elementu tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray wartości logiczne, z których każdy jest:

- **wartość true,** Jeśli *po lewej stronie* element lub wartość jest mniejsza niż odpowiadające *prawo* element lub wartość.

- **FALSE** Jeśli *po lewej stronie* element lub wartość nie jest mniejsza niż odpowiadające *prawo* element lub wartość.

### <a name="remarks"></a>Uwagi

Jeśli liczba valarrays dwóch elementów nie jest taki sam, wynik jest niezdefiniowany.

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
/* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the less-than comparson test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
*/
```

## <a name="op_lt_eq"></a>  Operator&lt;=

Sprawdza, czy elementów tworzonej tablicy valarray jednego są mniejsze niż lub równe elementów tworzonej tablicy valarray równej wielkości, czy wszystkie elementy tablicy valarray są większe niż lub równe lub mniejsze niż lub równa określonej wartości.

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

*left*<br/>
Pierwsza z dwóch valarrays, którego elementy mają być porównane lub określoną wartość ma zostać porównane z każdego elementu tablicy valarray.

*right*<br/>
Drugi dwóch valarrays, którego elementy mają być porównane lub określoną wartość do porównania z każdego elementu tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray wartości logiczne, z których każdy jest:

- **wartość true,** Jeśli *po lewej stronie* element lub wartość jest mniejsza niż lub równe do odpowiednich *prawo* element lub wartość.

- **FALSE** Jeśli *po lewej stronie* element lub wartość jest większa niż odpowiadające *prawo* element lub wartość.

### <a name="remarks"></a>Uwagi

Jeśli liczba valarrays dwóch elementów nie jest taki sam, wynik jest niezdefiniowany.

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
/* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the less than or equal test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
*/
```

## <a name="op_lt_lt"></a>  Operator&lt;&lt;

Po lewej stronie wykonuje przesunięcie bitów dla każdego elementu tablicy valarray określoną liczbę pozycji i według określonej ilości element-wise określony przez drugi tablicy valarray.

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

*left*<br/>
Wartość jest przesuwany lub tablicy valarray, którego elementy mają zostać przesunięte.

*right*<br/>
Wartość wskazująca, wielkość przesunięcia w lewo lub wskazać element-wise ilość przesunięcia w lewo, której elementy w tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy zostały przesunięte określonego po lewej stronie.

### <a name="remarks"></a>Uwagi

Oznaczone liczby ma znak zachowane.

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
/* Output:
The initial Left valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift is the
valarray: ( 1 -2 4 -8 16 -32 64 -128 ).
*/
```

## <a name="op_star"></a>  operator *

Uzyskuje mnożenia między odpowiadające elementy dwóch valarrays równej wielkości lub z między określoną wartość w tablicy valarray.

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

*left*<br/>
Pierwsze dwa valarrays, którego elementy mają zostać pomnożona lub określoną wartość pomnożenie z każdego elementu tablicy valarray.

*right*<br/>
Drugi dwóch valarrays, którego elementy mają zostać pomnożona lub określoną wartość pomnożenie z każdego elementu tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są mnożenia z *po lewej stronie* i *prawo*.

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
/* Output:
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
*/
```

## <a name="op_add"></a>  operator +

Uzyskuje element-wise Suma między odpowiadające elementy dwóch valarrays równej wielkości lub z między określoną wartość w tablicy valarray.

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

*left*<br/>
Pierwszego dnia dwóch valarrays, której elementy mają być dodawane lub określoną wartość do dodania z każdego elementu tablicy valarray.

*right*<br/>
Drugi dwóch valarrays, której elementy mają być dodawane lub określoną wartość do dodania z każdego elementu tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są element-wise sum z *po lewej stronie* i *prawo*.

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
/* Output:
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
valarray: ( 2 0 4 2 6 4 8 6 ).
*/
```

## <a name="operator-"></a>  operator-

Uzyskuje element-wise różnica między odpowiadające elementy dwóch valarrays równej wielkości lub z między określoną wartość w tablicy valarray.

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

*left*<br/>
Wartość lub tablicy valarray, która służy jako odjemna, z której można odejmować w stanowiące różnicę mają inne wartości lub valarrays.

*right*<br/>
Wartość lub tablicy valarray, służąca jako odjemnik do odjęcia od innych wartości lub valarrays w stanowiące różnicę.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są element-wise różnica z *po lewej stronie* i *prawo*.

### <a name="remarks"></a>Uwagi

Terminologia arytmetyczne, używana do opisywania odejmowania:

Różnica = odjemna - odjemnik

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
/* Output:
The initial Left valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
*/
```

## <a name="op_div"></a>  operator /

Uzyskuje element-wise iloraz między odpowiadające elementy dwóch valarrays równej wielkości lub z między określoną wartość w tablicy valarray.

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

*left*<br/>
Wartość lub tablicy valarray, która służy jako dzielna na inną wartość, która lub tablicy valarray jest podzielona w tworzeniu ilorazu.

*right*<br/>
Wartość lub tablicy valarray, który służy jako dzielnik i który dzieli inną wartość lub tablicy valarray w tworzeniu ilorazu.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są element-wise iloraz z *po lewej stronie* podzielona przez *prawo*.

### <a name="remarks"></a>Uwagi

Terminologia arytmetyczne, używana do opisywania dzielenia:

iloraz = dzielnik / dzielnik.

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
/* Output:
The initial Left valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
valarray: ( inf -50 25 -16.6667 12.5 -10 ).
*/
```

## <a name="op_eq_eq"></a>  operator ==

Testy, czy odpowiadające elementy dwóch valarrays równej wielkości są równe, lub czy są wszystkie elementy tablicy valarray równa określonej wartości.

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

*left*<br/>
Pierwsza z dwóch valarrays, którego elementy mają być sprawdzane pod kątem równości.

*right*<br/>
Drugi dwóch valarrays, którego elementy mają być sprawdzane pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

Valarray wartości logiczne, z których każdy jest:

- **wartość true,** odpowiednie elementy są równe.

- **FALSE** odpowiednie elementy nie są równe.

### <a name="remarks"></a>Uwagi

Pierwszy operator szablonu zwraca obiekt klasy [valarray\<bool >](../standard-library/valarray-bool-class.md), każdy z elementów, których `I` jest `left[I] == right[I]`. Drugi operator szablonu są przechowywane w elemencie `I` `left[I] == right`. Trzeci operator szablonu są przechowywane w elemencie `I` `left == right[I]`.

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
/* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the equality comparison test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
*/
```

## <a name="op_xor"></a>  operator ^

Uzyskuje wyłączny sumy bitowej `OR` ( **XOR**) między odpowiadające elementy dwóch valarrays równej wielkości lub tablicę valarray i określoną wartość typu elementu.

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

*left*<br/>
Pierwsza z dwóch valarrays, w której odpowiednie elementy, które mają być łączone za pomocą operatora testu koniunkcji **XOR** lub określoną wartość typu elementu, który ma być wyłączny sumy bitowej połączona z każdego elementu tablicy valarray.

*right*<br/>
Drugi dwóch valarrays, w której odpowiednie elementy, które mają być łączone za pomocą operatora testu koniunkcji **XOR** lub określoną wartość typu elementu, który ma być wyłączny sumy bitowej połączona z każdego elementu tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są element-wise kombinacji operatora testu koniunkcji **XOR** operacji *po lewej stronie* i *prawo*.

### <a name="remarks"></a>Uwagi

Operacja bitowa należy używać tylko do manipulowania bitów **char** i **int** typów danych i wariantów a nie w systemie **float**, **double**, **typu long double**, **void**, **bool** lub innych, bardziej złożone typy danych.

Wyłączny sumy bitowej `OR` ( **XOR**) charakteryzuje się następującą semantyką: Biorąc pod uwagę bitów *b*1 i *b*2, *b*1 **XOR** *b*2 jest **true** Jeśli dokładnie jeden z bitów jest PRAWDA. **false** Jeśli oba bity są fałszywe lub jeśli spełnione są oba bity.

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
/* Output:
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^ is the
valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
*/
```

## <a name="op_or"></a>  operator&#124;

Uzyskuje bitowe `OR` między odpowiadające elementy dwóch valarrays równej wielkości lub tablicę valarray i określoną wartość typu elementu.

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

*left*<br/>
Pierwsza z dwóch valarrays, w której odpowiednie elementy, które mają być łączone za pomocą operatora testu koniunkcji `OR` lub określoną wartość typu elementu, który ma być wyłączny sumy bitowej połączona z każdego elementu tablicy valarray.

*right*<br/>
Drugi dwóch valarrays, w której odpowiednie elementy, które mają być łączone za pomocą operatora testu koniunkcji `OR` lub określoną wartość typu elementu, który ma być wyłączny sumy bitowej połączona z każdego elementu tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są element-wise kombinacji operatora testu koniunkcji `OR` operacji *po lewej stronie* i *prawo*.

### <a name="remarks"></a>Uwagi

Operacja bitowa należy używać tylko do manipulowania bitów **char** i **int** typów danych i wariantów a nie w systemie **float**, **double**, **longdouble**, **void**, **bool** lub innych, bardziej złożone typy danych.

Bitowe OR ma tej samej tabeli prawdziwych danych jako logiczny `OR`, ale ma zastosowanie do typu danych na poziomie pojedynczych bitów. Biorąc pod uwagę bitów *b*1 i *b*2, *b*1 `OR` *b*2 jest **true** Jeśli co najmniej jeden z bitów jest wartość TRUE lub **false** Jeśli oba bity mają wartość false. Logiczny `OR` [operator&#124; &#124; ](../standard-library/valarray-operators.md#op_lor) ma zastosowanie na poziomie elementu wszystkich wartości niezerowych co inwentaryzacji **true**, a wynik jest valarray wartościami logicznymi. Bitowe OR `operator|`, z kolei może doprowadzić do tablicy valarray, o wartości innej niż 0 lub 1, w zależności od wyniku operacji na poziomie bitowym.

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
/* Output:
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise OR operator| is the
valarray: ( 1 0 1 3 3 4 7 6 7 9 ).
*/
```

## <a name="op_lor"></a>  operator&#124;&#124;

Uzyskuje logicznej `OR` między odpowiadające elementy dwóch valarrays równej wielkości lub tablicę valarray i określoną wartość typu elementu tablicy valarray.

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

*left*<br/>
Pierwsza z dwóch valarrays, którego odpowiednie elementy, które mają być łączone z logicznym `OR` lub określoną wartość typu elementu, który ma być połączona z każdego elementu tablicy valarray.

*right*<br/>
Drugi dwóch valarrays, którego odpowiednie elementy, które mają być łączone z logicznym `OR` lub określoną wartość typu elementu, który ma być połączona z każdego elementu tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są typu **bool** i element-wise kombinacji operacje logiczne OR *po lewej stronie* i *prawo*.

### <a name="remarks"></a>Uwagi

Logiczny `OR` `operator||` ma zastosowanie na poziomie elementu wszystkich wartości niezerowych co inwentaryzacji **true**, a wynik jest valarray wartościami logicznymi. Bitowe wersję `OR`, [operator&#124; ](../standard-library/valarray-operators.md#op_or) z kolei może doprowadzić do tablicy valarray, o wartości innej niż 0 lub 1, w zależności od wyniku operacji na poziomie bitowym.

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
/* Output:
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 0 0 3 0 0 6 0 0 9 ).
The element-by-element result of the logical OR operator|| is the
valarray: ( 0 0 0 1 0 1 1 1 0 1 ).
*/
```

## <a name="see-also"></a>Zobacz także

[\<valarray>](../standard-library/valarray.md)<br/>
