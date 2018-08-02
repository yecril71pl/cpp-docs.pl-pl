---
title: Nieobsługiwane wyjątki języka C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], unhandled exceptions
- catch keyword [C++], handler not found
- exceptions [C++], unhandled
- C++ exception handling, unhandled exceptions
- unhandled exceptions [C++]
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e2162034b3e9ff93ebccca0f7eb53299b19c648
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467540"
---
# <a name="unhandled-c-exceptions"></a>Nieobsługiwane wyjątki języka C++
Jeśli pasującej klauzuli obsługi (lub wielokropek **catch** obsługi) nie można odnaleźć dla bieżącego wyjątku jest wstępnie zdefiniowane `terminate` nosi nazwę funkcji czasu wykonywania. (Można także jawnie wywołać `terminate` w dowolnym inne programy obsługi.) Domyślną akcję `terminate` jest wywołanie `abort`. Jeśli chcesz `terminate` do wywołania niektórych innych funkcji w programie przed zakończeniem działania aplikacji, należy wywołać `set_terminate` funkcji o nazwie funkcja wywoływana, jako pojedynczy argument. Możesz wywołać `set_terminate` w dowolnym momencie w programach. `terminate` Procedura zawsze wywołuje ostatniej funkcji podawana jako argument do `set_terminate`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje `char *` wyjątku, ale nie zawiera program obsługi wyznaczone do przechwytywania wyjątków typu `char *`. Wywołanie `set_terminate` powoduje, że `terminate` do wywołania `term_func`.  
  
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
  
 `term_func` Funkcji powinna zakończyć działanie programu lub bieżącego wątku, najlepiej przez wywołanie metody `exit`. Jeśli nie, a zamiast tego zwraca do obiektu wywołującego, `abort` jest wywoływana.  
  
## <a name="see-also"></a>Zobacz także  
 [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)