---
title: Błąd kompilatora C3824
ms.date: 11/04/2016
f1_keywords:
- C3824
helpviewer_keywords:
- C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
ms.openlocfilehash: 47363da66416c326755cad12fe4cfd448e3154e2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741732"
---
# <a name="compiler-error-c3824"></a>Błąd kompilatora C3824

"member": ten typ nie może pojawić się w tym kontekście (parametr funkcji, zwracany typ lub statyczny element członkowski)

Przypinanie wskaźników nie może być parametrami funkcji, zwracanymi typami ani zadeklarowanymi `static`.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3824:

```cpp
// C3824a.cpp
// compile with: /clr /c
void func() {
   static pin_ptr<int> a; // C3824
   pin_ptr<int> b; // OK
}
```
