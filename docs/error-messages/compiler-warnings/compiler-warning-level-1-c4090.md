---
title: Ostrzeżenie kompilatora (poziom 1) C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: c4cb71355b4f3dca66c56ed4b89012ca9b9e646d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197049"
---
# <a name="compiler-warning-level-1-c4090"></a>Ostrzeżenie kompilatora (poziom 1) C4090

"Operation": różne kwalifikatory "modyfikator"

Zmienna użyta w operacji jest zdefiniowana z określonym modyfikatorem, który uniemożliwia jego modyfikację bez wykrywania przez kompilator. Wyrażenie jest kompilowane bez modyfikacji.

To ostrzeżenie może być spowodowane tym, że wskaźnik do **`const`** **`volatile`** elementu lub jest przypisany do wskaźnika, który nie został zadeklarowany jako wskazanie **`const`** lub **`volatile`** .

To ostrzeżenie jest wydawane dla programów C. W programie w języku C++ kompilator wystawia błąd: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).

Poniższy przykład generuje C4090:

```c
// C4090.c
// compile with: /W1
int *volatile *p;
int *const *q;
int **r;

int main() {
   p = q;   // C4090
   p = r;
   q = p;   // C4090
   q = r;
   r = p;   // C4090
   r = q;   // C4090
}
```
