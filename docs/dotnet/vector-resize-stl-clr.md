---
title: Vector::Resize (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::resize
dev_langs:
- C++
helpviewer_keywords:
- resize member [STL/CLR]
ms.assetid: a3556fbc-67d9-463a-9ffc-cb43ee15657f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f7327b62906746ef3bb561d88f8c6ddc2134aa65
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="vectorresize-stlclr"></a>vector::resize (STL/CLR)
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
 Funkcje Członkowskie zarówno upewnij się, że [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `()` odtąd zwraca `new_size`. Należy go dłużej kontrolowanej sekwencji, pierwszej funkcji Członkowskich dołącza elementy o wartości `value_type()`, podczas gdy druga funkcji członkowskiej dołącza elementy o wartości `val`. Aby kontrolowanej sekwencji krótszy, zarówno funkcje Członkowskie skutecznie wymazać ostatni element [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `() -` `new_size` razy. Umożliwia ona upewnij się, że kontrolowanej sekwencji ma rozmiar `new_size`, przycinanie lub dopełnienie bieżącego kontrolowanej sekwencji.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_vector_resize.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::vector<wchar_t> c1;   
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
 **Nagłówek:** \<cliext/wektor >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Wektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector::Clear (STL/CLR)](../dotnet/vector-clear-stl-clr.md)   
 [Vector::ERASE (STL/CLR)](../dotnet/vector-erase-stl-clr.md)   
 [vector::insert (STL/CLR)](../dotnet/vector-insert-stl-clr.md)