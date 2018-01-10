---
title: TypeID (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
caps.latest.revision: "35"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 20a3b1153bbb8a8502a54aa74998817abf191860
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="typeid--c-component-extensions"></a>typeid (C++ Component Extensions)
Pobiera wartość, która określa typ obiektu.  
  
> [!WARNING]
>  W tym temacie odnosi się do wersji rozszerzenia składnika C++ typeid. To słowo kluczowe w wersji ISO C++ [typeid — Operator](../cpp/typeid-operator.md).  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
T::typeid  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Nazwa typu.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
Platform::Type^ type = T::typeid;  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Nazwa typu.  
  
### <a name="remarks"></a>Uwagi  
 W języku C + +/ CX, identyfikator typu zwraca [Platform::Type](../cppcx/platform-type-class.md) który jest utworzone na podstawie informacji o typie środowiska uruchomieniowego.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 **Składnia**  
  
```  
  
type::typeid  
```  
  
 **Parametry**  
  
 *Typ*  
 Nazwa typu (abstract deklarator), dla którego ma zostać zwrócony obiekt System::Type.  
  
 **Uwagi**  
  
 `typeid`jest używany do pobierania <xref:System.Type> dla typu w czasie kompilacji.  
  
 `typeid`jest podobny do pobierania System::Type dla typu w czasie wykonywania za pomocą <xref:System.Type.GetType%2A> lub <xref:System.Object.GetType%2A>. Typeid akceptuje jednak tylko nazwę typu jako parametr.  Jeśli chcesz użyć wystąpienia typu można pobrać nazwy System::Type, użyj GetType.  
  
 `typeid`musi mieć możliwość oceny nazwę typu (typ) w czasie kompilacji, podczas gdy GetType ocenia typ do zwrócenia w czasie wykonywania.  
  
 `typeid`Nazwa typu macierzystego i wspólne alias środowiska uruchomieniowego języka dla nazwy typu macierzystego; zobacz [.NET Framework odpowiedniki typów natywnych języka C++ (C + +/ CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md) Aby uzyskać więcej informacji.  
  
 `typeid`współdziała również z natywnych typów, mimo że nadal zwróci System::Type.  Aby uzyskać struktury type_info —, należy użyć [typeid — Operator](../cpp/typeid-operator.md).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykład porównuje typeid, słowo kluczowe GetType() elementu członkowskiego.  
  
```  
// keyword__typeid.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct G {  
   int i;  
};  
  
int main() {  
   G ^ pG = gcnew G;  
   Type ^ pType = pG->GetType();  
   Type ^ pType2 = G::typeid;  
  
   if (pType == pType2)  
      Console::WriteLine("typeid and GetType returned the same System::Type");  
   Console::WriteLine(G::typeid);  
  
   typedef float* FloatPtr;  
   Console::WriteLine(FloatPtr::typeid);  
}  
```  
  
 **Output**  
  
```Output  
typeid and GetType returned the same System::Type  
G  
  
System.Single*  
  
```  
  
 **Przykład**  
  
 Poniższy przykład pokazuje, że zmienna typu może być używane System::Type można pobrać atrybutów w danym typie.  Ponadto dla niektórych typów, będzie trzeba utworzyć typedef do użycia `typeid`.  
  
```  
// keyword__typeid_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Security;  
using namespace System::Security::Permissions;  
  
typedef int ^ handle_to_int;  
typedef int * pointer_to_int;  
  
public ref class MyClass {};  
  
class MyClass2 {};  
  
[attribute(AttributeTargets::All)]  
ref class AtClass {  
public:  
   AtClass(Type ^) {  
      Console::WriteLine("in AtClass Type ^ constructor");  
   }  
};  
  
[attribute(AttributeTargets::All)]  
ref class AtClass2 {  
public:  
   AtClass2() {  
      Console::WriteLine("in AtClass2 constructor");  
   }  
};  
  
// Apply the AtClass and AtClass2 attributes to class B  
[AtClass(MyClass::typeid), AtClass2]     
[AttributeUsage(AttributeTargets::All)]  
ref class B : Attribute {};  
  
int main() {  
   Type ^ MyType = B::typeid;  
  
   Console::WriteLine(MyType->IsClass);  
  
   array<Object^>^ MyArray = MyType -> GetCustomAttributes(true);  
   for (int i = 0 ; i < MyArray->Length ; i++ )  
      Console::WriteLine(MyArray[i]);  
  
   if (int::typeid != pointer_to_int::typeid)  
      Console::WriteLine("int::typeid != pointer_to_int::typeid, as expected");  
  
   if (int::typeid == handle_to_int::typeid)  
      Console::WriteLine("int::typeid == handle_to_int::typeid, as expected");  
}  
```  
  
 **Output**  
  
```Output  
True  
  
in AtClass2 constructor  
  
in AtClass Type ^ constructor  
  
AtClass2  
  
System.AttributeUsageAttribute  
  
AtClass  
  
int::typeid != pointer_to_int::typeid, as expected  
  
int::typeid == handle_to_int::typeid, as expected  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)