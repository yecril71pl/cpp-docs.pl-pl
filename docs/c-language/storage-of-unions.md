---
title: Magazyn złożeń
ms.date: 11/04/2016
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
ms.openlocfilehash: 06444151a453017055667885304ecb59534f5774
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602231"
---
# <a name="storage-of-unions"></a>Magazyn złożeń

Magazyn skojarzony ze zmienną typu Unia jest magazynu wymaganego dla największego elementu Członkowskiego Unii. Gdy członek mniejszych są przechowywane, union zmienna może zawierać miejsca nieużywanej pamięci. Wszystkie elementy członkowskie są przechowywane w tej samej przestrzeni pamięci i rozpoczynają się od tego samego adresu. Wartość przechowywana jest zastąpione każdorazowo, gdy wartość jest przypisywana do innego członka. Na przykład:

```
union         /* Defines a union named x */
{
    char *a, b;
    float f[20];
} x;
```

Elementy członkowskie `x` Unii są w kolejności ich deklaracji, wskaźnik do `char` wartość `char` wartość i tablicę **float** wartości. Magazyn przydzielony do `x` magazynu wymaganych do 20-elementowej tablicy `f`, ponieważ `f` jest najdłuższym składowej Unii. Ponieważ żaden tag jest skojarzony z Unią, jego typ jest bez nazwy i "anonymous".

## <a name="see-also"></a>Zobacz też

[Deklaracje złożeń](../c-language/union-declarations.md)