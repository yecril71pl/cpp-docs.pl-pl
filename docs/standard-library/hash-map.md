---
title: "&lt;hash_map —&gt; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <hash_map>
- std::<hash_map>
dev_langs: C++
helpviewer_keywords: hash_map header
ms.assetid: 0765708a-a668-42a2-9800-654c857bdcc2
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a996142e128f4113fb9d1057cd061155dae251f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lthashmapgt"></a>&lt;hash_map —&gt;
> [!NOTE]
>  Ten nagłówek jest przestarzała. Alternatywą jest [ \<unordered_map >](unordered-map.md).  
  
 Definiuje hash_map klasy szablonu kontenera i hash_multimap i ich obsługi szablonów.  
 
  
## <a name="syntax"></a>Składnia  
  
```  
#include <hash_map>  
  
```  
  
### <a name="operators"></a>Operatory  
  
|Hash_map — wersja|Hash_multimap — wersja|Opis|  
|-----------------------|----------------------------|-----------------|  
|[Operator! = (hash_map)](hash-map-operators.md#op_neq)|[Operator!=(hash_multimap)](hash-map-operators.md#op_neq_mm)|Testy, jeśli obiekt hash_map lub hash_multimap po lewej stronie operatora nie jest taki sam jak obiekt hash_map lub hash_multimap po prawej stronie.|  
|[Operator == (hash_map)](hash-map-operators.md#op_eq_eq)|[operator == (hash_multimap)] ((hash-map — operators.md #op_eq_eq_mm)|Testy, jeśli obiekt hash_map lub hash_multimap po lewej stronie operatora jest taki sam jak obiekt hash_map lub hash_multimap po prawej stronie.|  
  
### <a name="specialized-template-functions"></a>Specialized Template — Funkcje  
  
|Hash_map — wersja|Hash_multimap — wersja|Opis|  
|-----------------------|----------------------------|-----------------|  
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|Zamienia elementy dwóch hash_maps lub hash_multimaps.|  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[hash_compare, klasa](hash-compare-class.md)|Opisuje obiekt, który mogą być używane przez dowolny kontener asocjacyjna skrótu — hash_map hash_multimap, hash_set, lub hash_multiset — domyślnie **cech** obiektu parameter kolejność i wyznaczania wartości skrótu elementy zawierają.|  
|[value_compare, klasa](value-compare-class.md)|Udostępnia obiekt funkcji, który można porównać elementów hash_map porównując wartości ich kluczy, aby określić ich kolejność względne w hash_map.|  
|[hash_map, klasa](hash-map-class.md)|Używany do przechowywania i szybkie pobieranie danych z kolekcji, w którym każdy element jest parę klucza sortowania, którego wartość jest unikatowa i skojarzone dane wartości.|  
|[hash_multimap, klasa](hash-multimap-class.md)|Używany do przechowywania i szybkie pobieranie danych z kolekcji, w którym każdy element jest parę klucza sortowania, którego wartość nie musi być unikatowa i skojarzone dane wartości.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<hash_map >  
  
 **Namespace:** stdext —  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](cpp-standard-library-reference.md)



