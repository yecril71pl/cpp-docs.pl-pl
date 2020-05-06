---
title: return — instrukcja (C)
ms.date: 11/04/2016
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
ms.openlocfilehash: c3975076ee65d267f3d278e20a7770e6750c06d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158388"
---
# <a name="return-statement-c"></a>return — instrukcja (C)

`return` Instrukcja kończy wykonywanie funkcji i zwraca kontrolę do funkcji wywołującej. Wykonanie wznowione w funkcji wywołującej w punkcie bezpośrednio po wywołaniu. `return` Instrukcja może również zwracać wartość do funkcji wywołującej. Aby uzyskać więcej informacji, zobacz [zwracany typ](../c-language/return-type.md) .

## <a name="syntax"></a>Składnia

*skok-instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<sub>wybór</sub> *wyrażenia* **zwrotu** **;**

Wartość *wyrażenia*, jeśli jest obecna, jest zwracana do funkcji wywołującej. Jeśli *wyrażenie* zostanie pominięte, zwracana wartość funkcji jest niezdefiniowana. Wyrażenie, jeśli jest obecny, jest oceniane, a następnie konwertowane na typ zwracany przez funkcję. Jeśli funkcja została zadeklarowana z typem `void`zwracanym, `return` instrukcja zawierająca wyrażenie generuje ostrzeżenie i wyrażenie nie jest oceniane.

Jeśli instrukcja `return` nie pojawia się w definicji funkcji, formant automatycznie wraca do wywołania funkcji po wykonaniu ostatniej instrukcji wywołanej funkcji. W takim przypadku zwracana wartość wywoływanej funkcji jest niezdefiniowana. Jeśli zwracana wartość nie jest wymagana, należy zadeklarować funkcję jako typu `void` zwracanego; w przeciwnym razie domyślnym typem zwracanym `int`jest.

Wielu programistów używa nawiasów, aby ująć argument *Expression* `return` instrukcji. Jednakże C nie wymaga nawiasów.

Ten przykład ilustruje `return` instrukcję:

```C
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

W tym przykładzie `main` funkcja wywołuje dwie funkcje: `sq` i. `draw` `sq` Funkcja zwraca wartość `x * x` do `main`, gdzie wartość zwracana jest przypisana do `y`. Nawiasy wokół wyrażenia Return w programie `sq` są oceniane jako część wyrażenia i nie są wymagane przez instrukcję return. Ponieważ wyrażenie zwracane jest oceniane przed przekonwertowaniem do typu zwracanego, `sq` wymusza, aby typ wyrażenia był typem zwracanym z rzutowania, aby zapobiec możliwemu przepełnieniu liczby całkowitej, co może prowadzić do nieoczekiwanych wyników. `draw` Funkcja jest zadeklarowana jako `void` funkcja. Drukuje wartości jego parametrów, a następnie pustą instrukcję return zwraca funkcję i nie zwraca wartości. Próba przypisania wartości `draw` zwracanej spowoduje, że zostanie wystawiony komunikat diagnostyczny. `main` Funkcja zwraca wartość `x` do systemu operacyjnego.

Dane wyjściowe przykładu wyglądają następująco:

```Output
i = 2147483647, ll = 4611686014132420609
```

## <a name="see-also"></a>Zobacz też

[Instrukcje](../c-language/statements-c.md)
