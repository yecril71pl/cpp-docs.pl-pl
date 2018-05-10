---
title: valarray — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7b0c0499b9dfbaf3cb1f19eba16fc684a229839
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="valarray-class"></a>valarray — Klasa

Klasa szablonu opisuje obiekt, który określa sekwencję elementów typu **typu** który są przechowywane w postaci tablicy, przeznaczony dla szybkich operacji matematycznych i zoptymalizowane pod kątem wydajności obliczeniowej.

## <a name="remarks"></a>Uwagi

Klasa jest reprezentację matematyczne pojęcie uporządkowany zestaw wartości i elementy są numerowane od zera. Klasa jest określane jako near kontenera, ponieważ obsługuje on niektórych, ale nie wszystkie funkcje to najwyższej jakości sekwencji kontenerów, takich jak [wektor](../standard-library/vector-class.md), obsługuje. Różni się od szablonu klasy wektor w dwóch sposobów:

- Definiuje wiele operacji arytmetycznych między elementami odpowiedniego **valarray —\<typu >** obiekty tego samego typu i długości, takich jak *xarr* = cos ( *yarr*) + sin ( *zarr*).

- Definiuje różne ciekawe sposoby indeks dolny **valarray —\<typu >** obiektu przez przeładowanie [operator&#91;&#93;](#op_at).

Obiekt klasy **typu**:

- Ma publicznego konstruktora domyślnego, destruktor, konstruktora kopiującego i operatora przypisania z konwencjonalnej zachowanie.

- Definiuje operatory arytmetyczne i funkcje matematyczne, zgodnie z potrzebami, które są zdefiniowane dla typów zmiennoprzecinkowych, z konwencjonalnej zachowanie.

W szczególności nie niewielkie różnice mogą istnieć między konstruowania kopiowania i konstrukcji domyślne następuje przypisania. Żadna z operacji w obiektach klasy **typu** może zgłaszać wyjątków.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[valarray —](#valarray)|Konstruuje `valarray` o określonym rozmiarze lub z elementami określonej wartości lub jest kopią innego `valarray` lub podzestawem innej `valarray`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[value_type](#value_type)|Typ reprezentujący typ elementu przechowywane w `valarray`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[Zastosuj](#apply)|Dotyczy określona funkcja każdy element `valarray`.|
|[cshift](#cshift)|Cyklicznie kierowany wszystkie elementy w `valarray` przez określoną liczbę pozycji.|
|[free](#free)|Zwalnia pamięć używana przez `valarray`.|
|[max](#max)|Wyszukuje największy element w `valarray`.|
|[min](#min)|Wyszukuje najmniejszy element w `valarray`.|
|[Zmiana rozmiaru](#resize)|Zmienia liczbę elementów w `valarray` do określonej liczby, dodawanie lub usuwanie elementów zgodnie z potrzebami.|
|[shift](#shift)|Przenosi wszystkie elementy w `valarray` przez określoną liczbę pozycji.|
|[Rozmiar](#size)|Liczba elementów w znajduje `valarray`.|
|[sum](#sum)|Określa Suma wszystkich elementów w `valarray` niezerową długość.|
|[swap](#swap)||

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!](#op_not)|Operator jednoargumentowy, który uzyskuje logicznym `NOT` wartości poszczególnych elementów w `valarray`.|
|[operator%=](#op_mod_eq)|Uzyskuje resztę z dzielenia elementów tablicy element-wise przez określonej `valarray` lub za pomocą wartości typu elementu.|
|[operator&=](#op_amp_eq)|Uzyskuje operatora testu koniunkcji `AND` elementów w tablicy za pomocą odpowiednich elementów w określonym `valarray` lub za pomocą wartości typu elementu.|
|[operator>>=](#op_gt_gt_eq)|Usługi bits dla każdego elementu przesunięcia w prawo z `valarray` określonej liczby miejsc lub element-wise wartość określoną w drugi operand `valarray`.|
|[Operator << =](#op_lt_lt_eq)|Usługi bits dla każdego elementu dla przesunięcia w lewo z `valarray` określonej liczby miejsc lub element-wise wartość określoną w drugi operand `valarray`.|
|[operator*=](#op_star_eq)|Mnoży elementy określonej `valarray` lub wartości typu elementu element-wise do argumentu operacji `valarray`.|
|[operator +](#op_add)|Operator jednoargumentowy, który dotyczy plus każdy element `valarray`.|
|[operator+=](#op_add_eq)|Dodaje elementy określonej `valarray` lub wartości typu elementu element-wise do argumentu operacji `valarray`.|
|[operator-](#operator-)|Operator jednoargumentowy, którego dotyczy minus każdego elementu w `valarray`.|
|[operator-=](#operator-_eq)|Odejmuje elementy określonej `valarray` lub wartości typu elementu element-wise z argumentem `valarray`.|
|[/ = — operator](#op_div_eq)|Dzieli operand `valarray` element-wise przez elementy określonej `valarray` lub wartości typu elementu.|
|[operator=](#op_eq)|Przypisuje elementy `valarray` których wartości są określone, bezpośrednio lub jako część innej `valarray` lub `slice_array`, `gslice_array`, `mask_array`, lub `indirect_array`.|
|[operator&#91;&#93;](#op_at)|Zwraca odwołanie do elementu lub jego wartość w określonym indeksie lub podzbiór określony.|
|[operator^=](#op_xor_eq)|Uzyskuje element-wise wyłącznie logicznego or — operator ( `XOR`) z określonym valarray — lub wartości typu elementu tablicy.|
|[operator&#124;=](#op_or_eq)|Uzyskuje operatora testu koniunkcji `OR` elementów w tablicy za pomocą odpowiednich elementów w określonym `valarray` lub za pomocą wartości typu elementu.|
|[operator ~](#op_dtor)|Operator jednoargumentowy, który uzyskuje operatora testu koniunkcji `NOT` wartości poszczególnych elementów w `valarray`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray — >

**Namespace:** Standard

## <a name="apply"></a>  valarray::apply

Każdy element valarray — dotyczy podanej funkcji.

```cpp
valarray<Type> apply(Type _Func(Type)) const;

valarray<Type> apply(Type _Func(constType&)) const;
```

### <a name="parameters"></a>Parametry

*_Func(Type)* obiekt funkcji ma zostać zastosowany do każdego elementu valarray — argument.

*_Func(Const type&)* funkcja obiekt const ma zostać zastosowany do każdego elementu valarray — argument.

### <a name="return-value"></a>Wartość zwracana

Valarray —, której elementy miały `_Func` element-wise stosowane do elementów valarray — argument.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca obiekt klasy [valarray —](../standard-library/valarray-class.md)**\<typu >**, o długości [rozmiar](#size), każdy z elementów, których `I` jest **func**((  **\*to**) [ `I`]).

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
\* Output:
The initial Right valarray is: ( 0 0 -2 3 0 -5 6 0 -8 9 )
The element-by-element result of applying MyApplyFunc to vaR is the
valarray: (  0 0 -4 6 0 -10 12 0 -16 18 )
*\
```

## <a name="cshift"></a>  valarray::cshift

Cyklicznie kierowany wszystkie elementy w valarray — przez określoną liczbę pozycji.

```cpp
valarray<Type> cshift(int count) const;
```

### <a name="parameters"></a>Parametry

`count` Liczba miejsc, w których elementy mają zostać przesunięty do przodu.

### <a name="return-value"></a>Wartość zwracana

Valarray — nowy, w którym wszystkie elementy zostały przeniesione `count` pozycji cyklicznie kierunku na początku valarray —, lewo względem ich położenia w valarray — argument.

### <a name="remarks"></a>Uwagi

Dodatnia wartość `count` przewiduje cyklicznie lewo elementów `count` miejsca.

Wartość ujemna `count` przewiduje elementy cyklicznie prawo `count` miejsca.

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
\* Output:
The operand valarray va1 is: ( 0 1 2 3 4 5 6 7 8 9)
The cyclically shifted valarray va1 is:
va1.cshift (4) = ( 4 5 6 7 8 9 0 1 2 3)
The operand valarray va2 is: ( 10 9 8 7 6 5 4 3 2 1)
The cyclically shifted valarray va2 is:
va2.shift (-4) = ( 4 3 2 1 10 9 8 7 6 5)
*\
```

## <a name="free"></a>  valarray::Free

Zwalnia pamięć używana przez valarray —.

```cpp
void free();
```

### <a name="remarks"></a>Uwagi

Ta funkcja niestandardowa jest odpowiednikiem przypisywanie puste valarray —. Na przykład:

```cpp
valarray<T> v;
v = valarray<T>();

// equivalent to v.free()
```

## <a name="max"></a>  valarray::Max

Valarray — znalezieniu największy element.

```cpp
Type max() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna wartość elementów w valarray — argument.

### <a name="remarks"></a>Uwagi

Funkcja członkowska porównuje wartości, stosując **operator\<**  lub **operator >** między parami elementy klasy **typu**, które operatory musi być podana dla elementu **typu**.

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
\* Output:
The operand valarray is: ( 0 1 8 3 7 5 6 13 2 9 ).
The largest element in the valarray is: 13.
*\
```

## <a name="min"></a>  valarray::min

Valarray — znalezieniu najmniejszy element.

```cpp
Type min() const;
```

### <a name="return-value"></a>Wartość zwracana

Minimalna wartość elementów w valarray — argument.

### <a name="remarks"></a>Uwagi

Funkcja członkowska porównuje wartości, stosując **operator\<**  lub **operator >** między parami elementy klasy **typu**, które operatory musi być podana dla elementu **typu**.

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
\* Output:
The operand valarray is: ( 0 2 3 -3 8 0 -6 14 -3 -9 ).
The smallest element in the valarray is: -9.
*\
```

## <a name="op_not"></a>  valarray::operator!

Operator jednoargumentowy, który uzyskuje logicznym **nie** wartości poszczególnych elementów w valarray —.

```cpp
valarray<bool> operator!() const;
```

### <a name="return-value"></a>Wartość zwracana

Valarray — wartości logiczna Negacja wartości elementu valarray — argument.

### <a name="remarks"></a>Uwagi

Operacja logiczna **nie** Negacja elementów, ponieważ konwertuje same zera do grupy i w odniesieniu do wszystkich wartości niezerowych, niż i konwertuje je na zero. Zwrócony valarray — wartości logicznych jest taki sam rozmiar jak valarray — argument.

Istnieje również bitowej **nie**[valarray::operator ~](#op_dtor) który Negacja na poziomie poszczególnych bitów w reprezentacja binarna `char` i `int` elementy valarray —.

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
        << "the logical NOT operator! is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The element-by-element result of the logical NOT operator! is the
 valarray: ( 1 1 1 0 1 0 1 0 1 0 ).
*\
```

## <a name="op_mod_eq"></a>  valarray::operator % =

Uzyskuje resztę z dzielenia elementów tablicy element-wise przez określony valarray — lub wartości typu elementu.

```cpp
valarray<Type>& operator%=(const valarray<Type>& right);

valarray<Type>& operator%=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray — lub wartość identyczna ze valarray — argument, który polega ona na dzieleniu element-wise, valarray — argument typu elementu.

### <a name="return-value"></a>Wartość zwracana

Valarray —, której elementy są resztę z element-wise podziału valarray — argument przez `right`

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
        << "division is the\n valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is: ( 53 -67 53 -67 53 -67 ).
The initial  right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
 valarray: ( 0 -3 4 -7 1 -3 ).
*\
```

## <a name="and_eq"></a>  valarray::operator&amp;=

Uzyskuje operatora testu koniunkcji **i** elementów w tablicy z odpowiednich elementów w określonym valarray — lub z wartością typu elementu.

```cpp
valarray<Type>& operator&=(const valarray<Type>& right);

valarray<Type>& operator&=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray — lub wartość typu elementu identyczna ze valarray — argument, który ma być łączone, element-wise przez logicznym **i** z valarray — argument.

### <a name="return-value"></a>Wartość zwracana

Valarray —, której elementy są element-wise logicznej **i** z valarray — argument przez `right`

### <a name="remarks"></a>Uwagi

Operacji można używać tylko do manipulowania bitów w `char` i `int` typy danych i wariantów, a nie na **float**, **podwójne**, **longdouble**, `void`, `bool`, lub inne, bardziej złożone typy danych.

Iloczynu bitowego AND ma tej samej tabeli prawdy jako logiczny **i** , ale odnoszące się do typu danych na poziomie poszczególnych bitów. Podane bitów *b*1 i *b*2, *b*1 **i** *b*2 jest **true** Jeśli oba Usługa BITS mają wartość true; **false** Jeśli co najmniej jeden ma wartość false.

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
        << "the logical AND operator&= is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&= is the
 valarray: ( 0 0 0 2 0 4 0 6 0 8 ).
*\
```

## <a name="op_gt_gt_eq"></a>  valarray::operator&gt;&gt;=

Prawo zmian usługi bits dla każdego elementu valarray — argument operacji określonej liczby miejsc lub element-wise wartość określoną w drugim valarray —.

```cpp
valarray<Type>& operator>>=(const valarray<Type>& right);

valarray<Type>& operator>>=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Wartość wskazująca przesunięcia w prawo lub valarray —, której elementy wskazują element-wise wielkość przesunięcia w prawo.

### <a name="return-value"></a>Wartość zwracana

Valarray —, której elementy zostały przesunięte prawo wartość określoną w `right`.

### <a name="remarks"></a>Uwagi

Numery podpisem mają swoje znaki zachowane.

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
        << "the right shift is the\n valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial operand valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
 valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
*\
```

## <a name="op_lt_lt_eq"></a>  valarray::operator&lt;&lt;=

Po lewej zmian usługi bits dla każdego elementu valarray — argument operacji określonej liczby miejsc lub element-wise wartość określoną w drugim valarray —.

```cpp
valarray<Type>& operator<<=(const valarray<Type>& right);

valarray<Type>& operator<<=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Wartość wskazująca przesunięcia w lewo lub valarray —, której elementy wskazują element-wise wielkość przesunięcia w lewo.

### <a name="return-value"></a>Wartość zwracana

Valarray —, których elementy mają zostać przesunięty w lewo wartość określoną w `right`.

### <a name="remarks"></a>Uwagi

Numery podpisem mają swoje znaki zachowane.

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
        << "the left shift\n on the operand array is the valarray:\n ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial operand valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift
 on the operand array is the valarray:
 ( 1 -2 4 -8 16 -32 64 -128 ).
*\
```

## <a name="op_star_eq"></a>  valarray::operator * =

Mnoży elementy określonego valarray — lub wartości typu elementu element-wise, aby valarray — argument.

```cpp
valarray<Type>& operator*=(const valarray<Type>& right);

valarray<Type>& operator*=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray — lub wartość identyczna ze valarray — argument, który mnożenia element-wise, valarray — argument typu elementu.

### <a name="return-value"></a>Wartość zwracana

Valarray —, której elementy są element-wise iloczyn valarray — operand i `right`.

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
        << "the multiplication is the\n valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
 valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
*\
```

## <a name="op_add"></a>  valarray::operator +

Operator jednoargumentowy dotyczy plus każdy element valarray —.

```cpp
valarray<Type> operator+() const;
```

### <a name="return-value"></a>Wartość zwracana

Valarray —, której elementy są oraz te tablicy argumentu.

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
        << "the operator+ is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaPLUS [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
 valarray: ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
*\
```

## <a name="op_add_eq"></a>  valarray::operator +=

Dodaje elementy określonej valarray — lub wartości typu elementu element-wise, valarray — argument.

```cpp
valarray<Type>& operator+=(const valarray<Type>& right);

valarray<Type>& operator+=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray — lub wartość identyczna ze valarray — argument, który ma zostać dodany, element-wise, aby valarray — operand typu elementu.

### <a name="return-value"></a>Wartość zwracana

Valarray —, której elementy są element-wise sumę valarray — operand i `right`.

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
        << "the sum is the\n valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
 valarray: ( 2 0 4 2 6 4 8 6 ).
*\
```

## <a name="valarray__operator-"></a>  valarray::operator-

Operator jednoargumentowy dotyczy minus każdy element valarray —.

```cpp
valarray<Type> operator-() const;
```

### <a name="return-value"></a>Wartość zwracana

Valarray —, której elementy są minus tych tablicy argumentu.

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
        << "the operator+ is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaMINUS [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
 valarray: ( 0 0 2 -2 4 -4 6 -6 8 -8 ).
*\
```

## <a name="valarray__operator-_eq"></a>  valarray::operator-=

Odejmuje elementy określonego valarray — lub wartości typu elementu element-wise, z valarray — argument.

```cpp
valarray<Type>& operator-=(const valarray<Type>& right);

valarray<Type>& operator-=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray — lub wartość identyczna ze valarray — argument, który można odejmować, element-wise, z valarray — argument typu elementu.

### <a name="return-value"></a>Wartość zwracana

Valarray —, której elementy są element-wise różnicę valarray — operand i `right`.

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
        << "the difference is the\n valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
 valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
*\
```

## <a name="op_div_eq"></a>  valarray::operator / =

Dzieli valarray — argument element-wise przez elementy określonego valarray — lub wartości typu elementu.

```cpp
valarray<Type>& operator/=(const valarray<Type>& right);

valarray<Type>& operator/=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray — lub wartość identyczna ze valarray — argument, który ma być podzielone, element-wise, valarray — operand typu elementu.

### <a name="return-value"></a>Wartość zwracana

Valarray —, której elementy są element-wise iloraz valarray — argument podzielona przez `right`.

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
        << "the quotient is the\n valarray: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
 valarray: ( inf -50 25 -16.6667 12.5 -10 ).
*\
```

## <a name="op_eq"></a>  valarray::operator =

Valarray —, których wartości są określone, bezpośrednio lub w ramach innych valarray — lub slice_array —, gslice_array —, mask_array — lub indirect_array — przypisuje elementów.

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

`right` Valarray — można skopiować do valarray — argument.

`val` Wartość do przypisania do elementów valarray — argument.

`_Slicearray` Slice_array — można skopiować do valarray — argument.

`_Gslicearray` Gslice_array — można skopiować do valarray — argument.

`_Maskarray` Mask_array — można skopiować do valarray — argument.

`_Indarray` Indirect_array — można skopiować do valarray — argument.

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator członkowski zastępuje kopię sekwencji kontrolowane przez kontrolowanej sekwencji `right`.

Drugi operator członkowski jest taka sama jak pierwszy, ale z [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

Trzeci operator członkowski zastępuje kopię każdego elementu w kontrolowanej sekwencji `val`.

Pozostałe operatorów Członkowskich Zastąp te elementy kontrolowanej sekwencji wybranych przez ich argumentów, które są generowane tylko przez [operator&#91;&#93;](#op_at).

Jeśli wartość elementu członkowskiego w sekwencji zastępczy kontrolowane zależy od elementu członkowskiego w kontrolowanej sekwencji początkowej, wynikiem jest niezdefiniowany.

### <a name="remarks"></a>Uwagi

W przypadku zmiany długości kontrolowanej sekwencji, wynik jest zwykle niezdefiniowany. W tej implementacji jednak efekt jest jedynie unieważnić wskaźniki ani odwołania do elementów w kontrolowanej sekwencji.

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
\* Output:
The operand valarray va is: 0 1 2 3 4 5 6 7 8 9
The operand valarray vaR is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 10 10 10 10 10 10 10 10 10
*\
```

## <a name="op_at"></a>  valarray::operator]

Zwraca odwołanie do elementu lub jego wartość w określonym indeksie lub podzbiór określony.

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

`_Off` Indeks elementu, który ma być przypisana wartość.

`_Slicearray` Slice_array — z valarray —, określająca podzbiór, która zostanie wybrana lub powrót do nowego valarray —.

`_Gslicearray` Gslice_array — z valarray —, określająca podzbiór, która zostanie wybrana lub powrót do nowego valarray —.

*_Boolarray* bool_array valarray —, określająca podzbiór, która zostanie wybrana lub powrót do nowego valarray —.

`_Indarray` Indirect_array — z valarray —, określająca podzbiór, która zostanie wybrana lub powrót do nowego valarray —.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu lub jego wartość w określonym indeksie lub podzbiór określony.

### <a name="remarks"></a>Uwagi

Operator członkowski jest przeciążony zapewnienie kilka sposobów wybierania sekwencji elementy spośród kontrolowane przez *\****to**. Pierwsza grupa operatorów Członkowskich pięć pracy w połączeniu z różnych przeciążeń [— operator =](#op_eq) (i innych operatory przypisywania) umożliwia selektywne zastąpienia (fragmentowania) kontrolowanej sekwencji. Musi istnieć wybrane elementy.

Podczas kompilacji za pomocą [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowany jako 1 lub 2, błąd środowiska uruchomieniowego wystąpi przy próbie uzyskania dostępu do elementu poza granicami valarray —.  Zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

### <a name="example"></a>Przykład

Przykłady dla [slice::slice](../standard-library/slice-class.md#slice) i [gslice::gslice](../standard-library/gslice-class.md#gslice) przykład sposobu deklarowanie i użycie operatora.

## <a name="op_xor_eq"></a>  valarray::operator ^ =

Uzyskuje element-wise wyłącznie logicznego or — operator ( **XOR**) z określonym valarray — lub wartości typu elementu tablicy.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray — lub wartość typu elementu identyczna ze valarray — argument, który ma być łączone, element-wise przez jedynego logicznej **XOR** z valarray — argument.

### <a name="return-value"></a>Wartość zwracana

Valarray —, której elementy są wyłączne element-wise, logiczna **XOR** z valarray — operand i `right`.

### <a name="remarks"></a>Uwagi

Logiczny lub określone jako jedynego **XOR**, ma semantykę następujące: podane elementy *e*1 i *e*2, *e*1  **XOR** *e*2 jest **true** Jeśli dokładnie jeden z elementów ma wartość true; **false** Jeśli oba elementy są false lub jeśli spełnione są oba elementy.

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
        << "the bitwise XOR operator^= is the\n valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial operand valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^= is the
 valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
*\
```

## <a name="op_or_eq"></a>  valarray::operator&#124;=

Uzyskuje operatora testu koniunkcji `OR` elementów w tablicy z odpowiednich elementów w określonym valarray — lub z wartością typu elementu.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray — lub wartość typu elementu identyczna ze valarray — argument, który ma być łączone, element-wise przez operatora testu koniunkcji `OR` z valarray — argument.

### <a name="return-value"></a>Wartość zwracana

Valarray —, której elementy są element-wise bitowo `OR` z valarray — argument przez `right`.

### <a name="remarks"></a>Uwagi

Operacji można używać tylko do manipulowania bitów w `char` i `int` typy danych i wariantów, a nie na **float**, **podwójne**, **longdouble**, `void`, `bool`, lub inne, bardziej złożone typy danych.

Bitowe `OR` ma tej samej tabeli prawdy jako logiczny `OR` , ale odnoszące się do typu danych na poziomie poszczególnych bitów. Podane bitów *b*1 i *b*2, *b*1 `OR` *b*2 jest **true** Jeśli co najmniej jeden z usługi bits wartość PRAWDA; **false** Jeśli oba bity są wartość false.

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

   cout << "The initial operand valarray is:\n ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is:\n ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL |= vaR;
   cout << "The element-by-element result of "
        << "the logical OR\n operator|= is the valarray:\n ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial operand valarray is:
 ( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is:
 ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the logical OR
 operator|= is the valarray:
 ( 1 0 1 3 3 4 7 6 7 9 ).
*\
```

## <a name="op_dtor"></a>  valarray::operator ~

Operator jednoargumentowy, który uzyskuje operatora testu koniunkcji **nie** wartości poszczególnych elementów w valarray —.

```cpp
valarray<Type> operator~() const;
```

### <a name="return-value"></a>Wartość zwracana

Valarray — wartość logiczna wartości bitowe **nie** wartości elementu valarray — argument.

### <a name="remarks"></a>Uwagi

Operacji można używać tylko do manipulowania bitów w `char` i `int` typy danych i wariantów, a nie na **float**, **podwójne**, **longdouble**, `void`, `bool` lub inne, bardziej złożone typy danych.

Bitowe **nie** ma tej samej tabeli prawdy jako logiczny **nie** , ale odnoszące się do typu danych na poziomie poszczególnych bitów. Podane bit *b*, ~ *b* ma wartość true Jeśli *b* ma wartość false, a wartość false, gdy *b* ma wartość true. Logiczny **nie**[operatora!](#op_not) stosuje się na poziomie elementu, inwentaryzacji wszystkich niezerowe wartości jako **true**, a wynik jest valarray — wartości logicznych. Bitowe **NOToperator ~**, z kolei może spowodować valarray — wartości innych niż 0 lub 1, w zależności od wyniku operacji.

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
        << "the bitwise NOT operator~ is the\n valarray: ( ";
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
        << "the bitwise NOT operator~ is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT2 [ i ] << " ";
   cout << ")." << endl;

   // The negative numbers are represented using
   // the two's complement approach, so adding one
   // to the flipped bits returns the negative elements
   vaNOT2 = vaNOT2 + 1;
   cout << "The element-by-element result of "
        << "adding one\n is the negative of the "
        << "original elements the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT2 [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray <unsigned short int> is:  ( 0 5 2 15 4 25 6 35 8 45 ).
The element-by-element result of the bitwise NOT operator~ is the
 valarray: ( 65535 65530 65533 65520 65531 65510 65529 65500 65527 65490 ).

The initial valarray <int> is:  ( 0 -2 2 -6 4 -10 6 -14 8 -18 ).
The element-by-element result of the bitwise NOT operator~ is the
 valarray: ( -1 1 -3 5 -5 9 -7 13 -9 17 ).
The element-by-element result of adding one
 is the negative of the original elements the
 valarray: ( 0 2 -2 6 -4 10 -6 14 -8 18 ).
*\
```

## <a name="resize"></a>  valarray::Resize

Liczba elementów w valarray — zmienia się na określonej liczby.

```cpp
void resize(
    size_t _Newsize);

void resize(
    size_t _Newsize,
    const Type val);
```

### <a name="parameters"></a>Parametry

`_Newsize` Liczba elementów w zmienionym rozmiarze valarray —.

`val` Wartość do elementów po zmianie rozmiaru valarray —.

### <a name="remarks"></a>Uwagi

Pierwszy funkcji członkowskiej inicjuje elementów przy użyciu ich domyślnego konstruktora.

Wskaźniki ani odwołania do elementów w kontrolowanej sekwencji zostały unieważnione.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie funkcji członkowskiej valarray::resize.

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

## <a name="shift"></a>  valarray::SHIFT

Przenosi wszystkie elementy w valarray — w ciągu określonej liczby miejsc.

```cpp
valarray<Type> shift(int count) const;
```

### <a name="parameters"></a>Parametry

`count` Liczba miejsc, w których elementy mają zostać przesunięty do przodu.

### <a name="return-value"></a>Wartość zwracana

Valarray — nowy, w którym wszystkie elementy zostały przeniesione `count` pozycji do przodu valarray —, lewo względem ich położenia w valarray — argument.

### <a name="remarks"></a>Uwagi

Dodatnia wartość `count` przenosi elementy w lewo `count` umieszcza z wypełnieniem zero.

Wartość ujemna `count` przewiduje prawo elementy `count` umieszcza z wypełnieniem zero.

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
\* Output:
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The shifted valarray va1 is: va1.shift (4) = ( 4 5 6 7 8 9 0 0 0 0 ).
The operand valarray va2(10) is: ( 10 9 8 7 6 5 4 3 2 1 ).
The shifted valarray va2 is: va2.shift (-4) = ( 0 0 0 0 10 9 8 7 6 5 ).
*\
```

## <a name="size"></a>  valarray::size

Valarray — znalezieniu liczby elementów.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w valarray — argument.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie funkcji członkowskiej valarray::size.

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
    cout << "After initializing two more elements,\n "
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

## <a name="sum"></a>  valarray::sum

Określa Suma wszystkich elementów w valarray — niezerową długość.

```cpp
Type sum() const;
```

### <a name="return-value"></a>Wartość zwracana

Suma elementów valarray — argument.

### <a name="remarks"></a>Uwagi

Jeśli długość jest większa niż jeden, funkcja członkowska dodaje wartości do sumy przez zastosowanie `operator+=` między parami elementy klasy **typu**, jaki operator w związku z tym, należy podać dla elementów typu  **Typ**.

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
\* Output:
The operand valarray va (10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The sum of elements in the valarray is: 45.
*\
```

## <a name="swap"></a>  valarray::swap

Zamienia elementy dwóch `valarray`s.

```cpp
void swap(valarray& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`right`|A `valarray` dostarczanie elementy, aby być zamieniona.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia kontrolowanej sekwencji między `*this` i `right`. Robi to w czasie stałej, zgłasza bez wyjątków i go unieważnia nie odwołań, wskaźniki lub Iteratory, które określają elementów w dwóch kontrolowanej sekwencji.

## <a name="valarray"></a>  valarray::valarray

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

`Count` Liczba elementów w valarray —.

`Val` Wartość, która ma być używana podczas inicjowania elementów w valarray —.

`Ptr` Wskaźnik do wartości, które ma być używany do inicjowania elementów w valarray —.

`Right` Istniejące valarray — zainicjować nowe valarray —.

`SliceArray` Slice_array — wartości elementów, których mają być używane podczas inicjowania elementów valarray — tworzona.

`GsliceArray` Gslice_array — wartości elementów, których mają być używane podczas inicjowania elementów valarray — tworzona.

`MaskArray` Mask_array — wartości elementów, których mają być używane podczas inicjowania elementów valarray — tworzona.

`IndArray` Indirect_array — wartości elementów, których mają być używane podczas inicjowania elementów valarray — tworzona.

`IList` Initializer_list, zawierający elementów do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy (domyślny) konstruktor inicjuje obiekt jako pustą tablicę. Następne trzy konstruktory inicjują obiekt jako tablicę elementów `Count` w następujący sposób:

- Dla jawnego `valarray(size_t Count)`, każdy element jest inicjowany przy użyciu konstruktora domyślnego.

- Dla `valarray(const Type& Val, Count)`, każdy element jest inicjowany za pomocą `Val`.

- Aby uzyskać `valarray(const Type* Ptr, Count)`, element na pozycji `I` jest inicjowany z `Ptr`[ `I`].

Każdy pozostałych Konstruktor inicjuje obiekt do valarray —\<typu > obiekt ustaleniami podzestawu określona w argumencie.

Ostatni Konstruktor jest taka sama jak dalej, aby w ostatniej, ale z [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

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

    cout << "The new valarray initialized from the slice is vaSlice ="
        << "\nva[slice( 2, 4, 3)] = (";
    for (int i = 0; i < 3; i++) {
        cout << " " << vaSlice[i];
    }
    cout << " )" << endl;

    valarray<int> va2{{ 1, 2, 3, 4 }};
    for (auto& v : va2){
        cout << v << " ";
    }
    cout << endl;
}

```

```Output
The operand valarray va is:( 0 2 2 2 2 2 2 2 2 2 )The new valarray initialized from the slice is vaSlice =va[slice( 2, 4, 3)] = ( 0 0 0 )1 2 3 4
```

## <a name="value_type"></a>  valarray::value_type

Typ, który reprezentuje typ elementu przechowywane w valarray —.

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **typu**.

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
\* Output:
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).
The decalared value_type Right is: 10
The resulting valarray is:  ( 0 -10 20 -10 40 -10 60 -10 80 -10 ).
*\
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
