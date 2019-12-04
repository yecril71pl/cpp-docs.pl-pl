---
title: Błąd kompilatora C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: 9976cb2425f8f855ffb2903c07de22822c781e20
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755827"
---
# <a name="compiler-error-c3628"></a>Błąd kompilatora C3628

"Klasa bazowa": zarządzana lub WinRTclasses obsługuje tylko publiczne dziedziczenie

Podjęto próbę użycia klasy zarządzanej lub WinRT jako [prywatnej](../../cpp/private-cpp.md) lub [chronionej](../../cpp/protected-cpp.md) klasy podstawowej. Klasa Managed lub WinRT może być używana tylko jako klasa bazowa z dostępem [publicznym](../../cpp/public-cpp.md) .

Poniższy przykład generuje C3628 i pokazuje, jak to naprawić:

```cpp
// C3628a.cpp
// compile with: /clr
ref class B {
};

ref class D : private B {   // C3628

// The following line resolves the error.
// ref class D : public B {
};

int main() {
}
```
