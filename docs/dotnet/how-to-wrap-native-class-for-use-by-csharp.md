---
title: 'Instrukcje: OPAKOWYWANIE klasy natywnej do użycia przezC#'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- native code [C++], Visual C# and
- classes [C++], Visual C# and
ms.assetid: 988819ae-cc6a-4453-8ff5-be369210d962
ms.openlocfilehash: e58530577fdcc87f4ca168b6976a848cba29b372
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751638"
---
# <a name="how-to-wrap-native-class-for-use-by-c"></a>Instrukcje: OPAKOWYWANIE klasy natywnej do użycia przezC#

Niniejszy przykład pokazuje, jak opakowywać natywnych klasy języka C++, dzięki czemu mogą być używane przez kod w języku C# lub innym języku .NET.

## <a name="example"></a>Przykład

```
// wrap_native_class_for_mgd_consumption.cpp
// compile with: /clr /LD
#include <windows.h>
#include <vcclr.h>
#using <System.dll>

using namespace System;

class UnmanagedClass {
public:
   LPCWSTR GetPropertyA() { return 0; }
   void MethodB( LPCWSTR ) {}
};

public ref class ManagedClass {
public:
   // Allocate the native object on the C++ Heap via a constructor
   ManagedClass() : m_Impl( new UnmanagedClass ) {}

   // Deallocate the native object on a destructor
   ~ManagedClass() {
      delete m_Impl;
   }

protected:
   // Deallocate the native object on the finalizer just in case no destructor is called
   !ManagedClass() {
      delete m_Impl;
   }

public:
   property String ^  get_PropertyA {
      String ^ get() {
         return gcnew String( m_Impl->GetPropertyA());
      }
   }

   void MethodB( String ^ theString ) {
      pin_ptr<const WCHAR> str = PtrToStringChars(theString);
      m_Impl->MethodB(str);
   }

private:
   UnmanagedClass * m_Impl;
};
```

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
