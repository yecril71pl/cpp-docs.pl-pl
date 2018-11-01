---
title: Błąd kompilatora C3217
ms.date: 11/04/2016
f1_keywords:
- C3217
helpviewer_keywords:
- C3217
ms.assetid: 99070417-c23a-4d82-bdd2-04be1a07adea
ms.openlocfilehash: bcb63c7025f0addda546379947e2e1f5c3afc545
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600362"
---
# <a name="compiler-error-c3217"></a>Błąd kompilatora C3217

"param": parametr generyczny nie może być ograniczony w tej deklaracji

Ograniczenie zostało ill sformułowany; Parametr ogólny ograniczenia należy uzgodnić z parametru szablonu klasy ogólnej.

Poniższy przykład spowoduje wygenerowanie C3217:

```
// C3217.cpp
// compile with: /clr
interface struct A {};

generic <class T>
ref class C {
   generic <class T1>
   where T : A   // C3217
   void f();
};
```

W poniższym przykładzie pokazano możliwe rozwiązania:

```
// C3217b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
ref class C {
   generic <class T1>
   where T1 : A
   void f();
};
```