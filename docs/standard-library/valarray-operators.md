---
title: "&lt;valarray —&gt; operatory | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
ms.assetid: 8a53562c-90ab-4eb3-85d3-ada5259d90b0
caps.latest.revision: "8"
manager: ghogen
helpviewer_keywords:
- std::operator!= (valarray), std::operator&amp; (valarray)
- std::operator&amp;&amp; (valarray)
- std::operator&gt; (valarray)
- std::operator&gt;&gt; (valarray)
- std::operator&gt;= (valarray)
- std::operator&lt; (valarray)
- std::operator&lt;&lt; (valarray)
- std::operator&lt;= (valarray), std::operator== (valarray)
ms.openlocfilehash: b422f33addb61eed4ce04eeef74a76a597f799ee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltvalarraygt-operators"></a>&lt;valarray —&gt; operatory
||||  
|-|-|-|  
|[operator! =](#op_neq)|[% — operator](#op_mod)|[operator&amp;](#op_amp)|  
|[operator&amp;&amp;](#op_amp_amp)|[operator&gt;](#op_gt)|[operator&gt;&gt;](#op_gt_gt)|  
|[operator&gt;=](#op_gt_eq)|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|  
|[operator&lt;=](#op_lt_eq)|[operator *](#op_star)|[operator +](#op_add)|  
|[operator-](#operator-)|[operator /](#op_div)|[operator ==](#op_eq_eq)|  
|[operator ^](#op_xor)|[— operator|](#op_or)|[— operator||](#op_lor)|  
  
##  <a name="op_neq"></a>operator! =  
 Sprawdza, czy są odpowiednie elementy dwóch valarrays równej wielkości nierównej lub czy są równe wszystkie elementy valarray — określona wartość.  
  
```  
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
 `left`  
 Pierwszy z dwóch valarrays, których elementy mają być sprawdzane pod kątem nierówności.  
  
 `right`  
 Drugi dwóch valarrays, których elementy mają być sprawdzane pod kątem nierówności.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray — wartości logicznych, z których każdy jest:  
  
- **wartość true,** Jeśli odpowiednie elementy nie są równe.  
  
- **FALSE** Jeśli odpowiednie elementy nie są równe.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy operator szablonu zwraca obiekt klasy [valarray —\<bool >](../standard-library/valarray-bool-class.md), każdy z elementów, których `I` jest `left[I] != right[I]`.  
  
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
        << "the not equal comparison test is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The element-by-element result of the not equal comparison test is the  
 valarray: ( 0 0 1 0 1 0 1 0 1 0 ).  
*\  
```  
  
##  <a name="op_mod"></a>% — operator  
 Uzyskuje resztę z dzielenia odpowiednie elementy dwóch valarrays równej wielkości lub podzielenie valarray — przez określoną wartość lub podziału przez valarray — określona wartość.  
  
```  
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
 `left`  
 Wartość lub valarray —, która służy jako dzielna, w którym inną wartość lub valarray — jest podzielona.  
  
 `right`  
 Wartość lub valarray —, który służy jako dzielnik i który dzieli inną wartość lub valarray —.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray —, której elementy są element-wise reszty z `left` rozdzielonych `right`.  
  
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
        << "division is the\n valarray: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaREM [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 53 -67 53 -67 53 -67 ).  
The initial Right valarray is: ( 1 4 7 10 13 16 ).  
The remainders from the element-by-element division is the  
 valarray: ( 0 -3 4 -7 1 -3 ).  
*\  
```  
  
##  <a name="op_amp"></a>operator&amp;  
 Uzyskuje operatora testu koniunkcji **i** między odpowiednie elementy dwóch valarrays równej wielkości lub valarray — i określoną wartość typu elementu.  
  
```  
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
 `left`  
 Pierwszy z dwóch valarrays, której elementy odpowiednich mają być łączone z bitowego **i** lub określoną wartość typu elementu, aby można było połączyć alternatywy bitowej z każdym elementem valarray —.  
  
 `right`  
 Drugi dwóch valarrays, której elementy odpowiednich mają być łączone z bitowego **i** lub określoną wartość typu elementu, aby można było połączyć alternatywy bitowej z każdym elementem valarray —.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray —, której elementy są element-wise kombinacją operacji i z `left` i `right`.  
  
### <a name="remarks"></a>Uwagi  
 Operacji można używać tylko do manipulowania bitów w `char` i `int` typy danych i wariantów, a nie na **float**, **podwójne**, **longdouble**, `void`, `bool` lub inne, bardziej złożone typy danych.  
  
 Bitowe **i** ma tej samej tabeli prawdy jako logiczny **i** , ale odnoszące się do typu danych na poziomie poszczególnych bitów. [— Operator & &](../standard-library/valarray-operators.md#amp) stosowana na poziomie elementu inwentaryzacji wszystkich niezerowe wartości jako true, a wynik jest valarray — wartości logicznych. Bitowe **ANDoperator &**, z kolei może spowodować valarray — wartości innych niż 0 lub 1, w zależności od wyniku operacji.  
  
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
        << "the bitwise operator & is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaBWA [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is:  ( 0 2 0 4 0 6 0 8 0 10 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The element-by-element result of the bitwise operator & is the  
 valarray: ( 0 0 0 0 0 4 0 0 0 8 ).  
*\  
```  
  
##  <a name="op_amp_amp"></a>operator&amp;&amp;  
 Uzyskuje logicznym **i** między odpowiednie elementy dwóch valarrays równej wielkości lub valarray — i określoną wartość valarray — typ elementu.  
  
```  
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
 `left`  
 Pierwszy z dwóch valarrays, której odpowiednie elementy mają być łączone z logicznym **i** lub określoną wartość typu elementu, aby można było połączyć z każdym elementem valarray —.  
  
 `right`  
 Drugi dwóch valarrays, której odpowiednie elementy mają być łączone z logicznym **i** lub określoną wartość typu elementu, aby można było połączyć z każdym elementem valarray —.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray —, której elementy są typu bool i element-wise kombinacja logicznym **i** działania `left` i `right`.  
  
### <a name="remarks"></a>Uwagi  
 Logiczny **ANDoperator & &** stosowana na poziomie elementu inwentaryzacji wszystkich niezerowe wartości jako true, a wynik jest valarray — wartości logicznych. Wersja bitowe **i**, [operatora &,](../standard-library/valarray-operators.md#op_amp), z kolei może spowodować valarray — wartości innych niż 0 lub 1, w zależności od wyniku operacji.  
  
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
        << "the logical AND operator&& is the\n valarray: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaLAA [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The element-by-element result of the logical AND operator&& is the  
 valarray: ( 0 0 0 1 0 1 0 1 0 1 ).  
*\  
```  
  
##  <a name="op_gt"></a>operator&gt;  
 Sprawdza, czy elementy jeden valarray — są większe niż elementów równej wielkości valarray — lub czy wszystkie elementy valarray — większa lub mniejsza niż określona wartość.  
  
```  
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
 `left`  
 Pierwszy z dwóch valarrays, których elementy mają zostać porównane lub określoną wartość ma zostać porównane z każdym elementem valarray —.  
  
 `right`  
 Drugi dwóch valarrays, których elementy mają zostać porównane lub określoną wartość do porównania z każdym elementem valarray —.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray — wartości logicznych, z których każdy jest:  
  
- **wartość true,** Jeśli `left` element lub wartość jest większa niż odpowiadający mu `right` element lub wartość.  
  
- **FALSE** Jeśli `left` nie jest większa niż odpowiadający mu element lub wartość `right` element lub wartość.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli liczba elementów w dwóch valarrays nie jest taki sam, wynikiem jest niezdefiniowany.  
  
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
        << "the greater than comparison test is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).  
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).  
The element-by-element result of the greater than comparison test is the  
 valarray: ( 1 1 0 1 0 1 0 1 0 1 ).  
*\  
```  
  
##  <a name="op_gt_eq"></a>operator&gt;=  
 Sprawdza, czy elementy jeden valarray — są większe niż lub równe elementów równej wielkości valarray — lub czy wszystkie elementy valarray — są większe niż lub równe lub mniejsze niż lub równa określonej wartości.  
  
```  
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
 `left`  
 Pierwszy z dwóch valarrays, których elementy mają zostać porównane lub określoną wartość ma zostać porównane z każdym elementem valarray —.  
  
 `right`  
 Drugi dwóch valarrays, których elementy mają zostać porównane lub określoną wartość do porównania z każdym elementem valarray —.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray — wartości logicznych, z których każdy jest:  
  
- **wartość true,** Jeśli `left` element lub wartość jest większa niż lub równa odpowiadającego `right` element lub wartość.  
  
- **FALSE** Jeśli `left` element lub wartość jest mniejsza niż odpowiadający mu `right` element lub wartość.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli liczba elementów w dwóch valarrays nie jest taki sam, wynikiem jest niezdefiniowany.  
  
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
        << "the greater than or equal test is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).  
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).  
The element-by-element result of the greater than or equal test is the  
 valarray: ( 1 1 0 1 0 1 0 1 0 1 ).  
*\  
```  
  
##  <a name="op_gt_gt"></a>operator&gt;&gt;  
 Prawo zmian usługi bits dla każdego elementu valarray — określonej liczby miejsc lub element-wise wartość określoną w drugim valarray —.  
  
```  
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
 `left`  
 Wartość lekkie lub valarray —, której elementy mają zostać przesunięte.  
  
 `right`  
 Wartość wskazująca przesunięcia w prawo lub valarray —, której elementy wskazują element-wise wielkość przesunięcia w prawo.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray —, której elementy ma prawo przesunięte o określonej szerokości.  
  
### <a name="remarks"></a>Uwagi  
 Numery podpisem mają swoje znaki zachowane.  
  
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
        << "the right shift is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the right shift is the  
 valarray: ( 64 -32 16 -8 4 -2 1 -1 ).  
*\  
```  
  
##  <a name="op_lt"></a>operator&lt;  
 Sprawdza, czy elementy valarray — co jest mniejsza od elementów równej wielkości valarray — lub czy wszystkie elementy valarray — większa lub mniejsza niż określona wartość.  
  
```  
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
 `left`  
 Pierwszy z dwóch valarrays, których elementy mają zostać porównane lub określoną wartość ma zostać porównane z każdym elementem valarray —.  
  
 `right`  
 Drugi dwóch valarrays, których elementy mają zostać porównane lub określoną wartość do porównania z każdym elementem valarray —.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray — wartości logicznych, z których każdy jest:  
  
- **wartość true,** Jeśli `left` element lub wartość jest mniejsza niż odpowiadający mu `right` element lub wartość.  
  
- **FALSE** Jeśli `left` element lub wartość nie jest mniejsza niż odpowiadający mu `right` element lub wartość.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli liczba valarrays dwóch elementów nie jest taki sam, wynikiem jest niezdefiniowany.  
  
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
        << "the less-than comparson test is the\n valarray: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The element-by-element result of the less-than comparson test is the  
 valarray: ( 0 0 1 0 1 0 1 0 1 0 ).  
*\  
```  
  
##  <a name="op_lt_eq"></a>operator&lt;=  
 Sprawdza, czy elementy jeden valarray — są mniejsze niż lub równe elementów równej wielkości valarray — lub czy wszystkie elementy valarray — są większe niż lub równe lub mniejsze niż lub równa określonej wartości.  
  
```  
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
 `left`  
 Pierwszy z dwóch valarrays, których elementy mają zostać porównane lub określoną wartość ma zostać porównane z każdym elementem valarray —.  
  
 `right`  
 Drugi dwóch valarrays, których elementy mają zostać porównane lub określoną wartość do porównania z każdym elementem valarray —.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray — wartości logicznych, z których każdy jest:  
  
- **wartość true,** Jeśli `left` element lub wartość jest mniejsza niż lub równa odpowiadającego `right` element lub wartość.  
  
- **FALSE** Jeśli `left` element lub wartość jest większa niż odpowiadający mu `right` element lub wartość.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli liczba valarrays dwóch elementów nie jest taki sam, wynikiem jest niezdefiniowany.  
  
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
        << "the less than or equal test is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).  
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).  
The element-by-element result of the less than or equal test is the  
 valarray: ( 0 0 1 0 1 0 1 0 1 0 ).  
*\  
```  
  
##  <a name="op_lt_lt"></a>operator&lt;&lt;  
 Po lewej wykonuje przesunięcie bitów dla każdego elementu valarray — określonej liczby miejsc lub element-wise wartość określoną w drugim valarray —.  
  
```  
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
 `left`  
 Wartość lekkie lub valarray —, której elementy mają zostać przesunięte.  
  
 `right`  
 Wartość wskazująca przesunięcia w lewo lub valarray —, której elementy wskazują element-wise wielkość przesunięcia w lewo.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray — elementy, których ma zostać przesunięty w określonym.  
  
### <a name="remarks"></a>Uwagi  
 Numery podpisem mają swoje znaki zachowane.  
  
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
        << "the left shift is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the left shift is the  
 valarray: ( 1 -2 4 -8 16 -32 64 -128 ).  
*\  
```  
  
##  <a name="op_star"></a>operator *  
 Uzyskuje element-wise produktu między elementami odpowiedniego dwóch valarrays równej wielkości typu lub między valarray — określona wartość.  
  
```  
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
 `left`  
 Pierwszy z dwóch valarrays, których elementy mają zostać pomnożona lub określoną wartość mnoży się z każdym elementem valarray —.  
  
 `right`  
 Drugi dwóch valarrays, których elementy mają zostać pomnożona lub określoną wartość mnożona z każdym elementem valarray —.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray —, której elementy są element-wise produktu z `left` i `right`.  
  
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
        << "the multiplication is the\n valarray: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the multiplication is the  
 valarray: ( 0 -1 4 -3 8 -5 12 -7 ).  
*\  
```  
  
##  <a name="op_add"></a>operator +  
 Uzyskuje element-wise Suma między elementami odpowiedniego dwóch valarrays równej wielkości typu lub między valarray — określona wartość.  
  
```  
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
 `left`  
 Pierwszy z dwóch valarrays, których elementy mają być dodawane lub określoną wartość ma zostać dodana z każdym elementem valarray —.  
  
 `right`  
 Drugi dwóch valarrays, których elementy mają być dodawane lub określoną wartość do dodania z każdym elementem valarray —.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray —, której elementy są element-wise Suma z `left` i `right`.  
  
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
        << "the sum is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the sum is the  
 valarray: ( 2 0 4 2 6 4 8 6 ).  
*\  
```  
  
##  <a name="operator-"></a>operator-  
 Uzyskuje element-wise różnica między odpowiednie elementy tego dwa valarrays równej wielkości lub między valarray — określona wartość.  
  
```  
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
 `left`  
 Wartość lub valarray —, która służy jako minuend, z której można odejmować w stanowiące różnicę mają inne wartości lub valarrays.  
  
 `right`  
 Wartość lub valarray —, która służy jako subtrahend, który odjęta od innych wartości lub valarrays w stanowiące różnicę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray —, której elementy są element-wise różnica z `left` i `right`.  
  
### <a name="remarks"></a>Uwagi  
 Arytmetyczny terminologii przy odejmowanie:  
  
 Różnica = minuend - subtrahend  
  
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
        << "the difference is the\n valarray: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 10 0 10 0 10 0 10 0 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the difference is the  
 valarray: ( 10 -1 8 -3 6 -5 4 -7 ).  
*\  
```  
  
##  <a name="op_div"></a>operator /  
 Uzyskuje element-wise iloraz między elementami odpowiedniego dwóch valarrays równej wielkości typu lub między valarray — określona wartość.  
  
```  
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
 `left`  
 Wartość lub valarray —, która służy jako dzielna, w którym inną wartość lub valarray — jest podzielona w tworzeniu iloraz.  
  
 `right`  
 Wartość lub valarray —, który służy jako dzielnik i który dzieli innej wartości lub valarray — w tworzeniu iloraz.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray —, której elementy są element-wise iloraz z `left` rozdzielonych `right`.  
  
### <a name="remarks"></a>Uwagi  
 Arytmetyczny terminologii przy podziale:  
  
 iloraz = dzielna / dzielnik.  
  
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
        << "the quotient is the\n valarray: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 100 -100 100 -100 100 -100 ).  
The initial Right valarray is: ( 0 2 4 6 8 10 ).  
The element-by-element result of the quotient is the  
 valarray: ( 1.#INF -50 25 -16.6667 12.5 -10 ).  
*\  
```  
  
##  <a name="op_eq_eq"></a>operator ==  
 Testy, czy są odpowiednie elementy dwóch valarrays równej wielkości większy lub czy są wszystkie elementy valarray — równa określonej wartości.  
  
```  
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
 `left`  
 Pierwszy z dwóch valarrays, których elementy mają być sprawdzane pod kątem równości.  
  
 `right`  
 Drugi dwóch valarrays, których elementy mają być sprawdzane pod kątem równości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray — wartości logicznych, z których każdy jest:  
  
- **wartość true,** odpowiednie elementy są równe.  
  
- **FALSE** odpowiednie elementy nie są równe.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy operator szablonu zwraca obiekt klasy [valarray —\<bool >](../standard-library/valarray-bool-class.md), każdy z elementów, których `I` jest `left[I] == right[I]`. Drugi operator szablonu są przechowywane w elemencie `I` `left[I] == right`. Trzeci operator szablonu są przechowywane w elemencie `I` `left == right[I]`.  
  
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
        << "the equality comparison test is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The element-by-element result of the equality comparison test is the  
 valarray: ( 1 1 0 1 0 1 0 1 0 1 ).  
*\  
```  
  
##  <a name="op_xor"></a>operator ^  
 Uzyskuje operator wyłączny `OR` ( **XOR**) między odpowiednie elementy dwóch valarrays równej wielkości lub valarray — i określoną wartość typu elementu.  
  
```  
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
 `left`  
 Pierwszy z dwóch valarrays, której elementy odpowiednich mają być łączone z bitowego **XOR** lub określoną wartość typu elementu, aby można było połączyć alternatywy bitowej z każdym elementem valarray —.  
  
 `right`  
 Drugi dwóch valarrays, której elementy odpowiednich mają być łączone z bitowego **XOR** lub określoną wartość typu elementu, aby można było połączyć alternatywy bitowej z każdym elementem valarray —.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray —, której elementy są element-wise kombinację operatora testu koniunkcji **XOR** działania `left` i `right`.  
  
### <a name="remarks"></a>Uwagi  
 Operacji można używać tylko do manipulowania bitów w `char` i `int` typy danych i wariantów, a nie na **float**, **podwójne**, `long double`, `void`, `bool` lub inne, bardziej złożone typy danych.  
  
 Operator wyłączny `OR` ( **XOR**) ma następujące semantykę: podane bitów *b*1 i *b*2, *b*1  **XOR** *b*2 jest **true** Jeśli dokładnie jeden z bitów jest PRAWDA. **false** Jeśli oba bity są false lub jeśli spełnione są oba bity.  
  
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
        << "the bitwise XOR operator^ is the\n valarray: ( ";  
           for ( i = 0 ; i < 10 ; i++ )  
         cout << vaLAA [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).  
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).  
The element-by-element result of the bitwise XOR operator^ is the  
 valarray: ( 1 0 0 3 2 4 7 6 6 9 ).  
*\  
```  
  
##  <a name="op_or"></a>Operator &#124;  
 Uzyskuje operatora testu koniunkcji `OR` między odpowiednie elementy dwóch valarrays równej wielkości lub valarray — i określoną wartość typu elementu.  
  
```  
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
 `left`  
 Pierwszy z dwóch valarrays, której elementy odpowiednich mają być łączone z bitowego `OR` lub określoną wartość typu elementu, aby można było połączyć alternatywy bitowej z każdym elementem valarray —.  
  
 `right`  
 Drugi dwóch valarrays, której elementy odpowiednich mają być łączone z bitowego `OR` lub określoną wartość typu elementu, aby można było połączyć alternatywy bitowej z każdym elementem valarray —.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray —, której elementy są element-wise kombinację operatora testu koniunkcji `OR` działania `left` i `right`.  
  
### <a name="remarks"></a>Uwagi  
 Operacji można używać tylko do manipulowania bitów w `char` i `int` typy danych i wariantów, a nie na **float**, **podwójne**, **longdouble**, `void`, `bool` lub inne, bardziej złożone typy danych.  
  
 Bitowe lub ma tej samej tabeli prawdy jako logiczny `OR`, ale odnoszące się do typu danych na poziomie poszczególnych bitów. Podane bitów *b*1 i *b*2, *b*1 `OR` *b*2 jest **true** Jeśli co najmniej jeden z usługi bits wartość TRUE lub **false** Jeśli oba bity są wartość false. Logicznym `OR` [operatora &#124; &#124;](../standard-library/valarray-operators.md#op_lor) stosowana na poziomie elementu, inwentaryzacji wszystkich niezerowe wartości jako **true**, a wynik jest valarray — wartości logicznych. Bitowe lub `operator|`, z kolei może spowodować valarray — wartości innych niż 0 lub 1, w zależności od wyniku operacji.  
  
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
        << "the bitwise OR operator| is the\n valarray: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaLAA [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).  
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).  
The element-by-element result of the bitwise OR operator| is the  
 valarray: ( 1 0 1 3 3 4 7 6 7 9 ).  
*\  
```  
  
##  <a name="op_lor"></a>Operator &#124; &#124;  
 Uzyskuje logicznym `OR` między odpowiednie elementy dwóch valarrays równej wielkości lub valarray — i określoną wartość valarray — typ elementu.  
  
```  
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
 `left`  
 Pierwszy z dwóch valarrays, której odpowiednie elementy mają być łączone z logicznym `OR` lub określoną wartość typu elementu, aby można było połączyć z każdym elementem valarray —.  
  
 `right`  
 Drugi dwóch valarrays, której odpowiednie elementy mają być łączone z logicznym `OR` lub określoną wartość typu elementu, aby można było połączyć z każdym elementem valarray —.  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray —, której elementy są typu `bool` i element-wise kombinacja operacje logiczne OR `left` i `right`.  
  
### <a name="remarks"></a>Uwagi  
 Logiczny `OR` `operator||` stosowana na poziomie elementu, inwentaryzacji wszystkich niezerowe wartości jako **true**, a wynik jest valarray — wartości logicznych. Wersja bitowe `OR`, [operatora &#124;](../standard-library/valarray-operators.md#op_or) z kolei może spowodować valarray — wartości innych niż 0 lub 1, w zależności od wyniku operacji.  
  
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
        << "the logical OR operator|| is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaLOR [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).  
The initial Right valarray is: ( 0 0 0 3 0 0 6 0 0 9 ).  
The element-by-element result of the logical OR operator|| is the  
 valarray: ( 0 0 0 1 0 1 1 1 0 1 ).  
*\  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<valarray — >](../standard-library/valarray.md)

