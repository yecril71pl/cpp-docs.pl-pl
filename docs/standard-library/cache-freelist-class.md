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
ms.openlocfilehash: 05260d6800597b64908ff0aeffac47b09fed9a0e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449687"
---
# <a name="cachefreelist-class"></a>cache_freelist — Klasa

Definiuje [Alokator bloku](../standard-library/allocators-header.md) , który przydziela i cofa alokacje bloków pamięci o pojedynczym rozmiarze.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Sz*|Liczba elementów w tablicy, która ma zostać przypisana.|
|*Maksymalna*|Maksymalna Klasa reprezentująca maksymalny rozmiar listy bezpłatnej. Może to być [max_fixed_size](../standard-library/max-fixed-size-class.md), [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md)lub [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Uwagi

Klasa szablonu cache_freelist przechowuje bezpłatną listę bloków pamięci o rozmiarze *sz*. Gdy lista bezpłatnych jest pełna, użyje **operatora delete** w celu cofnięcia alokacji bloków pamięci. Gdy lista bezpłatnych jest pusta, używa **operatora new** w celu przydzielenia nowych bloków pamięci. Maksymalny rozmiar bezpłatnej listy jest określany przez maksymalną klasę klasy przekazaną w parametrze *Max* .

Każdy blok pamięci zawiera *sz* bajtów użytecznej pamięci oraz dane, które **operator new** i **operator delete** wymagają.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[cache_freelist](#cache_freelist)|Konstruuje obiekt typu `cache_freelist`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[alokowany](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przypisania >

**Przestrzeń nazw:** stdext

## <a name="allocate"></a>cache_freelist:: Allocate

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

## <a name="cache_freelist"></a>cache_freelist::cache_freelist

Konstruuje obiekt typu `cache_freelist`.

```cpp
cache_freelist();
```

### <a name="remarks"></a>Uwagi

## <a name="deallocate"></a>cache_freelist::d eallocate

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

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)
