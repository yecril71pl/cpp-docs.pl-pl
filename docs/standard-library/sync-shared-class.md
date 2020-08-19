---
title: sync_shared — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_shared
- allocators/stdext::sync_shared::allocate
- allocators/stdext::sync_shared::deallocate
- allocators/stdext::sync_shared::equals
helpviewer_keywords:
- stdext::sync_shared
- stdext::sync_shared [C++], allocate
- stdext::sync_shared [C++], deallocate
- stdext::sync_shared [C++], equals
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
ms.openlocfilehash: 8b516762f0ae2f6d25c4d5109cbc9870f1254b89
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562080"
---
# <a name="sync_shared-class"></a>sync_shared — Klasa

Opisuje [filtr synchronizacji](../standard-library/allocators-header.md) , który używa elementu mutex do kontrolowania dostępu do obiektu pamięci podręcznej, który jest współużytkowany przez wszystkie przypisania.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class sync_shared
```

### <a name="parameters"></a>Parametry

*Chow*\
Typ pamięci podręcznej skojarzonej z filtrem synchronizacji. Może to być [`cache_chunklist`](../standard-library/cache-chunklist-class.md) , [`cache_freelist`](../standard-library/cache-freelist-class.md) , lub [`cache_suballoc`](../standard-library/cache-suballoc-class.md) .

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[alokowany](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.|
|[equals](#equals)|Porównuje dwie pamięci podręczne pod kątem równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<allocators>

**Przestrzeń nazw:** stdext

## <a name="sync_sharedallocate"></a><a name="allocate"></a> sync_shared:: Allocate

Przydziela blok pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

*liczbą*\
Liczba elementów w tablicy, która ma zostać przypisana.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielony obiekt.

### <a name="remarks"></a>Uwagi

Funkcja członkowska blokuje mutex, wywołuje `cache.allocate(count)` , odblokowuje element mutex i zwraca wynik wcześniejszego wywołania do `cache.allocate(count)` . `cache` reprezentuje bieżący obiekt pamięci podręcznej.

## <a name="sync_shareddeallocate"></a><a name="deallocate"></a> sync_shared::d eallocate

Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do pierwszego obiektu do cofnięcia przydziału z magazynu.

*liczbą*\
Liczba obiektów do cofnięcia przydziału z magazynu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska blokuje mutex, wywołuje `cache.deallocate(ptr, count)` , gdzie `cache` reprezentuje obiekt pamięci podręcznej, a następnie odblokowuje element mutex.

## <a name="sync_sharedequals"></a><a name="equals"></a> sync_shared:: Equals

Porównuje dwie pamięci podręczne pod kątem równości.

```cpp
bool equals(const sync_shared<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

*Chow*\
Typ pamięci podręcznej skojarzonej z filtrem synchronizacji.

*Różnych*\
Pamięć podręczna do porównania pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wynik `cache.equals(Other.cache)` , gdzie `cache` reprezentuje obiekt pamięci podręcznej, jest **`true`** ; w przeciwnym razie, **`false`** .

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[\<allocators>](../standard-library/allocators-header.md)
