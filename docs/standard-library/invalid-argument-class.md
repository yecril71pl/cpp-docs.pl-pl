---
title: invalid_argument — Klasa
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::invalid_argument
helpviewer_keywords:
- invalid_argument class
ms.assetid: af6c227d-ad7c-4e63-9dee-67af81d83506
ms.openlocfilehash: 1c5caa0129730750a6429d9f7fa883e9af30f225
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449261"
---
# <a name="invalidargument-class"></a>invalid_argument — Klasa

Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych w celu zgłoszenia nieprawidłowego argumentu.

## <a name="syntax"></a>Składnia

```cpp
class invalid_argument : public logic_error {
public:
    explicit invalid_argument(const string& message);

    explicit invalid_argument(const char *message);

};
```

## <a name="remarks"></a>Uwagi

Wartość zwracana przez [co](../standard-library/exception-class.md) to jest kopia[danych](../standard-library/basic-string-class.md#data) **komunikatów**`.`.

## <a name="example"></a>Przykład

```cpp
// invalid_arg.cpp
// compile with: /EHsc /GR
#include <bitset>
#include <iostream>

using namespace std;

int main( )
{
   try
   {
      bitset< 32 > bitset( string( "11001010101100001b100101010110000") );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught invalid bitset<N> char
Type class std::invalid_argument
*/
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<stdexcept >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Klasa logic_error](../standard-library/logic-error-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
