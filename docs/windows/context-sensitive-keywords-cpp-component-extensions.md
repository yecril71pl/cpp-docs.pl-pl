---
title: Kontekstowe słowa kluczowe (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal_CPP
dev_langs:
- C++
helpviewer_keywords:
- context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ceea3242087d89b511f6309003efe38d155735d2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871526"
---
# <a name="context-sensitive-keywords--c-component-extensions"></a>Kontekstowe słowa kluczowe (C++ Component Extensions)
*Kontekstowe słowa kluczowe* są elementy języka, które są rozpoznawane tylko w określonych kontekstach. Poza określonym kontekście kontekstowa — słowo kluczowe może być symbol zdefiniowany przez użytkownika.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 **Uwagi**  
  
 Poniżej przedstawiono listę kontekstowe słowa kluczowe:  
  
-   [abstract](../windows/abstract-cpp-component-extensions.md)  
  
-   [delegate](../windows/delegate-cpp-component-extensions.md)  
  
-   [event](../windows/event-cpp-component-extensions.md)  
  
-   [finally](../dotnet/finally.md)  
  
-   [for each, in](../dotnet/for-each-in.md)  
  
-   [InitOnly](../dotnet/initonly-cpp-cli.md)  
  
-   `internal`   
  
-   [Literału](../windows/literal-cpp-component-extensions.md)  
  
-   [override](../windows/override-cpp-component-extensions.md)  
  
-   [właściwość](../windows/property-cpp-component-extensions.md)  
  
-   [sealed](../windows/sealed-cpp-component-extensions.md)  
  
-   `where` (część [ogólne](../windows/generics-cpp-component-extensions.md))  
  
 Do celów czytelność można ograniczyć korzystanie z kontekstowe słowa kluczowe jako symbole zdefiniowane przez użytkownika.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 **Uwagi**  
  
 (Istnieją nie uwagi specyficzne dla platformy, dla tej funkcji.)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 **Uwagi**  
  
 (Istnieją nie uwagi specyficzne dla platformy, dla tej funkcji.)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 W poniższym przykładzie pokazano, że w kontekście odpowiednie `property` kontekstowa — słowo kluczowe może służyć do definiowania właściwości oraz zmienna.  
  
```  
// context_sensitive_keywords.cpp  
// compile with: /clr  
public ref class C {  
   int MyInt;  
public:  
   C() : MyInt(99) {}  
  
   property int Property_Block {   // context-sensitive keyword  
      int get() { return MyInt; }  
   }  
};  
  
int main() {  
   int property = 0;               // variable name  
   C ^ MyC = gcnew C();  
   property = MyC->Property_Block;  
   System::Console::WriteLine(++property);  
}  
```  
  
 **Output**  
  
```Output  
100  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)