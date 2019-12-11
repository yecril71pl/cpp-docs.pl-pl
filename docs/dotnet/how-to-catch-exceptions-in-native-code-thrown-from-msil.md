---
title: 'Porady: przechwytywanie wyjątków w kodzie natywnym wygenerowanym w języku MSIL'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: 23adb573a62e93933c487f611c05aed4c08494ef
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988269"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>Porady: przechwytywanie wyjątków w kodzie natywnym wygenerowanym w języku MSIL

W kodzie natywnym można wychwycić wyjątek C++ natywny z MSIL.  Wyjątki CLR można przechwycić za pomocą `__try` i `__except`.

Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków strukturalnych (CC++/)](../cpp/structured-exception-handling-c-cpp.md) i [nowoczesne C++ najlepsze rozwiązania dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md).

## <a name="example"></a>Przykład

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

## <a name="example"></a>Przykład

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

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../extensions/exception-handling-cpp-component-extensions.md)
