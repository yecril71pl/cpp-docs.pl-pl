---
title: "hash — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- functional/std::hash
- bitset/std::hash
- memory/std::hash
- string/std::hash
- system_error/std::hash
- thread/std::hash
- typeindex/std::hash
- vector/std::hash
- XSTDDEF/std::hash
- xstring/std::hash
dev_langs: C++
helpviewer_keywords:
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
ms.assetid: e1b500c6-a5c8-4f6f-ad33-7ec52eb8e2e4
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38d6cfc3864b76304f9146ebe864805a500aa519
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hash-class"></a>hash — Klasa
Oblicza wartość skrótu dla wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Ty>  
struct hash {  
    size_t operator()(Ty val) const; 
};  
```  
  
## <a name="remarks"></a>Uwagi  
Obiekt funkcji określa funkcja do wyznaczania wartości skrótu, mapowania wartości typu *Ty* dystrybucji wartości indeksu. Element członkowski `operator()` zwraca wartość skrótu dla *val*, odpowiednie do użycia z szablonu klasy `unordered_map`, `unordered_multimap`, `unordered_set`, i `unordered_multiset`. Standardowa biblioteka zawiera specjalizacje dla podstawowych typów: *Ty* mogą być dowolnego typu skalarne, łącznie z typami wskaźników i typów wyliczenia. Ponadto istnieją specjalizacje dla typów biblioteki `string`, `wstring`, `u16string`, `u32string`, `string_view`, `wstring_view`, `u16string_view`, `u32string_view`, `bitset`, `error_code`, `error_condition`, `optional`, `shared_ptr`, `thread`, `type_index`, `unique_ptr`, `variant`, i `vector<bool>`.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// std__functional__hash.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
#include <unordered_set>   
  
int main()   
    {   
    std::unordered_set<int, std::hash<int> > c0;   
    c0.insert(3);   
    std::cout << *c0.find(3) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
3  
```  
  
## <a name="requirements"></a>Wymagania  
**Nagłówek:** \<funkcjonalności >  
  
**Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< unordered_map >](../standard-library/unordered-map.md)   
 [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md)   
 [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md)   
 [<unordered_set>](../standard-library/unordered-set.md)

