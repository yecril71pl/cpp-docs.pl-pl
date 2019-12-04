---
title: Błąd kompilatora C2705
ms.date: 11/04/2016
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 1cd46db8e4cb237bebd9568409ecadf0ff84cdf8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758310"
---
# <a name="compiler-error-c2705"></a>Błąd kompilatora C2705

"label": niedozwolony skok do zakresu "blok obsługi wyjątków"

Wykonanie przeskakuje do etykiety w `try`/`catch`, `__try`/`__except`, `__try`/`__finally` bloku. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../../cpp/exception-handling-in-visual-cpp.md).

Poniższy przykład generuje C2705:

```cpp
// C2705.cpp
int main() {
goto trouble;
   __try {
      trouble: ;   // C2705
   }
   __finally {}

   // try the following line instead
   // trouble: ;
}
```
