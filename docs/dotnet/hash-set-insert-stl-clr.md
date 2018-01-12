---
title: hash_set::INSERT (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_set::insert
dev_langs: C++
helpviewer_keywords: insert member [STL/CLR]
ms.assetid: 0a9bc9aa-012e-4101-9e8c-f1f4b6b76af7
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d467c22d94521e8f40c84c68f4ba421289caba9d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hashsetinsert-stlclr"></a>hash_set::insert (STL/CLR)
Dodaje elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
cliext::pair<iterator, bool> insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 pierwszy  
 Początek zakresu do wstawienia.  
  
 ostatni  
 Koniec zakresu do wstawienia.  
  
 w prawo  
 Wyliczenie do wstawienia.  
  
 Val  
 Wartość klucza do wstawienia.  
  
 gdzie  
 Gdzie w kontenerze, aby wstawić (tylko wskazówka).  
  
## <a name="remarks"></a>Uwagi  
 Każda z funkcji Członkowskich wstawia sekwencję określony przez pozostałych argumentów operacji.  
  
 Pierwszy funkcji członkowskiej usiłują Wstaw element z wartością `val`i zwraca pary wartości `X`. Jeśli `X.second` ma wartość true, `X.first` wyznacza nowo wstawionej elementu; w przeciwnym razie `X.first` wskazuje element z równoważne porządkowania, która już istnieje i jest wstawiany nie nowego elementu. Umożliwia ona wstawić jeden element.  
  
 Drugi funkcji członkowskiej wstawia element z wartością `val`za pomocą `where` jako wskazówkę (Aby poprawić wydajność) i zwraca iterację wyznacza nowo wstawiony element. Umożliwia ona pojedynczy element, który może być obok elementu, który znasz Wstaw.  
  
 Trzeci funkcji członkowskiej wstawia sekwencji [`first`, `last`). Umożliwia ona Wstawianie zero lub więcej elementów skopiowanych z innej sekwencji.  
  
 Czwarty funkcji członkowskiej wstawia sekwencji wskazywany przez `right`. Umożliwia ona Wstaw sekwencję opisanego przez moduł wyliczający.  
  
 Każdy element wstawiania czas proporcjonalna do logarytmu liczba elementów w kontrolowanej sekwencji. Wstawiania może występować w amortyzowanego stałej czasu jednak podane wskazówki, który wskazuje element sąsiadujące punkt wstawiania.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_hash_set_insert.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
typedef Myhash_set::pair_iter_bool Pairib;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    Pairib pair1 = c1.insert(L'x');   
    System::Console::WriteLine("insert(L'x') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
    pair1 = c1.insert(L'b');   
    System::Console::WriteLine("insert(L'b') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Myhash_set c2;   
    Myhash_set::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myhash_set c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(L'x') = [x True]  
insert(L'b') = [b False]  
 a b c x  
insert(begin(), L'y') = y  
 a b c x y  
 a b c x  
 a b c x y  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)