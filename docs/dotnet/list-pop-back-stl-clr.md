---
title: list::pop_back (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::pop_back
dev_langs: C++
helpviewer_keywords: pop_back member [STL/CLR]
ms.assetid: 03fe8e0e-461b-41c4-8e20-97d0d4ed0feb
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c3e0cd3f7bb23b61f5b394b4871c3dca990cf800
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="listpopback-stlclr"></a>list::pop_back (STL/CLR)
Usuwa ostatnim elemencie.  
  
## <a name="syntax"></a>Składnia  
  
```  
void pop_back();  
```  
  
## <a name="remarks"></a>Uwagi  
 Funkcja członkowska usuwa ostatniego elementu w kontrolowanej sekwencji musi być niepusta. Umożliwia ona skrócić czas na liście przez jeden element z tyłu.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_list_pop_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_back();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/listy >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::pop_front (STL/CLR)](../dotnet/list-pop-front-stl-clr.md)   
 [list::push_back (STL/CLR)](../dotnet/list-push-back-stl-clr.md)   
 [list::push_front (STL/CLR)](../dotnet/list-push-front-stl-clr.md)