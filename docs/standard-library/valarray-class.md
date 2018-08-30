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
ms.openlocfilehash: 3294730f8f1cc835af49ee003d8f81830d64c9a6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198305"
---
# <a name="valarray-class"></a>valarray — Klasa

Klasa szablonu opisuje obiekt, który kontroluje sekwencje elementów typu `Type` , są przechowywane w postaci tablicy, przeznaczony do przeprowadzania szybkich operacji matematycznych i zoptymalizowana pod kątem wydajności obliczeniowej.

## <a name="remarks"></a>Uwagi

Klasa jest reprezentacją matematyczne koncepcji uporządkowany zestaw wartości i elementy są numerowane od zera. Klasa jest określana jako prawie kontenera, ponieważ obsługuje on niektóre, ale nie wszystkie funkcje to najwyższej jakości sekwencji kontenerów, takich jak [wektor](../standard-library/vector-class.md), pomocy technicznej. Różni się od szablonu klasy wektora na dwa istotne sposoby:

- Definiuje wiele operacji arytmetycznych między odpowiadające elementy `valarray<Type>` obiektów tego samego typu i długości, takich jak *xarr* = cos ( *yarr*) + sin ( *zarr*).

- Definiuje różne interesujących sposobów indeks dolny `valarray<Type>` obiektu przeciążając [operator&#91;&#93;](#op_at).

Obiekt klasy `Type`:

- Ma publicznego konstruktora domyślnego, destruktor, Konstruktor kopiujący i operator przypisania, za pomocą konwencjonalnych zachowanie.

- Definiuje operatory arytmetyczne i funkcje matematyczne, zgodnie z potrzebami, które są zdefiniowane dla typów zmiennoprzecinkowych, za pomocą konwencjonalnych zachowanie.

W szczególności nie subtelne może różnice między konstrukcja kopiowania i konstruowania domyślne następuje przypisanie. Brak operacji na obiekty klasy `Type` może zgłaszać wyjątki.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[valarray —](#valarray)|Konstruuje `valarray` o określonym rozmiarze lub z elementami określonej wartości lub jako kopię innej `valarray` lub podzbioru innej `valarray`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[value_type](#value_type)|Typ, który reprezentuje typ elementu przechowywanego w `valarray`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Zastosuj](#apply)|Stosuje określoną funkcję do każdego elementu `valarray`.|
|[cshift](#cshift)|Cyklicznie przenosi wszystkie elementy w `valarray` przez określoną liczbę pozycji.|
|[free](#free)|Zwalnia pamięć używana przez `valarray`.|
|[max](#max)|Umożliwia znalezienie największego elementu w `valarray`.|
|[min](#min)|Umożliwia znalezienie najmniejszy element w `valarray`.|
|[Zmiana rozmiaru](#resize)|Zmienia liczbę elementów w `valarray` do określonej liczby, dodawanie lub usuwanie elementów zgodnie z potrzebami.|
|[shift](#shift)|Przenosi wszystkie elementy w `valarray` przez określoną liczbę pozycji.|
|[Rozmiar](#size)|Wyszukuje liczbę elementów w `valarray`.|
|[sum](#sum)|Określa sumę wszystkich elementów w `valarray` długości wartość różną od zera.|
|[swap](#swap)||

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!](#op_not)|Jednoargumentowy operator, który uzyskuje logicznej `NOT` wartości każdego elementu w `valarray`.|
|[operator%=](#op_mod_eq)|Uzyskuje resztę z dzielenia element-wise elementów tablicy przy określonym `valarray` lub według wartości Typ elementu.|
|[operator&=](#op_amp_eq)|Uzyskuje bitowe `AND` elementów w tablicy przy użyciu odpowiednie elementy w określonej `valarray` przy użyciu wartości typu elementu.|
|[operator>>=](#op_gt_gt_eq)|Usługa bits dla każdego elementu przesunięcia w prawo o `valarray` określoną liczbę pozycji lub według określonej ilości element-wise określony przez drugi argument operacji `valarray`.|
|[Operator << =](#op_lt_lt_eq)|Usługi bits dla każdego elementu przesunięcia w lewo z `valarray` określoną liczbę pozycji lub według określonej ilości element-wise określony przez drugi argument operacji `valarray`.|
|[operator*=](#op_star_eq)|Mnoży elementy określonego `valarray` lub wartości typu elementu element-wise, aby argument operacji `valarray`.|
|[operator +](#op_add)|Operator jednoargumentowy stosowaną plus do każdego elementu w `valarray`.|
|[operator+=](#op_add_eq)|Dodaje elementy określonej `valarray` lub wartości typu elementu element-wise, aby argument operacji `valarray`.|
|[operator-](#operator-)|Jednoargumentowy operator, który ma zastosowanie minus do każdego elementu w `valarray`.|
|[operator-=](#operator-_eq)|Odejmuje elementy określonego `valarray` lub wartości typu elementu element-wise, od argumentu `valarray`.|
|[operator / =](#op_div_eq)|Dzieli operand `valarray` element-wise przez elementy określonego `valarray` lub wartości typu elementu.|
|[operator=](#op_eq)|Przypisuje elementów `valarray` których wartości są określone, bezpośrednio lub jako część innej `valarray` lub `slice_array`, `gslice_array`, `mask_array`, lub `indirect_array`.|
|[operator&#91;&#93;](#op_at)|Zwraca odwołanie do elementu lub jego wartość w określonym indeksie lub określony podzbiór.|
|[operator^=](#op_xor_eq)|Uzyskuje operator wyłączny element-wise logiczne or ( `XOR`) tablicy przy użyciu określonej tablicy valarray lub wartości typu elementu.|
|[operator&#124;=](#op_or_eq)|Uzyskuje bitowe `OR` elementów w tablicy przy użyciu odpowiednie elementy w określonej `valarray` przy użyciu wartości typu elementu.|
|[operator ~](#op_dtor)|Jednoargumentowy operator, który uzyskuje bitowe `NOT` wartości każdego elementu w `valarray`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray >

**Namespace:** standardowe

## <a name="apply"></a>  valarray::apply

Stosuje określoną funkcję do każdego elementu tablicy valarray.

```cpp
valarray<Type> apply(Type _Func(Type)) const;

valarray<Type> apply(Type _Func(constType&)) const;
```

### <a name="parameters"></a>Parametry

*_Func(Type)*<br/>
 Obiekt funkcji, które mają być stosowane do każdego elementu operand valarray.

*_Func(Const type&)*<br/>
 Obiekt funkcji dla stałej, które mają być stosowane do każdego elementu operand valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy miały `_Func` element-wise stosowany do elementów operand valarray.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca obiekt klasy [valarray](../standard-library/valarray-class.md)**\<typ >**, długości [rozmiar](#size), każdy z elementów, których *I*jest `_Func((*this)[I])`.

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

Cyklicznie przenosi wszystkie elementy w tablicy valarray przez określoną liczbę pozycji.

```cpp
valarray<Type> cshift(int count) const;
```

### <a name="parameters"></a>Parametry

*Liczba*  
 Liczba miejsc, które elementy są jest przesuwany do przodu.

### <a name="return-value"></a>Wartość zwracana

Nowa tablica valarray, w którym wszystkie elementy zostały przeniesione *liczba* pozycji cyklicznie w kierunku początku tablicy valarray, pozostanie w odniesieniu do ich pozycje w tablicy valarray operand.

### <a name="remarks"></a>Uwagi

Dodatnia wartość *liczba* przenosi cyklicznie lewej elementy *liczba* miejsc.

Wartość ujemna *liczba* przenosi cyklicznie odpowiednie elementy *liczba* miejsc.

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

Zwalnia pamięć używana przez tablicy valarray.

```cpp
void free();
```

### <a name="remarks"></a>Uwagi

Ta funkcja niestandardowa jest odpowiednikiem przypisywanie pusta tablicy valarray. Na przykład:

```cpp
valarray<T> v;
v = valarray<T>();

// equivalent to v.free()
```

## <a name="max"></a>  valarray::Max

Odnajduje największego elementu w tablicy valarray.

```cpp
Type max() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna wartość elementów w tablicy valarray operand.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego porównuje wartości, stosując **operator\<**  lub **operatora >** między parami elementów klasy `Type`, operatorów, które musi być podana dla elementu `Type`.

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

Odnajduje najmniejszy element w tablicy valarray.

```cpp
Type min() const;
```

### <a name="return-value"></a>Wartość zwracana

Minimalna wartość elementów w tablicy valarray operand.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego porównuje wartości, stosując **operator\<**  lub **operatora >** między parami elementów klasy `Type`, operatorów, które musi być podana dla elementu `Type`.

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

Jednoargumentowy operator, który uzyskuje logicznej **nie** wartości każdego elementu w tablicy valarray.

```cpp
valarray<bool> operator!() const;
```

### <a name="return-value"></a>Wartość zwracana

Valarray — wartości logicznych negacji wartości elementu operand valarray.

### <a name="remarks"></a>Uwagi

Operacja logiczna **nie** neguje elementów, ponieważ konwertuje na temat usług będą same zera i w odniesieniu do wszystkich wartości niezerowych, niż i konwertuje je do zera. Zwrócone valarray, wartości logicznych jest taki sam rozmiar jak operand valarray.

Istnieje również bitowej **nie**[valarray::operator ~](#op_dtor) , neguje na poziomie poszczególnych usługi bits w reprezentacja binarna **char** i **int**  elementów tablicy valarray.

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

Uzyskuje resztę z dzielenia elementów tablicy element-wise określonej tablicy valarray lub wartości typu elementu.

```cpp
valarray<Type>& operator%=(const valarray<Type>& right);

valarray<Type>& operator%=(const Type& right);
```

### <a name="parameters"></a>Parametry

*right*  
 Valarray lub wartość taka sama jak w przypadku operand valarray, który polega ona na dzieleniu element-wise, operand valarray typu elementu.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są resztę z dzielenia element-wise operand valarray przez *prawo*

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

Uzyskuje bitowe **i** elementów w tablicy przy użyciu odpowiednie elementy w określonej tablicy valarray lub z wartością typu elementu.

```cpp
valarray<Type>& operator&=(const valarray<Type>& right);

valarray<Type>& operator&=(const Type& right);
```

### <a name="parameters"></a>Parametry

*right*  
 Valarray lub wartości typu elementu, taka sama jak w przypadku operand valarray, który ma być łączone, element-wise, przez logicznej `AND` z operand valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są element-wise logiczne `AND` z operand valarray przez *prawo*

### <a name="remarks"></a>Uwagi

Operacja bitowa należy używać tylko do manipulowania bitów **char** i **int** typów danych i wariantów a nie w systemie **float**, **double**, **longdouble**, **void**, **bool**, lub inne, bardziej złożone typy danych.

Bitowe AND ma tej samej tabeli prawdziwych danych jako logiczny `AND` , ale ma zastosowanie do typu danych na poziomie pojedynczych bitów. Biorąc pod uwagę bitów *b*1 i *b*2, *b*1 `AND` *b*2 jest **true** Jeśli oba bity są true; **false** Jeśli co najmniej jedna ma wartość false.

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

Po prawej stronie przesunięcia bitów dla każdego elementu w tablicy valarray operandu określoną liczbę pozycji i według określonej ilości element-wise określony przez drugi tablicy valarray.

```cpp
valarray<Type>& operator>>=(const valarray<Type>& right);

valarray<Type>& operator>>=(const Type& right);
```

### <a name="parameters"></a>Parametry

*right*  
 Wartość wskazująca, wielkość przesunięcia bitowego w prawo lub wskazać element-wise ilość przesunięcia bitowego w prawo, której elementy w tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy zostały przesunięte w prawo wartość określoną w *prawo*.

### <a name="remarks"></a>Uwagi

Oznaczone liczby ma znak zachowane.

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

Po lewej stronie przesunięcia bitów dla każdego elementu w tablicy valarray operandu określoną liczbę pozycji i według określonej ilości element-wise określony przez drugi tablicy valarray.

```cpp
valarray<Type>& operator<<=(const valarray<Type>& right);

valarray<Type>& operator<<=(const Type& right);
```

### <a name="parameters"></a>Parametry

*right*  
 Wartość wskazująca, wielkość przesunięcia w lewo lub wskazać element-wise ilość przesunięcia w lewo, której elementy w tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy mają zostać przesunięty left wartość określoną w *prawo*.

### <a name="remarks"></a>Uwagi

Oznaczone liczby ma znak zachowane.

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

Mnoży elementów określonej tablicy valarray lub wartości typu elementu element-wise, aby operand valarray.

```cpp
valarray<Type>& operator*=(const valarray<Type>& right);

valarray<Type>& operator*=(const Type& right);
```

### <a name="parameters"></a>Parametry

*right*  
 Valarray lub wartość taka sama jak w przypadku operand valarray, który jest do pomnożenia element-wise, operand valarray typu elementu.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są mnożenia operand valarray i *prawo*.

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

Jednoargumentowy operator plus dotyczy każdego elementu w tablicy valarray.

```cpp
valarray<Type> operator+() const;
```

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są oraz te tablicy operand.

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

Dodaje elementy określonej tablicy valarray lub wartości typu elementu element-wise, operand valarray.

```cpp
valarray<Type>& operator+=(const valarray<Type>& right);

valarray<Type>& operator+=(const Type& right);
```

### <a name="parameters"></a>Parametry

*right*  
 Valarray lub wartość taka sama jak w przypadku operand valarray, który ma zostać dodany, element-wise, aby operand valarray typu elementu.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są element-wise sumę operand valarray i *prawo*.

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

Jednoargumentowy operator minus dotyczy każdego elementu w tablicy valarray.

```cpp
valarray<Type> operator-() const;
```

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są minus tych tablicy operand.

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

Odejmuje elementów określonej tablicy valarray lub wartości typu elementu element-wise, z operand valarray.

```cpp
valarray<Type>& operator-=(const valarray<Type>& right);

valarray<Type>& operator-=(const Type& right);
```

### <a name="parameters"></a>Parametry

*right*  
 Valarray lub wartość taka sama jak w przypadku operand valarray, który jest należy odejmować, element-wise, operand valarray typu elementu.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są element-wise różnica operand valarray i *prawo*.

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

Dzieli operand valarray element-wise elementów określonej tablicy valarray lub wartości typu elementu.

```cpp
valarray<Type>& operator/=(const valarray<Type>& right);

valarray<Type>& operator/=(const Type& right);
```

### <a name="parameters"></a>Parametry

*right*  
 Valarray lub wartość taka sama jak w przypadku operand valarray, który ma być podzielone, element-wise, operand valarray typu elementu.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są element-wise iloraz operand valarray podzielona przez *prawo*.

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

Przypisuje valarray, w których wartości są określone, bezpośrednio lub jako część innego tablicy valarray lub slice_array —, gslice_array —, mask_array — lub indirect_array — elementy.

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

*right*  
 Valarray, który ma zostać skopiowana do operand valarray.

*Val*  
 Wartość do przypisania do elementów tworzonej tablicy operand valarray.

*_Slicearray*  
 Slice_array — ma zostać skopiowana do operand valarray.

*_Gslicearray*  
 Gslice_array — ma zostać skopiowana do operand valarray.

*_Maskarray*  
 Mask_array — ma zostać skopiowana do operand valarray.

*_Indarray*  
 Indirect_array — ma zostać skopiowana do operand valarray.

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator członkowski zastępuje kontrolowanej sekwencji kopię sekwencji kontrolowanej przez *prawo*.

Drugi operator elementu członkowskiego jest taka sama jak pierwszy, ale z [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

Trzeci operator składowy zastępuje kopię każdego elementu w kontrolowanej sekwencji *val*.

Pozostałe operatorach składowych zastąpić te elementy kontrolowanej sekwencji wybranych przez ich argumentów, które są generowane tylko przez [operator&#91;&#93;](#op_at).

Jeśli wartość elementu członkowskiego, w kolejności zastępowania kontrolowane zależy od elementu członkowskiego w kontrolowanej sekwencji początkowej, wynik jest niezdefiniowany.

### <a name="remarks"></a>Uwagi

Jeśli długość kontrolowanej sekwencji zmieni się, wynik jest zazwyczaj niezdefiniowane. W tej implementacji jednak efekt jest jedynie do unieważnienia wszystkie wskaźniki lub odwołania do elementów w kontrolowanej sekwencji.

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

Zwraca odwołanie do elementu lub jego wartość w określonym indeksie lub określony podzbiór.

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

*_Off*  
 Indeks elementu, który ma zostać przypisana wartość.

*_Slicearray*  
 Tablica typu slice_array z tablicy valarray, określający podzbiór, która zostanie wybrana lub powrót do nowej tablicy valarray.

*_Gslicearray*  
 Tablica typu gslice_array z tablicy valarray, określający podzbiór, która zostanie wybrana lub powrót do nowej tablicy valarray.

*_Boolarray*  
 Bool_array valarray, określający podzbiór, która zostanie wybrana lub powrót do nowej tablicy valarray.

*_Indarray*  
 Indirect_array — z tablicy valarray, określający podzbiór, która zostanie wybrana lub powrót do nowej tablicy valarray.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu lub jego wartość w określonym indeksie lub określony podzbiór.

### <a name="remarks"></a>Uwagi

Operator elementów członkowskich jest przeciążona, aby podać kilka sposobów zaznaczania elementów spośród kontrolowanych przez  <strong>\*to</strong>. Pierwsza grupa pięć operatorach składowych pracy w połączeniu z różnych przeciążenia [operator =](#op_eq) (i inne operatory przypisywanie) umożliwia selektywne zastąpienia (dzielenie) kontrolowanej sekwencji. Wybrane elementy, musi istnieć.

Gdy kompilowany przy użyciu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowana jako 1 lub 2, błąd czasu wykonywania występuje, jeśli użytkownik podejmie próbę uzyskania dostępu do elementu poza granicami tablicy valarray.  Zobacz [Checked Iterators](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

### <a name="example"></a>Przykład

Zobacz przykłady dla [slice::slice](../standard-library/slice-class.md#slice) i [gslice::gslice](../standard-library/gslice-class.md#gslice) przykładowy sposób deklarowania i użyj operatora.

## <a name="op_xor_eq"></a>  valarray::operator ^ =

Uzyskuje operator wyłączny element-wise logiczne or ( **XOR**) tablicy przy użyciu określonej tablicy valarray lub wartości typu elementu.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>Parametry

*right*  
 Valarray lub wartości typu elementu, taka sama jak w przypadku operand valarray, który ma być łączone, element-wise, przez wyłącznie logiczne **XOR** z operand valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są wyłączne element-wise, logiczne **XOR** z operand valarray i *prawo*.

### <a name="remarks"></a>Uwagi

Wyłączne logiczny lub są nazywane **XOR**, charakteryzuje się następującą semantyką: dane elementy *e*1 i *e*2, *e*1  **XOR** *e*2 jest **true** Jeśli dokładnie jeden z elementów ma wartość true; **false** Jeśli oba te elementy są fałszywe lub jeśli spełnione są oba te elementy.

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

Uzyskuje bitowe `OR` elementów w tablicy przy użyciu odpowiednie elementy w określonej tablicy valarray lub z wartością typu elementu.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>Parametry

*right*  
 Valarray lub wartości typu elementu, taka sama jak w przypadku operand valarray, który ma być łączone, element-wise, przez operatora testu koniunkcji `OR` z operand valarray.

### <a name="return-value"></a>Wartość zwracana

Valarray, której elementy są element-wise bitowe `OR` z operand valarray przez *prawo*.

### <a name="remarks"></a>Uwagi

Operacja bitowa należy używać tylko do manipulowania bitów **char** i **int** typów danych i wariantów a nie w systemie **float**, **double**, **longdouble**, **void**, **bool**, lub inne, bardziej złożone typy danych.

Operatora testu koniunkcji `OR` ma tej samej tabeli prawdziwych danych jako logiczny `OR` , ale ma zastosowanie do typu danych na poziomie pojedynczych bitów. Biorąc pod uwagę bitów *b*1 i *b*2, *b*1 `OR` *b*2 jest **true** Jeśli co najmniej jeden z bitów jest wartość true; **false** Jeśli oba bity mają wartość false.

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

Jednoargumentowy operator, który uzyskuje bitowe `NOT` wartości każdego elementu w tablicy valarray.

```cpp
valarray<Type> operator~() const;
```

### <a name="return-value"></a>Wartość zwracana

Valarray — wartości logiczne, które są operatora testu koniunkcji `NOT` wartości elementu operand valarray.

### <a name="remarks"></a>Uwagi

Operacja bitowa należy używać tylko do manipulowania bitów **char** i **int** typów danych i wariantów a nie w systemie **float**, **double**, **longdouble**, **void**, **bool** lub innych, bardziej złożone typy danych.

Operatora testu koniunkcji `NOT` ma tej samej tabeli prawdziwych danych jako logiczny `NOT` , ale ma zastosowanie do typu danych na poziomie pojedynczych bitów. Biorąc pod uwagę bit *b*, ~ *b* ma wartość true Jeśli *b* ma wartość FAŁSZ i wartość false, jeśli *b* ma wartość true. Logiczny **nie**[operatora!](#op_not) ma zastosowanie na poziomie elementu wszystkich wartości niezerowych co inwentaryzacji **true**, a wynik jest valarray wartościami logicznymi. Operatora testu koniunkcji `NOToperator~`, z kolei może doprowadzić do tablicy valarray, o wartości innej niż 0 lub 1, w zależności od wyniku operacji na poziomie bitowym.

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

Liczba elementów w tablicy valarray zmienia się na określoną liczbę.

```cpp
void resize(
    size_t _Newsize);

void resize(
    size_t _Newsize,
    const Type val);
```

### <a name="parameters"></a>Parametry

*_Newsize*  
 Liczba elementów w tablicy valarray o zmienionym rozmiarze.

*Val*  
 Wartość do elementów tworzonej tablicy valarray o zmienionym rozmiarze.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego inicjuje elementy przy użyciu ich domyślnego konstruktora.

Wszystkie wskaźniki lub odwołania do elementów w kontrolowanej sekwencji są unieważniane.

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie valarray::resize funkcja elementu członkowskiego.

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

Przenosi wszystkie elementy w tablicy valarray przez określoną liczbę miejsc.

```cpp
valarray<Type> shift(int count) const;
```

### <a name="parameters"></a>Parametry

*Liczba*  
 Liczba miejsc, które elementy są jest przesuwany do przodu.

### <a name="return-value"></a>Wartość zwracana

Nowa tablica valarray, w którym wszystkie elementy zostały przeniesione *liczba* pozycje w kierunku początku tablicy valarray, pozostanie w odniesieniu do ich pozycje w tablicy valarray operand.

### <a name="remarks"></a>Uwagi

Dodatnia wartość *liczba* przenosi elementy w lewo *liczba* miejsc, zerowego wypełnienia.

Wartość ujemna *liczba* przenosi elementy w prawo *liczba* miejsc, zerowego wypełnienia.

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

Wyszukuje liczbę elementów w tablicy valarray.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tablicy valarray operand.

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie valarray::size funkcja elementu członkowskiego.

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

Określa sumę wszystkich elementów w tablicy valarray, o długości wartość różną od zera.

```cpp
Type sum() const;
```

### <a name="return-value"></a>Wartość zwracana

Suma elementów tworzonej tablicy operand valarray.

### <a name="remarks"></a>Uwagi

Jeśli długość jest większa niż jeden, funkcja elementu członkowskiego dodaje wartości do sumy, stosując `operator+=` między parami elementów klasy `Type`, których operator w związku z tym, musi być podana dla elementów typu `Type`.

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

Zamienia elementy z dwóch `valarray`s.

```cpp
void swap(valarray& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*right*|A `valarray` zawierająca elementy, które mają być zamienione.|

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia kontrolowanej sekwencji między `*this` i *prawo*. Robi to w stałym czasie, wyniku weryfikacji zgłasza wyjątek bez wyjątków, a jego unieważnienie nie odwołania wskaźniki i Iteratory, które wyznaczają elementy dwóch sekwencji kontrolowanej.

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

*Liczba*  
 Liczba elementów, które mają się znaleźć w tablicy valarray.

*Val*  
 Wartość, która ma być użyta do inicjowania elementów w tablicy valarray.

*PTR*  
 Wskaźnik do wartości, które mają użyte do inicjowania elementów w tablicy valarray.

*po prawej stronie*  
 Istniejąca tablica valarray do zainicjowania nowej tablicy valarray.

*SliceArray*  
 Tablica typu slice_array, której wartości elementów mają być użyte do inicjowania elementów tworzonej tablicy valarray.

*GsliceArray*  
 Tablica typu gslice_array, której wartości elementów mają być użyte do inicjowania elementów tworzonej tablicy valarray.

*MaskArray*  
 Tablica typu mask_array, której wartości elementów mają być użyte do inicjowania elementów tworzonej tablicy valarray.

*IndArray*  
 Tablica typu indirect_array, której wartości elementów mają być użyte do inicjowania elementów tworzonej tablicy valarray.

*IList*  
 Lista initializer_list zawierająca elementy do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy (domyślny) konstruktor inicjuje obiekt jako pustą tablicę. Następne trzy konstruktory inicjują obiekt jako tablicę *liczba* elementów w następujący sposób:

- Dla jawnego `valarray(size_t Count)`, każdy element jest inicjowany przy użyciu konstruktora domyślnego.

- Aby uzyskać `valarray(const Type& Val, Count)`, każdy element jest inicjowany z *Val*.

- Aby uzyskać `valarray(const Type* Ptr, Count)`, do elementu w położeniu `I` jest inicjowany za pomocą `Ptr`[ `I`].

Każdy pozostały Konstruktor inicjuje obiekt do tablicy valarray\<typ > obiektu określonego przez podzbiór określony w argumencie.

Ostatni Konstruktor jest taki sam jak dalej, aby w ostatniej, ale z [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

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

Typ, który reprezentuje typ elementu przechowywanego w tablicy valarray.

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
\* Output:
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).
The decalared value_type Right is: 10
The resulting valarray is:  ( 0 -10 20 -10 40 -10 60 -10 80 -10 ).
*\
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
