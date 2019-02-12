---
title: Magazyn złożeń
ms.date: 11/04/2016
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
ms.openlocfilehash: 49b99dc17fd7bdddd8a47e3bfd5913a70a7631a7
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152823"
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

## <a name="see-also"></a>Zobacz także

[Deklaracje złożeń](../c-language/union-declarations.md)
