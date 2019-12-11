---
title: Ostrzeżenie kompilatora (poziom 3) C4645
ms.date: 11/04/2016
f1_keywords:
- C4645
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
ms.openlocfilehash: d9aff4b554f4b162f87de9e1d373d59dea019637
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991741"
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
