---
title: Błąd kompilatora C3226
ms.date: 11/04/2016
f1_keywords:
- C3226
helpviewer_keywords:
- C3226
ms.assetid: 636106ca-6f4e-4303-a6a0-8803221ec67d
ms.openlocfilehash: 39b715b580d6fca9c15e5b9e2b63a9afb609eb16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660112"
---
# <a name="compiler-error-c3226"></a>Błąd kompilatora C3226

Deklaracja szablonu nie jest dozwolona wewnątrz deklaracji ogólnej

Użyj deklaracji ogólnej wewnątrz klasy ogólnej.

Poniższy przykład spowoduje wygenerowanie C3226:

```
// C3226.cpp
// compile with: /clr
generic <class T>
ref class C {
   template <class T1>   // C3226
   ref struct S1 {};
};
```

W poniższym przykładzie pokazano możliwe rozwiązania:

```
// C3226b.cpp
// compile with: /clr /c
generic <class T>
ref class C {
   generic <class T1>
   ref struct S1 {};
};
```