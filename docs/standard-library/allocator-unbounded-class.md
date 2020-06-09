---
title: allocator_unbounded — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: ba4c8b774752b327f5a4ede84fa804888cfd31d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617392"
---
# <a name="allocator_unbounded-class"></a>allocator_unbounded — Klasa

Opisuje obiekt, który zarządza alokacją i zwalnianiem magazynu dla *obiektów typu Type przy użyciu* pamięci podręcznej typu [cache_freelist](cache-freelist-class.md) o długości zarządzanej przez [max_unbounded](max-unbounded-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Typ*|Typ elementów przyznanych przez alokatora.|

## <a name="remarks"></a>Uwagi

Makro [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) przekazuje tę klasę jako parametr *name* w następującej instrukcji:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<allocators>

**Przestrzeń nazw:** stdext

## <a name="see-also"></a>Zobacz też

[\<allocators>](allocators-header.md)
