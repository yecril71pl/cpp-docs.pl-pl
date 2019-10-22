---
title: indirect_array — Klasa
ms.date: 11/04/2016
f1_keywords:
- valarray/std::indirect_array
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
ms.openlocfilehash: 6be0c5153cbc94d09b414fc9e14fa498c7a4cfa7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687919"
---
# <a name="indirect_array-class"></a>indirect_array — Klasa

Wewnętrzny, pomocniczy szablon klasy, który obsługuje obiekty, które są podzestawami valarrays przez dostarczanie operacji między tablicami podzestawu zdefiniowanymi przez określenie podzestawu indeksów nadrzędnego valarray.

## <a name="syntax"></a>Składnia

## <a name="remarks"></a>Uwagi

Klasa opisuje obiekt, który przechowuje odwołanie do obiektu `va` klasy [valarray](../standard-library/valarray-class.md)  **\<Type >** oraz obiekt `xa` klasy `valarray<size_t>`, który opisuje sekwencję elementów do wybrania z obiektu `valarray<Type>`.

Obiekt `indirect_array<Type>` można skonstruować tylko przez napisanie wyrażenia `va[xa]` formularza. Funkcje członkowskie klasy indirect_array, zachowują się jak odpowiadające im sygnatury funkcji zdefiniowane dla `valarray<Type>`, z tą różnicą, że dotyczy tylko sekwencji wybranych elementów.

Sekwencja składa się z **XA.** elementy [size](../standard-library/valarray-class.md#size) , gdzie element `I` stać się indeksem **XA**[`I`] w `va`.

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

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
