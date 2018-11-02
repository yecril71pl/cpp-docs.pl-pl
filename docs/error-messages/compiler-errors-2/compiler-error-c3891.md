---
title: Błąd kompilatora C3891
ms.date: 11/04/2016
f1_keywords:
- C3891
helpviewer_keywords:
- C3891
ms.assetid: 6e1a9458-97f5-4580-bc0f-aa97a1bfd20d
ms.openlocfilehash: 67d12984a32998c244bcd04f99a5f2200a192974
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524569"
---
# <a name="compiler-error-c3891"></a>Błąd kompilatora C3891

"var": literał składowej danych nie można użyć jako wartościowanie lewostronne

A [literału](../../windows/literal-cpp-component-extensions.md) zmiennej jest stała i nie można zmienić jego wartości, po inicjalizacji w deklaracji.

Poniższy przykład spowoduje wygenerowanie C3891:

```
// C3891.cpp
// compile with: /clr
ref struct Y1 {
   literal int staticConst = 9;
};

int main() {
   Y1::staticConst = 0;   // C3891
}
```