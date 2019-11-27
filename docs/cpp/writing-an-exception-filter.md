---
title: Pisanie filtru wyjątku
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: aaf0dc77207399d7c6be86127d7decf03895ced5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245988"
---
# <a name="writing-an-exception-filter"></a>Pisanie filtru wyjątku

Możesz obsłużyć wyjątek wykonując skok na poziom programu obsługi wyjątków lub kontynuując wykonywanie. Zamiast używać kodu programu obsługi wyjątków do obsługi wyjątku i przechodzenia przez program, można użyć *filtru* , aby oczyścić ten problem, a następnie, zwracając-1, wznowić normalny przepływ bez wyczyszczenia stosu.

> [!NOTE]
>  Niektóre wyjątki nie mogą być kontynuowane. Jeśli *Filtr* zwróci wartość-1 dla takiego wyjątku, system zgłasza nowy wyjątek. Po wywołaniu metody [Zgłoś](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception)wyjątek należy określić, czy będzie kontynuowany wyjątek.

Na przykład poniższy kod używa wywołania funkcji w wyrażeniu *filtru* : Ta funkcja obsługuje problem, a następnie zwraca-1, aby wznowić normalny przepływ sterowania:

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

Dobrym pomysłem jest użycie wywołania funkcji w wyrażeniu *filtru* za każdym razem, gdy *Filtr* musi wykonać dowolne złożone elementy. Obliczanie wyrażenia powoduje wykonanie funkcji, w tym przypadku jest to `Eval_Exception`.

Zwróć uwagę na użycie elementu [GetExceptionCode](/windows/win32/Debug/getexceptioncode) w celu określenia wyjątku. Musisz wywołać tę funkcję wewnątrz samego filtru. `Eval_Exception` nie może wywołać `GetExceptionCode`, ale musi mieć do niego przesłany kod wyjątku.

Ten program obsługi wyjątków przekazuje sterowanie do innego programu obsługi wyjątków, o ile wyjątek nie dotyczy przepełnienia liczby całkowitej lub zmiennoprzecinkowej. Jeśli tak się stanie, program obsługi wyjątku wywołuje funkcję (`ResetVars` jest tylko przykładem, a nie funkcją API), aby zresetować niektóre zmienne globalne. *Instrukcja-2*, która w tym przykładzie jest pusta, nigdy nie może być wykonana, ponieważ `Eval_Exception` nigdy nie zwraca EXCEPTION_EXECUTE_HANDLER (1).

Używanie wywołań funkcji jest dobrą techniką ogólnego przeznaczenia do radzenia sobie ze złożonymi wyrażeniami filtrującymi. Dwie inne funkcje języka C, które są przydatne to:

- Operator warunkowy

- Operator przecinka

Operator warunkowy jest często przydatny, ponieważ może być użyty do wyszukiwania określonego kodu zwracanej wartości, a następnie zwróci jedną z dwóch różnych wartości. Na przykład filtr w poniższym kodzie rozpoznaje wyjątek tylko wtedy, gdy wyjątek jest STATUS_INTEGER_OVERFLOW:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

Celem operatora warunkowego w tym przypadku jest głównie zapewnienie czytelności, ponieważ następujący kod generuje te same wyniki:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

Operator warunkowy jest bardziej użyteczny w sytuacjach, w których filtr ma być obliczany na wartość-1, EXCEPTION_CONTINUE_EXECUTION.

Operator przecinka umożliwia wykonanie wielu niezależnych operacji wewnątrz pojedynczego wyrażenia. Efektem jest (w przybliżeniu) wykonanie wielu instrukcji, a następnie zwrócenie wartości ostatniego wyrażenia. Na przykład, poniższy kod przechowuje kod wyjątku w zmiennej, a następnie ją sprawdza:

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>Zobacz także

[Pisanie procedury obsługi wyjątków](../cpp/writing-an-exception-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)