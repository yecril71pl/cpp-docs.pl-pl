---
title: allocator_unbounded — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: 4e5bf54b386a3c3fe4e2604a78437275707acbfd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586293"
---
# <a name="allocatorunbounded-class"></a>allocator_unbounded — Klasa

Opisuje obiekt, który zarządza alokacją pamięci i zwalnianiem dla obiektów typu *typu* używanie pamięci podręcznej typu [cache_freelist](../standard-library/cache-freelist-class.md) o długości zarządza [max_unbounded —](../standard-library/max-unbounded-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Typ*|Typ elementów przydzielonej przez alokator.|

## <a name="remarks"></a>Uwagi

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) — makro przekazuje tę klasę jako *nazwa* parametru w następującej instrukcji: `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
