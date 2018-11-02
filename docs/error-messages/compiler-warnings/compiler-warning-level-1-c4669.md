---
title: Kompilator ostrzeżenie (poziom 1) C4669
ms.date: 11/04/2016
f1_keywords:
- C4669
helpviewer_keywords:
- C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
ms.openlocfilehash: f4d0b87c91649c5f2f6b5823fea82d2ce355d11a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518641"
---
# <a name="compiler-warning-level-1-c4669"></a>Kompilator ostrzeżenie (poziom 1) C4669

Instrukcja "cast": niebezpieczna konwersja: "class" to zarządzana lub obiekt typu WinRT

Rzutowanie zawiera Windows Runtime lub typ zarządzany. Kompilator wykonuje rzutowanie, wykonując kopię operacja jeden wskaźnik do innego, ale zapewnia, żadne inne sprawdzanie. Aby rozwiązać tego ostrzeżenia, nie Rzutuj klasy zawierające zarządzanych członków lub typów środowiska wykonawczego Windows.

Poniższy przykład generuje C4669 i pokazuje, jak go naprawić:

```
// C4669.cpp
// compile with: /clr /W1
ref struct A {
   int i;
   Object ^ pObj;   // remove the managed member to fix the warning
};

ref struct B {
   int j;
};

int main() {
   A ^ a = gcnew A;
   B ^ b = reinterpret_cast<B ^>(a);   // C4669
}
```