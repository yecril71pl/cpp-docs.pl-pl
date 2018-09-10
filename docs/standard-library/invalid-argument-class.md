---
title: invalid_argument — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- stdexcept/std::invalid_argument
dev_langs:
- C++
helpviewer_keywords:
- invalid_argument class
ms.assetid: af6c227d-ad7c-4e63-9dee-67af81d83506
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7e6a555655ec6b05777c74a47090387ebf07f43
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314940"
---
# <a name="invalidargument-class"></a>invalid_argument — Klasa

Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych do zgłaszania nieprawidłowy argument.

## <a name="syntax"></a>Składnia

```cpp
class invalid_argument : public logic_error {
public:
    explicit invalid_argument(const string& message);

    explicit invalid_argument(const char *message);

};
```

## <a name="remarks"></a>Uwagi

Wartość zwrócona przez obiekt [co](../standard-library/exception-class.md) jest kopią **komunikat**`.`[danych](../standard-library/basic-string-class.md#data).

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

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[logic_error, klasa](../standard-library/logic-error-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
