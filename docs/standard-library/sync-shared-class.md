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
ms.openlocfilehash: 9f1a984d38bed9dd3795164e355c7ccac100ae6b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232888"
---
# <a name="sync_shared-class"></a>sync_shared — Klasa

Opisuje [filtr synchronizacji](../standard-library/allocators-header.md) , który używa elementu mutex do kontrolowania dostępu do obiektu pamięci podręcznej, który jest współużytkowany przez wszystkie przypisania.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class sync_shared
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Cache*|Typ pamięci podręcznej skojarzonej z filtrem synchronizacji. Może to być [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md)lub [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[alokowany](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.|
|[równa się](#equals)|Porównuje dwie pamięci podręczne pod kątem równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<allocators>

**Przestrzeń nazw:** stdext

## <a name="sync_sharedallocate"></a><a name="allocate"></a>sync_shared:: Allocate

Przydziela blok pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*liczbą*|Liczba elementów w tablicy, która ma zostać przypisana.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielony obiekt.

### <a name="remarks"></a>Uwagi

Funkcja członkowska blokuje mutex, wywołuje `cache.allocate(count)` , odblokowuje element mutex i zwraca wynik wcześniejszego wywołania do `cache.allocate(count)` . `cache`reprezentuje bieżący obiekt pamięci podręcznej.

## <a name="sync_shareddeallocate"></a><a name="deallocate"></a>sync_shared::d eallocate

Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik do pierwszego obiektu do cofnięcia przydziału z magazynu.|
|*liczbą*|Liczba obiektów do cofnięcia przydziału z magazynu.|

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska blokuje mutex, wywołuje `cache.deallocate(ptr, count)` , gdzie `cache` reprezentuje obiekt pamięci podręcznej, a następnie odblokowuje element mutex.

## <a name="sync_sharedequals"></a><a name="equals"></a>sync_shared:: Equals

Porównuje dwie pamięci podręczne pod kątem równości.

```cpp
bool equals(const sync_shared<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Cache*|Typ pamięci podręcznej skojarzonej z filtrem synchronizacji.|
|*Inne problemy*|Pamięć podręczna do porównania pod kątem równości.|

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wynik `cache.equals(Other.cache)` , gdzie `cache` reprezentuje obiekt pamięci podręcznej, jest **`true`** ; w przeciwnym razie, **`false`** .

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)
