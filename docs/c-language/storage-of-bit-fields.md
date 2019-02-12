---
title: Magazynowanie pól bitowych
ms.date: 11/04/2016
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
ms.openlocfilehash: 4dbfb3c6ad27fb023881dafde74bb27132959085
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147532"
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
