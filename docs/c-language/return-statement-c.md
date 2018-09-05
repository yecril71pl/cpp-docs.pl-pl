---
title: Zwróć Statement (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2bd1f1a9f441a8c4b5e2cf9418653a6a0544380e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759086"
---
# <a name="return-statement-c"></a>return — instrukcja (C)
`return` Instrukcja kończy wykonywanie funkcji i przekazuje sterowanie do funkcji wywołującej. Wznawia wykonywanie w funkcji wywołującej w punkcie, w następującej natychmiast po wywołaniu. A `return` instrukcji może również zwracać wartość do funkcji wywołującej. Zobacz [typie zwracanym](../c-language/return-type.md) Aby uzyskać więcej informacji.  
  
## <a name="syntax"></a>Składnia

*Instrukcja skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Zwróć** *wyrażenie*<sub>zoptymalizowany pod kątem</sub> **;**

Wartość *wyrażenie*, jeśli jest obecny, jest zwracana do funkcji wywołującej. Jeśli *wyrażenie* jest pominięty, wartość zwracana funkcji jest niezdefiniowane. Wyrażenie, jeśli jest obecny, jest obliczane i następnie przekonwertować na typ zwracany przez funkcję. Jeśli funkcja została zadeklarowana z typem zwracanym `void`, `return` instrukcji zawierającej wyrażenie generuje ostrzeżenie i wyrażenie nie jest oceniany.  
  
Jeśli nie `return` występuje instrukcja w definicji funkcji, sterowanie automatycznie powraca do funkcji wywołującej po wykonaniu ostatnią instrukcję wywołanej funkcji. W tym przypadku wartość zwracaną wywołanej funkcji jest niezdefiniowane. Jeśli wartość zwracana nie jest wymagana, Zadeklaruj funkcję mieć `void` zwracany typ; w przeciwnym razie domyślny typ zwracany jest `int`.  
  
Wielu programistów Użyj nawiasów, aby ująć *wyrażenie* argument `return` instrukcji. Jednak C nie wymaga nawiasów.  
  
W tym przykładzie przedstawiono `return` instrukcji:  
  
```  
#include <limits.h>  
#include <stdio.h>  
  
void draw( int i, long long ll );  
long long sq( int s );  
  
int main()  
{  
    long long y;  
    int x = INT_MAX;  
  
    y = sq( x );  
    draw( x, y );  
    return x;  
}  
  
long long sq( int s )  
{  
    // Note that parentheses around the return expression   
    // are allowed but not required here.  
    return( s * (long long)s );  
}  
  
void draw( int i, long long ll )  
{  
    printf( "i = %d, ll = %lld\n", i, ll );  
    return;  
}  
  
```  
  
W tym przykładzie `main` funkcja wywołuje dwie funkcje: `sq` i `draw`. `sq` Funkcja zwraca wartość `x * x` do `main`, gdzie wartość zwracana jest przypisywana do `y`. Nawiasy, zwracane wyrażenie w `sq` są oceniane jako część wyrażenia, a nie są wymagane przez instrukcję return. Ponieważ zwracane wyrażenie jest oceniane przed jest konwertowany na typ zwracany `sq` wymusza typ wyrażenia jako zwracany typ z rzutowanie w celu uniknięcia przepełnienia możliwa liczba całkowita, która może prowadzić do nieoczekiwanych wyników. `draw` Funkcja jest zadeklarowana jako `void` funkcji. Wyświetla wartości jego parametrów a następnie pustą instrukcję return kończy się funkcja nie zwraca wartości. Próba przypisania wartość zwracaną przez `draw` spowodowałoby komunikat diagnostyczny zostanie wysłane. `main` Następnie funkcja zwraca wartość `x` systemowi operacyjnemu.  
  
Dane wyjściowe z przykładu wygląda następująco:  
  
```Output  
i = 2147483647, ll = 4611686014132420609  
```  
  
## <a name="see-also"></a>Zobacz też  
[Instrukcje](../c-language/statements-c.md)