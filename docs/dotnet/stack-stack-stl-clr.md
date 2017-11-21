---
title: Stack::Stack (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stack::stack
dev_langs: C++
helpviewer_keywords: stack member [STL/CLR]
ms.assetid: f1cfb3fe-4d22-41e5-906b-e8faa0bcde9b
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e12c704561cd56ac251479861740c7df205f1e37
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="stackstack-stlclr"></a>stack::stack (STL/CLR)
Tworzy obiekt Karta kontenera.  
  
## <a name="syntax"></a>Składnia  
  
```  
stack();  
stack(stack<Value, Container>% right);  
stack(stack<Value, Container>^ right);  
explicit stack(container_type% wrapped);  
```  
  
#### <a name="parameters"></a>Parametry  
 w prawo  
 Obiekt przeznaczony do skopiowania.  
  
 opakowana  
 Opakowana kontener do użycia.  
  
## <a name="remarks"></a>Uwagi  
 Konstruktor:  
  
 `stack();`  
  
 tworzy pusty kontener opakowana. Umożliwia ona Określ pusty początkowej kontrolowanej sekwencji.  
  
 Konstruktor:  
  
 `stack(stack<Value, Container>% right);`  
  
 Tworzy opakowana kontener, który jest kopią `right.get_container()`. Należy użyć do określenia początkowej kontrolowanej sekwencji, który jest kopią sekwencji kontrolowane przez obiekt stosu `right`.  
  
 Konstruktor:  
  
 `stack(stack<Value, Container>^ right);`  
  
 Tworzy opakowana kontener, który jest kopią `right->get_container()`. Należy użyć do określenia początkowej kontrolowanej sekwencji, który jest kopią sekwencji kontrolowane przez obiekt stosu `*right`.  
  
 Konstruktor:  
  
 `explicit stack(container_type% wrapped);`  
  
 używa istniejącego kontenera `wrapped` jako kontener opakowana. Można użyć do utworzenia stosu z istniejącego kontenera.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_stack_construct.cpp   
// compile with: /clr   
#include <cliext/stack>   
#include <cliext/vector>   
  
typedef cliext::stack<wchar_t> Mystack;   
typedef cliext::vector<wchar_t> Myvector;   
typedef cliext::stack<wchar_t, Myvector> Mystack_vec;   
int main()   
    {   
// construct an empty container   
    Mystack c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct from an underlying container   
    Myvector v2(5, L'x');   
    Mystack_vec c2(v2);       
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mystack_vec c3(c2);   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container through handle   
    Mystack_vec c4(%c2);   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 x x x x x  
 x x x x x  
 x x x x x  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/stack >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [stos (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [Stack::ASSIGN (STL/CLR)](../dotnet/stack-assign-stl-clr.md)   
 [Stack::generic_container (STL/CLR)](../dotnet/stack-generic-container-stl-clr.md)   
 [Stack::operator = (STL/CLR)](../dotnet/stack-operator-assign-stl-clr.md)