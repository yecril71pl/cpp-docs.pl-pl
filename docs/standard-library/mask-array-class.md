---
title: mask_array — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::mask_array
dev_langs:
- C++
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b19ac68f1d1db9ac73e0519b566f68443775db11
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="maskarray-class"></a>mask_array — Klasa

Klasy wewnętrzne, pomocnicze szablonu, która obsługuje obiekty, które są podzbiorem valarrays nadrzędnego określić z wyrażenie logiczne, wprowadzając operacji między macierzami podzbioru.

## <a name="syntax"></a>Składnia

## <a name="remarks"></a>Uwagi

Klasa opisuje obiekt, który zawiera odwołanie do obiektu **va** klasy [valarray —](../standard-library/valarray-class.md)**\<typu >**, wraz z obiektem **ba**  klasy [valarray —\<bool >](../standard-library/valarray-bool-class.md), która opisuje kolejność elementów, aby dokonać wyboru spośród **valarray —\<typu >** obiektu.

Możesz utworzyć **mask_array —\<typu >** obiektu Pisząc wyrażenie w postaci [va&#91;ba&#93;](../standard-library/valarray-class.md#op_at). Funkcje Członkowskie mask_array — klasa następnie zachowania odpowiedniego sygnatury funkcji zdefiniowane dla **valarray —\<typu >**, ale dotyczy tylko sekwencji wybrane elementy.

Sekwencja składa się z co najwyżej **ba.size** elementów. Element *J* wchodzi tylko wtedy, gdy **ba**[ *J*] ma wartość true. W związku z tym istnieją dowolną liczbę elementów w sekwencji, jako wartość true, elementy w **ba**. Jeśli `I` jest indeksem najniższy elementu wartość true w **ba**, następnie **va**[ `I`] jest elementem zero w wybranej sekwencji.

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

**Nagłówek:** \<valarray — >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
