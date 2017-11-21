---
title: map::equal_range (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map::equal_range
dev_langs: C++
helpviewer_keywords: equal_range member [STL/CLR]
ms.assetid: c0d7409c-344d-4102-99c4-aeab8643a073
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 13500bbd5842460dff5cf071bd626555bf1c5cc9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mapequalrange-stlclr"></a>map::equal_range (STL/CLR)
Wyszukuje zakres, który odpowiada określonemu kluczowi.  
  
## <a name="syntax"></a>Składnia  
  
```  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 klawisz  
 Wartość klucza do wyszukania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca parę Iteratory `cliext::pair<iterator, iterator>(` [map::lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md) `(key),` [map::upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)`(key))`. Można użyć do określenia zakresu elementów aktualnie w kontrolowanej sekwencji zgodne z określonym kluczem.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_map_equal_range.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef Mymap::pair_iter_iter Pairii;   
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
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" [{0} {1}]",   
            pair1.first->first, pair1.first->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
equal_range(L'x') empty = True  
 [b 2]  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::Count (STL/CLR)](../dotnet/map-count-stl-clr.md)   
 [map::Find (STL/CLR)](../dotnet/map-find-stl-clr.md)   
 [map::lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md)   
 [map::upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)