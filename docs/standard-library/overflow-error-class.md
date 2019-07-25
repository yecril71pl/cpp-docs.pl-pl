---
title: overflow_error — Klasa
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::overflow_error
helpviewer_keywords:
- overflow_error class
ms.assetid: bae7128d-e36b-4a45-84f1-2f89da441d20
ms.openlocfilehash: b1faad62dc8e564d97170b5244b6406ae8e1dee6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450141"
---
# <a name="overflowerror-class"></a>overflow_error — Klasa

Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych do zgłaszania przepełnienia arytmetycznego.

## <a name="syntax"></a>Składnia

```cpp
class overflow_error : public runtime_error {
public:
    explicit overflow_error(const string& message);

    explicit overflow_error(const char *message);

};
```

## <a name="remarks"></a>Uwagi

Wartość zwracana przez [co](../standard-library/exception-class.md) to jest kopia[danych](../standard-library/basic-string-class.md#data) **komunikatów**`.`.

## <a name="example"></a>Przykład

```cpp
// overflow_error.cpp
// compile with: /EHsc /GR
#include <bitset>
#include <iostream>

using namespace std;

int main( )
{
   try
   {
      bitset< 33 > bitset;
      bitset[32] = 1;
      bitset[0] = 1;
      unsigned long x = bitset.to_ulong( );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught bitset<N> overflow
Type class std::overflow_error
*/
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<stdexcept >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Klasa runtime_error](../standard-library/runtime-error-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
