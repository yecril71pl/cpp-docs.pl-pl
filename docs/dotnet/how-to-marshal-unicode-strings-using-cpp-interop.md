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
ms.openlocfilehash: da320dbd41e7158e3bc2482b96a73c1f4728a01b
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414311"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>Porady: przeprowadzanie marshalingu ciągów Unicode za pomocą międzyoperacyjności języka C++

W tym temacie przedstawiono jeden aspekt współdziałania Visual C++. Aby uzyskać więcej informacji, zobacz [using C++ Interop (niejawne PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

W poniższych przykładach kodu użyto [zarządzanych, niezarządzanych](../preprocessor/managed-unmanaged.md) #pragma dyrektyw, aby zaimplementować funkcje zarządzane i niezarządzane w tym samym pliku, ale te funkcje współdziałają w taki sam sposób, jeśli zostały zdefiniowane w oddzielnych plikach. Pliki zawierające tylko funkcje niezarządzane nie muszą być kompilowane z [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md).

W tym temacie pokazano, jak ciągi Unicode mogą być przesyłane z zarządzanej do niezarządzanej funkcji, i na odwrót. Aby współdziałać z innymi typami ciągów, zobacz następujące tematy:

- [Instrukcje: kierowanie ciągów ANSI przy użyciu międzyoperacyjności języka C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Instrukcje: kierowanie ciągów COM za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example-pass-unicode-string-from-managed-to-unmanaged-function"></a>Przykład: przekazywanie ciągu Unicode z zarządzanej do niezarządzanej funkcji

Aby przekazać ciąg Unicode z zarządzanej do niezarządzanej funkcji, funkcja PtrToStringChars (zadeklarowana w Vcclr. h) może być używana do uzyskiwania dostępu do pamięci, w której jest przechowywany zarządzany ciąg. Ponieważ ten adres zostanie przesłany do funkcji natywnej, ważne jest, aby pamięć została przypięta przy użyciu [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) , aby zapobiec ponownemu umieszczeniu danych ciągu, w przypadku gdy niezarządzana funkcja zostanie wykonana.

```cpp
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

## <a name="example-data-marshaling-required-to-access-unicode-string"></a>Przykład: kierowanie danych wymagane do uzyskania dostępu do ciągu Unicode

Poniższy przykład demonstruje kierowanie danych wymagane do uzyskania dostępu do ciągu Unicode w zarządzanej funkcji wywołanej przez niezarządzaną funkcję. Funkcja zarządzana, przy odbiorze natywnego ciągu Unicode, konwertuje ją na ciąg zarządzany przy użyciu <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> metody.

```cpp
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

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawne PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
