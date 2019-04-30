---
title: Błąd kompilatora C3114
ms.date: 11/04/2016
f1_keywords:
- C3114
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
ms.openlocfilehash: c5a4feae5c8805a27c020b532fd58e0562e46b6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404120"
---
# <a name="compiler-error-c3114"></a>Błąd kompilatora C3114

"argument": nie jest prawidłowym argumentem nazwanego atrybutu

Aby dla atrybutu klasy element członkowski danych był prawidłowy, nazwany argument, go nie może być oznaczona `static`, `const`, lub `literal`. Właściwości, właściwość nie może być `static` i musi mieć get i ustaw metody dostępu.

Aby uzyskać więcej informacji, zobacz [właściwość](../../extensions/property-cpp-component-extensions.md) i [atrybuty zdefiniowane przez użytkownika](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3114.

```
// C3114.cpp
// compile with: /clr /c
public ref class A : System::Attribute {
public:
   static property int StaticProp {
      int get();
   }

   property int Prop2 {
      int get();
      void set(int i);
   }
};

[A(StaticProp=123)]   // C3114
public ref class R {};

[A(Prop2=123)]   // OK
public ref class S {};
```