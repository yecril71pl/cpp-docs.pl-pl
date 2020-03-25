---
title: Ostrzeżenie kompilatora (poziom 1) C4552
ms.date: 11/04/2016
f1_keywords:
- C4552
helpviewer_keywords:
- C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
ms.openlocfilehash: 8435abc60a7ba93800858b22cfd4c5e1778f8587
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186117"
---
# <a name="compiler-warning-level-1-c4552"></a>Ostrzeżenie kompilatora (poziom 1) C4552

"operator": operator nie ma żadnego wpływu; Oczekiwano operatora z efektem ubocznym

Jeśli instrukcja wyrażenia ma operator bez efektów ubocznych w górnej części wyrażenia, prawdopodobnie wystąpi błąd.

Aby zastąpić to ostrzeżenie, umieść wyrażenie w nawiasach.

Poniższy przykład generuje C4552:

```cpp
// C4552.cpp
// compile with: /W1
int main() {
   int i, j;
   i + j;   // C4552
   // try the following line instead
   // (i + j);
}
```
