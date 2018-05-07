---
title: Operator == (multiset) (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset::operator==
dev_langs:
- C++
helpviewer_keywords:
- operator== member [STL/CLR]
ms.assetid: 327918f8-ed9b-4549-a85e-11632757b317
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6a3e84e6cd17a7e7c037e6fa7549c43cd9fa2ab6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="operator-multiset-stlclr"></a>operator== (multiset) (STL/CLR)
Porównanie równy listy.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Key>  
    bool operator==(multiset<Key>% left,  
        multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Po lewej stronie kontenera do porównania.  
  
 w prawo  
 Kontener prawo do porównania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja operatora zwraca wartość true, tylko wtedy, gdy w sekwencji, które są kontrolowane przez `left` i `right` ma taką samą długość i dla każdej pozycji `i`, `left[i] ==` `right[i]`. Można go użyć do przetestowania czy `left` jest taka sama jak określona `right` po dwóch multisets są porównaniu elementu przez element.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_multiset_operator_eq.cpp   
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
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw wielokrotny (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Operator! = (multiset) (STL/CLR)](../dotnet/operator-inequality-multiset-stl-clr.md)   
 [operator\< (multiset) (STL/CLR)](../dotnet/operator-less-than-multiset-stl-clr.md)   
 [operator > = (multiset) (STL/CLR)](../dotnet/operator-greater-or-equal-multiset-stl-clr.md)   
 [operator > (multiset) (STL/CLR)](../dotnet/operator-greater-than-multiset-stl-clr.md)   
 [operator<= (multiset) (STL/CLR)](../dotnet/operator-less-or-equal-multiset-stl-clr.md)