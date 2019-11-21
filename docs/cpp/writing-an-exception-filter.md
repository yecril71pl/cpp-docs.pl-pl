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

Możesz obsłużyć wyjątek wykonując skok na poziom programu obsługi wyjątków lub kontynuując wykonywanie. Instead of using the exception handler code to handle the exception and falling through, you can use *filter* to clean up the problem and then, by returning -1, resume normal flow without clearing the stack.

> [!NOTE]
>  Niektóre wyjątki nie mogą być kontynuowane. If *filter* evaluates to -1 for such an exception, the system raises a new exception. When you call [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception), you determine whether the exception will continue.

For example, the following code uses a function call in the *filter* expression: this function handles the problem and then returns -1 to resume normal flow of control:

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

It is a good idea to use a function call in the *filter* expression whenever *filter* needs to do anything complex. Obliczanie wyrażenia powoduje wykonanie funkcji, w tym przypadku jest to `Eval_Exception`.

Note the use of [GetExceptionCode](/windows/win32/Debug/getexceptioncode) to determine the exception. Musisz wywołać tę funkcję wewnątrz samego filtru. `Eval_Exception` cannot call `GetExceptionCode`, but it must have the exception code passed to it.

Ten program obsługi wyjątków przekazuje sterowanie do innego programu obsługi wyjątków, o ile wyjątek nie dotyczy przepełnienia liczby całkowitej lub zmiennoprzecinkowej. Jeśli tak się stanie, program obsługi wyjątku wywołuje funkcję (`ResetVars` jest tylko przykładem, a nie funkcją API), aby zresetować niektóre zmienne globalne. *Statement-block-2*, which in this example is empty, can never be executed because `Eval_Exception` never returns EXCEPTION_EXECUTE_HANDLER (1).

Używanie wywołań funkcji jest dobrą techniką ogólnego przeznaczenia do radzenia sobie ze złożonymi wyrażeniami filtrującymi. Dwie inne funkcje języka C, które są przydatne to:

- Operator warunkowy

- Operator przecinka

Operator warunkowy jest często przydatny, ponieważ może być użyty do wyszukiwania określonego kodu zwracanej wartości, a następnie zwróci jedną z dwóch różnych wartości. For example, the filter in the following code recognizes the exception only if the exception is STATUS_INTEGER_OVERFLOW:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

Celem operatora warunkowego w tym przypadku jest głównie zapewnienie czytelności, ponieważ następujący kod generuje te same wyniki:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

The conditional operator is more useful in situations where you might want the filter to evaluate to -1, EXCEPTION_CONTINUE_EXECUTION.

Operator przecinka umożliwia wykonanie wielu niezależnych operacji wewnątrz pojedynczego wyrażenia. Efektem jest (w przybliżeniu) wykonanie wielu instrukcji, a następnie zwrócenie wartości ostatniego wyrażenia. Na przykład, poniższy kod przechowuje kod wyjątku w zmiennej, a następnie ją sprawdza:

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>Zobacz także

[Writing an exception handler](../cpp/writing-an-exception-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)