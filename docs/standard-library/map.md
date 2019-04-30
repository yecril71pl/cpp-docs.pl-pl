---
title: '&lt;Mapy&gt;'
ms.date: 11/04/2016
f1_keywords:
- <map>
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
ms.openlocfilehash: 0ea47a28599df543987831ee13a2c645f72a0113
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412998"
---
# <a name="ltmapgt"></a>&lt;Mapy&gt;

Definiuje mapę klasy szablonu kontenera i multimap i ich szablonów pomocniczych.

## <a name="syntax"></a>Składnia

```cpp
#include <map>
```

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|Mapy wersji|Multimap — wersja|Opis|
|-----------------|----------------------|-----------------|
|[Operator! = (map)](../standard-library/map-operators.md#op_neq)|[Operator! = (multimap)](../standard-library/map-operators.md#op_neq)|Sprawdza, czy obiekt mapy lub multimap po lewej stronie operatora nie jest równy obiektowi mapa lub multimap po prawej stronie.|
|[Operator < (map)](../standard-library/map-operators.md#op_eq_eq)|[Operator < (multimap)](../standard-library/map-operators.md#op_eq_eq)|Sprawdza, czy obiekt mapy lub multimap po lewej stronie operatora jest mniejszy niż obiekt mapy lub multimap po prawej stronie.|
|[Operator < = (map)](../standard-library/map-operators.md#op_lt)|[operator\<= (multimap)](../standard-library/map-operators.md#op_lt)|Sprawdza, czy mapa lub multimap obiektu po lewej stronie operatora jest mniejszy niż lub równe mapa lub multimap obiektu po prawej stronie.|
|[operator== (map)](../standard-library/map-operators.md#op_eq_eq)|[operator== (multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|Sprawdza, czy obiekt mapy lub multimap po lewej stronie operatora jest równy obiektowi mapa lub multimap po prawej stronie.|
|[operator > (map)](../standard-library/map-operators.md#op_gt)|[operator > (multimap)](../standard-library/map-operators.md#op_gt_multimap)|Sprawdza, czy obiekt mapy lub multimap po lewej stronie operatora jest większy niż mapa lub multimap obiektu po prawej stronie.|
|[operator > = (map)](../standard-library/map-operators.md#op_gt_eq)|[operator > = (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|Sprawdza, czy obiekt mapy lub multimap po lewej stronie operatora jest większy niż lub równy obiektowi mapa lub multimap po prawej stronie.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|Mapy wersji|Multimap — wersja|Opis|
|-----------------|----------------------|-----------------|
|[swap (map)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap_multimap)|Zamienia elementy z dwóch map lub multimaps.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[value_compare, klasa](../standard-library/value-compare-class-map.md)|Dostarcza obiekt funkcji, która może porównać elementy mapy przez porównanie wartości ich kluczy, aby określić ich względną kolejność w mapie.|
|[map, klasa](../standard-library/map-class.md)|Używany do przechowywania i pobierania danych z kolekcji, w którym każdy z elementów ma unikatowy klucz za pomocą którego dane są automatycznie porządkowane.|
|[multimap, klasa](../standard-library/multimap-class.md)|Używany do przechowywania i pobierania danych z kolekcji, w którym każdy z elementów ma klucz za pomocą którego dane są automatycznie porządkowane i klucze nie muszą mieć unikatowe wartości.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
