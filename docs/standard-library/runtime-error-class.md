---
title: runtime_error — Klasa
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::runtime_error
helpviewer_keywords:
- runtime_error class
ms.assetid: 4d0227bf-847b-45a2-a320-2351ebf98368
ms.openlocfilehash: a860e10994934ae0e97950fddb14e573f8752833
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520904"
---
# <a name="runtime_error-class"></a>runtime_error — Klasa

Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych w celu zgłaszania błędów, które mogą być wykrywalne tylko wtedy, gdy program jest wykonywany.

## <a name="syntax"></a>Składnia

```cpp
class runtime_error : public exception {
public:
    explicit runtime_error(const string& message);

    explicit runtime_error(const char *message);

};
```

## <a name="remarks"></a>Uwagi

Wartość zwracana przez `what()` to jest kopia `message.data()` . Aby uzyskać więcej informacji, zobacz [`what`](../standard-library/exception-class.md) i [`data`](../standard-library/basic-string-class.md#data) .

## <a name="example"></a>Przykład

```cpp
// runtime_error.cpp
// compile with: /EHsc /GR
#include <iostream>

using namespace std;

int main( )
{
// runtime_error
   try
   {
      locale loc( "test" );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught bad locale name
Type class std::runtime_error
*/
```

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<stdexcept>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Klasa wyjątku](../standard-library/exception-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
