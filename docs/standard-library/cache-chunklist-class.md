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
ms.openlocfilehash: 035e5153b4e4c84743a64bcc9cec24920a6a0336
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688363"
---
# <a name="cache_chunklist-class"></a>cache_chunklist — Klasa

Definiuje [Alokator bloku](../standard-library/allocators-header.md) , który przydziela i cofa alokacje bloków pamięci o pojedynczym rozmiarze.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Sz*|Liczba elementów w tablicy, która ma zostać przypisana.|

## <a name="remarks"></a>Uwagi

Ten szablon klasy używa **operatora new** do przydzielania fragmentów pamięci nieprzetworzonej, przydzielenia bloków w celu przydzielania magazynu dla bloku pamięci w razie potrzeby; przechowuje cofnięte alokacje bloków pamięci na oddzielnej liście wolnej dla każdego fragmentu i używa **operatora delete** w celu cofnięcia przydziału fragmentu, gdy żaden z jego bloków pamięci nie jest używany.

Każdy blok pamięci zawiera *sz* bajtów użytecznej pamięci i wskaźnik do fragmentu, do którego należy. Każdy fragment zawiera `Nelts` bloków pamięci, trzy wskaźniki, int i dane, które **operator new** i **operator delete** wymagają.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[cache_chunklist](#cache_chunklist)|Konstruuje obiekt typu `cache_chunklist`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[alokowany](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<allocators >

**Przestrzeń nazw:** stdext

## <a name="allocate"></a>cache_chunklist:: Allocate

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

## <a name="cache_chunklist"></a>cache_chunklist::cache_chunklist

Konstruuje obiekt typu `cache_chunklist`.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Uwagi

## <a name="deallocate"></a>cache_chunklist::d eallocate

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

[\<allocators >](../standard-library/allocators-header.md)
