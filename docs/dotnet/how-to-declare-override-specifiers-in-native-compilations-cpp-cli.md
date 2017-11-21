---
title: "Porady: deklarowanie specyfikatorów zastąpienia (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 07d612e97a6aaf3ff53116415b8eedc7324f78ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Porady: deklarowanie specyfikatorów przesłonięć w kompilacjach kodu natywnego (C++/CLI)
[zapieczętowane](../windows/sealed-cpp-component-extensions.md), [abstrakcyjny](../windows/abstract-cpp-component-extensions.md), i [zastąpienia](../windows/override-cpp-component-extensions.md) są dostępne w kompilacji, które nie używają **/ZW** lub [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
> [!NOTE]
>  ISO C ++ 11 standardowe języka [zastąpienia](../cpp/override-specifier.md) identyfikator i [końcowego](../cpp/final-specifier.md) identyfikator i obie są obsługiwane w Visual Studio użyj `final` zamiast `sealed` w kodzie, które mają na celu skompilowany, ponieważ wyłącznie natywnego.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie pokazano, że `sealed` jest prawidłowy w kompilacjach kodu natywnego.  
  
### <a name="code"></a>Kod  
  
```cpp  
// sealed_native_keyword.cpp  
#include <stdio.h>  
__interface I1 {  
   virtual void f();  
   virtual void g();  
};  
  
class X : public I1 {  
public:  
   virtual void g() sealed {}  
};  
  
class Y : public X {  
public:  
  
   // the following override generates a compiler error  
   virtual void g() {}   // C3248 X::g is sealed!  
};  
```  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W kolejnym przykładzie pokazano, że `override` jest prawidłowy w kompilacjach kodu natywnego.  
  
### <a name="code"></a>Kod  
  
```cpp  
// override_native_keyword.cpp  
#include <stdio.h>  
__interface I1 {  
   virtual void f();  
};  
  
class X : public I1 {  
public:  
   virtual void f() override {}   // OK  
   virtual void g() override {}   // C3668 I1::g does not exist  
};  
```  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W tym przykładzie pokazano, że `abstract` jest prawidłowy w kompilacjach kodu natywnego.  
  
### <a name="code"></a>Kod  
  
```cpp  
// abstract_native_keyword.cpp  
class X abstract {};  
  
int main() {  
   X * MyX = new X;   // C3622 cannot instantiate abstract class  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Specyfikatory zastąpienia](../windows/override-specifiers-cpp-component-extensions.md)