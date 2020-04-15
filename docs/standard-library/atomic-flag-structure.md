---
title: atomic_flag — Struktura
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: ad4b6dcaf6db1a8abe5b81b4d630e84b54fbaa63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376868"
---
# <a name="atomic_flag-structure"></a>atomic_flag — Struktura

Opisuje obiekt, który niepodzielnie ustawia i czyści **bool** flagi. Operacje na flagach atomowych są zawsze bez blokady.

## <a name="syntax"></a>Składnia

```cpp
struct atomic_flag;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Wyczyść](#clear)|Ustawia przechowywaną flagę na **false**.|
|[test_and_set](#test_and_set)|Ustawia przechowywaną flagę na **wartość true** i zwraca początkową wartość flagi.|

## <a name="remarks"></a>Uwagi

`atomic_flag`obiekty mogą być przekazywane do funkcji niebędących [członkami, atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear) [, atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set)i [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Można je zainicjować przy `ATOMIC_FLAG_INIT`użyciu wartości .

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> atomowy

**Przestrzeń nazw:** std

## <a name="atomic_flagclear"></a><a name="clear"></a>atomic_flag::wyczyść

Ustawia flagę **bool,** `*this` która jest przechowywana w **false,** w ramach określonych [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczeń.

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

*Zamówienia*\
[A memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flagtest_and_set"></a><a name="test_and_set"></a>atomic_flag::test_and_set

Ustawia flagę **bool,** `*this` która jest przechowywana w **true**, w ramach określonych [ograniczeń memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

*Zamówienia*\
[A memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Wartość początkowa flagi przechowywanej `*this`w pliku .

## <a name="see-also"></a>Zobacz też

[\<>atomowy](../standard-library/atomic.md)
