---
title: duration_values — Struktura
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: bc382bbc408b11cbc18210f3ab944dda39adc8f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413778"
---
# <a name="durationvalues-structure"></a>duration_values — Struktura

Zawiera określone wartości dla [czas trwania](../standard-library/duration-class.md) parametru szablonu `Rep`.

## <a name="syntax"></a>Składnia

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[max](#max)|Statyczne. Określa górną granicę dla wartości typu `Rep`.|
|[min](#min)|Statyczne. Określa dolną granicę dla wartości typu `Rep`.|
|[zero](#zero)|Statyczne. Zwraca `Rep(0)`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono >

**Namespace:** std::chrono

## <a name="max"></a>  duration_values::Max —

Metoda statyczna zwraca górną granicę wartości typu `Ref`.

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca `numeric_limits<Rep>::max()`.

### <a name="remarks"></a>Uwagi

Gdy `Rep` jest typ zdefiniowany przez użytkownika, zwracana wartość musi być większa niż [duration_values::zero](#zero).

## <a name="min"></a>  duration_values::min —

Metoda statyczna zwraca dolną granicę wartości typu `Ref`.

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca `numeric_limits<Rep>::lowest()`.

### <a name="remarks"></a>Uwagi

Gdy `Rep` jest typ zdefiniowany przez użytkownika, zwracana wartość musi być mniejsza lub równa [duration_values::zero](#zero).

## <a name="zero"></a>  duration_values::zero

Zwraca `Rep(0)`.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Uwagi

Gdy `Rep` jest typ zdefiniowany przez użytkownika, wartość zwracana musi reprezentować dodatek nieskończoności.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
