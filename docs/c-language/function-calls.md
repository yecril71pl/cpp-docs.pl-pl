---
title: Wywołania funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls, about function calls
- function calls
ms.assetid: 2cfa897d-3874-4820-933c-e624f75d1712
ms.openlocfilehash: 2402f3fef77b19c0420f0c4a52407a730b53b1d5
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148208"
---
# <a name="function-calls"></a>Wywołania funkcji

A *wywołania funkcji* jest wyrażeniem, które przekazuje kontrolę i argumentów (jeśli istnieje) do funkcji i ma postać:

*wyrażenie* (*lista wyrażeń*<sub>zoptymalizowany pod kątem</sub>)

gdzie *wyrażenie* jest nazwą funkcji lub daje w wyniku adres funkcji i *lista wyrażeń* znajduje się lista wyrażeń (oddzielonych przecinkami). Wartości tych końcowych wyrażeń są argumentami przekazywanymi do funkcji. Jeśli funkcja nie zwraca wartości, a następnie możesz deklarować jako funkcja, która zwraca `void`.

Jeśli deklaracja istnieje przed wywołaniem funkcji, ale nie informacji znajduje się w odniesieniu do parametrów, argumenty niezadeklarowany po prostu przejść zwykle konwersje arytmetyczne.

> [!NOTE]
>  Może zostać oceniony wyrażeń na liście argumentów funkcji w dowolnej kolejności, dlatego argumentów, których wartości mogą zostać zmienione przez efekty uboczne z innego argumentu ma niezdefiniowane wartości. Tylko punktu sekwencji zdefiniowane przez operator wywołania funkcji gwarantuje, ze wszystkimi efektami ubocznymi na liście argumentów są oceniane przed kontrola przechodzi do wywołanej funkcji. (Zwróć uwagę, że kolejność, w której argumenty są wypychane na stos jest kwestią oddzielne). Zobacz [punktów sekwencji](../c-language/c-sequence-points.md) Aby uzyskać więcej informacji.

Jedynym wymaganiem w żadnym wywołaniu, funkcja jest, że przed nawiasów wyrażenia musi być adresu funkcji. Oznacza to, że funkcja może być wywoływana przez dowolne wyrażenie wskaźnika funkcji.

## <a name="example"></a>Przykład

Ten przykład ilustruje wywołania funkcji o nazwie z `switch` instrukcji:

```
int main()
{
    /* Function prototypes */

    long lift( int ), step( int ), drop( int );
    void work( int number, long (*function)(int i) );

    int select, count;
    .
    .
    .
    select = 1;
    switch( select )
    {
        case 1: work( count, lift );
                break;

        case 2: work( count, step );
                break;

        case 3: work( count, drop );
                /* Fall through to next case */
        default:
                break;
    }
}

/* Function definition */

void work( int number, long (*function)(int i) )
{
    int i;
    long j;

    for ( i = j = 0; i < number; i++ )
            j += ( *function )( i );
}
```

W tym przykładzie funkcja wywołania `main`,

```
work( count, lift );
```

przekazuje zmienną całkowitoliczbową `count`oraz adres funkcji `lift` funkcji `work`. Należy pamiętać, że adres funkcji jest przekazywany, podając identyfikator funkcji, ponieważ identyfikator funkcji ocenia wyrażenie wskaźnika. Aby użyć identyfikator funkcji w ten sposób, funkcja musi być zadeklarowane lub zdefiniowane przed użyciem identyfikator; w przeciwnym razie identyfikator nie został rozpoznany. W tym przypadku prototyp `work` znajduje się na początku `main` funkcji.

Parametr `function` w `work` jest deklarowana jako wskaźnik do funkcji, w których jedna `int` argumentów i zwracanie **długie** wartość. Nawiasy, w których nazwa parametru są wymagane; bez nich deklaracji należałoby określić funkcji zwracającej wskaźnik do **długie** wartość.

Funkcja `work` wywołuje funkcję wybranego z wewnątrz **dla** pętli za pomocą poniższe wywołanie funkcji:

```
( *function )( i );
```

Jeden argument `i`, jest przekazywany do funkcji o nazwie.

## <a name="see-also"></a>Zobacz także

[Funkcje](../c-language/functions-c.md)
