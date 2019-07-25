---
title: duration_values — Struktura
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: ba4b202a5c8c6da742ac884bf58a5b8c55373d14
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454291"
---
# <a name="durationvalues-structure"></a>duration_values — Struktura

Zawiera określone wartości parametru `Rep`szablonu [czasu trwania](../standard-library/duration-class.md) .

## <a name="syntax"></a>Składnia

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[max](#max)|Ruchom. Określa górny limit wartości typu `Rep`.|
|[min](#min)|Ruchom. Określa dolny limit dla wartości typu `Rep`.|
|[zero](#zero)|Ruchom. Zwraca `Rep(0)`wartość.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<Chrono >

**Przestrzeń nazw:** std:: Chrono

## <a name="max"></a>duration_values:: max

Metoda statyczna zwracająca górną granicę dla wartości `Ref`typu.

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca wartość `numeric_limits<Rep>::max()`.

### <a name="remarks"></a>Uwagi

Gdy `Rep` jest typem zdefiniowanym przez użytkownika, zwracana wartość musi być większa niż [duration_values:: zero](#zero).

## <a name="min"></a>duration_values:: min

Metoda statyczna zwracająca dolną granicę dla wartości `Ref`typu.

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca wartość `numeric_limits<Rep>::lowest()`.

### <a name="remarks"></a>Uwagi

Gdy `Rep` jest typem zdefiniowanym przez użytkownika, zwracana wartość musi być mniejsza lub równa [duration_values:: zero](#zero).

## <a name="zero"></a>duration_values:: zero

Zwraca `Rep(0)`wartość.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Uwagi

Gdy `Rep` jest typem zdefiniowanym przez użytkownika, zwracana wartość musi reprezentować nieskończoność dodatku.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
