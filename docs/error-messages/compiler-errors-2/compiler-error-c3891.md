---
title: Błąd kompilatora C3891
ms.date: 11/04/2016
f1_keywords:
- C3891
helpviewer_keywords:
- C3891
ms.assetid: 6e1a9458-97f5-4580-bc0f-aa97a1bfd20d
ms.openlocfilehash: 74b8802a165ab3265cc0f1c6a0b33b31d3db401d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58779914"
---
# <a name="compiler-error-c3891"></a>Błąd kompilatora C3891

"var": literał składowej danych nie można użyć jako wartościowanie lewostronne

A [literału](../../extensions/literal-cpp-component-extensions.md) zmiennej jest stała i nie można zmienić jego wartości, po inicjalizacji w deklaracji.

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