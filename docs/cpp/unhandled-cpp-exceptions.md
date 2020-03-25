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
ms.openlocfilehash: f42a4e2af46ab7690d6f4bc9641c09f3757eb6b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160557"
---
# <a name="unhandled-c-exceptions"></a>Nieobsługiwane wyjątki języka C++

Jeśli nie można odnaleźć zgodnego programu obsługi (lub obsługi **catch** ) dla bieżącego wyjątku, zostanie wywołana wstępnie zdefiniowana funkcja czasu wykonywania `terminate`. (Można również jawnie wywołać `terminate` w którymkolwiek z programów obsługi). Domyślną akcją `terminate` jest wywołanie `abort`. Jeśli chcesz, aby `terminate` wywoływać inną funkcję w programie przed zamknięciem aplikacji, wywołaj funkcję `set_terminate` z nazwą funkcji, która ma zostać wywołana jako jej pojedynczy argument. `set_terminate` można wywołać w dowolnym momencie w programie. Procedura `terminate` zawsze wywołuje ostatnią funkcję podaną jako argument do `set_terminate`.

## <a name="example"></a>Przykład

Poniższy przykład zgłasza wyjątek `char *`, ale nie zawiera procedury obsługi wyznaczono do przechwytywania wyjątków typu `char *`. Wywołanie `set_terminate` instruuje `terminate`, aby wywołać `term_func`.

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

Funkcja `term_func` powinna kończyć program lub bieżący wątek, najlepiej przez wywoływanie `exit`. Jeśli nie, i zamiast tego powraca do obiektu wywołującego, `abort` jest wywoływana.

## <a name="see-also"></a>Zobacz też

[Nowoczesne C++ najlepsze rozwiązania dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md)
