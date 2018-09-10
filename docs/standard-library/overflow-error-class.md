---
title: overflow_error — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- stdexcept/std::overflow_error
dev_langs:
- C++
helpviewer_keywords:
- overflow_error class
ms.assetid: bae7128d-e36b-4a45-84f1-2f89da441d20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 17a8c5b1a95d133f66c729ae6736a8726f8a2a3f
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317527"
---
# <a name="overflowerror-class"></a>overflow_error — Klasa

Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych do zgłaszania przepełnienie arytmetyczne.

## <a name="syntax"></a>Składnia

```cpp
class overflow_error : public runtime_error {
public:
    explicit overflow_error(const string& message);

    explicit overflow_error(const char *message);

};
```

## <a name="remarks"></a>Uwagi

Wartość zwrócona przez obiekt [co](../standard-library/exception-class.md) jest kopią **komunikat**`.`[danych](../standard-library/basic-string-class.md#data).

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

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[runtime_error, klasa](../standard-library/runtime-error-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
