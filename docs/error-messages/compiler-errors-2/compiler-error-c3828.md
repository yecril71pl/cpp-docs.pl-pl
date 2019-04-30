---
title: Błąd kompilatora C3828
ms.date: 11/04/2016
f1_keywords:
- C3828
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
ms.openlocfilehash: f499bb2a8fd6d3148935daec89835b79d2ff5b49
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390597"
---
# <a name="compiler-error-c3828"></a>Błąd kompilatora C3828

"typ obiektu": argumenty umieszczania niedozwolone podczas tworzenia wystąpienia zarządzanego lub WinRTclasses

Podczas tworzenia obiektu typu zarządzanego lub typu środowiska wykonawczego Windows, nie można używać formularza położenia operatora [ref new, gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md) lub [nowe](../../cpp/new-operator-cpp.md).

Poniższy przykład generuje C3828 i pokazuje, jak go naprawić:

```
// C3828a.cpp
// compile with: /clr
ref struct M {
};

ref struct N {
   static array<char>^ bytes = gcnew array<char>(256);
};

int main() {
   M ^m1 = new (&N::bytes) M();   // C3828
   // The following line fixes the error.
   // M ^m1 = gcnew M();
}
```