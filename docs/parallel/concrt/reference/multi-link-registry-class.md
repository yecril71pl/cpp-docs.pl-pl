---
title: multi_link_registry — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26144fe1098e932512344550864c0949e5306238
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401710"
---
# <a name="multilinkregistry-class"></a>multi_link_registry — Klasa

`multi_link_registry` Obiekt jest `network_link_registry` który zarządza wiele bloków źródła lub wiele bloków docelowych.

## <a name="syntax"></a>Składnia

```
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```

#### <a name="parameters"></a>Parametry

*_Blok*<br/>
Typ danych bloku znajdujących się w `multi_link_registry` obiektu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[multi_link_registry](#ctor)|Konstruuje `multi_link_registry` obiektu.|
|[~multi_link_registry Destructor](#dtor)|Niszczy `multi_link_registry` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[add](#add)|Dodaje link do `multi_link_registry` obiektu. (Przesłania [network_link_registry::add —](network-link-registry-class.md#add).)|
|[begin](#begin)|Zwraca iterator do pierwszego elementu w `multi_link_registry` obiektu. (Przesłania [network_link_registry::Begin —](network-link-registry-class.md#begin).)|
|[zawiera](#contains)|Wyszukiwanie `multi_link_registry` obiektu dla określonego bloku. (Przesłania [network_link_registry::CONTAINS —](network-link-registry-class.md#contains).)|
|[Liczba](#count)|Zlicza liczbę elementów w `multi_link_registry` obiektu. (Przesłania [network_link_registry::Count —](network-link-registry-class.md#count).)|
|[remove](#remove)|Usuwa łącze między `multi_link_registry` obiektu. (Przesłania [network_link_registry::REMOVE —](network-link-registry-class.md#remove).)|
|[set_bound](#set_bound)|Ustawia górnej granicy liczby linków `multi_link_registry` obiekt może przechowywać.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[network_link_registry](network-link-registry-class.md)

`multi_link_registry`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="add"></a> Dodaj

Dodaje link do `multi_link_registry` obiektu.

```
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać dodana.

### <a name="remarks"></a>Uwagi

Metoda zgłasza [invalid_link_target —](invalid-link-target-class.md) wyjątku czy link znajduje się już w rejestrze, czy granicę został już ustawiony za pomocą `set_bound` funkcji i łącze odwałania został usunięty.

##  <a name="begin"></a> Rozpocznij

Zwraca iterator do pierwszego elementu w `multi_link_registry` obiektu.

```
virtual iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator odnoszący się do pierwszego elementu w `multi_link_registry` obiektu.

### <a name="remarks"></a>Uwagi

Stan zakończenia jest wskazywany przez `NULL` łącza.

##  <a name="contains"></a> zawiera

Wyszukiwanie `multi_link_registry` obiektu dla określonego bloku.

```
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać wyszukany w `multi_link_registry` obiektu.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli określony blok został znaleziony, `false` inaczej.

##  <a name="count"></a> Liczba

Zlicza liczbę elementów w `multi_link_registry` obiektu.

```
virtual size_t count();
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w `multi_link_registry` obiektu.

##  <a name="ctor"></a> multi_link_registry —

Konstruuje `multi_link_registry` obiektu.

```
multi_link_registry();
```

##  <a name="dtor"></a> ~multi_link_registry

Niszczy `multi_link_registry` obiektu.

```
virtual ~multi_link_registry();
```

### <a name="remarks"></a>Uwagi

Metoda zgłasza [invalid_operation](invalid-operation-class.md) wyjątek, jeśli metoda wywoływana przed zostaną usunięte wszystkie łącza.

##  <a name="remove"></a> Usuń

Usuwa łącze między `multi_link_registry` obiektu.

```
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać usunięty, jeśli znaleziono.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli łącze zostało znalezione i usuwane, `false` inaczej.

##  <a name="set_bound"></a> set_bound —

Ustawia górnej granicy liczby linków `multi_link_registry` obiekt może przechowywać.

```
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Parametry

*_MaxLinks*<br/>
Maksymalna liczba łączy, które `multi_link_registry` obiekt może przechowywać.

### <a name="remarks"></a>Uwagi

Po ustawieniu granicę spowoduje odłączenie wpis `multi_link_registry` obiektu, aby wprowadzić niezmiennego stanu gdzie dalsze wywołania `add` zgłosi `invalid_link_target` wyjątku.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[single_link_registry, klasa](single-link-registry-class.md)
