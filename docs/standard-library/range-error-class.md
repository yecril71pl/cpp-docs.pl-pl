---
title: range_error — Klasa
ms.date: 08/14/2018
f1_keywords:
- stdexcept/std::range_error
helpviewer_keywords:
- range_error class
ms.assetid: 8afb3e88-fc49-4213-b096-ed63d7aea37c
ms.openlocfilehash: a4b7e90e5806713408c6779b288cafe008e2b4ed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62369809"
---
# <a name="rangeerror-class"></a>range_error — Klasa

Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych, aby zgłosić błąd zakresu.

## <a name="syntax"></a>Składnia

```cpp
class range_error : public runtime_error {
public:
    explicit range_error(const string& message);
    explicit range_error(const char *message);
};
```

## <a name="remarks"></a>Uwagi

Wartość zwrócona przez obiekt [co](../standard-library/exception-class.md) jest kopią `message.data`. Aby uzyskać więcej informacji, zobacz [basic_string::data](../standard-library/basic-string-class.md#data).

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
   catch (range_error &e)
   {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught: The range is in error!
Type: class std::range_error
*/
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<stdexcept >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[runtime_error, klasa](../standard-library/runtime-error-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
