---
title: Błąd kompilatora C3767
ms.date: 11/04/2016
f1_keywords:
- C3767
helpviewer_keywords:
- C3767
ms.assetid: 5247cdcd-639c-4527-bd37-37e74c4e8fab
ms.openlocfilehash: 994b235b4775c28126d92c241a7e42dc837d4493
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757205"
---
# <a name="compiler-error-c3767"></a>Błąd kompilatora C3767

funkcje kandydujące "Function" są niedostępne

Funkcja zaprzyjaźniona zdefiniowana w klasie nie powinna być traktowana jakby została zdefiniowana i zadeklarowana w globalnym zakresie przestrzeni nazw. Można go jednak znaleźć za pomocą wyszukiwania zależnego od argumentów.

C3767 może również być spowodowany zmianą istotną: typy natywne są teraz domyślnie prywatne w kompilacji **/CLR** ; Aby uzyskać więcej informacji, zobacz [widoczność typu](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C3767:

```cpp
// C3767a.cpp
// compile with: /clr
using namespace System;
public delegate void TestDel();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;
};

public ref class MyClass2 : public MyClass {
public:
   void Test() {
      MyClass^ patient = gcnew MyClass;
      patient->MyClass_Event();
    }
};

int main() {
   MyClass^ x = gcnew MyClass;
   x->MyClass_Event();   // C3767

   // OK
   MyClass2^ y = gcnew MyClass2();
   y->Test();
};
```

Poniższy przykład generuje C3767:

```cpp
// C3767c.cpp
// compile with: /clr /c

ref class Base  {
protected:
   void Method() {
      System::Console::WriteLine("protected");
   }
};

ref class Der : public Base {
   void Method() {
      ((Base^)this)->Method();   // C3767
      // try the following line instead
      // Base::Method();
   }
};
```

