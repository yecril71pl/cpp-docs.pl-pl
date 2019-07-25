---
title: '&lt;zmapować&gt;'
ms.date: 11/04/2016
f1_keywords:
- <map>
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
ms.openlocfilehash: 3c3c7fc34e75772c10ba39ecc51f6d2ac59d7ad5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456290"
---
# <a name="ltmapgt"></a>&lt;zmapować&gt;

Definiuje mapowania klas szablonu kontenera i multimap oraz ich szablony pomocnicze.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<Mapuj >

**Przestrzeń nazw:** std

> [!NOTE]
> Biblioteka > `#include <initializer_list>` map również używa instrukcji. \<

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|Wersja mapy|Wersja multimap|Opis|
|-----------------|----------------------|-----------------|
|[operator! = (map)](../standard-library/map-operators.md#op_neq)|[operator! = (multimap)](../standard-library/map-operators.md#op_neq)|Testuje, czy obiekt mapy lub multimap po lewej stronie operatora nie jest równy obiektowi mapy lub multimap po prawej stronie.|
|[< operatora (mapa)](../standard-library/map-operators.md#op_eq_eq)|[< operatora (multimap)](../standard-library/map-operators.md#op_eq_eq)|Testuje, czy obiekt mapy lub multimap po lewej stronie operatora jest mniejszy niż obiekt mapy lub multimap po prawej stronie.|
|[operator < = (map)](../standard-library/map-operators.md#op_lt)|[operator\<= (multimap)](../standard-library/map-operators.md#op_lt)|Testuje, czy obiekt mapy lub multimap po lewej stronie operatora jest mniejszy niż lub równy obiektowi mapy lub multimap po prawej stronie.|
|[operator== (map)](../standard-library/map-operators.md#op_eq_eq)|[operator== (multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|Testuje, czy obiekt mapy lub multimap po lewej stronie operatora jest równy obiektowi mapy lub multimap po prawej stronie.|
|[> operatora (mapa)](../standard-library/map-operators.md#op_gt)|[> operatora (multimap)](../standard-library/map-operators.md#op_gt_multimap)|Testuje, czy obiekt mapy lub multimap po lewej stronie operatora jest większy niż obiekt mapy lub multimap po prawej stronie.|
|[operator > = (map)](../standard-library/map-operators.md#op_gt_eq)|[> operatora = (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|Testuje, czy obiekt mapy lub multimap po lewej stronie operatora jest większy niż lub równy obiektowi mapy lub multimap po prawej stronie.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|Wersja mapy|Wersja multimap|Opis|
|-----------------|----------------------|-----------------|
|[Zamień (mapa)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap_multimap)|Wymienia elementy dwóch map lub wielomap.|

### <a name="classes"></a>Klasy

|||
|-|-|
|[value_compare, klasa](../standard-library/value-compare-class-map.md)|Udostępnia obiekt funkcji, który może porównać elementy mapy przez porównanie wartości ich kluczy w celu określenia ich względnej kolejności w mapie.|
|[map, klasa](../standard-library/map-class.md)|Używany do przechowywania i pobierania danych z kolekcji, w której każdy element ma unikatowy klucz, z którym dane są automatycznie uporządkowane.|
|[multimap, klasa](../standard-library/multimap-class.md)|Używany do przechowywania i pobierania danych z kolekcji, w której każdy element ma klucz, z którym dane są automatycznie uporządkowane i klucze nie muszą mieć unikatowych wartości.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
