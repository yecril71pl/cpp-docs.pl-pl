---
title: atomic_flag, struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
dev_langs:
- C++
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6a5162057944ac3d91d2465cfefe99c68dd5fb3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961418"
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

*Kolejność* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="test_and_set"></a>  atomic_flag::test_and_set —

Zestawy **bool** flagę, która jest przechowywana w `*this` do **true**, w ramach określonych [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

*Kolejność* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Wartość początkowa flagi, która jest przechowywana w `*this`.

## <a name="see-also"></a>Zobacz także

[\<niepodzielne >](../standard-library/atomic.md)<br/>
