---
title: __identifier (c + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
dev_langs:
- C++
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a96363fcfbc753e727c6cbb6a5efbbb5606b6c40
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)
Umożliwia użycie słowa kluczowe języka Visual C++, identyfikatory.  
  
## <a name="all-platforms"></a>Wszystkie platformy  
**Składnia**  
  
```  
__identifier(  
Visual_C++_keyword  
)  
  
```  
  
**Uwagi**  
  
Użycie `__identifier` — słowo kluczowe dla identyfikatorów, które nie są słów kluczowych jest dozwolone, ale zdecydowanie odradzane jako styl.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 W poniższym przykładzie klasa o nazwie `template` jest utworzony w języku C# i jest dystrybuowany jako biblioteki DLL. W programie Visual C++, która używa `template` klasy `__identifier` — słowo kluczowe zawiera fakt który `template` jest standardowe słowa kluczowego języka C++.  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /ZW  
#using <identifier_template.dll>  
int main() {  
   __identifier(template)^ pTemplate = ref new __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 **Uwagi**  
  
 `__identifier` — Słowo kluczowe jest prawidłowy dla **/CLR** — opcja kompilatora.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 W poniższym przykładzie klasa o nazwie `template` jest utworzony w języku C# i jest dystrybuowany jako biblioteki DLL. W programie Visual C++, która używa `template` klasy `__identifier` — słowo kluczowe zawiera fakt który `template` jest standardowe słowa kluczowego języka C++.  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /clr  
#using <identifier_template.dll>  
  
int main() {  
   __identifier(template) ^pTemplate = gcnew __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)   
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)