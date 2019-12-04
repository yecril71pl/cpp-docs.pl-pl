---
title: Błąd kompilatora C2234
ms.date: 11/04/2016
f1_keywords:
- C2234
helpviewer_keywords:
- C2234
ms.assetid: cfa42458-c803-4717-a017-9eca1c0cbfb0
ms.openlocfilehash: 9f13b33c9e6c56e4ec82e6542ff0869849f0f822
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759246"
---
# <a name="compiler-error-c2234"></a>Błąd kompilatora C2234

"name": tablice odwołań są niedozwolone

Ponieważ wskaźniki do odwołań są niedozwolone, tablice odwołań nie są możliwe.

Poniższy przykład generuje C2234:

```cpp
// C2234.cpp
int main() {
   int i = 0, j = 0, k = 0, l = 0;
   int &array[4] = {i,j,k,l};   // C2234
   int array2[4] = {i,j,k,l};   // OK
}
```
