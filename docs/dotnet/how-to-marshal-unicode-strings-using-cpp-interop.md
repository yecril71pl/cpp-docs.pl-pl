---
title: 'Porady: przeprowadzanie marshalingu ciągów Unicode za pomocą międzyoperacyjności języka C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
ms.openlocfilehash: f08ea9d6eb879aa3b07ac0ff983637236368a11a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507786"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>Porady: przeprowadzanie marshalingu ciągów Unicode za pomocą międzyoperacyjności języka C++

W tym temacie przedstawiono jeden zestaw reguł współdziałania Visual C++. Aby uzyskać więcej informacji, zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Poniższy kod przykłady użycia [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) #pragma — dyrektywy do zaimplementowania zarządzanych i niezarządzanych funkcji w tym samym pliku, ale te funkcje współpracować w taki sam sposób, jeśli zdefiniowany w oddzielnych plikach. Pliki zawierające tylko funkcji niezarządzanych nie muszą być skompilowana przy użyciu [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md).

W tym temacie pokazano, jak ciągi Unicode mogą być przekazywane z zarządzanej do niezarządzanej funkcji i na odwrót. Do współpracy z innymi typami parametrów, zobacz następujące tematy:

- [Instrukcje: przeprowadzanie marshalingu ciągów ANSI za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Instrukcje: przeprowadzanie marshalingu ciągów COM za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example"></a>Przykład

Aby przekazać ciąg Unicode z zarządzanej do niezarządzanej funkcji, ptrtostringchars — funkcja (deklaracja w Vcclr.h) może służyć do dostępu w pamięci, gdzie zarządzanych ciąg jest przechowywany. Ponieważ ten adres zostanie przekazany do funkcji natywnej, jest ważne, przypinać pamięci za pomocą [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) aby zapobiec przeniesieniu danych ciągu, cykl zbierania śmieci odbędą się podczas wykonuje niezarządzanej funkcji.

```
// MarshalUnicode1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const wchar_t* p) {
   printf_s("(native) received '%S'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("test string");
   pin_ptr<const wchar_t> str = PtrToStringChars(s);

   Console::WriteLine("(managed) passing string to native func...");
   NativeTakesAString( str );
}
```

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, organizowanie danych wymagane do uzyskania dostępu ciąg Unicode w funkcji zarządzanej wywoływane przez niezarządzanej funkcji. Funkcji zarządzanej, po odebraniu natywnych ciąg Unicode konwertuje ją na ciąg zarządzanych za pomocą <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> metody.

```
// MarshalUnicode2.cpp
// compile with: /clr
#include <iostream>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(wchar_t* s) {
   String^ ms = Marshal::PtrToStringUni((IntPtr)s);
   Console::WriteLine("(managed) received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(unmanaged) calling managed func...\n";
   ManagedStringFunc(L"test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>Zobacz też

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)