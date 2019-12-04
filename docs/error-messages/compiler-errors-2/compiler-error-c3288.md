---
title: Błąd kompilatora C3288
ms.date: 11/04/2016
f1_keywords:
- C3288
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
ms.openlocfilehash: a7b87fdbd2e15906ebc0c669f0b9a74ebf97f0b3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760182"
---
# <a name="compiler-error-c3288"></a>Błąd kompilatora C3288

"Type": niedozwolone odwołanie do typu uchwytu

Kompilator wykrył niedozwolone odwołanie do typu dojścia. Możesz odwoływać się do typu uchwytu i przypisać go do odwołania. Aby uzyskać więcej informacji, zobacz [śledzenie operatora odwołania](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3288.

```cpp
// C3288.cpp
// compile with: /clr
ref class R {};
int main() {
   *(System::Object^) nullptr;   // C3288

// OK
   (System::Object^) nullptr;   // OK
   R^ r;
   R% pr = *r;
}
```
