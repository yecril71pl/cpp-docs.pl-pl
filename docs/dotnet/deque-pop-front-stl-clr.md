---
title: deque::pop_front (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque::pop_front
dev_langs: C++
helpviewer_keywords: pop_front member [STL/CLR]
ms.assetid: 5042df47-b226-4b16-982e-6a4543b8e00b
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4a6eab42a6fe3880c3c76f537f3c39b9e663a4f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dequepopfront-stlclr"></a>deque::pop_front (STL/CLR)
Usuwa pierwszego elementu.  
  
## <a name="syntax"></a>Składnia  
  
```  
void pop_front();  
```  
  
## <a name="remarks"></a>Uwagi  
 Funkcja członkowska usuwa pierwszego elementu obiektu kontrolowanej sekwencji musi być niepusta. Umożliwia ona skrócić czas deque — przez element jednego z przodu.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_deque_pop_front.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_front();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
b c  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/deque — >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [deque — (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::pop_back (STL/CLR)](../dotnet/deque-pop-back-stl-clr.md)   
 [deque::push_back (STL/CLR)](../dotnet/deque-push-back-stl-clr.md)   
 [deque::push_front (STL/CLR)](../dotnet/deque-push-front-stl-clr.md)