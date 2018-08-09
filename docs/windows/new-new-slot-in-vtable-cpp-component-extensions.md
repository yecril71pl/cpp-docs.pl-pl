---
title: New (nowe gniazdo w vtable) (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7ef754c380353716c923f6d5f404106cebc163c9
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011884"
---
# <a name="new-new-slot-in-vtable--c-component-extensions"></a>new (nowe gniazdo w vtable) (C++ Component Extensions)
**Nowe** słowo kluczowe wskazuje, że wirtualny element członkowski otrzyma nowe gniazdo w vtable.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 (Nie ma żadnych uwag dla tej funkcji języka, które są stosowane do wszystkich środowisk uruchomieniowych).  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Nie są obsługiwane w programie Windows Runtime.  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
### <a name="remarks"></a>Uwagi  
  
 W `/clr` kompilacji, **nowe** wskazuje, że wirtualny element członkowski otrzyma nowe gniazdo w vtable; że funkcja nie zastępuje metody klasy bazowej.  
  
 **nowe** powoduje, że modyfikatora nowego gniazda do IL dla funkcji.  Aby uzyskać więcej informacji na temat nowego gniazda zobacz:  
  
-   [Metoda MethodInfo.GetBaseDefinition](https://msdn.microsoft.com/library/system.reflection.methodinfo.getbasedefinition.aspx)  
  
-   [Wyliczenie MethodAttributes](https://msdn.microsoft.com/library/system.reflection.methodattributes.aspx)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: `/clr`  
  
### <a name="examples"></a>Przykłady  
  
 Poniższy przykład pokazuje wpływ **nowe**.  
  
```cpp  
// newslot.cpp  
// compile with: /clr  
ref class C {  
public:  
   virtual void f() {  
      System::Console::WriteLine("C::f() called");  
   }  
  
   virtual void g() {  
      System::Console::WriteLine("C::g() called");  
   }  
};  
  
ref class D : public C {  
public:  
   virtual void f() new {  
      System::Console::WriteLine("D::f() called");  
   }  
  
   virtual void g() override {  
      System::Console::WriteLine("D::g() called");  
   }  
};  
  
ref class E : public D {  
public:  
   virtual void f() override {  
      System::Console::WriteLine("E::f() called");  
   }  
};  
  
int main() {  
   D^ d = gcnew D;  
   C^ c = gcnew D;  
  
   c->f();   // calls C::f  
   d->f();   // calls D::f  
  
   c->g();   // calls D::g  
   d->g();   // calls D::g  
  
   D ^ e = gcnew E;  
   e->f();   // calls E::f  
}  
```  
  
```Output  
C::f() called  
  
D::f() called  
  
D::g() called  
  
D::g() called  
  
E::f() called  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)   
 [Specyfikatory przesłonięć](../windows/override-specifiers-cpp-component-extensions.md)