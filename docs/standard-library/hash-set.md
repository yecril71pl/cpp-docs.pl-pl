---
title: "&lt;hash_set —&gt; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <hash_set>
- std::<hash_set>
dev_langs:
- C++
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d9e439d2e87f6bf8b23aea09f1f3dd7781f2c7e1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="lthashsetgt"></a>&lt;hash_set&gt;
> [!NOTE]
>  Ten nagłówek jest przestarzała. Alternatywą jest [< unordered_set >](../standard-library/unordered-set.md).  
  
 Definiuje hash_set klasy szablonu kontenera i hash_multiset i ich obsługi szablonów.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <hash_set>  
  
```  
  
## <a name="remarks"></a>Uwagi  
  
### <a name="operators"></a>Operatory  
  
|Hash_set — wersja|Hash_multiset — wersja|Opis|  
|-----------------------|----------------------------|-----------------|  
|[Operator! = (hash_set)](../standard-library/hash-set-operators.md#op_neq)|[Operator! = (hash_multiset)](../standard-library/hash-set-operators.md#op_neq)|Testy, jeśli obiekt hash_set lub hash_multiset po lewej stronie operatora nie jest taki sam jak obiekt hash_set lub hash_multiset po prawej stronie.|  
|[operator== (hash_set)](../standard-library/hash-set-operators.md#op_eq_eq)|[Operator == (hash_multiset)](../standard-library/hash-set-operators.md#op_eq_eq)|Testy, jeśli obiekt hash_set lub hash_multiset po lewej stronie operatora jest taki sam jak obiekt hash_set lub hash_multiset po prawej stronie.|  
  
### <a name="specialized-template-functions"></a>Specialized Template — Funkcje  
  
|Hash_set — wersja|Hash_multiset — wersja|Opis|  
|-----------------------|----------------------------|-----------------|  
|[swap (hash_set)](../standard-library/hash-set-functions.md#swap)|[swap (hash_multiset)](../standard-library/hash-set-functions.md#swap_hash_multiset)|Zamienia elementy dwóch hash_sets lub hash_multisets.|  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[hash_compare, klasa](../standard-library/hash-compare-class.md)|Opisuje obiekt, który mogą być używane przez dowolny kontener asocjacyjna skrótu — hash_map hash_multimap, hash_set, lub hash_multiset — domyślnie **cech** obiektu parameter kolejność i wyznaczania wartości skrótu elementy zawierają.|  
|[hash_set, klasa](../standard-library/hash-set-class.md)|Używany do przechowywania i szybkie pobieranie danych z kolekcji, w której wartości elementy zawarte są unikatowe i służyć jako wartości klucza.|  
|[hash_multiset, klasa](../standard-library/hash-multiset-class.md)|Używany do przechowywania i szybkie pobieranie danych z kolekcji, w której wartości elementy zawarte są unikatowe i służyć jako wartości klucza.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)



