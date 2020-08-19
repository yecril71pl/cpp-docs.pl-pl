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
ms.openlocfilehash: 30e0f7902a8af435b46aaedf0b38661b7a6604a8
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562600"
---
# <a name="allocator_newdel-class"></a>allocator_newdel — Klasa

Implementuje program przydzielający, który używa **operatora delete** do cofnięcia alokacji bloku pamięci i **operatora new** , aby przydzielić blok pamięci.

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class allocator_newdel;
```

### <a name="parameters"></a>Parametry

*Wprowadź*\
Typ elementów przyznanych przez alokatora.

## <a name="remarks"></a>Uwagi

Makro [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) przekazuje tę klasę jako parametr *name* w następującej instrukcji: `ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<allocators>

**Przestrzeń nazw:** stdext

## <a name="see-also"></a>Zobacz też

[\<allocators>](allocators-header.md)
