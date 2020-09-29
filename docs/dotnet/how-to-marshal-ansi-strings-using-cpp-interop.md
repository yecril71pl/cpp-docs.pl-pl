---
title: 'Porady: kierowanie ciągów ANSI za pomocą międzyoperacyjności języka C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
ms.openlocfilehash: 3bdffa761bef74b9956842122b913e8213c736e9
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414571"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Porady: kierowanie ciągów ANSI za pomocą międzyoperacyjności języka C++

W tym temacie pokazano, jak ciągi ANSI mogą być przesyłane za pomocą międzyoperacyjności języka C++, ale .NET Framework <xref:System.String> reprezentuje ciągi w formacie Unicode, więc konwersja na ANSI jest dodatkowym krokiem. Aby współdziałać z innymi typami ciągów, zobacz następujące tematy:

- [Instrukcje: kierowanie ciągów Unicode przy użyciu międzyoperacyjności języka C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Instrukcje: kierowanie ciągów COM za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

W poniższych przykładach kodu użyto [zarządzanych, niezarządzanych](../preprocessor/managed-unmanaged.md) #pragma dyrektyw, aby zaimplementować funkcje zarządzane i niezarządzane w tym samym pliku, ale te funkcje współdziałają w taki sam sposób, jeśli zostały zdefiniowane w oddzielnych plikach. Ponieważ pliki zawierające tylko funkcje niezarządzane nie muszą być kompilowane z [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md), mogą zachować ich charakterystykę wydajności.

## <a name="example-pass-ansi-string"></a>Przykład: Przekaż ciąg ANSI

W przykładzie pokazano przekazywanie ciągu ANSI z zarządzanej do niezarządzanej funkcji przy użyciu <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> . Ta metoda przydziela pamięć na stercie niezarządzanym i zwraca adres po przeprowadzeniu konwersji. Oznacza to, że nie jest wymagane Przypinanie (ponieważ pamięć na stercie GC nie jest przesyłana do funkcji niezarządzanej) i że element IntPtr zwrócony z <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> musi być jawnie wydawany lub nie można uzyskać przecieków pamięci.

```cpp
// MarshalANSI1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const char* p) {
   printf_s("(native) received '%s'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("sample string");
   IntPtr ip = Marshal::StringToHGlobalAnsi(s);
   const char* str = static_cast<const char*>(ip.ToPointer());

   Console::WriteLine("(managed) passing string...");
   NativeTakesAString( str );

   Marshal::FreeHGlobal( ip );
}
```

## <a name="example-data-marshaling-required-to-access-ansi-string"></a>Przykład: kierowanie danych wymagane do uzyskania dostępu do ciągu ANSI

Poniższy przykład demonstruje kierowanie danych wymagane do uzyskania dostępu do ciągu ANSI w zarządzanej funkcji, która jest wywoływana przez niezarządzaną funkcję. Funkcja zarządzana, na odebranie ciągu natywnego, może użyć go bezpośrednio lub przekonwertować na ciąg zarządzany przy użyciu <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> metody, jak pokazano.

```cpp
// MarshalANSI2.cpp
// compile with: /clr
#include <iostream>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(char* s) {
   String^ ms = Marshal::PtrToStringAnsi(static_cast<IntPtr>(s));
   Console::WriteLine("(managed): received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(native) calling managed func...\n";
   ManagedStringFunc("test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawne PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
