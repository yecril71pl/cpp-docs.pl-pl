---
title: Błąd kompilatora C3611
ms.date: 11/04/2016
f1_keywords:
- C3611
helpviewer_keywords:
- C3611
ms.assetid: 42f3e320-41de-420a-bd05-8924cab765aa
ms.openlocfilehash: 08e9b969c9eb03dd0259813487bfeb04bfaa5ca9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590248"
---
# <a name="compiler-error-c3611"></a>Błąd kompilatora C3611

'Funkcja': funkcja zapieczętowana nie może mieć czystego specyfikatora

Funkcja zapieczętowana zadeklarowano niepoprawnie.  Aby uzyskać więcej informacji, zobacz [zapieczętowanego](../../windows/sealed-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3611.

```
// C3611.cpp
// compile with: /clr /c

ref struct V {
   virtual void Test() sealed = 0;   // C3611
   virtual void Test2() sealed;   // OK
   virtual void Test3() = 0;   // OK
};
```