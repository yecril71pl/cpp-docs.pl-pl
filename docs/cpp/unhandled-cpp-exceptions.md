---
title: "Nieobsługiwane wyjątki języka C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- event handlers [C++], unhandled exceptions
- catch keyword [C++], handler not found
- exceptions [C++], unhandled
- C++ exception handling, unhandled exceptions
- unhandled exceptions [C++]
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6b7410d34b7b9f31c96cf7e991133770099735a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="unhandled-c-exceptions"></a>Nieobsługiwane wyjątki języka C++
Jeśli pasujące obsługi (lub wielokropek **catch** obsługi) nie można odnaleźć dla bieżącego wyjątku, wstępnie zdefiniowane `terminate` została wywołana funkcja czasu wykonywania. (Można również jawnie wywołać `terminate` w żadnym z programu obsługi.) Domyślną akcję `terminate` jest wywołanie `abort`. Jeśli chcesz `terminate` wywoływanie niektórych innych funkcji w programie przed zakończeniem pracy aplikacji, należy wywołać `set_terminate` funkcji o nazwie funkcja wywoływana, jako jego jeden argument. Możesz wywołać `set_terminate` w dowolnym momencie w programie. `terminate` Procedura zawsze wywołuje ostatniej podany jako argument do funkcji `set_terminate`.  
  
## <a name="example"></a>Przykład  
 Zgłasza wyjątek w poniższym przykładzie `char *` wyjątek, ale nie zawiera obsługi wyznaczony przechwytują wyjątki typu `char *`. Wywołanie `set_terminate` nakazuje `terminate` do wywołania `term_func`.  
  
```  
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
  
```  
term_func was called by terminate.  
```  
  
 `term_func` Funkcja powinna zakończyć działanie programu lub bieżący wątek, najlepiej przez wywołanie metody `exit`. Jeśli nie, a zamiast tego zwraca do swojego obiektu wywołującego `abort` jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)