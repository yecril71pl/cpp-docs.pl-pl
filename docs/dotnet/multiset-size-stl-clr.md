---
title: multiset::size (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multiset::size
dev_langs: C++
helpviewer_keywords: size member [STL/CLR]
ms.assetid: 29338f4f-c13e-4eb6-844d-1d94769553c8
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1fb3ec48a865a6a7fea38a73832ccf3386932080
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="multisetsize-stlclr"></a>multiset::size (STL/CLR)
Liczy liczbę elementów.  
  
## <a name="syntax"></a>Składnia  
  
```  
size_type size();  
```  
  
## <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca długość kontrolowanej sekwencji. Można użyć do określenia liczby elementów aktualnie w kontrolowanej sekwencji. Jeśli wszystkie najważniejsze informacje dotyczące tego, czy sekwencja ma rozmiar różną od zera, zobacz [multiset::empty (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)`()`.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_multiset_size.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 3 starting with 3  
size() = 0 after clearing  
size() = 2 after adding 2  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw wielokrotny (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::EMPTY (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)