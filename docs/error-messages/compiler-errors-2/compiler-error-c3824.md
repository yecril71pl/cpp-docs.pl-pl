---
title: Błąd kompilatora C3824 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3824
dev_langs:
- C++
helpviewer_keywords:
- C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03d42f80716b81f4409449262af650220b1ad92b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083954"
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
