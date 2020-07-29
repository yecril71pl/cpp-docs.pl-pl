---
title: goto — instrukcja (C++)
ms.date: 11/04/2016
f1_keywords:
- goto_cpp
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
ms.openlocfilehash: e56ebfadea0d643ac68e2ace722a39587bd01312
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223710"
---
# <a name="goto-statement-c"></a>goto — instrukcja (C++)

**`goto`** Instrukcja bezwarunkowo przenosi kontrolę do instrukcji oznaczonej przez określony identyfikator.

## <a name="syntax"></a>Składnia

```
goto identifier;
```

## <a name="remarks"></a>Uwagi

Instrukcja oznaczona etykietą `identifier` musi znajdować się w bieżącej funkcji. Wszystkie `identifier` nazwy są członkami wewnętrznej przestrzeni nazw i w związku z tym nie zakłócają innych identyfikatorów.

Etykieta instrukcji jest istotna tylko dla **`goto`** instrukcji; w przeciwnym razie etykiety instrukcji są ignorowane. Nie można ponownie zadeklarować etykiet.

**`goto`** Instrukcja nie może przekazywać kontroli do lokalizacji, która pomija inicjalizację dowolnej zmiennej, która znajduje się w zakresie w tej lokalizacji. Poniższy przykład podnosi C2362:

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

Dobrym stylem programowania jest użycie **`break`** **`continue`** instrukcji,, i **`return`** zamiast instrukcji, gdy jest **`goto`** to możliwe. Jednak ze względu na to, że **`break`** instrukcja kończy się tylko z jednego poziomu pętli, może być konieczne użycie **`goto`** instrukcji, aby wyjść z głęboko zagnieżdżonej pętli.

Aby uzyskać więcej informacji na temat etykiet i **`goto`** instrukcji, zobacz [instrukcje z etykietami](../cpp/labeled-statements.md).

## <a name="example"></a>Przykład

W tym przykładzie **`goto`** instrukcja przekazuje formant do punktu oznaczonego etykietą, `stop` gdy `i` jest równa 3.

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
