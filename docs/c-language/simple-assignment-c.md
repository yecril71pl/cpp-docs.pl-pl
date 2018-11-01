---
title: Przypisanie proste (C)
ms.date: 11/04/2016
helpviewer_keywords:
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
ms.openlocfilehash: 76c48fc6774f97bab69f916ad7e5176e91d004ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574918"
---
# <a name="simple-assignment-c"></a>Przypisanie proste (C)

Operator przypisania prostego przypisuje jej prawy operand operand po lewej stronie. Wartość prawy operand jest konwertowany na typ wyrażenia przypisania i zastępuje wartość przechowywaną w obiekcie wyznaczonym przez lewy operand. Zastosuj reguły konwersji dla przypisania (zobacz [konwersje przypisań](../c-language/assignment-conversions.md)).

```
double x;
int y;

x = y;
```

W tym przykładzie wartość `y` jest konwertowany na typ **double** i przypisane do `x`.

## <a name="see-also"></a>Zobacz też

[Operatory przypisania w języku C](../c-language/c-assignment-operators.md)