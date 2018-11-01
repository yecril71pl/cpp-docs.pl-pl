---
title: indirect_array — Klasa
ms.date: 11/04/2016
f1_keywords:
- valarray/std::indirect_array
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
ms.openlocfilehash: 43c54bf3dae02eb117b15cae0dd7de9bb4a9db51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448883"
---
# <a name="indirectarray-class"></a>indirect_array — Klasa

Klasa szablonu wewnętrznego, pomocnicza, która obiektów obsługuje, które są podzbiorem valarrays, zapewniając operacji między macierzami podzbioru definiowaną przez określenie podzbiór indeksów valarray nadrzędnej.

## <a name="syntax"></a>Składnia

## <a name="remarks"></a>Uwagi

Klasa opisująca obiekt, który zawiera odwołanie do obiektu `va` klasy [valarray](../standard-library/valarray-class.md)**\<typ >**, wraz z obiektem `xa` klasy `valarray<size_t>`, opisano sekwencji elementów, które można wybierać `valarray<Type>` obiektu.

Konstruowanie `indirect_array<Type>` obiektu Pisząc wyrażenie w formie `va[xa]`. Funkcje Członkowskie indirect_array — klasa następnie zachowują się jak odpowiedniej sygnatury funkcji zdefiniowanych dla `valarray<Type>`, z tą różnicą, że dotyczy tylko kolejność wybranych elementów.

Sekwencja składa się z **xa.** [rozmiar](../standard-library/valarray-class.md#size) elementów, gdzie element `I` staje się indeks **xa**[ `I`] w ramach `va`.

## <a name="example"></a>Przykład:

```cpp
// indirect_array.cpp
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

   // Select 2nd, 4th & 6th elements
   // and assign a value of 10 to them
   valarray<size_t> indx ( 3 );
   indx [0] = 2;
   indx [1] = 4;
   indx [2] = 6;
   va[indx] = 10;

   cout << "The modified operand valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;
}
```

### <a name="output"></a>Dane wyjściowe

```cpp
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
