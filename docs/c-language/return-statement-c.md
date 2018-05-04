---
title: Zwraca Statement (C) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 08407f26e3c3d9064fded1620538262b0c91e2ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="return-statement-c"></a>return — instrukcja (C)
`return` Instrukcji kończy wykonywanie funkcji i zwraca sterowania do funkcji wywołującej. Wznawia wykonywanie w funkcji wywołującej w momencie bezpośrednio po wywołaniu. A `return` instrukcji można również zwrócić wartość do funkcji wywołującej. Zobacz [typu zwracanego](../c-language/return-type.md) Aby uzyskać więcej informacji.  
  
## <a name="syntax"></a>Składnia  
 *Instrukcja skok*:  
 **Zwraca***wyrażenie* opt **;**   
  
 Wartość *wyrażenie*, jeśli istnieje, jest zwracana do wywoływania funkcji. Jeśli *wyrażenie* jest pominięty, zwracana wartość funkcji jest niezdefiniowany. Wyrażenie, jeśli istnieje, jest oceniane i następnie konwertowana na typ zwracany przez funkcję. Jeśli funkcja została zadeklarowana z typem zwracanym `void`, `return` instrukcji zawierającej wyrażenie generuje ostrzeżenie i nie jest obliczane wyrażenie.  
  
 Jeśli nie `return` występuje instrukcja w definicji funkcji, kontroli automatycznie powróci do wywoływania funkcji po wykonaniu ostatniej instrukcji wywoływana funkcja. W takim przypadku wartość zwracaną wywołana funkcja jest niezdefiniowany. Jeśli wartości zwracanej nie jest wymagana, funkcji, aby zadeklarować `void` zwracany typ; w przeciwnym razie zwracany typ jest domyślnie `int`.  
  
 Wielu programistów Użyj nawiasów, należy ująć *wyrażenie* argument `return` instrukcji. Jednak C nie wymaga nawiasów.  
  
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
  
 W tym przykładzie `main` funkcja wywołuje dwie funkcje: `sq` i `draw`. `sq` Funkcja zwraca wartość `x * x` do `main`, gdzie wartość zwracana jest przypisany do `y`. Nawiasy otaczające wyrażenie zwracane w `sq` są traktowane jako część wyrażenia i nie są wymagane przez instrukcję return. Ponieważ zwracany wyrażenie jest obliczane, zanim zostanie przekonwertowane na typ zwracany `sq` wymusza typ wyrażenia zwracanego typu o rzutowanie w celu uniknięcia przepełnienia możliwa liczba całkowita, która może prowadzić do nieoczekiwanych wyników. `draw` Funkcji jest zadeklarowany jako `void` funkcji. Wyświetla wartości jego parametrów, a następnie pusta instrukcja return kończy się funkcji i nie zwraca wartości. Próba przypisania wartość zwracaną `draw` spowodowałoby diagnostycznych komunikat zostanie wysłane. `main` Funkcja zwraca wartość `x` do systemu operacyjnego.  
  
 Dane wyjściowe przykładu wygląda następująco:  
  
```Output  
i = 2147483647, ll = 4611686014132420609  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje](../c-language/statements-c.md)