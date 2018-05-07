---
title: Vector::Capacity (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::capacity
dev_langs:
- C++
helpviewer_keywords:
- capacity member [STL/CLR]
ms.assetid: f82d8da9-8b4d-4288-8d18-8e9ca5911d87
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9a08766c6b23deb4e36ad8c83f9c1f3e2bc1df1f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="vectorcapacity-stlclr"></a>vector::capacity (STL/CLR)
Informuje o rozmiarze Magazyn przydzielony do kontenera.  
  
## <a name="syntax"></a>Składnia  
  
```  
size_type capacity();  
```  
  
## <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca magazynu przydzielonego do przechowywania kontrolowanej sekwencji przynajmniej tak duże jak wartość [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`. Można użyć do określenia, ile kontener może zwiększyć się przed należy zmienić alokację magazynu w kontrolowanej sekwencji.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_vector_capacity.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
capacity() = 4, ok = True  
capacity() = 9, ok = True  
```  
  
## <a name="description"></a>Opis  
 Należy pamiętać, że rzeczywistej pojemności może różnić się od pokazanych tu wartości, tak długo jak `ok` testy raportu wartość true.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/wektor >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Wektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::reserve (STL/CLR)](../dotnet/vector-reserve-stl-clr.md)