---
title: Podsumowanie okresu istnienia i widoczności
ms.date: 11/04/2016
helpviewer_keywords:
- lifetime, and visibility
- visibility, identifiers
ms.assetid: ea05a253-7658-482c-9a6b-abd71169c42d
ms.openlocfilehash: 760973bba1798068b5a19ebeb7a285d241d4ef72
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220811"
---
# <a name="summary-of-lifetime-and-visibility"></a>Podsumowanie okresu istnienia i widoczności

Poniższa tabela zawiera podsumowanie okresu istnienia i cech charakterystycznych widoczności dla większości identyfikatorów. Pierwsze trzy kolumny zawierają atrybuty, które definiują okres istnienia i widoczność. Identyfikator o atrybutach przyznanych przez pierwsze trzy kolumny ma okres istnienia i widoczność pokazywany w czwartej i piątej kolumnie. Jednak tabela nie obejmuje wszystkich możliwych przypadków. Aby uzyskać więcej informacji, zapoznaj się z [klasami magazynu](../c-language/c-storage-classes.md) .

### <a name="summary-of-lifetime-and-visibility"></a>Podsumowanie okresu istnienia i widoczności

|Atrybuty:<br /><br /> Poziom|Element|Storage — Klasa<br /><br /> Specyfikator|Wynik:<br /><br /> Okres istnienia|Widoczność|
|---------------------------|----------|----------------------------------|--------------------------|----------------|
|Zakres pliku|Definicja zmiennej|**`static`**|Globalnie|Pozostała część pliku źródłowego, w którym występuje|
||Deklaracja zmiennej|**`extern`**|Globalnie|Pozostała część pliku źródłowego, w którym występuje|
||Prototyp lub definicja funkcji|**`static`**|Globalnie|Pojedynczy plik źródłowy|
||Prototyp funkcji|**`extern`**|Globalnie|Pozostała część pliku źródłowego|
|Zakres bloku|Deklaracja zmiennej|**`extern`**|Globalnie|Zablokowanie|
||Definicja zmiennej|**`static`**|Globalnie|Zablokowanie|
||Definicja zmiennej|**`auto`** oraz**`register`**|Lokalne|Zablokowanie|

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład ilustruje bloki, zagnieżdżanie i widoczność zmiennych:

### <a name="code"></a>Kod

```c
// Lifetime_and_Visibility.c

#include <stdio.h>

int i = 1;  // i defined at external level

int main()  // main function defined at external level
{
    printf_s( "%d\n", i ); // Prints 1 (value of external level i)
    {                                 // Begin first nested block
        int i = 2, j = 3;          // i and j defined at internal level
        printf_s( "%d %d\n", i, j );  // Prints 2, 3
        {                             // Begin second nested block
            int i = 0;                // i is redefined
            printf_s( "%d %d\n", i, j ); // Prints 0, 3
        }                             // End of second nested block
        printf_s( "%d\n", i );        // Prints 2 (outer definition
                                      //  restored)
    }                                 // End of first nested block
    printf_s( "%d\n", i );            // Prints 1 (external level
                                      // definition restored)
    return 0;
}
```

### <a name="comments"></a>Komentarze

W tym przykładzie istnieją cztery poziomy widoczności: poziom zewnętrzny i trzy poziomy blokowania. Wartości są drukowane na ekranie zgodnie z opisem w komentarzach po każdej instrukcji.

## <a name="see-also"></a>Zobacz także

[Okres istnienia, zakres, widoczność i połączenie](../c-language/lifetime-scope-visibility-and-linkage.md)
