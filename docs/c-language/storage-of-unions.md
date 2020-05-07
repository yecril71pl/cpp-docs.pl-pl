---
title: Magazyn złożeń
ms.date: 11/04/2016
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
ms.openlocfilehash: 49b99dc17fd7bdddd8a47e3bfd5913a70a7631a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157932"
---
# <a name="storage-of-unions"></a>Magazyn złożeń

Magazyn skojarzony ze zmienną Union to magazyn wymagany dla największego elementu członkowskiego Unii. Gdy mniejsza składowa jest przechowywana, zmienna Union może zawierać nieużywane miejsce w pamięci. Wszystkie elementy członkowskie są przechowywane w tym samym obszarze pamięci i zaczynają się na tym samym adresie. Wartość przechowywana jest zastępowana za każdym razem, gdy wartość zostanie przypisana do innego elementu członkowskiego. Przykład:

```
union         /* Defines a union named x */
{
    char *a, b;
    float f[20];
} x;
```

Elementy członkowskie `x` Unii są w kolejności ich deklaracji, wskaźnik do `char` wartości, `char` wartość i tablica wartości **zmiennoprzecinkowych** . Magazyn przydzielony do `x` jest magazynem wymaganym dla 20-elementowej `f`tablicy, `f` ponieważ jest najdłuższym członkiem Unii. Ponieważ żaden tag nie jest skojarzony z Unią, jego typ ma wartość unnamed lub "Anonymous".

## <a name="see-also"></a>Zobacz też

[Deklaracje złożeń](../c-language/union-declarations.md)
