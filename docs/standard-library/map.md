---
title: '&lt;Mapa&gt; | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <map>
dev_langs: C++
helpviewer_keywords: map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7079794aed6140dd4d21a7bf5bc7576363811b5b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltmapgt"></a>&lt;mapy&gt;
Definiuje mapowania klasy szablonu kontenera i multimap i ich obsługi szablonów.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <map>  
  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="operators"></a>Operatory  
  
|Mapy wersji|Multimap — wersja|Opis|  
|-----------------|----------------------|-----------------|  
|[Operator! = (map)](../standard-library/map-operators.md#op_neq)|[Operator! = (multimap)](../standard-library/map-operators.md#op_neq)|Testy, jeśli obiekt mapy lub multimap po lewej stronie operatora nie jest taki sam jak obiekt mapy lub multimap po prawej stronie.|  
|[Operator < (map)](../standard-library/map-operators.md#op_eq_eq)|[Operator < (multimap)](../standard-library/map-operators.md#op_eq_eq)|Testy, jeśli obiekt mapy lub multimap po lewej stronie operatora jest mniejsza niż obiekt mapy lub multimap po prawej stronie.|  
|[Operator < = (map)](../standard-library/map-operators.md#op_lt)|[operator\<= (multimap)](../standard-library/map-operators.md#op_lt)|Testy, jeśli obiekt mapy lub multimap po lewej stronie operatora jest mniejsza lub równa mapy lub multimap — obiektu po prawej stronie.|  
|[Operator == (map)](../standard-library/map-operators.md#op_eq_eq)|[Operator == (multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|Testy, jeśli obiekt mapy lub multimap po lewej stronie operatora jest taki sam jak obiekt mapy lub multimap po prawej stronie.|  
|[operator > (map)](../standard-library/map-operators.md#op_gt)|[operator > (multimap)](../standard-library/map-operators.md#op_gt_multimap)|Testy, jeśli obiekt mapy lub multimap po lewej stronie operatora jest większy niż mapa lub multimap obiekt po prawej stronie.|  
|[operator > = (map)](../standard-library/map-operators.md#op_gt_eq)|[operator > = (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|Testy, jeśli obiekt mapy lub multimap po lewej stronie operatora jest większa niż lub równa obiektu mapy lub multimap po prawej stronie.|  
  
### <a name="specialized-template-functions"></a>Specialized Template — Funkcje  
  
|Mapy wersji|Multimap — wersja|Opis|  
|-----------------|----------------------|-----------------|  
|[swap (map)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap_multimap)|Zamienia elementy dwóch map lub multimaps.|  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[value_compare — klasa](../standard-library/value-compare-class-map.md)|Udostępnia obiekt funkcji, który można porównać elementów mapy porównując wartości ich kluczy, aby określić ich kolejność względne w planie.|  
|[map — klasa](../standard-library/map-class.md)|Używany do przechowywania i pobierania danych z kolekcji, w którym każdy z elementów ma unikatowy klucz, z którym automatycznie porządkowania danych.|  
|[multimap — klasa](../standard-library/multimap-class.md)|Używany do przechowywania i pobierania danych z kolekcji, w którym każdy z elementów ma klucz, w którym automatycznie porządkowania danych i kluczy nie muszą mieć unikatowe wartości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Odwołanie do biblioteki C++ Standard](../standard-library/cpp-standard-library-reference.md)



