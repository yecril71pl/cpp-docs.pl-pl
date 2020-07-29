---
title: Funkcje rekursywne
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], recursive
- function calls, recursive
- functions [C], calling recursively
- recursive function calls
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
ms.openlocfilehash: 8979d386c6fc3415cd50159250db8488cb917cee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199519"
---
# <a name="recursive-functions"></a>Funkcje rekursywne

Każda funkcja w programie C może być wywoływana cyklicznie; oznacza to, że może wywoływać sam siebie. Liczba wywołań cyklicznych jest ograniczona do rozmiaru stosu. Aby uzyskać informacje na temat opcji konsolidatora, które ustawiają rozmiar stosu, zobacz opcję konsolidatora [ `/STACK` stosu](../build/reference/stack-stack-allocations.md) . Za każdym razem, gdy funkcja jest wywoływana, nowy magazyn jest przypisywany do parametrów i **`auto`** dla **`register`** zmiennych i, tak aby ich wartości w poprzednich, nieukończonych wywołaniach nie były zastępowane. Parametry są dostępne tylko bezpośrednio dla wystąpienia funkcji, w której zostały utworzone. Poprzednie parametry nie są bezpośrednio dostępne dla wynikający z tego, wystąpienia funkcji.

Należy zauważyć, że zmienne zadeklarowane za pomocą **`static`** magazynu nie wymagają nowego magazynu przy każdym wywołaniu cyklicznym. Ich magazyn istnieje na okres istnienia programu. Każde odwołanie do tej zmiennej uzyskuje dostęp do tego samego obszaru magazynu.

## <a name="example"></a>Przykład

Ten przykład ilustruje cykliczne wywołania:

```C
int factorial( int num );      /* Function prototype */

int main()
{
    int result, number;
    .
    .
    .
    result = factorial( number );
}

int factorial( int num )      /* Function definition */
{
    .
    .
    .
    if ( ( num > 0 ) || ( num <= 10 ) )
        return( num * factorial( num - 1 ) );
}
```

## <a name="see-also"></a>Zobacz także

[Wywołania funkcji](../c-language/function-calls.md)
