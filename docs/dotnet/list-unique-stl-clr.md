---
title: list::Unique (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::unique
dev_langs:
- C++
helpviewer_keywords:
- unique member [STL/CLR]
ms.assetid: c3a29e4e-0ec1-4472-b050-7a9511037132
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d5dbfab0fb53a4ca11128d01e7b32060c6428549
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="listunique-stlclr"></a>list::unique (STL/CLR)
Usuwa elementy sąsiednie przekazujące określonego testu.  
  
## <a name="syntax"></a>Składnia  
  
```  
void unique();  
template<typename Pred2>  
    void unique(Pred2 pred);  
```  
  
#### <a name="parameters"></a>Parametry  
 pred  
 Moduł porównujący dla elementu pary.  
  
## <a name="remarks"></a>Uwagi  
 Usuwa pierwsze funkcji członkowskiej z kontrolowanej sekwencji (wymazywanie) każdy element, który porównuje równa do jego poprzedniego elementu — Jeśli element `X` poprzedza element `Y` i `X == Y`, usuwa funkcji członkowskiej `Y`. Umożliwia ona Usuń wszystkie oprócz jednego kopię co podsekwencji elementy sąsiednie tego porównania równości. Należy pamiętać, że jeśli kontrolowanej sekwencji porządkowania, takie jak przez wywołanie metody [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)`()`, funkcja członkowska pozostawia tylko elementy unikatowe wartości. (Stąd nazwa).  
  
 Drugi funkcji członkowskiej działa tak samo jako pierwszy, z wyjątkiem, że każdy element spowoduje usunięcie `Y` następującego elementu `X` dla którego `pred(X, Y)`. Umożliwia ona Usuń wszystkie oprócz jednego kopię co podsekwencji sąsiadujących elementów, które spełniają funkcji predykatu lub delegata, który określisz. Należy pamiętać, że jeśli kontrolowanej sekwencji porządkowania, takie jak przez wywołanie metody `sort(pred)`, funkcja członkowska pozostawia tylko elementy, które nie mają równoważne kolejności z innymi elementami.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_list_unique.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique   
    cliext::list<wchar_t> c2(c1);   
    c2.unique();   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique(not_equal_to)   
    c2 = c1;   
    c2.unique(cliext::not_equal_to<wchar_t>());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a a b c  
a b c  
a a  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/listy >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::Remove (STL/CLR)](../dotnet/list-remove-stl-clr.md)   
 [list::remove_if (STL/CLR)](../dotnet/list-remove-if-stl-clr.md)   
 [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)