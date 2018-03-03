---
title: operator&gt;= (para) (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::pair::operator>=
dev_langs:
- C++
helpviewer_keywords:
- operator>= member [STL/CLR]
ms.assetid: dcc2decf-3b2b-495d-9fd5-3daba27d5096
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 196b2a16a5720b8d4862fafdf78f6d9768e3ffeb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="operatorgt-pair-stlclr"></a>operator&gt;= (para) (STL/CLR)
Para większa niż lub równe porównania.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator>=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Po lewej stronie para do porównania.  
  
 w prawo  
 Para prawo do porównania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja operatora `!(left < right)`. Można go użyć do przetestowania czy `left` nie jest umieszczane przed `right` kiedy dwie pary są porównaniu elementu przez element.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_pair_operator_ge.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] >= [x 3] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[x 3] >= [x 4] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] >= [x 3] is True  
[x 3] >= [x 4] is False  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/Narzędzia >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [para (STL/CLR)](../dotnet/pair-stl-clr.md)   
 [Operator == (para) (STL/CLR)](../dotnet/operator-equality-pair-stl-clr.md)   
 [Operator! = (para) (STL/CLR)](../dotnet/operator-inequality-pair-stl-clr.md)   
 [operator\< (para) (STL/CLR)](../dotnet/operator-less-than-pair-stl-clr.md)   
 [operator > (para) (STL/CLR)](../dotnet/operator-greater-than-pair-stl-clr.md)   
 [operator<= (pair) (STL/CLR)](../dotnet/operator-less-or-equal-pair-stl-clr.md)