---
title: set::end (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::set::end
dev_langs:
- C++
helpviewer_keywords:
- end member [STL/CLR]
ms.assetid: 3fe66e73-5eb9-4972-8a07-01f2eb4d1ccb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 70611bf9b8e7f99f034709499d82d05b24b817b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="setend-stlclr"></a>set::end (STL/CLR)
Określa koniec kontrolowanej sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
iterator end();  
```  
  
## <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca iteratora dwukierunkowego tego punkty bezpośrednio po zakończeniu kontrolowanej sekwencji. Służy do uzyskania iterację Określa koniec kontrolowanej sekwencji; jego stan zmieniać w przypadku zmiany długości kontrolowanej sekwencji.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_set_end.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Myset::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Ustaw (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set::begin (STL/CLR)](../dotnet/set-begin-stl-clr.md)