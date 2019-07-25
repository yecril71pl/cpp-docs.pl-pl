---
title: allocator_fixed_size — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_fixed_size
- allocators/stdext::allocator_fixed_size
- stdext::allocators::allocator_fixed_size
helpviewer_keywords:
- stdext::allocators [C++], allocator_fixed_size
- stdext::allocator_fixed_size
ms.assetid: 138f3ef8-b0b3-49c3-9486-58f2213c172f
ms.openlocfilehash: 5ee506838ea723b82f04bba301c19c0149d986bf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451000"
---
# <a name="allocatorfixedsize-class"></a>allocator_fixed_size — Klasa

Opisuje obiekt, który zarządza alokacją i zwalnianiem magazynu dla obiektów typu *typu za pomocą* pamięci podręcznej typu [cache_freelist](../standard-library/cache-freelist-class.md) o długości zarządzanej przez [max_fixed_size](../standard-library/max-fixed-size-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class allocator_fixed_size;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Typ*|Typ elementów przyznanych przez alokatora.|

## <a name="remarks"></a>Uwagi

Makro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) przekazuje tę klasę jako parametr *name* w następującej instrukcji:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_fixed_size<10>), SYNC_DEFAULT, allocator_fixed_size);`

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przypisania >

**Przestrzeń nazw:** stdext

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)
