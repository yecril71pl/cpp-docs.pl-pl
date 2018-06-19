---
title: Problemy z wersją w przypadku typów wartości zagnieżdżonych w typach natywnych (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __nogc type declarations
- __value keyword, issues when nesting
ms.assetid: 0a3b1a43-39c6-4b52-be2f-1074690188aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4c4f2598594930f49c1217c937c9142b3f84a47e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168844"
---
# <a name="version-issues-for-value-types-nested-in-native-types-ccli"></a>Problemy z wersją w przypadku typów wartości zagnieżdżonych w typach natywnych (C++/CLI)
Należy wziąć pod uwagę składnika zestawu podpisem (silnej nazwy), używany do tworzenia zestawu klienta. Składnik zawiera typ wartości, który jest używany w kliencie jako typ elementu Członkowskiego Unii macierzystego, klasy lub tablicy. W przypadku przyszłych wersji składnika zmiany rozmiaru lub układ typu wartości, klient musi ponownie kompilowana.  
  
 Utwórz keyfile z [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) (`sn -k mykey.snk`).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest składnikiem.  
  
```  
// nested_value_types.cpp  
// compile with: /clr /LD  
using namespace System::Reflection;  
[assembly:AssemblyVersion("1.0.0.*"),   
assembly:AssemblyKeyFile("mykey.snk")];  
  
public value struct S {  
   int i;  
   void Test() {  
      System::Console::WriteLine("S.i = {0}", i);  
   }  
};  
```  
  
## <a name="example"></a>Przykład  
 Ten przykład jest klienta:  
  
```  
// nested_value_types_2.cpp  
// compile with: /clr  
#using <nested_value_types.dll>  
  
struct S2 {  
   S MyS1, MyS2;  
};  
  
int main() {  
   S2 MyS2a, MyS2b;  
   MyS2a.MyS1.i = 5;  
   MyS2a.MyS2.i = 6;  
   MyS2b.MyS1.i = 10;  
   MyS2b.MyS2.i = 11;  
  
   MyS2a.MyS1.Test();  
   MyS2a.MyS2.Test();  
   MyS2b.MyS1.Test();  
   MyS2b.MyS2.Test();  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
S.i = 5  
S.i = 6  
S.i = 10  
S.i = 11  
```  
  
### <a name="comments"></a>Komentarze  
 Jednak jeśli dodasz innego członka do `struct S` w nested_value_types.cpp, (na przykład `double d;`) i skompiluj ponownie składnik bez konieczności ponownego kompilowania klienta, wynikiem jest nieobsługiwany wyjątek (typu <xref:System.IO.FileLoadException?displayProperty=fullName>).  
  
## <a name="see-also"></a>Zobacz też  
 [Typy zarządzane (C++/CLI)](../dotnet/managed-types-cpp-cli.md)