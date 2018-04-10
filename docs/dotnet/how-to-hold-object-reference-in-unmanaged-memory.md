---
title: 'Porady: utrzymywanie odwołania do obiektu w pamięci niezarządzanej | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- object references, in native functions
- objects [C++], reference in native functions
- references, to objects in native functions
- gcroot keyword [C++], object reference in native function
ms.assetid: a61eb8ce-3982-477d-8d3d-2173fd57166d
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: debda931ae121e109c4b1008054ace11a714f065
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-hold-object-reference-in-unmanaged-memory"></a>Porady: utrzymywanie odwołania do obiektu w pamięci niezarządzanej
Można użyć gcroot.h, który opakowuje <xref:System.Runtime.InteropServices.GCHandle>, aby pomieścić odwołanie do obiektu CLR w pamięci niezarządzanej. Alternatywnie można użyć `GCHandle` bezpośrednio.  
  
## <a name="example"></a>Przykład  
  
```  
// hold_object_reference.cpp  
// compile with: /clr  
#include "gcroot.h"  
using namespace System;  
  
#pragma managed  
class StringWrapper {  
  
private:  
   gcroot<String ^ > x;  
  
public:  
   StringWrapper() {  
      String ^ str = gcnew String("ManagedString");  
      x = str;  
   }  
  
   void PrintString() {  
      String ^ targetStr = x;  
      Console::WriteLine("StringWrapper::x == {0}", targetStr);  
   }  
};  
#pragma unmanaged  
int main() {  
   StringWrapper s;  
   s.PrintString();  
}  
```  
  
```Output  
StringWrapper::x == ManagedString  
```  
  
## <a name="example"></a>Przykład  
 `GCHandle`zapewnia sposób przechowuje odwołania zarządzanego obiektu w pamięci niezarządzanej.  Możesz użyć <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> metodę w celu utworzenia nieprzezroczystego uchwyt do zarządzanego obiektu i <xref:System.Runtime.InteropServices.GCHandle.Free%2A> do jego zwolnienia. Ponadto <xref:System.Runtime.InteropServices.GCHandle.Target%2A> metody umożliwia uzyskiwanie odwołanie do obiektu z dojścia w kodzie zarządzanym.  
  
```  
// hold_object_reference_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma managed  
class StringWrapper {  
   IntPtr m_handle;  
public:  
   StringWrapper() {  
      String ^ str = gcnew String("ManagedString");  
      m_handle = static_cast<IntPtr>(GCHandle::Alloc(str));  
   }  
   ~StringWrapper() {  
      static_cast<GCHandle>(m_handle).Free();  
   }  
  
   void PrintString() {  
      String ^ targetStr = safe_cast< String ^ >(static_cast<GCHandle>(m_handle).Target);  
      Console::WriteLine("StringWrapper::m_handle == {0}", targetStr);  
   }  
};  
  
#pragma unmanaged  
int main() {  
   StringWrapper s;   
   s.PrintString();  
}  
```  
  
```Output  
StringWrapper::m_handle == ManagedString  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)