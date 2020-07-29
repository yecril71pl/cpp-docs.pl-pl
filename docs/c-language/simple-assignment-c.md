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
ms.openlocfilehash: 64112a54828a9a6626e78e556e8fe6dc52a3300f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229548"
---
# <a name="simple-assignment-c"></a>Przypisanie proste (C)

Operator przypisywania prostego przypisuje jego prawy operand do lewego operandu. Wartość operandu Right jest konwertowana na typ wyrażenia przypisania i zastępuje wartość przechowywaną w obiekcie wydzielonym przez lewy argument operacji. Reguły konwersji dotyczące przypisywania są stosowane (zobacz [konwersje przypisań](../c-language/assignment-conversions.md)).

```
double x;
int y;

x = y;
```

W tym przykładzie wartość `y` jest konwertowana na typ **`double`** i przypisany do `x` .

## <a name="see-also"></a>Zobacz także

[Operatory przypisania języka C](../c-language/c-assignment-operators.md)
