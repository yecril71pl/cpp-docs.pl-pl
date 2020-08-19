---
title: sync_per_container — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
ms.openlocfilehash: 51a88e6ec4eca693c652635e1574e3611d7217cd
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562106"
---
# <a name="sync_per_container-class"></a>sync_per_container — Klasa

Opisuje [filtr synchronizacji](../standard-library/allocators-header.md) , który zawiera oddzielny obiekt pamięci podręcznej dla każdego obiektu alokatora.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class sync_per_container
    : public Cache
```

### <a name="parameters"></a>Parametry

*Chow*\
Typ pamięci podręcznej skojarzonej z filtrem synchronizacji. Może to być [`cache_chunklist`](../standard-library/cache-chunklist-class.md) , [`cache_freelist`](../standard-library/cache-freelist-class.md) , lub [`cache_suballoc`](../standard-library/cache-suballoc-class.md) .

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[equals](#equals)|Porównuje dwie pamięci podręczne pod kątem równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<allocators>

**Przestrzeń nazw:** stdext

## <a name="sync_per_containerequals"></a><a name="equals"></a> sync_per_container:: Equals

Porównuje dwie pamięci podręczne pod kątem równości.

```cpp
bool equals(const sync_per_container<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

*Chow*\
Obiekt pamięci podręcznej filtru synchronizacji.

*Różnych*\
Obiekt pamięci podręcznej, który ma zostać porównany pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zawsze zwraca wartość **`false`** .

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[\<allocators>](../standard-library/allocators-header.md)
