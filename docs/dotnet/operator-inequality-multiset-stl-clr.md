---
title: Operator! = (multiset) (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multiset::operator!=
dev_langs: C++
helpviewer_keywords: operator!= member [STL/CLR]
ms.assetid: d4bad562-b58b-4578-94ab-0aa0e191b3ca
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ae63893f71352119147716893d3a1b2fc5496a2c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="operator-multiset-stlclr"></a>operator!= (multiset) (STL/CLR)
Lista równa porównania.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Key>  
    bool operator!=(multiset<Key>% left,  
        multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Po lewej stronie kontenera do porównania.  
  
 w prawo  
 Kontener prawo do porównania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja operatora `!(left == right)`. Można go użyć do przetestowania czy `left` nie jest taka sama jak określona `right` po dwóch multisets są porównaniu elementu przez element.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_multiset_operator_ne.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultiset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw wielokrotny (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Operator == (multiset) (STL/CLR)](../dotnet/operator-equality-multiset-stl-clr.md)   
 [operator\< (multiset) (STL/CLR)](../dotnet/operator-less-than-multiset-stl-clr.md)   
 [operator > = (multiset) (STL/CLR)](../dotnet/operator-greater-or-equal-multiset-stl-clr.md)   
 [operator > (multiset) (STL/CLR)](../dotnet/operator-greater-than-multiset-stl-clr.md)   
 [Operator < = (multiset) (STL/CLR)](../dotnet/operator-less-or-equal-multiset-stl-clr.md)