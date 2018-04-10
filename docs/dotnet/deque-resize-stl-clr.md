---
title: deque::Resize (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- cliext::deque::resize
dev_langs:
- C++
helpviewer_keywords:
- resize member [STL/CLR]
ms.assetid: c83f3c57-38b3-4706-a124-59bafbf88484
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fac11adade64d03696cbe73b09d1c35dfdd026b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dequeresize-stlclr"></a>deque::resize (STL/CLR)
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
 Funkcje Członkowskie zarówno upewnij się, że [deque::size (STL/CLR)](../dotnet/deque-size-stl-clr.md) `()` odtąd zwraca `new_size`. Należy go dłużej kontrolowanej sekwencji, pierwszej funkcji Członkowskich dołącza elementy o wartości `value_type()`, podczas gdy druga funkcji członkowskiej dołącza elementy o wartości `val`. Aby kontrolowanej sekwencji krótszy, zarówno funkcje Członkowskie skutecznie wymazać ostatni element [deque::size (STL/CLR)](../dotnet/deque-size-stl-clr.md) `() -` `new_size` razy. Umożliwia ona upewnij się, że kontrolowanej sekwencji ma rozmiar `new_size`, przycinanie lub dopełnienie bieżącego kontrolowanej sekwencji.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_deque_resize.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::deque<wchar_t> c1;   
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
 **Nagłówek:** \<cliext/deque — >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [deque — (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::Clear (STL/CLR)](../dotnet/deque-clear-stl-clr.md)   
 [deque::ERASE (STL/CLR)](../dotnet/deque-erase-stl-clr.md)   
 [deque::insert (STL/CLR)](../dotnet/deque-insert-stl-clr.md)