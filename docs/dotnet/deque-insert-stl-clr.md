---
title: deque::INSERT (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: a3b86c46-e6a8-42d0-b642-5a8f05ddd68c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6819b1c2e1086c38b2bb1be8207a26afc85168d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dequeinsert-stlclr"></a>deque::insert (STL/CLR)
Dodaje elementy na określonej pozycji.  
  
## <a name="syntax"></a>Składnia  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 `count`  
 Liczba elementów do wstawienia.  
  
 `first`  
 Początek zakresu do wstawienia.  
  
 `last`  
 Koniec zakresu do wstawienia.  
  
 `right`  
 Wyliczenie do wstawienia.  
  
 `val`  
 Wartość elementu do wstawienia.  
  
 `where`  
 Gdzie w kontenerze, aby wstawić przed.  
  
## <a name="remarks"></a>Uwagi  
 Każdy element członkowski funkcji wstawiania przed elementem wskazywana przez `where` w kontrolowanej sekwencji sekwencję określonej przez pozostałych argumentów.  
  
 Pierwszy funkcji członkowskiej wstawia element z wartością `val` i zwracającą iterator określający nowo wstawiony element. Umożliwia ona Wstaw pojedynczy element przed miejsce wskazywany przez iteratora.  
  
 Drugi funkcji członkowskiej wstawia powtórzenia `count` elementy wartości `val`. Umożliwia ona Wstawianie zero lub więcej sąsiadujących elementów, które są wszystkie kopie tej samej wartości.  
  
 Jeśli `InIt` jest typu integer trzeci funkcji członkowskiej działa tak samo jak `insert(where, (size_type)first, (value_type)last)`. W przeciwnym razie wstawia sekwencji [`first`, `last`). Umożliwia ona Wstawianie zero lub więcej sąsiadujących elementów skopiowanych z innej sekwencji.  
  
 Czwarty funkcji członkowskiej wstawia sekwencji wskazywany przez `right`. Umożliwia ona Wstaw sekwencję opisanego przez moduł wyliczający.  
  
 Podczas wstawiania pojedynczy element, liczbę kopii elementu jest liniowa liczby elementów między punkt wstawiania i bliżej położonego zakończeniem sekwencji. (Podczas wstawiania co najmniej jeden element na końcu sekwencji, brak kopii elementu wykonywane.) Jeśli `InIt` jest iterację wejściowych trzeci funkcji członkowskiej skutecznie wykonuje wstawiania jednej dla każdego elementu w sekwencji. W przeciwnym razie podczas wstawiania `N` elementów, liczbę kopii elementu jest liniowa w `N` wraz z liczbą elementów między punkt wstawiania i bliżej położonego zakończeniem sekwencji.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_insert.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::deque<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::deque<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(begin()+1, L'x') = x  
 a x b c  
 y y  
 y y a x b  
 a x b c y y a x b  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/deque — >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [deque — (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::assign (STL/CLR)](../dotnet/deque-assign-stl-clr.md)