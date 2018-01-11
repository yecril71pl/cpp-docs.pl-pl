---
title: '&lt;Ustaw&gt; | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <set>
dev_langs: C++
helpviewer_keywords: set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 16338888d64155ddeab188159030ac060ebb2b17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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



