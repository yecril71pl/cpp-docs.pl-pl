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
ms.openlocfilehash: 881b4f15c7238e69a91def08e5d20ad8955ec4e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545993"
---
# <a name="sourcelinkmanager-class"></a>source_link_manager — Klasa

`source_link_manager` Obiektu zarządza komunikatów blok połączeń sieciowych z `ISource` bloków.

## <a name="syntax"></a>Składnia

```
template<class _LinkRegistry>
class source_link_manager;
```

#### <a name="parameters"></a>Parametry

*_LinkRegistry*<br/>
Rejestr łącza sieci.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`const_pointer`|Typ, który dostarcza wskaźnik do `const` element `source_link_manager` obiektu.|
|`const_reference`|Typ, który zawiera odwołanie do `const` przechowywanego w `source_link_manager` obiektu do odczytu i wykonywania operacji const.|
|`iterator`|Typ zapewniający iterator, który może odczytać lub zmodyfikować dowolny element w `source_link_manager` obiektu.|
|`type`|Typ rejestru łącze, które są zarządzane przez `source_link_manager` obiektu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[source_link_manager](#ctor)|Konstruuje `source_link_manager` obiektu.|
|[~source_link_manager Destructor](#dtor)|Niszczy `source_link_manager` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[add](#add)|Dodaje źródło łącza do `source_link_manager` obiektu.|
|[begin](#begin)|Zwraca iterator do pierwszego elementu w `source_link_manager` obiektu.|
|[zawiera](#contains)|Wyszukiwanie `network_link_registry` w ramach tej `source_link_manager` obiektu dla określonego bloku.|
|[Liczba](#count)|Zlicza liczbę połączonych bloków w `source_link_manager` obiektu.|
|[Odwołanie](#reference)|Uzyskuje odwołanie na `source_link_manager` obiektu.|
|[register_target_block](#register_target_block)|Rejestruje blok docelowy, który zawiera ten `source_link_manager` obiektu.|
|[Wydania](#release)|Wydaje odniesienie na `source_link_manager` obiektu.|
|[remove](#remove)|Usuwa łącze między `source_link_manager` obiektu.|
|[set_bound](#set_bound)|Ustawia maksymalną liczbę łączy źródła, które mogą zostać dodane do tego `source_link_manager` obiektu.|

## <a name="remarks"></a>Uwagi

Obecnie bloków źródła jest liczona liczba odwołań. Jest to otokę `network_link_registry` obiekt, który umożliwia równoczesnego dostępu do łączy i umożliwia odwołanie łącza za pomocą wywołania zwrotne. Bloki komunikatów ( `target_block`s lub `propagator_block`s) należy używać tej klasy ich źródło łącza.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`source_link_manager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="add"></a> Dodaj

Dodaje źródło łącza do `source_link_manager` obiektu.

```
void add(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać dodana.

##  <a name="begin"></a> Rozpocznij

Zwraca iterator do pierwszego elementu w `source_link_manager` obiektu.

```
iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator odnoszący się do pierwszego elementu w `source_link_manager` obiektu.

### <a name="remarks"></a>Uwagi

Stan końcowy iterator który jest wskazywany przez `NULL` łącza.

##  <a name="contains"></a> zawiera

Wyszukiwanie `network_link_registry` w ramach tej `source_link_manager` obiektu dla określonego bloku.

```
bool contains(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać wyszukany w `source_link_manager` obiektu.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli określony blok został znaleziony, **false** inaczej.

##  <a name="count"></a> Liczba

Zlicza liczbę połączonych bloków w `source_link_manager` obiektu.

```
size_t count();
```

### <a name="return-value"></a>Wartość zwracana

Liczba połączonych bloków w `source_link_manager` obiektu.

##  <a name="reference"></a> Odwołanie

Uzyskuje odwołanie na `source_link_manager` obiektu.

```
void reference();
```

##  <a name="register_target_block"></a> register_target_block —

Rejestruje blok docelowy, który zawiera ten `source_link_manager` obiektu.

```
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Blok docelowy, przechowywania to `source_link_manager` obiektu.

##  <a name="release"></a> Wydania

Wydaje odniesienie na `source_link_manager` obiektu.

```
void release();
```

##  <a name="remove"></a> Usuń

Usuwa łącze między `source_link_manager` obiektu.

```
bool remove(_EType _Link);
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać usunięty, jeśli znaleziono.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli łącze zostało znalezione i usuwane, **false** inaczej.

##  <a name="set_bound"></a> set_bound —

Ustawia maksymalną liczbę łączy źródła, które mogą zostać dodane do tego `source_link_manager` obiektu.

```
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Parametry

*_MaxLinks*<br/>
Maksymalna liczba łączy.

##  <a name="ctor"></a> source_link_manager

Konstruuje `source_link_manager` obiektu.

```
source_link_manager();
```

##  <a name="dtor"></a> ~source_link_manager

Niszczy `source_link_manager` obiektu.

```
~source_link_manager();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[single_link_registry, klasa](single-link-registry-class.md)<br/>
[multi_link_registry, klasa](multi-link-registry-class.md)
