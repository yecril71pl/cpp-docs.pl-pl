---
title: Błąd kompilatora C3824
ms.date: 11/04/2016
f1_keywords:
- C3824
helpviewer_keywords:
- C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
ms.openlocfilehash: d7c55ede285d027b1a65b33adbf6407df243f068
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390610"
---
# <a name="compiler-error-c3824"></a>Błąd kompilatora C3824

"członek": ten typ nie może występować w tym kontekście (parametr funkcji, zwracany typ lub składową statyczną)

Unieruchamiania wskaźników nie może być działać parametry i zwracane typy lub zadeklarowana `static`.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3824:

```
// C3824a.cpp
// compile with: /clr /c
void func() {
   static pin_ptr<int> a; // C3824
   pin_ptr<int> b; // OK
}
```
