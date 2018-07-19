---
title: gslice — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::gslice
- valarray/std::gslice::size
- valarray/std::gslice::start
- valarray/std::gslice::stride
dev_langs:
- C++
helpviewer_keywords:
- std::gslice [C++]
- std::gslice [C++], size
- std::gslice [C++], start
- std::gslice [C++], stride
ms.assetid: f47cffd0-ea59-4b13-848b-7a5ce1d7e2a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5c47f91a3e029175d40bd1a762fb6e6ff527ee7
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955817"
---
# <a name="gslice-class"></a>gslice — Klasa

Klasy narzędzi do tablicy valarray, który jest używany do definiowania wielowymiarowe podzbiór tablicy valarray. Jeśli tablica valarray jest traktowany jako wielowymiarowe macierzy przy użyciu wszystkich elementów w tablicy, wycinek wyodrębnia wektor z tablicy wielowymiarowej.

## <a name="remarks"></a>Uwagi

Klasa przechowuje parametrów, charakteryzujące się do obiektu typu [gslice_array —](../standard-library/gslice-array-class.md). Podzbiór tablicy valarray pośrednio jest tworzony, gdy obiekt gslice — klasa pojawi się jako argument dla obiektu klasy [valarray](../standard-library/valarray-class.md#op_at)**\<typ >**. Przechowywane wartości, które określają podzbioru wybrana w zaufanym valarray nadrzędnego obejmują:

- Indeks początkowy.

- Długość wektora klasy `valarray<size_t>`.

- Wektor stride klasy `valarray<size_t>`.

Dwa wektory muszą mieć tę samą długość.

Jeśli zestawu zdefiniowanego przez gslice — jest podzbiorem stałej tablicy valarray, gslice — jest nowej tablicy valarray. Jeśli zestawu zdefiniowanego przez gslice — jest podzbiorem stałymi valarray, gslice — ma semantyki odwołania do oryginalnego tablicy valarray. Mechanizm oceny dla nieunikatowego valarrays oszczędza czas i pamięci.

Operacje na valarrays jest gwarantowane tylko wtedy, gdy podzestawy źródłowym i docelowym, zdefiniowane przez gslices różniące się od siebie i wszystkich indeksów są prawidłowe.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[gslice](#gslice)|Definiuje podzbiór `valarray` składający się z wielu wycinków `valarray` że wszystkie zaczynają się od określonego elementu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Rozmiar](#size)|Umożliwia znalezienie wartości tablicy, określenie liczby elementów w ogólne wycinek `valarray`.|
|[start](#start)|Znajduje indeks początkowy ogólne wycinek `valarray`.|
|[stride](#stride)|Odległość między elementami w wycinku ogólne `valarray`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray >

**Namespace:** standardowe

## <a name="gslice"></a>  gslice::gslice

Klasy narzędzi do tablicy valarray, który jest używany do definiowania wycinków wielowymiarowej tablicy valarray.

```cpp
gslice();

gslice(
    size_t _StartIndex,
    const valarray<size_t>& _LenArray,
    const valarray<size_t>& _IncArray);
```

### <a name="parameters"></a>Parametry

*_StartIndex* valarray indeks pierwszego elementu w podzbiorze.

*_LenArray* tablicy, określając liczbę elementów w każdym wycinkiem.

*_IncArray* tablicy, określając krok w każdym wycinkiem.

### <a name="return-value"></a>Wartość zwracana

Domyślny konstruktor przechowuje zera indeks początkowy i czynnikami ułatwiającymi wektorów długości i stride o zerowej długości. Drugi Konstruktor magazynów *_StartIndex* począwszy od indeksu *_LenArray* tablicy długości i *_IncArray* dla tablicy krok.

### <a name="remarks"></a>Uwagi

**gslice —** definiuje podzbiór tablicy valarray, który składa się z wielu wycinków tablicy valarray, rozpoczyna się w tym samym określony element. Możliwość używania tablic do definiowania wielu wycinków jest jedyną różnicą między `gslice` i [slice::slice](../standard-library/slice-class.md#slice). Pierwszy wycinek ma pierwszego elementu z indeksu *_StartIndex*, liczbę elementów w określonym przez pierwszy element *_LenArray*i stride, biorąc pod uwagę, pierwszego elementu *_IncArray* . Kolejny zbiór prostopadły wycinki ma pierwszych elementów z podanym przez pierwszy wycinek. Drugi element *_LenArray* określa liczbę elementów. Drugi element wynosi stride *_IncArray*. Trzeci wymiar wycinków będzie wykonać elementy dwuwymiarową tablicę jako wyjścia elementy i kontynuować analogicznie

### <a name="example"></a>Przykład

```cpp
// gslice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:" << endl << "(";
   for ( i = 0 ; i < 20 ; i++ )
      cout << " " << va [ i ];
   cout << " )" << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];

   cout << "The valarray for vaGSlice is vaResult:" << endl
        << "va[vaGSlice] = (";

   for ( i = 0 ; i < 8 ; i++ )
      cout << " " << vaResult [ i ];
   cout << ")" << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 )
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19)
```

## <a name="size"></a>  gslice::size

Umożliwia znalezienie wartości tablicy, określając liczby elementów w ogólne wycinek tablicy valarray.

```cpp
valarray<size_t> size() const;
```

### <a name="return-value"></a>Wartość zwracana

Valarray — Określanie liczby elementów w każdym wycinkiem ogólne wycinek tablicy valarray.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca przechowywaną długości wycinki.

### <a name="example"></a>Przykład

```cpp
// gslice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> sizeGS = vaGSlice.size ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The size of vaResult is:"
        << "\n vaGSlice.size ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << sizeGS[ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The size of the valarray is: 20.

The valarray for vaGSlice is vaResult:
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The size of vaResult is:
 vaGSlice.size ( ) = ( 4 4 ).
```

## <a name="start"></a>  gslice::Start

Znajduje indeks początkowy ogólne wycinek tablicy valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks początkowy ogólne wycinek tablicy valarray.

### <a name="example"></a>Przykład

```cpp
// gslice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   size_t vaGSstart = vaGSlice.start ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The index of the first element of vaResult is: "
        << vaGSstart << "." << endl;
}
```

```Output
The operand valarray va is:
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The index of the first element of vaResult is: 0.
```

## <a name="stride"></a>  gslice::STRIDE

Umożliwia znalezienie odległości między elementami w ogólne wycinek tablicy valarray.

```cpp
valarray<size_t> stride() const;
```

### <a name="return-value"></a>Wartość zwracana

Valarray — Określanie odległości między elementami w każdym wycinkiem ogólne wycinek tablicy valarray.

### <a name="example"></a>Przykład

```cpp
// gslice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for (i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> strideGS = vaGSlice.stride ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The strides of vaResult are:"
        << "\n vaGSlice.stride ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << strideGS[ i ] << " ";
   cout << ")." << endl;

}
```

```Output
The operand valarray va is:
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The strides of vaResult are:
 vaGSlice.stride ( ) = ( 7 4 ).
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
