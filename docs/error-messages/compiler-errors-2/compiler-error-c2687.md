---
title: Błąd kompilatora C2687
ms.date: 11/04/2016
f1_keywords:
- C2687
helpviewer_keywords:
- C2687
ms.assetid: 1d24b24a-cd0f-41cc-975c-b08dcfb7f402
ms.openlocfilehash: f3e728033a3230d628242aab341377be2f6670ca
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760260"
---
# <a name="compiler-error-c2687"></a>Błąd kompilatora C2687

"Type": Deklaracja wyjątku nie może być typu "void" lub wskazuje niekompletny typ lub wskaźnik lub odwołanie do niekompletnego typu

Dla typu, który będzie częścią deklaracji wyjątku, musi być zdefiniowana, a nie void.

Poniższy przykład generuje C2687:

```cpp
// C2687.cpp
class C;

int main() {
   try {}
   catch (C) {}   // C2687 error
}
```

Możliwe rozwiązanie:

```cpp
// C2687b.cpp
// compile with: /EHsc
class C {};

int main() {
   try {}
   catch (C) {}
}
```
