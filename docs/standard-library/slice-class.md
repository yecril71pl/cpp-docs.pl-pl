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
ms.openlocfilehash: 830e345eb7522cef44dbf6e727a976fb79c1e081
ms.sourcegitcommit: 49cf365176557456f56c994e06ea1a38f73e938b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937435"
---
# <a name="slice-class"></a>slice — Klasa

Klasa narzędzi do valarray, która jest używana do definiowania jednowymiarowych podzestawów nadrzędnej valarray. Jeśli valarray jest traktowany jako dwuwymiarowa macierz ze wszystkimi elementami w tablicy, wycinek zostanie wyodrębniony w jednym wymiarze z tablicy dwuwymiarowej.

## <a name="remarks"></a>Uwagi

Klasa przechowuje parametry, które opisują obiekt typu [slice_array](../standard-library/slice-array-class.md) podzbiór elementu valarray jest pośrednio skonstruowany, gdy obiekt klasy wycinka jest wyświetlany jako argument dla obiektu klasy [valarray](../standard-library/valarray-class.md#op_at) **\<typu >** . Przechowywane wartości określające podzbiór wybrany z elementu nadrzędnego valarray obejmują:

- Początkowy indeks w valarray.

- Łączna długość lub liczba elementów wycinka.

- Krok lub odległość między kolejnymi indeksami elementów w valarray.

Jeśli zestaw zdefiniowany przez wycinek jest podzbiorem stałej valarray, wycinek jest nowym valarray. Jeśli zestaw zdefiniowany przez wycinek jest podzbiorem niestałego valarray, wówczas wycinek ma semantykę odwołania do oryginalnego valarray. Mechanizm oceny dla niestałe valarrays oszczędza czas i pamięć.

Operacje na valarrays są gwarantowane tylko wtedy, gdy podzbiory źródłowe i docelowe zdefiniowane przez wycinki są różne i wszystkie indeksy są prawidłowe.

### <a name="constructors"></a>Konstruktorzy

|Konstruktor|Opis|
|-|-|
|[Cinek](#slice)|Definiuje podzestaw `valarray`, który składa się z wielu elementów, które są równej odległości od siebie i zaczyna się od określonego elementu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[zmienia](#size)|Znajduje liczbę elementów w wycinku `valarray`.|
|[start](#start)|Znajduje początkowy indeks wycinka `valarray`.|
|[tabela](#stride)|Znajduje odległość między elementami w wycinku `valarray`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray >

**Przestrzeń nazw:** std

## <a name="size"></a>plasterek:: size

Znajduje liczbę elementów w wycinku valarray.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Wartość zwrócona

Liczba elementów w wycinku elementu valarray.

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

## <a name="slice"></a>plasterek:: Slice

Definiuje podzestaw elementu valarray, który składa się z wielu elementów, które są równej odległości od siebie i zaczyna się od określonego elementu.

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

*krok*\
Odległość między elementami w podzbiorze.

### <a name="return-value"></a>Wartość zwrócona

Konstruktor domyślny przechowuje zera dla początkowego indeksu, całkowitej długości i krok. Drugi Konstruktor przechowuje *_StartIndex* w indeksie początkowym, *_LEN* dla łącznej długości i *krok* dla tego elementu.

### <a name="remarks"></a>Uwagi

Krok może być ujemny.

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

## <a name="start"></a>Slice:: Start

Znajduje początkowy indeks wycinka elementu valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Wartość zwrócona

Początkowy indeks wycinka elementu valarray.

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

## <a name="stride"></a>Slice:: krok

Znajduje odległość między elementami w wycinku valarray.

```cpp
size_t stride() const;
```

### <a name="return-value"></a>Wartość zwrócona

Odległość między elementami w wycinku valarray.

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
