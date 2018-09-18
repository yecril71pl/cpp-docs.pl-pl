---
title: Błąd kompilatora C3628 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3628
dev_langs:
- C++
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a65dc33c5381b063c3adb01072e930075108649
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037375"
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
