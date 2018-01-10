---
title: hash_multiset::rend (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_multiset::rend
dev_langs: C++
helpviewer_keywords: rend member [STL/CLR]
ms.assetid: 6d007ac9-18cc-4b51-8384-a4ff65d23e97
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 141ba7547749e4a3ca3edfb82b9f5cfcfe8c0d8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hashmultisetrend-stlclr"></a>hash_multiset::rend (STL/CLR)
Określa koniec odwróconej kontrolowanej sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
reverse_iterator rend();  
```  
  
## <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca odwrotnej iteratora tego punktów poza początku kontrolowanej sekwencji. W związku z tym wyznacza `end` odwrotnej kolejności. Służy do uzyskania iterację wyznacza `current` koniec kontrolowanej sekwencji występuje w odwrotnej kolejności, ale jej stan można zmieniać w przypadku zmiany długości kontrolowanej sekwencji.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_hash_multiset_rend.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myhash_multiset::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [hash_multiset — (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::BEGIN (STL/CLR)](../dotnet/hash-multiset-begin-stl-clr.md)   
 [hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)   
 [hash_multiset::rbegin (STL/CLR)](../dotnet/hash-multiset-rbegin-stl-clr.md)