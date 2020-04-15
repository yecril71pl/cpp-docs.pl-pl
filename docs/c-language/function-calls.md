---
title: Wywołania funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls, about function calls
- function calls
ms.assetid: 2cfa897d-3874-4820-933c-e624f75d1712
ms.openlocfilehash: cce1a888f3e1224822ab4e97c67bf59da4c46fc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334570"
---
# <a name="function-calls"></a>Wywołania funkcji

*Wywołanie funkcji* jest wyrażeniem, które przekazuje kontrolę i argumenty (jeśli istnieją) do funkcji i ma formularz:

*wyrażenie* *(wyrażenie-lista*<sub>opt)</sub>

gdzie *wyrażenie* jest nazwą funkcji lub ocenia adres funkcji, a *lista wyrażeń* jest listą wyrażeń (oddzielonych przecinkami). Wartości tych końcowych wyrażeń są argumentami przekazywanymi do funkcji. Jeśli funkcja nie zwraca wartości, należy zadeklarować, że `void`jest to funkcja zwracająca .

Jeśli deklaracja istnieje przed wywołaniem funkcji, ale nie podano żadnych informacji dotyczących parametrów, wszelkie niezadeklarowane argumenty po prostu przechodzą zwykłe konwersje arytmetyczne.

> [!NOTE]
> Wyrażenia na liście argumentów funkcji mogą być oceniane w dowolnej kolejności, więc argumenty, których wartości mogą zostać zmienione przez skutki uboczne z innego argumentu mają wartości niezdefiniowane. Punkt sekwencji zdefiniowany przez operator wywołania funkcji gwarantuje tylko, że wszystkie skutki uboczne na liście argumentów są oceniane przed przepuszczenia kontroli do wywoływana funkcja. (Należy zauważyć, że kolejność, w jakiej argumenty są wypychane na stosie jest osobną sprawą.) Zobacz [punkty sekwencji, aby](../c-language/c-sequence-points.md) uzyskać więcej informacji.

Jedynym wymaganiem w każdym wywołaniu funkcji jest to, że wyrażenie przed nawiasami musi ocenić adres funkcji. Oznacza to, że funkcja może być wywoływana za pośrednictwem dowolnego wyrażenia wskaźnik funkcji.

## <a name="example"></a>Przykład

W tym przykładzie przedstawiono `switch` wywołania funkcji wywoływane z instrukcji:

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

W tym przykładzie wywołanie funkcji w `main`,

```
work( count, lift );
```

przekazuje zmienną całkowitą, `count`a adres funkcji `lift` do funkcji `work`. Należy zauważyć, że adres funkcji jest przekazywany po prostu przez podanie identyfikatora funkcji, ponieważ identyfikator funkcji ocenia wyrażenie wskaźnika. Aby w ten sposób użyć identyfikatora funkcji, funkcja musi być zadeklarowana lub zdefiniowana przed użyciem identyfikatora; w przeciwnym razie identyfikator nie zostanie rozpoznany. W takim przypadku prototyp `work` dla jest podany na `main` początku funkcji.

Parametr `function` w `work` jest zadeklarowany jako wskaźnik do `int` funkcji przy jednym argumentie i zwracaniu **wartości długiej.** Nawiasy wokół nazwy parametru są wymagane; bez nich deklaracja określi funkcję zwracającą wskaźnik do wartości **długiej.**

Funkcja `work` wywołuje wybraną funkcję z wewnątrz pętli **for** za pomocą następującego wywołania funkcji:

```
( *function )( i );
```

Jeden argument `i`, jest przekazywany do wywoływana funkcja.

## <a name="see-also"></a>Zobacz też

[Funkcje](../c-language/functions-c.md)
