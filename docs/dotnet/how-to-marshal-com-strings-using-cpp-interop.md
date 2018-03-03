---
title: "Porady: kierowanie ciągów COM za pomocą międzyoperacyjności języka C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 45a79f3aa78d229c71aba5a1d1144d05afe7bbd7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>Porady: przeprowadzanie marshalingu ciągów COM za pomocą międzyoperacyjności języka C++
W tym temacie przedstawiono sposób BSTR (format ciągu podstawowe ich drużyna jest faworytem w programowaniu modelu COM) mogą być przekazywane z zarządzanego, do funkcji niezarządzanej i na odwrót. Do współpracy z innych typów parametrów, zobacz następujące tematy:  
  
-   [Instrukcje: przeprowadzanie marshalingu ciągów Unicode za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [Instrukcje: przeprowadzanie marshalingu ciągów ANSI za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
 Poniższy kod przykłady użycia [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) dyrektywy #pragma do zaimplementowania zarządzanych i niezarządzanych funkcji w tym samym pliku, ale te funkcje współdziałanie w taki sam sposób, jeśli zdefiniowane w oddzielnych plików. Nie trzeba być kompilowana przy użyciu plików zawierających tylko funkcje niezarządzane [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak BSTR (ciąg formatu w programowaniu modelu COM) mogą zostać przekazane z zarządzanych do niezarządzanych funkcji. Wywołanie zarządzanego używa funkcji <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> uzyskać adres BSTR reprezentację zawartość .NET System.String. Ten wskaźnik jest przypięty przy użyciu [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) aby upewnić się, że adres fizyczny nie ulega zmianie podczas cyklu zbierania pamięci podczas wykonuje funkcji niezarządzanej. Moduł zbierający elementy bezużyteczne jest zabronione w myśl przenoszenie pamięci do [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) wykracza poza zakres.  
  
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
 W poniższym przykładzie pokazano, jak mogą być przekazywane BSTR z niezarządzanych w funkcji niezarządzanej. Odbieranie funkcja zarządzanych albo użyć ciągu w jako BSTR lub <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> przekonwertować go do <xref:System.String> do użytku z innymi zarządzane funkcji. Ponieważ pamięci reprezentująca BSTR jest przydzielone na stercie niezarządzane przypinanie nie jest niezbędne, ponieważ nie istnieje żadne wyrzucanie elementów bezużytecznych na stercie niezarządzane.  
  
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