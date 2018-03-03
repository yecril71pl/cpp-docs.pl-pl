---
title: multiset::ERASE (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::multiset::erase
dev_langs:
- C++
helpviewer_keywords:
- erase member [STL/CLR]
ms.assetid: 3ff9fe2d-bf43-446a-bd3f-74550313a1d2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9e31d88345ea483c2abe5492b5b94122e86665cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="multiseterase-stlclr"></a>multiset::erase (STL/CLR)
Usuwa elementy z określonych pozycji.  
  
## <a name="syntax"></a>Składnia  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
size_type erase(key_type key)  
```  
  
#### <a name="parameters"></a>Parametry  
 pierwszy  
 Początek zakresu, aby wymazać.  
  
 klawisz  
 Wartość klucza, aby wymazać.  
  
 ostatni  
 Koniec zakresu, aby wymazać.  
  
 gdzie  
 Element, aby wymazać.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy funkcji członkowskiej spowoduje usunięcie elementu w kontrolowanej sekwencji wskazywana przez `where`i zwraca iterację wyznacza pierwszy element pozostałych poza element usunięty, lub [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md) `()` Jeśli nie zawiera żadnego takiego elementu. Umożliwia ona Usuń pojedynczy element.  
  
 Drugi funkcji członkowskiej usuwa elementy kontrolowanej sekwencji z zakresu [`first`, `last`) i zwraca iterację wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte, lub `end()` w przypadku braku takiego elementu istnieje.. Można użyć do usunięcia zero lub więcej elementów ciągłe.  
  
 Trzeci funkcji członkowskiej usuwa dowolny element kontrolowanej sekwencji, którego klucz został równoważne kolejności do `key`i zwraca liczbę liczba elementów usuniętych. Można użyć do usunięcia, a liczba wszystkie elementy zgodne z określonym kluczem.  
  
 Każdy element usunięcia czas proporcjonalna do logarytmu liczba elementów w kontrolowanej sekwencji.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_multiset_erase.cpp   
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
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Mymultiset::iterator it = c1.end();   
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
 **Nagłówek:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw wielokrotny (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::clear (STL/CLR)](../dotnet/multiset-clear-stl-clr.md)