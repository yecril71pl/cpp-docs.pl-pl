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
ms.openlocfilehash: e362ec513cb7cb14f5fd3abb8a028c6e0eab616b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644232"
---
# <a name="context-sensitive-keywords--c-component-extensions"></a>Kontekstowe słowa kluczowe (C++ Component Extensions)
*Kontekstowe słowa kluczowe* są elementami języka, które są rozpoznawane tylko w określonych kontekstach. Poza określonym kontekstem kontekstowe słowo kluczowe może być symbolem zdefiniowanych przez użytkownika.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
### <a name="remarks"></a>Uwagi
  
 Oto lista kontekstowych słów kluczowych:  
  
-   [abstract](../windows/abstract-cpp-component-extensions.md)  
  
-   [delegate](../windows/delegate-cpp-component-extensions.md)  
  
-   [event](../windows/event-cpp-component-extensions.md)  
  
-   [finally](../dotnet/finally.md)  
  
-   [for each, in](../dotnet/for-each-in.md)  
  
-   [InitOnly](../dotnet/initonly-cpp-cli.md)  
  
-   `internal`   
  
-   [literał](../windows/literal-cpp-component-extensions.md)  
  
-   [override](../windows/override-cpp-component-extensions.md)  
  
-   [właściwość](../windows/property-cpp-component-extensions.md)  
  
-   [sealed](../windows/sealed-cpp-component-extensions.md)  
  
-   `where` (część [ogólne](../windows/generics-cpp-component-extensions.md))  
  
 Dla potrzeb czytelności warto ograniczyć korzystanie z kontekstowych słów kluczowych jako symboli zdefiniowanych przez użytkownika.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
### <a name="remarks"></a>Uwagi  
  
 (Nie ma żadnych uwag specyficznych dla platformy, dla tej funkcji).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: `/ZW`  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
### <a name="remarks"></a>Uwagi  
  
 (Nie ma żadnych uwag specyficznych dla platformy, dla tej funkcji).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: `/clr`  
  
### <a name="examples"></a>Przykłady  
  
 Poniższy przykład kodu pokazuje, że w odpowiedniego kontekstu **właściwość** kontekstowe słowo kluczowe może służyć do definiowania właściwości i zmiennej.  
  
```cpp  
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
  
```Output  
100  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)