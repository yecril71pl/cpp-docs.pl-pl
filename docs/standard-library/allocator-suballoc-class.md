---
title: allocator_suballoc — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
ms.openlocfilehash: 3e5b69ef3f47a173ef768283bbae4f6e3b5f5190
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458142"
---
# <a name="allocatorsuballoc-class"></a>allocator_suballoc — Klasa

Opisuje obiekt zarządzający alokacją i zwalnianiem magazynu dla obiektów typu Type *przy użyciu* pamięci podręcznej typu [cache_suballoc](../standard-library/cache-suballoc-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class allocator_suballoc;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Typ*|Typ elementów przyznanych przez alokatora.|

## <a name="remarks"></a>Uwagi

Makro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) przekazuje tę klasę jako parametr *name* w następującej instrukcji:`ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przypisania >

**Przestrzeń nazw:** stdext

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)
