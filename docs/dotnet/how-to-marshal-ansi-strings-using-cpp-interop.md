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
ms.openlocfilehash: 6987b23311354cfe6fd095e0e811d043e9b9692e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988467"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Porady: kierowanie ciągów ANSI za pomocą międzyoperacyjności języka C++

W tym temacie pokazano, jak ciągi ANSI mogą być C++ przesyłane za pomocą międzyoperacyjności, ale <xref:System.String> .NET Framework reprezentuje ciągi w formacie Unicode, dlatego konwersja na ANSI jest dodatkowym krokiem. Aby współdziałać z innymi typami ciągów, zobacz następujące tematy:

- [Instrukcje: przeprowadzanie marshalingu ciągów Unicode za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Instrukcje: przeprowadzanie marshalingu ciągów COM za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

W poniższych przykładach kodu użyto [zarządzanych, niezarządzanych](../preprocessor/managed-unmanaged.md) #pragma dyrektyw, aby zaimplementować funkcje zarządzane i niezarządzane w tym samym pliku, ale te funkcje współdziałają w taki sam sposób, jeśli zostały zdefiniowane w oddzielnych plikach. Ponieważ pliki zawierające tylko funkcje niezarządzane nie muszą być kompilowane z [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md), mogą zachować ich charakterystykę wydajności.

## <a name="example"></a>Przykład

W przykładzie pokazano przekazywanie ciągu ANSI z zarządzanej do niezarządzanej funkcji przy użyciu <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>. Ta metoda przydziela pamięć na stercie niezarządzanym i zwraca adres po przeprowadzeniu konwersji. Oznacza to, że nie jest wymagane Przypinanie (ponieważ pamięć na stercie GC nie jest przesyłana do funkcji niezarządzanej) i że element IntPtr zwrócony z <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> musi być jawnie wydawany lub mieć wyniki przecieków pamięci.

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

## <a name="example"></a>Przykład

Poniższy przykład demonstruje kierowanie danych wymagane do uzyskania dostępu do ciągu ANSI w zarządzanej funkcji, która jest wywoływana przez niezarządzaną funkcję. Funkcja zarządzana, na odebranie ciągu natywnego, może użyć go bezpośrednio lub przekonwertować na ciąg zarządzany przy użyciu metody <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A>, jak pokazano.

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

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
