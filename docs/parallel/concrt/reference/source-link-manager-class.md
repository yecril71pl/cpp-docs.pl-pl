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
ms.openlocfilehash: 98f99bb5aec85a640eaf83a07fae3a1b667f7d91
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228430"
---
# <a name="source_link_manager-class"></a>source_link_manager — Klasa

`source_link_manager`Obiekt zarządza łączami sieci bloku komunikatów do `ISource` bloków.

## <a name="syntax"></a>Składnia

```cpp
template<class _LinkRegistry>
class source_link_manager;
```

### <a name="parameters"></a>Parametry

*_LinkRegistry*<br/>
Rejestr łączy sieciowych.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`const_pointer`|Typ, który dostarcza wskaźnik do **`const`** elementu w `source_link_manager` obiekcie.|
|`const_reference`|Typ, który zawiera odwołanie do **`const`** elementu przechowywanego w `source_link_manager` obiekcie na potrzeby odczytywania i wykonywania operacji const.|
|`iterator`|Typ, który dostarcza iterator, który może odczytać lub zmodyfikować dowolny element w `source_link_manager` obiekcie.|
|`type`|Typ rejestru łącza, który jest zarządzany przez `source_link_manager` obiekt.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[source_link_manager](#ctor)|Konstruuje `source_link_manager` obiekt.|
|[~ source_link_manager destruktor](#dtor)|Niszczy `source_link_manager` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[add](#add)|Dodaje łącze źródła do `source_link_manager` obiektu.|
|[zaczną](#begin)|Zwraca iterator do pierwszego elementu w `source_link_manager` obiekcie.|
|[wyświetlana](#contains)|Wyszukuje `network_link_registry` w obrębie tego `source_link_manager` obiektu dla określonego bloku.|
|[liczbą](#count)|Zlicza połączone bloki w `source_link_manager` obiekcie.|
|[odwoła](#reference)|Uzyskuje odwołanie do `source_link_manager` obiektu.|
|[register_target_block](#register_target_block)|Rejestruje blok docelowy, który zawiera ten `source_link_manager` obiekt.|
|[Usuwanie](#release)|Zwalnia odwołanie do `source_link_manager` obiektu.|
|[usuwa](#remove)|Usuwa łącze z `source_link_manager` obiektu.|
|[set_bound](#set_bound)|Ustawia maksymalną liczbę linków źródłowych, które można dodać do tego `source_link_manager` obiektu.|

## <a name="remarks"></a>Uwagi

Obecnie w blokach źródłowych są zliczane odwołania. Jest to otoka dla `network_link_registry` obiektu, który umożliwia współbieżny dostęp do linków i zapewnia możliwość odwoływania się do linków za pomocą wywołań zwrotnych. Bloki komunikatów ( `target_block` s `propagator_block` ) powinny używać tej klasy do ich linków źródłowych.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`source_link_manager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="add"></a><a name="add"></a>dodana

Dodaje łącze źródła do `source_link_manager` obiektu.

```cpp
void add(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać dodany.

## <a name="begin"></a><a name="begin"></a>zaczną

Zwraca iterator do pierwszego elementu w `source_link_manager` obiekcie.

```cpp
iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator odnoszący się do pierwszego elementu w `source_link_manager` obiekcie.

### <a name="remarks"></a>Uwagi

Końcowy stan iteratora jest wskazywany przez `NULL` łącze.

## <a name="contains"></a><a name="contains"></a>wyświetlana

Wyszukuje `network_link_registry` w obrębie tego `source_link_manager` obiektu dla określonego bloku.

```cpp
bool contains(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma być wyszukiwany w `source_link_manager` obiekcie.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli określony blok został znaleziony, **`false`** w przeciwnym razie.

## <a name="count"></a><a name="count"></a>liczbą

Zlicza połączone bloki w `source_link_manager` obiekcie.

```cpp
size_t count();
```

### <a name="return-value"></a>Wartość zwracana

Liczba połączonych bloków w `source_link_manager` obiekcie.

## <a name="reference"></a><a name="reference"></a>odwoła

Uzyskuje odwołanie do `source_link_manager` obiektu.

```cpp
void reference();
```

## <a name="register_target_block"></a><a name="register_target_block"></a>register_target_block

Rejestruje blok docelowy, który zawiera ten `source_link_manager` obiekt.

```cpp
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Blok docelowy przechowujący ten `source_link_manager` obiekt.

## <a name="release"></a><a name="release"></a>Usuwanie

Zwalnia odwołanie do `source_link_manager` obiektu.

```cpp
void release();
```

## <a name="remove"></a><a name="remove"></a>usuwa

Usuwa łącze z `source_link_manager` obiektu.

```cpp
bool remove(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do usunięcia bloku, jeśli został znaleziony.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli łącze zostało odnalezione i usunięte, **`false`** w przeciwnym razie.

## <a name="set_bound"></a><a name="set_bound"></a>set_bound

Ustawia maksymalną liczbę linków źródłowych, które można dodać do tego `source_link_manager` obiektu.

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Parametry

*_MaxLinks*<br/>
Maksymalna liczba linków.

## <a name="source_link_manager"></a><a name="ctor"></a>source_link_manager

Konstruuje `source_link_manager` obiekt.

```cpp
source_link_manager();
```

## <a name="source_link_manager"></a><a name="dtor"></a>~ source_link_manager

Niszczy `source_link_manager` obiekt.

```cpp
~source_link_manager();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa single_link_registry](single-link-registry-class.md)<br/>
[Klasa multi_link_registry](multi-link-registry-class.md)
