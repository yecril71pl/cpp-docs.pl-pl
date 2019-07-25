---
title: allocator_newdel — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_newdel
- allocators/stdext::allocator_newdel
- stdext::allocators::allocator_newdel
helpviewer_keywords:
- stdext::allocators [C++], allocator_newdel
- stdext::allocator_newdel
ms.assetid: 62666cd2-3afe-49f7-9dd1-9bbbb154da98
ms.openlocfilehash: d49a1596371e4a69873b826d3e756f263539d034
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448309"
---
# <a name="allocatornewdel-class"></a>allocator_newdel — Klasa

Implementuje program przydzielający, który używa **operatora delete** do cofnięcia alokacji bloku pamięci i **operatora new** , aby przydzielić blok pamięci.

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class allocator_newdel;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Typ*|Typ elementów przyznanych przez alokatora.|

## <a name="remarks"></a>Uwagi

Makro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) przekazuje tę klasę jako parametr *name* w następującej instrukcji:`ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przypisania >

**Przestrzeń nazw:** stdext

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)
