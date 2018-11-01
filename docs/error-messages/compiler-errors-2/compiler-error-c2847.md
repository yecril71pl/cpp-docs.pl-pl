---
title: Błąd kompilatora C2847
ms.date: 11/04/2016
f1_keywords:
- C2847
helpviewer_keywords:
- C2847
ms.assetid: 9ad9a0e0-8b16-49d9-a5be-f8eda2372aa9
ms.openlocfilehash: 99c49be746cea6fb80c5e24667bcd97556a0ad04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481487"
---
# <a name="compiler-error-c2847"></a>Błąd kompilatora C2847

Nie można zastosować operatora sizeof do zarządzanych lub typu WinRT "class"

[Sizeof](../../cpp/sizeof-operator.md) operator pobiera wartości obiektu w czasie kompilacji. Rozmiar zarządzanej lub klasa WinRT, interfejsu lub typu wartości jest dynamiczny, a więc nie może być znane w czasie kompilacji.

Na przykład poniższy przykład spowoduje wygenerowanie C2847:

```
// C2847.cpp
// compile with: /clr
ref class A {};

int main() {
   A ^ xA = gcnew A;
   sizeof(*xA);   // C2847 cannot use sizeof on managed object
}
```
