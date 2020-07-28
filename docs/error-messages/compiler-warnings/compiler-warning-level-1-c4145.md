---
title: Ostrzeżenie kompilatora (poziom 1) C4145
ms.date: 11/04/2016
f1_keywords:
- C4145
helpviewer_keywords:
- C4145
ms.assetid: 0440777a-cca2-4159-aff5-e67a254ad64a
ms.openlocfilehash: 19d2d1a018c7ee981f83aa6fa0914f1241c55538
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220109"
---
# <a name="compiler-warning-level-1-c4145"></a>Ostrzeżenie kompilatora (poziom 1) C4145

"wyrażenie1": wyrażenie relacyjne jako wyrażenie przełącznika; możliwe pomyłki z "wyrażenie2"

W **`switch`** instrukcji jest stosowane wyrażenie relacyjne jako wyrażenie kontrolne, które daje w wyniku wartość logiczną **`case`** instrukcji. Czy chodziło o *to?*

## <a name="example"></a>Przykład

Poniższy przykład generuje C4145:

```cpp
// C4145.cpp
// compile with: /W1
int main() {
   int i = 0;
   switch(i == 1) {   // C4145, use i instead of i == 1 to resolve
      case 1:
         break;
      default:
         break;
   }
}
```
