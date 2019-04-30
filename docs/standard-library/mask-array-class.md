---
title: mask_array — Klasa
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 108c942bef33e44b515d46e953c9d99274e3ce8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412985"
---
# <a name="maskarray-class"></a>mask_array — Klasa

Klasa szablonu pomocnicze, wewnętrzne, który obiektów obsługuje, które są podzbiorem valarrays nadrzędnego, określony za pomocą wyrażenie logiczne, zapewniając operacji między macierzami podzbioru.

## <a name="syntax"></a>Składnia

## <a name="remarks"></a>Uwagi

Klasa opisująca obiekt, który zawiera odwołanie do obiektu `va` klasy [valarray](../standard-library/valarray-class.md)**\<typ >**, wraz z obiektem `ba` klasy [ valarray\<bool >](../standard-library/valarray-bool-class.md), która opisuje kolejność elementów, które można wybierać `valarray<Type>` obiektu.

Konstruowanie `mask_array<Type>` obiektu Pisząc wyrażenie w formie [oceny luk w zabezpieczeniach&#91;ba&#93;](../standard-library/valarray-class.md#op_at). Funkcje Członkowskie mask_array — klasa następnie zachowują się jak odpowiedniej sygnatury funkcji zdefiniowanych dla `valarray<Type>`, z tą różnicą, że dotyczy tylko kolejność wybranych elementów.

Sekwencja składa się z co najwyżej `ba.size` elementów. Element *"j"* znajduje się tylko wtedy, gdy **ba**[ *"j"*] ma wartość true. Tak więc istnieją dowolną liczbę elementów w sekwencji, ponieważ wartość true, elementy w `ba`. Jeśli `I` jest indeksem najniższy element wartość true w `ba`, następnie **oceny luk w zabezpieczeniach**[ `I`] jest element zero w wybranej sekwencji.

## <a name="example"></a>Przykład

```cpp
// mask_array.cpp
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

   // Use masked subsets to assign a value of 10
   // to all elements grrater than 3 in value
   va [va > 3 ] = 10;
   cout << "The modified operand valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;
}
```

### <a name="output"></a>Dane wyjściowe

```Output
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 2 -1 10 -1 10 -1 10 -1).
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
