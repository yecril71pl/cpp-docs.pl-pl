---
title: Błąd kompilatora C3923
ms.date: 11/04/2016
f1_keywords:
- C3923
helpviewer_keywords:
- C3923
ms.assetid: db8838e9-6344-4cd6-83e0-a8abeb12c4c0
ms.openlocfilehash: 82bdfef997248dea11784c00fc04d1ac3b4189d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386567"
---
# <a name="compiler-error-c3923"></a>Błąd kompilatora C3923

'składowa': lokalnej klasy, struktury lub Unii definicje są niedozwolone w funkcji składowej klasy zarządzanej lub WinRT

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3923.

```
// C3923.cpp
// compile with: /clr /c
ref struct x {
   void Test() {
      struct a {};   // C3923
      class b {};   // C3923
      union c {};   // C3923
   }
};
```