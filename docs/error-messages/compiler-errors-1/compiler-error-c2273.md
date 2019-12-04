---
title: Błąd kompilatora C2273
ms.date: 11/04/2016
f1_keywords:
- C2273
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
ms.openlocfilehash: 9cd46f7a8a0762fcae2bdec15b9b4be6384adb25
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758687"
---
# <a name="compiler-error-c2273"></a>Błąd kompilatora C2273

"Type": niedozwolony po prawej stronie operatora "->"

Typ jest wyświetlany jako prawy operand operatora `->`.

Ten błąd może być spowodowany próbą uzyskania dostępu do konwersji typu zdefiniowanego przez użytkownika. Użyj słowa kluczowego `operator` między > i `type`.

Poniższy przykład generuje C2273:

```cpp
// C2273.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};
int main() {
   MyClass * ClassPtr = new MyClass;
   int i = ClassPtr->int();   // C2273
   int j = ClassPtr-> operator int();   // OK
}
```
