---
title: Isource — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
dev_langs:
- C++
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e53f8999b4559a221b335528ec20b6034de269d3
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162207"
---
# <a name="isource-class"></a>ISource — Klasa

`ISource` Klasy to interfejs dla wszystkich źródłowych bloków. Bloków źródła Propagacja komunikatów `ITarget` bloków.

## <a name="syntax"></a>Składnia

```
template<class T>
class ISource;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych ładunku w komunikaty generowane przez blok źródłowy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`source_type`|Alias typu `T`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[~ ISource — destruktor](#dtor)|Niszczy `ISource` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Zaakceptuj](#accept)|W przypadku przesłonięcia w klasie pochodnej, akceptuje wiadomości, które było oferowane przez to `ISource` bloku, przenoszenia własności do obiektu wywołującego.|
|[acquire_ref](#acquire_ref)|W przypadku przesłonięcia w klasie pochodnej, uzyskuje licznik odwołań, w tym `ISource` bloku, aby zapobiec usunięciu.|
|[Używanie](#consume)|W przypadku przesłonięcia w klasie pochodnej, zużywa komunikat oferowane wcześniej to `ISource` blokowania i pomyślnie zarezerwowany przez element docelowy przenoszenia własności do obiektu wywołującego.|
|[link_target](#link_target)|W przypadku przesłonięcia w klasie pochodnej, łączy blok docelowy to `ISource` bloku.|
|[Wydania](#release)|W przypadku przesłonięcia w klasie pochodnej, zwalnia poprzedniego zastrzeżenie komunikatu pomyślnie.|
|[release_ref](#release_ref)|W przypadku przesłonięcia w klasie pochodnej, zwalnia licznik odwołań, w tym `ISource` bloku.|
|[reserve](#reserve)|W przypadku przesłonięcia w klasie pochodnej, rezerwuje komunikat oferowane wcześniej to `ISource` bloku.|
|[unlink_target](#unlink_target)|W przypadku przesłonięcia w klasie pochodnej, rozłączysz blok docelowy z tego `ISource` zablokować, jeśli znaleziono wcześniej połączenie.|
|[unlink_targets](#unlink_targets)|W przypadku przesłonięcia w klasie pochodnej, odłączenie wszystkich bloków docelowych z tego `ISource` bloku.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ISource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="accept"></a> Zaakceptuj

W przypadku przesłonięcia w klasie pochodnej, akceptuje wiadomości, które było oferowane przez to `ISource` bloku, przenoszenia własności do obiektu wywołującego.

```
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z oferowane `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `accept` metody.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wiadomości, że obiekt wywołujący ma teraz własności.

### <a name="remarks"></a>Uwagi

`accept` Metoda jest wywoływana przez obiekt docelowy, gdy komunikat jest oferowana przez to `ISource` bloku. Zwrócony wskaźnik komunikat może być inny niż ten, który został przekazany do `propagate` metody `ITarget` zablokować, jeśli to źródło zdecyduje się na kopię wiadomości.

##  <a name="acquire_ref"></a> acquire_ref —

W przypadku przesłonięcia w klasie pochodnej, uzyskuje licznik odwołań, w tym `ISource` bloku, aby zapobiec usunięciu.

```
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana `ITarget` obiekt, który jest kojarzony z tym źródłem podczas `link_target` metody.

##  <a name="consume"></a> Używanie

W przypadku przesłonięcia w klasie pochodnej, zużywa komunikat oferowane wcześniej to `ISource` blokowania i pomyślnie zarezerwowany przez element docelowy przenoszenia własności do obiektu wywołującego.

```
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z zarezerwowanego `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `consume` metody.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, że obiekt wywołujący ma teraz własności.

### <a name="remarks"></a>Uwagi

`consume` Metoda jest podobna do `accept`, ale zawsze musi być poprzedzony przez wywołanie `reserve` zwróconą **true**.

##  <a name="dtor"></a> ~ ISource

Niszczy `ISource` obiektu.

```
virtual ~ISource();
```

##  <a name="link_target"></a> link_target —

W przypadku przesłonięcia w klasie pochodnej, łączy blok docelowy to `ISource` bloku.

```
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego jest połączona z tym `ISource` bloku.

##  <a name="release"></a> Wydania

W przypadku przesłonięcia w klasie pochodnej, zwalnia poprzedniego zastrzeżenie komunikatu pomyślnie.

```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z zarezerwowanego `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `release` metody.

##  <a name="release_ref"></a> release_ref —

W przypadku przesłonięcia w klasie pochodnej, zwalnia licznik odwołań, w tym `ISource` bloku.

```
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana `ITarget` obiekt, który jest jest rozłączony z tego źródła. Blok źródłowy może zwolnić wszystkie zasoby, które są zarezerwowane dla blok docelowy.

##  <a name="reserve"></a> Zarezerwuj

W przypadku przesłonięcia w klasie pochodnej, rezerwuje komunikat oferowane wcześniej to `ISource` bloku.

```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z oferowane `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `reserve` metody.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli komunikat został pomyślnie zarezerwowany, **false** inaczej. Rezerwacji może się nie powieść z wielu powodów, takich jak: komunikat został już zarezerwowany lub zaakceptowane przez inny obiekt docelowy, źródła można odmówić rezerwacji i tak dalej.

### <a name="remarks"></a>Uwagi

Po wywołaniu metody `reserve`, jeśli się powiedzie, należy wywołać albo `consume` lub `release` aby można było podjąć lub zrezygnować z posiadania wiadomości, odpowiednio.

##  <a name="unlink_target"></a> unlink_target —

W przypadku przesłonięcia w klasie pochodnej, rozłączysz blok docelowy z tego `ISource` zablokować, jeśli znaleziono wcześniej połączenie.

```
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego jest rozłączony z tego `ISource` bloku.

##  <a name="unlink_targets"></a> unlink_targets —

W przypadku przesłonięcia w klasie pochodnej, odłączenie wszystkich bloków docelowych z tego `ISource` bloku.

```
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[ITarget, klasa](itarget-class.md)
