---
title: hash_map::hash_map (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_map::hash_map
dev_langs: C++
helpviewer_keywords: hash_map member [STL/CLR]
ms.assetid: d65eb3fa-4bf9-4186-95f8-5517c90ef1fa
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b00688397cc76bb618631dfa92f4da16e6f4bc4a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="hashmaphashmap-stlclr"></a>hash_map::hash_map (STL/CLR)
Konstruuje obiekt kontenera.  
  
## <a name="syntax"></a>Składnia  
  
```  
hash_map();  
explicit hash_map(key_compare^ pred);  
hash_map(key_compare^ pred, hasher^ hashfn);  
hash_map(hash_map<Key, Mapped>% right);  
hash_map(hash_map<Key, Mapped>^ right);  
template<typename InIter>  
    hash_maphash_map(InIter first, InIter last);  
template<typename InIter>  
    hash_map(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_map(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred, hasher^ hashfn);  
```  
  
#### <a name="parameters"></a>Parametry  
 pierwszy  
 Początek zakresu do wstawienia.  
  
 hashfn  
 Hash — funkcja kluczy mapowania do zasobników.  
  
 ostatni  
 Koniec zakresu do wstawienia.  
  
 pred  
 Porządkowanie predykatu w kontrolowanej sekwencji.  
  
 w prawo  
 Obiekt lub zakresu do wstawienia.  
  
## <a name="remarks"></a>Uwagi  
 Konstruktor:  
  
 `hash_map();`  
  
 Inicjuje kontrolowanej sekwencji z żadnych elementów przy użyciu domyślnego porządkowanie predykatu `key_compare()`i przy użyciu funkcji skrótu domyślne. Umożliwia ona Określ pusty początkowej kontrolowanej sekwencji, przy użyciu domyślnego porządkowanie funkcji predykatu i wyznaczania wartości skrótu.  
  
 Konstruktor:  
  
 `explicit hash_map(key_compare^ pred);`  
  
 Inicjuje kontrolowanej sekwencji z żadnych elementów z porządkowania predykatu `pred`i przy użyciu funkcji skrótu domyślne. Umożliwia ona Określ pusty początkowej kontrolowanej sekwencji, określony predykat porządkowania i domyślnej funkcji skrótu.  
  
 Konstruktor:  
  
 `hash_map(key_compare^ pred, hasher^ hashfn);`  
  
 Inicjuje kontrolowanej sekwencji z żadnych elementów z porządkowania predykatu `pred`i przy użyciu funkcji skrótu `hashfn`. Umożliwia ona Określ pusty początkowej kontrolowanej sekwencji, przy użyciu określonego sortowania funkcji predykatu i wyznaczania wartości skrótu.  
  
 Konstruktor:  
  
 `hash_map(hash_map<Key, Mapped>% right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`right.begin()`, `right.end()`), przy użyciu domyślnego porządkowanie predykat i przy użyciu funkcji skrótu domyślne. Należy użyć do określenia początkowej kontrolowanej sekwencji, który jest kopią sekwencji kontrolowane przez obiekt hash_map `right`, przy użyciu domyślnego sortowania predykat i funkcji skrótu.  
  
 Konstruktor:  
  
 `hash_map(hash_map<Key, Mapped>^ right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`right->begin()`, `right->end()`), przy użyciu domyślnego porządkowanie predykat i przy użyciu funkcji skrótu domyślne. Należy użyć do określenia początkowej kontrolowanej sekwencji, który jest kopią sekwencji kontrolowane przez obiekt hash_map `right`, przy użyciu domyślnego sortowania predykat i funkcji skrótu.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_map(InIter first, InIter last);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`first`, `last`), przy użyciu domyślnego porządkowanie predykat i przy użyciu funkcji skrótu domyślne. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji przy użyciu domyślnego porządkowanie funkcji predykatu i wyznaczania wartości skrótu.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_map(InIter first, InIter last, key_compare^ pred);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`first`, `last`), z porządkowania predykatu `pred`i przy użyciu funkcji skrótu domyślne. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji określony predykat porządkowania i domyślnej funkcji skrótu.  
  
 Konstruktor:  
  
 `template<typename InIter> hash_map(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`first`, `last`), z porządkowania predykatu `pred`i przy użyciu funkcji skrótu `hashfn`. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji o określonej porządkowania funkcji wyznaczania wartości skrótu i predykatu.  
  
 Konstruktor:  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją wskazywany przez moduł wyliczający `right`, przy użyciu domyślnego porządkowanie predykat i przy użyciu funkcji skrótu domyślne. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji opisanego przez moduł wyliczający przy użyciu domyślnego porządkowanie funkcji predykatu i wyznaczania wartości skrótu.  
  
 Konstruktor:  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją wskazywany przez moduł wyliczający `right`, z porządkowania predykatu `pred`i przy użyciu funkcji skrótu domyślne. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji opisanego przez moduł wyliczający, przy użyciu określonego sortowania predykat i domyślnej funkcji skrótu.  
  
 Konstruktor:  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją wskazywany przez moduł wyliczający `right`, z porządkowania predykatu `pred`i przy użyciu funkcji skrótu `hashfn`. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji opisanego przez moduł wyliczający o określonej porządkowania funkcji wyznaczania wartości skrótu i predykatu.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_hash_map_construct.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
// construct an empty container   
    Myhash_map c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_map c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Myhash_map::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_map c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_map::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (Myhash_map::value_type elem in c2h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_map c3(c1.begin(), c1.end());   
    for each (Myhash_map::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_map c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Myhash_map::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_map c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_map::hasher(&myfun));   
    for each (Myhash_map::value_type elem in c4h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_map c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_map::value_type>^)%c3);   
    for each (Myhash_map::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_map c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_map::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Myhash_map::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_map c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_map::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_map::hasher(&myfun));   
    for each (Myhash_map::value_type elem in c6h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_map c7(c4);   
    for each (Myhash_map::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Myhash_map c8(%c3);   
    for each (Myhash_map::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [hash_map — (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map::generic_container (STL/CLR)](../dotnet/hash-map-generic-container-stl-clr.md)   
 [hash_map::operator = (STL/CLR)](../dotnet/hash-map-operator-assign-stl-clr.md)