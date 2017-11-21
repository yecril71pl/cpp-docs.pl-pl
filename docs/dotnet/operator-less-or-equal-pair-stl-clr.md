---
title: operator&lt;= (para) (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::pair::operator<=
dev_langs: C++
helpviewer_keywords: operator<= member [STL/CLR]
ms.assetid: 94a4cc0a-cef4-4050-bd59-f826bd318e7b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 31fe33f274a60b3fba69fa7b800e5e2c6c92ce20
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="operatorlt-pair-stlclr"></a>operator&lt;= (para) (STL/CLR)
Sparuj mniejsza lub równa porównania.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator<=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Po lewej stronie para do porównania.  
  
 w prawo  
 Para prawo do porównania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja operatora `!(right < left)`. Można go użyć do przetestowania czy `left` porządkowania nie po `right` kiedy dwie pary są porównaniu elementu przez element.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_pair_operator_le.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] <= [x 3] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[x 4] <= [x 3] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] <= [x 3] is True  
[x 4] <= [x 3] is False  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/Narzędzia >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [para (STL/CLR)](../dotnet/pair-stl-clr.md)   
 [Operator == (para) (STL/CLR)](../dotnet/operator-equality-pair-stl-clr.md)   
 [Operator! = (para) (STL/CLR)](../dotnet/operator-inequality-pair-stl-clr.md)   
 [operator\< (para) (STL/CLR)](../dotnet/operator-less-than-pair-stl-clr.md)   
 [operator > = (para) (STL/CLR)](../dotnet/operator-greater-or-equal-pair-stl-clr.md)   
 [operator > (para) (STL/CLR)](../dotnet/operator-greater-than-pair-stl-clr.md)