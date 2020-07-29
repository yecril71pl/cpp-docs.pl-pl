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
ms.openlocfilehash: 24f89a6b2fb998ba5e5a82dbb470accb45d0fd9f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219550"
---
# <a name="single_link_registry-class"></a>single_link_registry — Klasa

`single_link_registry`Obiekt jest `network_link_registry` , który zarządza tylko pojedynczym blokiem źródłowym lub docelowym.

## <a name="syntax"></a>Składnia

```cpp
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>Parametry

*_Block*<br/>
Typ danych bloku przechowywanych w `single_link_registry` obiekcie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[single_link_registry](#ctor)|Konstruuje `single_link_registry` obiekt.|
|[~ single_link_registry destruktor](#dtor)|Niszczy `single_link_registry` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[add](#add)|Dodaje łącze do `single_link_registry` obiektu. (Zastępuje [network_link_registry:: Add](network-link-registry-class.md#add).)|
|[zaczną](#begin)|Zwraca iterator do pierwszego elementu w `single_link_registry` obiekcie. (Zastępuje [network_link_registry:: BEGIN](network-link-registry-class.md#begin).)|
|[wyświetlana](#contains)|Przeszukuje `single_link_registry` obiekt pod kątem określonego bloku. (Zastępuje [network_link_registry:: Contains](network-link-registry-class.md#contains).)|
|[liczbą](#count)|Zlicza elementy w `single_link_registry` obiekcie. (Zastępuje [network_link_registry:: Count](network-link-registry-class.md#count).)|
|[usuwa](#remove)|Usuwa łącze z `single_link_registry` obiektu. (Zastępuje [network_link_registry:: Remove](network-link-registry-class.md#remove).)|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[network_link_registry](network-link-registry-class.md)

`single_link_registry`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="add"></a><a name="add"></a>dodana

Dodaje łącze do `single_link_registry` obiektu.

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać dodany.

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_link_target](invalid-link-target-class.md) , jeśli w tym rejestrze znajduje się już link.

## <a name="begin"></a><a name="begin"></a>zaczną

Zwraca iterator do pierwszego elementu w `single_link_registry` obiekcie.

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator odnoszący się do pierwszego elementu w `single_link_registry` obiekcie.

### <a name="remarks"></a>Uwagi

Stan końcowy jest wskazywany przez `NULL` łącze.

## <a name="contains"></a><a name="contains"></a>wyświetlana

Przeszukuje `single_link_registry` obiekt pod kątem określonego bloku.

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma być wyszukiwany w `single_link_registry` obiekcie.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli łącze zostało znalezione, **`false`** w przeciwnym razie.

## <a name="count"></a><a name="count"></a>liczbą

Zlicza elementy w `single_link_registry` obiekcie.

```cpp
virtual size_t count();
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w `single_link_registry` obiekcie.

## <a name="remove"></a><a name="remove"></a>usuwa

Usuwa łącze z `single_link_registry` obiektu.

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do usunięcia bloku, jeśli został znaleziony.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli łącze zostało odnalezione i usunięte, **`false`** w przeciwnym razie.

## <a name="single_link_registry"></a><a name="ctor"></a>single_link_registry

Konstruuje `single_link_registry` obiekt.

```cpp
single_link_registry();
```

## <a name="single_link_registry"></a><a name="dtor"></a>~ single_link_registry

Niszczy `single_link_registry` obiekt.

```cpp
virtual ~single_link_registry();
```

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_operation](invalid-operation-class.md) , jeśli jest wywoływana przed usunięciem łącza.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa multi_link_registry](multi-link-registry-class.md)
