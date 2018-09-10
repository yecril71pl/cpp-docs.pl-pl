---
title: underflow_error — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- stdexcept/std::underflow_error
dev_langs:
- C++
helpviewer_keywords:
- underflow_error class
ms.assetid: d632f1f9-9c6c-4954-b96b-03041bfab22d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ef86d368a0ca9f7aa2c3b6700350ccaaa8f7836
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317332"
---
# <a name="underflowerror-class"></a>underflow_error — Klasa

Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych do zgłaszania arytmetyczne niedopełnienie.

## <a name="syntax"></a>Składnia

```cpp
class underflow_error : public runtime_error {
public:
    explicit underflow_error(const string& message);

    explicit underflow_error(const char *message);

};
```

## <a name="remarks"></a>Uwagi

Wartość zwrócona przez obiekt [co](../standard-library/exception-class.md) jest kopią **komunikat**`.`[danych](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Przykład

```cpp
// underflow_error.cpp
// compile with: /EHsc /GR
#include <iostream>

using namespace std;

int main( )
{
   try
   {
      throw underflow_error( "The number's a bit small, captain!" );
   }
   catch ( exception &e ) {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught: The number's a bit small, captain!
Type: class std::underflow_error
*/
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<stdexcept >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[runtime_error, klasa](../standard-library/runtime-error-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
