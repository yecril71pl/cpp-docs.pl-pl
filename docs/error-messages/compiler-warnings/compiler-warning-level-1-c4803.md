---
title: Kompilator ostrzeżenie (poziom 1) C4803
ms.date: 11/04/2016
f1_keywords:
- C4803
helpviewer_keywords:
- C4803
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
ms.openlocfilehash: 3915307ac2bcc6a923c93382cfefa618ce01fe52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563218"
---
# <a name="compiler-warning-level-1-c4803"></a>Kompilator ostrzeżenie (poziom 1) C4803

"method": podniesiona metoda ma klasę magazynu inną od zdarzenia, "event"

Metody zdarzeń musi mieć tą samą klasę magazynu jako deklaracja zdarzenia. Kompilator dostosowuje metody zdarzeń, tak aby klasy magazynu są takie same.

To ostrzeżenie może wystąpić, jeśli masz klasę, która implementuje zdarzenia z interfejsu. Kompilator nie generuje niejawnie metodę Zgłoś zdarzenie w interfejsie. Podczas implementowania interfejsu w klasie, kompilator niejawnie wygenerować metody wzrostu i tej metody nie będzie wirtualnego, dlatego to ostrzeżenie. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [zdarzeń](../../windows/event-cpp-component-extensions.md).

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
