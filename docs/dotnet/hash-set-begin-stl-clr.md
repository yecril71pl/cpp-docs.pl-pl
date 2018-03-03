---
title: hash_set::BEGIN (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::hash_set::begin
dev_langs:
- C++
helpviewer_keywords:
- begin member [STL/CLR]
ms.assetid: 1bd02b6b-0e24-4f42-ad13-fd7776f7f811
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dcd2f8d4c414ea613d7728a32ce899cae78e7e51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hashsetbegin-stlclr"></a>hash_set::begin (STL/CLR)
Określa początek kontrolowanej sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
iterator begin();  
```  
  
## <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca iteratora dwukierunkowego, który wyznacza pierwszego elementu w kontrolowanej sekwencji lub bezpośrednio po zakończeniu pustej sekwencji. Służy do uzyskania iterację wyznacza `current` początku kontrolowanej sekwencji, ale jej stan można zmieniać w przypadku zmiany długości kontrolowanej sekwencji.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_hash_set_begin.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myhash_set::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [hash_set — (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)