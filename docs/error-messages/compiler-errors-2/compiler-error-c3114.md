---
title: Błąd kompilatora C3114
ms.date: 11/04/2016
f1_keywords:
- C3114
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
ms.openlocfilehash: 481e0ac5a395b38bc9d1874959b010ecd71f9fb5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233382"
---
# <a name="compiler-error-c3114"></a>Błąd kompilatora C3114

"argument": nie jest prawidłowym argumentem nazwanego atrybutu

Aby element członkowski danych klasy atrybutów był prawidłowym argumentem nazwanym, nie może być oznaczony jako, **`static`** **`const`** lub **`literal`** . Jeśli właściwość, właściwość nie może być **`static`** i musi mieć metody dostępu get i Set.

Aby uzyskać więcej informacji, zobacz [Właściwości](../../extensions/property-cpp-component-extensions.md) i [atrybuty zdefiniowane przez użytkownika](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3114.

```cpp
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
