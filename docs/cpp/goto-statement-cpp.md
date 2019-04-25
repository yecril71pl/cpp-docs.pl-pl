---
title: goto — instrukcja (C++)
ms.date: 11/04/2016
f1_keywords:
- goto_cpp
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
ms.openlocfilehash: aac308905a01a52a4ce5ee0fa3be03f2f33ac1cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153700"
---
# <a name="goto-statement-c"></a>goto — instrukcja (C++)

**Goto** instrukcji bezwarunkowo przekazuje sterowanie do instrukcji, którego etykietą jest określony identyfikator.

## <a name="syntax"></a>Składnia

```
goto identifier;
```

## <a name="remarks"></a>Uwagi

Instrukcja labeled wyznaczonym przez `identifier` musi znajdować się w bieżącej funkcji. Wszystkie `identifier` nazwy są elementami członkowskimi wewnętrznej przestrzeni nazw i w związku z tym kolidują z innymi identyfikatorami.

Etykieta instrukcji jest istotny tylko **goto** instrukcji; w przeciwnym razie etykiety instrukcji są ignorowane. Nie można ponownie zadeklarować etykiety.

A **goto** instrukcja nie jest dozwolona na kontrola jest przekazywana do lokalizacji, która nakłada się na inicjowanie dowolną zmienną znajdującą się w zakresie w tej lokalizacji. Poniższy przykład wywołuje C2362:

```cpp
int goto_fn(bool b)
{
    if (!b)
    {
        goto exit;  // C2362
    }
    else
    { /*...*/ }

    int error_code = 42;

exit:
    return error_code;
}
```

Jest dobrą programowania stylu **podziału**, **nadal**, i **zwracają** instrukcji zamiast **przejdź do** instrukcji zawsze wtedy, gdy możliwe. Jednak ponieważ **podziału** instrukcji zamyka tylko jeden poziom w pętli, może być konieczne użycie **goto** instrukcję, aby zakończyć głęboko zagnieżdżonych pętli.

Aby uzyskać więcej informacji dotyczących etykiet i **goto** poufności informacji, zobacz [Labeled — instrukcje](../cpp/labeled-statements.md).

## <a name="example"></a>Przykład

W tym przykładzie **goto** instrukcji przekazuje sterowanie do punktu z etykietą `stop` podczas `i` jest równa 3.

```cpp
// goto_statement.cpp
#include <stdio.h>
int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 2; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 3 )
                goto stop;
        }
    }

    // This message does not print:
    printf_s( "Loop exited. i = %d\n", i );

    stop:
    printf_s( "Jumped to stop. i = %d\n", i );
}
```

```Output
Outer loop executing. i = 0
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 1
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 2
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 3
Inner loop executing. j = 0
Jumped to stop. i = 3
```

## <a name="see-also"></a>Zobacz także

[Instrukcje skoku](../cpp/jump-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
