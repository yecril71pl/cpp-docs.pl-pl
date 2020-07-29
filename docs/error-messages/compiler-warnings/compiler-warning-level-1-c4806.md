---
title: Ostrzeżenie kompilatora (poziom 1) C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: 0d3b0aa05ca5fff16b3cd28c11e3bf8290de1b3b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225348"
---
# <a name="compiler-warning-level-1-c4806"></a>Ostrzeżenie kompilatora (poziom 1) C4806

"Operation": niebezpieczna operacja: żadna wartość typu "Type", która nie została podwyższona do typu "Type", może być równa podanych stałej

Ten komunikat ostrzega o kodzie, takim jak `b == 3` , gdzie `b` ma typ **`bool`** . Reguły podwyższania poziomu mogą **`bool`** być podwyższane do **`int`** . Jest to dozwolone, ale nigdy nie może **`true`** . Poniższy przykład generuje C4806:

```cpp
// C4806.cpp
// compile with: /W1
int main()
{
   bool b = true;
   // try..
   // int b = true;

   if (b == 3)   // C4806
   {
      b = false;
   }
}
```
