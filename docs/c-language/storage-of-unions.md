---
title: Magazyn złożeń
ms.date: 11/04/2016
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
ms.openlocfilehash: 64e8b5184eeccd4de6d196e40ec464807bec93e7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211661"
---
# <a name="storage-of-unions"></a>Magazyn złożeń

Magazyn skojarzony ze zmienną Union to magazyn wymagany dla największego elementu członkowskiego Unii. Gdy mniejsza składowa jest przechowywana, zmienna Union może zawierać nieużywane miejsce w pamięci. Wszystkie elementy członkowskie są przechowywane w tym samym obszarze pamięci i zaczynają się na tym samym adresie. Wartość przechowywana jest zastępowana za każdym razem, gdy wartość zostanie przypisana do innego elementu członkowskiego. Na przykład:

```
union         /* Defines a union named x */
{
    char *a, b;
    float f[20];
} x;
```

Elementy członkowskie `x` Unii są w kolejności ich deklaracji, wskaźnikiem do **`char`** wartości, **`char`** wartości i tablicą **`float`** wartości. Magazyn przydzielony do `x` jest magazynem wymaganym dla 20-elementowej tablicy `f` , ponieważ `f` jest najdłuższym członkiem Unii. Ponieważ żaden tag nie jest skojarzony z Unią, jego typ ma wartość unnamed lub "Anonymous".

## <a name="see-also"></a>Zobacz także

[Deklaracje Unii](../c-language/union-declarations.md)
