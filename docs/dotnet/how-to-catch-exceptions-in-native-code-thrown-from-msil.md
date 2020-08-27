---
title: 'Instrukcje: Przechwytywanie wyjątków w kodzie natywnym wygenerowanym w języku MSIL'
description: Przykłady sposobu przechwytywania wyjątków w kodzie natywnym wygenerowanym z MSIL.
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: b68a771d27e091f86331703b55bc2eb52dfbb41b
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898581"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>Instrukcje: Przechwytywanie wyjątków w kodzie natywnym wygenerowanym w języku MSIL

W kodzie natywnym można przechwycić natywny wyjątek C++ z MSIL.  Wyjątki CLR można przechwycić za pomocą **`__try`** i **`__except`** .

Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md) i [nowoczesne najlepsze rozwiązania C++ dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md).

## <a name="example-1"></a>Przykład 1

Poniższy przykład definiuje moduł z dwoma funkcjami, taki, który zgłasza wyjątek macierzysty, i inny, który zgłasza wyjątek MSIL.

```cpp
// catch_MSIL_in_native.cpp
// compile with: /clr /c
void Test() {
   throw ("error");
}

void Test2() {
   throw (gcnew System::Exception("error2"));
}
```

## <a name="example-2"></a>Przykład 2

Poniższy przykład definiuje moduł, który przechwytuje wyjątek natywny i MSIL.

```cpp
// catch_MSIL_in_native_2.cpp
// compile with: /clr catch_MSIL_in_native.obj
#include <iostream>
using namespace std;
void Test();
void Test2();

void Func() {
   // catch any exception from MSIL
   // should not catch Visual C++ exceptions like this
   // runtime may not destroy the object thrown
   __try {
      Test2();
   }
   __except(1) {
      cout << "caught an exception" << endl;
   }

}

int main() {
   // catch native C++ exception from MSIL
   try {
      Test();
   }
   catch(char * S) {
      cout << S << endl;
   }
   Func();
}
```

```Output
error
caught an exception
```

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../extensions/exception-handling-cpp-component-extensions.md)
