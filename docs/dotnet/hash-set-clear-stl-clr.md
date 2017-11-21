---
title: hash_set::Clear (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_set::clear
dev_langs: C++
helpviewer_keywords: clear member [STL/CLR]
ms.assetid: 9f38b72a-5db8-485a-b41a-7d47ac57f4a9
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3175588d49c02d960067864a4d3ff35db0464c5b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="hashsetclear-stlclr"></a>hash_set::clear (STL/CLR)
Usuwa wszystkie elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
void clear();  
```  
  
## <a name="remarks"></a>Uwagi  
 Wywołuje funkcję elementu członkowskiego [hash_set::erase (STL/CLR)](../dotnet/hash-set-erase-stl-clr.md) `(` [hash_set::begin (STL/CLR)](../dotnet/hash-set-begin-stl-clr.md) `(),` [hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md) `())`. Umożliwia ona upewnij się, że kontrolowanej sekwencji jest pusty.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_hash_set_clear.cpp   
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
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [hash_set — (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::ERASE (STL/CLR)](../dotnet/hash-set-erase-stl-clr.md)