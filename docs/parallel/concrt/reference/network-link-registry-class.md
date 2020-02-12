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
ms.openlocfilehash: 430190c11ec06a4f26eb9d8c4237552848420ad7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138889"
---
# <a name="network_link_registry-class"></a>network_link_registry — Klasa

Abstrakcyjna klasa bazowa `network_link_registry` zarządza łączami między blokami źródłowymi i docelowymi.

## <a name="syntax"></a>Składnia

```cpp
template<class _Block>
class network_link_registry;
```

### <a name="parameters"></a>Parametry

*_Block*<br/>
Typ danych bloku przechowywanych w `network_link_registry`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`const_pointer`|Typ, który dostarcza wskaźnik do elementu `const` w obiekcie `network_link_registry`.|
|`const_reference`|Typ, który dostarcza odwołanie do `const` elementu przechowywanego w obiekcie `network_link_registry` do odczytu i wykonywania operacji const.|
|`iterator`|Typ, który dostarcza iterator, który może odczytać lub zmodyfikować dowolny element w obiekcie `network_link_registry`.|
|`type`|Typ, który reprezentuje typ bloku przechowywany w obiekcie `network_link_registry`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[add](#add)|Gdy jest zastępowany w klasie pochodnej, dodaje łącze do obiektu `network_link_registry`.|
|[zaczną](#begin)|Gdy jest zastępowany w klasie pochodnej, zwraca iterator do pierwszego elementu w obiekcie `network_link_registry`.|
|[wyświetlana](#contains)|Gdy jest zastępowany w klasie pochodnej, wyszukuje `network_link_registry` obiektu dla określonego bloku.|
|[count](#count)|Gdy jest zastępowany w klasie pochodnej, zwraca liczbę elementów w obiekcie `network_link_registry`.|
|[remove](#remove)|Gdy jest zastępowany w klasie pochodnej, usuwa określony blok z obiektu `network_link_registry`.|

## <a name="remarks"></a>Uwagi

`network link registry` nie jest bezpieczna do jednoczesnego dostępu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`network_link_registry`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="add"></a>dodana

Gdy jest zastępowany w klasie pochodnej, dodaje łącze do obiektu `network_link_registry`.

```cpp
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać dodany.

## <a name="begin"></a>zaczną

Gdy jest zastępowany w klasie pochodnej, zwraca iterator do pierwszego elementu w obiekcie `network_link_registry`.

```cpp
virtual iterator begin() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Iterator odnoszący się do pierwszego elementu w obiekcie `network_link_registry`.

### <a name="remarks"></a>Uwagi

Końcowy stan iteratora jest wskazywany przez łącze `NULL`.

## <a name="contains"></a>wyświetlana

Gdy jest zastępowany w klasie pochodnej, wyszukuje `network_link_registry` obiektu dla określonego bloku.

```cpp
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który jest wyszukiwany w obiekcie `network_link_registry`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli blok został znaleziony, w przeciwnym razie **zwraca wartość false** .

## <a name="count"></a>liczbą

Gdy jest zastępowany w klasie pochodnej, zwraca liczbę elementów w obiekcie `network_link_registry`.

```cpp
virtual size_t count() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Liczba elementów w obiekcie `network_link_registry`.

## <a name="remove"></a>usuwa

Gdy jest zastępowany w klasie pochodnej, usuwa określony blok z obiektu `network_link_registry`.

```cpp
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do usunięcia bloku, jeśli został znaleziony.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli łącze zostało znalezione i usunięte, w przeciwnym razie **zwraca wartość false** .

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[single_link_registry, klasa](single-link-registry-class.md)<br/>
[multi_link_registry, klasa](multi-link-registry-class.md)
