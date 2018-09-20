---
title: 'Porady: przeprowadzanie Marshalingu ciągów COM za pomocą międzyoperacyjności języka C++ | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f758352c11cc5e7d8c66c2a29b69504b2c5ad641
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394182"
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>Porady: przeprowadzanie marshalingu ciągów COM za pomocą międzyoperacyjności języka C++

W tym temacie pokazano, jak ciąg BSTR (format ciągu podstawowe faworytem w programowaniu modelu COM) może być przekazywany z zarządzanej do niezarządzanej funkcji i na odwrót. Do współpracy z innymi typami parametrów, zobacz następujące tematy:

- [Instrukcje: przeprowadzanie marshalingu ciągów Unicode za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Instrukcje: przeprowadzanie marshalingu ciągów ANSI za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

Poniższy kod przykłady użycia [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) #pragma — dyrektywy do zaimplementowania zarządzanych i niezarządzanych funkcji w tym samym pliku, ale te funkcje współpracować w taki sam sposób, jeśli zdefiniowany w oddzielnych plikach. Pliki zawierające tylko funkcji niezarządzanych nie muszą być skompilowana przy użyciu [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak ciąg BSTR (ciąg formatu w programowaniu modelu COM) mogą być przekazywane z zarządzanego do niezarządzanej funkcji. Wywołanie zarządzanego funkcja <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> uzyskać adres BSTR reprezentacja zawartość .NET System.String. This, wskaźnik jest przypięty, za pomocą [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) aby upewnić się, że adres fizyczny nie ulega zmianie podczas cyklu kolekcji wyrzucania elementów, gdy wykonuje niezarządzanej funkcji. Moduł zbierający elementy bezużyteczne zakaz przenoszenia pamięci do momentu [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) wykracza poza zakres.

```
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

W poniższym przykładzie pokazano, jak może być przekazywany Ciąg BSTR z niezarządzanych do niezarządzanej funkcji. Odbieranie funkcji zarządzanej można użyć ciągu w jako ciąg BSTR lub przy użyciu <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> Aby przekonwertować go pod kątem <xref:System.String> do użycia z innymi funkcje zarządzane. Ponieważ pamięci reprezentująca BSTR została przydzielona na stosie niezarządzanym, brak możliwości przypinania jest to konieczne, ponieważ nie istnieje żadne wyrzucanie elementów bezużytecznych na stosie niezarządzanym.

```
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

## <a name="see-also"></a>Zobacz też

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)