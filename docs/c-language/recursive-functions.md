---
title: Funkcje rekursywne
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], recursive
- function calls, recursive
- functions [C], calling recursively
- recursive function calls
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
ms.openlocfilehash: 82f0c820ab75fda4bae83db78fa402d7a07cb7fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232137"
---
# <a name="recursive-functions"></a>Funkcje rekursywne

Każda funkcja w programie C może być wywoływana cyklicznie; oznacza to, że może wywoływać sam siebie. Liczba wywołań cyklicznych jest ograniczona do rozmiaru stosu. Aby uzyskać informacje na temat opcji konsolidatora, które ustawiają rozmiar stosu, zobacz [/Stack (](../build/reference/stack-stack-allocations.md) /stack) — opcja konsolidatora. Za każdym razem, gdy funkcja jest wywoływana, nowy magazyn jest przypisywany do **parametrów i dla zmiennych autoi** **rejestru** , tak aby ich wartości w poprzednich, nieukończonych wywołaniach nie były zastępowane. Parametry są dostępne tylko bezpośrednio dla wystąpienia funkcji, w której zostały utworzone. Poprzednie parametry nie są bezpośrednio dostępne dla wynikający z tego, wystąpienia funkcji.

Należy zauważyć, że zmienne zadeklarowane za pomocą magazynu **statycznego** nie wymagają nowego magazynu przy każdym wywołaniu cyklicznym. Ich magazyn istnieje na okres istnienia programu. Każde odwołanie do tej zmiennej uzyskuje dostęp do tego samego obszaru magazynu.

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

## <a name="see-also"></a>Zobacz też

[Wywołania funkcji](../c-language/function-calls.md)
