---
title: gslice — Klasa
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice
- valarray/std::gslice::size
- valarray/std::gslice::start
- valarray/std::gslice::stride
helpviewer_keywords:
- std::gslice [C++]
- std::gslice [C++], size
- std::gslice [C++], start
- std::gslice [C++], stride
ms.assetid: f47cffd0-ea59-4b13-848b-7a5ce1d7e2a3
ms.openlocfilehash: 07c987fb08a213bb66da628bec3021a3bf9ba24a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370625"
---
# <a name="gslice-class"></a>gslice — Klasa

Klasa użytkowa do valarray, która jest używana do definiowania wielowymiarowych podzbiorów valarray. Jeśli valarray jest uważany za macierz wielowymiarową ze wszystkimi elementami w tablicy, a następnie plasterek wyodrębnia wektor z tablicy wielowymiarowej.

## <a name="remarks"></a>Uwagi

Klasa przechowuje parametry, które charakteryzują obiekt typu [gslice_array](../standard-library/gslice-array-class.md). Podzbiór valarray jest pośrednio konstruowany, gdy obiekt gslice klasy pojawia się jako argument dla obiektu klasy [valarray](../standard-library/valarray-class.md#op_at)**\<Typ>**. Przechowywane wartości, które określają podzbiór wybrany z nadrzędnej valarray obejmują:

- Indeks początkowy.

- Wektor długości klasy `valarray<size_t>`.

- Wektor kroków klasy `valarray<size_t>`.

Dwa wektory muszą mieć taką samą długość.

Jeśli zestaw zdefiniowany przez gslice jest podzbiorem stałej valarray, gslice jest nową valarray. Jeśli zestaw zdefiniowany przez gslice jest podzbiorem niestałej valarray, wówczas gslice ma semantykę odniesienia do oryginalnej valarray. Mechanizm oceny niestających valarrays oszczędza czas i pamięć.

Operacje na valarrays są gwarantowane tylko wtedy, gdy podzbiory źródłowe i docelowe zdefiniowane przez gslices są różne i wszystkie indeksy są prawidłowe.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Gslice](#gslice)|Definiuje podzbiór `valarray` a, który składa się `valarray` z wielu wycinków, które wszystkie zaczynają się od określonego elementu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Rozmiar](#size)|Znajduje wartości tablicy określające liczbę elementów w `valarray`ogólnym wycinku programu .|
|[Uruchomić](#start)|Znajduje indeks początkowy ogólnego wycinka `valarray`.|
|[Kroku](#stride)|Znajduje odległość między elementami w `valarray`ogólnym wycinku pliku .|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray>

**Przestrzeń nazw:** std

## <a name="gslicegslice"></a><a name="gslice"></a>gslice::gslice

Klasa narzędzia do valarray, która jest używana do definiowania wielowymiarowych wycinków valarray.

```cpp
gslice();

gslice(
    size_t _StartIndex,
    const valarray<size_t>& _LenArray,
    const valarray<size_t>& _IncArray);
```

### <a name="parameters"></a>Parametry

*_StartIndex*\
Indeks valarray pierwszego elementu w podzbiorze.

*_LenArray*\
Tablica określająca liczbę elementów w każdym wycinku.

*_IncArray*\
Tablica określająca krok w każdym wycinku.

### <a name="return-value"></a>Wartość zwracana

Domyślny konstruktor przechowuje zero dla indeksu początkowego i wektory o zerowej długości dla wektorów długości i kroku. Drugi konstruktor przechowuje *_StartIndex* dla indeksu początkowego, *_LenArray* dla tablicy długości i *_IncArray* dla tablicy kroku.

### <a name="remarks"></a>Uwagi

**gslice** definiuje podzbiór valarray, który składa się z wielu wycinków valarray, że każdy rozpoczyna się w tym samym określonym elemencie. Możliwość używania tablic do definiowania wielu plasterków `gslice` jest jedyną różnicą między [i plasterkiem::slice](../standard-library/slice-class.md#slice). Pierwszy wycinek ma pierwszy element z indeksem *_StartIndex*, liczba elementów określonych przez pierwszy element *_LenArray*i krok podany przez pierwszy element *_IncArray*. Następny zestaw plasterków ortogonalnych ma pierwsze elementy podane przez pierwszy plasterek. Drugi element *_LenArray* określa liczbę elementów. Krok jest podany przez drugi element *_IncArray*. Trzeci wymiar wycinków wziąłby elementy tablicy dwuwymiarowej jako elementy początkowe i postępować analogicznie

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

## <a name="gslicesize"></a><a name="size"></a>gslice::size

Znajduje wartości tablicy określające liczbę elementów w ogólnym wycinku valarray.

```cpp
valarray<size_t> size() const;
```

### <a name="return-value"></a>Wartość zwracana

Valarray określający liczbę elementów w każdym wycinku ogólnego wycinka valarray.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca przechowywane długości plasterków.

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

## <a name="gslicestart"></a><a name="start"></a>gslice::start

Znajduje indeks początkowy ogólnego wycinka valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks początkowy ogólnego wycinka valarray.

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

## <a name="gslicestride"></a><a name="stride"></a>gslice::krok

Znajduje odległość między elementami w ogólnym wycinku valarray.

```cpp
valarray<size_t> stride() const;
```

### <a name="return-value"></a>Wartość zwracana

Valarray określający odległości między elementami w każdym wycinku ogólnego wycinka valarray.

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

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
