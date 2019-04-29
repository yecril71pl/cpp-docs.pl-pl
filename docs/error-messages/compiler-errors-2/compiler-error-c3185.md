---
title: Błąd kompilatora C3185
ms.date: 11/04/2016
f1_keywords:
- C3185
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
ms.openlocfilehash: 45afe70b454f72dd8c9b8ce9771ce1f5aef6a10e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366085"
---
# <a name="compiler-error-c3185"></a>Błąd kompilatora C3185

"typeid" używane z zarządzanych lub typu WinRT "type", zamiast tego użyj "operator"

Nie można zastosować [typeid](../../cpp/typeid-operator.md) operator ma być zarządzany lub WinRT typu; użyj [typeid](../../extensions/typeid-cpp-component-extensions.md) zamiast tego.

Poniższy przykład generuje C3185 i pokazuje, jak go naprawić:

```
// C3185a.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};

int main() {
   Derived ^ pd = gcnew Derived;
   Base ^pb = pd;
   const type_info & t1 = typeid(pb);   // C3185
   System::Type ^ MyType = Base::typeid;   // OK
};
```
