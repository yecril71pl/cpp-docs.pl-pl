---
title: Błąd kompilatora C2048
ms.date: 11/04/2016
f1_keywords:
- C2048
helpviewer_keywords:
- C2048
ms.assetid: 44704726-85fc-42f0-afb9-194df8c4ca7c
ms.openlocfilehash: 483e4d706a1c08899e6cd6e1ec561a21ed805014
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87210439"
---
# <a name="compiler-error-c2048"></a>Błąd kompilatora C2048

więcej niż jeden domyślny

**`switch`** Instrukcja zawiera wiele **`default`** etykiet. Usuń jedną z **`default`** etykiet, aby rozwiązać ten problem.

Poniższy przykład generuje C2048:

```cpp
// C2048.cpp
int main() {
   int a = 1;
   switch (a) {
      case 1:
         a = 0;
      default:
         a = 2;
      default:   // C2048
         a = 3;
   }
}
```

Możliwe rozwiązanie:

```cpp
// C2048b.cpp
int main() {
   int a = 1;
   switch (a) {
      case 1:
         a = 0;
      default:
         a = 2;
   }
}
```
