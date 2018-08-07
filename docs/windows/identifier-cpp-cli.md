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
ms.openlocfilehash: 6eac892da91c5f3640bdd243a0b3c6525faa5c2a
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603348"
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)
Umożliwia korzystanie z Visual C++ słów kluczowych jako identyfikatorów.  
  
## <a name="all-platforms"></a>Wszystkie platformy  
### <a name="syntax"></a>Składnia  
  
```  
__identifier(  
Visual_C++_keyword  
)  
```  
  
### <a name="remarks"></a>Uwagi  
  
Korzystanie z **__identifier** — słowo kluczowe dla identyfikatorów, które nie są słowami kluczowymi jest dozwolone, ale zdecydowanie niezalecane jako stylu.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: `/ZW`  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 W poniższym przykładzie klasę o nazwie `template` jest tworzone w języku C# i dystrybuowanych jako biblioteki DLL. W programie Visual C++, który używa `template` klasy **__identifier** — słowo kluczowe zawiera fakt, **szablonu** jest standardowa słowa kluczowego języka C++.  
  
```cs  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```cpp  
// keyword__identifier.cpp  
// compile with: /ZW  
#using <identifier_template.dll>  
int main() {  
   __identifier(template)^ pTemplate = ref new __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
### <a name="remarks"></a>Uwagi  
  
 **__Identifier** — słowo kluczowe jest prawidłowa w przypadku `/clr` — opcja kompilatora.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: `/clr`  
  
### <a name="examples"></a>Przykłady  
  
 W poniższym przykładzie klasę o nazwie `template` jest tworzone w języku C# i dystrybuowanych jako biblioteki DLL. W programie Visual C++, który używa `template` klasy **__identifier** — słowo kluczowe zawiera fakt, **szablonu** jest standardowa słowa kluczowego języka C++.  
  
```cs  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```cpp  
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