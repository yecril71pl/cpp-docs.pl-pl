---
title: override (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6818256aafc64702e5423a5560c251e6d46750fa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878882"
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