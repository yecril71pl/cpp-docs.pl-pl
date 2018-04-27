---
title: duration_values — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
dev_langs:
- C++
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a2cba8fd6fe3e4763e05dc0cc897e8a0b968d611
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="durationvalues-structure"></a>duration_values — Struktura

Udostępnia wartości określonej dla [czas trwania](../standard-library/duration-class.md) parametr szablonu `Rep`.

## <a name="syntax"></a>Składnia

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[max](#max)|Statyczna. Określa górne ograniczenie dla wartości typu `Rep`.|
|[min](#min)|Statyczna. Określa dolną granicę dla wartości typu `Rep`.|
|[zero](#zero)|Statyczna. Zwraca `Rep(0)`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono >

**Namespace:** std::chrono

## <a name="max"></a>  duration_values::Max

Metoda statyczna, która zwraca górną granicę dla wartości typu `Ref`.

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca `numeric_limits<Rep>::max()`.

### <a name="remarks"></a>Uwagi

Gdy `Rep` typu zdefiniowane przez użytkownika jest zwracana wartość musi być większa niż [duration_values::zero](#zero).

## <a name="min"></a>  duration_values::min

Statyczną metodę, która zwraca ograniczeniem dla wartości typu `Ref`.

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca `numeric_limits<Rep>::lowest()`.

### <a name="remarks"></a>Uwagi

Gdy `Rep` typu zdefiniowane przez użytkownika jest zwracana wartość musi być mniejsza lub równa [duration_values::zero](#zero).

## <a name="zero"></a>  duration_values::zero

Zwraca `Rep(0)`.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Uwagi

Gdy `Rep` jest typem użytkownika zwracana wartość musi reprezentować nieskończoności dodatku.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
