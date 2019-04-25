---
title: Błąd kompilatora C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: 581aae7e1f979b3dd39caf2ce3d263fdb856c56a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221688"
---
# <a name="compiler-error-c3628"></a>Błąd kompilatora C3628

"klasa bazowa": zarządzane lub WinRTclasses obsługują tylko publiczne dziedziczenie

Próbowano użyć zarządzanej lub WinRT klasy [prywatnej](../../cpp/private-cpp.md) lub [chronione](../../cpp/protected-cpp.md) klasy bazowej. A zarządzany lub klasa WinRT należy używać tylko jako klasa bazowa z [publicznych](../../cpp/public-cpp.md) dostępu.

Poniższy przykład generuje C3628 i pokazuje, jak go naprawić:

```
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
