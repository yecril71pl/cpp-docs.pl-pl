---
title: "Jawne zastąpienia (C++ Component Extensions) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 387141945882bf3c491c55a4a8ab8ab3804e876a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="explicit-overrides--c-component-extensions"></a>Jawne zastąpienia (C++ Component Extensions)
W tym temacie omówiono sposób jawnie przesłonić element członkowski klasy podstawowej lub interfejsu. Nazwanego przesłaniania (jawne) należy używać tylko do zastąpienia metody Metoda pochodna, która ma inną nazwę.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 **Składnia**  
  
```  
  
      overriding-function-declarator = type::function [,type::function] { overriding-function-definition }  
overriding-function-declarator = function { overriding-function-definition }  
```  
  
 **Parametry**  
  
 *zastępowanie — funkcja — deklarator*  
 Zwracany typ, nazwa i argument listy zastępowanie funkcji.  Należy pamiętać, że funkcja pomijania muszą mieć taką samą nazwę jak przesłaniana funkcja.  
  
 *Typ*  
 Typ podstawowy zawiera funkcję do zastąpienia.  
  
 *Funkcja*  
 Rozdzielana przecinkami lista co najmniej jedną nazwę funkcji do zastąpienia.  
  
 *zastępowanie--definicji funkcji*  
 Instrukcje treści funkcji definiujące zastępowanie funkcji.  
  
 **Uwagi**  
  
 Użyj jawnego przesłania do utworzenia aliasu dla podpisu metody lub w celu udostępnienia różnych implementacji dla metody witht takiego samego podpisu.  
  
 Informacje dotyczące modyfikowania zachowania dziedziczonych typów i członków dziedziczonych typu, zobacz [specyfikatory Override](../windows/override-specifiers-cpp-component-extensions.md).  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 **Uwagi**  
  
 Informacje o jawnego przesłania w kodzie natywnym lub kodu skompilowanego z **: oldsyntax**, zobacz [jawne zastąpienia](../cpp/explicit-overrides-cpp.md).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykład kodu zawiera proste, niejawnego zastąpienia i implementację elementu członkowskiego w interfejs podstawowy, nie za pomocą jawne zastąpienia.  
  
```  
// explicit_override_1.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
X::f override of I1::f  
```  
  
 **Przykład**  
  
 Poniższy przykład kodu pokazuje, jak do zaimplementowania wszystkie elementy członkowskie interfejsu za pomocą wspólnego podpisu za pomocą składnia jawnego przesłaniania.  
  
```  
  
// explicit_override_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
interface struct I2 {  
   virtual void f();  
};  
  
ref struct X : public I1, I2 {  
   virtual void f() = I1::f, I2::f {  
      System::Console::WriteLine("X::f override of I1::f and I2::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   I2 ^ MyI2 = gcnew X;  
   MyI -> f();  
   MyI2 -> f();  
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
X::f override of I1::f and I2::f  
X::f override of I1::f and I2::f  
```  
  
 **Przykład**  
  
 Poniższy przykład kodu pokazuje, jak zastąpienie funkcja może mieć inną nazwę funkcji, które implementuje.  
  
```  
// explicit_override_3.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void g() = I1::f {  
      System::Console::WriteLine("X::g");  
   }  
};  
  
int main() {  
   I1 ^ a = gcnew X;  
   a->f();  
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
X::g  
```  
  
 **Przykład**  
  
 Poniższy przykładowy kod przedstawia implementację interfejsu jawnego, która implementuje kolekcji bezpieczne typu.  
  
```  
// explicit_override_4.cpp  
// compile with: /clr /LD  
using namespace System;  
ref class R : ICloneable {  
   int X;  
  
   virtual Object^ C() sealed = ICloneable::Clone {  
      return this->Clone();  
   }  
  
public:  
   R() : X(0) {}  
   R(int x) : X(x) {}  
  
   virtual R^ Clone() {  
      R^ r = gcnew R;  
      r->X = this->X;  
      return r;  
   }  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)