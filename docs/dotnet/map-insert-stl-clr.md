---
title: map::INSERT (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: 599c702e-7db0-45b8-8247-4ff041a3639c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a06fa94e9752d72e8743d3a360ffd81bc9322db1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mapinsert-stlclr"></a>map::insert (STL/CLR)
Dodaje elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
cliext::pair<iterator, bool> insert(value_type val);  
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
  
 Pierwszy funkcji członkowskiej usiłują Wstaw element z wartością `val`i zwraca pary wartości `X`. Jeśli `X.second` ma wartość true, `X.first` wyznacza nowo wstawionej elementu; w przeciwnym razie `X.first` wskazuje element z równoważne porządkowania, która już istnieje i jest wstawiany nie nowego elementu. Umożliwia ona wstawić jeden element.  
  
 Drugi funkcji członkowskiej wstawia element z wartością `val`za pomocą `where` jako wskazówkę (Aby poprawić wydajność) i zwraca iterację wyznacza nowo wstawiony element. Umożliwia ona pojedynczy element, który może być obok elementu, który znasz Wstaw.  
  
 Trzeci funkcji członkowskiej wstawia sekwencji [`first`, `last`). Umożliwia ona Wstawianie zero lub więcej elementów skopiowanych z innej sekwencji.  
  
 Czwarty funkcji członkowskiej wstawia sekwencji wskazywany przez `right`. Umożliwia ona Wstaw sekwencję opisanego przez moduł wyliczający.  
  
 Każdy element wstawiania czas proporcjonalna do logarytmu liczba elementów w kontrolowanej sekwencji. Wstawiania może występować w amortyzowanego stałej czasu jednak podane wskazówki, który wskazuje element sąsiadujące punkt wstawiania.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_map_insert.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef Mymap::pair_iter_bool Pairib;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
// insert a single value, success and failure   
    Pairib pair1 = c1.insert(Mymap::make_value(L'x', 24));   
    System::Console::WriteLine("insert([L'x' 24]) = [[{0} {1}] {2}]",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    pair1 = c1.insert(Mymap::make_value(L'b', 2));   
    System::Console::WriteLine("insert([L'b' 2]) = [[{0} {1}] {2}]",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    Mymap::iterator it =   
        c1.insert(c1.begin(), Mymap::make_value(L'y', 25));   
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",   
        it->first, it->second);   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Mymap c2;   
    it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Mymap c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::   
            IEnumerable<Mymap::value_type>^)%c1);   
    for each (Mymap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
insert([L'x' 24]) = [[x 24] True]  
insert([L'b' 2]) = [[b 2] False]  
 [a 1] [b 2] [c 3] [x 24]  
insert(begin(), [L'y' 25]) = [y 25]  
 [a 1] [b 2] [c 3] [x 24] [y 25]  
 [a 1] [b 2] [c 3] [x 24]  
 [a 1] [b 2] [c 3] [x 24] [y 25]  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [map (STL/CLR)](../dotnet/map-stl-clr.md)