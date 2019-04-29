---
title: Błąd kompilatora C2550
ms.date: 11/04/2016
f1_keywords:
- C2550
helpviewer_keywords:
- C2550
ms.assetid: 3293f53e-ee66-4035-920d-34e115c3a24c
ms.openlocfilehash: 2df6ae70be31bc519e6cfd826646073becf1ad61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353355"
---
# <a name="compiler-error-c2550"></a>Błąd kompilatora C2550

'Identyfikator': listy inicjatorów konstruktora są dozwolone tylko dla definicji konstruktora

Listy inicjatorów klasy bazowej jest używany w definicji funkcji, która nie jest konstruktorem.

Poniższy przykład spowoduje wygenerowanie C2550:

```
// C2550.cpp
// compile with: /c
class C {
public:
   C();
};

class D : public C {
public:
   D();
   void func();
};

void D::func() : C() {}  // C2550
D::D() : C() {}   // OK
```