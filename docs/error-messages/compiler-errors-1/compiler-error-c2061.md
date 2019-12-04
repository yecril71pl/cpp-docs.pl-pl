---
title: Błąd kompilatora C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: dc64852523b6b56bc506260576e3c79164628340
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735934"
---
# <a name="compiler-error-c2061"></a>Błąd kompilatora C2061

Błąd składniowy: Identyfikator "Identyfikator"

Kompilator znalazł identyfikator, którego nie oczekiwano. Upewnij się, że `identifier` jest zadeklarowany przed użyciem.

Inicjator może być ujęty w nawiasy. Aby uniknąć tego problemu, umieść deklarator w nawiasach lub Przekształć go w `typedef`.

Ten błąd może być również spowodowany tym, że kompilator wykrywa wyrażenie jako argument szablonu klasy; Użyj parametru [TypeName](../../cpp/typename.md) , aby poinformować kompilator, że jest typem.

Poniższy przykład generuje C2061:

```cpp
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

C2061 może wystąpić w przypadku przekazania nazwy wystąpienia do elementu [typeid](../../extensions/typeid-cpp-component-extensions.md):

```cpp
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
