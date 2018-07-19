---
title: cache_chunklist — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 808340df89bb548fee57604f25409c117933cc4e
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953263"
---
# <a name="cachechunklist-class"></a>cache_chunklist — Klasa

Definiuje [block alokatora](../standard-library/allocators-header.md) który przydziela i zwalnia bloki pamięci o rozmiarze jednego.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Sz*|Liczba elementów w tablicy do przydzielenia.|

## <a name="remarks"></a>Uwagi

Korzysta z tej klasy szablonu **nowy operator** można przydzielić pamięci surowej fragmentów, blokuje suballocating do przydzielania pamięci dla bloku pamięci, w razie; bloki cofnięcia przydziału pamięci są przechowywane w osobnej listy bezpłatne dla każdego fragmentu i używa **operatora delete** można cofnąć alokacji fragment, gdy żaden z jej bloki pamięci jest w użyciu.

Każdy blok pamięci przechowuje *Sz* bajtach dostępnej pamięci i wskaźnik fragmentów, do którego on należy. Każdy fragment zawiera `Nelts` bloki pamięci, trzy wskaźniki, int i dane, **nowy operator** i **operatora delete** wymagają.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[cache_chunklist](#cache_chunklist)|Tworzy obiekt typu `cache_chunklist`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[Cofnij Przydział](#deallocate)|Zwalnia określoną liczbę obiektów z pamięci masowej rozpoczynający się od określonej pozycji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="allocate"></a>  cache_chunklist::allocate

Przydziela blok pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Liczba*|Liczba elementów w tablicy do przydzielenia.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielonego obiektu.

### <a name="remarks"></a>Uwagi

## <a name="cache_chunklist"></a>  cache_chunklist::cache_chunklist

Tworzy obiekt typu `cache_chunklist`.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Uwagi

## <a name="deallocate"></a>  cache_chunklist::deallocate

Zwalnia określoną liczbę obiektów z pamięci masowej rozpoczynający się od określonej pozycji.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik do pierwszego obiektu można cofnąć przydziału z magazynu.|
|*Liczba*|Liczba obiektów, które można cofnąć przydziału z magazynu.|

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
