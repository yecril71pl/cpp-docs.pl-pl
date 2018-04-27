---
title: Slice — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- valarray/std::slice
- valarray/std::slice::size
- valarray/std::slice::start
- valarray/std::slice::stride
dev_langs:
- C++
helpviewer_keywords:
- std::slice [C++]
- std::slice [C++], size
- std::slice [C++], start
- std::slice [C++], stride
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb28a7f309566d6bf4c296190cd65e77fbadc4ac
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="slice-class"></a>slice — Klasa

Klasa narzędzia valarray —, który służy do definiowania jednowymiarowa podzbiór nadrzędnej valarray —. Jeśli valarray — jest traktowany jako macierz dwuwymiarowa z wszystkich elementów w tablicy, wycinka wyodrębnia wektor w jednym wymiarze poza tablicą dwuwymiarową.

## <a name="remarks"></a>Uwagi

Klasa przechowuje parametry, charakteryzujące typu obiektu [slice_array —](../standard-library/slice-array-class.md) podzbiór valarray — pośrednio jest tworzony, gdy obiekt klasy wycinka pojawia się jako argument dla obiekt klasy [valarray — ](../standard-library/valarray-class.md#op_at)  **\<Typu >**. Przechowywane wartości, które określają podzestawu wybrany z valarray — nadrzędnego obejmują:

- Indeks początkowy w valarray —.

- Łączna długość lub liczba elementów w wycinka.

- Krok lub odległość między kolejnych indeksów elementów w valarray —.

Jeśli zestaw zdefiniowanych przez wycinek jest podzbiorem stałej valarray —, wycinek jest nowy valarray —. Jeśli zestaw zdefiniowanych przez wycinek jest podzbiorem nieunikatowego valarray —, wycinek ma semantykę odwołania do oryginalnego valarray —. Mechanizm oceny nieunikatowego valarrays oszczędza czas i pamięci.

Operacje na valarrays dotrą tylko wtedy, gdy podzestawy źródłowym i docelowym, zdefiniowane przez wycinków są unikatowe i wszystkich indeksów są prawidłowe.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Wycinek](#slice)|Definiuje ona podzestaw `valarray` składający się z liczbą elementów, które są takie same odległości i który rozpoczęli określonego elementu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[Rozmiar](#size)|Wyszukuje liczbę elementów w wycinek `valarray`.|
|[start](#start)|Znajduje indeks początkowy wycinek `valarray`.|
|[stride](#stride)|Odległość między elementami w wycinek `valarray`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray — >

**Namespace:** Standard

## <a name="size"></a>  Slice::size

Odnajduje liczba elementów w wycinek valarray —.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w wycinek valarray —.

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

## <a name="slice"></a>  Slice::Slice

Definiuje ona podzestaw valarray —, która składa się z liczbą elementów, które są takie same odległości i który rozpoczęli określonego elementu.

```cpp
slice();

slice(
    size_t _StartIndex,
    size_t _Len,
    size_t stride);
```

### <a name="parameters"></a>Parametry

`_StartIndex` Valarray — indeks pierwszego elementu w podzbiorze.

`_Len` Liczba elementów w podzbiorze.

`stride` Odległość między elementami w podzbiorze.

### <a name="return-value"></a>Wartość zwracana

Domyślny konstruktor przechowuje zera indeks początkowy, całkowita długość i krok. Drugi Konstruktor magazynów `_StartIndex` początkowy indeks `_Len` całkowita długość i `stride` dla krok.

### <a name="remarks"></a>Uwagi

Krok może być ujemna.

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

## <a name="start"></a>  Slice::Start

Znajduje indeks początkowy wycinek valarray —.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks początkowy wycinek valarray —.

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

## <a name="stride"></a>  Slice::STRIDE

Umożliwia znalezienie odległość między elementami w wycinek valarray —.

```cpp
size_t stride() const;
```

### <a name="return-value"></a>Wartość zwracana

Odległość między elementami w wycinek valarray —.

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

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
