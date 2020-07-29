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
ms.openlocfilehash: 777b3f5206b4a595b5dcac653d608255e92f4ef6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231705"
---
# <a name="multi_link_registry-class"></a>multi_link_registry — Klasa

`multi_link_registry`Obiekt jest `network_link_registry` zarządza wieloma blokami źródłowymi lub wieloma blokami docelowymi.

## <a name="syntax"></a>Składnia

```cpp
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>Parametry

*_Block*<br/>
Typ danych bloku przechowywanych w `multi_link_registry` obiekcie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[multi_link_registry](#ctor)|Konstruuje `multi_link_registry` obiekt.|
|[~ multi_link_registry destruktor](#dtor)|Niszczy `multi_link_registry` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[add](#add)|Dodaje łącze do `multi_link_registry` obiektu. (Zastępuje [network_link_registry:: Add](network-link-registry-class.md#add).)|
|[zaczną](#begin)|Zwraca iterator do pierwszego elementu w `multi_link_registry` obiekcie. (Zastępuje [network_link_registry:: BEGIN](network-link-registry-class.md#begin).)|
|[wyświetlana](#contains)|Przeszukuje `multi_link_registry` obiekt pod kątem określonego bloku. (Zastępuje [network_link_registry:: Contains](network-link-registry-class.md#contains).)|
|[liczbą](#count)|Zlicza elementy w `multi_link_registry` obiekcie. (Zastępuje [network_link_registry:: Count](network-link-registry-class.md#count).)|
|[usuwa](#remove)|Usuwa łącze z `multi_link_registry` obiektu. (Zastępuje [network_link_registry:: Remove](network-link-registry-class.md#remove).)|
|[set_bound](#set_bound)|Ustawia górną granicę dla liczby linków, które `multi_link_registry` obiekt może przechowywać.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[network_link_registry](network-link-registry-class.md)

`multi_link_registry`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="add"></a><a name="add"></a>dodana

Dodaje łącze do `multi_link_registry` obiektu.

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać dodany.

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_link_target](invalid-link-target-class.md) , jeśli link jest już obecny w rejestrze lub jeśli powiązano został już ustawiony przy użyciu `set_bound` funkcji i Link został usunięty.

## <a name="begin"></a><a name="begin"></a>zaczną

Zwraca iterator do pierwszego elementu w `multi_link_registry` obiekcie.

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator odnoszący się do pierwszego elementu w `multi_link_registry` obiekcie.

### <a name="remarks"></a>Uwagi

Stan końcowy jest wskazywany przez `NULL` łącze.

## <a name="contains"></a><a name="contains"></a>wyświetlana

Przeszukuje `multi_link_registry` obiekt pod kątem określonego bloku.

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma być wyszukiwany w `multi_link_registry` obiekcie.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli określony blok został znaleziony, **`false`** w przeciwnym razie.

## <a name="count"></a><a name="count"></a>liczbą

Zlicza elementy w `multi_link_registry` obiekcie.

```cpp
virtual size_t count();
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w `multi_link_registry` obiekcie.

## <a name="multi_link_registry"></a><a name="ctor"></a>multi_link_registry

Konstruuje `multi_link_registry` obiekt.

```cpp
multi_link_registry();
```

## <a name="multi_link_registry"></a><a name="dtor"></a>~ multi_link_registry

Niszczy `multi_link_registry` obiekt.

```cpp
virtual ~multi_link_registry();
```

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_operation](invalid-operation-class.md) , jeśli wywoływana przed usunięciem wszystkich linków.

## <a name="remove"></a><a name="remove"></a>usuwa

Usuwa łącze z `multi_link_registry` obiektu.

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do usunięcia bloku, jeśli został znaleziony.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli łącze zostało odnalezione i usunięte, **`false`** w przeciwnym razie.

## <a name="set_bound"></a><a name="set_bound"></a>set_bound

Ustawia górną granicę dla liczby linków, które `multi_link_registry` obiekt może przechowywać.

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Parametry

*_MaxLinks*<br/>
Maksymalna liczba linków, które mogą być `multi_link_registry` przechowywane w obiekcie.

### <a name="remarks"></a>Uwagi

Po ustawieniu powiązania, odłączenie wpisu spowoduje, że `multi_link_registry` obiekt przejdzie do niezmiennego stanu, gdy dalsze wywołania `add` wywoła `invalid_link_target` wyjątek.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa single_link_registry](single-link-registry-class.md)
