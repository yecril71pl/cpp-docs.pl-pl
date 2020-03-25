---
title: Błąd kompilatora C3556
ms.date: 11/04/2016
f1_keywords:
- C3556
helpviewer_keywords:
- C3556
ms.assetid: 9b002dcc-494e-414f-9587-20c2a0a39333
ms.openlocfilehash: bc5eae58ac453182fd25853edd45e2c45093f5e5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200580"
---
# <a name="compiler-error-c3556"></a>Błąd kompilatora C3556

> "*Expression*": nieprawidłowy argument dla "decltype"

Kompilator nie może wywnioskować typu wyrażenia będącego argumentem *wyrażenia* `decltype(`specyfikatorem typu`)`.

## <a name="example"></a>Przykład

W poniższym przykładzie kodu kompilator nie może wywnioskować typu argumentu `myFunction`, ponieważ `myFunction` jest przeciążona. Aby rozwiązać ten problem, można użyć `static_cast`, aby utworzyć wystąpienie wskaźnika do określonej przeciążonej funkcji, aby określić w wyrażeniu `decltype`.

```cpp
// C3556.cpp
// compile with: cl /W4 /EHsc C3556.cpp
#include <iostream>

void myFunction(int);
void myFunction(float, float);

void callsMyFunction(decltype(myFunction) fn); // C3556
// One way to fix is to comment out the line above, and
// use static_cast to create specialized function pointer
// instances:
auto myFunctionInt = static_cast<void(*)(int)>(myFunction);
auto myFunctionFloatFloat = static_cast<void(*)(float,float)>(myFunction);
void callsMyFunction(decltype(myFunctionInt) fn, int n);
void callsMyFunction(decltype(myFunctionFloatFloat) fn, float f, float g);

void myFunction(int i) {
    std::cout << "called myFunction(" << i << ")" << std::endl;
}

void myFunction(float f, float g) {
    std::cout << "called myFunction(" << f << ", " << g << ")" << std::endl;
}

void callsMyFunction(decltype(myFunctionInt) fn, int n) {
    fn(n);
}

void callsMyFunction(decltype(myFunctionFloatFloat) fn, float f, float g) {
    fn(f, g);
}

int main() {
    callsMyFunction(myFunction, 42);
    callsMyFunction(myFunction, 0.1f, 2.3f);
}
```
