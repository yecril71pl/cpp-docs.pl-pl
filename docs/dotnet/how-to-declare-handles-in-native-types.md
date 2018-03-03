---
title: "Porady: deklarowanie dojść w typach natywnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- gcroot
dev_langs:
- C++
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 097889acd9a77cea5e0a81dd3bd13be712a70550
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-declare-handles-in-native-types"></a>Porady: deklarowanie dojść w typach natywnych
Nie można zadeklarować typu uchwytu w typie natywnym. vcclr.h zapewnia bezpieczny otoki szablonu `gcroot` w odwołaniu do obiektu CLR ze stosu C++. Ten szablon umożliwia osadzanie dojścia wirtualnego w typie natywnym i traktować go tak, jakby była typu bazowego. W większości przypadków można użyć `gcroot` jako osadzony typ bez żadnych rzutowania. Jednak w przypadku [dla poszczególnych usług, w](../dotnet/for-each-in.md), należy użyć `static_cast` można pobrać odwołanie do podstawowej zarządzanych.  
  
 `gcroot` Szablonu jest implementowane za pomocą funkcji klasy wartości System::Runtime::InteropServices::GCHandle, która zapewnia "dojść" do stosu zebranego przez pamięci. Należy pamiętać, że uchwyty siebie nie są bezużytecznych i są zwalniane nie jest już w użyciu przez destruktor w `gcroot` klasy (ten destruktor nie można wywołać ręcznie). Jeśli można utworzyć wystąpienia `gcroot` obiektów na stercie natywnej, należy wywołać usunąć tego zasobu.  
  
 Środowisko uruchomieniowe zachowa skojarzenie dojście obiektu CLR, która odwołuje się. Jeśli obiektu CLR jest przenoszony z zebranych pamięci sterty, dojście zwróci adresu nowego obiektu. Zmienna nie trzeba przypięty przed jest przypisany do `gcroot` szablonu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób tworzenia `gcroot` obiektu na stosie macierzystego.  
  
```  
// mcpp_gcroot.cpp  
// compile with: /clr  
#include <vcclr.h>  
using namespace System;  
  
class CppClass {  
public:  
   gcroot<String^> str;   // can use str as if it were String^  
   CppClass() {}  
};  
  
int main() {  
   CppClass c;  
   c.str = gcnew String("hello");  
   Console::WriteLine( c.str );   // no cast required  
}  
```  
  
```Output  
hello  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób tworzenia `gcroot` w stercie natywnej obiektu.  
  
```  
// mcpp_gcroot_2.cpp  
// compile with: /clr  
// compile with: /clr  
#include <vcclr.h>  
using namespace System;  
  
struct CppClass {  
   gcroot<String ^> * str;  
   CppClass() : str(new gcroot<String ^>) {}  
  
   ~CppClass() { delete str; }  
  
};  
  
int main() {  
   CppClass c;  
   *c.str = gcnew String("hello");  
   Console::WriteLine( *c.str );  
}  
```  
  
```Output  
hello  
```  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia sposób użycia `gcroot` do przechowywania odwołań do typów wartości (nie typy referencyjne) w polu typu natywnego przy użyciu `gcroot` na typ opakowany.  
  
```  
// mcpp_gcroot_3.cpp  
// compile with: /clr  
#include < vcclr.h >  
using namespace System;  
  
public value struct V {  
   String^ str;  
};  
  
class Native {  
public:  
   gcroot< V^ > v_handle;  
};  
  
int main() {  
   Native native;  
   V v;  
   native.v_handle = v;  
   native.v_handle->str = "Hello";  
   Console::WriteLine("String in V: {0}", native.v_handle->str);  
}  
```  
  
```Output  
String in V: Hello  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)