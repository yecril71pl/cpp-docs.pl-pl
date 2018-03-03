---
title: multimap::INSERT (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::multimap::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: 98922ea1-c7ed-4c53-8834-8a0470b11c9e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7ea2f027fb6b8133e4830adbb80e7db5ce0b1d8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="multimapinsert-stlclr"></a>multimap::insert (STL/CLR)
Dodaje elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
iterator insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 pierwszy  
 Początek zakresu do wstawienia.  
  
 ostatni  
 Koniec zakresu do wstawienia.  
  
 w prawo  
 Wyliczenie do wstawienia.  
  
 Val  
 Wartość klucza do wstawienia.  
  
 gdzie  
 Gdzie w kontenerze, aby wstawić (tylko wskazówka).  
  
## <a name="remarks"></a>Uwagi  
 Każda z funkcji Członkowskich wstawia sekwencję określony przez pozostałych argumentów operacji.  
  
 Pierwszy funkcji członkowskiej wstawia element z wartością `val`i zwraca iterację wyznacza nowo wstawiony element. Umożliwia ona wstawić jeden element.  
  
 Drugi funkcji członkowskiej wstawia element z wartością `val`za pomocą `where` jako wskazówkę (Aby poprawić wydajność) i zwraca iterację wyznacza nowo wstawiony element. Umożliwia ona pojedynczy element, który może być obok elementu, który znasz Wstaw.  
  
 Trzeci funkcji członkowskiej wstawia sekwencji [`first`, `last`). Umożliwia ona Wstawianie zero lub więcej elementów skopiowanych z innej sekwencji.  
  
 Czwarty funkcji członkowskiej wstawia sekwencji wskazywany przez `right`. Umożliwia ona Wstaw sekwencję opisanego przez moduł wyliczający.  
  
 Każdy element wstawiania czas proporcjonalna do logarytmu liczba elementów w kontrolowanej sekwencji. Wstawiania może występować w amortyzowanego stałej czasu jednak podane wskazówki, który wskazuje element sąsiadujące punkt wstawiania.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_multimap_insert.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    Mymultimap::iterator it =   
        c1.insert(Mymultimap::make_value(L'x', 24));   
    System::Console::WriteLine("insert([L'x' 24]) = [{0} {1}]",   
        it->first, it->second);   
  
    it = c1.insert(Mymultimap::make_value(L'b', 2));   
    System::Console::WriteLine("insert([L'b' 2]) = [{0} {1}]",   
        it->first, it->second);   
  
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    it = c1.insert(c1.begin(), Mymultimap::make_value(L'y', 25));   
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",   
        it->first, it->second);   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Mymultimap c2;   
    it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (Mymultimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Mymultimap c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::   
            IEnumerable<Mymultimap::value_type>^)%c1);   
    for each (Mymultimap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
insert([L'x' 24]) = [x 24]  
insert([L'b' 2]) = [b 2]  
 [a 1] [b 2] [b 2] [c 3] [x 24]  
insert(begin(), [L'y' 25]) = [y 25]  
 [a 1] [b 2] [b 2] [c 3] [x 24] [y 25]  
 [a 1] [b 2] [b 2] [c 3] [x 24]  
 [a 1] [b 2] [b 2] [c 3] [x 24] [y 25]  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)