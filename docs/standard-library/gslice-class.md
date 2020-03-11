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
ms.openlocfilehash: 9290fabc86ffbdb051b7c61fe1600cd2f7f17dca
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866257"
---
# <a name="gslice-class"></a>gslice — Klasa

Klasa narzędzi do valarray, która jest używana do definiowania wielowymiarowych podzestawów valarray. Jeśli valarray jest traktowany jako wielowymiarowa macierz ze wszystkimi elementami w tablicy, wycinek zostanie wyodrębniony z tablicy wielowymiarowej.

## <a name="remarks"></a>Uwagi

Klasa przechowuje parametry, które opisują obiekt typu [gslice_array](../standard-library/gslice-array-class.md). Podzestaw elementu valarray jest pośrednio skonstruowany, gdy obiekt klasy gslice pojawia się jako argument dla obiektu klasy [valarray](../standard-library/valarray-class.md#op_at) **\<typu >** . Przechowywane wartości określające podzbiór wybrany z elementu nadrzędnego valarray obejmują:

- Indeks początkowy.

- Wektor długości klasy `valarray<size_t>`.

- Wektora krok klasy `valarray<size_t>`.

Dwa wektory muszą mieć tę samą długość.

Jeśli zestaw zdefiniowany przez gslice jest podzbiorem stałej valarray, wówczas gslice jest nowym valarray. Jeśli zestaw zdefiniowany przez gslice jest podzbiorem niestałej valarray, wówczas gslice ma semantykę odwołania do oryginalnego valarray. Mechanizm oceny dla niestałe valarrays oszczędza czas i pamięć.

Operacje na valarrays są gwarantowane tylko wtedy, gdy źródłowe i docelowe podzestawy zdefiniowane przez gslices są różne i wszystkie indeksy są prawidłowe.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[gslice](#gslice)|Definiuje podzestaw `valarray`, który składa się z wielu wycinków `valarray`, które zaczynają się od określonego elementu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[zmienia](#size)|Znajduje wartości tablicy, określając liczbę elementów w ogólnym wycinku `valarray`.|
|[start](#start)|Znajduje początkowy indeks ogólnego wycinka `valarray`.|
|[tabela](#stride)|Znajduje odległość między elementami w ogólnym wycinku `valarray`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray >

**Przestrzeń nazw:** std

## <a name="gslice"></a>gslice:: gslice

Klasa narzędzi do valarray, która jest używana do definiowania wielowymiarowych wycinków valarray.

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

Konstruktor domyślny przechowuje zero dla indeksu początkowego i wektorów o zerowej długości dla wektorów długości i kroków. Drugi Konstruktor przechowuje *_StartIndex* dla początkowego indeksu, *_LenArray* dla tablicy długość i *_IncArray* dla tablicy kroków.

### <a name="remarks"></a>Uwagi

**gslice** definiuje podzestaw valarray, który składa się z wielu wycinków valarray, które rozpoczynają się w tym samym określonym elemencie. Możliwość używania tablic do definiowania kilku wycinków jest jedyną różnicą między `gslice` i [Slice:: Slice](../standard-library/slice-class.md#slice). Pierwszy plasterek ma pierwszy element z indeksem *_StartIndex*, liczbę elementów określoną przez pierwszy element *_LenArray*i krok podany przez pierwszy element *_IncArray*. Następny zestaw ortogonalnych wycinków ma pierwsze elementy określone przez pierwszy plasterek. Drugi element *_LenArray* określa liczbę elementów. Krok jest określony przez drugi element *_IncArray*. Trzeci wymiar wycinków będzie przyjmować elementy dwuwymiarowej tablicy jako elementy początkowe i działać analogicznie

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

## <a name="size"></a>gslice:: size

Znajduje wartości tablicy, określając liczbę elementów w ogólnym wycinku valarray.

```cpp
valarray<size_t> size() const;
```

### <a name="return-value"></a>Wartość zwracana

Valarray określający liczbę elementów w każdym wycinku ogólnego wycinka valarray.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca przechowywane długości wycinków.

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

## <a name="start"></a>gslice:: Start

Znajduje początkowy indeks ogólnego wycinka valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Wartość zwracana

Początkowy indeks ogólnego wycinka valarray.

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

## <a name="stride"></a>gslice:: krok

Znajduje odległość między elementami w ogólnym wycinku valarray.

```cpp
valarray<size_t> stride() const;
```

### <a name="return-value"></a>Wartość zwracana

Valarray określający odległość między elementami w każdym wycinku ogólnego wycinka valarray.

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

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
