---
title: Błąd kompilatora C3375
ms.date: 11/04/2016
f1_keywords:
- C3375
helpviewer_keywords:
- C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
ms.openlocfilehash: b3dfc17f9df495fe6907b816bace0dac1eff08cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545278"
---
# <a name="compiler-error-c3375"></a>Błąd kompilatora C3375

'Funkcja': niejednoznaczna funkcja delegata

Podczas tworzenia wystąpienia delegata mogło być do statycznej funkcji członkowskiej lub jako niezwiązanego delegata do funkcji wystąpienia, kompilator wydany tego błędu.

Aby uzyskać więcej informacji, zobacz [delegate (C++ Component Extensions)](../../windows/delegate-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3375.

```
// C3375.cpp
// compile with: /clr
ref struct R {
   static void f(R^) {}
   void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::f);   // C3375
}
```