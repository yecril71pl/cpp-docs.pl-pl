---
title: network_link_registry — Klasa
ms.date: 11/04/2016
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
ms.openlocfilehash: 18fabd0e741c144201f299271cdd01eb9ac55fac
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222683"
---
# <a name="network_link_registry-class"></a>network_link_registry — Klasa

`network_link_registry`Abstrakcyjna klasa bazowa zarządza łączami między blokami źródłowymi i docelowymi.

## <a name="syntax"></a>Składnia

```cpp
template<class _Block>
class network_link_registry;
```

### <a name="parameters"></a>Parametry

*_Block*<br/>
Typ danych bloku przechowywanych w `network_link_registry` .

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`const_pointer`|Typ, który dostarcza wskaźnik do **`const`** elementu w `network_link_registry` obiekcie.|
|`const_reference`|Typ, który zawiera odwołanie do **`const`** elementu przechowywanego w `network_link_registry` obiekcie na potrzeby odczytywania i wykonywania operacji const.|
|`iterator`|Typ, który dostarcza iterator, który może odczytać lub zmodyfikować dowolny element w `network_link_registry` obiekcie.|
|`type`|Typ, który reprezentuje typ bloku przechowywany w `network_link_registry` obiekcie.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[add](#add)|Gdy jest zastępowany w klasie pochodnej, dodaje łącze do `network_link_registry` obiektu.|
|[zaczną](#begin)|Gdy jest zastępowany w klasie pochodnej, zwraca iterator do pierwszego elementu w `network_link_registry` obiekcie.|
|[wyświetlana](#contains)|Gdy jest zastępowany w klasie pochodnej, przeszukuje `network_link_registry` obiekt pod kątem określonego bloku.|
|[liczbą](#count)|Gdy jest zastępowany w klasie pochodnej, zwraca liczbę elementów w `network_link_registry` obiekcie.|
|[usuwa](#remove)|Gdy jest zastępowany w klasie pochodnej, usuwa określony blok z `network_link_registry` obiektu.|

## <a name="remarks"></a>Uwagi

`network link registry`Nie jest to bezpieczny dostęp do współbieżności.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`network_link_registry`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="add"></a><a name="add"></a>dodana

Gdy jest zastępowany w klasie pochodnej, dodaje łącze do `network_link_registry` obiektu.

```cpp
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać dodany.

## <a name="begin"></a><a name="begin"></a>zaczną

Gdy jest zastępowany w klasie pochodnej, zwraca iterator do pierwszego elementu w `network_link_registry` obiekcie.

```cpp
virtual iterator begin() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Iterator odnoszący się do pierwszego elementu w `network_link_registry` obiekcie.

### <a name="remarks"></a>Uwagi

Końcowy stan iteratora jest wskazywany przez `NULL` łącze.

## <a name="contains"></a><a name="contains"></a>wyświetlana

Gdy jest zastępowany w klasie pochodnej, przeszukuje `network_link_registry` obiekt pod kątem określonego bloku.

```cpp
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który jest wyszukiwany w `network_link_registry` obiekcie.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli blok został znaleziony, **`false`** w przeciwnym razie.

## <a name="count"></a><a name="count"></a>liczbą

Gdy jest zastępowany w klasie pochodnej, zwraca liczbę elementów w `network_link_registry` obiekcie.

```cpp
virtual size_t count() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w `network_link_registry` obiekcie.

## <a name="remove"></a><a name="remove"></a>usuwa

Gdy jest zastępowany w klasie pochodnej, usuwa określony blok z `network_link_registry` obiektu.

```cpp
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do usunięcia bloku, jeśli został znaleziony.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli łącze zostało odnalezione i usunięte, **`false`** w przeciwnym razie.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa single_link_registry](single-link-registry-class.md)<br/>
[Klasa multi_link_registry](multi-link-registry-class.md)
