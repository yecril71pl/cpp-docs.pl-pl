---
title: operator&gt;= (wektor) (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::operator>=
dev_langs: C++
helpviewer_keywords: operator>= member [STL/CLR]
ms.assetid: c06f4489-f65a-4bd6-944f-9b23a2bb4e35
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 75412a0336a498d20830d4a910a7be9a9d819594
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="operatorgt-vector-stlclr"></a>operator&gt;= (wektor) (STL/CLR)
Wektor większe lub równe porównania.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Value>  
    bool operator>=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Po lewej stronie kontenera do porównania.  
  
 w prawo  
 Kontener prawo do porównania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja operatora `!(left < right)`. Można go użyć do przetestowania czy `left` nie jest umieszczane przed `right` kiedy dwa wektory są porównaniu elementu przez element.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_vector_operator_ge.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/wektor >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Wektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Operator == (wektor) (STL/CLR)](../dotnet/operator-equality-vector-stl-clr.md)   
 [Operator! = (wektor) (STL/CLR)](../dotnet/operator-inequality-vector-stl-clr.md)   
 [operator\< (wektor) (STL/CLR)](../dotnet/operator-less-than-vector-stl-clr.md)   
 [operator > (wektor) (STL/CLR)](../dotnet/operator-greater-than-vector-stl-clr.md)   
 [operator<= (vector) (STL/CLR)](../dotnet/operator-less-or-equal-vector-stl-clr.md)