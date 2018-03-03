---
title: "Pisanie filtra wyjątku | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 40afc6872ac04522c4c42f0a0d890b791ac03d53
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="writing-an-exception-filter"></a>Pisanie filtra wyjątku
Możesz obsłużyć wyjątek wykonując skok na poziom programu obsługi wyjątków lub kontynuując wykonywanie. Zamiast za pomocą kodu obsługi wyjątków do obsługi wyjątku i/lub za pośrednictwem, możesz użyć *filtru* aby wyczyścić problem, a następnie, zwracając wartość -1, Wznów normalnym przepływie bez wyczyszczenie stosu.  
  
> [!NOTE]
>  Niektóre wyjątki nie mogą być kontynuowane. Jeśli *filtru* wartość-1 takiego wyjątku, system zgłasza wyjątek nowe. Podczas wywoływania [raiseexception —](http://msdn.microsoft.com/library/windows/desktop/ms680552), należy określić, czy wyjątek będzie kontynuowana.  
  
 Na przykład w poniższym kodzie użyto wywołania funkcji w *filtru* wyrażenie: Ta funkcja obsługuje ten problem, a następnie zwraca -1, aby wznowić normalnym przepływie sterowania:  
  
```  
// exceptions_Writing_an_Exception_Filter.cpp  
#include <windows.h>  
int main() {  
   int Eval_Exception( int );  
  
   __try {}  
  
   __except ( Eval_Exception( GetExceptionCode( ))) {  
      ;  
   }  
  
}  
void ResetVars( int ) {}  
int Eval_Exception ( int n_except ) {  
   if ( n_except != STATUS_INTEGER_OVERFLOW &&   
      n_except != STATUS_FLOAT_OVERFLOW )   // Pass on most exceptions  
   return EXCEPTION_CONTINUE_SEARCH;  
  
   // Execute some code to clean up problem  
   ResetVars( 0 );   // initializes data to 0  
   return EXCEPTION_CONTINUE_EXECUTION;  
}  
```  
  
 Jest warto używać wywołania funkcji w *filtru* wyrażenie zawsze, gdy *filtru* trzeba podejmować żadnych działań złożonych. Obliczanie wyrażenia powoduje wykonanie funkcji, w tym przypadku jest to `Eval_Exception`.  
  
 Zwróć uwagę na użycie [getexceptioncode —](http://msdn.microsoft.com/library/windows/desktop/ms679356) ustalenie wyjątek. Musisz wywołać tę funkcję wewnątrz samego filtru. `Eval_Exception`Nie można wywołać **getexceptioncode —**, ale musi być przekazywane do niego kod wyjątku.  
  
 Ten program obsługi wyjątków przekazuje sterowanie do innego programu obsługi wyjątków, o ile wyjątek nie dotyczy przepełnienia liczby całkowitej lub zmiennoprzecinkowej. Jeśli tak się stanie, program obsługi wyjątku wywołuje funkcję (`ResetVars` jest tylko przykładem, a nie funkcją API), aby zresetować niektóre zmienne globalne. *Instrukcja bloku 2*, który w tym przykładzie jest pusta, nie można wykonać ponieważ `Eval_Exception` nigdy nie zwraca exception_execute_handler — (1).  
  
 Używanie wywołań funkcji jest dobrą techniką ogólnego przeznaczenia do radzenia sobie ze złożonymi wyrażeniami filtrującymi. Dwie inne funkcje języka C, które są przydatne to:  
  
-   Operator warunkowy  
  
-   Operator przecinka  
  
 Operator warunkowy jest często przydatny, ponieważ może być użyty do wyszukiwania określonego kodu zwracanej wartości, a następnie zwróci jedną z dwóch różnych wartości. Na przykład, filtr w poniższym kodzie rozpoznaje wyjątek, tylko jeśli wyjątkiem jest `STATUS_INTEGER_OVERFLOW`:  
  
```  
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {  
```  
  
 Celem operatora warunkowego w tym przypadku jest głównie zapewnienie czytelności, ponieważ następujący kod generuje te same wyniki:  
  
```  
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {  
```  
  
 Operator warunkowy jest bardziej przydatne w sytuacji, gdy być może filtr, aby zwrócić wartość -1, exception_continue_execution —.  
  
 Operator przecinka umożliwia wykonanie wielu niezależnych operacji wewnątrz pojedynczego wyrażenia. Efektem jest (w przybliżeniu) wykonanie wielu instrukcji, a następnie zwrócenie wartości ostatniego wyrażenia. Na przykład, poniższy kod przechowuje kod wyjątku w zmiennej, a następnie ją sprawdza:  
  
```  
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie programu do obsługi wyjątków](../cpp/writing-an-exception-handler.md)   
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)