---
title: Przykłady wyrównania struktury
ms.date: 11/19/2018
helpviewer_keywords:
- structure alignment
- examples [C++], structure alignment
ms.assetid: 03d137bf-5cc4-472e-9583-6498f2534199
ms.openlocfilehash: 7c4b3ae29674e9c4fc27e8e175867339001b9a0d
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175343"
---
# <a name="examples-of-structure-alignment"></a>Przykłady wyrównania struktury

Następujące cztery przykłady zadeklarować, że wyrównany struktury lub Unii i dane porównawcze ilustrują układ tej struktury lub Unii w pamięci. Każda kolumna na ilustracji reprezentuje bajt pamięci i liczby w kolumnie wskazuje przesunięcie tego bajtu. Nazwa w drugim wierszu każdej rysunek odnosi się do nazwy zmiennej w deklaracji. Zacieniowaniu kolumn wskazują, że dopełnienie, które są wymagane do osiągnięcia określonego wyrównania.

## <a name="example-1"></a>Przykład 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![Układ struktury przykład 1 konwersji AMD](../build/media/vcamd_conv_ex_1_block.png "AMD konwersji przykład 1 struktury układu")

## <a name="example-2"></a>Przykład 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![Układ struktury przykład 2 konwersji AMD](../build/media/vcamd_conv_ex_2_block.png "AMD konwersji przykład 2 struktury układu")

## <a name="example-3"></a>Przykład 3

```C
// Total size = 22 bytes, alignment = 4 bytes (doubleword).

_declspec(align(4)) struct {
    char a;       // +0; size = 1 byte
    short b;      // +2; size = 2 bytes
    char c;       // +4; size = 1 byte
    int d;        // +8; size = 4 bytes
}
```

![Układ struktury przykład 2 konwersji AMD](../build/media/vcamd_conv_ex_3_block.png "AMD konwersji przykład 2 struktury układu")

## <a name="example-4"></a>Przykład 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![AMD konwersji przykład 4 złożenia layouit](../build/media/vcamd_conv_ex_4_block.png "AMD konwersji przykład 4 złożenia layouit")

## <a name="see-also"></a>Zobacz także

[Typy i magazyn](../build/types-and-storage.md)<br/>
