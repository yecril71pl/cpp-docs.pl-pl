---
title: range_error — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- stdexcept/std::range_error
dev_langs:
- C++
helpviewer_keywords:
- range_error class
ms.assetid: 8afb3e88-fc49-4213-b096-ed63d7aea37c
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ca154c0bfa05da025df1c9c8e2ebf54750fe71c
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="rangeerror-class"></a>range_error — Klasa

Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłaszanych zgłosić błąd zakresu.

## <a name="syntax"></a>Składnia

```cpp
class range_error : public runtime_error {
public:
    explicit range_error(const string& message);

    explicit range_error(const char *message);

};
```

## <a name="remarks"></a>Uwagi

Wartość zwrócona przez [co](../standard-library/exception-class.md) kopię **komunikat**`.`[danych](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Przykład

```cpp
// range_error.cpp
// compile with: /EHsc /GR
#include <iostream>
using namespace std;
int main()
{
   try
   {
      throw range_error( "The range is in error!" );
   }
   catch (exception &e)
   {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
\* Output:
Caught: The range is in error!
Type: class std::range_error
*\
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<stdexcept — >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[runtime_error, klasa](../standard-library/runtime-error-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
