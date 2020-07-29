---
title: Błąd kompilatora C2203
ms.date: 11/04/2016
f1_keywords:
- C2203
helpviewer_keywords:
- C2203
ms.assetid: 5497df43-86f6-43d5-b6cb-723c4c589b10
ms.openlocfilehash: 4a078cd4c64bbb8d301aa3e4817272d23e3acbb4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216313"
---
# <a name="compiler-error-c2203"></a>Błąd kompilatora C2203

operator delete nie może określić granic dla tablicy

Za pomocą opcji **/za** (ANSI) **`delete`** operator może usunąć całą tablicę, ale nie części lub określonych elementów członkowskich tablicy.

Poniższy przykład generuje C2203:

```cpp
// C2203.cpp
// compile with: /Za
int main() {
   int *ar = new int[10];
   delete [4] ar;   // C2203
   // try the following line instead
   // delete [] ar;
}
```
