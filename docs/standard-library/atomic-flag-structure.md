---
title: atomic_flag — Struktura
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: 36944c3c3bdc58272d87bbcdfb119d1c52c43995
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447401"
---
# <a name="atomicflag-structure"></a>atomic_flag — Struktura

Opisuje obiekt, który niepodzielnie ustawia i czyści flagę **logiczną** . Operacje na flagach niepodzielnych są zawsze zablokowane.

## <a name="syntax"></a>Składnia

```cpp
struct atomic_flag;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Wyczyść](#clear)|Ustawia **wartość false**dla flagi przechowywanej.|
|[test_and_set](#test_and_set)|Ustawia wartość true dla flagi przechowywanej na wartość **prawda** .|

## <a name="remarks"></a>Uwagi

`atomic_flag`obiekty mogą być przesyłane do funkcji nienależących do elementu członkowskiego [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set)i [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Można je zainicjować przy użyciu wartości `ATOMIC_FLAG_INIT`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> niepodzielne

**Przestrzeń nazw:** std

## <a name="clear"></a>atomic_flag:: Clear

Ustawia flagę **logiczną** , która jest przechowywana `*this` w **wartości false**w ramach określonych ograniczeń [memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

*Porządek*\
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="test_and_set"></a>atomic_flag::test_and_set

Ustawia flagę **logiczną** , która jest przechowywana `*this` w **wartości true**w ramach określonych ograniczeń [memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

*Porządek*\
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Początkowa wartość flagi, która jest przechowywana w `*this`.

## <a name="see-also"></a>Zobacz także

[\<> niepodzielne](../standard-library/atomic.md)
