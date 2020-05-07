---
title: Magazynowanie pól bitowych
ms.date: 11/04/2016
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
ms.openlocfilehash: 4dbfb3c6ad27fb023881dafde74bb27132959085
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157893"
---
# <a name="storage-of-bit-fields"></a>Magazynowanie pól bitowych

**3.5.2.1 ANSI** Kolejność alokacji pól bitowych w ramach int

Pola bitowe są przypisywane w postaci liczby całkowitej od najmniej znaczącej do najbardziej znaczącego bitu. W poniższym kodzie

```
struct mybitfields
{
   unsigned a : 4;
   unsigned b : 5;
   unsigned c : 7;
} test;

int main( void )
{
   test.a = 2;
   test.b = 31;
   test.c = 0;
}
```

bity można rozmieścić w następujący sposób:

```
00000001 11110010
cccccccb bbbbaaaa
```

Ponieważ procesory 80x86 przechowują niską liczbę wartości całkowitych przed bajtem, liczba całkowita 0x01F2 powyżej byłaby przechowywana w pamięci fizycznej jako 0xF2, a po nim 0x01.

## <a name="see-also"></a>Zobacz też

[Struktury, złożenia, wyliczenia i pola bitowe](../c-language/structures-unions-enumerations-and-bit-fields.md)
