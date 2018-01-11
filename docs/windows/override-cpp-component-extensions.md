---
title: override (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88138001a9767bbe9752c1de0577910fca8bc914
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="override--c-component-extensions"></a>override (C++ Component Extensions)
`override` Kontekstowa — słowo kluczowe wskazuje, że element członkowski typu zastępuje klasy podstawowej lub elementem członkowskim interfejs podstawowy.  
  
## <a name="remarks"></a>Uwagi  
 `override` — Słowo kluczowe jest prawidłowa w przypadku kompilowania kodu natywnego obiektów docelowych (opcja kompilatora domyślna), elementy docelowe środowiska wykonawczego systemu Windows (**/ZW** — opcja kompilatora), lub wspólne elementy docelowe środowisko uruchomieniowe języka (**/CLR** kompilatora Opcja).  
  
 Aby uzyskać więcej informacji na temat specyfikatorów zastąpienia, zobacz [specyfikator przesłonięcia](../cpp/override-specifier.md) i [specyfikatory Override i kompilacjach macierzystych](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
 Aby uzyskać więcej informacji na temat kontekstowe słowa kluczowe, zobacz [słowa kluczowe Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
## <a name="examples"></a>Przykłady  
 **Przykład**  
  
 W poniższym przykładzie pokazano, że `override` można również w kompilacjach kodu natywnego.  
  
```cpp#  
// override_keyword_1.cpp  
// compile with: /c  
struct I1 {  
   virtual void f();  
};  
  
struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Przykład**  
  
 W poniższym przykładzie pokazano, że `override` mogą być używane w kompilacjach środowiska wykonawczego systemu Windows.  
  
```cpp#  
// override_keyword_2.cpp  
// compile with: /ZW /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Wymagania**  
  
 — Opcja kompilatora: **/ZW**  
  
 **Przykład**  
  
 W poniższym przykładzie pokazano, że `override` mogą być używane w typowych kompilacje środowiska uruchomieniowego języka.  
  
```cpp#  
// override_keyword_3.cpp  
// compile with: /clr /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Wymagania**  
  
 — Opcja kompilatora:   **/CLR**  
  
## <a name="see-also"></a>Zobacz też  
 [override, Specyfikator](../cpp/override-specifier.md)   
 [Specyfikatory zastąpienia](../windows/override-specifiers-cpp-component-extensions.md)