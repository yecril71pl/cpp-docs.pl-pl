---
title: priority_queue::priority_queue (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::priority_queue::priority_queue
dev_langs:
- C++
helpviewer_keywords:
- priority_queue member [STL/CLR]
ms.assetid: aab423d7-959e-48fd-9028-e9f45f43cb8a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8cb50eed9dbfcbe9480a6588ff10f966f1888205
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33163396"
---
# <a name="priorityqueuepriorityqueue-stlclr"></a>priority_queue::priority_queue (STL/CLR)
Tworzy obiekt Karta kontenera.  
  
## <a name="syntax"></a>Składnia  
  
```  
priority_queue();  
priority_queue(priority_queue<Value, Container> right);  
priority_queue(priority_queue<Value, Container> right);  
explicit priority_queue(value_compare^ pred);  
priority_queue(value_compare^ pred, container_type% cont);  
template<typename InIt>  
    priority_queue(InIt first, InIt last);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred, container_type% cont);  
```  
  
#### <a name="parameters"></a>Parametry  
 Pobi  
 Kontener do skopiowania.  
  
 pierwszy  
 Początek zakresu do wstawienia.  
  
 ostatni  
 Koniec zakresu do wstawienia.  
  
 pred  
 Porządkowanie predykatu w kontrolowanej sekwencji.  
  
 w prawo  
 Obiekt lub zakresu do wstawienia.  
  
## <a name="remarks"></a>Uwagi  
 Konstruktor:  
  
 `priority_queue();`  
  
 tworzy pusty kontener zawinięty, przy użyciu domyślnego porządkowanie predykatu. Umożliwia ona Określ pusty początkowej kontrolowanej sekwencji, przy użyciu domyślnego porządkowanie predykatu.  
  
 Konstruktor:  
  
 `priority_queue(priority_queue<Value, Container>% right);`  
  
 Tworzy opakowana kontener, który jest kopią `right.get_container()`, z porządkowania predykatu `right.value_comp()`. Należy użyć do określenia początkowej kontrolowanej sekwencji, który jest kopią sekwencji kontrolowane przez obiekt kolejki `right`, z tego samego sortowania predykatu.  
  
 Konstruktor:  
  
 `priority_queue(priority_queue<Value, Container>^ right);`  
  
 Tworzy opakowana kontener, który jest kopią `right->get_container()`, z porządkowania predykatu `right->value_comp()`. Należy użyć do określenia początkowej kontrolowanej sekwencji, który jest kopią sekwencji kontrolowane przez obiekt kolejki `*right`, z tego samego sortowania predykatu.  
  
 Konstruktor:  
  
 `explicit priority_queue(value_compare^ pred);`  
  
 tworzy pusty kontener opakowana z porządkowania predykatu `pred`. Umożliwia ona Określ pusty początkowej kontrolowanej sekwencji, z określony predykat porządkowania.  
  
 Konstruktor:  
  
 `priority_queue(value_compare^ pred, container_type cont);`  
  
 tworzy pusty kontener opakowana z porządkowania predykatu `pred`, następnie umieszcza wszystkie elementy `cont` można używać do określenia początkowej kontrolowanej sekwencji z istniejącego kontenera, z określony predykat porządkowania.  
  
 Konstruktor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last);`  
  
 tworzy kontener opakowana pusty z predykatu sortowania domyślnego, a następnie umieszcza sekwencji [`first`, `last`). Umożliwia ona określić początkowej kontrolowanej sekwencji z określonym eqeuence, określony predykat porządkowania.  
  
 Konstruktor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`  
  
 tworzy pusty kontener opakowana z porządkowania predykatu `pred`, następnie wypchnięcia sekwencji [`first`, `last`). Umożliwia ona określić początkowej kontrolowanej sekwencji z określonym seqeuence, określony predykat porządkowania.  
  
 Konstruktor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`  
  
 tworzy pusty kontener opakowana z porządkowania predykatu `pred`, następnie umieszcza wszystkie elementy `cont` plus sekwencji [`first`, `last`). Umożliwia ona określić początkowej kontrolowanej sekwencji z istniejącego kontenera i określonym seqeuence, określony predykat porządkowania.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// cliext_priority_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/deque>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
typedef cliext::deque<wchar_t> Mydeque;   
int main()   
    {   
// construct an empty container   
    Mypriority_queue c1;   
    Mypriority_queue::container_type^ wc1 = c1.get_container();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    for each (wchar_t elem in wc1)   
        c2.push(elem);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule by copying an underlying container   
    Mypriority_queue c2x =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
   for each (wchar_t elem in c2x.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mypriority_queue c3(wc1->begin(), wc1->end());   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mypriority_queue c4(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>());   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range, another container, and an ordering rule   
    Mypriority_queue c5(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c5.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Mypriority_queue c6(c3);   
    for each (wchar_t elem in c6.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mypriority_queue c7(%c3);   
    for each (wchar_t elem in c7.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule, by copying an underlying container   
    Mypriority_queue c8 =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c8.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 c a b  
size() = 0  
 a c b  
 a c b  
 c a b  
 a c b  
 a a b c c b  
 c a b  
 c a b  
 a c b  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/kolejki >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [priority_queue — (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::ASSIGN (STL/CLR)](../dotnet/priority-queue-assign-stl-clr.md)   
 [priority_queue::generic_container (STL/CLR)](../dotnet/priority-queue-generic-container-stl-clr.md)   
 [priority_queue::operator= (STL/CLR)](../dotnet/priority-queue-operator-assign-stl-clr.md)