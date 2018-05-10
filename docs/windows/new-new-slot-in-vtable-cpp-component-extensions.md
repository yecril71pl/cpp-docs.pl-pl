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
ms.openlocfilehash: 7189909f3cff84d2bb1a767e4ddeda817bcd6128
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="new-new-slot-in-vtable--c-component-extensions"></a>new (nowe gniazdo w vtable) (C++ Component Extensions)
`new` — Słowo kluczowe wskazuje, czy członek wirtualnego otrzymają nowe gniazdo w vtable.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 (Brak żadnych uwag dla tej funkcji języka, które są stosowane do wszystkich środowisk uruchomieniowych.)  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Nie są obsługiwane w środowisku wykonawczym systemu Windows.  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 **Uwagi**  
  
 W **/CLR** kompilacji, `new` wskazuje, czy członek wirtualnego otrzymają nowe gniazdo w vtable; funkcja nie przesłania metody klasy podstawowej.  
  
 `new` powoduje, że modyfikator newslot mają zostać dodane do IL dla funkcji.  Aby uzyskać więcej informacji na temat newslot zobacz:  
  
-   [MethodInfo.GetBaseDefinition — metoda](https://msdn.microsoft.com/en-us/library/system.reflection.methodinfo.getbasedefinition.aspx)  
  
-   [Wyliczenie MethodAttributes — wyliczenie](https://msdn.microsoft.com/en-us/library/system.reflection.methodattributes.aspx)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykład przedstawia wynik `new`.  
  
```  
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
  
 **Output**  
  
```Output  
C::f() called  
  
D::f() called  
  
D::g() called  
  
D::g() called  
  
E::f() called  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)   
 [Specyfikatory zastąpienia](../windows/override-specifiers-cpp-component-extensions.md)