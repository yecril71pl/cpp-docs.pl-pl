---
title: multi_link_registry — Klasa
ms.date: 11/04/2016
f1_keywords:
- multi_link_registry
- AGENTS/concurrency::multi_link_registry
- AGENTS/concurrency::multi_link_registry::multi_link_registry
- AGENTS/concurrency::multi_link_registry::add
- AGENTS/concurrency::multi_link_registry::begin
- AGENTS/concurrency::multi_link_registry::contains
- AGENTS/concurrency::multi_link_registry::count
- AGENTS/concurrency::multi_link_registry::remove
- AGENTS/concurrency::multi_link_registry::set_bound
helpviewer_keywords:
- multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
ms.openlocfilehash: e22df5ee65d0219a46065044385dca46aac297a3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142371"
---
# <a name="multi_link_registry-class"></a>multi_link_registry — Klasa

Obiekt `multi_link_registry` jest `network_link_registry`, który zarządza wieloma blokami źródłowymi lub wieloma blokami docelowymi.

## <a name="syntax"></a>Składnia

```cpp
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>Parametry

*_Block*<br/>
Typ danych bloku przechowywanych w obiekcie `multi_link_registry`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[multi_link_registry](#ctor)|Konstruuje obiekt `multi_link_registry`.|
|[~ multi_link_registry destruktor](#dtor)|Niszczy obiekt `multi_link_registry`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[add](#add)|Dodaje łącze do obiektu `multi_link_registry`. (Zastępuje [network_link_registry:: Add](network-link-registry-class.md#add).)|
|[zaczną](#begin)|Zwraca iterator do pierwszego elementu w obiekcie `multi_link_registry`. (Zastępuje [network_link_registry:: BEGIN](network-link-registry-class.md#begin).)|
|[wyświetlana](#contains)|Wyszukuje `multi_link_registry` obiektu dla określonego bloku. (Zastępuje [network_link_registry:: Contains](network-link-registry-class.md#contains).)|
|[count](#count)|Zlicza elementy w obiekcie `multi_link_registry`. (Zastępuje [network_link_registry:: Count](network-link-registry-class.md#count).)|
|[remove](#remove)|Usuwa łącze z obiektu `multi_link_registry`. (Zastępuje [network_link_registry:: Remove](network-link-registry-class.md#remove).)|
|[set_bound](#set_bound)|Ustawia górną granicę dla liczby linków, które mogą być przechowywane w obiekcie `multi_link_registry`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[network_link_registry](network-link-registry-class.md)

`multi_link_registry`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="add"></a>dodana

Dodaje łącze do obiektu `multi_link_registry`.

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać dodany.

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_link_target](invalid-link-target-class.md) , jeśli link jest już obecny w rejestrze, lub jeśli powiązano został już ustawiony za pomocą funkcji `set_bound` i Link został usunięty.

## <a name="begin"></a>zaczną

Zwraca iterator do pierwszego elementu w obiekcie `multi_link_registry`.

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>Wartość zwrócona

Iterator odnoszący się do pierwszego elementu w obiekcie `multi_link_registry`.

### <a name="remarks"></a>Uwagi

Stan końcowy jest wskazywany przez łącze `NULL`.

## <a name="contains"></a>wyświetlana

Wyszukuje `multi_link_registry` obiektu dla określonego bloku.

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma być wyszukiwany w obiekcie `multi_link_registry`.

### <a name="return-value"></a>Wartość zwrócona

**wartość true** , jeśli znaleziono określony blok, w przeciwnym razie **zwraca wartość false** .

## <a name="count"></a>liczbą

Zlicza elementy w obiekcie `multi_link_registry`.

```cpp
virtual size_t count();
```

### <a name="return-value"></a>Wartość zwrócona

Liczba elementów w obiekcie `multi_link_registry`.

## <a name="ctor"></a>multi_link_registry

Konstruuje obiekt `multi_link_registry`.

```cpp
multi_link_registry();
```

## <a name="dtor"></a>~ multi_link_registry

Niszczy obiekt `multi_link_registry`.

```cpp
virtual ~multi_link_registry();
```

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_operation](invalid-operation-class.md) , jeśli wywoływana przed usunięciem wszystkich linków.

## <a name="remove"></a>usuwa

Usuwa łącze z obiektu `multi_link_registry`.

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do usunięcia bloku, jeśli został znaleziony.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli łącze zostało znalezione i usunięte, w przeciwnym razie **zwraca wartość false** .

## <a name="set_bound"></a>set_bound

Ustawia górną granicę dla liczby linków, które mogą być przechowywane w obiekcie `multi_link_registry`.

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Parametry

*_MaxLinks*<br/>
Maksymalna liczba linków, które mogą być przechowywane w obiekcie `multi_link_registry`.

### <a name="remarks"></a>Uwagi

Po ustawieniu granicy odłączenie wpisu spowoduje, że obiekt `multi_link_registry` przejdzie do niezmiennego stanu, gdy dalsze wywołania `add` spowodują zgłoszenie wyjątku `invalid_link_target`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[single_link_registry, klasa](single-link-registry-class.md)
