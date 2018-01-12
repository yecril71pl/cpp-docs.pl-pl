---
title: "Porady: Wyliczanie typów danych przy użyciu odbicia (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- assemblies [C++], enumerating data types in
- public types [C++]
- reflection [C++], external assemblies
- assemblies [C++]
- data types [C++], enumerating
- public members [C++]
ms.assetid: c3578e6d-bb99-4599-80e1-ab795305f878
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 209124e6d4e8afa7930a4c74d2cce1acd7e279b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-enumerate-data-types-in-assemblies-using-reflection-ccli"></a>Porady: wyliczanie typów danych w zestawach za pomocą odbicia (C++/CLI)
Poniższy kod przedstawia wyliczenie typy publiczne i elementów członkowskich za pomocą <xref:System.Reflection>.  
  
 Podana nazwa zestawu w lokalnym katalogu lub w pamięci GAC, poniższy kod próby otwarcia zestawu i pobrać opisy. W przypadku powodzenia każdego typu zostanie wyświetlony z jego publiczne elementy członkowskie.  
  
 Należy pamiętać, że <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> wymaga służy ma rozszerzenia pliku. W związku z tym za pomocą "mscorlib.dll" jako argumentu wiersza polecenia zakończy się niepowodzeniem, gdy przy użyciu tylko "mscorlib" spowoduje wyświetlanie typów .NET Framework. Jeśli zostanie podana żadna nazwa zestawu, kod wykryje i typów w bieżącym zestawie raportów (EXE, wynikające z tego kodu).  
  
## <a name="example"></a>Przykład  
  
```  
// self_reflection.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Reflection;  
using namespace System::Collections;  
  
public ref class ExampleType {  
public:  
   ExampleType() {}  
   void Func() {}  
};  
  
int main() {  
   String^ delimStr = " ";  
   array<Char>^ delimiter = delimStr->ToCharArray( );  
   array<String^>^ args = Environment::CommandLine->Split( delimiter );  
  
// replace "self_reflection.exe" with an assembly from either the local  
// directory or the GAC  
   Assembly^ a = Assembly::LoadFrom("self_reflection.exe");  
   Console::WriteLine(a);  
  
   int count = 0;  
   array<Type^>^ types = a->GetTypes();  
   IEnumerator^ typeIter = types->GetEnumerator();  
  
   while ( typeIter->MoveNext() ) {  
      Type^ t = dynamic_cast<Type^>(typeIter->Current);  
      Console::WriteLine("   {0}", t->ToString());  
  
      array<MemberInfo^>^ members = t->GetMembers();  
      IEnumerator^ memberIter = members->GetEnumerator();  
      while ( memberIter->MoveNext() ) {  
         MemberInfo^ mi = dynamic_cast<MemberInfo^>(memberIter->Current);  
         Console::Write("      {0}", mi->ToString( ) );  
         if (mi->MemberType == MemberTypes::Constructor)  
            Console::Write("   (constructor)");  
  
         Console::WriteLine();  
      }  
      count++;  
   }  
   Console::WriteLine("{0} types found", count);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odbicie (C++/CLI)](../dotnet/reflection-cpp-cli.md)