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
ms.openlocfilehash: d050a127fe3e62bf8f4eb4ce56fe25e33f88c041
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535889"
---
# <a name="allocatorfixedsize-class"></a>allocator_fixed_size — Klasa

Opisuje obiekt, który zarządza alokacją pamięci i zwalnianiem dla obiektów typu *typu* używanie pamięci podręcznej typu [cache_freelist](../standard-library/cache-freelist-class.md) o długości zarządza [max_fixed_size —](../standard-library/max-fixed-size-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class allocator_fixed_size;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Typ*|Typ elementów przydzielonej przez alokator.|

## <a name="remarks"></a>Uwagi

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) — makro przekazuje tę klasę jako *nazwa* parametru w następującej instrukcji: `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_fixed_size<10>), SYNC_DEFAULT, allocator_fixed_size);`

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
