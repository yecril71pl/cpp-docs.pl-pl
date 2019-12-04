---
title: Błąd kompilatora C3894
ms.date: 11/04/2016
f1_keywords:
- C3894
helpviewer_keywords:
- C3894
ms.assetid: 6d5ac903-1dea-431d-8e3a-cebca4342983
ms.openlocfilehash: c08a7eca473a4ae043879b49266efec6b8afe7b1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749441"
---
# <a name="compiler-error-c3894"></a>Błąd kompilatora C3894

"var": użycie wartości l elementu członkowskiego danych initonly jest dozwolone tylko w konstruktorze klasy klasy "Class"

Statyczne składowe danych [initonly](../../dotnet/initonly-cpp-cli.md) mogą być używane tylko jako l-wartości w ich punkcie deklaracji lub w konstruktorze statycznym.

Elementy członkowskie danych initonly wystąpienia (niestatyczne) mogą być używane tylko jako l-wartości w ich punkcie deklaracji lub w konstruktorach wystąpień (niestatycznych).

Poniższy przykład generuje C3894:

```cpp
// C3894.cpp
// compile with: /clr
ref struct Y1 {
   initonly static int data_var = 0;

public:
   // class constructor
   static Y1() {
      data_var = 99;   // OK
      System::Console::WriteLine("in static constructor");
   }

   // not the class constructor
   Y1(int i) {
      data_var = i;   // C3894
   }

   static void Test() {}

};

int main() {
   Y1::data_var = 88;   // C3894
   int i = Y1::data_var;
   Y1 ^ MyY1 = gcnew Y1(99);
   Y1::Test();
}
```
