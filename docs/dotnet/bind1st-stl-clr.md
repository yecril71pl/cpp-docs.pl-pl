---
title: "bind1st — (STL/CLR) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::bind1st
dev_langs: C++
helpviewer_keywords: bind1st function [STL/CLR]
ms.assetid: 03a04cef-60fb-4667-b22a-22a387adb028
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 732238e3c0754731dcf7caf10ad1d6a140490cd0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="bind1st-stlclr"></a>bind1st (STL/CLR)
Generuje `binder1st` argumentu i obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Fun,  
    typename Arg>  
    binder1st<Fun> bind1st(Fun% functor,  
        Arg left);  
```  
  
## <a name="template-parameters"></a>Parametry szablonu  
 ARG  
 Typ argumentu.  
  
 Fun  
 Typ obiekt.  
  
## <a name="function-parameters"></a>Parametry funkcji  
 obiekt  
 Obiekt do zakodowania.  
  
 left  
 Pierwszy argument do zakodowania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja szablonu [binder1st — (STL/CLR)](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`. Możesz używać go jako wygodny sposób zawijanie obiekt dwa argumentu i jego pierwszy argument w obiekt jeden argument, który odwołuje się on z drugiego argumentu.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_bind1st.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        subfrom3);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind1st(sub_op, 3));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
-1 0  
-1 0  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/funkcjonalności >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [binder1st — (STL/CLR)](../dotnet/binder1st-stl-clr.md)