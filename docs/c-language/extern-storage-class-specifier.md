---
title: extern — specyfikator klasy magazynowania
ms.date: 07/10/2018
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
ms.openlocfilehash: 6bbae7c778f5196ac0dca387265499b27119a367
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233837"
---
# <a name="extern-storage-class-specifier"></a>extern — specyfikator klasy magazynowania

Zmienna zadeklarowana ze specyfikatorem klasy magazynu **extern** jest odwołaniem do zmiennej o tej samej nazwie zdefiniowanej w innym pliku źródłowym. Służy do widoczności definicji zmiennej na poziomie zewnętrznym. Zmienna zadeklarowana jako **extern** nie ma magazynu przypisanego do siebie. jest to tylko nazwa.

## <a name="example"></a>Przykład

Ten przykład ilustruje deklaracje na poziomie wewnętrznym i zewnętrznym:

```c

// Source1.c

int i = 1;

// Source2. c

#include <stdio.h>

// Refers to the i that is defined in Source1.c:
extern int i;

void func(void);

int main()
{
    // Prints 1:
    printf_s("%d\n", i);
    func();
    return;
}

void func(void)
{
    // Address of global i assigned to pointer variable:
    static int *external_i = &i;

    // This definition of i hides the global i in Source.c:
    int i = 16;

    // Prints 16, 1:
    printf_s("%d\n%d\n", i, *external_i);
}
```

W tym przykładzie zmienna `i` jest zdefiniowana w Source1. c z początkową wartością 1. Deklaracja **extern** w SOURCE2. c sprawia, że w tym pliku jest widoczne "i".

W `func` funkcji adres zmiennej `i` globalnej jest używany do inicjowania zmiennej `external_i`wskaźnika **statycznego** . Dzieje się tak, ponieważ zmienna globalna ma **statyczny** okres istnienia, co oznacza, że jej adres nie zmienia się podczas wykonywania programu. Następnie zmienna `i` jest definiowana w zakresie `func` jako zmienna lokalna z wartością początkową 16. Ta definicja nie wpływa na wartość na poziomie `i`zewnętrznym, która jest ukryta przy użyciu jego nazwy dla zmiennej lokalnej. Wartość globalnego `i` jest teraz dostępna tylko za pomocą wskaźnika `external_i`.

## <a name="see-also"></a>Zobacz też

[Specyfikatory klasy magazynowania dla deklaracji na poziomie wewnętrznym](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
