---
title: Zdefiniowane przez użytkownika atrybuty (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 22f8dfa7e78568f100b0c58c881b9e84cb47a149
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891769"
---
# <a name="user-defined-attributes--c-component-extensions"></a>Atrybuty zdefiniowane przez użytkownika (C++ Component Extensions)
Atrybuty niestandardowe umożliwiają rozszerzanie metadanych interfejsu, klasy lub struktury, — metoda, parametr lub wyliczenia.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 Wszystkich środowisk uruchomieniowych obsługuje atrybutów niestandardowych.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 C + +/ CX atrybutów obsługuje tylko właściwości, ale nie atrybutu konstruktorów lub metody.  
  
### <a name="remarks"></a>Uwagi  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania  
 Atrybuty niestandardowe umożliwiają rozszerzenie metadanych elementu zarządzanego. Aby uzyskać więcej informacji, zobacz [atrybutów](/dotnet/standard/attributes/index).  
  
### <a name="remarks"></a>Uwagi  
 Informacje i składni przedstawionych w tym temacie jest przeznaczona do zastępowania informacje przedstawione w [atrybutu](../windows/attribute.md).  
  
 Można określić atrybutu niestandardowego Definiowanie typu i wprowadzając <xref:System.Attribute> klasę podstawową dla typu i opcjonalnie stosowania <xref:System.AttributeUsageAttribute> atrybutu.  
  
 Na przykład w Microsoft Transaction Server (MTS) 1.0, zachowanie względem transakcji, synchronizacja, równoważenie obciążenia i określonej za pomocą niestandardowych identyfikatorów GUID wstawione do biblioteki typów przy użyciu atrybutu niestandardowego ODL itd. W związku z tym klient serwera MTS może określić jego właściwości, odczytując biblioteki typów. W programie .NET Framework analogowy biblioteki typów są metadane, a analogowy atrybutu niestandardowego ODL jest atrybutów niestandardowych. Ponadto odczytu biblioteki typów jest odpowiednikiem za pomocą odbicia typów.  
  
 Aby uzyskać więcej informacji, zobacz,  
  
-   [Docelowe atrybuty](../windows/attribute-targets-cpp-component-extensions.md)  
  
-   [Typy parametrów atrybutu](../windows/attribute-parameter-types-cpp-component-extensions.md)  
  
 Aby uzyskać informacji na temat podpisywania zestawy w programie Visual C++, zobacz [silnych nazwach (podpisywanie zestawów) (C + +/ CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykład przedstawia sposób definiowania atrybutu niestandardowego.  
  
```cpp  
// user_defined_attributes.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::All)]  
ref struct Attr : public Attribute {  
   Attr(bool i){}  
   Attr(){}  
};  
  
[Attr]  
ref class MyClass {};  
```  
  
 **Przykład**  
  
 Poniższy przykład przedstawia niektóre ważne funkcje atrybutów niestandardowych. Na przykład, w tym przykładzie przedstawiono typowe obciążenie atrybutów niestandardowych: utworzenie wystąpienia serwera, który można całkowicie opisania siebie klientom.  
  
```cpp  
// extending_metadata_b.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Reflection;  
  
public enum class Access { Read, Write, Execute };  
  
// Defining the Job attribute:  
[AttributeUsage(AttributeTargets::Class, AllowMultiple=true )]  
public ref class Job : Attribute {  
public:  
   property int Priority {  
      void set( int value ) { m_Priority = value; }  
      int get() { return m_Priority; }  
   }  
  
   // You can overload constructors to specify Job attribute in different ways  
   Job() { m_Access = Access::Read; }  
   Job( Access a ) { m_Access = a; }  
   Access m_Access;  
  
protected:  
   int m_Priority;  
};  
  
interface struct IService {  
   void Run();  
};  
  
   // Using the Job attribute:  
   // Here we specify that QueryService is to be read only with a priority of 2.  
   // To prevent namespace collisions, all custom attributes implicitly   
   // end with "Attribute".   
  
[Job( Access::Read, Priority=2 )]  
ref struct QueryService : public IService {  
   virtual void Run() {}  
};  
  
// Because we said AllowMultiple=true, we can add multiple attributes   
[Job(Access::Read, Priority=1)]  
[Job(Access::Write, Priority=3)]  
ref struct StatsGenerator : public IService {  
   virtual void Run( ) {}  
};  
  
int main() {  
   IService ^ pIS;  
   QueryService ^ pQS = gcnew QueryService;  
   StatsGenerator ^ pSG = gcnew StatsGenerator;  
  
   //  use QueryService  
   pIS = safe_cast<IService ^>( pQS );  
  
   // use StatsGenerator  
   pIS = safe_cast<IService ^>( pSG );  
  
   // Reflection  
   MemberInfo ^ pMI = pIS->GetType();  
   array <Object ^ > ^ pObjs = pMI->GetCustomAttributes(false);  
  
   // We can now quickly and easily view custom attributes for an   
   // Object through Reflection */  
   for( int i = 0; i < pObjs->Length; i++ ) {  
      Console::Write("Service Priority = ");  
      Console::WriteLine(static_cast<Job^>(pObjs[i])->Priority);  
      Console::Write("Service Access = ");  
      Console::WriteLine(static_cast<Job^>(pObjs[i])->m_Access);  
   }  
}  
```  
  
 **Output**  
  
```Output  
Service Priority = 0  
  
Service Access = Write  
  
Service Priority = 3  
  
Service Access = Write  
  
Service Priority = 1  
  
Service Access = Read  
```  
  
 **Przykład**  
  
 Obiekt ^ typ zastąpi typ danych variant. W poniższym przykładzie zdefiniowano atrybutu niestandardowego, który pobiera tablicę obiektów ^ jako parametry.  
  
 Argumentów atrybutu muszą być stałymi kompilacji; w większości przypadków powinny one być stałe literałami.  
  
 Zobacz [typeid](../windows/typeid-cpp-component-extensions.md) informacji dotyczących zwracać wartość System::Type z bloku atrybutu niestandardowego.  
  
```cpp  
// extending_metadata_e.cpp  
// compile with: /clr /c  
using namespace System;  
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Method)]  
public ref class AnotherAttr : public Attribute {  
public:  
   AnotherAttr(array<Object^>^) {}  
   array<Object^>^ var1;  
};  
  
// applying the attribute  
[ AnotherAttr( gcnew array<Object ^> { 3.14159, "pi" }, var1 = gcnew array<Object ^> { "a", "b" } ) ]  
public ref class SomeClass {};  
```  
  
 **Przykład**  
  
 Środowisko uruchomieniowe wymaga, że publicznego część klasy atrybutu niestandardowego musi być możliwy do serializacji.  Podczas tworzenia niestandardowych atrybutów nazwanych argumentów atrybutu niestandardowego są ograniczone do kompilacji stałe.  (Go traktować jako sekwencja bitów dołączany do układu klasy w metadanych.)  
  
```cpp  
// extending_metadata_f.cpp  
// compile with: /clr /c  
using namespace System;  
ref struct abc {};  
  
[AttributeUsage( AttributeTargets::All )]  
ref struct A : Attribute {  
   A( Type^ ) {}  
   A( String ^ ) {}  
   A( int ) {}  
};  
  
[A( abc::typeid )]  
ref struct B {};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)