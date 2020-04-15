---
title: duration_values — Struktura
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: e2c03b4540ea5f89843562d1310b71635b3bc259
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368743"
---
# <a name="duration_values-structure"></a>duration_values — Struktura

Zawiera określone wartości [duration](../standard-library/duration-class.md) parametru `Rep`szablonu czasu trwania .

## <a name="syntax"></a>Składnia

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Max](#max)|Statyczny. Określa górny limit dla wartości `Rep`typu .|
|[Min](#min)|Statyczny. Określa dolny limit dla wartości `Rep`typu .|
|[Zero](#zero)|Statyczny. Zwraca wartość `Rep(0)`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono>

**Przestrzeń nazw:** std::chrono

## <a name="duration_valuesmax"></a><a name="max"></a>duration_values::maks.

Metoda statyczna, która zwraca górną `Ref`granicę dla wartości typu .

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie `numeric_limits<Rep>::max()`zwraca .

### <a name="remarks"></a>Uwagi

Gdy `Rep` jest to typ zdefiniowany przez użytkownika, zwracana wartość musi być większa niż [duration_values::zero](#zero).

## <a name="duration_valuesmin"></a><a name="min"></a>duration_values::min

Metoda statyczna, która zwraca dolną `Ref`granicę dla wartości typu .

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie `numeric_limits<Rep>::lowest()`zwraca .

### <a name="remarks"></a>Uwagi

Gdy `Rep` jest to typ zdefiniowany przez użytkownika, zwracana wartość musi być mniejsza lub równa [duration_values::zero](#zero).

## <a name="duration_valueszero"></a><a name="zero"></a>duration_values::zero

Zwraca wartość `Rep(0)`.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Uwagi

Gdy `Rep` jest typem zdefiniowanym przez użytkownika, zwracana wartość musi reprezentować nieskończoność dodatku.

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<>chrono](../standard-library/chrono.md)
