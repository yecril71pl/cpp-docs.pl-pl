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
ms.openlocfilehash: e3242f86e30dcf3227586400b83266ad366ec7e8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217106"
---
# <a name="extern-storage-class-specifier"></a>extern — specyfikator klasy magazynowania

Zmienna zadeklarowana ze **`extern`** specyfikatorem klasy magazynu jest odwołaniem do zmiennej o tej samej nazwie zdefiniowanej w innym pliku źródłowym. Służy do widoczności definicji zmiennej na poziomie zewnętrznym. Zmienna zadeklarowana jako nie **`extern`** ma magazynu przypisanego do siebie; jest tylko nazwą.

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

W tym przykładzie zmienna `i` jest zdefiniowana w Source1. c z początkową wartością 1. **`extern`** Deklaracja w SOURCE2. c powoduje, że w tym pliku jest widoczne "i".

W `func` funkcji adres zmiennej globalnej `i` jest używany do inicjowania **`static`** zmiennej wskaźnika `external_i` . Dzieje się tak, ponieważ zmienna globalna ma **`static`** okres istnienia, co oznacza, że jej adres nie zmienia się podczas wykonywania programu. Następnie zmienna `i` jest definiowana w zakresie `func` jako zmienna lokalna z wartością początkową 16. Ta definicja nie wpływa na wartość na poziomie zewnętrznym `i` , która jest ukryta przy użyciu jego nazwy dla zmiennej lokalnej. Wartość globalnego `i` jest teraz dostępna tylko za pomocą wskaźnika `external_i` .

## <a name="see-also"></a>Zobacz także

[Specyfikatory klasy magazynowania dla deklaracji na poziomie wewnętrznym](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
