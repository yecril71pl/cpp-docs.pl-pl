---
title: valarray — Klasa
ms.date: 03/27/2019
f1_keywords:
- valarray/std::valarray
- valarray/std::valarray::value_type
- valarray/std::valarray::apply
- valarray/std::valarray::cshift
- valarray/std::valarray::free
- valarray/std::valarray::max
- valarray/std::valarray::min
- valarray/std::valarray::resize
- valarray/std::valarray::shift
- valarray/std::valarray::size
- valarray/std::valarray::sum
- valarray/std::valarray::swap
helpviewer_keywords:
- std::valarray [C++]
- std::valarray [C++], value_type
- std::valarray [C++], apply
- std::valarray [C++], cshift
- std::valarray [C++], free
- std::valarray [C++], max
- std::valarray [C++], min
- std::valarray [C++], resize
- std::valarray [C++], shift
- std::valarray [C++], size
- std::valarray [C++], sum
- std::valarray [C++], swap
ms.assetid: 19b862f9-5d09-4003-8844-6ddd02c1a3a7
ms.openlocfilehash: f116758591461614acfa7c171bff2b1675f453e4
ms.sourcegitcommit: 49cf365176557456f56c994e06ea1a38f73e938b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937421"
---
# <a name="valarray-class"></a>valarray — Klasa

Szablon klasy opisuje obiekt, który kontroluje sekwencję elementów typu `Type`, które są przechowywane jako tablica, zaprojektowane do wykonywania operacji matematycznych o dużej szybkości i zoptymalizowane pod kątem wydajności obliczeniowej.

## <a name="remarks"></a>Uwagi

Klasa jest reprezentacją koncepcji matematycznej uporządkowanego zestawu wartości, a elementy są numerowane sekwencyjnie od zera. Klasa jest opisana jako blisko kontenera, ponieważ obsługuje niektóre, ale nie wszystkie możliwości, które są dostępne dla kontenerów sekwencji pierwszej klasy, takich jak [Vector](../standard-library/vector-class.md), support. Różni się od wektora szablonu klasy na dwa ważne sposoby:

- Definiuje wiele operacji arytmetycznych między odpowiednimi elementami `valarray<Type>` obiektów tego samego typu i długości, takich jak *xarr* = cos ( *YARR*) + Sin ( *zarr*).

- Definiuje on różne interesujące metody tworzenia indeksu `valarray<Type>` obiektu przez przeciążanie [operatora&#91;](#op_at).

Obiekt klasy `Type`:

- Ma publiczny Konstruktor domyślny, destruktor, Konstruktor kopiujący i operator przypisania, z zachowaniem konwencjonalnym.

- Definiuje operatory arytmetyczne i funkcje matematyczne w razie potrzeby, które są zdefiniowane dla typów zmiennoprzecinkowych z zachowaniem konwencjonalnym.

W szczególności nie mogą istnieć żadne delikatne różnice między konstrukcją kopiowania i domyślną konstrukcją, po którym następuje przypisanie. Żadna z operacji na obiektach klasy `Type` może generować wyjątki.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorzy

|||
|-|-|
|[valarray](#valarray)|Konstruuje `valarray` o określonym rozmiarze lub z elementami określonej wartości lub jako kopię innego `valarray` lub podzbioru innych `valarray`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[value_type](#value_type)|Typ, który reprezentuje typ elementu przechowywanego w `valarray`.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[stosowa](#apply)|Stosuje określoną funkcję do każdego elementu `valarray`.|
|[cshift](#cshift)|Cyklicznie przesuwa wszystkie elementy w `valarray` o określoną liczbę pozycji.|
|[free](#free)|Zwalnia pamięć używaną przez `valarray`.|
|[Maksymalny](#max)|Znajduje największy element w `valarray`.|
|[długości](#min)|Znajduje najmniejszy element w `valarray`.|
|[Zmień rozmiar](#resize)|Zmienia liczbę elementów w `valarray` na określoną liczbę, dodając lub usuwając elementy zgodnie z wymaganiami.|
|[nocn](#shift)|Przenosi wszystkie elementy w `valarray` o określoną liczbę pozycji.|
|[zmienia](#size)|Znajduje liczbę elementów w `valarray`.|
|[należności](#sum)|Określa sumę wszystkich elementów w `valarray` o niezerowej długości.|
|[wymiany](#swap)||

### <a name="operators"></a>Operatory

|||
|-|-|
|[zakład!](#op_not)|Jednoargumentowy operator, który uzyskuje logiczne wartości `NOT` każdego elementu w `valarray`.|
|[operator% =](#op_mod_eq)|Uzyskuje pozostałą część dzielenia elementów tablicy przez określony `valarray` lub przez wartość typu elementu.|
|[& operatora =](#op_and_eq)|Uzyskuje `AND` bitowe elementów w tablicy albo z odpowiednimi elementami w określonym `valarray` lub z wartością typu elementu.|
|[> operatora > =](#op_gt_gt_eq)|Prawy przesuwa bity dla każdego elementu operandu `valarray` określoną liczbę pozycji lub przez liczbę elementów określoną przez drugi `valarray`.|
|[< operatora < =](#op_lt_lt_eq)|Lewy przesuwa bity dla każdego elementu operandu `valarray` określoną liczbę pozycji lub przez liczbę elementów określoną przez drugi `valarray`.|
|[operator * =](#op_star_eq)|Mnoży elementy określonego `valarray` lub wartości typu elementu z elementem, do `valarray`operandu.|
|[operator +](#op_add)|Jednoargumentowy operator, który stosuje znak plus do każdego elementu w `valarray`.|
|[operator + =](#op_add_eq)|Dodaje elementy określonego `valarray` lub wartości typu elementu z elementem do operandu `valarray`.|
|[zakład](#operator-)|Jednoargumentowy operator, który stosuje znak minus do każdego elementu w `valarray`.|
|[operator-=](#operator-_eq)|Odejmuje elementy określonego `valarray` lub wartości typu elementu z elementu operandu z `valarray`.|
|[operator/=](#op_div_eq)|Dzieli operand `valarray` elementowo przez elementy określonego `valarray` lub wartość typu elementu.|
|[operator =](#op_eq)|Przypisuje elementy do `valarray`, których wartości są określone bezpośrednio lub jako część innych `valarray` lub `slice_array`, `gslice_array`, `mask_array`lub `indirect_array`.|
|[zakład&#91;&#93;](#op_at)|Zwraca odwołanie do elementu lub jego wartości w określonym indeksie lub określonym podzbiorze.|
|[operator ^ =](#op_xor_eq)|Uzyskuje wyłączny operator logiczny or (`XOR`) tablicy z określonym valarray lub wartością typu elementu.|
|[operator&#124;=](#op_or_eq)|Uzyskuje `OR` bitowe elementów w tablicy albo z odpowiednimi elementami w określonym `valarray` lub z wartością typu elementu.|
|[operator ~](#op_dtor)|Jednoargumentowy operator, który uzyskuje wartości bitowe `NOT` każdego elementu w `valarray`.|

## <a name="apply"></a>stosowa

Stosuje określoną funkcję do każdego elementu valarray.

```cpp
valarray<Type> apply(Type _Func(Type)) const;

valarray<Type> apply(Type _Func(constType&)) const;
```

### <a name="parameters"></a>Parametry

*_Func (typ)* \
Obiekt funkcyjny do zastosowania do każdego elementu operandu valarray.

*_Func (typ stałej &)* \
Obiekt funkcyjny dla elementu const, który ma być stosowany do poszczególnych elementów operandu valarray.

### <a name="return-value"></a>Wartość zwrócona

Element valarray, którego elementy miały `_Func` zastosowane elementy do elementów operandu valarray.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca obiekt klasy [valarray](../standard-library/valarray-class.md) **\<typu >** , o [rozmiarze](#size)długości, z których *każdy jest `_Func((*this)[I])`* elementów.

### <a name="example"></a>Przykład

```cpp
// valarray_apply.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

using namespace std;

int __cdecl MyApplyFunc( int n )
{
   return n*2;
}

int main( int argc, char* argv[] )
{
   valarray<int> vaR(10), vaApplied(10);
   int i;

   for ( i = 0; i < 10; i += 3 )
      vaR[i] = i;

   for ( i = 1; i < 10; i += 3 )
      vaR[i] = 0;

   for ( i = 2; i < 10; i += 3 )
      vaR[i] = -i;

   cout << "The initial Right valarray is: (";
   for   ( i=0; i < 10; ++i )
      cout << " " << vaR[i];
   cout << " )" << endl;

   vaApplied = vaR.apply( MyApplyFunc );

   cout << "The element-by-element result of "
       << "applying MyApplyFunc to vaR is the\nvalarray: ( ";
   for ( i = 0; i < 10; ++i )
      cout << " " << vaApplied[i];
   cout << " )" << endl;
}
```

```Output
The initial Right valarray is: ( 0 0 -2 3 0 -5 6 0 -8 9 )
The element-by-element result of applying MyApplyFunc to vaR is the
valarray: (  0 0 -4 6 0 -10 12 0 -16 18 )
```

## <a name="cshift"></a>cshift

Cyklicznie przesuwa wszystkie elementy w valarray o określoną liczbę pozycji.

```cpp
valarray<Type> cshift(int count) const;
```

### <a name="parameters"></a>Parametry

*liczba*\
Liczba miejsc, w których elementy mają zostać przesunięte do przodu.

### <a name="return-value"></a>Wartość zwrócona

Nowy valarray, w którym wszystkie elementy zostały *przesunięte* cyklicznie do przodu valarray, po lewej stronie względem ich pozycji w valarray operandu.

### <a name="remarks"></a>Uwagi

Dodatnia wartość *Count* przesuwa elementy w *liczbie* pozostawionych cyklicznie.

Ujemna wartość *Count* przesuwa elementy o *liczbę* w prawo cyklicznie.

### <a name="example"></a>Przykład

```cpp
// valarray_cshift.cpp
// compile with: /EHsc

#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;

    valarray<int> va1(10), va2(10);
    for (i = 0; i < 10; i+=1)
        va1[i] = i;
    for (i = 0; i < 10; i+=1)
        va2[i] = 10 - i;

    cout << "The operand valarray va1 is: (";
    for (i = 0; i < 10; i++)
        cout << " " << va1[i];
    cout << ")" << endl;

    // A positive parameter shifts elements right
    va1 = va1.cshift(4);
    cout << "The cyclically shifted valarray va1 is:\nva1.cshift (4) = (";
    for (i = 0; i < 10; i++)
        cout << " " << va1[i];
    cout << ")" << endl;

    cout << "The operand valarray va2 is: (";
    for (i = 0; i < 10; i++)
        cout << " " << va2[i];
    cout << ")" << endl;

    // A negative parameter shifts elements left
    va2 = va2.cshift(-4);
    cout << "The cyclically shifted valarray va2 is:\nva2.shift (-4) = (";
    for (i = 0; i < 10; i++)
        cout << " " << va2[i];
    cout << ")" << endl;
}
```

```Output
The operand valarray va1 is: ( 0 1 2 3 4 5 6 7 8 9)
The cyclically shifted valarray va1 is:
va1.cshift (4) = ( 4 5 6 7 8 9 0 1 2 3)
The operand valarray va2 is: ( 10 9 8 7 6 5 4 3 2 1)
The cyclically shifted valarray va2 is:
va2.shift (-4) = ( 4 3 2 1 10 9 8 7 6 5)
```

## <a name="free"></a>zwolniony

Zwalnia pamięć używaną przez valarray.

```cpp
void free();
```

### <a name="remarks"></a>Uwagi

Ta funkcja niestandardowa jest równoważna przypisaniu pustej valarray. Na przykład:

```cpp
valarray<T> v;
v = valarray<T>();

// equivalent to v.free()
```

## <a name="max"></a>Maksymalny

Znajduje największy element w valarray.

```cpp
Type max() const;
```

### <a name="return-value"></a>Wartość zwrócona

Maksymalna wartość elementów w operandzie valarray.

### <a name="remarks"></a>Uwagi

Funkcja członkowska porównuje wartości przez zastosowanie **\<operatora** lub **operatora >** między parami elementów klasy `Type`, dla których operatory muszą być dostarczone dla elementu `Type`.

### <a name="example"></a>Przykład

```cpp
// valarray_max.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i, MaxValue;

   valarray<int> vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  2*i - 1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  10 - i;

   cout << "The operand valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   MaxValue = vaR.max (  );
   cout << "The largest element in the valarray is: "
        << MaxValue  << "." << endl;
}
```

```Output
The operand valarray is: ( 0 1 8 3 7 5 6 13 2 9 ).
The largest element in the valarray is: 13.
```

## <a name="min"></a>długości

Znajduje najmniejszy element w valarray.

```cpp
Type min() const;
```

### <a name="return-value"></a>Wartość zwrócona

Minimalna wartość elementów w operandzie valarray.

### <a name="remarks"></a>Uwagi

Funkcja członkowska porównuje wartości przez zastosowanie **\<operatora** lub **operatora >** między parami elementów klasy `Type`, dla których operatory muszą być dostarczone dla elementu `Type`.

### <a name="example"></a>Przykład

```cpp
// valarray_min.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i, MinValue;

   valarray<int> vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  2*i;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  5 - i;

   cout << "The operand valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   MinValue = vaR.min ( );
   cout << "The smallest element in the valarray is: "
        << MinValue  << "." << endl;
}
/* Output:
The operand valarray is: ( 0 2 3 -3 8 0 -6 14 -3 -9 ).
The smallest element in the valarray is: -9.
*/
```

## <a name="op_not"></a>zakład!

Jednoargumentowy operator, który uzyskuje logiczne **nie** wartości każdego elementu w valarray.

```cpp
valarray<bool> operator!() const;
```

### <a name="return-value"></a>Wartość zwrócona

Valarray wartości logicznych, które są negacją wartości elementu operandu valarray.

### <a name="remarks"></a>Uwagi

Operacja logiczna **nie** wyklucza elementów, ponieważ konwertuje wszystkie zera na te i traktuje wszystkie wartości niezerowe jako te i konwertuje je na zera. Zwrócone valarray wartości logicznych mają taki sam rozmiar jak argument operacji valarray.

Istnieje również bitowy **nie**[valarray:: operator ~](#op_dtor) , który wyklucza poziom poszczególnych bitów w binarnej reprezentacji **char** i **int** elementów valarray.

### <a name="example"></a>Przykład

```cpp
// valarray_op_lognot.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<bool> vaNOT ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaNOT = !vaL;
   cout << "The element-by-element result of "
        << "the logical NOT operator! is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The element-by-element result of the logical NOT operator! is the
valarray: ( 1 1 1 0 1 0 1 0 1 0 ).
```

## <a name="op_mod_eq"></a>operator% =

Uzyskuje pozostałą część dzielenia elementów tablicy przez określony valarray lub przez wartość typu elementu.

```cpp
valarray<Type>& operator%=(const valarray<Type>& right);

valarray<Type>& operator%=(const Type& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Valarray lub wartość typu elementu identycznego z argumentem operandu valarray, który jest podzielona, element, argument operacji valarray.

### <a name="return-value"></a>Wartość zwrócona

Element valarray, którego elementy są resztą z dzielenia elementu operandu valarray przez *prawo*

### <a name="example"></a>Przykład

```cpp
// valarray_class_op_rem.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 6 ), vaR ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  53;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -67;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  3*i+1;

   cout << "The initial valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL %= vaR;
   cout << "The remainders from the element-by-element "
        << "division is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 53 -67 53 -67 53 -67 ).
The initial  right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
valarray: ( 0 -3 4 -7 1 -3 ).
```

## <a name="op_and_eq"></a>&amp;operatora =

Uzyskuje bitowe **i** elementy w tablicy z odpowiednimi elementami w określonym valarray lub z wartością typu elementu.

```cpp
valarray<Type>& operator&=(const valarray<Type>& right);

valarray<Type>& operator&=(const Type& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Valarray lub wartość typu elementu identyczna z typem operandu valarray, który ma być połączony, element, przez `AND` logiczny z operandem valarray.

### <a name="return-value"></a>Wartość zwrócona

Element valarray, którego elementy są logicznymi `AND` argumentu operacji valarray przez *prawo*

### <a name="remarks"></a>Uwagi

Operacji bitowej można używać tylko do manipulowania bitami w typach danych **char** i **int** , a nie w obiektach typu **float**, **Double**, **longdouble**, **void**, **bool**lub innych, bardziej złożonych typów danych.

Bitowe i ma tę samą tabelę prawdy co `AND` logicznej, ale ma zastosowanie do typu danych na poziomie poszczególnych bitów. Dane bity *b*1 i *b*2, *b*1 `AND` *b*2 są **prawdziwe** , jeśli obie bity są prawdziwe; **wartość false** , jeśli co najmniej jeden ma wartość false.

### <a name="example"></a>Przykład

```cpp
// valarray_class_op_bitand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL &= vaR;
   cout << "The element-by-element result of "
        << "the logical AND operator&= is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&= is the
valarray: ( 0 0 0 2 0 4 0 6 0 8 ).
```

## <a name="op_gt_gt_eq"></a>&gt;&gt;operatora =

Prawy przesuwa bity dla każdego elementu operandu valarray określoną liczbę pozycji lub przez liczbę elementów określoną przez drugi valarray.

```cpp
valarray<Type>& operator>>=(const valarray<Type>& right);

valarray<Type>& operator>>=(const Type& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Wartość wskazująca ilość prawego przesunięcia lub valarray, której elementy wskazują ilość elementów po prawej stronie.

### <a name="return-value"></a>Wartość zwrócona

Element valarray, którego elementy zostały przesunięte w prawo o kwotę określoną w *prawej*.

### <a name="remarks"></a>Uwagi

Cyfry podpisane mają zachowane znaki.

### <a name="example"></a>Przykład

```cpp
// valarray_class_op_rs.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  64;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -64;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial operand valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL >>= vaR;
   cout << "The element-by-element result of "
        << "the right shift is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial operand valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
```

## <a name="op_lt_lt_eq"></a>&lt;&lt;operatora =

Lewy przesuwa bity dla każdego elementu operandu valarray określoną liczbę pozycji lub przez liczbę elementów określoną przez drugi valarray.

```cpp
valarray<Type>& operator<<=(const valarray<Type>& right);

valarray<Type>& operator<<=(const Type& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Wartość wskazująca ilość przesunięcia w lewo lub valarray, której elementy wskazują liczbę elementów przesunięcia w lewo.

### <a name="return-value"></a>Wartość zwrócona

Element valarray, którego elementy zostały przesunięte w lewo o kwotę określoną w *prawej*.

### <a name="remarks"></a>Uwagi

Cyfry podpisane mają zachowane znaki.

### <a name="example"></a>Przykład

```cpp
// valarray_class_op_ls.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial operand valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL <<= vaR;
   cout << "The element-by-element result of "
        << "the left shift"
        << endl << "on the operand array is the valarray:"
        << endl << "( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial operand valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift
on the operand array is the valarray:
( 1 -2 4 -8 16 -32 64 -128 ).
```

## <a name="op_star_eq"></a>operator * =

Mnoży elementy określonego valarray lub wartości typu elementu z elementem, do operandu valarray.

```cpp
valarray<Type>& operator*=(const valarray<Type>& right);

valarray<Type>& operator*=(const Type& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Valarray lub wartość typu elementu identycznego z argumentem operandu valarray, który ma być mnożony element, argument operacji valarray.

### <a name="return-value"></a>Wartość zwrócona

Element valarray, którego elementy stanowią iloczyn elementu operandu valarray i *Right*.

### <a name="example"></a>Przykład

```cpp
// valarray_op_emult.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL *= vaR;
   cout << "The element-by-element result of "
        << "the multiplication is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
*/
```

## <a name="op_add"></a>operator +

Jednoargumentowy operator, który stosuje znak plus do każdego elementu w valarray.

```cpp
valarray<Type> operator+() const;
```

### <a name="return-value"></a>Wartość zwrócona

Element valarray, którego elementy są powiększone do tablic operandów.

### <a name="example"></a>Przykład

```cpp
// valarray_op_eplus.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<int> vaPLUS ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaPLUS = +vaL;
   cout << "The element-by-element result of "
        << "the operator+ is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaPLUS [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
valarray: ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
```

## <a name="op_add_eq"></a>operator + =

Dodaje elementy określonego valarray lub wartości typu elementu z elementem, do operandu valarray.

```cpp
valarray<Type>& operator+=(const valarray<Type>& right);

valarray<Type>& operator+=(const Type& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Valarray lub wartość typu elementu identycznego z argumentem operandu valarray, który ma zostać dodany do operandu valarray.

### <a name="return-value"></a>Wartość zwrócona

Element valarray, którego elementy są sumą elementów operandu valarray i *Right*.

### <a name="example"></a>Przykład

```cpp
// valarray_op_eadd.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL += vaR;
   cout << "The element-by-element result of "
        << "the sum is the"
        << endl << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
valarray: ( 2 0 4 2 6 4 8 6 ).
```

## <a name="operator-"></a>zakład

Jednoargumentowy operator, który stosuje znak minus do każdego elementu w valarray.

```cpp
valarray<Type> operator-() const;
```

### <a name="return-value"></a>Wartość zwrócona

Element valarray, którego elementy są pomniejszone o tablicę operandu.

### <a name="example"></a>Przykład

```cpp
// valarray_op_eminus.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<int> vaMINUS ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaMINUS = -vaL;
   cout << "The element-by-element result of "
        << "the operator+ is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaMINUS [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
valarray: ( 0 0 2 -2 4 -4 6 -6 8 -8 ).
```

## <a name="operator-_eq"></a>operator-=

Odejmuje elementy określonego valarray lub wartości typu elementu z elementu z operandem valarray.

```cpp
valarray<Type>& operator-=(const valarray<Type>& right);

valarray<Type>& operator-=(const Type& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Valarray lub wartość typu elementu identycznego z typem operandu valarray, który ma zostać odjęty, z elementem operandu valarray.

### <a name="return-value"></a>Wartość zwrócona

Element valarray, którego elementy są różnicą elementu operandu valarray i *po prawej stronie*.

### <a name="example"></a>Przykład

```cpp
// valarray_op_esub.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  10;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL -= vaR;
   cout << "The element-by-element result of "
        << "the difference is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
```

## <a name="op_div_eq"></a>operator/=

Dzieli argument operandu valarray przez elementy określonego valarray lub wartość typu elementu.

```cpp
valarray<Type>& operator/=(const valarray<Type>& right);

valarray<Type>& operator/=(const Type& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Valarray lub wartość typu elementu identyczna z typem operandu valarray, który ma być podzielony, elementowy, do operand valarray.

### <a name="return-value"></a>Wartość zwrócona

Element valarray, którego elementy są elementem ilorazu argumentu operacji valarray podzielone przez *prawo*.

### <a name="example"></a>Przykład

```cpp
// valarray_op_ediv.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<double> vaL ( 6 ), vaR ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  100;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -100;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  2*i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL /= vaR;
   cout << "The element-by-element result of "
        << "the quotient is the"
        << endl << "valarray: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
valarray: ( inf -50 25 -16.6667 12.5 -10 ).
```

## <a name="op_eq"></a>operator =

Przypisuje elementy do valarray, których wartości są określone bezpośrednio lub jako część innych valarray lub przez slice_array, gslice_array, mask_array lub indirect_array.

```cpp
valarray<Type>& operator=(const valarray<Type>& right);

valarray<Type>& operator=(valarray<Type>&& right);

valarray<Type>& operator=(const Type& val);

valarray<Type>& operator=(const slice_array<Type>& _Slicearray);

valarray<Type>& operator=(const gslice_array<Type>& _Gslicearray);

valarray<Type>& operator=(const mask_array<Type>& _Maskarray);

valarray<Type>& operator=(const indirect_array<Type>& _Indarray);
```

### <a name="parameters"></a>Parametry

*prawa*\
Valarray do skopiowania do operandu valarray.

*val*\
Wartość, która ma zostać przypisana do elementów operandu valarray.

*_Slicearray*\
Slice_array, które mają zostać skopiowane do operandu valarray.

*_Gslicearray*\
Gslice_array, które mają zostać skopiowane do operandu valarray.

*_Maskarray*\
Mask_array, które mają zostać skopiowane do operandu valarray.

*_Indarray*\
Indirect_array, które mają zostać skopiowane do operandu valarray.

### <a name="return-value"></a>Wartość zwrócona

Pierwszy operator członkowski zastępuje kontrolowaną sekwencję kopią sekwencji kontrolowanej przez *prawo*.

Drugi operator składowej jest taki sam jak pierwszy, ale z [odwołaniem rvalue deklarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

Trzeci operator członkowski zamienia każdy element kontrolowanej sekwencji na kopię *Val*.

Operatory pozostałych członków zastępują te elementy kontrolowanej sekwencji wybranej przez ich argumenty, które są generowane tylko przez [operator&#91;](#op_at).

Jeśli wartość elementu członkowskiego w sekwencji z kontrolą zastępczą zależy od elementu członkowskiego w początkowej kontrolowanej sekwencji, wynik jest niezdefiniowany.

### <a name="remarks"></a>Uwagi

Jeśli długość kontrolowanej sekwencji ulegnie zmianie, wynik jest zwykle niezdefiniowany. W tej implementacji efekt jest jednak jedynie unieważnić wszystkie wskaźniki lub odwołania do elementów w kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// valarray_op_assign.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 1 )
      va [ i ] = i;
   for ( i = 0 ; i < 10 ; i+=1 )
      vaR [ i ] = 10 -  i;

   cout << "The operand valarray va is:";
   for ( i = 0 ; i < 10 ; i++ )
      cout << " " << va [ i ];
   cout << endl;

   cout << "The operand valarray vaR is:";
      for ( i = 0 ; i < 10 ; i++ )
         cout << " " << vaR [ i ];
   cout << endl;

   // Assigning vaR to va with the first member functon
   va = vaR;
   cout << "The reassigned valarray va is:";
   for ( i = 0 ; i < 10 ; i++ )
      cout << " " << va [ i ];
   cout << endl;

   // Assigning elements of value 10 to va
   // with the second member functon
   va = 10;
   cout << "The reassigned valarray va is:";
      for ( i = 0 ; i < 10 ; i++ )
         cout << " " << va [ i ];
   cout << endl;
}
```

```Output
The operand valarray va is: 0 1 2 3 4 5 6 7 8 9
The operand valarray vaR is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 10 10 10 10 10 10 10 10 10

```

## <a name="op_at"></a>operator []

Zwraca odwołanie do elementu lub jego wartości w określonym indeksie lub określonym podzbiorze.

```cpp
Type& operator[](size_t _Off);

slice_array<Type> operator[](slice _Slicearray);

gslice_array<Type> operator[](const gslice& _Gslicearray);

mask_array<Type> operator[](const valarray<bool>& _Boolarray);

indirect_array<Type> operator[](const valarray<size_t>& _Indarray);

Type operator[](size_t _Off) const;

valarray<Type> operator[](slice _Slice) const;

valarray<Type> operator[](const gslice& _Gslicearray) const;

valarray<Type> operator[](const valarray<bool>& _Boolarray) const;

valarray<Type> operator[](const valarray<size_t>& _Indarray) const;
```

### <a name="parameters"></a>Parametry

*_Off*\
Indeks elementu, do którego ma zostać przypisana wartość.

*_Slicearray*\
Slice_array elementu valarray, który określa podzestaw do wybrania lub zwrócenia do nowego valarray.

*_Gslicearray*\
Gslice_array elementu valarray, który określa podzestaw do wybrania lub zwrócenia do nowego valarray.

*_Boolarray*\
Bool_array elementu valarray, który określa podzestaw do wybrania lub zwrócenia do nowego valarray.

*_Indarray*\
Indirect_array elementu valarray, który określa podzestaw do wybrania lub zwrócenia do nowego valarray.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do elementu lub jego wartości w określonym indeksie lub określonym podzbiorze.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego jest przeciążony, aby zapewnić kilka sposobów wybierania sekwencji elementów spośród tych, które są kontrolowane przez <strong>\*to</strong>. Pierwsza grupa pięciu operatorów członkowskich działa w połączeniu z różnymi przeciążeniami [operatora =](#op_eq) (i innych przypisywania operatorów), aby umożliwić selektywne zastępowanie (cięcie) kontrolowanej sekwencji. Wybrane elementy muszą istnieć.

Podczas kompilowania przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowanego jako 1 lub 2, wystąpi błąd czasu wykonywania, jeśli próbujesz uzyskać dostęp do elementu poza granicami valarray.  Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md) .

### <a name="example"></a>Przykład

Zobacz przykłady [wycinków:: Slice](../standard-library/slice-class.md#slice) i [gslice:: gslice](../standard-library/gslice-class.md#gslice) , aby zapoznać się z przykładem sposobu deklarowania i używania operatora.

## <a name="op_xor_eq"></a>operator ^ =

Uzyskuje wyłączny operator logiczny or ( **XOR**) tablicy z określonym valarray lub wartością typu elementu.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Valarray lub wartość typu elementu identycznego z argumentem operandu valarray, który ma być połączony, element, przez wyłączną logiczną **XOR** z argumentem valarray.

### <a name="return-value"></a>Wartość zwrócona

Valarray, którego elementy są elementami elementu, wyłączną logiczną **XOR** operacji valarray i *Right*.

### <a name="remarks"></a>Uwagi

Wartość logiczna or, nazywana **XOR**, ma następującą semantykę: podano elementy *e*1 i *e*2, *e*1 **XOR** *e*2 jest **prawdziwe** , jeśli dokładnie jeden z tych elementów ma wartość true; **Fałsz** , jeśli oba elementy mają wartość false lub jeśli oba elementy mają wartość true.

### <a name="example"></a>Przykład

```cpp
// valarray_op_exor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;

    valarray<int> vaL ( 10 ), vaR ( 10 );
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

    cout << "The initial operand valarray is:  ( ";
        for (i = 0 ; i < 10 ; i++ )
            cout << vaL [ i ] << " ";
    cout << ")." << endl;

    cout << "The  right valarray is: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaR [ i ] << " ";
    cout << ")." << endl;

    vaL ^= vaR;
    cout << "The element-by-element result of "
        << "the bitwise XOR operator^= is the"
        << endl << "valarray: ( ";
        for (i = 0 ; i < 10 ; i++ )
            cout << vaL [ i ] << " ";
    cout << ")." << endl;
}
```

```Output
The initial operand valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^= is the
valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
```

## <a name="op_or_eq"></a>operator&#124;=

Uzyskuje `OR` bitowe elementów w tablicy albo z odpowiednimi elementami w określonym valarray lub z wartością typu elementu.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Valarray lub wartość typu elementu identycznego z argumentem operandu valarray, który ma być połączony, element, przez `OR` bitowego z operandem valarray.

### <a name="return-value"></a>Wartość zwrócona

Element valarray, którego elementy stanowią `OR` bitowe elementu operand valarray przez *prawo*.

### <a name="remarks"></a>Uwagi

Operacji bitowej można używać tylko do manipulowania bitami w typach danych **char** i **int** , a nie w obiektach typu **float**, **Double**, **longdouble**, **void**, **bool**lub innych, bardziej złożonych typów danych.

`OR` bitowe ma tę samą tabelę prawdy co logiczne `OR`, ale ma zastosowanie do typu danych na poziomie poszczególnych bitów. Określone bity *b*1 i *b*2, *b*1 `OR` *b*2 są **prawdziwe** , jeśli co najmniej jeden z bitów ma wartość true; **Fałsz** , jeśli obie bity mają wartość false.

### <a name="example"></a>Przykład

```cpp
// valarray_class_op_bitor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
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

   cout << "The initial operand valarray is:"
        << endl << "( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is:"
        << endl << "( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL |= vaR;
   cout << "The element-by-element result of "
        << "the logical OR"
        << endl << "operator|= is the valarray:"
        << endl << "( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial operand valarray is:
( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is:
( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the logical OR
operator|= is the valarray:
( 1 0 1 3 3 4 7 6 7 9 ).
```

## <a name="op_dtor"></a>operator ~

Jednoargumentowy operator, który uzyskuje wartości bitowe `NOT` każdego elementu w valarray.

```cpp
valarray<Type> operator~() const;
```

### <a name="return-value"></a>Wartość zwrócona

Valarray wartości logicznych, które są bitowym `NOT` wartości elementu operandu valarray.

### <a name="remarks"></a>Uwagi

Operacji bitowej można używać tylko w celu manipulowania bitami w typach danych **char** i **int** oraz w odmianach, a nie w przypadku elementów **zmiennoprzecinkowych**, **Double**, **longdouble**, **void**, **bool** i innych, bardziej złożonych typów danych.

`NOT` bitowe ma tę samą tabelę prawdy co logiczne `NOT`, ale ma zastosowanie do typu danych na poziomie poszczególnych bitów. Podano bit *b*, ~ *b* ma wartość true, jeśli *b* ma wartość false, i wartość false, jeśli *b* ma wartość true. Operator logiczny **not**[!](#op_not) dotyczy na poziomie elementu, licząc wszystkie wartości niezerowe jako **prawdziwe**, a wynik jest valarray wartości logicznych. `NOToperator~`bitowe, z kolei, może spowodować valarray wartości innych niż 0 lub 1, w zależności od wyniku operacji bitowej.

### <a name="example"></a>Przykład

```cpp
// valarray_op_bitnot.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;

    valarray<unsigned short int> vaL1 ( 10 );
    valarray<unsigned short int> vaNOT1 ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        vaL1 [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 2 )
        vaL1 [ i ] =  5*i;

    cout << "The initial valarray <unsigned short int> is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaL1 [ i ] << " ";
    cout << ")." << endl;

    vaNOT1 = ~vaL1;
    cout << "The element-by-element result of "
        << "the bitwise NOT operator~ is the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT1 [ i ] << " ";
    cout << ")." << endl << endl;

    valarray<int> vaL2 ( 10 );
    valarray<int> vaNOT2 ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        vaL2 [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 2 )
        vaL2 [ i ] =  -2 * i;

    cout << "The initial valarray <int> is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaL2 [ i ] << " ";
    cout << ")." << endl;

    vaNOT2 = ~vaL2;
    cout << "The element-by-element result of "
        << "the bitwise NOT operator~ is the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT2 [ i ] << " ";
    cout << ")." << endl;

    // The negative numbers are represented using
    // the two's complement approach, so adding one
    // to the flipped bits returns the negative elements
    vaNOT2 = vaNOT2 + 1;
    cout << "The element-by-element result of "
        << "adding one"
        << endl << "is the negative of the "
        << "original elements the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT2 [ i ] << " ";
    cout << ")." << endl;
}
```

```Output
The initial valarray <unsigned short int> is:  ( 0 5 2 15 4 25 6 35 8 45 ).
The element-by-element result of the bitwise NOT operator~ is the
valarray: ( 65535 65530 65533 65520 65531 65510 65529 65500 65527 65490 ).

The initial valarray <int> is:  ( 0 -2 2 -6 4 -10 6 -14 8 -18 ).
The element-by-element result of the bitwise NOT operator~ is the
valarray: ( -1 1 -3 5 -5 9 -7 13 -9 17 ).
The element-by-element result of adding one
is the negative of the original elements the
valarray: ( 0 2 -2 6 -4 10 -6 14 -8 18 ).
```

## <a name="resize"></a>Zmień rozmiar

Zmienia liczbę elementów w valarray na określoną liczbę.

```cpp
void resize(
    size_t _Newsize);

void resize(
    size_t _Newsize,
    const Type val);
```

### <a name="parameters"></a>Parametry

*_Newsize*\
Liczba elementów w valarray o zmienionym rozmiarze.

*val*\
Wartość, która ma zostać nadana elementom valarray o zmienionym rozmiarze.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska inicjuje elementy z ich konstruktorem domyślnym.

Wszystkie wskaźniki lub odwołania do elementów w kontrolowanej sekwencji są unieważnione.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia funkcji składowej valarray:: Resize.

```cpp
// valarray_resize.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;
    size_t size1, sizeNew;

    valarray<int> va1(10);
    for (i = 0; i < 10; i+=1)
        va1[i] = i;

    cout << "The valarray contains ( ";
        for (i = 0; i < 10; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;

    size1 = va1.size();
    cout << "The number of elements in the valarray is: "
         << size1  << "." <<endl << endl;

    va1.resize(15, 10);

    cout << "The valarray contains ( ";
        for (i = 0; i < 15; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;
    sizeNew = va1.size();
    cout << "The number of elements in the resized valarray is: "
         << sizeNew  << "." <<endl << endl;
}
```

```Output
The valarray contains ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray is: 10.

The valarray contains ( 10 10 10 10 10 10 10 10 10 10 10 10 10 10 10 ).
The number of elements in the resized valarray is: 15.
```

## <a name="shift"></a>nocn

Przenosi wszystkie elementy w valarray o określoną liczbę miejsc.

```cpp
valarray<Type> shift(int count) const;
```

### <a name="parameters"></a>Parametry

*liczba*\
Liczba miejsc, w których elementy mają zostać przesunięte do przodu.

### <a name="return-value"></a>Wartość zwrócona

Nowy valarray, w którym wszystkie elementy zostały *przesunięte* do góry valarray, po lewej stronie w odniesieniu do ich pozycji w valarray operandu.

### <a name="remarks"></a>Uwagi

Dodatnia wartość *Count* przesuwa elementy w lewo *Liczba* , z wypełnieniem zero.

Ujemna wartość *Count* przesuwa się w miejscach *Liczba* praw elementów z wartością zero.

### <a name="example"></a>Przykład

```cpp
// valarray_shift.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va1 ( 10 ), va2 ( 10 );
   for ( i = 0 ; i < 10 ; i += 1 )
      va1 [ i ] =  i;
   for ( i = 0 ; i < 10 ; i += 1 )
      va2 [ i ] = 10 -  i;

   cout << "The operand valarray va1(10) is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va1 [ i ] << " ";
   cout << ")." << endl;

   // A positive parameter shifts elements left
   va1 = va1.shift ( 4 );
   cout << "The shifted valarray va1 is: va1.shift (4) = ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va1 [ i ] << " ";
   cout << ")." << endl;

   cout << "The operand valarray va2(10) is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va2 [ i ] << " ";
   cout << ")." << endl;

   // A negative parameter shifts elements right
   va2 = va2.shift ( - 4 );
   cout << "The shifted valarray va2 is: va2.shift (-4) = ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va2 [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The shifted valarray va1 is: va1.shift (4) = ( 4 5 6 7 8 9 0 0 0 0 ).
The operand valarray va2(10) is: ( 10 9 8 7 6 5 4 3 2 1 ).
The shifted valarray va2 is: va2.shift (-4) = ( 0 0 0 0 10 9 8 7 6 5 ).
```

## <a name="size"></a>zmienia

Znajduje liczbę elementów w valarray.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Wartość zwrócona

Liczba elementów w operandzie valarray.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia funkcji składowej valarray:: size.

```cpp
// valarray_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;
    size_t size1, size2;

    valarray<int> va1(10), va2(12);
    for (i = 0; i < 10; i += 1)
        va1[i] =  i;
    for (i = 0; i < 10; i += 1)
        va2[i] =  i;

    cout << "The operand valarray va1(10) is: ( ";
        for (i = 0; i < 10; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;

    size1 = va1.size();
    cout << "The number of elements in the valarray va1 is: va1.size = "
         << size1  << "." <<endl << endl;

    cout << "The operand valarray va2(12) is: ( ";
        for (i = 0; i < 10; i++)
            cout << va2[i] << " ";
    cout << ")." << endl;

    size2 = va2.size();
    cout << "The number of elements in the valarray va2 is: va2.size = "
         << size2  << "." << endl << endl;

    // Initializing two more elements to va2
    va2[10] = 10;
    va2[11] = 11;
    cout << "After initializing two more elements,\n"
         << "the operand valarray va2(12) is now: ( ";
        for (i = 0; i < 12; i++)
            cout << va2[i] << " ";
    cout << ")." << endl;
    cout << "The number of elements in the valarray va2 is still: "
         << size2  << "." << endl;
}
```

```Output
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray va1 is: va1.size = 10.

The operand valarray va2(12) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray va2 is: va2.size = 12.

After initializing two more elements,
the operand valarray va2(12) is now: ( 0 1 2 3 4 5 6 7 8 9 10 11 ).
The number of elements in the valarray va2 is still: 12.
```

## <a name="sum"></a>należności

Określa sumę wszystkich elementów w valarray o niezerowej długości.

```cpp
Type sum() const;
```

### <a name="return-value"></a>Wartość zwrócona

Suma elementów operandu valarray.

### <a name="remarks"></a>Uwagi

Jeśli długość jest większa niż jeden, funkcja członkowska dodaje wartości do sumy przez zastosowanie `operator+=` między parami elementów klasy `Type`, które w związku z tym muszą być dostarczone dla elementów typu `Type`.

### <a name="example"></a>Przykład

```cpp
// valarray_sum.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    int sumva = 0;

    valarray<int> va ( 10 );
    for ( i = 0 ; i < 10 ; i+=1 )
        va [ i ] =  i;

    cout << "The operand valarray va (10) is: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << va [ i ] << " ";
    cout << ")." << endl;

    sumva = va.sum ( );
    cout << "The sum of elements in the valarray is: "
        << sumva  << "." <<endl;
}
```

```Output
The operand valarray va (10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The sum of elements in the valarray is: 45.
```

## <a name="swap"></a>wymiany

Wymienia elementy dwóch `valarray`s.

```cpp
void swap(valarray& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
`valarray` udostępniający elementy, które mają zostać zamienione.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia kontrolowane sekwencje między `*this` i *po prawej*. Robi to w stałym czasie, nie zgłasza żadnych wyjątków i unieważnia odwołania, wskaźniki lub Iteratory, które wyznaczają elementy w dwóch kontrolowanej sekwencji.

## <a name="valarray"></a>valarray

Tworzy tablicę valarray, o określonym rozmiarze lub z elementami o określonej wartości lub jako kopię innej tablicy valarray lub podzbioru innej tablicy valarray.

```cpp
valarray();

explicit valarray(
    size_t Count);

valarray(
    const Type& Val,
    size_t Count);

valarray(
    const Type* Ptr,
    size_t Count);

valarray(
    const valarray<Type>& Right);

valarray(
    const slice_array<Type>& SliceArray);

valarray(
    const gslice_array<Type>& GsliceArray);

valarray(
    const mask_array<Type>& MaskArray);

valarray(
    const indirect_array<Type>& IndArray);

valarray(
    valarray<Type>&& Right);

valarray(
    initializer_list<Type> IList);
```

### <a name="parameters"></a>Parametry

*Liczba*\
Liczba elementów, które mają się znaleźć w tablicy valarray.

*Val*\
Wartość, która ma być użyta do inicjowania elementów w tablicy valarray.

\ *PTR*
Wskaźnik do wartości, które mają użyte do inicjowania elementów w tablicy valarray.

*Prawa*\
Istniejąca tablica valarray do zainicjowania nowej tablicy valarray.

*SliceArray*\
Tablica typu slice_array, której wartości elementów mają być użyte do inicjowania elementów tworzonej tablicy valarray.

*GsliceArray*\
Tablica typu gslice_array, której wartości elementów mają być użyte do inicjowania elementów tworzonej tablicy valarray.

*MaskArray*\
Tablica typu mask_array, której wartości elementów mają być użyte do inicjowania elementów tworzonej tablicy valarray.

*IndArray*\
Tablica typu indirect_array, której wartości elementów mają być użyte do inicjowania elementów tworzonej tablicy valarray.

\ *IList*
Lista initializer_list zawierająca elementy do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy (domyślny) konstruktor inicjuje obiekt jako pustą tablicę. Następne trzy konstruktory każdy inicjują obiekt do tablicy elementów *Count* w następujący sposób:

- Dla jawnego `valarray(size_t Count)`, każdy element jest inicjowany przy użyciu konstruktora domyślnego.

- W przypadku `valarray(const Type& Val, Count)`każdy element jest inicjowany z *Val*.

- W przypadku `valarray(const Type* Ptr, Count)`element w pozycji `I` jest inicjowany z `Ptr`[`I`].

Każdy pozostały Konstruktor inicjuje obiekt do valarray typu\<> obiektu określonego przez podzestaw określony w argumencie.

Ostatni Konstruktor jest taki sam jak następny do ostatniego, ale z [rvalue odwołanie deklarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

### <a name="example"></a>Przykład

```cpp
// valarray_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;

    // The second member function
    valarray<int> va(10);
    for (auto i : va){
        va[i] = 2 * (i + 1);
    }

    cout << "The operand valarray va is:\n(";
    for (auto i : va) {
        cout << " " << va[i];
    }
    cout << " )" << endl;

    slice Slice(2, 4, 3);

    // The fifth member function
    valarray<int> vaSlice = va[Slice];

    cout << "The new valarray initialized from the slice is vaSlice =\n"
        << "va[slice( 2, 4, 3)] = (";
    for (int i = 0; i < 3; i++) {
        cout << " " << vaSlice[i];
    }
    cout << " )" << endl;

    valarray<int> va2{{ 1, 2, 3, 4 }};
    for (auto& v : va2) {
        cout << v << " ";
    }
    cout << endl;
}
```

```Output
The operand valarray va is:
( 0 2 2 2 2 2 2 2 2 2 )
The new valarray initialized from the slice is vaSlice =
va[slice( 2, 4, 3)] = ( 0 0 0 )
1 2 3 4
```

## <a name="value_type"></a>value_type

Typ, który reprezentuje typ elementu przechowywanego w valarray.

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Type`.

### <a name="example"></a>Przykład

```cpp
// valarray_value_type.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    valarray<int> va ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        va [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 2 )
        va [ i ] =  -1;

    cout << "The initial operand valarray is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << va [ i ] << " ";
    cout << ")." << endl;

    // value_type declaration and initialization:
    valarray<int>::value_type Right = 10;

    cout << "The decalared value_type Right is: "
            << Right << endl;
    va *= Right;
    cout << "The resulting valarray is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << va [ i ] << " ";
    cout << ")." << endl;
}
```

```Output
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).
The decalared value_type Right is: 10
The resulting valarray is:  ( 0 -10 20 -10 40 -10 60 -10 80 -10 ).
```

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
