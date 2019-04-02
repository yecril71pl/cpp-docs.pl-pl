---
title: Kompilator ostrzeżenie (poziom 1) C4803
ms.date: 11/04/2016
f1_keywords:
- C4803
helpviewer_keywords:
- C4803
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
ms.openlocfilehash: bb8f5fe9d55a44193325a2fcfe9ef7675a2b3b89
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58774883"
---
# <a name="compiler-warning-level-1-c4803"></a>Kompilator ostrzeżenie (poziom 1) C4803

"method": podniesiona metoda ma klasę magazynu inną od zdarzenia, "event"

Metody zdarzeń musi mieć tą samą klasę magazynu jako deklaracja zdarzenia. Kompilator dostosowuje metody zdarzeń, tak aby klasy magazynu są takie same.

To ostrzeżenie może wystąpić, jeśli masz klasę, która implementuje zdarzenia z interfejsu. Kompilator nie generuje niejawnie metodę Zgłoś zdarzenie w interfejsie. Podczas implementowania interfejsu w klasie, kompilator niejawnie wygenerować metody wzrostu i tej metody nie będzie wirtualnego, dlatego to ostrzeżenie. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [zdarzeń](../../extensions/event-cpp-component-extensions.md).

Zobacz [ostrzeżenie](../../preprocessor/warning.md) pragma informacji na temat wyłączyć ostrzeżenia.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4803.

```
// C4803.cpp
// compile with: /clr /W1
using namespace System;

public delegate void Del();

ref struct E {
   Del ^ _pd1;
   event Del ^ E1 {
      void add (Del ^ pd1) {
         _pd1 = dynamic_cast<Del ^>(Delegate::Combine(_pd1, pd1));
      }

      void remove(Del^ pd1) {
         _pd1 = dynamic_cast<Del^> (Delegate::Remove(_pd1, pd1));
      }

      virtual void raise() {   // C4803 warning (remove virtual)
         if (_pd1)
            _pd1();
      }
   }

   void func() {
      Console::WriteLine("In E::func()");
   }
};

int main() {
   E ^ ep = gcnew E;
   ep->E1 += gcnew Del(ep, &E::func);
   ep->E1();
   ep->E1 -= gcnew Del(ep, &E::func);
   ep->E1();
}
```
