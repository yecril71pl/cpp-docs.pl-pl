---
title: Ostrzeżenie kompilatora (poziom 3) C4645
ms.date: 11/04/2016
f1_keywords:
- C4645
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
ms.openlocfilehash: 607122b5592c9db4fc2ad4cabf369b4605b2673b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228768"
---
# <a name="compiler-warning-level-3-c4645"></a>Ostrzeżenie kompilatora (poziom 3) C4645

Funkcja zadeklarowana z __declspec (noreturn) zawiera instrukcję return

W funkcji, która jest oznaczona modyfikatorem [noreturn](../../cpp/noreturn.md) , znaleziono instrukcję [Return](../../cpp/return-statement-in-program-termination-cpp.md) **`__declspec`** . **`return`** Instrukcja została zignorowana.

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
