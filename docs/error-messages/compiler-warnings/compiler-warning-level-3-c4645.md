---
title: Ostrzeżenie kompilatora (poziom 3) C4645
ms.date: 11/04/2016
f1_keywords:
- C4645
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
ms.openlocfilehash: 4fa286f177284c03e5067b4af56f4e606b073653
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189373"
---
# <a name="compiler-warning-level-3-c4645"></a>Ostrzeżenie kompilatora (poziom 3) C4645

Funkcja zadeklarowana z __declspec (noreturn) zawiera instrukcję return

Instrukcja [Return](../../cpp/return-statement-in-program-termination-cpp.md) została znaleziona w funkcji, która jest oznaczona za pomocą modyfikatora `__declspec` [noreturn](../../cpp/noreturn.md) . Instrukcja `return` została zignorowana.

Poniższy przykład generuje C4645:

```cpp
// C4645.cpp
// compile with:  /W3
void __declspec(noreturn) func() {
   return;   // C4645, delete this line to resolve
}

int main() {
}
```