---
title: Ostrzeżenie kompilatora (poziom 1) C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: dae6ed7d7a38daf0ce525ae62409823212db711b
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052361"
---
# <a name="compiler-warning-level-1-c4806"></a>Ostrzeżenie kompilatora (poziom 1) C4806

"Operation": niebezpieczna operacja: żadna wartość typu "Type", która nie została podwyższona do typu "Type", może być równa podanych stałej

Ten komunikat ostrzega o kodzie, takim jak `b == 3`, gdzie `b` ma `bool`typu. Reguły promocji powodują awansowanie `bool` `int`. Jest to dozwolone, ale nigdy nie może być **prawdziwe**. Poniższy przykład generuje C4806:

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