---
title: single_link_registry — Klasa
ms.date: 11/04/2016
f1_keywords:
- single_link_registry
- AGENTS/concurrency::single_link_registry
- AGENTS/concurrency::single_link_registry::single_link_registry
- AGENTS/concurrency::single_link_registry::add
- AGENTS/concurrency::single_link_registry::begin
- AGENTS/concurrency::single_link_registry::contains
- AGENTS/concurrency::single_link_registry::count
- AGENTS/concurrency::single_link_registry::remove
helpviewer_keywords:
- single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
ms.openlocfilehash: c29caf6d31df316e80b15fe6827c81e34ece8a18
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142721"
---
# <a name="single_link_registry-class"></a>single_link_registry — Klasa

Obiekt `single_link_registry` jest `network_link_registry`, który zarządza tylko pojedynczym blokiem źródłowym lub docelowym.

## <a name="syntax"></a>Składnia

```cpp
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>Parametry

*_Block*<br/>
Typ danych bloku przechowywanych w obiekcie `single_link_registry`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[single_link_registry](#ctor)|Konstruuje obiekt `single_link_registry`.|
|[~ single_link_registry destruktor](#dtor)|Niszczy obiekt `single_link_registry`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[add](#add)|Dodaje łącze do obiektu `single_link_registry`. (Zastępuje [network_link_registry:: Add](network-link-registry-class.md#add).)|
|[zaczną](#begin)|Zwraca iterator do pierwszego elementu w obiekcie `single_link_registry`. (Zastępuje [network_link_registry:: BEGIN](network-link-registry-class.md#begin).)|
|[wyświetlana](#contains)|Wyszukuje `single_link_registry` obiektu dla określonego bloku. (Zastępuje [network_link_registry:: Contains](network-link-registry-class.md#contains).)|
|[count](#count)|Zlicza elementy w obiekcie `single_link_registry`. (Zastępuje [network_link_registry:: Count](network-link-registry-class.md#count).)|
|[remove](#remove)|Usuwa łącze z obiektu `single_link_registry`. (Zastępuje [network_link_registry:: Remove](network-link-registry-class.md#remove).)|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[network_link_registry](network-link-registry-class.md)

`single_link_registry`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="add"></a>dodana

Dodaje łącze do obiektu `single_link_registry`.

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać dodany.

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_link_target](invalid-link-target-class.md) , jeśli w tym rejestrze znajduje się już link.

## <a name="begin"></a>zaczną

Zwraca iterator do pierwszego elementu w obiekcie `single_link_registry`.

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>Wartość zwrócona

Iterator odnoszący się do pierwszego elementu w obiekcie `single_link_registry`.

### <a name="remarks"></a>Uwagi

Stan końcowy jest wskazywany przez łącze `NULL`.

## <a name="contains"></a>wyświetlana

Wyszukuje `single_link_registry` obiektu dla określonego bloku.

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma być wyszukiwany w obiekcie `single_link_registry`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli Link został znaleziony, w przeciwnym razie **zwraca wartość false** .

## <a name="count"></a>liczbą

Zlicza elementy w obiekcie `single_link_registry`.

```cpp
virtual size_t count();
```

### <a name="return-value"></a>Wartość zwrócona

Liczba elementów w obiekcie `single_link_registry`.

## <a name="remove"></a>usuwa

Usuwa łącze z obiektu `single_link_registry`.

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do usunięcia bloku, jeśli został znaleziony.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli łącze zostało znalezione i usunięte, w przeciwnym razie **zwraca wartość false** .

## <a name="ctor"></a>single_link_registry

Konstruuje obiekt `single_link_registry`.

```cpp
single_link_registry();
```

## <a name="dtor"></a>~ single_link_registry

Niszczy obiekt `single_link_registry`.

```cpp
virtual ~single_link_registry();
```

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_operation](invalid-operation-class.md) , jeśli jest wywoływana przed usunięciem łącza.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[multi_link_registry, klasa](multi-link-registry-class.md)
