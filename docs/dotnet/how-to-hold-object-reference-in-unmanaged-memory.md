---
title: 'Instrukcje: Utrzymywanie odwołania do obiektu w pamięci niezarządzanej'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- object references, in native functions
- objects [C++], reference in native functions
- references, to objects in native functions
- gcroot keyword [C++], object reference in native function
ms.assetid: a61eb8ce-3982-477d-8d3d-2173fd57166d
ms.openlocfilehash: 0d8dc341d1fe2c61eba098abec9258a2c6dade79
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747985"
---
# <a name="how-to-hold-object-reference-in-unmanaged-memory"></a>Instrukcje: Utrzymywanie odwołania do obiektu w pamięci niezarządzanej

Możesz użyć gcroot.h, który otacza <xref:System.Runtime.InteropServices.GCHandle>, aby pomieścić odwołanie do obiektu CLR w pamięci niezarządzanej. Alternatywnie, można użyć `GCHandle` bezpośrednio.

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

`GCHandle` zapewnia sposób utrzymywanie odwołania do obiektu zarządzanego w niezarządzanej pamięci.  Możesz użyć <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> metodę w celu utworzenia nieprzezroczyste dojścia do obiektu zarządzanego i <xref:System.Runtime.InteropServices.GCHandle.Free%2A> do jego zwolnienia. Ponadto <xref:System.Runtime.InteropServices.GCHandle.Target%2A> metoda pozwala uzyskać odwołanie do obiektu powrót po awarii z dojście w kodzie zarządzanym.

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

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
