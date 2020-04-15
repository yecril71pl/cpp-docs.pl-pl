---
title: Pisanie filtru wyjątku
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: 05d3aa79d1293001e80a77b3171b7a4607cd81c7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369486"
---
# <a name="writing-an-exception-filter"></a>Pisanie filtru wyjątku

Możesz obsłużyć wyjątek wykonując skok na poziom programu obsługi wyjątków lub kontynuując wykonywanie. Zamiast używać kodu obsługi wyjątków do obsługi wyjątku i przechodzenia przez, można użyć *filtru,* aby usunąć problem, a następnie, zwracając -1, wznowić normalny przepływ bez czyszczenia stosu.

> [!NOTE]
> Niektóre wyjątki nie mogą być kontynuowane. Jeśli *filtr* ocenia do -1 dla takiego wyjątku, system zgłasza nowy wyjątek. Po [wywołaniu RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception), można określić, czy wyjątek będzie kontynuowany.

Na przykład następujący kod używa wywołania funkcji w wyrażeniu *filtru:* ta funkcja obsługuje problem, a następnie zwraca -1, aby wznowić normalny przepływ kontroli:

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

Dobrym pomysłem jest użycie wywołania funkcji w wyrażeniu *filtru,* gdy *filtr* musi wykonać coś złożonego. Obliczanie wyrażenia powoduje wykonanie funkcji, w tym przypadku jest to `Eval_Exception`.

Należy zauważyć użycie [GetExceptionCode](/windows/win32/Debug/getexceptioncode) do określenia wyjątku. Musisz wywołać tę funkcję wewnątrz samego filtru. `Eval_Exception`nie `GetExceptionCode`można wywołać , ale musi mieć kod wyjątku przekazany do niego.

Ten program obsługi wyjątków przekazuje sterowanie do innego programu obsługi wyjątków, o ile wyjątek nie dotyczy przepełnienia liczby całkowitej lub zmiennoprzecinkowej. Jeśli tak się stanie, program obsługi wyjątku wywołuje funkcję (`ResetVars` jest tylko przykładem, a nie funkcją API), aby zresetować niektóre zmienne globalne. *Instrukcja-block-2*, który w tym przykładzie `Eval_Exception` jest pusty, nigdy nie może być wykonywane, ponieważ nigdy nie zwraca EXCEPTION_EXECUTE_HANDLER (1).

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

Operator warunkowy jest bardziej przydatne w sytuacjach, w których może chcesz filtr ocenić do -1, EXCEPTION_CONTINUE_EXECUTION.

Operator przecinka umożliwia wykonanie wielu niezależnych operacji wewnątrz pojedynczego wyrażenia. Efektem jest (w przybliżeniu) wykonanie wielu instrukcji, a następnie zwrócenie wartości ostatniego wyrażenia. Na przykład, poniższy kod przechowuje kod wyjątku w zmiennej, a następnie ją sprawdza:

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>Zobacz też

[Pisanie obsługi wyjątków](../cpp/writing-an-exception-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
