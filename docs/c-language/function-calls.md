---
title: Wywołania funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls, about function calls
- function calls
ms.assetid: 2cfa897d-3874-4820-933c-e624f75d1712
ms.openlocfilehash: 495dc3cf77df79336af364eb80ea7edf17b54400
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227871"
---
# <a name="function-calls"></a>Wywołania funkcji

*Wywołanie funkcji* jest wyrażeniem, które przekazuje formant i argumenty (jeśli istnieją) do funkcji i ma postać:

*wyrażenie* (<sub>wybór</sub>*wyrażenia-list*)

*wyrażenie* WHERE jest nazwą funkcji lub szacuje *się, że jest to* Lista wyrażeń (rozdzielonych przecinkami). Wartości tych końcowych wyrażeń są argumentami przekazywanymi do funkcji. Jeśli funkcja nie zwraca wartości, deklaruje ją jako funkcję, która zwraca **`void`** .

Jeśli deklaracja istnieje przed wywołaniem funkcji, ale nie podano informacji dotyczących parametrów, wszelkie niezadeklarowane argumenty po prostu poddają się do zwykłych konwersji arytmetycznych.

> [!NOTE]
> Wyrażenia na liście argumentów funkcji można ocenić w dowolnej kolejności, dlatego argumenty, których wartości mogą być zmieniane przez skutki uboczne z innego argumentu mają niezdefiniowane wartości. Punkt sekwencji zdefiniowany przez operator wywołania funkcji gwarantuje tylko, że wszystkie efekty uboczne na liście argumentów są oceniane przed przekazaniem sterowania do wywołanej funkcji. (Należy zauważyć, że kolejność, w jakiej argumenty są wypychane na stosie, jest odrębna.) Zobacz [punkty sekwencji](../c-language/c-sequence-points.md) , aby uzyskać więcej informacji.

Jedynym wymaganiem w każdym wywołaniu funkcji jest to, że wyrażenie przed nawiasami musi obliczyć do adresu funkcji. Oznacza to, że funkcja może być wywoływana za pośrednictwem dowolnego wyrażenia wskaźnika funkcji.

## <a name="example"></a>Przykład

Ten przykład ilustruje wywołania funkcji wywoływane z **`switch`** instrukcji:

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

W tym przykładzie funkcja wywołuje w `main` ,

```
work( count, lift );
```

przekazuje zmienną całkowitą, `count` i adres funkcji `lift` do funkcji `work` . Należy zauważyć, że adres funkcji jest przesyłany po prostu przez podanie identyfikatora funkcji, ponieważ identyfikator funkcji oblicza wyrażenie wskaźnika. Aby użyć identyfikatora funkcji w ten sposób, funkcja musi być zadeklarowana lub zdefiniowana przed użyciem identyfikatora; w przeciwnym razie identyfikator nie jest rozpoznawany. W tym przypadku prototyp dla `work` jest podawany na początku `main` funkcji.

Parametr `function` w `work` jest zadeklarowany jako wskaźnik do funkcji pobierającej jeden **`int`** argument i zwracająca **`long`** wartość. Nawiasy wokół nazwy parametru są wymagane; bez nich, deklaracja określi funkcję zwracającą wskaźnik do **`long`** wartości.

Funkcja `work` wywołuje wybraną funkcję z wewnątrz pętli przy **`for`** użyciu następującego wywołania funkcji:

```
( *function )( i );
```

Jeden argument, `i` , jest przesyłany do wywołanej funkcji.

## <a name="see-also"></a>Zobacz także

[Funkcje](../c-language/functions-c.md)
