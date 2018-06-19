---
title: list::splice (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::splice
dev_langs:
- C++
helpviewer_keywords:
- splice member [STL/CLR]
ms.assetid: ebc424b9-8341-4a88-b101-86d56324f5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e0c92faf6a4ec84e6ed65c58d02337038398d37e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135953"
---
# <a name="listsplice-stlclr"></a>list::splice (STL/CLR)
Restitch łącza między węzłami.  
  
## <a name="syntax"></a>Składnia  
  
```  
void splice(iterator where, list<Value>% right);  
void splice(iterator where, list<Value>% right,  
    iterator first);  
void splice(iterator where, list<Value>% right,  
    iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>Parametry  
 pierwszy  
 Początek zakresu splice.  
  
 ostatni  
 Koniec zakresu do splice.  
  
 w prawo  
 Kontener, aby splice z.  
  
 gdzie  
 Gdzie w celu splice przed kontenera.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy funkcji członkowskiej wstawia sekwencji kontrolowane przez `right` przed elementu w kontrolowanej sekwencji wskazywana przez `where`. Usuwa również wszystkie elementy z `right`. (`%right` nie może być równa `this`.) Umożliwia ona splice wszystkie jedną listę do innego.  
  
 Drugi funkcji członkowskiej usuwa element wskazywana przez `first` w sekwencji kontrolowane przez `right` i wstawia go przed elementu w kontrolowanej sekwencji wskazywana przez `where`. (Jeśli `where` `==` `first` `||` `where` `== ++first`, Brak zmian.) Umożliwia ona splice pojedynczy element listy jednego do drugiego.  
  
 Trzeci funkcji członkowskiej wstawia Podzakres wskazywany przez [`first`, `last`) z sekwencji kontrolowane przez `right` przed elementu w kontrolowanej sekwencji wskazywana przez `where`. Powoduje usunięcie oryginalnego Podzakres z sekwencji kontrolowane przez `right`. (Jeśli `right` `==` `this`, zakres [`first`, `last`) nie może zawierać elementu wskazywanego przez `where`.) Umożliwia ona splice podsekwencji zero lub więcej elementów z listy jeden do innego.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_list_splice.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// splice to a new list   
    cliext::list<wchar_t> c2;   
    c2.splice(c2.begin(), c1);   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return one element   
    c1.splice(c1.end(), c2, c2.begin());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return remaining elements   
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
c1.size() = 0  
 a b c  
 a  
 b c  
 b c a  
c2.size() = 0  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/listy >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::ASSIGN (STL/CLR)](../dotnet/list-assign-stl-clr.md)   
 [list::INSERT (STL/CLR)](../dotnet/list-insert-stl-clr.md)   
 [list::merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)