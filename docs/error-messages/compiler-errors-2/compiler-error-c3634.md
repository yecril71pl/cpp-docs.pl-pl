---
title: Błąd kompilatora C3634
ms.date: 11/04/2016
f1_keywords:
- C3634
helpviewer_keywords:
- C3634
ms.assetid: fd09f10c-f863-483b-9756-71c16b760b02
ms.openlocfilehash: 2acd76fee5e7ca309991e639044a45ea83ed112b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527546"
---
# <a name="compiler-error-c3634"></a>Błąd kompilatora C3634

'Funkcja': nie można definiować metody abstrakcyjnej klasy zarządzanej lub WinRTclass

Metoda abstrakcyjna może być zadeklarowana w zarządzanej lub klasa WinRT, ale nie może być zdefiniowana.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3634:

```
// C3634.cpp
// compile with: /clr
ref class C {
   virtual void f() = 0;
};

void C::f() {   // C3634 - don't define managed class' pure virtual method
}
```
