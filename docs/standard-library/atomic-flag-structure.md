---
title: atomic_flag — Struktura
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: 13af0c26b765aa7ebbbd1ec22b5a0ed1b8cce0ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550426"
---
# <a name="atomicflag-structure"></a>atomic_flag — Struktura

Opisuje obiekt, który niepodzielnie Ustawia lub usuwa **bool** flagi. Operacje na flagach atomowych są zawsze wolne od blokady.

## <a name="syntax"></a>Składnia

```cpp
struct atomic_flag;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Usuń zaznaczenie](#clear)|Ustawia przechowywany znacznik na **false**.|
|[test_and_set](#test_and_set)|Ustawia przechowywany znacznik na **true** i zwraca wartość początkową znacznika.|

## <a name="remarks"></a>Uwagi

`atomic_flag` obiekty mogą być przekazywane do funkcji nieczłonkowskich [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set), i [atomic _flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Mogą one być inicjowane przy użyciu wartości `ATOMIC_FLAG_INIT`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<atomic >

**Namespace:** standardowe

## <a name="clear"></a>  atomic_flag::Clear —

Zestawy **bool** flagę, która jest przechowywana w `*this` do **false**, w ramach określonych [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

*Kolejność*<br/>
A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="test_and_set"></a>  atomic_flag::test_and_set —

Zestawy **bool** flagę, która jest przechowywana w `*this` do **true**, w ramach określonych [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

*Kolejność*<br/>
A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Wartość początkowa flagi, która jest przechowywana w `*this`.

## <a name="see-also"></a>Zobacz także

[\<niepodzielne >](../standard-library/atomic.md)<br/>
