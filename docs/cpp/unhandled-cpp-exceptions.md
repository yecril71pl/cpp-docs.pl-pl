---
title: Nieobsługiwane wyjątki języka C++
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], unhandled exceptions
- catch keyword [C++], handler not found
- exceptions [C++], unhandled
- C++ exception handling, unhandled exceptions
- unhandled exceptions [C++]
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
ms.openlocfilehash: 48b417c48a3cbb903f3fabaf31b1423e79a1a414
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233590"
---
# <a name="unhandled-c-exceptions"></a>Nieobsługiwane wyjątki języka C++

Jeśli nie można odnaleźć zgodnej procedury obsługi (lub obsługi wielokropka **`catch`** ) dla bieżącego wyjątku, `terminate` zostanie wywołana wstępnie zdefiniowana funkcja czasu wykonywania. (Można również jawnie wywołać `terminate` w dowolnym z programów obsługi). Domyślną akcją `terminate` jest wywołanie `abort` . Jeśli chcesz `terminate` wywołać inną funkcję w programie przed wyjściem z aplikacji, wywołaj `set_terminate` funkcję z nazwą funkcji, która ma zostać wywołana jako jej pojedynczy argument. Możesz wywołać `set_terminate` w dowolnym momencie w programie. `terminate`Procedura zawsze wywołuje ostatnią funkcję podaną jako argument do `set_terminate` .

## <a name="example"></a>Przykład

Poniższy przykład zgłasza `char *` wyjątek, ale nie zawiera procedury obsługi wyznaczeniowej do przechwytywania wyjątków typu `char *` . Wywołanie `set_terminate` nakazuje `terminate` wywołania `term_func` .

```cpp
// exceptions_Unhandled_Exceptions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
void term_func() {
   cout << "term_func was called by terminate." << endl;
   exit( -1 );
}
int main() {
   try
   {
      set_terminate( term_func );
      throw "Out of memory!"; // No catch handler for this exception
   }
   catch( int )
   {
      cout << "Integer exception raised." << endl;
   }
   return 0;
}
```

## <a name="output"></a>Dane wyjściowe

```Output
term_func was called by terminate.
```

`term_func`Funkcja powinna kończyć program lub bieżący wątek, najlepiej przez wywołanie metody `exit` . Jeśli nie, i zamiast tego powraca do obiektu wywołującego, `abort` jest wywoływana.

## <a name="see-also"></a>Zobacz także

[Nowoczesne najlepsze rozwiązania w języku C++ dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md)
