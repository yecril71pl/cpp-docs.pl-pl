---
title: Ostrzeżenie kompilatora (poziom 1) C4549
ms.date: 11/04/2016
f1_keywords:
- C4549
helpviewer_keywords:
- C4549
ms.assetid: 81a07676-625b-4f58-9b0c-3ee22830b04a
ms.openlocfilehash: 728c3040f383632f2b4990c2f1d44e500a040138
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966390"
---
# <a name="compiler-warning-level-1-c4549"></a>Ostrzeżenie kompilatora (poziom 1) C4549

operator "operator": przed przecinkiem nie ma żadnego wpływu; Czy chodziło o "operator"?

Kompilator wykrył nieprawidłowo sformułowane wyrażenie przecinka.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Poniższy przykład generuje C4549:

```cpp
// C4549.cpp
// compile with: /W1
#pragma warning (default : 4549)

int main() {
   int i = 0, k = 0;

   if ( i == 0, k )   // C4549
   // try the following line instead
   // if ( i == 0 )
      i++;
}
```