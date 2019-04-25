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

**ANSI 3.5.2.1** kolejność alokacji pól bitowych w ramach int

Pola bitowe są przydzielane w ramach całkowitą od najmniej znaczącego najbardziej znaczący bit. W poniższym kodzie

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

bity mogłoby być ułożone w następujący sposób:

```
00000001 11110010
cccccccb bbbbaaaa
```

Ponieważ procesorów 80 x 86 przechowywać bajcie liczb całkowitych, przed bajcie, liczba całkowita 0x01F2 powyższych powinny być przechowywane w pamięci fizycznej jako 0xF2 następuje 0x01.

## <a name="see-also"></a>Zobacz także

[Struktury, złożenia, wyliczenia i pola bitowe](../c-language/structures-unions-enumerations-and-bit-fields.md)
