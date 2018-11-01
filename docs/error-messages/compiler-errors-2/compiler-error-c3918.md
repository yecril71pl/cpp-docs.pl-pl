---
title: Błąd kompilatora C3918
ms.date: 11/04/2016
f1_keywords:
- C3918
helpviewer_keywords:
- C3918
ms.assetid: a8b3a90a-3fe1-4244-a5ff-a31cdae97d98
ms.openlocfilehash: 2c2d2f2598d06ca228a96f2786fcb02888e29a1b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530900"
---
# <a name="compiler-error-c3918"></a>Błąd kompilatora C3918

użycie wymaga członka, jako element członkowski danych

C3918 może wystąpić z kilku powodów związanych ze zdarzeniami.

## <a name="example"></a>Przykład

C3918 może wystąpić, ponieważ element członkowski klasy jest wymagana w bieżącym kontekście. Poniższy przykład spowoduje wygenerowanie C3918.

```
// C3918.cpp
// compile with: /clr /c
public ref class C {
public:
   System::Object ^ o;
   delegate void Del();

   event Del^ MyEvent {
      void add(Del^ev) {
         if ( MyEvent != nullptr) {}   // C3918
         if ( o != nullptr) {}   // OK
   }
   void remove(Del^){}
   }
};
```

## <a name="example"></a>Przykład

C3918 przyczyną jest również, jeśli zostanie podjęta próba Sprawdź trivial zdarzeń w przypadku wartości null (Nazwa zdarzenia nie będzie już zapewniać bezpośredni dostęp do magazynu pomocniczego delegata zdarzenia).

Poniższy przykład spowoduje wygenerowanie C3918.

```
// C3918_2.cpp
// compile with: /clr /c
using namespace System;
public delegate int MyDel(int);

interface struct IEFace {
   event MyDel ^ E;
};

ref struct EventSource : public IEFace {
   virtual event MyDel ^ E;
   void Fire_E(int i) {
      if (E)   // C3918
         E(i);
   }
};
```

## <a name="example"></a>Przykład

C3918 może również wystąpić, jeśli niepoprawnie subskrybować zdarzenie. Poniższy przykład spowoduje wygenerowanie C3918.

```
// C3918_3.cpp
// compile with: /clr /c
using namespace System;

public delegate void del();

public ref class A {
public:
   event del^ e {
      void add(del ^handler ) {
         d += handler;
      }

      void remove(del ^handler) {
         d -= handler;
      }

      void raise() {
         d();
      }
   }

   del^ d;
   void f() {}

   A() {
      e = gcnew del(this, &A::f);   // C3918
      // try the following line instead
      // e += gcnew del(this, &A::f);
      e();
   }
};

int main() {
   A a;
}
```