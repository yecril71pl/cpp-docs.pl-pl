---
title: list::Resize (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::list::resize
dev_langs:
- C++
helpviewer_keywords:
- resize member [STL/CLR]
ms.assetid: c4b8d41f-a62b-4dbc-8568-0e0a9da24016
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ca91c9764f1fe438d0d7dfb66c52797d5d97aae8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="listresize-stlclr"></a>list::resize (STL/CLR)
Zmiany liczby elementów.  
  
## <a name="syntax"></a>Składnia  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>Parametry  
 new_size  
 Nowy rozmiar kontrolowanej sekwencji.  
  
 Val  
 Wartość elementu dopełnienia.  
  
## <a name="remarks"></a>Uwagi  
 Funkcje Członkowskie zarówno upewnij się, że [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md) `()` odtąd zwraca `new_size`. Należy go dłużej kontrolowanej sekwencji, pierwszej funkcji Członkowskich dołącza elementy o wartości `value_type()`, podczas gdy druga funkcji członkowskiej dołącza elementy o wartości `val`. Aby kontrolowanej sekwencji krótszy, zarówno funkcje Członkowskie skutecznie wymazać ostatni element [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md) `() -` `new_size` razy. Umożliwia ona upewnij się, że kontrolowanej sekwencji ma rozmiar `new_size`, przycinanie lub dopełnienie bieżącego kontrolowanej sekwencji.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_list_resize.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0 0  
size() = 0  
 x x x x x  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/listy >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::Clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)   
 [list::ERASE (STL/CLR)](../dotnet/list-erase-stl-clr.md)   
 [list::insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)