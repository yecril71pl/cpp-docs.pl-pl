---
title: zamknięte (C++ Component Extensions) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 47efadb89786b7be54f33678d2f71d2474e4deb4
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604554"
---
# <a name="sealed--c-component-extensions"></a>sealed (C++ Component Extensions)
**zapieczętowane** jest słowem kluczowym kontekstowych dla klasy ref, która wskazuje, że wirtualny element członkowski nie może być zastąpiona, lub typu nie można użyć jako typu podstawowego.  
  
> [!NOTE]
>  ISO C ++ 11 standardowy język ma [końcowego](../cpp/final-specifier.md) — słowo kluczowe, która jest obsługiwana w programie Visual Studio. Użyj **końcowego** na standardowych klas i **zapieczętowanego** na klasy ref.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
  
## <a name="syntax"></a>Składnia
  
```  
ref class identifier sealed {...};  
virtual return-type identifier() sealed {...};  
```  
  
### <a name="parameters"></a>Parametry  
  
 *Identyfikator*  
 Nazwa klasy lub funkcji.  
  
 *zwracany typ*  
 Typ, który jest zwracany przez funkcję.  
  
## <a name="remarks"></a>Uwagi  
  
 W pierwszym przykładzie składni klasa jest zapieczętowany. W drugim przykładzie funkcją wirtualną jest zapieczętowany.  
  
 **Zapieczętowanego** — słowo kluczowe jest prawidłowy dla natywnych obiektów docelowych, a także dla środowiska uruchomieniowego Windows i środowisko uruchomieniowe języka wspólnego (CLR). Aby uzyskać więcej informacji, zobacz [zastąpienie specyfikatorów i kompilacji macierzystych](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
 Można wykrywać w czasie kompilacji, czy typ jest zapieczętowany przy użyciu `__is_sealed(type)` cechy typu. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 **zapieczętowane** jest kontekstowej słowem kluczowym.  Aby uzyskać więcej informacji, zobacz [Context-Sensitive Keywords](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Zobacz [klasy i struktury odwołania](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: `/ZW`  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania  
 (Nie ma żadnych uwag dla tej funkcji języka, które dotyczą tylko środowiska uruchomieniowego języka wspólnego).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: `/clr`  
  
### <a name="examples"></a>Przykłady  
 Ten poniższy kod ilustruje efekt **zapieczętowanego** na wirtualny element członkowski.  
  
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
  
 Następny przykład kodu pokazuje, jak oznaczyć klasę jako zapieczętowany.  
  
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