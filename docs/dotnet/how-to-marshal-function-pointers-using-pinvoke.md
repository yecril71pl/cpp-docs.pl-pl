---
title: "Porady: kierowanie wskaźników funkcji za pomocą funkcji PInvoke | Dokumentacja firmy Microsoft"
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
- interop [C++], callbacks and delegates
- platform invoke [C++], callbacks and delegates
- marshaling [C++], callbacks and delegates
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cf7f23ea9337b499d4ec80b19e3104074429cc71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-function-pointers-using-pinvoke"></a>Porady: przeprowadzanie marshalingu wskaźników funkcji za pomocą funkcji PInvoke
W tym temacie opisano sposób zarządzanych obiektów delegowanych podczas współpracy z niezarządzanych funkcji przy użyciu funkcji .NET Framework P/Invoke można użyć zamiast wskaźników funkcji. Jednak programistów Visual C++ są zachęcani do zamiast tego użyj funkcji międzyoperacyjności języka C++ (jeśli jest to możliwe), ponieważ P/Invoke zapewnia małego błąd kompilacji raportowania, nie jest bezpieczne i może być niewygodne wdrożenia. Jeśli niezarządzanego API jest dostarczana jako biblioteki DLL i kod źródłowy jest niedostępny, P/Invoke jest jedyną opcją. W przeciwnym razie zobacz następujące tematy:  
  
-   [Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [Instrukcje: przeprowadzanie marshalingu wywołań zwrotnych i delegatów za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
 Niezarządzane interfejsy API prowadzące wskaźników funkcji argumentów można wywołać z kodu zarządzanego z zarządzanego delegatem zamiast wskaźnika funkcji macierzystej. Kompilator automatycznie marshals delegata z funkcjami niezarządzanymi jako wskaźnik funkcji i wstawia kod niezbędne przejścia zarządzanych/niezarządzanych.  
  
## <a name="example"></a>Przykład  
 Poniższy kod składa się z modułu zarządzanych i niezarządzanych. Moduł niezarządzanym jest bibliotekę DLL, która definiuje funkcji o nazwie TakesCallback, który akceptuje wskaźnik funkcji. Ten adres służy do wykonywania funkcji.  
  
 Moduł zarządzany definiuje delegata, który jest przekazywane do kodu macierzystego jako wskaźnik funkcji i używa <xref:System.Runtime.InteropServices.DllImportAttribute> atrybut do udostępnienia funkcji macierzystej TakesCallback do kodu zarządzanego. W funkcji main wystąpienia delegata jest utworzony i przekazany do funkcji TakesCallback. Dane wyjściowe programu pokazuje, że ta funkcja jest wykonywany przez funkcję TakesCallback macierzystego.  
  
 Funkcja zarządzanych pomija wyrzucanie elementów bezużytecznych do zarządzanego pełnomocnika, aby zapobiec .NET Framework wyrzucanie elementów bezużytecznych z przemieszczanie delegata, podczas gdy wykonuje funkcji macierzystej.  
  
 Moduł zarządzany została skompilowana z/CLR, ale/CLR: pure działa również. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
```cpp  
// TraditionalDll5.cpp  
// compile with: /LD /EHsc  
#include <iostream>  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   /* Declare an unmanaged function type that takes two int arguments  
      Note the use of __stdcall for compatibility with managed code */  
   typedef int (__stdcall *CALLBACK)(int);  
   TRADITIONALDLL_API int TakesCallback(CALLBACK fp, int);  
}  
  
int TakesCallback(CALLBACK fp, int n) {  
   printf_s("[unmanaged] got callback address, calling it...\n");  
   return fp(n);  
}  
```  
  
```cpp  
// MarshalDelegate.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
public delegate int GetTheAnswerDelegate(int);  
public value struct TraditionalDLL {  
   [DllImport("TraditionalDLL5.dll")]  
   static public int TakesCallback(GetTheAnswerDelegate^ pfn, int n);  
};  
  
int GetNumber(int n) {  
   Console::WriteLine("[managed] callback!");  
   static int x = 0;  
   ++x;  
   return x + n;  
}  
  
int main() {  
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);  
   pin_ptr<GetTheAnswerDelegate^> pp = &fp;  
   Console::WriteLine("[managed] sending delegate as callback...");  
  
   int answer = TraditionalDLL::TakesCallback(fp, 42);  
}  
```  
  
 Należy pamiętać, że żadna jego część biblioteki DLL jest narażony na kod zarządzany przy użyciu tradycyjnych # dyrektywy include. W rzeczywistości biblioteki DLL jest dostępny tylko w czasie wykonywania, problemy z funkcjami zaimportowane z <xref:System.Runtime.InteropServices.DllImportAttribute> nie zostanie wykryty w czasie kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)