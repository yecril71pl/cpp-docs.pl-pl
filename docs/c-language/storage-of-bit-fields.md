---
title: Magazynowanie pól bitowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c39fa4455cfdc387ab5aa2068c80494a4a8810ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020097"
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