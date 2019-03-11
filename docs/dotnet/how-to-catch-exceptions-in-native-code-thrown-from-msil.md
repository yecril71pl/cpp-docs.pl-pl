---
title: 'Instrukcje: Przechwytywanie wyjątków w kodzie natywnym wygenerowanym w języku MSIL'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: acb3ba1ab6d10decba10b899861007abfff03359
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748726"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>Instrukcje: Przechwytywanie wyjątków w kodzie natywnym wygenerowanym w języku MSIL

W kodzie natywnym może przechwycić natywnego wyjątek C++ z MSIL.  Może przechwycić wyjątków CLR za pomocą `__try` i `__except`.

Aby uzyskać więcej informacji, zobacz [obsługi wyjątków strukturalnych, (C/C++)](../cpp/structured-exception-handling-c-cpp.md) i [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md).

## <a name="example"></a>Przykład

Poniższy przykład definiuje moduł o dwie funkcje, który zgłasza wyjątek natywnych i innym zgłaszający wyjątek MSIL.

```
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

Poniższy przykład definiuje moduł, który przechwytuje natywne i wyjątków MSIL.

```
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

[Obsługa wyjątków](../windows/exception-handling-cpp-component-extensions.md)
