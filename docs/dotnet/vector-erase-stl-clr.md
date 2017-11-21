---
title: Vector::ERASE (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::erase
dev_langs: C++
helpviewer_keywords: erase member [STL/CLR]
ms.assetid: 624905eb-83c0-499b-a07a-c10aebd7acc3
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7edabb5d02b09944f5745a6d6cfc264fb120eade
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="vectorerase-stlclr"></a>vector::erase (STL/CLR)
Usuwa elementy z określonych pozycji.  
  
## <a name="syntax"></a>Składnia  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>Parametry  
 pierwszy  
 Początek zakresu, aby wymazać.  
  
 ostatni  
 Koniec zakresu, aby wymazać.  
  
 gdzie  
 Element, aby wymazać.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy funkcji członkowskiej spowoduje usunięcie elementu w kontrolowanej sekwencji wskazywana przez `where`. Umożliwia ona Usuń pojedynczy element.  
  
 Drugi funkcji członkowskiej usuwa elementy kontrolowanej sekwencji z zakresu [`first`, `last`). Można użyć do usunięcia zero lub więcej elementów ciągłe.  
  
 Zarówno członek zwracają wartość iterację wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte, lub [vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `()` , jeśli nie zawiera żadnego takiego elementu.  
  
 Podczas usuwania elementów, liczbę kopii elementu jest liniowa liczby elementów między koniec wymazywania i bliżej położonego zakończeniem sekwencji. (Podczas usuwania co najmniej jeden element na końcu sekwencji, brak kopii elementu wykonywane.)  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_vector_erase.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::vector<wchar_t>::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/wektor >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Wektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector::Clear (STL/CLR)](../dotnet/vector-clear-stl-clr.md)