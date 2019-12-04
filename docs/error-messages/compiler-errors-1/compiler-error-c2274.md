---
title: Błąd kompilatora C2274
ms.date: 11/04/2016
f1_keywords:
- C2274
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
ms.openlocfilehash: fd807dedb6c300860611d07212b8fc8952a90a65
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758674"
---
# <a name="compiler-error-c2274"></a>Błąd kompilatora C2274

"Type": niedozwolony po prawej stronie operatora "."

Typ jest wyświetlany jako prawy operand operatora dostępu do elementu członkowskiego (.).

Ten błąd może być spowodowany próbą uzyskania dostępu do konwersji typu zdefiniowanego przez użytkownika. Użyj słowa kluczowego `operator` między kropką i `type`.

Poniższy przykład generuje C2286:

```cpp
// C2274.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};

int main() {
   MyClass ClassName;
   int i = ClassName.int();   // C2274
   int j = ClassName.operator int();   // OK
}
```
