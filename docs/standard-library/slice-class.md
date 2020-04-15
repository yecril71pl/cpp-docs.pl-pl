---
title: slice — Klasa
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice
- valarray/std::slice::size
- valarray/std::slice::start
- valarray/std::slice::stride
helpviewer_keywords:
- std::slice [C++]
- std::slice [C++], size
- std::slice [C++], start
- std::slice [C++], stride
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
ms.openlocfilehash: 05f87cbb6061e205f9731d2a903ce52a2482b214
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336720"
---
# <a name="slice-class"></a>slice — Klasa

Klasa narzędzia do valarray, która jest używana do definiowania jednowymiarowych podzbiorów nadrzędnej valarray. Jeśli valarray jest uważany za macierz dwuwymiarową ze wszystkimi elementami w tablicy, a następnie plasterek wyodrębnia wektora w jednym wymiarze z tablicy dwuwymiarowej.

## <a name="remarks"></a>Uwagi

Klasa przechowuje parametry, które charakteryzują obiekt typu [slice_array](../standard-library/slice-array-class.md) Podzbiór valarray jest pośrednio konstruowany, gdy obiekt plasterka klasy pojawia się jako argument dla obiektu [klasy valarray](../standard-library/valarray-class.md#op_at)**\<Typ>**. Przechowywane wartości, które określają podzbiór wybrany z nadrzędnej valarray obejmują:

- Indeks początkowy w valarray.

- Całkowita długość lub liczba elementów w plasterku.

- Krok lub odległość między kolejnymi wskaźnikami elementów w valarray.

Jeśli zestaw zdefiniowany przez plasterek jest podzbiorem stałej valarray, wówczas plasterek jest nową valarray. Jeśli zestaw zdefiniowany przez plasterek jest podzbiorem niestałej valarray, wówczas plasterek ma semantykę odniesienia do oryginalnej valarray. Mechanizm oceny niestających valarrays oszczędza czas i pamięć.

Operacje na valarrays są gwarantowane tylko wtedy, gdy podzbiory źródłowe i docelowe zdefiniowane przez wycinki są różne i wszystkie indeksy są prawidłowe.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Plasterek](#slice)|Definiuje podzbiór `valarray` a, który składa się z wielu elementów, które są równe odległości od siebie i które zaczynają się od określonego elementu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Rozmiar](#size)|Znajduje liczbę elementów w wycinku `valarray`pliku .|
|[Uruchomić](#start)|Znajduje indeks początkowy wycinka `valarray`.|
|[Kroku](#stride)|Znajduje odległość między elementami w `valarray`wycinku pliku .|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray>

**Przestrzeń nazw:** std

## <a name="slicesize"></a><a name="size"></a>plasterek::size

Znajduje liczbę elementów w wycinku valarray.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w kawałku valarray.

### <a name="example"></a>Przykład

```cpp
// slice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA, sizeVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   sizeVAR = vaSlice.size ( );
   cout << "The size of slice vaSlice is: "
        << sizeVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The size of the valarray is: 20.

The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The size of slice vaSlice is: 6.
```

## <a name="sliceslice"></a><a name="slice"></a>plasterek::plasterek

Definiuje podzbiór valarray, który składa się z wielu elementów, które są równe odległości od siebie i które zaczynają się od określonego elementu.

```cpp
slice();

slice(
    size_t _StartIndex,
    size_t _Len,
    size_t stride);
```

### <a name="parameters"></a>Parametry

*_StartIndex*\
Indeks valarray pierwszego elementu w podzbiorze.

*_Len*\
Liczba elementów w podzbiorze.

*Kroku*\
Odległość między elementami w podzbiorze.

### <a name="return-value"></a>Wartość zwracana

Domyślny konstruktor przechowuje zera dla indeksu początkowego, całkowita długość i krok. Drugi konstruktor przechowuje *_StartIndex* dla indeksu początkowego, *_Len* dla całkowitej długości i *kroku* dla kroku.

### <a name="remarks"></a>Uwagi

Krok może być negatywny.

### <a name="example"></a>Przykład

```cpp
// slice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  2 * (i + 1 );

   cout << "The operand valarray va is:\n( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 1 , 7 , 3 );
   vaResult = va [ vaSlice ];

   cout << "\nThe slice of valarray va is vaResult:"
        << "\nva[slice( 1, 7, 3)] = ( ";
      for ( i = 0 ; i < 7 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
( 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 ).

The slice of valarray va is vaResult:
va[slice( 1, 7, 3)] = ( 4 10 16 22 28 34 40 ).
```

## <a name="slicestart"></a><a name="start"></a>plasterek::start

Znajduje indeks początkowy wycinka valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks początkowy wycinka valarray.

### <a name="example"></a>Przykład

```cpp
// slice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t startVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] = i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   startVAR = vaSlice.start ( );
   cout << "The start index of slice vaSlice is: "
        << startVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The start index of slice vaSlice is: 3.
```

## <a name="slicestride"></a><a name="stride"></a>plasterek::krok

Znajduje odległość między elementami w wycinku valarray.

```cpp
size_t stride() const;
```

### <a name="return-value"></a>Wartość zwracana

Odległość między elementami w kawałku valarray.

### <a name="example"></a>Przykład

```cpp
// slice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t strideVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  3 * ( i + 1 );

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 4 , 5 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 4, 5, 3)] =\n ( ";
      for ( i = 0 ; i < 5 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   strideVAR = vaSlice.stride ( );
   cout << "The stride of slice vaSlice is: "
        << strideVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45 48 51 54 57 60 ).
The slice of valarray va is vaResult = va[slice( 4, 5, 3)] =
( 15 24 33 42 51 ).
The stride of slice vaSlice is: 3.
```

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
