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

Operator przypisania prostego przypisuje jej prawy operand operand po lewej stronie. Wartość prawy operand jest konwertowany na typ wyrażenia przypisania i zastępuje wartość przechowywaną w obiekcie wyznaczonym przez lewy operand. Zastosuj reguły konwersji dla przypisania (zobacz [konwersje przypisań](../c-language/assignment-conversions.md)).

```
double x;
int y;

x = y;
```

W tym przykładzie wartość `y` jest konwertowany na typ **double** i przypisane do `x`.

## <a name="see-also"></a>Zobacz także

[Operatory przypisania w języku C](../c-language/c-assignment-operators.md)
