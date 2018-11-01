---
title: Błąd kompilatora C2719
ms.date: 11/04/2016
f1_keywords:
- C2719
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
ms.openlocfilehash: d635601fbf8b36218fb47c09444f3f5d023c823e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653118"
---
# <a name="compiler-error-c2719"></a>Błąd kompilatora C2719

"parametru": formalny parametr z __declspec(align('#')) nie zostanie wyrównany

[Wyrównać](../../cpp/align-cpp.md) `__declspec` modyfikator nie jest dozwolona w parametrów funkcji. Funkcja parametrów wyrównanie jest kontrolowana przez Konwencję wywołania używany. Aby uzyskać więcej informacji, zobacz [Konwencje wywoływania](../../cpp/calling-conventions.md).

Poniższy przykład generuje C2719 i pokazuje, jak go naprawić:

```
// C2719.cpp
void func(int __declspec(align(32)) i);   // C2719
// try the following line instead
// void func(int i);
```