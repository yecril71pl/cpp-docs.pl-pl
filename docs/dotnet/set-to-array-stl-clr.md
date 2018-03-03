---
title: set::to_array (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::set::to_array
dev_langs:
- C++
helpviewer_keywords:
- to_array member [STL/CLR]
ms.assetid: 62ee03ce-5bf0-4235-9835-8b77929702c9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3e1ca3dbd78110483499de6de6216f2ca4e4718b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="settoarray-stlclr"></a>set::to_array (STL/CLR)
Kopiuje kontrolowanej sekwencji do nowej tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
cli::array<value_type>^ to_array();  
```  
  
## <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca tablicę zawierającą kontrolowanej sekwencji. Umożliwia ona uzyskać kopię kontrolowanej sekwencji w postaci tablicy.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_set_to_array.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c d  
a b c  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [set (STL/CLR)](../dotnet/set-stl-clr.md)