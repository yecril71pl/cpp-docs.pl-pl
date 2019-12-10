---
title: 'Porady: kierowanie ciągów COM za pomocą międzyoperacyjności języka C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
ms.openlocfilehash: 8dfdad892261d5ae2d3494734458e1447f8ebd7c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988465"
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>Porady: kierowanie ciągów COM za pomocą międzyoperacyjności języka C++

W tym temacie pokazano, jak BSTR (podstawowy format ciągu preferowany w programowaniu COM) można przesłać z zarządzanej do niezarządzanej funkcji i na odwrót. Aby współdziałać z innymi typami ciągów, zobacz następujące tematy:

- [Instrukcje: przeprowadzanie marshalingu ciągów Unicode za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Instrukcje: przeprowadzanie marshalingu ciągów ANSI za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

W poniższych przykładach kodu użyto [zarządzanych, niezarządzanych](../preprocessor/managed-unmanaged.md) #pragma dyrektyw, aby zaimplementować funkcje zarządzane i niezarządzane w tym samym pliku, ale te funkcje współdziałają w taki sam sposób, jeśli zostały zdefiniowane w oddzielnych plikach. Pliki zawierające tylko funkcje niezarządzane nie muszą być kompilowane z [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak BSTR (format ciągu używany w programowaniu COM) można przekazywać z zarządzanej do niezarządzanej funkcji. Wywołanie funkcji zarządzanej używa <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>, aby uzyskać adres BSTRej reprezentacji zawartości elementu .NET system. String. Ten wskaźnik jest przypięty przy użyciu [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) , aby upewnić się, że jego adres fizyczny nie został zmieniony podczas cyklu wyrzucania elementów bezużytecznych podczas wykonywania funkcji niezarządzanej. Moduł wyrzucania elementów bezużytecznych nie jest w trakcie przesuwania pamięci, dopóki [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) nie znajdzie się poza zakresem.

```cpp
// MarshalBSTR1.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(BSTR bstr) {
   printf_s("%S", bstr);
}

#pragma managed

int main() {
   String^ s = "test string";

   IntPtr ip = Marshal::StringToBSTR(s);
   BSTR bs = static_cast<BSTR>(ip.ToPointer());
   pin_ptr<BSTR> b = &bs;

   NativeTakesAString( bs );
   Marshal::FreeBSTR(ip);
}
```

## <a name="example"></a>Przykład

Poniższy przykład demonstruje, jak można przesłać element BSTR z niezarządzanej do niezarządzanej funkcji. Funkcja zarządzane zarządzanie może użyć ciągu jako BSTR lub użyć <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A>, aby przekonwertować go na <xref:System.String> do użycia z innymi funkcjami zarządzanymi. Ponieważ pamięć reprezentująca element BSTR jest przypisana na stercie niezarządzanym, nie jest wymagane przypinanie, ponieważ nie ma wyrzucania elementów bezużytecznych na stercie niezarządzanym.

```cpp
// MarshalBSTR2.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedTakesAString(BSTR bstr) {
   String^ s = Marshal::PtrToStringBSTR(static_cast<IntPtr>(bstr));
   Console::WriteLine("(managed) convered BSTR to String: '{0}'", s);
}

#pragma unmanaged

void UnManagedFunc() {
   BSTR bs = SysAllocString(L"test string");
   printf_s("(unmanaged) passing BSTR to managed func...\n");
   ManagedTakesAString(bs);
}

#pragma managed

int main() {
   UnManagedFunc();
}
```

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
