---
title: set::upper_bound (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::upper_bound
dev_langs:
- C++
helpviewer_keywords:
- upper_bound member [STL/CLR]
ms.assetid: 874d258a-990f-486f-ac7b-757a2f7c150a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: da9f1ce48d77d3168dbfcb61d6ff23415d4f4c5b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164078"
---
# <a name="setupperbound-stlclr"></a>set::upper_bound (STL/CLR)
Wyszukuje koniec zakresu, który jest zgodny z określonym kluczem.  
  
## <a name="syntax"></a>Składnia  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 klawisz  
 Wartość klucza do wyszukania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja członkowska Określa ostatni element `X` w kontrolowanej sekwencji zawierającej równoważne kolejności do `key`. Jeśli nie zawiera żadnego takiego elementu lub `X` jest ostatniego elementu w kontrolowanej sekwencji zwraca [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; w przeciwnym razie zwraca iterację wyznacza pierwszy element poza `X`. Umożliwia ona obecnie Znajdź koniec sekwencję elementów w kontrolowanej sekwencji, który jest zgodny z określonym kluczem.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_set_upper_bound.cpp   
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
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*upper_bound(L'a') = {0}",   
        *c1.upper_bound(L'a'));   
    System::Console::WriteLine("*upper_bound(L'b') = {0}",   
        *c1.upper_bound(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = b  
*upper_bound(L'b') = c  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Ustaw (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set::Count (STL/CLR)](../dotnet/set-count-stl-clr.md)   
 [set::equal_range (STL/CLR)](../dotnet/set-equal-range-stl-clr.md)   
 [set::Find (STL/CLR)](../dotnet/set-find-stl-clr.md)   
 [set::lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md)