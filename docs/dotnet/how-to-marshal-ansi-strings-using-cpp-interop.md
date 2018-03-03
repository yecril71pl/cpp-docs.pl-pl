---
title: "Porady: kierowanie ciągów ANSI za pomocą międzyoperacyjności języka C++ | Dokumentacja firmy Microsoft"
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
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7e70d62fa7a94a7278080c31f6650b31b71ff35b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Porady: przeprowadzanie marshalingu ciągów ANSI za pomocą międzyoperacyjności języka C++
W tym temacie przedstawiono, jak można ciągów ANSI przekazany za pomocą międzyoperacyjności języka C++, ale programu .NET Framework <xref:System.String> reprezentuje ciągi w formacie Unicode, więc konwersja na ANSI jest dodatkowy krok. Do współpracy z innego typu ciąg, zobacz następujące tematy:  
  
-   [Instrukcje: przeprowadzanie marshalingu ciągów Unicode za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [Instrukcje: przeprowadzanie marshalingu ciągów COM za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
 Poniższy kod przykłady użycia [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) dyrektywy #pragma do zaimplementowania zarządzanych i niezarządzanych funkcji w tym samym pliku, ale te funkcje współdziałanie w taki sam sposób, jeśli zdefiniowane w oddzielnych plików. Ponieważ pliki zawierające tylko funkcje niezarządzane nie muszą być kompilowana przy użyciu [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md), zachowują ich charakterystyk wydajności.  
  
## <a name="example"></a>Przykład  
 W przykładzie pokazano, przekazując ciągu ANSI z zarządzanego przy użyciu funkcji niezarządzanej <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>. Ta metoda przydziela pamięć na stercie niezarządzane i zwraca adres po przeprowadzeniu konwersji. Oznacza to, że nie przypinanie jest niezbędne (ponieważ pamięci na stercie GC nie jest przekazywany do funkcji niezarządzanej) i czy IntPtr zwrócone z <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> musi jawnie zwolnione lub wyników wyciek pamięci.  
  
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
 W poniższym przykładzie pokazano, przekazywanie danych wymagane do uzyskania dostępu ciągu ANSI w funkcji zarządzanych, która jest wywoływana przez funkcji niezarządzanej. Funkcja zarządzanych, po otrzymaniu natywnego ciąg można używać go bezpośrednio lub przekonwertować go na ciąg zarządzanych za pomocą <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> — metoda, jak pokazano.  
  
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