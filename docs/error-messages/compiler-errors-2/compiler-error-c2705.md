---
title: Błąd kompilatora C2705
ms.date: 11/04/2016
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 65d9ed2458f43e6c9a697be02ffc9b831259624c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225439"
---
# <a name="compiler-error-c2705"></a>Błąd kompilatora C2705

"label": niedozwolony skok do zakresu "blok obsługi wyjątków"

Wykonanie przeskakuje do etykiety w **`try`** / **`catch`** bloku, `__try` / **`__except`** , `__try` / **`__finally`** . Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../../cpp/exception-handling-in-visual-cpp.md).

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
