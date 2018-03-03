---
title: REF new, gcnew (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
dev_langs:
- C++
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 616117f7274d6f68456aa23614fb354a71982fb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ref-new-gcnew--c-component-extensions"></a>ref new, gcnew (C++ Component Extensions)
`ref new` Agregacji — słowo kluczowe przydziela wystąpienia typu, który jest bezużytecznych, gdy obiekt staje się niedostępny, i który zwraca uchwyt ([^](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)) do przydzielonego obiektu.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 Pamięć dla wystąpienia typu, który jest przydzielony przez `ref new` automatycznie cofnięciu przydziału.  
  
 A `ref new` zgłasza operacji `OutOfMemoryException` Jeśli nie można przydzielić pamięci.  
  
 Aby uzyskać więcej informacji dotyczących sposobu przydzielone i cofnięciu przydziału pamięci dla natywnych typów języka C++, zobacz [nowy i delete — operatory](../cpp/new-and-delete-operators.md).  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Użyj `ref new` można przydzielić pamięci dla obiektów środowiska wykonawczego systemu Windows, którego okres istnienia, którą chcesz administrować automatycznie. Obiekt jest automatycznie alokację jego liczebności referencyjnej systemowi na zero, co następuje po ostatniej kopii odwołania wykroczyła poza zakres. Aby uzyskać więcej informacji, zobacz [Ref klas i struktur](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 Jest przydzielana pamięć dla typu zarządzanego (odwołanie lub wartość typu), przez `gcnew`i alokację przy użyciu wyrzucanie elementów bezużytecznych.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 W poniższym przykładzie użyto `gcnew` można przydzielić obiektu komunikatu.  
  
```  
// mcppv2_gcnew_1.cpp  
// compile with: /clr  
ref struct Message {  
   System::String^ sender;  
   System::String^ receiver;  
   System::String^ data;  
};  
  
int main() {  
   Message^ h_Message  = gcnew Message;  
  //...  
}  
```  
  
 **Przykład**  
  
 W poniższym przykładzie użyto `gcnew` utworzyć opakowanym typem wartościowym do użycia, takie jak typ referencyjny.  
  
```  
// example2.cpp : main project file.  
// compile with /clr  
using namespace System;  
value class Boxed {  
    public:  
        int i;  
};  
int main()  
{  
    Boxed^ y = gcnew Boxed;  
    y->i = 32;  
    Console::WriteLine(y->i);  
    return 0;  
}  
```  
  
 **Output**  
  
```Output  
32  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)