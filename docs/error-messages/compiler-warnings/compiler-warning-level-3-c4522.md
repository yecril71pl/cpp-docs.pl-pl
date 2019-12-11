---
title: Ostrzeżenie kompilatora (poziom 3) C4522
ms.date: 11/04/2016
f1_keywords:
- C4522
helpviewer_keywords:
- C4522
ms.assetid: 7065dc27-0b6c-4e68-a345-c51cdb99a20b
ms.openlocfilehash: e791e490929daa4742a4db985f5a4f99f4db9d37
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992044"
---
# <a name="compiler-warning-level-3-c4522"></a>Ostrzeżenie kompilatora (poziom 3) C4522

"Class": określono wiele operatorów przypisania

Klasa ma wiele operatorów przypisania jednego typu. Ostrzeżenie to jest informacje; Konstruktory są wywoływane w programie.

Użyj [ostrzeżenia](../../preprocessor/warning.md) pragma, aby pominąć to ostrzeżenie.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4522.

```cpp
// C4522.cpp
// compile with: /EHsc /W3
#include <iostream>

using namespace std;
class A {
public:
   A& operator=( A & o ) { cout << "A&" << endl; return *this; }
   A& operator=( const A &co ) { cout << "const A&" << endl; return *this; }   // C4522
};

int main() {
   A o1, o2;
   o2 = o1;
   const A o3;
   o1 = o3;
}
```
