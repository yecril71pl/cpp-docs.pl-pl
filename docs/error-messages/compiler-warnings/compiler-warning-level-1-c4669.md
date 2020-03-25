---
title: Ostrzeżenie kompilatora (poziom 1) C4669
ms.date: 11/04/2016
f1_keywords:
- C4669
helpviewer_keywords:
- C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
ms.openlocfilehash: b45490ec399249a721f2d2567ca0182d44667243
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175562"
---
# <a name="compiler-warning-level-1-c4669"></a>Ostrzeżenie kompilatora (poziom 1) C4669

"CAST": niebezpieczna konwersja: "Class" jest obiektem typu zarządzanego lub WinRT

Rzutowanie zawiera środowisko wykonawcze systemu Windows lub typ zarządzany. Kompilator uzupełnia rzutowanie, wykonując niestandardową kopię jednego wskaźnika do drugiego, ale nie zapewnia innego sprawdzenia. Aby usunąć to ostrzeżenie, nie należy rzutować klas zawierających zarządzane elementy członkowskie ani typy środowisko wykonawcze systemu Windows.

Poniższy przykład generuje C4669 i pokazuje, jak to naprawić:

```cpp
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
