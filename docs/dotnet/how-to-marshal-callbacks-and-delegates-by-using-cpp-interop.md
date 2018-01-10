---
title: "Porady: kierowanie wywołań zwrotnych i delegatów za pomocą międzyoperacyjności języka C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- C++ Interop, callbacks and delegates
- interop [C++], callbacks and delegates
- delegates [C++], marshaling
- marshaling [C++], callbacks and delegates
- callbacks [C++], marshaling
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dbae96aeb7b11105a1a2aa30aa513c8d94011a91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>Porady: przeprowadzanie marshalingu wywołań zwrotnych i delegatów za pomocą międzyoperacyjności języka C++
W tym temacie przedstawiono kierowanie wywołań zwrotnych i deleguje (zarządzanej wersji wywołanie zwrotne) między zarządzanymi i niezarządzanymi kodu za pomocą języka Visual C++.  
  
 Poniższy kod przykłady użycia [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) dyrektywy #pragma do zaimplementowania zarządzanych i niezarządzanych funkcji w tym samym pliku, ale można również zdefiniować funkcje w oddzielnych plików. Nie trzeba być kompilowana przy użyciu plików zawierających tylko funkcje niezarządzane [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób konfigurowania niezarządzanego API do wyzwolenia zarządzanego obiektu delegowanego. Delegat zarządzanych jest tworzony i jednej z metod międzyoperacyjnego <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>, służy do pobierania podstawowy punkt wejścia dla delegata. Ten adres są następnie przekazywane do niezarządzanej funkcji wywołania go z nie wie, fakt, że są one zaimplementowane jako funkcja zarządzanych.  
  
 Zwróć uwagę, że jest to możliwe, ale nie jest to konieczne, aby przypiąć delegata za pomocą [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) zapobiegające jej ponownie znajduje się lub usuwane przez moduł garbage collector. Konieczna jest ochrona z przedwczesny wyrzucanie elementów bezużytecznych, ale przypinanie chroni więcej niż jest to konieczne, uniemożliwia kolekcji, ale uniemożliwia także programowi relokacji.  
  
 Jeśli delegat znajduje się ponownie przez wyrzucania elementów bezużytecznych, nie wpłynie to wywołanie zwrotne underlaying zarządzane, więc <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> służy do dodawania odwołania do delegata, umożliwiając przenoszenie obiektu delegowanego, ale uniemożliwia usuwania. Za pomocą dojścia GCHandle zamiast pin_ptr zmniejsza ryzyko fragmentacji sterty zarządzanej.  
  
```  
// MarshalDelegate1.cpp  
// compile with: /clr  
#include <iostream>  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
// Declare an unmanaged function type that takes two int arguments  
// Note the use of __stdcall for compatibility with managed code  
typedef int (__stdcall *ANSWERCB)(int, int);  
  
int TakesCallback(ANSWERCB fp, int n, int m) {  
   printf_s("[unmanaged] got callback address, calling it...\n");  
   return fp(n, m);  
}  
  
#pragma managed  
  
public delegate int GetTheAnswerDelegate(int, int);  
  
int GetNumber(int n, int m) {  
   Console::WriteLine("[managed] callback!");  
   return n + m;  
}  
  
int main() {  
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);  
   GCHandle gch = GCHandle::Alloc(fp);  
   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);  
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());  
   Console::WriteLine("[managed] sending delegate as callback...");  
  
// force garbage collection cycle to prove  
// that the delegate doesn't get disposed  
   GC::Collect();  
  
   int answer = TakesCallback(cb, 243, 257);  
  
// release reference to delegate  
   gch.Free();  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest podobny do poprzedniego przykładu, ale w takim przypadku wskaźnika określona funkcja jest przechowywane przez niezarządzanego API, aby go można wywołać w dowolnej chwili, wymagających pomijane wyrzucanie elementów bezużytecznych przez dowolnego czas. W związku z tym w poniższym przykładzie użyto globalnego wystąpienia <xref:System.Runtime.InteropServices.GCHandle> uniemożliwi delegat przeniesiono, niezależnie od zakresem funkcji. Zgodnie z opisem w pierwszym przykładzie, przy użyciu pin_ptr nie jest konieczne te przykłady, ale w takim przypadku nie działa mimo to, jak zakres pin_ptr jest ograniczona do jednej funkcji.  
  
```  
// MarshalDelegate2.cpp  
// compile with: /clr   
#include <iostream>  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
// Declare an unmanaged function type that takes two int arguments  
// Note the use of __stdcall for compatibility with managed code  
typedef int (__stdcall *ANSWERCB)(int, int);  
static ANSWERCB cb;  
  
int TakesCallback(ANSWERCB fp, int n, int m) {  
   cb = fp;  
   if (cb) {  
      printf_s("[unmanaged] got callback address (%d), calling it...\n", cb);  
      return cb(n, m);  
   }  
   printf_s("[unmanaged] unregistering callback");  
   return 0;  
}  
  
#pragma managed  
  
public delegate int GetTheAnswerDelegate(int, int);  
  
int GetNumber(int n, int m) {  
   Console::WriteLine("[managed] callback!");  
   static int x = 0;  
   ++x;  
  
   return n + m + x;  
}  
  
static GCHandle gch;  
  
int main() {  
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);  
  
   gch = GCHandle::Alloc(fp);  
  
   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);  
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());  
   Console::WriteLine("[managed] sending delegate as callback...");  
  
   int answer = TakesCallback(cb, 243, 257);  
  
   // possibly much later (in another function)...  
  
   Console::WriteLine("[managed] releasing callback mechanisms...");  
   TakesCallback(0, 243, 257);  
   gch.Free();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)