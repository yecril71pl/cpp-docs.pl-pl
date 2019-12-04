---
title: Błąd kompilatora C2582
ms.date: 11/04/2016
f1_keywords:
- C2582
helpviewer_keywords:
- C2582
ms.assetid: ee1b9378-8bcd-4792-b87e-6d7a466d29ed
ms.openlocfilehash: 102682e64602d06b2ee5449ac5b71852cfa33af3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748674"
---
# <a name="compiler-error-c2582"></a>Błąd kompilatora C2582

Funkcja "Function" jest niedostępna w elemencie "Type"

Podjęto próbę przypisania do obiektu, który nie ma operatora przypisania.

Poniższy przykład generuje C2582:

```cpp
// C2582.cpp
// compile with: /clr
using namespace System;

struct N {};
ref struct O {};
ref struct R {
   property O prop;   // C2582
   property O ^ prop2;   // OK
};

int main() {
   String ^ st1 = gcnew String("");
   ^st1 = gcnew String("");   // C2582
   st1 = "xxx";   // OK
}
```
