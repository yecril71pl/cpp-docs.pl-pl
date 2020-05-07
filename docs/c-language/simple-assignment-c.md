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
ms.openlocfilehash: 77c61101e9540a0d9469e7176eb15992a73b4b09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158285"
---
# <a name="simple-assignment-c"></a>Przypisanie proste (C)

Operator przypisywania prostego przypisuje jego prawy operand do lewego operandu. Wartość operandu Right jest konwertowana na typ wyrażenia przypisania i zastępuje wartość przechowywaną w obiekcie wydzielonym przez lewy argument operacji. Reguły konwersji dotyczące przypisywania są stosowane (zobacz [konwersje przypisań](../c-language/assignment-conversions.md)).

```
double x;
int y;

x = y;
```

W tym przykładzie wartość `y` jest konwertowana na typ **Double** i przypisany do. `x`

## <a name="see-also"></a>Zobacz też

[Operatory przypisania w języku C](../c-language/c-assignment-operators.md)
