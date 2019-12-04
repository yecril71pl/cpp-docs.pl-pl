---
title: Błąd kompilatora C3154
ms.date: 11/04/2016
f1_keywords:
- C3154
helpviewer_keywords:
- C3154
ms.assetid: 78005c74-eaaf-4ac2-88ae-6c25d01a302a
ms.openlocfilehash: e40b0c2a56c36b92465fb3bb3451a48c88b5822e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745931"
---
# <a name="compiler-error-c3154"></a>Błąd kompilatora C3154

Oczekiwano znaku "," przed wielokropkiem. Wielokropek rozdzielonych przecinkami nie jest obsługiwany w funkcjach tablicy parametrów.

Funkcja argumentu zmiennej nie została prawidłowo zadeklarowana.

Aby uzyskać więcej informacji, zobacz [listę zmiennych argumentów (...)C++(/CLI)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3154.

```cpp
// C3154.cpp
// compile with: /clr
ref struct R {
   void Func(int ... array<int> ^);   // C3154
   void Func2(int i, ... array<int> ^){}   // OK
   void Func3(array<int> ^){}   // OK
   void Func4(... array<int> ^){}   // OK
};

int main() {
   R ^ r = gcnew R;
   r->Func4(1,2,3);
}
```
