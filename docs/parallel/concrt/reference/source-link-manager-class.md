---
title: source_link_manager — Klasa
ms.date: 11/04/2016
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
ms.openlocfilehash: 35c7cc72520cdb0675abf9c15574a49e33741d0b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142697"
---
# <a name="source_link_manager-class"></a>source_link_manager — Klasa

Obiekt `source_link_manager` zarządza łączami sieci bloku komunikatów do bloków `ISource`.

## <a name="syntax"></a>Składnia

```cpp
template<class _LinkRegistry>
class source_link_manager;
```

### <a name="parameters"></a>Parametry

*_LinkRegistry*<br/>
Rejestr łączy sieciowych.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`const_pointer`|Typ, który dostarcza wskaźnik do elementu `const` w obiekcie `source_link_manager`.|
|`const_reference`|Typ, który dostarcza odwołanie do `const` elementu przechowywanego w obiekcie `source_link_manager` do odczytu i wykonywania operacji const.|
|`iterator`|Typ, który dostarcza iterator, który może odczytać lub zmodyfikować dowolny element w obiekcie `source_link_manager`.|
|`type`|Typ rejestru łącza zarządzany przez obiekt `source_link_manager`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[source_link_manager](#ctor)|Konstruuje obiekt `source_link_manager`.|
|[~ source_link_manager destruktor](#dtor)|Niszczy obiekt `source_link_manager`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[add](#add)|Dodaje łącze źródła do obiektu `source_link_manager`.|
|[zaczną](#begin)|Zwraca iterator do pierwszego elementu w obiekcie `source_link_manager`.|
|[wyświetlana](#contains)|Wyszukuje `network_link_registry` w tym obiekcie `source_link_manager` dla określonego bloku.|
|[count](#count)|Zlicza połączone bloki w obiekcie `source_link_manager`.|
|[odwoła](#reference)|Uzyskuje odwołanie do obiektu `source_link_manager`.|
|[register_target_block](#register_target_block)|Rejestruje blok docelowy, który zawiera ten obiekt `source_link_manager`.|
|[Usuwanie](#release)|Zwalnia odwołanie do obiektu `source_link_manager`.|
|[remove](#remove)|Usuwa łącze z obiektu `source_link_manager`.|
|[set_bound](#set_bound)|Ustawia maksymalną liczbę linków źródłowych, które można dodać do tego obiektu `source_link_manager`.|

## <a name="remarks"></a>Uwagi

Obecnie w blokach źródłowych są zliczane odwołania. Jest to otoka dla obiektu `network_link_registry`, który umożliwia współbieżny dostęp do linków i zapewnia możliwość odwoływania się do linków za pomocą wywołań zwrotnych. Bloki komunikatów (`target_block`s lub `propagator_block`s) powinny używać tej klasy jako linków źródłowych.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`source_link_manager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="add"></a>dodana

Dodaje łącze źródła do obiektu `source_link_manager`.

```cpp
void add(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać dodany.

## <a name="begin"></a>zaczną

Zwraca iterator do pierwszego elementu w obiekcie `source_link_manager`.

```cpp
iterator begin();
```

### <a name="return-value"></a>Wartość zwrócona

Iterator odnoszący się do pierwszego elementu w obiekcie `source_link_manager`.

### <a name="remarks"></a>Uwagi

Końcowy stan iteratora jest wskazywany przez łącze `NULL`.

## <a name="contains"></a>wyświetlana

Wyszukuje `network_link_registry` w tym obiekcie `source_link_manager` dla określonego bloku.

```cpp
bool contains(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma być wyszukiwany w obiekcie `source_link_manager`.

### <a name="return-value"></a>Wartość zwrócona

**wartość true** , jeśli znaleziono określony blok, w przeciwnym razie **zwraca wartość false** .

## <a name="count"></a>liczbą

Zlicza połączone bloki w obiekcie `source_link_manager`.

```cpp
size_t count();
```

### <a name="return-value"></a>Wartość zwrócona

Liczba połączonych bloków w obiekcie `source_link_manager`.

## <a name="reference"></a>odwoła

Uzyskuje odwołanie do obiektu `source_link_manager`.

```cpp
void reference();
```

## <a name="register_target_block"></a>register_target_block

Rejestruje blok docelowy, który zawiera ten obiekt `source_link_manager`.

```cpp
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Blok docelowy przechowujący ten obiekt `source_link_manager`.

## <a name="release"></a>Usuwanie

Zwalnia odwołanie do obiektu `source_link_manager`.

```cpp
void release();
```

## <a name="remove"></a>usuwa

Usuwa łącze z obiektu `source_link_manager`.

```cpp
bool remove(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do usunięcia bloku, jeśli został znaleziony.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli łącze zostało znalezione i usunięte, w przeciwnym razie **zwraca wartość false** .

## <a name="set_bound"></a>set_bound

Ustawia maksymalną liczbę linków źródłowych, które można dodać do tego obiektu `source_link_manager`.

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Parametry

*_MaxLinks*<br/>
Maksymalna liczba linków.

## <a name="ctor"></a>source_link_manager

Konstruuje obiekt `source_link_manager`.

```cpp
source_link_manager();
```

## <a name="dtor"></a>~ source_link_manager

Niszczy obiekt `source_link_manager`.

```cpp
~source_link_manager();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[single_link_registry, klasa](single-link-registry-class.md)<br/>
[multi_link_registry, klasa](multi-link-registry-class.md)
