---
title: map::Find (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map::find
dev_langs: C++
helpviewer_keywords: find member [STL/CLR]
ms.assetid: 779dcbee-d584-4fbd-b788-481e094ece9d
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 805ddfc8e2e8194df38703011a90c62d96475ddd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mapfind-stlclr"></a>map::find (STL/CLR)
Wyszukuje element, który odpowiada określonemu kluczowi.  
  
## <a name="syntax"></a>Składnia  
  
```  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 klawisz  
 Wartość klucza do wyszukania.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli co najmniej jednego elementu w kontrolowanej sekwencji ma porządkowanie równoważne z `key`, funkcją członkowską zwracającą iterator wyznaczenie jednego z tych elementów; w przeciwnym razie zwraca [map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`. Umożliwia ona obecnie zlokalizować elementu w kontrolowanej sekwencji zgodny z określonym kluczem.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_map_find.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
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
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
  
    Mymap::iterator it = c1.find(L'b');   
    System::Console::WriteLine("find {0} = [{1} {2}]",   
        L'b', it->first, it->second);   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
find A = False  
find b = [b 2]  
find C = False  
```  
  
## <a name="description"></a>Opis  
 Należy pamiętać, że `find` nie gwarantuje, którego element kilka znajdzie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::equal_range (STL/CLR)](../dotnet/map-equal-range-stl-clr.md)   
 [map::lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md)   
 [map::upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)