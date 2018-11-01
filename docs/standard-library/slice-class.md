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
ms.openlocfilehash: f2c054626b36083d67f9dbc4c87cf6283c12f001
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495423"
---
# <a name="slice-class"></a>slice — Klasa

Klasa narzędzia do tablicy valarray, który jest używany do definiowania jednowymiarowa podzbiór valarray nadrzędnej. Jeśli tablica valarray jest traktowany jako dwuwymiarowej macierzy przy użyciu wszystkich elementów w tablicy, wycinek wyodrębnia wektora w jednym wymiarze poza dwuwymiarową tablicę.

## <a name="remarks"></a>Uwagi

Klasa przechowuje parametrów, charakteryzujące się do obiektu typu [slice_array —](../standard-library/slice-array-class.md) podzbiór tablicy valarray pośrednio jest tworzony, gdy obiekt klasy wycinka jest wyświetlany jako argument dla obiektu klasy [valarray ](../standard-library/valarray-class.md#op_at)  **\<Typ >**. Przechowywane wartości, które określają podzbioru wybrana w zaufanym valarray nadrzędnego obejmują:

- Indeks początkowy w tablicy valarray.

- Łączna długość lub liczba elementów w wycinka.

- Krok lub odległość między kolejnych indeksy elementów w tablicy valarray.

Jeśli zestawu zdefiniowanego przez wycinek jest podzbiorem stałej tablicy valarray, wycinek jest nowej tablicy valarray. Jeśli zestawu zdefiniowanego przez wycinek jest podzbiorem stałymi valarray, wycinek ma semantyki odwołania do oryginalnego tablicy valarray. Mechanizm oceny dla nieunikatowego valarrays oszczędza czas i pamięci.

Operacje na valarrays jest gwarantowane tylko wtedy, gdy podzestawy źródłowym i docelowym, zdefiniowane przez wycinki różniące się od siebie i wszystkich indeksów są prawidłowe.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[wycinek](#slice)|Definiuje podzbiór `valarray` składający się z liczbą elementów, które są równe odległości i, która jest uruchamiana na określony element.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Rozmiar](#size)|Wyszukuje liczbę elementów w wycinku `valarray`.|
|[start](#start)|Znajduje indeks początkowy wycinek `valarray`.|
|[stride](#stride)|Odległość między elementami w wycinku `valarray`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray >

**Namespace:** standardowe

## <a name="size"></a>  Slice::size

Wyszukuje liczbę elementów w wycinku tablicy valarray.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w wycinku tablicy valarray.

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

Definiuje podzbiór tablicy valarray, która składa się z liczbą elementów, które są równe odległości i, która jest uruchamiana na określony element.

```cpp
slice();

slice(
    size_t _StartIndex,
    size_t _Len,
    size_t stride);
```

### <a name="parameters"></a>Parametry

*_StartIndex*<br/>
Indeks tablicy valarray pierwszego elementu w podzbiorze.

*_Len*<br/>
Liczba elementów w podzbiorze.

*stride*<br/>
Odległość między elementami w podzbiorze.

### <a name="return-value"></a>Wartość zwracana

Domyślny konstruktor przechowuje zera indeks początkowy, całkowita długość i krok. Drugi Konstruktor magazynów *_StartIndex* począwszy od indeksu *_Len* całkowita długość i *stride* dla krok.

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

Znajduje indeks początkowy wycinek tablicy valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks początkowy wycinek tablicy valarray.

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

Umożliwia znalezienie odległości między elementami w wycinku tablicy valarray.

```cpp
size_t stride() const;
```

### <a name="return-value"></a>Wartość zwracana

Odległość między elementami w wycinku tablicy valarray.

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
