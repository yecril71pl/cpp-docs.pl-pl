---
title: '&lt;Ustaw&gt; | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <set>
dev_langs:
- C++
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 83a933c889ad89ed7b5361217608303a9b42f500
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltsetgt"></a>&lt;set&gt;
Definiuje zestaw klas szablonu kontenera i multiset i ich obsługi szablonów.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <set>  
  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="operators"></a>Operatory  
  
|Ustaw wersję|Multiset — wersja|Opis|  
|-----------------|----------------------|-----------------|  
|[Operator! = (set)](../standard-library/set-operators.md#op_neq)|[Operator! = (multiset)](../standard-library/set-operators.md#op_neq)|Testy, jeśli nie jest równa set lub multiset — obiektu po prawej stronie set lub multiset — obiektu po lewej stronie operatora.|  
|[Operator < (wartość)](../standard-library/set-operators.md#op_lt)|[Operator < (multiset)](../standard-library/set-operators.md#op_lt_multiset)|Testy, jeśli wartość jest mniejsza niż set lub multiset — obiektu po prawej stronie set lub multiset — obiektu po lewej stronie operatora.|  
|[Operator < = (set)](../standard-library/set-operators.md#op_lt_eq)|[operator\<= (multiset)](../standard-library/set-operators.md#op_lt_eq_multiset)|Testy, jeśli wartość jest mniejsza niż lub równe set lub multiset — obiektu po prawej stronie set lub multiset — obiektu po lewej stronie operatora.|  
|[Operator == (set)](../standard-library/set-operators.md#op_eq_eq)|[Operator == (multiset)](../standard-library/set-operators.md#op_eq_eq_multiset)|Testy, jeśli set lub multiset — obiektu po lewej stronie operatora jest równa set lub multiset — obiektu po prawej stronie.|  
|[operator > (wartość)](../standard-library/set-operators.md#op_gt)|[operator > (multiset)](../standard-library/set-operators.md#op_gt_multiset)|Testy, jeśli set lub multiset — obiektu po lewej stronie operatora jest większa niż set lub multiset — obiektu po prawej stronie.|  
|[operator > = (set)](../standard-library/set-operators.md#op_gt_eq)|[operator > = (multiset)](../standard-library/set-operators.md#op_gt_eq_multiset)|Testy, jeśli set lub multiset — obiektu po lewej stronie operatora jest większa niż lub równa set lub multiset — obiektu po prawej stronie.|  
  
### <a name="specialized-template-functions"></a>Specialized Template — Funkcje  
  
|Ustaw wersję|Multiset — wersja|Opis|  
|-----------------|----------------------|-----------------|  
|[swap](../standard-library/set-functions.md#swap)|[swap (multiset)](../standard-library/set-functions.md#swap_multiset)|Zamienia elementy dwóch zestawów lub multisets.|  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[set, klasa](../standard-library/set-class.md)|Używany do przechowywania i pobierania danych z kolekcji, w której wartości elementy zawarte są unikatowe i służyć jako wartości klucza, zgodnie z którymi automatycznie porządkowania danych.|  
|[multiset, klasa](../standard-library/multiset-class.md)|Używany do przechowywania i pobierania danych z kolekcji, w której wartości elementów zawartych nie musi być unikatowa i które służą jako wartości klucza, zgodnie z którymi automatycznie porządkowania danych.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)



