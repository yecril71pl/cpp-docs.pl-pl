---
title: Błąd kompilatora C3893
ms.date: 11/04/2016
f1_keywords:
- C3893
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
ms.openlocfilehash: 20c17eaa6555b5511ecbc930eacdb2ec92475b23
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749506"
---
# <a name="compiler-error-c3893"></a>Błąd kompilatora C3893

"var": wykorzystanie wartości l składowej danych initonly jest dozwolone tylko w konstruktorze wystąpienia klasy "type_name"

Statyczne składowe danych [initonly](../../dotnet/initonly-cpp-cli.md) mogą mieć tylko adresy wykonywane w konstruktorze statycznym.

Elementy członkowskie danych initonly wystąpienia (niestatyczne) mogą mieć tylko ich adresy w konstruktorach wystąpień (niestatycznych).

Poniższy przykład generuje C3893:

```cpp
// C3893.cpp
// compile with: /clr
ref struct Y1 {
   Y1() : data_var(0) {
      int% i = data_var;   // OK
   }
   initonly int data_var;
};

int main(){
   Y1^ y= gcnew Y1;
   int% i = y->data_var;   // C3893
}
```
