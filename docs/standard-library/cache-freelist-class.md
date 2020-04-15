---
title: cache_freelist — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
ms.openlocfilehash: d757909d3e54fed35bf42b943b9f9740dffee115
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366736"
---
# <a name="cache_freelist-class"></a>cache_freelist — Klasa

Definiuje [alokator bloków,](../standard-library/allocators-header.md) który przydziela i przydziela bloki pamięci o jednym rozmiarze.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Sz*|Liczba elementów w tablicy, które mają zostać przydzielone.|
|*Max*|Maksymalna klasa reprezentująca maksymalny rozmiar listy bezpłatnych. Może to być [max_fixed_size,](../standard-library/max-fixed-size-class.md) [max_none,](../standard-library/max-none-class.md) [max_unbounded](../standard-library/max-unbounded-class.md)lub [max_variable_size.](../standard-library/max-variable-size-class.md)|

## <a name="remarks"></a>Uwagi

Szablon klasy cache_freelist przechowuje bezpłatną listę bloków pamięci o rozmiarze *Sz*. Gdy wolna lista jest pełna używa **operatora delete** do usuwania alokacji bloków pamięci. Gdy lista wolny jest pusta używa **operatora nowy** przydzielić nowe bloki pamięci. Maksymalny rozmiar listy wolnych jest określany przez klasę max przeszedł w *Max* parametru.

Każdy blok pamięci przechowuje *bajty sz* pamięci użytkowej i danych, które **operator nowy** i **operator usunąć** wymagają.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[cache_freelist](#cache_freelist)|Konstruuje obiekt `cache_freelist`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[Deallocate](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, począwszy od określonej pozycji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<alokatory>

**Obszar nazw:** stdext

## <a name="cache_freelistallocate"></a><a name="allocate"></a>cache_freelist::przydziel

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

## <a name="cache_freelistcache_freelist"></a><a name="cache_freelist"></a>cache_freelist::cache_freelist

Konstruuje obiekt `cache_freelist`typu .

```cpp
cache_freelist();
```

### <a name="remarks"></a>Uwagi

## <a name="cache_freelistdeallocate"></a><a name="deallocate"></a>cache_freelist::dlokalizuj

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

## <a name="see-also"></a>Zobacz też

[\<>alokatorów](../standard-library/allocators-header.md)
