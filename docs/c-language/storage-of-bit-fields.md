---
title: Magazynowanie pól bitowych
ms.date: 11/04/2016
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
ms.openlocfilehash: 7aa6e02c347ff14bb0552320567b343c7215ebc7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499092"
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

## <a name="see-also"></a>Zobacz też

[Struktury, złożenia, wyliczenia i pola bitowe](../c-language/structures-unions-enumerations-and-bit-fields.md)