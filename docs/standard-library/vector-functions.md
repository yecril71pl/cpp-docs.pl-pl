---
title: '&lt;Wektor&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
caps.latest.revision: 10
manager: ghogen
ms.openlocfilehash: ec6b11a94fbf1b8b736db111a65cf720a1a9438c
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltvectorgt-functions"></a>&lt;Wektor&gt; funkcji


## <a name="swap"></a>  Swap

Zamienia elementy dwa wektory.

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Wektor zapewnianie elementów zamianę lub wektora, której elementy są wymienianych z tymi wektora `left`.

`left` Wektor, której elementy są wymienianych z tymi wektora `right`.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm specjalizowany na wektor klasy kontenera do wykonywania funkcji członkowskiej `left`. [Vector::swap](../standard-library/vector-class.md) *(prawo*). Te są wystąpieniami klasy częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonów są przeciążone w taki sposób, dopasowania szablonu z wywołaniem funkcji nie jest unikatowa, kompilator wybierze najbardziej specjalna wersja funkcji szablonu. Ogólne wersja funkcji szablonu **szablonu** \< **klasy T**> **void wymiany**( **T &**, **T &**), w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalna wersja w poszczególnych kontenerach jest znacznie szybsze może współpracować z reprezentacji wewnętrznej klasy kontenera.

### <a name="example"></a>Przykład

Zobacz przykład kodu dla funkcji członkowskiej [vector::swap](../standard-library/vector-class.md) na przykład, który używa wersji szablonu `swap`.

## <a name="see-also"></a>Zobacz także

[\<Wektor >](../standard-library/vector.md)<br/>
