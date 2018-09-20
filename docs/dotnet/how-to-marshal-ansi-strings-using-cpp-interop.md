---
title: 'Porady: przeprowadzanie Marshalingu ciągów ANSI za pomocą międzyoperacyjności języka C++ | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4a1a0cd8b9da5812e404f70dc999dfaf1606666
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383366"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Porady: przeprowadzanie marshalingu ciągów ANSI za pomocą międzyoperacyjności języka C++

W tym temacie pokazano, jak można ciągów ANSI przekazywane za pomocą międzyoperacyjności języka C++, ale programu .NET Framework <xref:System.String> reprezentuje ciągi w formacie Unicode, więc konwersji do ANSI jest dodatkowego kroku. Do współpracy z innymi typami parametrów, zobacz następujące tematy:

- [Instrukcje: przeprowadzanie marshalingu ciągów Unicode za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Instrukcje: przeprowadzanie marshalingu ciągów COM za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

Poniższy kod przykłady użycia [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) #pragma — dyrektywy do zaimplementowania zarządzanych i niezarządzanych funkcji w tym samym pliku, ale te funkcje współpracować w taki sam sposób, jeśli zdefiniowany w oddzielnych plikach. Ponieważ pliki zawierające tylko funkcji niezarządzanych nie muszą być kompilowane z [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md), zachowują ich charakterystyk wydajności.

## <a name="example"></a>Przykład

W przykładzie pokazano, przekazując ciąg ANSI z zarządzanej do niezarządzanej funkcji przy użyciu <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>. Ta metoda przydziela pamięć na stosie niezarządzanym i zwraca adres po przeprowadzeniu konwersji. Oznacza to, że brak możliwości przypinania jest konieczne (pamięci na stercie GC nie został przekazany do funkcji niezarządzanych) i czy IntPtr zwrócone z <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> musi jawnie zwolnione lub pamięci, przecieków wyników.

```
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

W poniższym przykładzie pokazano, organizowanie danych wymagane do uzyskania dostępu na ciąg ANSI w funkcji zarządzanej, która jest wywoływana przez niezarządzanej funkcji. Funkcji zarządzanej, po odebraniu natywnych ciągu, można bezpośrednio korzystać lub przekonwertować na ciąg zarządzane za pośrednictwem <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> metodzie, jak pokazano.

```
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

## <a name="see-also"></a>Zobacz też

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)