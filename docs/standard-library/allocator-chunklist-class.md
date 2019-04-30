---
title: allocator_chunklist — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_chunklist
- allocators/stdext::allocators::allocator_chunklist
helpviewer_keywords:
- stdext::allocator_chunklist
- stdext::allocators [C++], allocator_chunklist
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
ms.openlocfilehash: d52eeb1f34938958c9716692ed6bbd7d830c93b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411061"
---
# <a name="allocatorchunklist-class"></a>allocator_chunklist — Klasa

Opisuje obiekt, który zarządza alokacją pamięci i zwalnianiem dla obiektów przy użyciu pamięci podręcznej typu [cache_chunklist](../standard-library/cache-chunklist-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class allocator_chunklist;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Typ*|Typ elementów przydzielonej przez alokator.|

## <a name="remarks"></a>Uwagi

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) — makro przekazuje tę klasę jako *nazwa* parametru w następującej instrukcji: `ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist);`

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)<br/>
