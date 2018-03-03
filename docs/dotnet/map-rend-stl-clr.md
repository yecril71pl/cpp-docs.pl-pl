---
title: map::rend (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::map::rend
dev_langs:
- C++
helpviewer_keywords:
- rend member [STL/CLR]
ms.assetid: 132d9a82-f76a-4f3e-8d21-26de17e1245f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: eeafd4d7c6cf0fc6d79d17c462115297ad7cbc71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="maprend-stlclr"></a>map::rend (STL/CLR)
Określa koniec odwróconej kontrolowanej sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
reverse_iterator rend();  
```  
  
## <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca odwrotnej iteratora tego punktów poza początku kontrolowanej sekwencji. W związku z tym wyznacza `end` odwrotnej kolejności. Służy do uzyskania iterację wyznacza `current` koniec kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmieniać w przypadku zmiany długości kontrolowanej sekwencji.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_map_rend.cpp   
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
  
// inspect first two items in reversed sequence   
    Mymap::reverse_iterator rit = c1.rend();   
    --rit;   
    --rit;   
    System::Console::WriteLine("*-- --rend() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*--rend() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*-- --rend() = [b 2]  
*--rend() = [a 1]  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::BEGIN (STL/CLR)](../dotnet/map-begin-stl-clr.md)   
 [map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)   
 [map::rbegin (STL/CLR)](../dotnet/map-rbegin-stl-clr.md)