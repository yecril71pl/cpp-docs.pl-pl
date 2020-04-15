---
title: cache_chunklist — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
ms.openlocfilehash: d0dd6176a34bd625069511106c491225d1467d08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366753"
---
# <a name="cache_chunklist-class"></a>cache_chunklist — Klasa

Definiuje [alokator bloków,](../standard-library/allocators-header.md) który przydziela i przydziela bloki pamięci o jednym rozmiarze.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Sz*|Liczba elementów w tablicy, które mają zostać przydzielone.|

## <a name="remarks"></a>Uwagi

Ten szablon klasy używa **operatora nowy** przydzielić fragmenty pamięci pierwotnej, suballocating bloków przydzielić magazyn dla bloku pamięci w razie potrzeby; przechowuje cofnięte bloki pamięci w osobnej bezpłatnej liście dla każdego fragmentu i używa **usuwania operatora** do usuwania alokacji fragmentu, gdy żaden z jego bloków pamięci nie jest używany.

Każdy blok pamięci zawiera *bajty sz* pamięci użytkowej i wskaźnik do fragmentu, który należy do. Każdy fragment `Nelts` zawiera bloki pamięci, trzy wskaźniki, int i dane, które **operator nowy** i **operator usunąć** wymagają.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[cache_chunklist](#cache_chunklist)|Konstruuje obiekt `cache_chunklist`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[Deallocate](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, począwszy od określonej pozycji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<alokatory>

**Obszar nazw:** stdext

## <a name="cache_chunklistallocate"></a><a name="allocate"></a>cache_chunklist::przydziel

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

## <a name="cache_chunklistcache_chunklist"></a><a name="cache_chunklist"></a>cache_chunklist::cache_chunklist

Konstruuje obiekt `cache_chunklist`typu .

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Uwagi

## <a name="cache_chunklistdeallocate"></a><a name="deallocate"></a>cache_chunklist::dlokalizuj

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
