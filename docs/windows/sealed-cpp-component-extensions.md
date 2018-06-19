---
title: zapieczętowane (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05c75aef047e914086aaf4ae2c0d0d3bdd04e8c7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890866"
---
# <a name="sealed--c-component-extensions"></a>sealed (C++ Component Extensions)
`sealed` jest słowem kluczowym kontekstowej dla klasy ref, który wskazuje, że nie można zastąpić członka wirtualnego lub że typu nie można użyć jako typu podstawowego.  
  
> [!NOTE]
>  ISO C ++ 11 standardowe języka [końcowego](../cpp/final-specifier.md) — słowo kluczowe, który jest obsługiwany w programie Visual Studio. Użyj `final` na standardowych klas i `sealed` na klasy ref.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
  
## <a name="syntax"></a>Składnia
  
```  
ref class identifier sealed {...};  
virtual return-type identifier() sealed {...};  
```  
  
### <a name="parameters"></a>Parametry  
  
 *Identyfikator*  
 Nazwa klasy lub funkcji.  
  
 *zwracanego typu*  
 Typ zwracany przez funkcję.  
  
## <a name="remarks"></a>Uwagi  
  
 W pierwszym przykładzie składni klasy jest zapieczętowany. W drugim przykładzie funkcji wirtualnej jest zapieczętowany.  
  
 `sealed` — Słowo kluczowe jest prawidłowy dla celów natywnego, a także do środowiska wykonawczego systemu Windows i środowisko uruchomieniowe języka wspólnego (CLR). Aby uzyskać więcej informacji, zobacz [specyfikatory Override i kompilacjach macierzystych](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
 Można wykrywać w czasie kompilacji, czy typ jest zapieczętowany przy użyciu `__is_sealed(type)` typu cechy. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 `sealed` jest słowem kluczowym kontekstowa.  Aby uzyskać więcej informacji, zobacz [słowa kluczowe Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Zobacz [Ref klas i struktur](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania  
 (Istnieją nie uwagi dla tej funkcji języka, które dotyczą tylko środowiska CLR.)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 Poniższy przykład kodu pokazuje wpływ `sealed` wirtualnego elementu członkowskiego.  
  
```cpp  
// sealed_keyword.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
   virtual void g();  
};  
  
ref class X : I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
  
   virtual void g() sealed {  
      System::Console::WriteLine("X::f override of I1::g");  
   }  
};  
  
ref class Y : public X {  
public:  
   virtual void f() override {  
      System::Console::WriteLine("Y::f override of I1::f");  
   }  
  
   /*  
   // the following override generates a compiler error  
   virtual void g() override {  
      System::Console::WriteLine("Y::g override of I1::g");  
   }    
   */  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
   MyI -> g();  
  
   I1 ^ MyI2 = gcnew Y;  
   MyI2 -> f();  
}  
```  
  
```Output  
X::f override of I1::f  
X::f override of I1::g  
Y::f override of I1::f  
```  
  
 W następnym przykładzie kodu pokazano, jak można oznaczyć klasę jako sealed.  
  
```cpp  
// sealed_keyword_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X sealed : I1 {  
public:  
   virtual void f() override {}  
};  
  
ref class Y : public X {   // C3246 base class X is sealed  
public:  
   virtual void f() override {}  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)