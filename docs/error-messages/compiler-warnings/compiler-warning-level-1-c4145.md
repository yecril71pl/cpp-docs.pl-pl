---
title: Ostrzeżenie kompilatora (poziom 1) C4145
ms.date: 11/04/2016
f1_keywords:
- C4145
helpviewer_keywords:
- C4145
ms.assetid: 0440777a-cca2-4159-aff5-e67a254ad64a
ms.openlocfilehash: 5028ae20c2413c98fa55bd81081552d22381cdbc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163679"
---
# <a name="compiler-warning-level-1-c4145"></a>Ostrzeżenie kompilatora (poziom 1) C4145

"wyrażenie1": wyrażenie relacyjne jako wyrażenie przełącznika; możliwe pomyłki z "wyrażenie2"

W instrukcji `switch` jest używany wyrażenie relacyjne jako wyrażenie kontrolne, które daje w wyniku wartość logiczną instrukcji **Case** . Czy chodziło o *to?*

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
