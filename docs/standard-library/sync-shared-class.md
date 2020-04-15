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
ms.openlocfilehash: 029edea59f29534491232d5d99353ccb093447bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376534"
---
# <a name="sync_shared-class"></a>sync_shared — Klasa

W tym artykule opisano [filtr synchronizacji,](../standard-library/allocators-header.md) który używa obiektu mutex do kontrolowania dostępu do obiektu pamięci podręcznej, który jest współużytkowany przez wszystkie alokatory.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class sync_shared
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Pamięć podręczna*|Typ pamięci podręcznej skojarzonej z filtrem synchronizacji. Może to być [cache_chunklist,](../standard-library/cache-chunklist-class.md) [cache_freelist](../standard-library/cache-freelist-class.md)lub [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[Deallocate](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, począwszy od określonej pozycji.|
|[equals](#equals)|Porównuje dwie pamięci podręczne dla równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<alokatory>

**Obszar nazw:** stdext

## <a name="sync_sharedallocate"></a><a name="allocate"></a>sync_shared::przydziel

Przydziela blok pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Liczba*|Liczba elementów w tablicy, które mają zostać przydzielone.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielonego obiektu.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego blokuje obiekt `cache.allocate(count)`mutex, wywołuje, odblokowuje obiekt mutex i zwraca wynik wcześniejszego wywołania . `cache.allocate(count)` `cache`reprezentuje bieżący obiekt pamięci podręcznej.

## <a name="sync_shareddeallocate"></a><a name="deallocate"></a>sync_shared::dlokalizuj

Zwalnia określoną liczbę obiektów z magazynu, począwszy od określonej pozycji.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Ptr*|Wskaźnik do pierwszego obiektu, który ma zostać cofnięty z magazynu.|
|*Liczba*|Liczba obiektów, które mają zostać przydzielone z magazynu.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego blokuje `cache.deallocate(ptr, count)`obiektu `cache` mutex, wywołuje , gdzie reprezentuje obiekt pamięci podręcznej, a następnie odblokowuje obiektu mutex.

## <a name="sync_sharedequals"></a><a name="equals"></a>sync_shared::równa się

Porównuje dwie pamięci podręczne dla równości.

```cpp
bool equals(const sync_shared<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Pamięć podręczna*|Typ pamięci podręcznej skojarzonej z filtrem synchronizacji.|
|*Inne*|Pamięć podręczna do porównania dla równości.|

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli `cache.equals(Other.cache)`wynik `cache` , gdzie reprezentuje obiekt pamięci podręcznej, jest **true;** w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[\<>alokatorów](../standard-library/allocators-header.md)
