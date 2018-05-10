---
title: '&lt;Mapa&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <map>
dev_langs:
- C++
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac523342cc175721b9c1ef33a3d8ac4cad83033b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltmapgt"></a>&lt;mapy&gt;

Definiuje mapowania klasy szablonu kontenera i multimap i ich obsługi szablonów.

## <a name="syntax"></a>Składnia

```cpp
#include <map>

```

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|Mapy wersji|Multimap — wersja|Opis|
|-----------------|----------------------|-----------------|
|[Operator! = (map)](../standard-library/map-operators.md#op_neq)|[Operator! = (multimap)](../standard-library/map-operators.md#op_neq)|Testy, jeśli obiekt mapy lub multimap po lewej stronie operatora nie jest taki sam jak obiekt mapy lub multimap po prawej stronie.|
|[Operator < (map)](../standard-library/map-operators.md#op_eq_eq)|[Operator < (multimap)](../standard-library/map-operators.md#op_eq_eq)|Testy, jeśli obiekt mapy lub multimap po lewej stronie operatora jest mniejsza niż obiekt mapy lub multimap po prawej stronie.|
|[Operator < = (map)](../standard-library/map-operators.md#op_lt)|[operator\<= (multimap)](../standard-library/map-operators.md#op_lt)|Testy, jeśli obiekt mapy lub multimap po lewej stronie operatora jest mniejsza lub równa mapy lub multimap — obiektu po prawej stronie.|
|[operator== (map)](../standard-library/map-operators.md#op_eq_eq)|[operator== (multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|Testy, jeśli obiekt mapy lub multimap po lewej stronie operatora jest taki sam jak obiekt mapy lub multimap po prawej stronie.|
|[operator > (map)](../standard-library/map-operators.md#op_gt)|[operator > (multimap)](../standard-library/map-operators.md#op_gt_multimap)|Testy, jeśli obiekt mapy lub multimap po lewej stronie operatora jest większy niż mapa lub multimap obiekt po prawej stronie.|
|[operator > = (map)](../standard-library/map-operators.md#op_gt_eq)|[operator > = (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|Testy, jeśli obiekt mapy lub multimap po lewej stronie operatora jest większa niż lub równa obiektu mapy lub multimap po prawej stronie.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|Mapy wersji|Multimap — wersja|Opis|
|-----------------|----------------------|-----------------|
|[swap (map)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap_multimap)|Zamienia elementy dwóch map lub multimaps.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[value_compare, klasa](../standard-library/value-compare-class-map.md)|Udostępnia obiekt funkcji, który można porównać elementów mapy porównując wartości ich kluczy, aby określić ich kolejność względne w planie.|
|[map, klasa](../standard-library/map-class.md)|Używany do przechowywania i pobierania danych z kolekcji, w którym każdy z elementów ma unikatowy klucz, z którym automatycznie porządkowania danych.|
|[multimap, klasa](../standard-library/multimap-class.md)|Używany do przechowywania i pobierania danych z kolekcji, w którym każdy z elementów ma klucz, w którym automatycznie porządkowania danych i kluczy nie muszą mieć unikatowe wartości.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
