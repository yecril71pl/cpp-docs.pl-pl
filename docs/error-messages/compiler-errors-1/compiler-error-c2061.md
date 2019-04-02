---
title: Błąd kompilatora C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: 85357d94c7bc2d709e852daa60caf269949ad1b8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58771464"
---
# <a name="compiler-error-c2061"></a>Błąd kompilatora C2061

Błąd składniowy: identyfikator 'Identyfikator'

Kompilator znaleźć identyfikator, gdy nie był oczekiwany. Upewnij się, że `identifier` jest zadeklarowana, zanim go użyjesz.

Inicjator mogą być ujęte w nawiasy. Aby uniknąć tego problemu, należy umieścić specyfikator w nawiasach lub Przekształć go w `typedef`.

Również być przyczyną tego błędu, gdy kompilator wykryje wyrażenie jako argument szablonu klasy; Użyj [typename](../../cpp/typename.md) aby poinformować kompilator jest typem.

Poniższy przykład spowoduje wygenerowanie C2061:

```
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

C2061 może wystąpić w przypadku przekazania nazwy wystąpienia [typeid](../../extensions/typeid-cpp-component-extensions.md):

```
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```