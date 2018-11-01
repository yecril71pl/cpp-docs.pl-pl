---
title: Błąd kompilatora C2662
ms.date: 11/04/2016
f1_keywords:
- C2662
helpviewer_keywords:
- C2662
ms.assetid: e172c2a4-f29e-4034-8232-e7dc6f83689f
ms.openlocfilehash: fefd523ca3b9a3406afc307150322f9d431aa730
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515248"
---
# <a name="compiler-error-c2662"></a>Błąd kompilatora C2662

'Funkcja': nie można konwertować wskaźnika "this" z 'Typ1' na 'type2'

Kompilator nie może przekonwertować `this` wskaźnika z `type1` do `type2`.

Ten błąd może być spowodowany przez wywołanie innej niż`const` funkcja elementu członkowskiego na `const` obiektu.  Możliwe rozwiązania:

- Usuń `const` z deklaracja obiektu.

- Dodaj `const` do funkcji składowej.

Poniższy przykład spowoduje wygenerowanie C2662:

```
// C2662.cpp
class C {
public:
   void func1();
   void func2() const{}
} const c;

int main() {
   c.func1();   // C2662
   c.func2();   // OK
}
```

Podczas kompilowania za pomocą **/CLR**, nie można wywołać funkcję w `const` lub `volatile` kwalifikowaną typu zarządzanego. Nie można zadeklarować stała składowa klasy zarządzanej, więc nie można wywoływać metod dla stałych zarządzanych obiektów.

```
// C2662_b.cpp
// compile with: /c /clr
ref struct M {
   property M^ Type {
      M^ get() { return this; }
   }

   void operator=(const M %m) {
      M ^ prop = m.Type;   // C2662
   }
};

ref struct N {
   property N^ Type {
      N^ get() { return this; }
   }

   void operator=(N % n) {
      N ^ prop = n.Type;   // OK
   }
};
```

Poniższy przykład spowoduje wygenerowanie C2662:

```
// C2662_c.cpp
// compile with: /c
// C2662 expected
typedef int ISXVD;
typedef unsigned char BYTE;

class LXBASE {
protected:
    BYTE *m_rgb;
};

class LXISXVD:LXBASE {
public:
   // Delete the following line to resolve.
   ISXVD *PMin() { return (ISXVD *)m_rgb; }

   ISXVD *PMin2() const { return (ISXVD *)m_rgb; };   // OK
};

void F(const LXISXVD *plxisxvd, int iDim) {
   ISXVD isxvd;
   // Delete the following line to resolve.
   isxvd = plxisxvd->PMin()[iDim];

   isxvd = plxisxvd->PMin2()[iDim];
}
```