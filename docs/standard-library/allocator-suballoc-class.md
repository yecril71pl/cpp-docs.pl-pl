---
title: allocator_suballoc — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
ms.openlocfilehash: 01d282585133d55ee3f7ec96c212705c2afca9d1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617423"
---
# <a name="allocator_suballoc-class"></a>allocator_suballoc — Klasa

Opisuje obiekt zarządzający alokacją i zwalnianiem magazynu dla *obiektów typu Type przy użyciu* pamięci podręcznej typu [cache_suballoc](cache-suballoc-class.md).

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

Makro [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) przekazuje tę klasę jako parametr *name* w następującej instrukcji:`ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<allocators>

**Przestrzeń nazw:** stdext

## <a name="see-also"></a>Zobacz też

[\<allocators>](allocators-header.md)
