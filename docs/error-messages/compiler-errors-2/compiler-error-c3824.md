---
title: Błąd kompilatora C3824
ms.date: 11/04/2016
f1_keywords:
- C3824
helpviewer_keywords:
- C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
ms.openlocfilehash: 78081de44a834b16d34d1f88a5dc996efb1f784c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220148"
---
# <a name="compiler-error-c3824"></a>Błąd kompilatora C3824

"member": ten typ nie może pojawić się w tym kontekście (parametr funkcji, zwracany typ lub statyczny element członkowski)

Przypinanie wskaźników nie może być parametrów funkcji, zwracanych typów lub zadeklarowanych **`static`** .

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
