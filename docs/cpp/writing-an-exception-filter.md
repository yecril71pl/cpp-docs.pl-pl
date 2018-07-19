---
title: Pisanie filtra wyjątku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb4b02144f55231a7b4472cd62322fd61a543d18
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947780"
---
# <a name="writing-an-exception-filter"></a>Pisanie filtra wyjątku
Możesz obsłużyć wyjątek wykonując skok na poziom programu obsługi wyjątków lub kontynuując wykonywanie. Zamiast używania kodu programu obsługi wyjątków, aby obsłużyć wyjątek i przejść przez, można użyć *filtru* Aby oczyścić problem, a następnie, zwracając wartość -1, wznowić Normalny przepływ bez czyszczenia stosu.  
  
> [!NOTE]
>  Niektóre wyjątki nie mogą być kontynuowane. Jeśli *filtru* ocenia na -1 dla takiego wyjątku, to system zgłosi nowy wyjątek. Gdy wywołujesz [RaiseException](http://msdn.microsoft.com/library/windows/desktop/ms680552), należy określić, czy kontynuować wyjątek.  
  
 Na przykład, poniższy kod używa wywołania funkcji w *filtru* wyrażenia: funkcja ta obsługuje problem, a następnie zwraca wartość -1, aby wznowić Normalny przepływ sterowania:  
  
```cpp 
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
  
 To dobry pomysł, aby używać wywołania funkcji w *filtru* wyrażenie zawsze wtedy, gdy *filtru* musi wykonać jakiekolwiek złożone. Obliczanie wyrażenia powoduje wykonanie funkcji, w tym przypadku jest to `Eval_Exception`.  
  
 Zwróć uwagę na użycie [GetExceptionCode](http://msdn.microsoft.com/library/windows/desktop/ms679356) do określenia wyjątku. Musisz wywołać tę funkcję wewnątrz samego filtru. `Eval_Exception` Nie można wywołać `GetExceptionCode`, ale musi mieć przekazany kod wyjątku.  
  
 Ten program obsługi wyjątków przekazuje sterowanie do innego programu obsługi wyjątków, o ile wyjątek nie dotyczy przepełnienia liczby całkowitej lub zmiennoprzecinkowej. Jeśli tak się stanie, program obsługi wyjątku wywołuje funkcję (`ResetVars` jest tylko przykładem, a nie funkcją API), aby zresetować niektóre zmienne globalne. *Instrukcja block-2*, który w tym przykładzie jest pusta, może nigdy nie można wykonać, ponieważ `Eval_Exception` nigdy nie zwraca EXCEPTION_EXECUTE_HANDLER (1).  
  
 Używanie wywołań funkcji jest dobrą techniką ogólnego przeznaczenia do radzenia sobie ze złożonymi wyrażeniami filtrującymi. Dwie inne funkcje języka C, które są przydatne to:  
  
-   Operator warunkowy  
  
-   Operator przecinka  
  
 Operator warunkowy jest często przydatny, ponieważ może być użyty do wyszukiwania określonego kodu zwracanej wartości, a następnie zwróci jedną z dwóch różnych wartości. Na przykład filtr w poniższym kodzie rozpoznaje wyjątek, tylko wtedy, gdy wyjątek jest STATUS_INTEGER_OVERFLOW:  
  
```cpp 
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {  
```  
  
 Celem operatora warunkowego w tym przypadku jest głównie zapewnienie czytelności, ponieważ następujący kod generuje te same wyniki:  
  
```cpp 
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {  
```  
  
 Operator warunkowy jest bardziej użyteczny w sytuacjach, w których możesz chcieć filtru wartości -1, EXCEPTION_CONTINUE_EXECUTION.  
  
 Operator przecinka umożliwia wykonanie wielu niezależnych operacji wewnątrz pojedynczego wyrażenia. Efektem jest (w przybliżeniu) wykonanie wielu instrukcji, a następnie zwrócenie wartości ostatniego wyrażenia. Na przykład, poniższy kod przechowuje kod wyjątku w zmiennej, a następnie ją sprawdza:  
  
```cpp 
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie programu do obsługi wyjątków](../cpp/writing-an-exception-handler.md)   
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)